# Ejemplo práctico: operaciones aritméticas, comparación y visualización digital

Este ejemplo utiliza una simulación en **Proteus** para observar cómo se pueden combinar sumadores binarios, comparadores de magnitud y decodificadores de siete segmentos en un mismo circuito. La práctica permite modificar las entradas digitales y estudiar cómo se propagan los resultados hasta los displays.

## Suma de datos binarios

En la parte superior del circuito se utilizan integrados **74LS283**, que realizan sumas binarias de cuatro bits. Cada bloque recibe dos operandos y una entrada de acarreo, y produce cuatro bits de suma y un acarreo de salida.

```text
Entradas: A3 A2 A1 A0  +  B3 B2 B1 B0  +  C0
Salidas:  S3 S2 S1 S0  y  C4
```

Algunas salidas se conectan con otros bloques, formando distintas etapas de procesamiento. Es importante revisar el recorrido de las señales en el esquema para identificar qué valores llegan a cada sumador.

## Comparación de resultados

En la sección central se encuentran integrados **74LS85**, utilizados para comparar valores binarios de cuatro bits. Estos componentes disponen de tres salidas que indican el resultado de la comparación:

```text
A > B  → El primer valor es mayor.
A = B  → Los dos valores son iguales.
A < B  → El primer valor es menor.
```

En esta simulación, las conexiones permiten analizar las condiciones de comparación entre los datos de las distintas etapas. Se recomienda seguir las entradas y salidas etiquetadas en el esquema para comprender el comportamiento completo.

## Visualización en displays de siete segmentos

En la parte inferior aparecen tres integrados **74LS48** conectados a sus respectivos displays de siete segmentos. Su función es convertir una entrada **BCD de cuatro bits** en las señales necesarias para representar un dígito decimal.

```text
BCD 0000 → 0
BCD 0001 → 1
BCD 0010 → 2
...
BCD 1001 → 9
```

El **74LS48 no convierte por sí solo un número binario de varios bits a decimal**: recibe un dígito ya codificado en BCD. Por ello, para interpretar correctamente los números mostrados, hay que verificar qué señales alimentan las entradas de cada decodificador.

## Archivo de simulación

Abrir [Ejemplo_practico.pdsprj](./Ejemplo_practico.pdsprj) en **Proteus** e iniciar la simulación. Utilizar los interruptores de la parte inferior izquierda para modificar las entradas digitales y observar los cambios en las salidas de los sumadores, comparadores y displays.

Para realizar la práctica, se recomienda:

1. Identificar los **74LS283** de la parte superior y seguir sus conexiones de entrada y salida.
2. Observar los **74LS85** de la sección central y determinar qué valores comparan.
3. Revisar los **74LS48** y los tres displays de siete segmentos.
4. Cambiar una entrada a la vez y anotar los resultados observados.
5. Repetir las pruebas con distintas combinaciones para relacionar las entradas binarias con el comportamiento del circuito.

El propósito del ejemplo es comprender la integración de **operaciones aritméticas, comparaciones lógicas y visualización digital** dentro de un sistema combinacional.
