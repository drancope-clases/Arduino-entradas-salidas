# Aprender y manejar las entradas y salidas con **Arduino**, usando **PlatformIO**
Si necesitas instalar **PlatformIO** en tu **VS Code**, puedes encontrar información en [este repositorio](https://github.com/drancope-clases/Instalar_Platformio).
<quote>En este repositorio encontrarás una explicación de cómo conectar un **pulsador** (*push button*) un un **LED** a tu arduino y cómo escribir las instrucciones en el lenguaje C++ para que funcionen.</quote>

## El **LED** y su resistencia para limitar la corriente.
Un **diodo emisor de luz** es un dispositivo que se comporta como un diodo normal, pero que emite luz al ser atravesado por la corriente. Para que esto ocurra hay que conectar su ánodo (pata larga) al voltaje positivo y el cátodo al negativo. El  efecto ocurrirá si el voltaje de la pila es superior al voltaje mínimo directo que necesita el LED para encenderse. Aproximadamente un voltio, pero depende del color del diodo.

![led básico](imagenes/pila_led.png)

Y a partir de ese voltaje, la corriente empieza a fluir, creciendo mucho aunque el voltaje sea muy poco superior al mínimo. ***El diodo se quema.***

**Es necesario limitar la corriente con una resistencia en serie**.

Ahora, si la resistencia es muy alta, la corriente será muy baja, y no vemos el diodo encendido. Si la resistencia es muy baja, pasa demasiada corriente, y se quema el diodo.

Si sabemos la corriente necesaria para encender el diodo, podremos ajustar el valor de la resistencia para que el encendido sea perfecto.

El voltaje que debe aguantar la resistencia es el voltaje de la pila menos el voltaje mínimo del diodo, que puede ser de aproximadamente 1 voltio, según el color del diodo. La corriente adecuada para un diodo está entre 10 y 20 miliamperios.

Por lo tanto, cuando conectemos nuestro arduino, que tiene aproximadamente 5V, la resistencia será: R = 4V / 15mA = 266ØΩ. Con una resistencia de 220Ω se encenderá un poco más brillante. Con una resistencia de 330Ω, ahorraremos un poco de energía aunque se vea un poco menos el LED.

## Conectando el LED al arduino.

El arduino UNO, el de la imagen, tiene dos filas de conectores para cables *Dupont*. En total, 32 puntos de conexión. Tiene también un conector de 6 pines macho, que no tendremos en cuenta, porque se usa para funciones especiales.

<img src="imagenes/Arduino-Uno-Pinout-1.png" width=450></img>
De los 32 puntos de conexión, 22 de ellos son entradas o salidas (se pueden configurar la mayoría) de datos. Las verdes, que son 14 son , solamente admiten encendido o apagado. Las 6 amarillas permiten la lectura de datos analógicos (o sea, valores reales de voltaje, comprendidos entre 0 y 5 voltios). Las dos grises de la zona superior derecha y las que comparten configuración con las verdes tienen asignadas, de manera preferente si necesitamos usarlas, tareas especiales de comunicación con determinados dispositivos.

Para conectar un LED (con su resistencia en serie) lo mejor es usar cualquiera de las verdes. Tenemos que decidir si conectamos el ánodo o el cátodo al *pin* verde, porque de una forma habrá que "encender" el pin para encender el diodo, y de la otra habrá que "apagar" el pin para lo mismo -esto se llama *lógica inversa*-.

Lo más cómodo para realizar el cableado de los componentes es usar una **protoboard**. 

(Foto real)

## El Botón y sus dos posibilidades de configuración.
