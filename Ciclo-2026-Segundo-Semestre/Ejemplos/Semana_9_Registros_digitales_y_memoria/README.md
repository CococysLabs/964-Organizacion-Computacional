# Registros, transferencia de datos y memoria RAM

## Descripción del ejemplo

El circuito mostrado está construido con flip-flops tipo D (integrados 7474) y permite observar distintas formas de organizar el almacenamiento y la transferencia de información digital. Se divide en tres secciones: un registro de cuatro bits con entradas paralelas, un registro de desplazamiento y una transferencia de información entre dos registros.

> **Importante:** Los flip-flops tipo D almacenan un bit. En condiciones normales, la salida `Q` toma el valor presente en `D` cuando ocurre el flanco activo del reloj. El estado almacenado se mantiene hasta el siguiente flanco activo, salvo que se utilicen las entradas asíncronas de preset o clear.

## 1. Registro con entrada y salida en paralelo

La sección de la izquierda utiliza cuatro flip-flops tipo D. Cada flip-flop recibe un bit independiente, por lo que los cuatro bits pueden presentarse simultáneamente en sus entradas.

- Las entradas individuales representan los bits que se desean almacenar.
- Los cuatro flip-flops comparten la señal de reloj.
- Cuando ocurre el flanco activo del reloj, cada flip-flop almacena el valor de su entrada `D`.
- Las salidas permiten consultar los bits almacenados de manera simultánea.

Este comportamiento corresponde a un registro de entrada paralela y lectura paralela (PIPO, *Parallel-In Parallel-Out*). Es útil cuando se necesita almacenar temporalmente una palabra binaria completa y disponer de todos sus bits al mismo tiempo.

## 2. Registro de desplazamiento

La sección central también utiliza cuatro flip-flops tipo D, pero sus conexiones son diferentes: la salida de una etapa se conecta a la entrada de la siguiente.

- Un dato serial ingresa por la primera etapa.
- Todos los flip-flops reciben una señal de reloj común.
- En cada flanco activo, el dato almacenado en una etapa pasa a la siguiente.
- Las salidas de las etapas permiten observar los bits que se encuentran almacenados en el registro.

Este circuito representa un registro de desplazamiento de entrada serial y salidas paralelas (SIPO, *Serial-In Parallel-Out*). Permite convertir una secuencia de bits recibida uno por uno en varios bits disponibles simultáneamente.

Por ejemplo, si se ingresan los bits `1`, `0`, `1` y `1`, cada pulso de reloj desplaza la información una posición. El contenido final depende del orden de entrada y de la cantidad de pulsos aplicados.

## 3. Transferencia de datos entre dos registros

La sección de la derecha muestra dos registros de cuatro bits: **Registro A** y **Registro B**.

- Las cuatro entradas del Registro A permiten establecer una palabra binaria.
- Los flip-flops del Registro A almacenan esos bits cuando reciben el flanco activo de reloj.
- Las salidas `Q` del Registro A están conectadas a las entradas `D` correspondientes del Registro B.
- Cuando se aplica el flanco activo de reloj al Registro B, este captura los valores que recibe desde el Registro A.
- Las salidas del Registro B muestran la palabra transferida.

Esta conexión permite estudiar cómo se transfiere una palabra binaria entre dos registros. El Registro A funciona como origen de los datos y el Registro B como destino. La transferencia ocurre mediante las señales de reloj, no simplemente por conectar las salidas de un registro con las entradas del otro.

## Relación con la memoria RAM

Un registro y una memoria RAM comparten la función básica de almacenar información binaria, pero tienen diferencias importantes:

- Un registro se construye con flip-flops y normalmente almacena una cantidad pequeña y fija de bits.
- La memoria RAM almacena una mayor cantidad de información organizada en posiciones direccionables.
- Para leer o escribir en RAM se selecciona una dirección; en los registros del ejemplo, los bits se encuentran en etapas definidas por el circuito.
- La RAM permite acceder a distintas posiciones mediante señales de dirección y control.

Los registros son fundamentales dentro de un procesador y otros sistemas digitales porque mantienen temporalmente datos, direcciones e instrucciones que se están utilizando. También pueden servir como etapas intermedias para transferir información entre diferentes unidades.

## Actividades de comprobación

1. En el primer circuito, modifica las entradas y aplica un pulso de reloj. ¿Qué valores quedan almacenados?
2. En el segundo circuito, ingresa una secuencia de cuatro bits, aplicando un pulso de reloj por cada bit. ¿Cómo cambia el contenido después de cada pulso?
3. En el tercer circuito, establece una palabra en el Registro A y observa sus salidas. Después, aplica el pulso de reloj correspondiente al Registro B. ¿Qué información queda almacenada en B?
4. Explica una diferencia entre almacenar datos en un registro y almacenarlos en una memoria RAM.

## Conclusión

Los tres circuitos permiten comparar el almacenamiento paralelo, el desplazamiento de datos en serie y la transferencia de información entre registros. En todos los casos, los flip-flops tipo D conservan bits de información y utilizan el reloj para sincronizar su actualización. Estos principios constituyen una base para comprender el funcionamiento de los registros internos de un computador y la organización de las memorias.
