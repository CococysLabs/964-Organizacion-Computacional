# Ejemplo de flip flops D, JK y T con Proteus

Este proyecto es un ejemplo de simulación en Proteus para mostrar el funcionamiento de los flip flops tipo D, JK y T. Los flip flops son circuitos de almacenamiento de estado: guardan un bit y solo cambian su salida Q cuando llega el flanco de la señal de reloj (CLK).

## Flip flop D

El flip flop D (Data) copia en la salida Q el valor de la entrada D en el flanco de reloj. Se usa para guardar un dato tal como llega.

| D | Q (siguiente) |
|---|---------------|
| 0 | 0             |
| 1 | 1             |

## Flip flop JK

El flip flop JK tiene dos entradas, J y K. Puede mantener el estado, ponerlo en 0, ponerlo en 1 o invertirlo.

| J | K | Q (siguiente) | Acción      |
|---|---|---------------|-------------|
| 0 | 0 | Q             | Mantiene    |
| 0 | 1 | 0             | Reset       |
| 1 | 0 | 1             | Set         |
| 1 | 1 | Q'            | Invierte    |

## Flip flop T

El flip flop T (Toggle) invierte su salida cuando T vale 1 y la mantiene cuando T vale 0. Se puede obtener a partir de un JK uniendo J y K en una sola entrada.

| T | Q (siguiente) |
|---|---------------|
| 0 | Q             |
| 1 | Q'            |

## Que observar en la simulacion

Al cambiar las entradas D, J, K y T en Proteus y aplicar pulsos de reloj, se observa que la salida Q solo cambia en el flanco de CLK y que el valor se mantiene guardado entre pulsos. Así se ve cómo cada tipo de flip flop almacena y modifica un bit de estado.
