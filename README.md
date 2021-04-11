# Freestyle-Tuning

Este repositorio es una adaptación del repositorio de Betaflight - Freestyle Tuning Principles.  
Authors: Elia Palme, Daniel Appel, Hugo Chiang(DusKing1), Mark Spatz and co.  

La intención de este repositorio es proporcionar pautas sencillas para configurar Betaflight para un modo de vuelo Freestyle.  
Esta guía tiene como objetivo proporcionar principios  simples y sugerencias de ajuste para aprovechar Betaflight al máximo para el freestyle.  

Este repositorio esta en constante edición y se recomienda mirar el hilo principal:  
https://github.com/betaflight/betaflight/wiki/Freestyle---Tuning-Principles  

## Principios y Atributos  

El Freestyle se trata principalmente de un vuelo acrobático suave y preciso.  

Para lograr tales objetivos, un quad de Freestyle debe ajustarse teniendo en cuenta los siguientes principios:  

1 - Optimizado para suavidad en baja latencia y control nítido.  
Los pilotos de freestyle tienden a preferir un quad más suave y "suelto" a uno extremadamente reactivo  Principalmente porque ayuda a suavizar la microcorrección y hace que el vuelo parezca más orgánico y fluido.  

2 - Optimizado para comportarse de forma predictiva y coherente.
La consistencia ayuda a los pilotos a desarrollar la memoria muscular y sentir el quad, por lo tanto, ganar confianza y precisión. Uno de los mejores pilotos, Mr. Steel es conocido por ejecutar la misma configuración durante varios años y rara vez realiza cambios en ella.

Con los principios anteriores en mente, podemos extraer tres atributos para los que deberíamos optimizar:

- Retención de actitud   
La retención de actitud es la capacidad de la nave para mantener su trayectoria y comportarse como se espera. Un cuadricóptero con buena actitud tiene un propwash bajo, no sufre de vibraciones de frecuencia media o alta y lucha eficientemente contra fuerzas externas como el viento y la gravedad mientras rastrea el punto de ajuste de cerca (sigue las entradas de la palanca con precisión). La actitud proporciona suavidad.  

- Previsibilidad   
La previsibilidad es la capacidad del piloto para estimar cómo se comportará la nave en función de las condiciones ambientales y las entradas de palanca proporcionadas. Cuanto más predecible sea el comportamiento del quad, más precisión y confianza ganará el piloto.  

- Capacidad de respuesta   
La capacidad de respuesta es la capacidad de la nave para rastrear el punto de ajuste (entradas de palanca) lo más cerca posible. Un quad receptivo tiene una latencia muy baja y se siente conectado.  

En teoría, los tres atributos son igualmente importantes en la práctica, un aumento de la capacidad de respuesta podría afectar la capacidad del piloto para volar de manera uniforme y constante.

Por lo tanto, se recomienda comprometer la capacidad de respuesta para que el quad se comporte de manera predictiva y consistente.  

## Betaflight Tune  
Nota importante: Los valores de ajuste sugeridos están pensados para una configuración típica de 5 ", ya sea 6S con motores [1600 a 1800] KV o 4S con motores [2400-2600] KV.

### Compensación VBat Sag
Esta característica tiene como objetivo proporcionar coherencia en la respuesta motora durante todo el vuelo.   
Podeis ver las notas en detalle en https://github.com/betaflight/betaflight/wiki/4.2-Tuning-Notes#dynamic-battery-sag-compensation.   

Al habilitar VBat Sag Compensation, la nave volará de manera más consistente y predictiva.  
Si planea utilizar esta función, es fundamental que la habilite antes de realizar el ajuste PID.   

Configuración para estos valores en un 5":  
VBat Sag Period (vbat_sag_lpf_period)	   **200 (20 second)**    
VBat compensation                   	   **40-70**    

El uso de valores más altos de VBatSagCompensation, como 100, reducirá la caída de la batería y dará como resultado una respuesta muy consistente desde el inicio de un vuelo hasta el final del vuelo. El riesgo inherente de este enfoque es que, particularmente para configuraciones eficientes de batería 6S, el rendimiento del vuelo pasará de nominal a batería cayendo por debajo de 3,0 V / celda muy rápidamente. Por esta razón, muchos pilotos preferirían ejecutar valores más bajos si están acostumbrados a usar la respuesta de caída de la batería para medir cuándo es prudente aterrizar.  
Debido a la química de las baterías de polímero de litio, volar por debajo de 3,0 V por celda da como resultado un recubrimiento de litio en el ánodo, lo que reduce permanentemente tanto la capacidad como la capacidad de descarga máxima de la batería. Esto debe evitarse en la medida de lo posible.

### PID  

Los PID son importantes en el ajuste del quad, con el ajuste de los PID podemos lograr una buena respuesta del quad.  

D es el término PID más importante para lograr un vuelo suave, D ayuda a minimizar el apoyo y a deshacer cualquier movimiento de los quads. Los quads de estilo libre tienden a usar ganancias de D más altas. 

**Nota**: Aunque en el repositorio los autores hablan de empezar subiendo la D hay que tener en cuenta que un valor de D excesivo podria dañar nuestros motores por sobrecalentamiento.  

Para contrarrestar una ganancia D más alta de lo normal, P también debe aumentarse.  

Un enfoque simple para ajustar P y D es establecer una ganancia D deseada (por ejemplo, 45) y aumentar lentamente P lo más alto posible sin producir ningún rebote en los giros y vueltas (consulte el video de UAV Tech).  

https://www.youtube.com/watch?v=qK5APBg76AU  

El término I es generalmente lo suficientemente bueno por defecto, sin embargo, si el quad no tiene un movimiento solido, aumentar la ganancia podría mejorar la actitud general.  

**Valores sugeridos por betaflight:** Quad de 5"  
======P======I======D=====      
Rol===60-70==90-100==40-50====   
Pitch==06-70==90-100==40-50====  
Yaw===30-40==90-100==0=======   
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX   

===============================EN DESARROLLO=========================================


https://theuavtech.com/presets/



















