

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

**Idea final:** 

La experiencia propone representar un recorrido interactivo mediante un mapa. El escenario tendrá un punto de partida ubicado en la esquina inferior izquierda y un destino en la esquina superior derecha, representado por un volcán. Inspirado en los recorridos del Volcanic Attitude Festival, el mapa simboliza un territorio en constante transformación, donde diferentes formas de aleatoriedad generan distintas maneras de explorar el paisaje.

Dentro del mapa se desplazarán varios puntos rojos que simbolizan a los guías. Estos seguirán una trayectoria desde el inicio hasta el volcán utilizando un movimiento orgánico generado con ruido de Perlin, por lo que, aunque todos persiguen el mismo destino, cada recorrido será ligeramente diferente y parecerá surgir de manera natural.

A cada guía lo acompañarán varios puntos negros que representan a los turistas. Estos se moverán mediante una caminata aleatoria, pero su posición respecto al guía seguirá una distribución normal: la mayoría permanecerá cerca de él, mientras que solo unos pocos se alejarán temporalmente antes de volver al grupo. Esto generará agrupaciones dinámicas que reflejan el comportamiento habitual de un recorrido guiado.

De manera ocasional, y con una probabilidad muy baja, uno de los turistas realizará un desplazamiento mucho mayor (Lévy flight), alejándose del grupo para explorar una zona distante del mapa. Estos eventos excepcionales permitirán descubrir partes del paisaje que normalmente permanecerían ocultas, representando cómo un evento improbable puede abrir nuevas posibilidades.

El usuario interactuará con la experiencia controlando un punto amarillo mediante las teclas WASD, permitiéndole desplazarse libremente por el mapa. Cuando se aproxime a uno de los guías, aparecerán pequeñas ondas a su alrededor para representar una interacción o conversación entre ambos. Sin embargo, esta interacción no será únicamente visual: la presencia del usuario modificará las probabilidades del sistema. Al acercarse a un guía aumentará la probabilidad de que los turistas permanezcan cerca de él (por ejemplo, pasando de un 70% a un 90% de probabilidad de seguir al guía), reduciendo la posibilidad de grandes desviaciones. Cuando el usuario se aleje, estas probabilidades volverán gradualmente a su estado normal, favoreciendo nuevamente la exploración y aumentando la posibilidad de que ocurran desplazamientos excepcionales.

Como parte del componente visual, el recorrido irá transformando el mapa de forma progresiva. A medida que los turistas exploran el territorio, aparecerán zonas de color que construirán el entorno: tonos azules representarán el mar y tonos cafés se concentrarán alrededor del volcán y de los caminos recorridos, reforzando la percepción del paisaje y haciendo visible la huella que dejan las exploraciones.

# Implementación:

<img width="1869" height="915" alt="image" src="https://github.com/user-attachments/assets/cfa447b0-c13d-4d96-8782-f0ab272a7fd8" />

<img width="1333" height="748" alt="image" src="https://github.com/user-attachments/assets/f22039dc-2244-41e1-aa97-f26630bdc5a7" />

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
