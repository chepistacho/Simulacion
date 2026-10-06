# Encargo de diseño
La verdad, esta es una de las unidades que más me ha interesado hasta el momento, por lo que decidí empezar a trabajarle (aunque sea a la idea) desde ya.  
Lo primero que hice fue seleccionar unas canciones que, por un motivo u otro, me llamaban la atención para realizar este ejercicio, las cuales fueron:
- Nocturnalized - Pär Hagström
- Why can't this night go on forever - Journey
- Constelación - Ramma
- eCLIPSE sOLAR - Duki
- Otro Amanecer - Delaossa
- Never Love You Again - Post Malone
- Breathe Me - SIA
- Como Estrellas - LA YOUNG
- lady madrizZz - céro
- Perfect Circle / Godspeed (solo Godspeed) - Mac Miller
Después de esto, me quedé con un total de 3 canciones que, después de hacer algunos ensayos con los algoritmos, veré cuál puede ser mi mejor opción.
Los tres temas fueron:
- Nocturnalized
- Constelación
- Godspeed
Tenía demasiadas ganas de hacer algo con el tema de Journey, pero no fui capaz de conectar mi idea con los algoritmos de la unidad, por lo que decidí mejor dejarlo para luego.
Antes de empezar a idear, decidí que lo mejor era pedirle a la IA un modelo básico de cada algoritmo, de forma que pueda decidir qué comportamientos y parámetros me pueden servir para desarrollar una idea acorde.
## Ensayos
### Nocturnalized
Es un tema con una energía bastante imponente que, aunque tiene un tempo algo lento, se siente pesado. Para este, decidí usar Interactive Physarum, apoyándome de una transformada de Fourier para que le diera dinamismo a la zancada. Después de jugar un rato con algunos parámetros, dio unos resultados interesantes, pero aún se sentían como un algoritmo genérico.  
### Constelación
Un tema menos imponente, pero más rápido. Habla de una relación desde un punto de vista un poco más crudo, con agradecimiento hacia la otra persona, usando las estrellas como metáfora (no sé qué tan conectado esté realmente, pero igual qué temazo).


## Conceptualización 
Finalmente me decanté por **"Constelación"**. Arrancamos el proyecto teniendo la letra completa del tema para armar la coreografía visual del toque en vivo. Definí que la estética principal sería una red de constelaciones controlada en tiempo real. El concepto base lo monté sobre un único sistema de partículas en Three.js para optimizar los recursos y no tostar el rendimiento. La idea fue mezclar dos lógicas matemáticas: flocking para el comportamiento de enjambre y flow fields para las corrientes y gravedades.  
Al principio mapeé las emociones básicas de la canción, como la rabia o la represión, alterando la separación o la cohesión de las estrellas. Sin embargo, noté que en los versos y en el clímax la simulación se quedaba muy monótona. A partir de esto, exploré la letra a fondo y definí estados conceptuales nuevos para momentos específicos, logrando dinámicas como un latido central, apagones repentinos de las conexiones o ráfagas de viento que barren la pantalla para limpiar la tensión.  
Durante el diseño de la interacción pillé varios problemas visuales que resolví desde el planteamiento conceptual. Por ejemplo, cuando mandaba todas las partículas a proteger el centro, se armaba un pegote de luz que encandilaba y saturaba la imagen, así que le metí órbitas de seguridad y rebotes elásticos para que formaran un escudo dinámico en lugar de colisionar. También evité que las partículas se acumularan en los bordes del lienzo formando una geometría cuadrada poco estética, cambiándolo por un flujo en forma de halo infinito.  
Para los momentos de ausencia lírica en la canción, decidí no apagar la pantalla por completo para no desconectar al público de la presentación. En su lugar, opté por empujar las estrellas hacia las esquinas para dibujar el vacío utilizando el espacio negativo, sumando un efecto de chispas o falso contacto en las líneas para mantener la ansiedad visual antes del siguiente estallido de la pista.  
Finalmente, hice uso de la inteligencia artificial para plasmar estas ideas en mi instrumento visual, explicándole los comportamientos e identidad visual.  
La asignación de botones quedó de la siguiente manera:  
| Tecla | Movimiento de las partículas |
| :--- | :--- |
| **0** | Posiciones estáticas en sus coordenadas iniciales con líneas de conexión apagadas. |
| **1** | Repulsión extrema y rápida entre partículas, generando trayectorias caóticas y ruptura constante de las líneas. |
| **2** | Contracción masiva hacia el centro del lienzo, agrupando todo en un núcleo denso con leve vibración. |
| **3** | Alineación absoluta y desplazamiento unidireccional, moviendo toda la red a la misma velocidad como una grilla rígida. |
| **A** | Frenado en seco. La velocidad cae a cero y el sistema se congela en el espacio inmediatamente. |
| **4** | El grupo A se concentra en el medio con mínima separación. El grupo B rota de forma constante alrededor del grupo A respetando un radio fijo. |
| **S** | Expulsión súbita. Aceleración instantánea que dispara las partículas hacia los bordes rompiendo la red de golpe. |
| **5** | Movimiento orbital circular y continuo de todo el sistema alrededor del punto central del escenario (donde se ubica el sol). |
| **6** | Flujo suave y orgánico a baja velocidad, con variaciones leves de dirección generadas por ruido matemático (turbulencia continua). |
| **D** | Renderizado de conexiones desactivado. Las partículas sueltas flotan a la deriva con un arrastre muy alto. |
| **7** | Dos subgrupos avanzando a la misma velocidad pero en trayectorias de onda senoidal, cruzándose continuamente sin colisionar. |
| **F** | Separación horizontal forzada. La mitad del sistema se arrastra rápidamente hacia el borde izquierdo y la otra hacia el derecho. |
| **8** | Colisiones inducidas. Las partículas se atraen a alta velocidad y experimentan un rebote elástico violento al acercarse. |
| **9** | Aproximación paulatina. Las partículas dispersas reducen la distancia entre sí gradualmente hasta reconstruir la red conectada. |
| **Z** | Dos pulsaciones concéntricas veloces. Toda la red se expande ligeramente y se vuelve a contraer desde el centro. |
| **X** | Barrido horizontal repentino. Un flujo de altísima velocidad arrastra bruscamente todas las partículas hacia un extremo, desarmando la geometría. |
| **C** | Desaceleración extrema (cámara lenta) mientras las partículas se estabilizan formando un anillo de rotación circular. |
| **G** | Desplazamiento forzado hacia la diagonal inferior con alta resistencia (fricción), ralentizando el avance de todo el bloque. |
| **H** | Tensión espacial. Las partículas oscilan y vibran erráticamente en su propio eje debido a fuerzas de atracción y repulsión simultáneas. |
| **Q** | Desplazamiento perimetral. Las partículas migran hacia los extremos formando un toroide o anillo lejano sin llegar a estrellarse contra los bordes. |
| **J** | El grupo A rota a altísima velocidad formando un anillo central sólido. El grupo B viaja hacia el centro pero rebota agresivamente al chocar con el radio del grupo A. |
| **W** | Desplome vertical total. La red pierde soporte y cae en línea recta hacia el límite inferior del lienzo. |
| **E** | Repulsión central sostenida. El medio de la pantalla se vacía lentamente y las partículas quedan arrinconadas y estáticas en las esquinas. |
| **Y** | Posiciones frenadas y estáticas mientras el dibujado matemático de las líneas se prende y se apaga de forma aleatoria (parpadeo o chispa). |
| **K** | Contradicción vectorial. Las partículas se orientan y hacen el esfuerzo de subir, pero un campo de fuerza dominante las arrastra lentamente hacia abajo. |
| **R** | Movimiento browniano a máxima velocidad. Las partículas cambian de dirección de manera caótica e impredecible sin formar conexiones. |
| **T** | Reducción progresiva e interpolada de la velocidad hasta la detención total, combinada con un desvanecimiento simultáneo de la visibilidad. |. 

## El link
https://chepistacho.github.io/Constelacion/

## Autoevaluación
