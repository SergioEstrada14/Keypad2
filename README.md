# KEYPAD 

Es un dispositivo que agrupa varios pulsadores y permite controlarlos empleando un número de conductores inferior al que necesitaríamos al usarlos de forma individual. Podemos emplear estos teclados como un controlador para un autómata o un procesador como Arduino.

Estos dispositivos agrupan los pulsadores en filas y columnas formando una matriz, disposición que da lugar a su nombre. Tiene una disposición rectangular pura de 4×4.


![image](https://user-images.githubusercontent.com/124211869/223575866-1a191b82-5cee-4cfa-acc0-d5ed04a27552.png)


# ¿Cómo Funciona un Keypad?

Este teclado matricial 4×4 se encuentra formado por la matriz de pulsadores que se encuentran dispuestos en filas (L1, L2, L3 y L4), y las columnas (C1, C2, C3 y C4), esta organización es de acuerdo a reducir el número de pines requeridos para su conexión y programación. Los 16 botones necesitan sólo 8 pines del microcontrolador en lugar de 16 independientes. Para poder leer el botón que fue pulsado es necesario utilizar una técnica de barrido, no sólo leyendo el pin del microcontrolador.

<br>
En su aplicación con Arduino o cualquier otra plataforma de microcontroladores, el sistema de conectividad es simple, contamos con 8 pines digitales en total, además que puede trabajar con microcontroladores de 3.3 V y 5 V sin tener problema alguno. 
</br>
<br>
<br>

![image](https://user-images.githubusercontent.com/124211869/225752447-711b482d-2734-4703-9ab3-46d6c282ad29.png)


<br>
<br>

# Especificaciones del Keypad
* Contamos con 16 botones de organización matricial. (4 columnas, 4 filas).
* Teclado de tipo membranal.
* Máxima resistencia al agua y al polvo.
* Cuenta con un autoadhesivo en la parte trasera del teclado.
* El tiempo de rebote se encuentra en promedio de ≤5 ms.
* Máximo voltaje de operación: 24V DC.
* Máxima corriente de operación 30mA
* Resistencia de aislamiento de 100MΩ (@ 100 V).
* Voltaje de soporte del dieléctrico: 250 VRMS (@ 60Hz, por 1 min)
* Expectativa de vida útil : 1.000.000 de operaciones (pulsaciones).
* Dimensiones del teclado: 69*77mm
* Cable de cinta plana con longitud de 8.5 cm de largo aprox. (incluido con el conector)
* Conectores de tipo DuPont hembra de una fila y 8 contactos con separación estándar 0.1″ (equivalente a 2.54mm)
* Temperatura de operación óptima: 0 a 50 °C

<br>
<br>

# Simulación 

Simulación: https://wokwi.com/projects/358580157180679169

<br>
<br>

![image](https://user-images.githubusercontent.com/124211869/223578860-3cdaff96-ff08-4043-ba47-aae900f8c902.png)

<br>
<br>

# Código de ejemplo 

 ```Python

from machine import Pin
import utime
 
# Conexion los pines del teclado
colm=[1,2,3,4]
fils=[5,6,7,8]
 
# Establecer pin para las filas como salida
for x in range(0,4):
    fils[x]=Pin(fils[x], Pin.OUT)
    fils[x].value(1)
 
# Establecer columna como entrada
for x in range(0,4):
   colm[x] = Pin(colm[x], Pin.IN, Pin.PULL_UP)
 
# Crearción de un mapa entre los botones del teclado y los caracteres
key_map=[["D","#","0","*"],\
         ["C","9","8","7"],\
         ["B","6","5","4"],\
         ["A","3","2","1"]]
 
def Keypad4x4Read(cols,rows):
  for r in rows:
    r.value(0)
    result=[cols[0].value(),cols[1].value(),cols[2].value(),cols[3].value()]
    if min(result)==0:
      key=key_map[int(rows.index(r))][int(result.index(0))]
      r.value(1) 
      return(key)
    r.value(1)
 

print("--- Ready to get user inputs ---")
while True:
    key=Keypad4x4Read(colm, fils)
    if key != None:
      print("Botón presionado : "+key)
      utime.sleep(0.3) 
 ```
 
 
 # Resultados de simulacion 
 
 ![image](https://user-images.githubusercontent.com/124211869/223623341-51640b77-f77e-44e4-ba7a-5751359b654a.png)

