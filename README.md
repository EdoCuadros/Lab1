# Laboratorio 1 de Robótica
Integrantes:

***Eduardo Cuadros Montealegre***

***Oscar Javier Restrepo***

## Introducción
En la industria de alimentos, en especial panadería, quieren mejorar su proceso de producción. Ellos consideran que
la decoración de las tortas puede ser un punto a ser ejecutado por robots. En los siguientes links se puede observar
diferentes automatización de decoración de tortas con robots.

Inspirados en los vídeos anteriores, y considerando las limitaciones del laboratorio se propone hacer la decoración
de una torta virtual. Es decir. Sobre una superficie plana bien sea redonda o rectangular, escribir 5 primeras letras
de los nombres de cada uno de los integrantes del grupo y una decoración a su gusto. En este caso se desea generar
los paths o los movimientos de robot necesarios para representar las letras y la decoración. Se deben tener en cuenta
las siguientes restricciones:

- El tamaño de la torta es para 20 personas
- Las trayectorias a desarrollar deberán realizarse en un rango de velocidades entre 100 y 1000.
- La zona tolerable de errores máxima debe ser de z10.
- El movimiento debe partir de una posición home especificada (puede ser el home del robot) y realizar la
trayectoria de cada palabra y decoración con un trazo continuo. El movimiento debe finalizar en la misma
posición de home en la que se inició.
- La decoración de la torta debe ser realizada sobre una papel. El papel puede ser fijado sobre una superficie
horizontal o sobre una plano inclinado.
- Los nombres deben estar separados.

## Descripción de la solución planteada.
Se trabaja sobre una torta de forma de paralelepípedo, cuyas dimensiones son 20 cm x 20 cm x 15 cm. 

Se diseñó un efector o herramienta final para el manipulador de tal forma que pueda ser posicionado sobre el manipulador y que contenga el marcador con el que se escribirá sobre una hoja en blanco que simulará la superficie de la torta.

Se diseña una caja en Inventor sobre la que se colocan los nombres EDUAR y OSCAR, ambos en alto relieve. Esta caja se importa al RobotStudio y se pueden trazar una secuencia de puntos sobre las letras en alto relieve.

Con RobotStudio importamos y configuramos la herramienta previamente diseñada en Inventor. 

Se crean tres path. Dos para los nombres y otro para la decoración. Se validan las indicaciones de uso de las instrucciones MoveL y MoveJ, así como el de las velocidades y el zoom. 

Posteriormente se sincroniza con Rapid. 

Se montan los archivos al robot y se procede con la calibración de la herramienta, la selección del workobject y el posterior trazado sobre el papel.

## Diagrama de flujo de acciones del robot

![Diagrama de flujo](https://github.com/EdoCuadros/Lab1/blob/main/Flujo.png)

## Plano de planta de la ubicación de cada uno de los elementos.
![Diagrama de planta - superior](https://github.com/EdoCuadros/Lab1/blob/main/planta1.png)
![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/planta2.png)
## Descripción de las funciones utilizadas.
Para la generación de las trayectorias es emplearon las funciones:
- MoveL. Traza una línea entre dos puntos. 
- MoveJ. Traza una línea entre dos puntos pero el software selecciona la trayectoria más conveniente
- v100. Velocidad de la herramienta.
- zfine, z10. Zona tolerable de errores.
La selección del objeto de trabajo (caja) fue a través del workobject (WO) identificado con tres puntos. Sobre este WO se ubicaron los diferentes puntos que son parte de las trayectorias para los nombres y para la decoración


## Diseño de la herramienta.
La herramienta se encuentra dividida en 3 partes. 
![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/base1.png)

Base. Parte que une la herramienta al robot

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/base3.png)

Plano de diseño de la base

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/herramienta1.png)

Vista 3D de la herramienta completa

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/herramienta2.png)

Plano de diseño de la herramienta
## Código en RAPID del módulo utilizado para el desarrollo de la práctica.
## Vídeo que contenga la simulación en RobotStudio así como la implementación de la práctica con los robots reales.
