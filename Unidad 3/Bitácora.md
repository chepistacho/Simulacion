# Actividad 3
Me demoré mucho en empezar la bitácora, pese a que ya tenía cosas avanzadas, entonces voy a intentar recapitular lo mejor posible.  
Lo primero que hice fue hacer que el preset por default fuera el de atracción, pues sentía que era un buen punto de partida para jugar con las físicas. Después de eso, tuve una idea, y era que salieran unas pequeñas protuberancias (como si fuera un fluido raro) de la parte de arriba y de abajo con sus respectivas flechas. Sin embargo, esto no salió como lo pensé, pero tampoco me disgustó (más aún con la combinación con otras implementaciones).  
<img width="304" height="217" alt="image" src="https://github.com/user-attachments/assets/db538d91-88f8-422d-83a0-98d4a216d6f5" />

Además de esto, decidí que el atractor estuviera fijo en el centro, de manera que todo funcionara más simétricamente.  
En este punto, me di cuenta de que el efecto de repeler y atraer casi instantáneamente, daba un buen efecto de "respiración", por lo que le pedí a la IA que implementara esta función. Nuevamente falló, pero dejó otro efecto interesante que terminé usando incluso más que el de la idea original, por lo que la dejé además de la función de beat y otra adicional, que funcionaba parecido, pero con el efecto de vórtice en vez de repulsión. También arreglé las partículas para que tuvieran una margen con respecto al centro, de forma que no se juntaran todas las partículas como una bola blanca, sino que se alcanzaran a distinguir entre ellas.  
Por último, le pedí a la IA que me ayudara a implementar dos cosas: una fuerza tipo vórtice, pero con atracción en vez de repulsión, y un segundo atractor que funcionara con el mouse y la barra espaciadora, de manera que solo funcione en ciertos momentos.  
Ya con todo esto listo, solo quedaba ponerse a jugar para ver qué movimientos me gustaban. Dado que esta bitácora perdió el sentido de registrar esto gradualmente, me tomaré la libertad de mostrar los movimientos que más me gustaron, acompañando cada captura captura con un texto que, a su vez, será mi visual score.  
## Visual Score
<img width="626" height="475" alt="image" src="https://github.com/user-attachments/assets/d5472c90-6d63-464b-a880-846241b05fcf" />  

Aquí se queda oscilando un rato. **00:00 - 00:04**  

<img width="731" height="580" alt="image" src="https://github.com/user-attachments/assets/58fa3388-0a4c-492f-ac87-ec0e7845ffb1" />   

Esta es la versión del "beat" que me terminó gustando más. Pienso apretar el botón al ritmo de la música durante un tiempo **00:04 - 00:18**  

<img width="373" height="475" alt="image" src="https://github.com/user-attachments/assets/72866b79-0da4-4cf2-b66a-e1b769759a59" />  

No es la mejor captura, pero este es el efecto de las flechas. La idea es que, al igual que los beats, los vaya presionando rítmicamente hacia arriba y hacia abajo. **00:18 - 00:31**  

<img width="429" height="729" alt="image" src="https://github.com/user-attachments/assets/70c32237-b95e-4396-927a-32913f63c602" />  

Esta es la fuerza de movimiento continuo del proyecto original. **00:31 - 00:52**  

<img width="791" height="481" alt="image" src="https://github.com/user-attachments/assets/1256cbe3-f807-4397-a302-f33aad0fdcfd" />  

Al aplicar la fuerza de atracción sobre la fuerza de movimiento constante, se forman estas figuras, que me parece que combinan bien con esta parte del tema **00:52 - 01:14**  

<img width="469" height="412" alt="image" src="https://github.com/user-attachments/assets/33a28aee-5cf5-4305-b406-914e296ac3ff" />  

La fuerza que la IA bautizó como "agujero negro". Al aplicarle los "disparos" de las flechas se logra este efecto, que van re bien con el "tururun" que suena cada beat. **01:14 - 01:54**  

<img width="589" height="475" alt="image" src="https://github.com/user-attachments/assets/68c1d48b-36fc-4908-8847-4e12caf9e7c9" />  

Al liberar las partículas repentinamente, se forman estos patrones que sirven para representar la tranquilidad antes de la pausa. **01:54 - 02:08**  

<img width="539" height="502" alt="image" src="https://github.com/user-attachments/assets/7f63b2ca-3b72-4236-b4cf-93aa30e9d21a" />  

Mientras la música vuelve a subir, se forma una esfera con el modo de atracción. **02:08 - 02:15**  

<img width="373" height="475" alt="image" src="https://github.com/user-attachments/assets/72866b79-0da4-4cf2-b66a-e1b769759a59" />  

Aquí repetimos este patrón del principio. **02:15 - 02:28**  

<img width="491" height="433" alt="image" src="https://github.com/user-attachments/assets/f894eeb2-0862-4afa-a589-15e361126f1b" />  

Aquí empiezan a sonar unos chords que se repiten, entonces quise representarlo con el movimiento del segundo atractor, moviendo el mouse cada que sonara uno de estos chords. **02:28 - 03:51**  

Otra vez agujero negro. **03:51 - 03:54**  

En este momento presiono la barra espaciadora y paso el mouse por el medio de la esfera central al ritmo de los 4 beats. **03:54 - 03:56**  

Aquí aplico la misma lógica de antes, pero con el agujero negro en vez de la atracción, usando el segundo atractor con cada chord. **03:56 - 04:23**  

Me quedo solo tirando beat. **04:23 - 04:32**

Vuelvo a pasar el mouse por la mitad al ritmo de los 4 beats. **04:32 - 04:36**  


**El link**: https://chepistacho.github.io/Sim-U3/  

## Mapa del sistema
| Concepto | Qué es en este proyecto | Archivos |
| :--- | :--- | :--- |
| **Estado** | Es la memoria en la tarjeta gráfica donde guardamos la posición, la velocidad y el eje de rotación de cada una de las 131,072 partículas, esto para que el computador no se cuelgue procesando toda la información. | createSimulation.js, main.js |
| **Fuerzas** | Son las reglas que empujan las partículas. En este caso sumamos varias: viento, un remolino tridimensional, fricción para frenarlas, atracción al centro (con una fuerza de rebote para que no colapsen en un solo punto), pulsos rítmicos y la atracción hacia el mouse. | createSimulation.js, parameters.js |
| **Integración** | Es el motor que suma todas las fuerzas y calcula hacia dónde se tiene que mover la partícula en el siguiente frame. También limita la velocidad máxima y hace un efecto de portal: si una partícula sale de la pantalla, entra por el lado contrario. | createSimulation.js |
| **Render** | Es la parte netamente visual. No calcula física, solo toma los datos y dibuja las partículas como puntos de luz. Además, usa la velocidad para definir el color: se pintan de azul si van lento y de naranja si van rápido. | createSimulation.js |
| **Controles** | Es la interacción con el teclado. Los números del 1 al 7 activan combinaciones de fuerzas predefinidas (como la tormenta o el agujero negro), las flechas y teclas B/N/V lanzan efectos de ritmo, y la barra espaciadora activa el atractor del mouse | main.js |

## Ficha de fuerzas
| Fuerza | Ecuación / Dirección | Parámetros | Predicción de Comportamiento | Decisiones de Diseño |
| :--- | :--- | :--- | :--- | :--- |
| **Viento (Wind)** | Constante direccional: wind | wind, windEnabled | Las partículas son empujadas uniformemente en la dirección del vector definido, simulando un flujo constante. | Fuerza base lineal sin decaimiento por distancia. Se utiliza para desplazar el sistema entero o crear flujos direccionales que rompen la simetría orbital. |
| **Radial (Lennard-Jones)** | dir * ((fuerza / d²) - (3.5 / d⁴)) | radialStrength, softening, radialEnabled | Las partículas son atraídas hacia el origen desde lejos, pero al acercarse demasiado al núcleo experimentan una repulsión violenta, quedando suspendidas en una zona de equilibrio. | Se implementó un comportamiento tipo Lennard-Jones en lugar de atracción pura para evitar la singularidad geométrica (el colapso en el punto 0,0,0) sin necesidad de programar costosas colisiones inter-partículacite: 7, 8. |
| **Vórtice 3D (Vortex)** | Producto cruz: spinAxis × dir_radial | spinAxisBuffer (por partícula), vortexStrength | Las partículas orbitan el centro. Al poseer cada una un eje de rotación distinto, la nube se estructura como un volumen esférico tridimensional. | Asignar un vector de giro individual desde la inicialización (spinAxis) soluciona el problema técnico de la rotación plana. Evita que el vórtice colapse en un disco sobre el plano XY. |
| **Fricción (Drag)** | Opuesta a la velocidad: -v * dragCoefficient | dragCoefficient, dragEnabled | Las partículas pierden energía cinética gradualmente, frenando su desplazamiento y cerrando sus órbitas. | Fundamental para la estabilidad numérica del sistema. Disipa el momento angular residual al cambiar de *presets*, evitando que las velocidades se acumulen infinitamente. |
| **Ráfaga (Burst)** | Empuje radial saliente acotado por un cono (smoothstep) | BURST_STRENGTH (fija=10), BURST_CONE, top/bottomBurst | Exclusivamente las partículas ubicadas en los polos geométricos reciben un impulso hacia afuera, generando una protuberancia direccional. | Se le asignó una magnitud fija independiente de la distancia para evitar que la fuerza se diluya. Se usa smoothstep para difuminar los bordes del cono, logrando un empuje orgánico y sin cortes duros. |
| **Pulso (Beat)** | Empuje radial saliente: dir_radial * BEAT_STRENGTH * fase | BEAT_STRENGTH (fija=12), beatPhase (+1, -1, 0) | El sistema entero se expande bruscamente desde el centro y luego se contrae sincrónicamente, simulando un latido. | Al ser una fuerza estrictamente radial, no inyecta momento angular indeseado al sistema. Su magnitud también es fija para garantizar que el pulso sea visible sin importar qué *preset* esté activo. |
| **Atractor Mouse** | dir_mouse * (mouseStrength / d²) | mousePos, mouseStrength, mouseActive | Al presionar Espacio, las partículas modifican su trayectoria para orbitar o impactar la proyección 2D del cursor del usuario. | Introduce una capa de interacción tipo *live instrument* sobre la física base. Actúa de manera independiente al atractor central para permitir órbitas excéntricas e impredecibles. |  

## Autoevaluación
| Criterio | Peso | Justificación | Valoración |
| :--- | :--- | :--- | :--- |
| **Trazabilidad y comprensión del sistema** | 25 | Falta de conceptualización. | 3.5 |
| **Verificación del algoritmo de fuerzas** | 25 | Entiendo parte de la arquitectura, pero la mayoría me queda grande. | 3.5 |
| **Diseño de fuerzas e intención** | 20 | Todo es a base de las físicas de las partículas. No hay nada definido en cuanto a sus movimientos exactos. | 5.0 |
| **Instrumento, score e interpretación** | 15 | Todos los movimientos son con intención. Practiqué los movimientos de controles para que se muevan como yo indico y no como la música lo dicta. | 5.0 |
| **Experimentación y criterio frente a la IA** | 10 | Sí registré hallazgos y experimentación, pero casi que lo único que descarté fue cuando el sistema ya no funcionaba (pantalla negra/una sola partícula). | 4.5 |
| **Entrega técnica y documentación** | 5 | Cumple. | 5.0 |
| **Total Puntos** | **100** |  | **4.2** |
