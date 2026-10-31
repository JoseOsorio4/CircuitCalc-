# CircuitCalc v1.3

Comparte **CircuitCalc.html** con tus compañeros. Es idéntico a **index.html**, que sigue siendo el archivo principal del proyecto. Abre cualquiera **con doble clic** en Chrome o Edge. Si ya estaba abierto, recarga la pestaña para ver esta versión. Toda la aplicación está dentro del archivo: no necesita internet, Node, instalaciones, servidor, localhost, CDN ni archivos adicionales.

## Ejemplo estrella–delta de los compañeros

El esquema de 13 resistencias está disponible en el selector de ejemplos y se abre en modo avanzado. Con R11 = 7.9 kΩ, Req ≈ 2.855652790 kΩ. La imagen aportada no especifica el voltaje; el ejemplo usa 1 V de referencia y permite cambiarlo.

## Constructor rápido

1. Ajusta el voltaje de la fuente. El circuito inicial contiene R1 = 100 Ω, editable.
2. Haz clic en una resistencia del dibujo. Cambia su nombre o valor en el panel contextual.
3. Pulsa **Añadir en serie** o **Añadir en paralelo**. Aparece la siguiente resistencia, inicialmente de 100 Ω, con su campo de valor seleccionado para que puedas sustituirlo.
4. Para conectar algo respecto a un conjunto completo, selecciona el borde o el título del bloque. También puedes seleccionarlo mediante los botones de sus bloques contenedores en el panel contextual.
5. Pulsa **Calcular mi circuito**. Verás Req, voltaje, corriente, potencia y la tabla individual.

Por ejemplo: selecciona R1, añade R2 en paralelo, selecciona el bloque R1/R2 y añade R3 en serie. El programa crea el anidamiento y los nodos internamente. No necesitas crear grupos manualmente.

Con un componente ya seleccionado, añadir una resistencia y establecer su conexión requiere **un clic**. En la interfaz anterior, el flujo de relaciones requería añadir la resistencia, elegir dos componentes, escoger la relación y crear la conexión.

El esquema empieza en tamaño legible, al menos al 100 %. Usa **+**, **−** y el desplazamiento del lienzo para inspeccionar circuitos extensos. **Ver todo** encaja el circuito completo, aunque los textos se reduzcan; **Legible** recupera el tamaño de lectura. Los grupos automáticos muestran «Circuito completo» o «Conjunto R1–R3»; se conservan los nombres que tú asignas. Puedes arrastrar el dibujo con el ratón o usar el desplazamiento táctil. Los componentes del SVG también admiten selección por teclado con Tab y Enter/Espacio.

**Eliminar** quita la resistencia seleccionada; si seleccionas un bloque, el botón indica cuántas resistencias contiene. Los bloques que quedan con un solo componente se simplifican. **Deshacer** restaura los cambios, la selección y el voltaje; se conservan hasta 80 cambios durante la sesión. El guardado automático conserva el circuito, pero el historial de deshacer corresponde únicamente a la sesión actual.

## Funciones secundarias conservadas

- **Edición detallada:** nombres y valores en lista, selección múltiple, grupos en serie/paralelo, relaciones mediante selectores, mover a un grupo, desagrupar, sacar componentes y reordenar. Los bloques sueltos o vacíos requieren una conexión explícita antes de calcular.
- **Ver procedimiento:** en el constructor muestra primero la reducción de cada grupo en serie/paralelo hasta Req, seguida de I y P. Las ecuaciones, potenciales y sistema normalizado se conservan bajo **Ecuaciones de Kirchhoff (avanzado)**. Los desplegables empiezan cerrados. Si la explicación no puede representarse con precisión suficiente, se mantiene el procedimiento nodal.
- **Detalles avanzados:** editor de nodos para puentes y redes generales, revisión del PDF y botón de pruebas.
- **Ver esta red en modo avanzado:** copia exactamente la red del constructor. Ambos modos conservan borradores separados; los cambios hechos por nodos no se convierten automáticamente en grupos.
- **Imprimir / Guardar PDF:** utiliza el diálogo nativo del navegador. El reporte contiene fuente, resultados, tabla, dibujo y procedimiento, con colores adecuados para papel. El SVG se captura al calcular y no depende del zoom de pantalla. Los esquemas anchos usan una página horizontal mediante CSS de impresión; el navegador puede aplicar sus propios ajustes. El dibujo es vectorial y se puede ampliar dentro del lector de PDF. Las secciones del procedimiento se abren al imprimir y recuperan después su estado anterior.

El selector conserva los ejemplos anteriores y añade mixtos de 8, 10, 15 y 16 resistencias. El ejemplo original del PDF conserva 239 V y R1 = 294 Ω; la variante de R1 = 244 Ω sigue identificada por separado. El ejemplo puente abre el modo avanzado.

## Guardado y copias

El indicador **Guardado en este navegador** confirma que se escribió el borrador local. Se conservan los circuitos fácil y avanzado por separado, voltajes, selección, modo y precisión de la tabla. También se guardan componentes sin conectar o valores a medio escribir; al volver debes completar los datos y calcular. Los resultados se recalculan, no se confía en resultados almacenados.

- **Guardar copia** descarga `CircuitCalc-circuito.json`, con ambos borradores y ajustes.
- **Abrir copia** restaura ese archivo. Un JSON inválido se rechaza antes de modificar el circuito activo.
- Para compartir un ejercicio editable, envía **CircuitCalc.html y el JSON**. Cada compañero abre el HTML y pulsa **Abrir copia**. Enviar solamente el HTML comparte la aplicación y sus ejemplos; no incluye tu borrador privado del navegador.
- Si el almacenamiento está bloqueado o lleno, la calculadora sigue funcionando y el indicador pide guardar una copia. Un borrador local corrupto no se sobrescribe automáticamente.

El almacenamiento depende del navegador y de la ubicación del archivo. No se garantiza al cambiar de nombre/carpeta, borrar datos del navegador o usar modo privado. El comportamiento de `localStorage` en direcciones `file:` no está definido de forma uniforme; por eso se ofrece la copia JSON. [Referencia oficial de MDN](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage).

## Lectura de resultados

La tabla se ordena naturalmente por el nombre visible: R1, R2… R10. Presenta **cuatro decimales** por defecto y permite elegir **12 cifras significativas**. Los valores completos se muestran también en la ayuda al pasar el cursor sobre las celdas. Las magnitudes muy pequeñas usan notación científica para evitar mostrar cero cuando no lo son. La precisión visual no cambia el cálculo ni el orden interno de la red.

## Diseño y animaciones

La pantalla principal pone el SVG y las dos acciones de conexión en primer plano. La paleta usa azul marino, circuitos en cian, botón de cálculo amarillo y verificaciones verdes. Los controles complejos comienzan plegados.

Las animaciones se limitan a aparición de componentes, trazado breve de cables y resultados. No representan circulación de corriente. La opción del sistema **reducir movimiento** desactiva las animaciones y transiciones. El indicador de cálculo se muestra mientras se procesa una solicitud; editar durante ese intervalo cancela la solicitud pendiente para evitar resultados desactualizados.

## Revisión independiente del PDF

Se inspeccionaron las cuatro páginas. El circuito válido para la tarea es el manuscrito de diez resistencias de las páginas 2–4; la portada muestra un circuito diferente y se interpreta como ilustración.

Hay una diferencia entre las fuentes: **el PDF muestra R1 = 294 Ω**, mientras que el texto de especificaciones indica **R1 = 244 Ω**. La expectativa de aproximadamente 515.26 Ω corresponde al primero. La aplicación incluye ambas variantes con nombres explícitos.

| Variante, a 239 V | Req (Ω) | I total (A) | P total (W) |
|---|---:|---:|---:|
| PDF: R1 = 294 Ω | 515.257131027832 | 0.463846079186220 | 110.859212925507 |
| Texto adjunto: R1 = 244 Ω | 513.393358632876 | 0.465529980045782 | 111.261665230942 |

La topología usada es:

`(R1 ∥ R2 ∥ R3) + R5 + [R6 ∥ (R7 + (R9 ∥ (R8 + R10)))] + R4`

Para el PDF, una comprobación por reducción con fracciones exactas da:

- R1 ∥ R2 ∥ R3 = 52.65093435553426 Ω.
- R8 + R10 = 369 Ω.
- R9 ∥ (R8 + R10) = 213.56506849315068 Ω.
- R7 + bloque anterior = 312.56506849315068 Ω.
- R6 ∥ rama anterior = 158.6061966722974 Ω.
- Req = 398506554205 / 773412982 Ω = 515.2571310278316 Ω.

### Inconsistencias encontradas

- **Potencia de R7:** la tabla dice 3.48 W. El valor correcto es **5.484567616438 W**, que redondea a **5.48 W**. Sus propios valores de voltaje y corriente, 23.30 V y 0.2354 A, dan aproximadamente 5.485 W. La diferencia afecta la conservación de potencia en unos 2 W.
- **Suma final de resistencias:** los sumandos manuscritos `52.6509 + 100 + 204 + 158.6061` dan **515.2570 Ω**, no 515.2651 Ω. Sin redondear antes, se obtiene 515.257131 Ω.
- **División para la corriente:** `239 / 515.2` da **0.4638975155 A**, no 0.46385 A. La corriente 0.46385 A sí es un redondeo válido al usar la resistencia equivalente correcta sin truncar.
- **Potencia total:** el manuscrito indica aproximadamente 110.8542 W. La potencia correcta es **110.859212925507 W**. Incluso usando la corriente redondeada escrita, `239 × 0.46385 = 110.86015 W`.
- **Potencia de R5:** el último trazo no permite distinguir con plena certeza entre 43.84 W y 43.89 W. El resultado correcto es **43.891249775991 W**, o **43.89 W** a dos decimales. Si la anotación es 43.84 W, requiere corrección.
- **Fuente:** la primera anotación puede parecer 2.39 V por su escritura; los esquemas posteriores y las operaciones usan **239 V**, el valor adoptado. Con 2.39 V las corrientes serían cien veces menores y las potencias diez mil veces menores.

Las pequeñas diferencias restantes de últimas cifras son compatibles con redondeos o truncamientos. La reducción de las ramas en serie y paralelo es conceptualmente correcta.

### Tabla corregida del PDF, R1 = 294 Ω

| Resistencia | Valor (Ω) | Voltaje (V) | Corriente (A) | Potencia (W) |
|---|---:|---:|---:|---:|
| R1 | 294 | 24.4219294663 | 0.0830677873 | 2.0286756424 |
| R2 | 69 | 24.4219294663 | 0.3539410068 | 8.6439223023 |
| R3 | 910 | 24.4219294663 | 0.0268372851 | 0.6554182845 |
| R4 | 100 | 46.3846079186 | 0.4638460792 | 21.5153185176 |
| R5 | 204 | 94.6246001540 | 0.4638460792 | 43.8912497760 |
| R6 | 322 | 73.5688624611 | 0.2284747281 | 16.8086258504 |
| R7 | 99 | 23.3017637536 | 0.2353713510 | 5.4845676164 |
| R8 | 39 | 5.3127827902 | 0.1362251997 | 0.7237348968 |
| R9 | 507 | 50.2670987075 | 0.0991461513 | 4.9837893737 |
| R10 | 330 | 44.9543159173 | 0.1362251997 | 6.1239106654 |

ΣP = 110.859212925507 W = Vfuente × Itotal. La tabla usa los sentidos de corriente seleccionados en el ejemplo de la aplicación.

## Implementación y verificación de v1.3

Se conservaron literalmente once módulos anteriores: motor matemático, ejemplos, escape HTML, modelo de grupos, diagramas, constructor y sus pruebas. Se comparó el contenido de cada bloque y se registraron sus hashes SHA-256. Las mejoras se añadieron en presentación, persistencia y reporte dentro del mismo HTML.

### Ejecutado

- **100 comprobaciones internas correctas:** las 77 anteriores, incluidas las 25 matemáticas originales, más 23 nuevas. Estas últimas cubren orden natural, precisión visual, escala de lectura, nombres de grupos, equivalencia de reducciones con el motor, escala numérica extrema, copias, entradas incompletas, seguridad del texto y dibujo del reporte.
- **26 recorridos de interacción anteriores en DOM simulado:** añadir, seleccionar, editar, eliminar, deshacer, ejemplos, cambio de modo, nodos, relaciones, cancelación de cálculos y eventos de impresión. Todos correctos.
- **25 comprobaciones nuevas en DOM simulado:** zoom, etiquetas, tabla, procedimiento, SVG para impresión, guardado y recarga de ambos borradores, caracteres especiales, copia JSON, importación inválida, salida inmediata, copia corrupta, cuota agotada, almacenamiento local bloqueado y cálculo de 140 resistencias cuando el dibujo excede su límite. Todas correctas, sin errores JavaScript.
- **Correspondencia SVG ↔ nodos:** se reconstruyen las uniones desde los segmentos dibujados y se comparan los terminales con la red del motor. Se conservaron las pruebas anteriores y se verificó nuevamente la geometría después de aplicar los nombres visuales.
- **Revisión estática:** sintaxis JavaScript válida, IDs únicos, referencias de controles resueltas, cero recursos externos y ninguna solicitud de red. HTML/CSS/JavaScript puro, con estilos de impresión y diseño adaptable.
- **PDF de referencia:** Req = 515.257131027832 Ω, I = 0.463846079186219 A y P = 110.859212925506 W, coincidentes con la reducción independiente dentro de la precisión de doble coma flotante.

El DOM simulado se usó únicamente en herramientas de desarrollo bajo `work/`. Ninguna biblioteca de pruebas ni dependencia externa se incluyó en el HTML entregado.

### Pendiente de comprobación real

No se afirma una prueba visual en Chrome o Edge. La apertura local automatizada y el acceso posterior a la ventana de Chrome habían sido bloqueados por las políticas del entorno: el visor integrado no acepta `file://` y el control de aplicaciones no pudo identificar con suficiente confianza la URL del navegador. La apertura y recarga reales, las dimensiones visuales, el arrastre con ratón/táctil, las descargas y la paginación horizontal del PDF generado por Chrome/Edge siguen pendientes. Las pruebas de DOM no equivalen a estas pruebas en un navegador real.

Los eventos de impresión y las reglas de papel se comprobaron en código/DOM; no se generó ni inspeccionó un PDF real del navegador en esta revisión.

## Alcance y límites

- **Constructor rápido:** circuitos de dos terminales reducibles por serie y paralelo. El anidamiento es automático; una selección siempre tiene un alcance concreto. Los puentes se editan por nodos.
- **Modo avanzado:** una fuente ideal DC y resistencias positivas, lineales y finitas; admite puentes y redes que no se reducen por serie/paralelo. No admite múltiples fuentes, AC, capacitores, inductores ni elementos no lineales.
- **Precisión:** aritmética IEEE 754 de doble precisión, sin redondeos intermedios intencionales, con cuatro decimales predeterminados en la tabla o 12 cifras significativas opcionales. Las tarjetas mantienen ocho cifras significativas; el procedimiento muestra hasta diez. No se afirma exactitud simbólica infinita.
- **Validaciones conservadas:** rango relativo de resistencias hasta 10¹², comprobación de conservación con tolerancia relativa de 10⁻⁷, detección de valores inválidos, terminales incorrectos, autoenlaces, subcircuitos flotantes y resultados fuera del rango numérico.
- **Circuito abierto:** en avanzado, ramas conectadas por separado a los terminales producen Req = ∞, I = 0 y P = 0. En edición de grupos, varios bloques sueltos requieren definir primero su conexión y no se unen por defecto.
- **Cantidad variable:** no hay un número fijo de resistencias en el motor. La matriz es densa: tiempo aproximadamente cúbico y memoria cuadrática respecto a los nodos desconocidos. Se mantienen pruebas anteriores de 120 resistencias en serie y 200 en paralelo.
- **Diagramas muy extensos:** el constructor ofrece zoom y desplazamiento. Si alguna dimensión del plano supera 24000 unidades, remite a la edición detallada para conservar la legibilidad y mantiene disponible el cálculo. El mapa del modo avanzado conserva su alternativa textual cuando supera 10 nodos o 24 resistencias. En estos casos el reporte indica que no puede incluir el dibujo, pero conserva los datos y las ecuaciones. Un circuito muy extenso puede requerir ampliar el PDF para leer sus etiquetas.
- **Almacenamiento:** guardado automático local cuando está permitido. La copia JSON sirve para trasladar o respaldar ambos borradores. No hay sincronización en internet; no se persiste el historial de deshacer.
- **Repositorio:** `index.html` y `CircuitCalc.html` contienen la misma aplicación autónoma.


