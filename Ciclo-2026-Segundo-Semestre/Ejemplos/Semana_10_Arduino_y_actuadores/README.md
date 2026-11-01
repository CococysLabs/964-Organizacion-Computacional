# Arduino: contador ascendente de 4 bits y control de un puente H

## Descripción general

Este ejemplo integra una placa Arduino con dos circuitos digitales: un contador ascendente de 4 bits y un puente H para controlar un motor de corriente continua (DC).

Arduino cumple dos funciones principales:

- Genera la señal de reloj que sincroniza el funcionamiento del contador.
- Envía señales de control al puente H para determinar el sentido de giro del motor.

El montaje permite relacionar la programación de un microcontrolador con circuitos secuenciales, lógica combinacional, visualización de datos y control de actuadores.

## 1. Arduino como fuente de reloj del contador

En la parte superior del circuito se observa un contador construido con cuatro flip-flops tipo D y compuertas lógicas.

Cada flip-flop almacena un bit. En conjunto, los cuatro flip-flops representan un número binario de cuatro bits, por lo que el contador puede recorrer 16 estados diferentes, desde `0000` hasta `1111`.

Arduino proporciona los pulsos de reloj que permiten avanzar al contador:

- Arduino configura uno de sus pines digitales como salida.
- El programa genera pulsos alternando el nivel lógico bajo (`LOW`) y alto (`HIGH`).
- Cada flanco activo de la señal de reloj provoca la actualización de los flip-flops.
- La lógica combinacional determina el siguiente estado del contador para que incremente una unidad.
- Las cuatro salidas representan el valor binario actual.

La secuencia de conteo es:

`0000 → 0001 → 0010 → 0011 → ... → 1110 → 1111 → 0000`

Después de alcanzar `1111` (15 en decimal), el contador vuelve a `0000`, debido a que trabaja con cuatro bits.

## 2. Visualización del conteo

En la parte superior derecha se encuentra la etapa de decodificación y visualización mediante displays de siete segmentos.

Las salidas binarias del contador se utilizan para representar el valor contado en los displays, mediante los circuitos de decodificación correspondientes.

Esta etapa permite observar el resultado del conteo sin tener que interpretar directamente los cuatro bits. Es importante distinguir que los flip-flops almacenan el estado binario, mientras que los decodificadores adaptan esa información para encender los segmentos necesarios.

## 3. Arduino y programación

El programa de Arduino coordina el comportamiento del montaje. Para generar el reloj del contador, debe producir pulsos digitales con una frecuencia adecuada para que los cambios puedan observarse.

De forma conceptual, la generación de un pulso puede realizarse así:

```cpp
digitalWrite(pinReloj, HIGH);
delay(intervalo);
digitalWrite(pinReloj, LOW);
delay(intervalo);
```

El pin utilizado debe conectarse a la entrada de reloj del contador. El intervalo determina la velocidad del conteo: intervalos menores producen pulsos más frecuentes y, por lo tanto, un conteo más rápido.

Además, el programa configura las salidas que se conectan al puente H. De esta manera, una misma placa puede generar el reloj del contador y controlar el actuador.

## 4. Control de un motor DC mediante un puente H

En la parte inferior del circuito se muestra un puente H construido con cuatro transistores, resistencias de base y diodos de protección.

El motor se conecta entre los dos puntos medios de las ramas del puente. Al activar combinaciones específicas de transistores, se puede invertir la polaridad aplicada al motor y cambiar su sentido de giro.

El funcionamiento básico es el siguiente:

- **Giro en un sentido:** se activa un par de transistores ubicados en diagonal, de manera que la corriente atraviesa el motor en una dirección.
- **Giro en sentido contrario:** se activa el par diagonal opuesto, invirtiendo el sentido de la corriente a través del motor.
- **Paro:** se desactivan los transistores de conducción, según la configuración del puente.

Los diodos conectados en el circuito proporcionan caminos para las corrientes inducidas por el motor al conmutar, ayudando a proteger los transistores.

**Precaución:** nunca deben activarse simultáneamente los dos transistores de una misma rama del puente H, ya que se puede producir un cortocircuito entre la alimentación y tierra. También debe verificarse que los transistores, diodos y fuente de alimentación soporten la corriente requerida por el motor.

## 5. Relación entre el hardware y el software

En este montaje, Arduino no realiza internamente el conteo de cuatro bits: genera la señal de reloj y el circuito secuencial externo se encarga de actualizar el estado. De forma independiente, Arduino controla las entradas del puente H mediante señales digitales.

Esto permite identificar tres elementos importantes de un sistema digital:

- **Entradas y salidas digitales:** los pines de Arduino intercambian señales lógicas con los circuitos externos.
- **Sincronización:** los pulsos de reloj coordinan los cambios de estado de los flip-flops.
- **Control de actuadores:** las señales de Arduino gobiernan los transistores del puente H para controlar el motor.

La comunicación entre Arduino y estos circuitos se realiza mediante señales eléctricas digitales. No se necesita un protocolo serial como UART, I2C o SPI para las conexiones de control mostradas.

## Actividades de comprobación

1. ¿Cuántos estados diferentes puede representar un contador de cuatro bits?
2. ¿Qué sucede con el conteo después de llegar a `1111`?
3. ¿Qué función cumple Arduino en el contador?
4. ¿Cómo cambia el sentido de giro del motor al activar el par diagonal opuesto del puente H?
5. ¿Por qué no se deben activar simultáneamente los dos transistores de una misma rama?
6. ¿Qué sucede con la velocidad del conteo si se reduce el intervalo entre pulsos de reloj?

## Conclusión

El ejemplo demuestra cómo Arduino puede interactuar con circuitos digitales externos para generar señales de reloj y controlar actuadores. El contador de cuatro bits permite estudiar los circuitos secuenciales y la representación binaria, mientras que el puente H muestra cómo las señales digitales pueden controlar el sentido de giro de un motor DC. La integración de ambos circuitos permite comprender la relación entre programación, electrónica digital y control de hardware.
