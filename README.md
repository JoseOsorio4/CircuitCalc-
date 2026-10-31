# CircuitCalc

CircuitCalc es una aplicación educativa para construir y resolver circuitos de resistencias con una fuente de corriente continua. Funciona sin internet, servidor ni instalación: todo el HTML, CSS y JavaScript de la aplicación está en un único archivo.

## Abrir y usar

1. Descarga [`CircuitCalc.html`](CircuitCalc.html) y ábrelo con doble clic en un navegador moderno. [`index.html`](index.html) contiene la misma aplicación.
2. En el **constructor rápido**, introduce el voltaje y el valor de R1. Selecciona una resistencia o un grupo del esquema y pulsa **Añadir en serie** o **Añadir en paralelo**. También puedes usar **Edición detallada** para agrupar, mover, ordenar o eliminar componentes.
3. Pulsa **Calcular mi circuito** para obtener resistencia equivalente, voltaje, corriente y potencia totales, además de los valores de cada resistencia. **Ver procedimiento** explica las reducciones; las ecuaciones de Kirchhoff están en una sección avanzada.
4. Usa **Imprimir / Guardar PDF** para generar un reporte con tabla y esquema. **Guardar copia** descarga un JSON con tus borradores; **Abrir copia** lo recupera.

El **modo avanzado** permite conectar resistencias mediante nodos para resolver puentes y otras redes que no se pueden expresar como grupos simples en serie y paralelo. Al pasar de un modo a otro, los borradores se conservan por separado.

## Ejemplos incluidos

El selector contiene circuitos en serie, paralelo y mixtos de diversos tamaños, el ejercicio de 10 resistencias del PDF, su variante con R1 = 244 Ω, un puente y el circuito **estrella–delta de 13 resistencias** de los compañeros. En este último, R11 = **7.9 kΩ** y la resistencia equivalente es aproximadamente **2.855652790 kΩ**. El dibujo recibido no especifica el voltaje: el ejemplo usa **1 V de referencia**, editable en el modo avanzado. La resistencia equivalente no depende de ese voltaje.

## Cómo calcula

El constructor rápido transforma los grupos anidados en una red de nodos. Un motor de análisis nodal resuelve las leyes de Kirchhoff mediante eliminación gaussiana con pivoteo parcial y calcula voltajes, corrientes y potencias con la ley de Ohm. El programa comprueba la conservación de corriente y potencia. La reducción serie/paralelo se presenta como explicación del resultado del modo fácil. El redondeo de la tabla solo afecta a la presentación.

El motor admite resistencias positivas y finitas y una fuente ideal de corriente continua. No modela corriente alterna, varias fuentes, capacitores, inductores ni componentes no lineales.

## Tecnología y pruebas

- HTML, CSS, SVG y JavaScript puro; sin frameworks ni dependencias de ejecución.
- El archivo se puede usar directamente desde el disco, sin `localhost`.
- El guardado automático utiliza el almacenamiento local del navegador cuando está disponible. Para mover un circuito a otra computadora, comparte el HTML **y** el JSON de **Guardar copia**.
- El botón **Ejecutar pruebas matemáticas**, en **Detalles avanzados**, ejecuta las 100 comprobaciones integradas. La guía [`docs/VERIFICACION.md`](docs/VERIFICACION.md) recoge el alcance de las verificaciones y el análisis del PDF original.

## Abrir el proyecto en IntelliJ IDEA

1. En IntelliJ IDEA, selecciona **File → Open** y elige la carpeta descargada o clonada de este repositorio.
2. En el panel **Project**, abre `index.html` para leer o editar el código.
3. Para usar la aplicación, abre `index.html` o `CircuitCalc.html` en un navegador. También puedes hacer clic derecho sobre el archivo en IntelliJ IDEA y elegir **Open in Browser**, si esa opción aparece en tu instalación.

No hace falta crear una configuración de ejecución, instalar paquetes ni iniciar un servidor.

