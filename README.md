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

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/Base3.png)

Plano de diseño de la base

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/herramienta1.png)

Vista 3D de la herramienta completa

![Diagrama de planta - lateral](https://github.com/EdoCuadros/Lab1/blob/main/herramienta2.png)

Plano de diseño de la herramienta
## Código en RAPID del módulo utilizado para el desarrollo de la práctica.
```
MODULE Module1
    CONST robtarget inicio:=[[459.502218959,16.972449376,378.090243512],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_10:=[[135.812,131.693,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_20:=[[135.812,145.21,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_30:=[[145.812,145.21,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_40:=[[146.582,132.358,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_50:=[[145.812,145.21,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_60:=[[155.812,145.21,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_70:=[[155.812,131.693,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_80:=[[155.812,128.29,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_90:=[[135.812,128.29,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_100:=[[136.104,118.144,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_110:=[[140.788,111.669,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_120:=[[150.836,111.588,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_130:=[[155.545,118.152,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_140:=[[155.812,125.194,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_150:=[[155.812,107.755,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_160:=[[143.041,107.755,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_170:=[[135.391,99.376,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_180:=[[137.376,93.112,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_190:=[[149.435,90.997,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_200:=[[155.812,90.997,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_210:=[[155.812,82.536,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_220:=[[135.812,89.295,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_230:=[[143.527,81.92,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_240:=[[135.812,72.885,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_250:=[[155.812,77.058,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_260:=[[155.812,68.306,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_270:=[[135.812,68.306,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_280:=[[143.154,63.314,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_290:=[[135.812,52.885,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_300:=[[144.321,56.556,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_310:=[[153,53.379,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_320:=[[155.812,60.267,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_330:=[[65.855,138.897,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_340:=[[76.277,148.573,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_350:=[[86.698,138.897,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_360:=[[76.277,129.205,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_370:=[[68.635,131.798,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_380:=[[67.46,127.309,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_390:=[[67.735,113.719,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_400:=[[72.533,111.377,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_410:=[[78.935,119.416,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_420:=[[82.889,119.805,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_430:=[[85.288,112.171,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_440:=[[84.996,93.403,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_450:=[[83.837,107.317,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_460:=[[68.61,107.325,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_470:=[[65.888,100.178,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,-1,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_480:=[[67.022,94.675,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_490:=[[66.277,87.568,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_500:=[[86.277,85.834,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_510:=[[76.277,76.977,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_520:=[[76.277,89.213,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_530:=[[76.277,76.977,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_540:=[[66.277,73.597,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_550:=[[66.277,66.612,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_560:=[[85.207,58.379,-10],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_570:=[[80.782,56.045,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_580:=[[74.785,59.853,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_590:=[[73.619,64.797,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_600:=[[66.277,59.238,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_610:=[[180,120,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_620:=[[160,180,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_630:=[[120,140,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_640:=[[80,170,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_650:=[[40,120,0],[0.475497026,-0.537456769,0.511913548,-0.472215331],[0,-1,-1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_660:=[[-211.443167567,-408.890540837,300],[0.471243517,-0.532844792,0.516712383,-0.476460164],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_670:=[[-220.016632808,-412.408354897,300],[0.471243517,-0.532844792,0.516712383,-0.476460164],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_680:=[[-212.505051377,-403.019553461,300],[0.471243517,-0.532844792,0.516712383,-0.476460164],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget Target_690:=[[-219.784825253,-399.484433617,300],[0.471243517,-0.532844792,0.516712383,-0.476460164],[-1,0,-2,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    PERS tooldata MyBridaToolTCP:=[TRUE,[[0,56.281,147.2],[0.855815998,0.517280366,0,0]],[0.3,[0,0,1],[1,0,0,0],0,0,0]];
    TASK PERS wobjdata WO_caja:=[FALSE,TRUE,"",[[0,0,0],[1,0,0,0]],[[471.941,-114.434,100],[1,0,0,0]]];
    !***********************************************************
    !
    ! M?dulo:  Module1
    !
    ! Descripci�n:
    !   <Introduzca la descripci�n aqu�>
    !
    ! Autor: Juandrosa
    !
    ! Versi�n: 1.0
    !
    !***********************************************************
    
    
    !***********************************************************
    !
    ! Procedimiento Main
    !
    !   Este es el punto de entrada de su programa
    !
    !***********************************************************
    PROC main()
        !Add your code here
        Eduar;
        Oscar;
        Decora;
    ENDPROC
    PROC Eduar()
        MoveL inicio,v1000,z100,MyBridaToolTCP\WObj:=wobj0;
        MoveJ Target_10,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_20,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_30,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_40,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_50,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_60,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_70,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_80,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_90,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_100,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_110,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_120,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_130,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_140,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_150,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_160,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_170,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_180,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_190,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_200,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_210,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_220,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_230,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_240,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_250,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_260,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_270,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_280,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_290,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_300,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_310,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_320,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ inicio,v100,fine,MyBridaToolTCP\WObj:=wobj0;
    ENDPROC
    PROC Path_10()

    ENDPROC
    PROC Oscar()
        MoveJ inicio,v100,fine,MyBridaToolTCP\WObj:=wobj0;
        MoveJ Target_330,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_340,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_350,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_360,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_370,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_380,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_390,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_400,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_410,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_420,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_430,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_440,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_450,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_460,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_470,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_480,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_490,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_500,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_510,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_520,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_530,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_540,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_550,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_560,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_570,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_580,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_590,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ Target_600,v100,fine,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ inicio,v100,fine,MyBridaToolTCP\WObj:=wobj0;
    ENDPROC
    PROC Decora()
        MoveJ inicio,v100,fine,MyBridaToolTCP\WObj:=wobj0;
        MoveL Target_610,v100,z10,MyBridaToolTCP\WObj:=WO_caja;
        MoveL Target_620,v100,z10,MyBridaToolTCP\WObj:=WO_caja;
        MoveL Target_630,v100,z10,MyBridaToolTCP\WObj:=WO_caja;
        MoveL Target_640,v100,z10,MyBridaToolTCP\WObj:=WO_caja;
        MoveL Target_650,v100,z10,MyBridaToolTCP\WObj:=WO_caja;
        MoveJ inicio,v100,fine,MyBridaToolTCP\WObj:=wobj0;
    ENDPROC
ENDMODULE
```
## Vídeo que contenga la simulación en RobotStudio así como la implementación de la práctica con los robots reales.
