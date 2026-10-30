# Ejemplo práctico: conteo digital y control de secuencias

Este ejemplo de la semana 7 utiliza una simulación en Proteus para mostrar cómo los circuitos secuenciales realizan un conteo a partir de pulsos de reloj. El enfoque principal está en dos contadores de 4 bits: uno ascendente de **0 a 15** y otro descendente de **10 a 0**.

## Contador ascendente de 0 a 15

Permite observar la secuencia de conteo ascendente y su representación en binario. Con cada pulso de reloj, el valor aumenta una unidad:

```text
Decimal: 0 → 1 → 2 → … → 14 → 15
Binario: 0000 → 0001 → 0010 → … → 1110 → 1111
```

Los cuatro bits permiten representar los 16 valores comprendidos entre 0 y 15. Este circuito ilustra cómo cambian las salidas y cómo se relaciona cada combinación binaria con el número contado.

## Contador descendente de 10 a 0

Presenta una secuencia de conteo en sentido descendente. Con cada pulso de reloj, el valor disminuye una unidad dentro del recorrido de 10 a 0:

```text
Decimal: 10 → 9 → 8 → … → 1 → 0
Binario: 1010 → 1001 → 1000 → … → 0001 → 0000
```

Este circuito permite estudiar el cambio de estados en una cuenta regresiva y la lógica necesaria para obtener la secuencia indicada.

## Archivo de simulación

Abrir [Ejemplo_practico.pdsprj](./Ejemplo_practico.pdsprj) en Proteus e iniciar la simulación. Localizar los bloques **CONTADOR ASCENDENTE 0-15** y **CONTADOR DESCENDENTE 10-0**, y observar sus salidas conforme se aplican los pulsos de reloj.

La simulación también contiene otros circuitos de apoyo, como la conversión de binario a BCD y la visualización con displays de siete segmentos. El propósito de este ejemplo se centra en comprender las dos secuencias de conteo y su representación binaria.
