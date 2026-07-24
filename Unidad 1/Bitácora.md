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
```
# Actividad 5  
Primero que nada, es importante entender qué es un vuelo de Levy.  
Según lo que entendí (me tocó confirmar con IA) es un patrón en el que, a diferencia de una caminata aleatoria, va por "regiones" (o al menos así lo entendí yo). Da pasos alrededor de un area y, en algunas ocasiones, pega un brinco largo, donde vuelve a dar pasos alrededor, y así sucesivamente. El cálculo de los pasos debe ser aleatorio, con mucha probabilidad de que el paso sea pequeño, y poca probabilidad de que sea un paso largo.
Para el primer punto de esta actividad, voy a usar el ejercicio de la caminata aleatoria, y voy a cambiar los parámetros para que los pasos puedan ser grandes con una probabilidad más baja que los pasos cortos. También pensé que sería interesante si los colores del caminante cambiaran junto con su posición y, realmente, me gustó el resultado. Los pasos los calculé con el método Monte Carlo mostrado en el texto guía, cambiando algunas cosas en función de un resultado más coherente con el concepto de vuelo de Lévy.  
Esta técnica la usé para no terminar usando el machetazo del inicio, pues, como dice en el texto, termina siendo muy cesgado y no da lugar a resultados intermedios, mientras que el método Monte Carlo daba lugar a una gama más amplia de resultados.  
``` js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(this.x, this.y, random(255));
    point(this.x, this.y);
  }

  step() {
    let stepsize;
    const choice = random(1);
    while (true){
      let r1 = random(1, 50);
      let probability = 1/(r1*r1);
      let r2 = random(1);
      if (r2 < probability){
        stepsize = r1;
        break;
      }
    }
    let dirX = random(-1, 1);
    let dirY = random(-1, 1);

    this.x += dirX * stepsize;
    this.y += dirY * stepsize;
    
    if (this.x < 0){
      this.x = 640
    }
    else if (this.x > 640){
      this.x = 0;
    }
    if (this.y < 0){
      this.y = 240
    }
    else if (this.y > 240){
      this.y = 0
    }
  }
}
```
Lo que espero es tener un montón de manchas coloridas distribuídas por todo el lienzo, siendo más las grandes que las pequeñas, habiendo saltos poco frecuentes comparados con los pasos inmediatos del caminante.  
<img width="800" height="297" alt="image" src="https://github.com/user-attachments/assets/ed0dd436-8b09-4866-ba48-c92284d583b8" />  

# Actividad 7 (reto de diseño)  
Para esto modifiqué el código del vuelo de Lévy, pues era el que más acorde vi a los momentos del enunciado, y la interacción la puse en la parte del método Monte Carlo, dejando que el primer número sea elegido mediante la posición del mouse, y que el tercer parámetro del color, que antes era aleatorio fuera definido con la posción vertical del mouse. Ese, al menos, es mi punto de partida, y queda como anillo al dedo, pues cuando vi mi primer intento de este ejercicio me daba vibras de una pintura en aerosol, por lo que también tengo un concepto por ahí de paso: **arte urbano**.  
<img width="801" height="305" alt="image" src="https://github.com/user-attachments/assets/ef48f4cd-37b1-418c-b6fd-de1f6db456e9" />  
Ahora bien, muy bonito y todo, pero ahí solo tiene vuelo de Lévy y parte de una caminata aleatoria de toda la vida, pero aún tengo que meterle más cambios de probabilidad, quizás otros elementos, y bastante interacción relacionada con lo que pide el enunciado.  
Después de echarle mucha cabeza, llegué a una idea que finalmente me convenció, y que sería orquestrada como una canción, en la que los instrumentos se van acoplando poco a poco para dar una obra enorme:  
1. Al principio se vería un caminante aleatorio normal, con poco color, caminando en su zona.
2. Después de un tiempo, el caminante empezaría a mostrar una tendencia hacia algún lado, pero sin dejar de moverse en todas las direcciones.
3. En el tercer momento aún no sé qué poner, pero lo documentaré aquí si se me ocurre algo. Se me ocurre empezar a meter color y/o tamaño aquí, pero, nuevamente, aún es muy abstracta la idea.
4. Aquí se implementaría el vuelo de Lévy tradicional, que 100% depende de la aleatoriedad, mostrando saltos ocasionales.
5. Finalmente, el usuario termina controlando un parámetro, que sería lo que tenía planteado desde el principio.
Para esto me apoyé de la IA, con el fin de refrescar la lógica de una máquina de estados que, además, funcionara con tiempo y no con botones.
Con esto claro, me puse manos a la obra y no salió bien. Lo primero fue que el walker estaba de colores, y no había pensado en cómo alterar ese valor dependiendo del estado, pero ya luego corrijo eso. El comportamiento del primer momento (estado) va bien, pero al segundo se terminó tirando para la izquierda:  
<img width="773" height="285" alt="image" src="https://github.com/user-attachments/assets/496198a2-720b-4d00-b2a1-4ecc3adc5b86" />  
Mañana me pondré a corregir esos errores, y terminaré el resto de los estados.


