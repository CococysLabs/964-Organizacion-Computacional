# Ejemplo práctico: contadores digitales y control mediante puente H

Este ejemplo de la **semana 11** utiliza una simulación en **Proteus** para estudiar el funcionamiento de circuitos de conteo y un sistema de control. En el esquema se identifican dos bloques principales de conteo: uno **ascendente de 0 a 15** y otro **descendente de 10 a 0**. También aparecen bloques identificados como **CONTROLADOR CONTADOR** y **PUENTE H**.

## Contador ascendente de 0 a 15

El primer circuito representa una secuencia ascendente de 4 bits. Cada avance del contador incrementa el valor en una unidad hasta llegar a 15.

```text
Decimal: 0 → 1 → 2 → 3 → … → 14 → 15
Binario: 0000 → 0001 → 0010 → 0011 → … → 1110 → 1111
```

Como dispone de cuatro bits, puede representar **16 combinaciones**. En Proteus se debe observar el comportamiento de las salidas y la indicación numérica al recorrer los estados de la cuenta.

## Contador descendente de 10 a 0

El segundo bloque trabaja con una secuencia decreciente: comienza en 10 y disminuye hasta llegar a 0.

```text
Decimal: 10 → 9 → 8 → 7 → … → 1 → 0
Binario: 1010 → 1001 → 1000 → 0111 → … → 0001 → 0000
```

Este circuito permite analizar cómo cambia cada bit durante una cuenta regresiva y verificar la correspondencia entre la representación binaria y el valor mostrado.

## Controlador del contador

En la parte superior derecha del esquema aparece el bloque **CONTROLADOR CONTADOR**. Durante la simulación se deben identificar sus señales y verificar qué efecto tiene cada control sobre el funcionamiento de los contadores, de acuerdo con las conexiones realizadas en el proyecto.

## Puente H

La simulación también contiene un bloque identificado como **PUENTE H**. Un puente H es una disposición de conmutación utilizada habitualmente para controlar el sentido de la corriente a través de una carga, como un motor de corriente continua.

En este ejemplo conviene revisar sus entradas y salidas, reconocer las condiciones de control y comprobar mediante la simulación el comportamiento del circuito conectado. La captura por sí sola no permite confirmar una secuencia concreta de movimiento del motor.

## Archivo de simulación

Abrir [Ejemplo_practico.pdsprj](./Ejemplo_practico.pdsprj) en **Proteus** e iniciar la simulación. Localizar los bloques **Contador de 0 a 15**, **Contador de 10 a 0**, **CONTROLADOR CONTADOR** y **PUENTE H**.

Aplicar los estímulos correspondientes y observar las salidas de cada circuito. Registrar la secuencia de conteo y comprobar el efecto de los controles disponibles. El objetivo es relacionar las señales de entrada con los estados digitales y con el comportamiento del sistema de control.

> **Nota:** La imagen muestra estos bloques, pero no permite verificar por sí sola todos sus valores de configuración ni las conexiones funcionales completas. Las pruebas específicas deben realizarse en el archivo de Proteus.
