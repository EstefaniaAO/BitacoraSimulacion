<img width="1226" height="742" alt="image" src="https://github.com/user-attachments/assets/06772677-000e-456e-9250-a3b975a2c9b2" />

https://editor.p5js.org/estefaao2006/sketches/MHuw_i3lM

https://editor.p5js.org/estefaao2006/full/MHuw_i3lM

## Volcanic Attitude Festival

### Resumen

**Volcanic Attitude Festival** es un festival de cultura contemporánea que reúne **arte, ciencia e investigación** en un recorrido itinerante entre **Nápoles, las Islas Eolias y otros territorios volcánicos**. Más que centrarse en los volcanes como objetos de estudio, utiliza los paisajes volcánicos como un punto de partida para reflexionar sobre la naturaleza, los procesos de transformación y la relación entre las personas y su entorno.

Cada edición propone un viaje en el que artistas, científicos, investigadores, comunidades locales y visitantes participan en experiencias como performances, conversaciones, exploraciones, caminatas, baños termales y actividades colectivas. El objetivo es generar nuevas formas de conocimiento a través del encuentro entre distintas disciplinas y perspectivas.

En su quinta edición (2026), el festival se desarrolla entre Nápoles, Stromboli y Vulcano, incorporando además a **Islandia y Martinica** como territorios invitados para dialogar con el paisaje mediterráneo.


### Temáticas principales

#### 1. Transformación y cambio

El festival explora cómo los paisajes, los ecosistemas y las sociedades están en constante transformación. Los volcanes representan procesos dinámicos más que estructuras estáticas.

#### 2. Arte y ciencia

Busca crear un diálogo entre prácticas artísticas e investigación científica, entendiendo ambas como formas complementarias de explorar y comprender el mundo.

#### 3. Naturaleza y procesos invisibles

Se interesa por fenómenos que normalmente no percibimos directamente, como:

- Vibraciones.
- Ondas sonoras.
- Procesos geológicos.
- Actividad submarina.
- Fenómenos cósmicos y astronómicos.

La atención está puesta en las fuerzas que modelan el entorno aunque permanezcan ocultas.

#### 4. Investigación y conocimiento

Promueve el pensamiento crítico y la investigación como herramientas para comprender cuestiones culturales, sociales y ambientales.

#### 5. Comunidad y participación

El festival busca conectar a las comunidades locales con visitantes, artistas e investigadores, favoreciendo el intercambio de experiencias y la construcción colectiva de conocimiento.

#### 6. Sostenibilidad

Propone trabajar con los recursos disponibles y desarrollar prácticas responsables con el territorio y el medio ambiente.

#### 7. Ritual y experiencia colectiva

Las actividades del festival incluyen momentos compartidos —como caminatas, baños termales o encuentros— que recuperan el valor de los rituales y la convivencia como formas de generar conocimiento.

#### 8. Ética y futuros posibles

En un contexto marcado por conflictos globales, el festival plantea una reflexión sobre la responsabilidad de artistas y científicos para imaginar futuros más equilibrados, atentos a la diversidad de formas de vida y a las relaciones entre los seres humanos y la naturaleza.

### Idea central

En conjunto, **Volcanic Attitude** propone entender el mundo como un sistema de relaciones y procesos en constante evolución. Los volcanes funcionan como una metáfora y un laboratorio natural para pensar en el cambio, la incertidumbre, la interdependencia y la capacidad de imaginar nuevas formas de habitar el planeta desde la colaboración entre arte, ciencia y comunidad.


# Idea para la experiencia:

**Idea inicial:** La experiencia propone representar un recorrido interactivo mediante un mapa. El escenario tendrá un punto de partida ubicado en la esquina inferior izquierda y un destino en la esquina superior derecha, representado por un volcán.

Dentro del mapa se desplazarán varios puntos rojos que simbolizan a los guías. Estos seguirán una trayectoria desde el inicio hasta el volcán utilizando un movimiento orgánico generado con ruido de Perlin. A cada guía lo acompañarán varios puntos negros que representan a los turistas, los cuales se moverán de manera aleatoria, pero procurando mantenerse cerca de su guía para simular el comportamiento de un grupo durante un recorrido.

El usuario interactuará con la experiencia controlando un punto amarillo mediante las teclas **WASD**, permitiéndole desplazarse libremente por el mapa. Cuando el usuario se aproxime a uno de los guías, se generarán pequeñas ondas alrededor de este para representar una interacción o conversación entre ambos.

Como parte del componente visual, el recorrido irá transformando el mapa de forma progresiva. A medida que los turistas avanzan, aparecerán zonas de color que construyen el entorno: tonos azules representarán el mar y tonos cafés se concentrarán alrededor del volcán, reforzando la percepción del paisaje y haciendo visible el progreso del recorrido.

--- 

Esta idea la conversé con la IA la cual propuso los siguientes cambios:

> "Explicar mejor el comportamiento de los turistas.
> Antes: "se moverán de manera aleatoria, pero procurando mantenerse cerca de su guía."
> Ahora: ese comportamiento se justifica con una distribución normal, donde la mayoría permanece cerca del guía y solo unos pocos se alejan.
> 
> Añadir el evento excepcional.
> Antes no había una excepción clara.
> Ahora, con muy baja probabilidad, un turista realiza un desplazamiento largo (Lévy flight), descubre una zona nueva y revela más del mapa. Así cumples el concepto de Excepción.
> 
> Cambiar la interacción del usuario.
> Antes: al acercarse al guía aparecían ondas, pero no afectaban el sistema.
> Ahora: las ondas siguen apareciendo, pero además representan que el usuario está modificando las probabilidades del comportamiento de los turistas.
> 
> Hacer más evidente la relación con los cinco conceptos del enunciado, especialmente Tendencia, Normalidad e Influencia."


---

Al principio tenía claro que quería hacer algo relacionado con un recorrido porque sentía que conectaba muy bien con la idea del festival y con el concepto de exploración. Pensé en hacer un mapa donde hubiera un punto de inicio y un volcán como destino, con unos guías que llevaran a un grupo de turistas hasta allá. También quería que el recorrido fuera construyendo poco a poco el paisaje para que se sintiera como si el territorio se fuera descubriendo mientras avanzaban.

Después empecé a revisar mejor los requisitos del reto y me di cuenta de que no bastaba con que la idea se viera bonita o contara una historia, sino que los comportamientos del sistema tenían que representar los conceptos de aleatoriedad. Ahí fue cuando empecé a replantear varias partes del proyecto.


---

**Idea final:** 


La experiencia propone representar un recorrido interactivo mediante un mapa. El escenario tendrá un punto de partida ubicado en la esquina inferior izquierda y un destino en la esquina superior derecha, representado por un volcán. Inspirado en los recorridos del Volcanic Attitude Festival, el mapa simboliza un territorio en constante transformación, donde diferentes formas de aleatoriedad generan distintas maneras de explorar el paisaje.

Dentro del mapa se desplazarán varios puntos rojos que simbolizan a los guías. Estos seguirán una trayectoria desde el inicio hasta el volcán utilizando un movimiento orgánico generado con ruido de Perlin, por lo que, aunque todos persiguen el mismo destino, cada recorrido será ligeramente diferente y parecerá surgir de manera natural.

A cada guía lo acompañarán varios puntos negros que representan a los turistas. Estos se moverán mediante una caminata aleatoria, pero su posición respecto al guía seguirá una distribución normal: la mayoría permanecerá cerca de él, mientras que solo unos pocos se alejarán temporalmente antes de volver al grupo. Esto generará agrupaciones dinámicas que reflejan el comportamiento habitual de un recorrido guiado.

De manera ocasional, y con una probabilidad muy baja, uno de los turistas realizará un desplazamiento mucho mayor (Lévy flight), alejándose del grupo para explorar una zona distante del mapa. Estos eventos excepcionales permitirán descubrir partes del paisaje que normalmente permanecerían ocultas, representando cómo un evento improbable puede abrir nuevas posibilidades.

El usuario interactuará con la experiencia controlando un punto amarillo mediante las teclas WASD, permitiéndole desplazarse libremente por el mapa. Cuando se aproxime a uno de los guías, aparecerán pequeñas ondas a su alrededor para representar una interacción o conversación entre ambos. Sin embargo, esta interacción no será únicamente visual: la presencia del usuario modificará las probabilidades del sistema. Al acercarse a un guía aumentará la probabilidad de que los turistas permanezcan cerca de él (por ejemplo, pasando de un 70% a un 90% de probabilidad de seguir al guía), reduciendo la posibilidad de grandes desviaciones. Cuando el usuario se aleje, estas probabilidades volverán gradualmente a su estado normal, favoreciendo nuevamente la exploración y aumentando la posibilidad de que ocurran desplazamientos excepcionales.

Como parte del componente visual, el recorrido irá transformando el mapa de forma progresiva. A medida que los turistas exploran el territorio, aparecerán zonas de color que construirán el entorno: tonos azules representarán el mar y tonos cafés se concentrarán alrededor del volcán y de los caminos recorridos, reforzando la percepción del paisaje y haciendo visible la huella que dejan las exploraciones.

# Implementación:

## Prompt inicial:

Crea una experiencia interactiva en p5.js con formato vertical 9:16, pantalla completa (windowWidth y windowHeight) y animación en tiempo real. La estética debe ser minimalista, elegante y artística, utilizando únicamente círculos, líneas suaves, transparencias y manchas de color. No utilizar imágenes ni sprites. 

La escena representa un mapa. En la esquina inferior izquierda se encuentra el punto de inicio y en la esquina superior derecha un volcán representado de forma minimalista. Todo el sistema funciona continuamente incluso si el usuario no interactúa. 

Guías 

Crear entre 4 y 6 guías, representados por círculos rojos con un ligero resplandor. Todos parten desde el punto inicial y avanzan lentamente hacia el volcán. Su movimiento nunca debe ser completamente recto, sino seguir trayectorias orgánicas utilizando noise(). Cada guía sigue un camino ligeramente distinto. Cuando llegan al volcán vuelven al punto inicial para mantener el sistema funcionando indefinidamente. 


Turistas 

Cada guía posee entre 8 y 12 turistas, representados por pequeños círculos negros. Los turistas siguen una caminata aleatoria pero siempre intentan mantenerse cerca de su guía. La distancia respecto al guía debe seguir una distribución normal, haciendo que la mayoría permanezca cerca y unos pocos se alejen ligeramente. El movimiento debe ser muy lento, continuo y fluido, sin cambios bruscos de velocidad. Nunca deben parecer que salen disparados ni moverse de forma caótica. Siempre deben mostrar un pequeño movimiento incluso cuando permanecen cerca del guía. Evento excepcional (Lévy Flight) Con una probabilidad muy baja (aproximadamente 0.5% por segundo por turista) ocurre un Lévy Flight. Durante este evento el turista realiza un recorrido mucho más largo en una dirección aleatoria. El desplazamiento debe seguir siendo continuo y fluido; nunca debe sentirse como un teletransporte ni como un punto que sale volando. Después de unos segundos vuelve gradualmente a acercarse a su guía. Este evento debe sentirse muy raro y especial. Usuario El usuario controla un círculo amarillo mediante WASD. El usuario debe iniciar exactamente en el mismo punto de partida que los guías, en la esquina inferior izquierda. Puede desplazarse libremente por todo el mapa. 

Influencia del usuario

Cuando el usuario se acerca a un guía dentro de un radio determinado: aparecen pequeñas ondas circulares alrededor del guía representando una conversación; aumenta la probabilidad de que los turistas permanezcan cerca del guía (por ejemplo del 70% al 90%); disminuye considerablemente la probabilidad de que ocurra un Lévy Flight. Cuando el usuario se aleja, estas probabilidades vuelven gradualmente a la normalidad. La interacción debe modificar realmente el comportamiento probabilístico del sistema, no únicamente su apariencia. Construcción del paisaje El mapa comienza prácticamente vacío. A medida que los turistas recorren el territorio, el paisaje se construye lentamente. 

Mar 

El mar no aparece de inmediato, sino que comienza a formarse desde el inicio del recorrido. A medida que los guías y turistas avanzan hacia el volcán, el mar también avanza junto con ellos. Debe construirse mediante muchos círculos semitransparentes organizados como ondas perpendiculares al recorrido principal. Cada vez que el recorrido avanza un poco, aparece una nueva fila de círculos que se expande hacia ambos lados del camino. Estas ondas deben ir progresando lentamente desde el punto de inicio hasta el volcán, llenando la pantalla poco a poco conforme avanza la expedición. El crecimiento debe sentirse completamente orgánico, como si el recorrido fuera revelando el paisaje. Utilizar noise() para romper la perfección de las ondas y hacer que los bordes del mar sean naturales. Los círculos deben superponerse mediante transparencias para crear manchas suaves similares a una acuarela. Recorridos Mientras los turistas avanzan: dejan un rastro tenue y permanente; las zonas cercanas al volcán adquieren tonos cafés y terracotas; el resto del terreno se construye mediante manchas cálidas; múltiples recorridos deben mezclarse para crear un paisaje cada vez más rico. Cada ejecución debe producir un mapa distinto gracias a la aleatoriedad. Estética Toda la experiencia debe sentirse como una instalación artística generativa. La paleta de colores debe ser completamente coherente y agradable visualmente. Utilizar colores armónicos: mar en tonos celestes, turquesas y azules profundos; tierra en arenas, beige, ocres y terracotas; volcán en cafés cálidos con un brillo naranja sutil; guías en un rojo elegante con un halo suave; turistas como pequeños puntos gris oscuro o negro; usuario amarillo con un resplandor delicado. Todas las manchas deben mezclarse mediante transparencias para generar una apariencia similar a tinta o acuarela. El movimiento debe transmitir calma, contemplación y fluidez. 

La composición general debe verse muy cuidada y estéticamente agradable, como una obra de arte generativa, evitando colores estridentes o elementos que rompan la armonía visual. Requisitos técnicos Utilizar clases para Guía, Turista y Usuario. Utilizar noise() para el movimiento de los guías. Utilizar una caminata aleatoria para los turistas. Simular una distribución normal para mantener a los turistas alrededor del guía. Implementar Lévy Flights para los eventos excepcionales. Adaptarse automáticamente mediante windowResized(). 

Objetivo conceptual 

La experiencia debe transmitir que: existen muchas trayectorias posibles; pequeñas tendencias construyen caminos; la mayoría de los comportamientos permanece dentro de lo habitual; ocasionalmente ocurre un evento excepcional que permite explorar nuevos territorios; el usuario nunca controla completamente el sistema, sino que únicamente modifica las probabilidades de lo que puede suceder. El resultado final debe sentirse como una instalación artística interactiva, donde el paisaje emerge lentamente gracias al recorrido colectivo. El mar nace mediante ondas perpendiculares al camino, los recorridos construyen el territorio y toda la composición comunica que la incertidumbre surge de reglas probabilísticas y no del caos absoluto.


<img width="1869" height="915" alt="image" src="https://github.com/user-attachments/assets/cfa447b0-c13d-4d96-8782-f0ab272a7fd8" />

Inicialmente surgió este prototipo, el cual contaba inicialmente con los requerimientos excepto el mar y el fondo de mapa. Intenté en un principio guiar a la IA para crear el mapa, modificar los recorridos de forma más llamativa y manejar de mejor forma el recorrido.
Uno de los cambios más importantes fue el movimiento de los personajes. En un principio los turistas simplemente se movían de forma aleatoria alrededor del guía, pero luego decidí que era mejor usar una distribución normal para que la mayoría permaneciera cerca y solo unos pocos se alejaran más. También agregué los Lévy flights para que, muy de vez en cuando, un turista hiciera un recorrido mucho más largo y pudiera descubrir nuevas zonas del mapa.


<img width="1333" height="748" alt="image" src="https://github.com/user-attachments/assets/f22039dc-2244-41e1-aa97-f26630bdc5a7" />

Después de algunos prompts la IA me sale con lo siguiente para intentar implementar el mapa, pero el recorrido se veía feo, el mapa no se adaptaba a la pantalla y aún no salía el mar.

<img width="1866" height="881" alt="image" src="https://github.com/user-attachments/assets/f6d89468-467e-4234-812e-e57c32a5946f" />

```js
// ----------------------------------------------------------------------------------
// PEREGRINAJE AL VOLCÁN - Arte Generativo en p5.js (Con textura de mapa)
// ----------------------------------------------------------------------------------

let guides = [];
let user;
let bgTexture;       // Fondo con textura de mapa cartográfico
let trails;          // Capa donde el mar y la tierra depositan color progresivo
let startPt, volcanoPt;
let INFLUENCE_RADIUS;
let hintAlpha = 255;

function setup() {
  pixelDensity(1);
  createCanvas(windowWidth, windowHeight);
  frameRate(60);
  
  computeAnchors();

  // 1. Generamos la textura de mapa continuo
  buildMapTexture();

  // 2. Capa transparente acumulativa para el mar y los caminos
  trails = createGraphics(width, height);
  trails.clear();

  user = new UserAvatar();
  INFLUENCE_RADIUS = min(width, height) * 0.16;

  guides = [];
  let n = floor(random(4, 7)); // Entre 4 y 6 guías
  for (let i = 0; i < n; i++) {
    guides.push(new Guide(i));
  }
}

function computeAnchors() {
  startPt = createVector(width * 0.1, height * 0.92);
  volcanoPt = createVector(width * 0.85, height * 0.12);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  computeAnchors();
  buildMapTexture();
  INFLUENCE_RADIUS = min(width, height) * 0.16;
  
  let newTrails = createGraphics(width, height);
  newTrails.image(trails, 0, 0, width, height);
  trails = newTrails;
}

function draw() {
  let dt = min(deltaTime, 50);

  // 1. Textura base de mapa vintage
  image(bgTexture, 0, 0);

  // 2. Mar y huellas que los exploradores van descubriendo
  image(trails, 0, 0);

  // 3. Puntos fijos
  drawVolcano();
  drawStart();

  // 4. Entidades en movimiento
  user.update();
  for (let g of guides) {
    g.update(dt);
    g.display();
  }
  user.display();

  drawHint();
}

// ------------------------------ TEXTURA BASE DEL MAPA ------------------------------

function buildMapTexture() {
  bgTexture = createGraphics(width, height);
  bgTexture.noStroke();

  // Color base amarillo/beige dorado con variaciones suaves de noise
  let step = 8;
  for (let x = 0; x < width; x += step) {
    for (let y = 0; y < height; y += step) {
      let n = noise(x * 0.003, y * 0.003);
      let r = lerp(246, 238, n);
      let g = lerp(201, 185, n);
      let b = lerp(74,  90,  n);
      bgTexture.fill(r, g, b);
      bgTexture.rect(x, y, step + 1, step + 1);
    }
  }

  // Grano fino de papel/mapa antiguo
  let grains = floor((width * height) / 800);
  for (let i = 0; i < grains; i++) {
    let gx = random(width), gy = random(height);
    let shade = random() < 0.5 ? 0 : 255;
    bgTexture.fill(shade, random(5, 18));
    bgTexture.circle(gx, gy, random(1, 2.2));
  }

  // Curvas de nivel topográficas sutiles
  bgTexture.noFill();
  for (let i = 0; i < 8; i++) {
    bgTexture.stroke(140, 90, 30, 20);
    bgTexture.strokeWeight(1);
    let yBase = random(height);
    let seed = i * 45.2;
    bgTexture.beginShape();
    for (let x = 0; x <= width; x += 25) {
      let yy = yBase + (noise(x * 0.002, seed) - 0.5) * 160;
      bgTexture.curveVertex(x, yy);
    }
    bgTexture.endShape();
  }
}

// ------------------------------ PAISAJE GENERATIVO ------------------------------

function paintSeaWave(pos, prevPos, progress) {
  trails.noStroke();
  
  // Direccion de movimiento real
  let moveDir = p5.Vector.sub(pos, prevPos);
  if (moveDir.magSq() < 0.0001) {
    moveDir = p5.Vector.sub(volcanoPt, startPt);
  }
  
  // Vector perpendicular estricto (-y, x)
  let perp = createVector(-moveDir.y, moveDir.x).normalize();
  
  let waveWidth = map(progress, 0, 1, width * 0.15, width * 0.85);
  let numCircles = 12;
  
  for (let i = -numCircles; i <= numCircles; i++) {
    if (i === 0) continue; 
    
    let offsetFactor = (i / numCircles);
    let distFromPath = offsetFactor * waveWidth;
    
    let n = noise(pos.x * 0.005 + i, pos.y * 0.005 + progress);
    let offset = distFromPath + (n - 0.5) * 35;
    
    let wavePos = p5.Vector.add(pos, p5.Vector.mult(perp, offset));
    
    let tColor = constrain(map(abs(offset), 20, width * 0.6, 0, 1), 0, 1);
    let c1 = color(150, 215, 235, 10);
    let c2 = color(25, 80, 140, 6);
    let seaCol = lerpColor(c1, c2, tColor);
    
    trails.fill(seaCol);
    trails.circle(wavePos.x, wavePos.y, random(20, 40));
  }
}

function paintTrail(pos) {
  trails.noStroke();
  
  let dTotal = dist(startPt.x, startPt.y, volcanoPt.x, volcanoPt.y);
  let t = constrain(dist(pos.x, pos.y, startPt.x, startPt.y) / dTotal, 0, 1);
  
  let cSand = color(220, 150, 70, 18);
  let cTerracotta = color(160, 60, 35, 22);
  let trailCol = lerpColor(cSand, cTerracotta, t);
  
  trails.fill(trailCol);
  trails.circle(pos.x + random(-1.5, 1.5), pos.y + random(-1.5, 1.5), random(10, 20));
}

// ------------------------------ ANCLAS Y ELEMENTOS ------------------------------

function drawVolcano() {
  push();
  translate(volcanoPt.x, volcanoPt.y);

  // 1. Resplandor exterior (Caldera)
  noStroke();
  for (let r = 80; r > 10; r -= 10) {
    fill(240, 90, 30, map(r, 80, 10, 5, 45));
    ellipse(0, 15, r * 1.8, r * 0.9);
  }

  // 2. Silueta base y capas topográficas de la montaña
  stroke(90, 40, 25, 180);
  strokeWeight(1.2);
  fill(130, 60, 40, 230);
  
  // Lado sombreado (izquierdo)
  beginShape();
  vertex(-55, 45);
  curveVertex(-35, 10);
  vertex(-18, -20); // Cresta izq
  vertex(0, -18);   // Cráter
  vertex(0, 48);
  endShape(CLOSE);

  // Lado iluminado (derecho)
  fill(160, 75, 45, 230);
  beginShape();
  vertex(0, -18);
  vertex(18, -20);  // Cresta der
  curveVertex(35, 10);
  vertex(55, 45);
  vertex(0, 48);
  endShape(CLOSE);

  // 3. Trazos topográficos internos de la ladera
  noFill();
  stroke(80, 35, 20, 100);
  strokeWeight(1);
  ellipse(0, 15, 75, 25);
  ellipse(0, 30, 95, 30);

  // 4. Cráter y magma encendido
  noStroke();
  fill(50, 20, 15);
  ellipse(0, -19, 36, 12);
  
  fill(255, 100, 20);
  ellipse(0, -19, 26, 8);
  
  fill(255, 215, 0);
  ellipse(0, -19, 14, 4);

  // 5. Pluma de humo suave animada
  let t = millis() * 0.0012;
  for (let i = 0; i < 6; i++) {
    let yOff = (t * 25 + i * 18) % 90;
    let alpha = map(yOff, 0, 90, 120, 0);
    let size = map(yOff, 0, 90, 10, 38);
    let xOff = (noise(t + i) - 0.5) * 22;
    fill(90, 75, 70, alpha);
    circle(xOff, -22 - yOff, size);
  }

  pop();
}

function drawStart() {
  push();
  noFill();
  stroke(160, 60, 40, 180);
  strokeWeight(1.5);
  circle(startPt.x, startPt.y, 24);
  circle(startPt.x, startPt.y, 10);
  pop();
}

function drawHint() {
  if (hintAlpha <= 0) return;
  push();
  noStroke();
  fill(80, 55, 30, hintAlpha);
  textSize(13);
  textAlign(LEFT, TOP);
  text("WASD para moverte · Acércate a un guía (rojo)", 20, 24);
  pop();
  hintAlpha -= 0.3;
}

// --------------------------------- CLASES ---------------------------------

class Guide {
  constructor(id) {
    this.id = id;
    this.reset();
    this.progress = random(0, 0.1);
    this.tourists = [];
    
    let nT = floor(random(8, 13));
    for (let i = 0; i < nT; i++) {
      this.tourists.push(new Tourist(this));
    }
  }

  reset() {
    this.progress = 0;
    this.speed = random(0.000012, 0.000022);
    this.noiseSeed = random(5000);
    this.wobbleAmp = random(60, 130);
    this.pos = startPt.copy();
    this.prevPos = startPt.copy();

    this.stayCloseProb = 0.7;
    this.stayCloseTarget = 0.7;
    this.levyMult = 1.0;
    this.levyMultTarget = 1.0;

    this.rippleTimer = 0;
    this.ripples = [];
  }

  update(dt) {
    this.progress += this.speed * dt;
    
    if (this.progress >= 1) {
      this.reset();
      for (let t of this.tourists) t.repositionAtGuide();
    }

    this.prevPos = this.pos.copy();

    let base = p5.Vector.lerp(startPt, volcanoPt, this.progress);
    let dir = p5.Vector.sub(volcanoPt, startPt).normalize();
    let perp = createVector(-dir.y, dir.x);
    let n = noise(this.noiseSeed + this.progress * 3.5) - 0.5;
    let offset = perp.mult(n * this.wobbleAmp * 2);
    this.pos = p5.Vector.add(base, offset);

    // 1. PRIMERO proyectamos el mar azul en la perpendicular exacta
    paintSeaWave(this.pos, this.prevPos, this.progress);

    // Influencia probabilística
    let d = p5.Vector.dist(user.pos, this.pos);
    let near = d < INFLUENCE_RADIUS;
    
    this.stayCloseTarget = near ? 0.90 : 0.70;
    this.levyMultTarget = near ? 0.10 : 1.0;
    this.stayCloseProb = lerp(this.stayCloseProb, this.stayCloseTarget, 0.03);
    this.levyMult = lerp(this.levyMult, this.levyMultTarget, 0.03);

    if (near) {
      this.rippleTimer -= dt;
      if (this.rippleTimer <= 0) {
        this.ripples.push({ r: 0, alpha: 180 });
        this.rippleTimer = 450;
      }
    }

    for (let i = this.ripples.length - 1; i >= 0; i--) {
      let rp = this.ripples[i];
      rp.r += dt * 0.04;
      rp.alpha -= dt * 0.12;
      if (rp.alpha <= 0) this.ripples.splice(i, 1);
    }

    // 2. DESPUÉS se actualizan los turistas (que estampan el camino ocre encima)
    for (let t of this.tourists) t.update(dt);
  }

  display() {
    for (let rp of this.ripples) {
      noFill();
      stroke(190, 50, 40, rp.alpha);
      strokeWeight(1.2);
      circle(this.pos.x, this.pos.y, rp.r * 2);
    }

    for (let t of this.tourists) t.display();

    noStroke();
    fill(200, 40, 40, 230);
    circle(this.pos.x, this.pos.y, 14);
    fill(200, 40, 40, 50);
    circle(this.pos.x, this.pos.y, 26);
  }
}

class Tourist {
  constructor(guide) {
    this.guide = guide;
    this.repositionAtGuide();
    this.vel = createVector(0, 0);
    this.desiredDist = 20;
    this.recalcTimer = 0;
    this.state = "normal";
    this.flightTarget = null;
    this.flightTimer = 0;
  }

  repositionAtGuide() {
    this.pos = this.guide.pos.copy().add(p5.Vector.random2D().mult(15));
    this.state = "normal";
  }

  recalcDesired() {
    if (random() < this.guide.stayCloseProb) {
      this.desiredDist = abs(randomGaussian(16, 7));
    } else {
      this.desiredDist = abs(randomGaussian(48, 15));
    }
  }

  update(dt) {
    this.recalcTimer -= dt;
    if (this.recalcTimer <= 0) {
      this.recalcDesired();
      this.recalcTimer = random(800, 2000);
    }

    if (this.state === "normal") {
      let pFrame = 1 - pow(1 - 0.005, dt / 1000);
      pFrame *= this.guide.levyMult;

      if (random() < pFrame) {
        this.state = "flight";
        let ang = random(TWO_PI);
        let stepDist = 50 / pow(random(0.01, 1), 1 / 1.3);
        stepDist = constrain(stepDist, 120, max(width, height) * 0.7);
        
        this.flightTarget = createVector(
          constrain(this.pos.x + cos(ang) * stepDist, 20, width - 20),
          constrain(this.pos.y + sin(ang) * stepDist, 20, height - 20)
        );
        this.flightTimer = random(1500, 3200);
      } else {
        let toGuide = p5.Vector.sub(this.guide.pos, this.pos);
        let d = toGuide.mag();
        let steer = createVector(0, 0);
        
        if (d > 0.01) {
          steer = toGuide.copy().normalize().mult(d - this.desiredDist).mult(0.02);
        }
        
        let jitter = p5.Vector.random2D().mult(0.3);
        this.vel.add(steer).add(jitter);
        this.vel.limit(1.0);
        this.pos.add(p5.Vector.mult(this.vel, dt * 0.04));
        this.vel.mult(0.92);
      }
    } else if (this.state === "flight") {
      let toTarget = p5.Vector.sub(this.flightTarget, this.pos);
      if (toTarget.mag() > 4) {
        this.pos.add(toTarget.normalize().mult(dt * 0.18));
      }
      this.flightTimer -= dt;
      if (this.flightTimer <= 0) this.state = "returning";

    } else if (this.state === "returning") {
      let toGuide = p5.Vector.sub(this.guide.pos, this.pos);
      if (toGuide.mag() < this.desiredDist + 10) {
        this.state = "normal";
      } else {
        this.pos.add(toGuide.normalize().mult(dt * 0.035));
      }
    }

    this.pos.x = constrain(this.pos.x, 5, width - 5);
    this.pos.y = constrain(this.pos.y, 5, height - 5);

    paintTrail(this.pos);
  }

  display() {
    noStroke();
    fill(25, 25, 25, 220);
    circle(this.pos.x, this.pos.y, this.state === "flight" ? 5.5 : 4.5);
  }
}

class UserAvatar {
  constructor() {
    this.pos = startPt.copy();
    this.speed = 2.6;
  }

  update() {
    let v = createVector(0, 0);
    if (keyIsDown(87)) v.y -= 1; // W
    if (keyIsDown(83)) v.y += 1; // S
    if (keyIsDown(65)) v.x -= 1; // A
    if (keyIsDown(68)) v.x += 1; // D
    
    if (v.mag() > 0) {
      v.normalize().mult(this.speed);
      this.pos.add(v);
    }
    
    this.pos.x = constrain(this.pos.x, 10, width - 10);
    this.pos.y = constrain(this.pos.y, 10, height - 10);
  }

  display() {
    noStroke();
    fill(255, 215, 0, 50);
    circle(this.pos.x, this.pos.y, 30);
    fill(255, 215, 0, 230);
    circle(this.pos.x, this.pos.y, 14);
  }
}

```

Seguí probando y modificando varias cosas para que se viera el volcán mejor, se llenara más el mapa y fueran colores más agradables.

<img width="1901" height="780" alt="image" src="https://github.com/user-attachments/assets/37641ce8-e33f-4540-adc6-02d165cd18f1" />


Otra cosa que cambió bastante fue la interacción. Al comienzo el usuario solo generaba unas ondas cuando se acercaba a un guía porque quería representar una conversación. Después entendí que el ejercicio pedía que la interacción modificara realmente el sistema, así que cambié esa parte para que la presencia del usuario alterara las probabilidades del comportamiento de los turistas, haciendo que permanecieran más cerca del guía y reduciendo la posibilidad de que ocurrieran desviaciones largas.

También fui ajustando la parte visual. Probé diferentes colores, tamaños y formas de construir el paisaje hasta llegar a una estética que se sintiera más coherente con el festival. En lugar de mostrar el mapa completo desde el inicio, hice que el mar y los recorridos fueran apareciendo poco a poco a medida que los personajes avanzan, para que el paisaje se construya con las trayectorias del sistema y cada ejecución sea diferente.

En general, el proceso fue ir tomando una idea inicial bastante simple y convertirla poco a poco en un sistema donde las probabilidades, el movimiento y la interacción fueran los que comunicaran el concepto de incertidumbre, en lugar de hacerlo únicamente con elementos visuales.


<img width="1902" height="774" alt="image" src="https://github.com/user-attachments/assets/9aa04aa5-3ff0-4231-9ecd-d5d0006fc2e8" />

Cambié la forma en la que se generaba el mar ya que sentia que al ser una gradiente definida le quitaba ese factor de que fuera aun más único cada vez que se ejecutaba. Le puse una paleta de colores claros y oscuros segun su cercanía al recorrido y al volcán, donde se formaran diferentes olas de colores hasta llenar el mar.

```
// ----------------------------------------------------------------------------------
// PEREGRINAJE AL VOLCÁN - Arte Generativo en p5.js
// ----------------------------------------------------------------------------------

let guides = [];
let user;
let bgTexture;      // Capa 0: Fondo mapa beige vacío
let seaLayer;       // Capa 1: Mar orgánico + ondas del volcán y halos de desvío
let trailsLayer;    // Capa 2: Puntos de guías y turistas
let startPt, volcanoPt;
let INFLUENCE_RADIUS;
let hintAlpha = 255;

// Paleta Verde Turquesa vibrante y artística para desvíos
const TURQUOISE_DETOUR_PALETTE = [
  [0, 230, 180],    // Turquesa brillante
  [26, 188, 156],   // Verde Turquesa
  [72, 201, 176],   // Menta luminoso
  [0, 206, 209],    // Turquesa oscuro
  [163, 228, 215]   // Menta suave / Pastel
];

// Paleta de amarillos/dorados para turistas
const YELLOW_PALETTE = [
  [255, 220, 80],
  [240, 190, 60],
  [230, 165, 45],
  [250, 230, 140],
  [215, 170, 65]
];

// Paleta del camino de los guías
const DARK_TRAIL_PALETTE = [
  [110, 45, 30],
  [85, 35, 25],
  [145, 65, 35],
  [175, 90, 45],
  [195, 120, 55]
];

// Paletas de Mar armonizadas
const LIGHT_SEA_PALETTE = [
  [180, 230, 240], 
  [160, 220, 235], 
  [140, 205, 225], 
  [200, 240, 248]  
];

const DARK_SEA_PALETTE = [
  [25, 70, 120],   
  [35, 95, 150],   
  [20, 55, 100],   
  [45, 110, 165]   
];

function setup() {
  pixelDensity(1);
  createCanvas(windowWidth, windowHeight);
  frameRate(60);
  
  colorMode(RGB, 255);
  computeAnchors();
  buildMapTexture();

  seaLayer = createGraphics(width, height);
  seaLayer.clear();

  trailsLayer = createGraphics(width, height);
  trailsLayer.clear();

  user = new UserAvatar();
  // Radio reducido a la mitad (antes era 0.16)
  INFLUENCE_RADIUS = min(width, height) * 0.08;

  guides = [];
  let n = floor(random(4, 7));
  for (let i = 0; i < n; i++) {
    guides.push(new Guide(i));
  }
}

function computeAnchors() {
  startPt = createVector(width * 0.1, height * 0.92);
  volcanoPt = createVector(width * 0.85, height * 0.12);
}

function windowResized() {
  let oldW = width;
  let oldH = height;

  resizeCanvas(windowWidth, windowHeight);
  computeAnchors();
  buildMapTexture();
  INFLUENCE_RADIUS = min(width, height) * 0.08;
  
  let newSea = createGraphics(width, height);
  newSea.image(seaLayer, 0, 0, width, height);
  seaLayer = newSea;

  let newTrails = createGraphics(width, height);
  newTrails.image(trailsLayer, 0, 0, width, height);
  trailsLayer = newTrails;

  user.pos.x = map(user.pos.x, 0, oldW, 0, width);
  user.pos.y = map(user.pos.y, 0, oldH, 0, height);
}

function draw() {
  let dt = min(deltaTime, 50);

  // Capa 0: Fondo
  image(bgTexture, 0, 0);

  // 1. Emitir aros expansivos de circulitos azules desde el volcán
  paintVolcanoSeaRipples();

  // Capa 1: Mar acumulativo
  image(seaLayer, 0, 0);

  // Capa 2: Senderos y manchas
  image(trailsLayer, 0, 0);

  // Capa 3: Anclas fijas
  drawVolcano();
  drawStart();

  // Capa 4: Personajes
  user.update(dt);
  for (let g of guides) {
    g.update(dt);
    g.display();
  }
  user.display();

  drawHint();
}

// ------------------------------ CAPA 0: TEXTURA BASE ------------------------------

function buildMapTexture() {
  bgTexture = createGraphics(width, height);
  bgTexture.pixelDensity(1);
  bgTexture.noStroke();

  let step = 8;
  for (let x = 0; x < width + step; x += step) {
    for (let y = 0; y < height + step; y += step) {
      let n = noise(x * 0.003, y * 0.003);
      let r = lerp(246, 238, n);
      let g = lerp(201, 185, n);
      let b = lerp(74,  90,  n);
      bgTexture.fill(r, g, b);
      bgTexture.rect(x, y, step, step);
    }
  }

  let grains = floor((width * height) / 600);
  for (let i = 0; i < grains; i++) {
    let gx = random(width), gy = random(height);
    let shade = random() < 0.5 ? 0 : 255;
    bgTexture.fill(shade, random(5, 18));
    bgTexture.circle(gx, gy, random(1, 2));
  }

  bgTexture.noFill();
  for (let i = 0; i < 8; i++) {
    bgTexture.stroke(140, 90, 30, 20);
    bgTexture.strokeWeight(1);
    let yBase = random(height);
    let seed = i * 45.2;
    bgTexture.beginShape();
    for (let x = 0; x <= width + 50; x += 30) {
      let yy = yBase + (noise(x * 0.002, seed) - 0.5) * 160;
      bgTexture.curveVertex(x, yy);
    }
    bgTexture.endShape();
  }
}

// ------------------------------ PAISAJE GENERATIVO ------------------------------

function paintVolcanoSeaRipples() {
  seaLayer.noStroke();

  let maxRadius = max(width, height) * 0.9;
  
  for (let wave = 0; wave < 3; wave++) {
    let baseR = ((frameCount * 1.5) + wave * (maxRadius / 3)) % maxRadius;
    let dots = floor(map(baseR, 0, maxRadius, 16, 48));

    for (let i = 0; i < dots; i++) {
      let angle = (TWO_PI / dots) * i + noise(frameCount * 0.01, wave) * 0.5;
      let rOffset = baseR + (noise(i, frameCount * 0.02) - 0.5) * 20;
      
      let x = volcanoPt.x + cos(angle) * rOffset;
      let y = volcanoPt.y + sin(angle) * rOffset;

      let c = random() < 0.5 ? random(LIGHT_SEA_PALETTE) : random(DARK_SEA_PALETTE);
      let alpha = map(rOffset, 0, maxRadius, random(30, 70), random(1, 6));
      
      seaLayer.fill(c[0], c[1], c[2], alpha);
      let dotSize = map(rOffset, 0, maxRadius, random(6, 12), random(14, 28));
      seaLayer.circle(x, y, dotSize);
    }
  }
}

function paintSeaWave(pos, prevPos, progress) {
  seaLayer.noStroke();
  
  let moveDir = p5.Vector.sub(pos, prevPos);
  if (moveDir.magSq() < 0.0001) {
    moveDir = p5.Vector.sub(volcanoPt, startPt);
  }
  
  let perp = createVector(-moveDir.y, moveDir.x).normalize();
  let maxWaveWidth = map(progress, 0, 1, width * 0.25, width * 1.2);
  let numCircles = 10;
  let wavePulse = (sin(millis() * 0.003) + 1) * 0.5;

  for (let i = -numCircles; i <= numCircles; i++) {
    if (i === 0) continue; 
    
    let offsetFactor = (i / numCircles);
    let distFromPath = offsetFactor * maxWaveWidth * lerp(0.6, 1.0, wavePulse);
    let n = noise(pos.x * 0.005 + i, pos.y * 0.005 + progress);
    let offset = distFromPath + (n - 0.5) * 45;
    let wavePos = p5.Vector.add(pos, p5.Vector.mult(perp, offset));
    
    let dTotal = dist(startPt.x, startPt.y, volcanoPt.x, volcanoPt.y);
    let distToVolcanoFactor = constrain(dist(wavePos.x, wavePos.y, startPt.x, startPt.y) / dTotal, 0, 1);
    
    let seaCol;
    if (random() > distToVolcanoFactor) {
      let c = random(LIGHT_SEA_PALETTE);
      seaCol = color(c[0], c[1], c[2], random(5, 12));
    } else {
      let c = random(DARK_SEA_PALETTE);
      seaCol = color(c[0], c[1], c[2], random(4, 10));
    }
    
    seaLayer.fill(seaCol);
    let dynamicSize = map(abs(offset), 0, maxWaveWidth, random(10, 18), random(28, 48));
    seaLayer.circle(wavePos.x, wavePos.y, dynamicSize);
  }
}

function paintArtisticTurquoiseHalo(pos, currentRadius) {
  seaLayer.noStroke();

  let dotsInRing = floor(map(currentRadius, 10, 180, 20, 60));
  for (let i = 0; i < dotsInRing; i++) {
    let ang = (TWO_PI / dotsInRing) * i + random(-0.15, 0.15);
    let r = currentRadius + (noise(i, frameCount * 0.05) - 0.5) * 25;
    
    let x = pos.x + cos(ang) * r;
    let y = pos.y + sin(ang) * r;

    let col = random(TURQUOISE_DETOUR_PALETTE);
    let alpha = map(currentRadius, 10, 180, random(40, 90), random(10, 30));

    seaLayer.fill(col[0], col[1], col[2], alpha);
    let sz = random(6, 18);
    seaLayer.circle(x, y, sz);
  }

  for (let i = 0; i < 6; i++) {
    let ang = random(TWO_PI);
    let r = currentRadius + random(-40, 40);
    let x = pos.x + cos(ang) * r;
    let y = pos.y + sin(ang) * r;

    let col = random(TURQUOISE_DETOUR_PALETTE);
    seaLayer.fill(col[0], col[1], col[2], random(15, 50));
    seaLayer.circle(x, y, random(3, 8));
  }
}

function paintGuideTrail(pos) {
  trailsLayer.noStroke();
  let c = random(DARK_TRAIL_PALETTE);
  trailsLayer.fill(c[0], c[1], c[2], random(25, 55));
  trailsLayer.circle(pos.x + random(-12, 12), pos.y + random(-12, 12), random(12, 26));
}

function paintTouristDots(pos) {
  trailsLayer.noStroke();
  let col = random(YELLOW_PALETTE);
  trailsLayer.fill(col[0], col[1], col[2], random(20, 50));
  trailsLayer.circle(pos.x + random(-2, 2), pos.y + random(-2, 2), random(5, 12));
}

// ------------------------------ ELEMENTOS FIJOS ------------------------------

function drawVolcano() {
  push();
  translate(volcanoPt.x, volcanoPt.y);

  noStroke();
  for (let r = 80; r > 10; r -= 10) {
    fill(240, 90, 30, map(r, 80, 10, 5, 45));
    ellipse(0, 15, r * 1.8, r * 0.9);
  }

  stroke(90, 40, 25, 180);
  strokeWeight(1.2);
  fill(130, 60, 40, 230);
  
  beginShape();
  vertex(-55, 45);
  curveVertex(-35, 10);
  vertex(-18, -20);
  vertex(0, -18);
  vertex(0, 48);
  endShape(CLOSE);

  fill(160, 75, 45, 230);
  beginShape();
  vertex(0, -18);
  vertex(18, -20);
  curveVertex(35, 10);
  vertex(55, 45);
  vertex(0, 48);
  endShape(CLOSE);

  noFill();
  stroke(80, 35, 20, 100);
  strokeWeight(1);
  ellipse(0, 15, 75, 25);
  ellipse(0, 30, 95, 30);

  noStroke();
  fill(50, 20, 15);
  ellipse(0, -19, 36, 12);
  fill(255, 100, 20);
  ellipse(0, -19, 26, 8);
  fill(255, 215, 0);
  ellipse(0, -19, 14, 4);

  let t = millis() * 0.0012;
  for (let i = 0; i < 6; i++) {
    let yOff = (t * 25 + i * 18) % 90;
    let alpha = map(yOff, 0, 90, 120, 0);
    let size = map(yOff, 0, 90, 10, 38);
    let xOff = (noise(t + i) - 0.5) * 22;
    fill(90, 75, 70, alpha);
    circle(xOff, -22 - yOff, size);
  }

  pop();
}

function drawStart() {
  push();
  noFill();
  stroke(160, 60, 40, 180);
  strokeWeight(1.5);
  circle(startPt.x, startPt.y, 24);
  circle(startPt.x, startPt.y, 10);
  pop();
}

function drawHint() {
  if (hintAlpha <= 0) return;
  push();
  noStroke();
  fill(80, 55, 30, hintAlpha);
  textSize(13);
  textAlign(LEFT, TOP);
  text("WASD para moverte · Sigue las huellas marcadas", 20, 24);
  pop();
  hintAlpha -= 0.3;
}

// --------------------------------- CLASES ---------------------------------

class Guide {
  constructor(id) {
    this.id = id;
    this.reset();
    this.progress = random(0, 0.1);
    this.tourists = [];
    
    let nT = floor(random(8, 13));
    for (let i = 0; i < nT; i++) {
      this.tourists.push(new Tourist(this));
    }
  }

  reset() {
    this.progress = 0;
    this.direction = 1;
    this.speed = random(0.000012, 0.000022);
    this.noiseSeed = random(5000);
    this.wobbleAmp = random(60, 130);
    this.pos = startPt.copy();
    this.prevPos = startPt.copy();

    this.state = "marching"; 
    this.detourTarget = null;
    this.detourTimer = 0;
    this.haloRadius = 10;
    this.pathPos = startPt.copy();

    this.stayCloseProb = 0.7;
    this.stayCloseTarget = 0.7;
    this.levyMult = 1.0;
    this.levyMultTarget = 1.0;

    this.rippleTimer = 0;
    this.ripples = [];
  }

  update(dt) {
    this.prevPos = this.pos.copy();

    if (this.state === "marching") {
      this.progress += this.speed * dt * this.direction;

      if (this.progress >= 1) {
        this.progress = 1;
        this.direction = -1;
      } else if (this.progress <= 0 && this.direction === -1) {
        this.progress = 0;
        this.direction = 1;
      }

      let base = p5.Vector.lerp(startPt, volcanoPt, this.progress);
      let dir = p5.Vector.sub(volcanoPt, startPt).normalize();
      let perp = createVector(-dir.y, dir.x);
      let n = noise(this.noiseSeed + this.progress * 3.5) - 0.5;
      let offset = perp.mult(n * this.wobbleAmp * 2);
      this.pathPos = p5.Vector.add(base, offset);
      this.pos = this.pathPos.copy();

      if (random() < 0.0015) {
        this.state = "detouring";
        let detourAng = random(TWO_PI);
        let detourDist = random(50, 110);
        this.detourTarget = createVector(
          constrain(this.pos.x + cos(detourAng) * detourDist, 30, width - 30),
          constrain(this.pos.y + sin(detourAng) * detourDist, 30, height - 30)
        );
      }

    } else if (this.state === "detouring") {
      let toTarget = p5.Vector.sub(this.detourTarget, this.pos);
      if (toTarget.mag() > 3) {
        this.pos.add(toTarget.normalize().mult(dt * 0.04));
      } else {
        this.state = "resting";
        this.detourTimer = random(2500, 5000);
        this.haloRadius = 10;
      }

    } else if (this.state === "resting") {
      this.detourTimer -= dt;

      if (this.haloRadius < 180) {
        paintArtisticTurquoiseHalo(this.pos, this.haloRadius);
        this.haloRadius += dt * 0.06;
      }

      if (this.detourTimer <= 0) {
        this.state = "returning";
      }

    } else if (this.state === "returning") {
      let toPath = p5.Vector.sub(this.pathPos, this.pos);
      if (toPath.mag() > 3) {
        this.pos.add(toPath.normalize().mult(dt * 0.04));
      } else {
        this.state = "marching";
      }
    }

    paintSeaWave(this.pos, this.prevPos, this.progress);
    paintGuideTrail(this.pos);

    let d = p5.Vector.dist(user.pos, this.pos);
    let near = d < INFLUENCE_RADIUS;
    
    if (near) {
      user.isLearning = true;
    }

    this.stayCloseTarget = near ? 0.90 : 0.70;
    this.levyMultTarget = near ? 0.10 : 1.0;
    this.stayCloseProb = lerp(this.stayCloseProb, this.stayCloseTarget, 0.03);
    this.levyMult = lerp(this.levyMult, this.levyMultTarget, 0.03);

    if (near) {
      this.rippleTimer -= dt;
      if (this.rippleTimer <= 0) {
        this.ripples.push({ r: 0, alpha: 180 });
        this.rippleTimer = 450;
      }
    }

    for (let i = this.ripples.length - 1; i >= 0; i--) {
      let rp = this.ripples[i];
      rp.r += dt * 0.04;
      rp.alpha -= dt * 0.12;
      if (rp.alpha <= 0) this.ripples.splice(i, 1);
    }

    for (let t of this.tourists) t.update(dt);
  }

  display() {
    for (let rp of this.ripples) {
      noFill();
      stroke(190, 50, 40, rp.alpha);
      strokeWeight(1.2);
      circle(this.pos.x, this.pos.y, rp.r * 2);
    }

    for (let t of this.tourists) t.display();

    noStroke();
    fill(200, 40, 40, 230);
    circle(this.pos.x, this.pos.y, 14);
    fill(200, 40, 40, 50);
    circle(this.pos.x, this.pos.y, 26);
  }
}

class Tourist {
  constructor(guide) {
    this.guide = guide;
    this.repositionAtGuide();
    this.vel = createVector(0, 0);
    this.desiredDist = 20;
    this.recalcTimer = 0;
    this.state = "normal";
    this.flightTarget = null;
    this.flightTimer = 0;
  }

  repositionAtGuide() {
    this.pos = this.guide.pos.copy().add(p5.Vector.random2D().mult(15));
    this.state = "normal";
  }

  recalcDesired() {
    if (random() < this.guide.stayCloseProb) {
      this.desiredDist = abs(randomGaussian(16, 7));
    } else {
      this.desiredDist = abs(randomGaussian(48, 15));
    }
  }

  update(dt) {
    this.recalcTimer -= dt;
    if (this.recalcTimer <= 0) {
      this.recalcDesired();
      this.recalcTimer = random(800, 2000);
    }

    if (this.state === "normal") {
      let pFrame = 1 - pow(1 - 0.005, dt / 1000);
      pFrame *= this.guide.levyMult;

      if (random() < pFrame) {
        this.state = "flight";
        let ang = random(TWO_PI);
        let stepDist = 50 / pow(random(0.01, 1), 1 / 1.3);
        stepDist = constrain(stepDist, 120, max(width, height) * 0.7);
        
        this.flightTarget = createVector(
          constrain(this.pos.x + cos(ang) * stepDist, 20, width - 20),
          constrain(this.pos.y + sin(ang) * stepDist, 20, height - 20)
        );
        this.flightTimer = random(1500, 3200);
      } else {
        let toGuide = p5.Vector.sub(this.guide.pos, this.pos);
        let d = toGuide.mag();
        let steer = createVector(0, 0);
        
        if (d > 0.01) {
          steer = toGuide.copy().normalize().mult(d - this.desiredDist).mult(0.02);
        }
        
        let jitter = p5.Vector.random2D().mult(0.3);
        this.vel.add(steer).add(jitter);
        this.vel.limit(1.0);
        this.pos.add(p5.Vector.mult(this.vel, dt * 0.04));
        this.vel.mult(0.92);
      }
    } else if (this.state === "flight") {
      let toTarget = p5.Vector.sub(this.flightTarget, this.pos);
      if (toTarget.mag() > 4) {
        this.pos.add(toTarget.normalize().mult(dt * 0.18));
      }
      this.flightTimer -= dt;
      if (this.flightTimer <= 0) this.state = "returning";

    } else if (this.state === "returning") {
      let toGuide = p5.Vector.sub(this.guide.pos, this.pos);
      if (toGuide.mag() < this.desiredDist + 10) {
        this.state = "normal";
      } else {
        this.pos.add(toGuide.normalize().mult(dt * 0.035));
      }
    }

    this.pos.x = constrain(this.pos.x, 5, width - 5);
    this.pos.y = constrain(this.pos.y, 5, height - 5);

    paintTouristDots(this.pos);
  }

  display() {
    noStroke();
    fill(25, 25, 25, 220);
    circle(this.pos.x, this.pos.y, this.state === "flight" ? 5.5 : 4.5);
  }
}

class UserAvatar {
  constructor() {
    this.pos = startPt.copy();
    this.speed = 0.08; // Velocidad pausada, alineada al ritmo de movimiento del grupo
    this.isLearning = false;
    this.rainbowHue = 0;
  }

  // Verifica si un punto objetivo está sobre un camino dibujado o cerca de un guía/turista
  isOnTrail(targetPos) {
    // 1. Inmunidad en el punto de partida para poder comenzar a caminar
    if (p5.Vector.dist(targetPos, startPt) < 30) return true;

    // 2. Comprobar si hay rastro en la capa de senderos
    trailsLayer.loadPixels();
    let px = floor(constrain(targetPos.x, 0, width - 1));
    let py = floor(constrain(targetPos.y, 0, height - 1));
    let idx = 4 * (py * width + px);
    let alpha = trailsLayer.pixels[idx + 3];

    if (alpha > 5) return true;

    // 3. Permite avanzar directamente sobre la posición actual de guías o turistas
    for (let g of guides) {
      if (p5.Vector.dist(targetPos, g.pos) < 25) return true;
      for (let t of g.tourists) {
        if (p5.Vector.dist(targetPos, t.pos) < 15) return true;
      }
    }

    return false;
  }

  update(dt) {
    let v = createVector(0, 0);
    if (keyIsDown(87)) v.y -= 1; // W
    if (keyIsDown(83)) v.y += 1; // S
    if (keyIsDown(65)) v.x -= 1; // A
    if (keyIsDown(68)) v.x += 1; // D
    
    if (v.mag() > 0) {
      v.normalize().mult(this.speed * dt);
      let nextPos = p5.Vector.add(this.pos, v);

      // Solo avanza si la siguiente posición está sobre un sendero o cerca de caminantes
      if (this.isOnTrail(nextPos)) {
        this.pos = nextPos;
      }
    }
    
    this.pos.x = constrain(this.pos.x, 10, width - 10);
    this.pos.y = constrain(this.pos.y, 10, height - 10);

    this.isLearning = false;
  }

  display() {
    noStroke();

    if (this.isLearning) {
      colorMode(HSB, 360, 100, 100);
      this.rainbowHue = (this.rainbowHue + 3) % 360;
      
      fill(this.rainbowHue, 80, 100, 0.25);
      circle(this.pos.x, this.pos.y, 34);
      
      fill(this.rainbowHue, 85, 95);
      circle(this.pos.x, this.pos.y, 15);
      
      colorMode(RGB, 255);
    } else {
      fill(46, 204, 113, 60);
      circle(this.pos.x, this.pos.y, 30);
      
      fill(46, 204, 113, 230);
      circle(this.pos.x, this.pos.y, 14);
    }
  }
}
```

<img width="1226" height="742" alt="image" src="https://github.com/user-attachments/assets/2aa5ac14-6246-4e3e-aa0e-997b5bbb0b36" />

Finalmente llegué a un diseño que representaba el evento de la forma en la que quería, aunque hubo dificultades en el factor estético que fue un poco frustrante expresar a la IA.

Principalmente en el desarrollo del proyecto encontré las siguientes dificultades:

| Dificultad / Problema | Causa raíz | Solución implementada |
|-----------------------|------------|------------------------|
| Traducir la visión creativa a prompts de código | Resultaba difícil describir con palabras conceptos visuales abstractos (como la sensación de un mapa antiguo o un movimiento orgánico) para convertirlos en lógica de programación. | Se descompuso cada idea visual en parámetros concretos como colores específicos, ruido de Perlin, distribuciones gaussianas y el uso de capas independientes con `createGraphics`. |
| Ajustar la estética sin perder la coherencia | Al modificar colores, texturas o formas para mejorar el resultado visual, era fácil romper la armonía del mapa o dificultar su lectura. | Se definió una paleta inspirada en cartografía vintage: tonos beige para la base, colores oscuros para los personajes y acuarelas suaves en azules y ocres para construir el paisaje. |
| Hacer la simulación más interesante visualmente | El movimiento de los puntos podía sentirse como un algoritmo abstracto sin suficiente personalidad ni narrativa. | Se añadieron elementos visuales como rastros del recorrido, halos de influencia, ondas cuando el usuario interactúa con los guías y efectos que hacen más evidente la construcción progresiva del paisaje. |
| Adaptar la experiencia a un contexto de feria | En un festival los visitantes deben comprender rápidamente cómo interactuar sin necesidad de leer instrucciones largas. | Se implementó un control simple con las teclas **WASD**, un mensaje inicial de ayuda y retroalimentación visual inmediata mediante ondas cuando el usuario se acerca a un guía. |


## Autoevaluación:

| Criterio | Cumplo | No cumplo | Evidencia |
|---------|:------:|:---------:|-----------|
| **Encargo completo: interpreto los cinco momentos dentro de un mismo sistema visual.** | ☑ | ☐ | Toda la experiencia ocurre en un único sistema visual ("Peregrinaje al Volcán"). **Posibilidad:** los turistas presentan movimiento aleatorio alrededor de los guías. **Tendencia:** los guías siguen repetidamente una ruta hacia el volcán. **Normalidad:** la mayoría de los turistas permanece cerca del guía mediante una distribución normal de distancias. **Excepción:** algunos turistas realizan *Lévy flights*, explorando regiones lejanas antes de regresar. **Influencia:** la cercanía del usuario modifica las probabilidades del comportamiento colectivo sin controlar completamente el sistema. |
| **Simulación con intención: utilizo al menos tres conceptos de la unidad para comunicar las ideas del encargo.** | ☑ | ☐ | Se combinan varios conceptos: **ruido Perlin** para generar variaciones suaves en el recorrido de los guías y la textura del paisaje; **distribución normal** mediante `randomGaussian()` para mantener a los turistas cerca del guía; **Lévy flight** para producir desplazamientos excepcionales de algunos turistas. Además, existe una caminata con componente aleatoria en los movimientos de los agentes. |
| **Interacción significativa: la interacción modifica el comportamiento o las probabilidades del sistema, que también funciona sin intervención.** | ☑ | ☐ | El usuario no mueve directamente a los personajes. Al acercarse a un guía cambia parámetros como `stayCloseProb` y `levyMult`, alterando la probabilidad de que los turistas permanezcan agrupados o realicen vuelos de Lévy. Cuando no hay interacción, la simulación continúa ejecutándose de forma autónoma. |
| **Prototipo funcional: la experiencia puede ejecutarse y recorrerse completa sin errores que impidan comprenderla.** | ☑ | ☐ | El sketch funciona en tiempo real, ocupa toda la pantalla, mantiene la simulación activa y permite recorrer la experiencia mediante teclado (WASD), observando cómo la presencia del usuario modifica el sistema. |
| **Proceso documentado: la bitácora evidencia avances, decisiones, dificultades, soluciones, uso de IA y enlace al prototipo.** | ☑ *(si la tienes)* | ☐ | La bitácora incluye el proceso de diseño, iteraciones del comportamiento de guías y turistas, decisiones sobre las distribuciones utilizadas, dificultades técnicas, apoyo de IA durante el desarrollo y el enlace al prototipo en p5.js. Si aún no tienes la bitácora, este sería el único criterio que no podrías marcar como cumplido. |
