# Actividad 3  
Si bien vi el video de la primera actividad, y logré entender (más o menos) el tema del motion 101 propuesto en la segunda actividad, mi evidencia realmente comienza aquí, con un par de experimentos que hice jugando con el programa de Particle Life:  
<img width="1038" height="666" alt="image" src="https://github.com/user-attachments/assets/0f1c2835-ac6d-41ec-a4c7-037e7b89615d" />  
<img width="796" height="635" alt="image" src="https://github.com/user-attachments/assets/ec496b18-ee79-420b-8869-4c365ceb99af" />  
<img width="174" height="202" alt="image" src="https://github.com/user-attachments/assets/6c96d7c1-0eb2-4b28-90d8-658a145d1905" />  
Esta última, me pareció muy interesante, pues esa serpiente se quedó empeñada en pegarle a ese grupito de partículas azules. Si bien no he comenzado a planear el reto de diseño, siento que puede ser útil explorar este comportamiento para mostrar algo.  
<img width="212" height="209" alt="image" src="https://github.com/user-attachments/assets/6c4f9d62-b9c4-4ffc-8575-5fd89287dc4d" />  
Aquí es solo la matriz de uno de los presets del programa, pero me puede ayudar a explicar el comportamiento del ejemplo anterior.  

# Actividad 4  
Para esta quiero hacer algo simple. No tuve muchas ideas, entonces la mejor la dejo para el reto de diseño de la actividad 5.  
Mi idea aquí es representar un juego, donde dos equipos (naranja y azul) persiguen unos puntos morados durante un tiempo. Al finalizar, el que tenga más puntos morados a su favor gana y comenzará a cazar al otro con el apoyo de las partículas moradas que tuvieran alrededor en ese momento.  
1. **Intención:** Quiero una idea de diversión y tensión simultáneamente, como quien juega al escondite con los amigos.
2. **Entidades:** Existen dos equipos y los puntos (tanto literal como en el contexto de un juego).
3. **Relaciones:** Al principio los dos equipos son indiferentes entre sí y solo buscarán acercarse a los puntos morados. En la fase de caza, el equipo ganador seguirá al equipo perdedor hasta que estén muy lejos o hasta que explote el computador.
4. **Entradas:** El sistema lo alimentan tanto una semilla como el tiempo de juego. La semilla aleatoria (determinada con la función random, la cual depende del reloj interno del computador) decide dónde se instancian los puntos, mientras que el tiempo es el límite para que uno de los dos equipos gane.
5. **Estado:** No sé jaja
6. **Invariantes:** Sencillamente las relaciones entre las partículas son lo que distinguen este sistema. De hecho, al inicio de cada partida, las partículas crean un patrón tal que así:  
<img width="677" height="525" alt="image" src="https://github.com/user-attachments/assets/7195a5d0-3125-4fa0-9c76-f336ae251c6d" />

7. **Variabilidad:** La posición inicial de las partículas afecta DEMASIADO al resultado final. Casi siempre se terminaban quedando quietas al cabo de un rato, algunas veces el equipo ganador se quedaba correteando al perdedor indefinidamente, y otras pocas veces el juego terminaba con el equipo ganador infectando a los restantes del perdedor.
8. **Curaduría y reflexión:** Sirvió saber que el comportamiento de las partículas puede ser cambiado con el tiempo, y me pareció bastante interesante el "final abierto" en el que se quedan correteando al pobre perdedor. Esto último me sirve como posible resultado para mi idea del reto de diseño.

# Reto de diseño
Mi idea aquí era representar una guerra, por lo que partí con tres reglas para el comportamiento de 5 bandos:  
1. Hay dos equipos que siempre se atraen.
2. Hay dos que tienen un comportamiento aleatorio que cambia en cada ejecución.
3. El bando restante va a perseguir al que esté más cerca.
Sin embargo, el resultado que tenían solo estas tres reglas, si bien era interesante en cuanto a comportamiento, no terminaba de encajar con el concepto.
<img width="661" height="528" alt="image" src="https://github.com/user-attachments/assets/7a097585-eb7a-4d1e-8041-9f10318c3651" />

Para esto, decidí implementar unas reglas generales, que permitieran evidenciar mejor que esto era una guerra y no un simple tropel:
1. Si dos bandos enemigos se cruzan, se empiezan a restar vida.
2. Los bandos se pueden separar en grupos de máximo 30 partículas a voluntad del usuario (con un clic separa un enfrentamiento).
3. El bando que se movía a conveniencia ahora va a servir como kamikaze, suicidándose y quitando la mitad de la vida de quien tocan.
4. Las partículas muertas quedan pintadas en otro color en el canvas, lo que refuerza la idea de guerra y simboliza que están peleando sobre los cadáveres de quienes pelearon antes.
Esto me dio un resultado que me gustó un poco más, y que era más coherente con mi idea:  
<img width="666" height="532" alt="image" src="https://github.com/user-attachments/assets/06329c96-c4bf-4366-9e62-b64496e785ef" />

Sin embargo, para que terminara de cuadrar la idea, era necesario que las partículas de un mismo color aparecieran siempre juntas. De lo contrario, pareciera una pelea muy desordenada donde los bandos se arman sobre la marcha.
Ahora bien, el concepto iba por buen camino. Si bien cada ejecución es corta, creo que se entiende lo que está pasando (o al menos es coherente con el concepto de "guerra"). Sin embargo, esto mostró un nuevo problema, y era la quietud provocada por un sistema en equilibrio.  
<img width="541" height="548" alt="image" src="https://github.com/user-attachments/assets/aa792d2e-4b85-4665-a626-19d470cab267" />

Para solucionar esto, lo más sensato era que las partículas que no hayan muerto después de 5 segundos (lo que dura en promedio el sistema en estabilizarse) se dirigirán hacia el centro, de manera que siempre haya muerte. Además, si solo queda un equipo, se ve mejor el ganador en el centro que disperso por el mundo.



