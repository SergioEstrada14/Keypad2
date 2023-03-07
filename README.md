# KEYPAD 

Es un dispositivo que agrupa varios pulsadores y permite controlarlos empleando un número de conductores inferior al que necesitaríamos al usarlos de forma individual. Podemos emplear estos teclados como un controlador para un autómata o un procesador como Arduino.

Estos dispositivos agrupan los pulsadores en filas y columnas formando una matriz, disposición que da lugar a su nombre. Tiene una disposición rectangular pura de 4×4.


![image](https://user-images.githubusercontent.com/124211869/223575866-1a191b82-5cee-4cfa-acc0-d5ed04a27552.png)


# ¿Cómo Funciona un Keypad?

Este teclado matricial 4×4 se encuentra formado por la matriz de pulsadores que se encuentran dispuestos en filas (L1, L2, L3 y L4), y las columnas (C1, C2, C3 y C4), esta organización es de acuerdo a reducir el número de pines requeridos para su conexión y programación. Los 16 botones necesitan sólo 8 pines del microcontrolador en lugar de 16 independientes. Para poder leer el botón que fue pulsado es necesario utilizar una técnica de barrido, no sólo leyendo el pin del microcontrolador.
