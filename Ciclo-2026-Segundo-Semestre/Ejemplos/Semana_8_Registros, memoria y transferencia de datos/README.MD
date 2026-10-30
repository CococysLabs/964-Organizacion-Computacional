# Ejemplo práctico: registros, memoria y transferencia de datos

Este ejemplo de la semana 8 utiliza una simulación en Proteus para mostrar cómo **guardar un dato en un registro paralelo, compararlo con una entrada y utilizar el resultado de la comparación para contar eventos**. El circuito representa una contraseña de 4 bits y lleva el conteo de los intentos incorrectos.

## Almacenamiento en paralelo

El bloque **GUARDAR CONTRASEÑA** utiliza cuatro flip-flops tipo D para almacenar los cuatro bits de la contraseña. Cada bit tiene su propia entrada y todos comparten la señal de reloj de guardado, por lo que el dato se carga en paralelo.

Una vez guardado, el registro conserva el valor en sus salidas para utilizarlo en la comparación, aunque cambien los valores de las entradas de guardado. Un nuevo pulso de guardado permite actualizar la contraseña almacenada.

## Comparación de la contraseña

En el bloque **INGRESAR CONTRASEÑA** se establece el dato que se desea comprobar. El bloque **COMPARADOR CONTRASEÑA** compara esos cuatro bits con los del registro y, al activar la señal de ingreso, genera el evento correspondiente:

- **Contraseña correcta:** el dato ingresado coincide con el almacenado y se activa la señal de validación.
- **Contraseña incorrecta:** los datos son diferentes y se genera un pulso para el contador de errores.

Por ejemplo, si el registro guarda `1010`, ingresar `1010` produce una coincidencia; ingresar `1001` produce un evento de error.

## Conteo de eventos

El bloque **CONTADOR ERRORES** recibe los pulsos de los intentos incorrectos. Cada evento incrementa el contador y su valor se muestra en un display de siete segmentos. Cuando la contraseña es correcta, la señal de validación reinicia el conteo de errores.

Así se relacionan el almacenamiento de un dato, la comparación mediante lógica combinacional y el conteo mediante un circuito secuencial.

## Archivo de simulación

Abrir [Ejemplo_practico.pdsprj](./Ejemplo_practico.pdsprj) en Proteus e iniciar la simulación:

1. Establecer los cuatro bits en **GUARDAR CONTRASEÑA** y aplicar un pulso de guardado.
2. Configurar los cuatro bits en **INGRESAR CONTRASEÑA** y aplicar un pulso de ingreso.
3. Probar valores distintos al almacenado y observar cómo aumenta el contador de errores.
4. Ingresar el valor correcto y observar la validación y el reinicio del contador.
