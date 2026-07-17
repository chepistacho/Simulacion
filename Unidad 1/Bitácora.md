# Actividad 1

En esta actividad quise incluir, no solo ideas de los videos y ensayos del GitHub del curso, sino también algunas ideas de lo que dijo el profe en la primera sesión, los cuales no solo sirven como guía, sino también como un recorderis de cursos pasados:

## Videos
- "El arte generativo no depende solo de código, sino también de la entropía y la **aleatoriedad**"

- (No sé qué tanto tenga que ver la fuente de Duchamp con el arte generativo, pero me parece interesante la comparación de lo "random" en lo aleatorio y lo "random" en corrientes como el dadaísmo)

- "Hubo algunos matemáticos en ingenieros que fueron **pioneros** en el arte generativo"

- "El resultado va más allá de lo que puedes imaginar con esas reglas simples"

- "Al final todo va de una imagen a un código, que devuelve una imagen"

- "Estereotípicamente son máquinas precisas y calculadoras. Poder permitir resultados inesperados es una manera emocionante de trabajar"

- "El artista trabaja mediante un sistema o un proceso, en vez de intentar crear un trabajo específico"

- Me parece brutal la comparación que hace con el skateboard y el jazz, usando conceptos como la concentración, el peligro y el diálogo. Es una idea bonita y un mensaje increíble sobre el arte en general.

- "Veo el computador como un compañero de trabajo para **Incomplete Control**"

- "Quiero que el espectador pueda disfrutar mi trabajo de la misma manera en que disfruta de la música"

- "Es importante seguir tu propia visión de lo que es un buen trabajo, y abrir la mente para encontrar esa visión"

## Lo que dijo el profe
- "El trabajo es nuestro en la misma medida que un triunfo es de un DT"

- "No nos quedemos solo con lo técnico; pensemos en cómo acoplar esta teoría al arte"

- "La media es el punto más alto de la campana. Mientras más ancha sea la campana, mayor es la desviación estándar"

- "Nosotros hacemos las reglas con la que se genera la obra" (o algo así dijo).

## Los ensayos de Tyler
Dejaré evidencia si los llego a leer. Realmente Tyler me pareció un tipazo, con una visión y un arte bastante interesantes, pero creo que voy a priorizar el resto de actividades antes de profundizar en un solo artista.


# Actividad 2
Esta la alcanzamos a revisar en clase, entonces voy a dejar aquí algunas cosas que me quedaron:

- Siempre instanciar la clase por fuera de los métodos **(preguntar al profe el por qué, pues se me olvidó camino a casa)**
- Se puede observar la distribución aleatoria desde el mismo dibujo. Si bien en el ejemplo de la clase se veía una clara tendencia hacia la derecha y abajo, lo dejé corriendo un rato en mi computador y muestra un comportamiento más uniforme.

Pregunta que me surgió: ¿Una partida de "El Juego de la Vida" de John Conway puede ser considerada como arte generativo?


# Actividad 3
- La diferencia, es que, en una distribución uniforme, todas las opciones contempladas tienen la misma probabilidad de "aparecer" (no se me ocurre otra palabra), mientras que en una distribución no uniforme las probabilidades están más acumuladas hacia ciertos resultados.
-Intenté con una distribución normal, pero no me dio el coco para la sintaxis, por lo que el resultado con este código
   ``` js
  step() {
    const choice = floor(randomGaussian(0, 0));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
`  
Fue el sguiente:  
<img width="505" height="181" alt="image" src="https://github.com/user-attachments/assets/612e0e3b-ec96-473d-ad3f-fd09dbdd4a55" />

De las que mostró el profe, la mejr opción fue con los rangos, dejando de redondear el resultado y dándole más peso al que crrespondía a la variación positiva en el eje X.

# Actividad 4
Aquí cambié un poco la cosa. Por un lado, le metí mano al color, para que los valores RGB dependieran de la **distribución normal**, pero también hice que el radio del círculo dependiera de ese `x` mediante la fúrmula `10000/x`, dando como resultado una forma que parece com un túnel:  
<img width="750" height="716" alt="image" src="https://github.com/user-attachments/assets/cd327862-e0fc-4ab9-85d3-cdd6d3b5d8f5" />
Aquí se aprecia la distribución normal, pues podemos ver cómo se amontonan más círculos con el radio más pequeño, es decir, cuando la `x`en la fórmula `10000/x` es más grande. 
El código es este:  
``` js
function draw() {
  // A normal distribution with mean 320 and standard deviation 60
  let x = randomGaussian(320, 100);
  noStroke();
  fill(400-x, 360-x, 420-x, 5);
  circle(width/2, height/2, 100000/x);
}  
