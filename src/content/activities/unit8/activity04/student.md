#### ¿Cómo configuraste p5.sound y qué datos de audio estás extrayendo?
Para esta actividad usé la librería p5.sound. Cargué la canción "Devil Trigger" desde un archivo local con loadSound() y la reproduje al iniciar el sketch. Para extraer datos del audio utilicé dos objetos:

- p5.FFT para obtener el espectro de frecuencias y detectar la energía en los graves (bass) y agudos (treble).

- p5.Amplitude para obtener el nivel general de volumen (amplitud) en tiempo real.


#### Fragmentos de código clave

1. Partículas que varían según agudos y graves:

``` js
let tipo = energyTreble > 100 && random() < 0.4 ? "agudo" : "grave";
particles.push(new Particle(width / 2, height / 2, tipo));
```

2. Pulsos visuales según volumen (amplitude) y agudos (treble):

``` js
fill(255, 0, 0, level * 400);
ellipse(width / 2, height / 2, level * 800);

fill(0, 150, 255, level * map(energyTreble, 0, 255, 100, 300));
ellipse(width / 2, height / 2, level * 600);
```
3. Rayos que se activan con graves o agudos altos:

``` js
if ((energyBass > 210 || energyTreble > 190) && random() < 0.3) {
  bolts.push(new LightningBolt(random(width), random(height), energyBass > energyTreble ? "grave" : "agudo"));
}
```

4. Texto que aparece al ritmo de los graves:

``` js
if (energyBass > 200 && frameCount % 10 < 3) {
  text("DEVIL TRIGGER", ...); // Estilo y color cambian también
}
```


Código completo:

``` js
let song;
let fft, amp;
let particles = [];
let glitchLines = [];
let bolts = [];

function preload() {
  song = loadSound("devil_trigger.mp3");
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  noStroke();
  fft = new p5.FFT();
  amp = new p5.Amplitude();
  song.play();
}

function draw() {
  background(10, 10, 10, 40);

  let spectrum = fft.analyze();
  let level = amp.getLevel();
  let energyBass = fft.getEnergy("bass");
  let energyTreble = fft.getEnergy("treble");

  // fuego (partículas base)
  if (frameCount % 2 === 0) {
    let tipo = energyTreble > 100 && random() < 0.4 ? "agudo" : "grave";
    particles.push(new Particle(width / 2, height / 2, tipo));
  }

  for (let p of particles) {
    p.update(level);
    p.display();
  }

  // glitch lines
  if (random() < 0.05) {
    let tipo = energyTreble > 100 && random() < 0.5 ? "agudo" : "grave";
    glitchLines.push(new GlitchLine(tipo));
  }

  for (let g of glitchLines) {
    g.update();
    g.display();
  }

  // ⚡ rayos
  if ((energyBass > 210 || energyTreble > 190) && random() < 0.3) {
    bolts.push(new LightningBolt(random(width), random(height), energyBass > energyTreble ? "grave" : "agudo"));
  }

  for (let b of bolts) {
    b.update();
    b.display();
  }

  bolts = bolts.filter(b => b.life > 0);

  // pulsos y distorsión
  push();
  blendMode(ADD);
  fill(255, 0, 0, level * 400);
  ellipse(width / 2, height / 2, level * 800);
  fill(0, 150, 255, level * map(energyTreble, 0, 255, 100, 300));
  ellipse(width / 2, height / 2, level * 600);
  pop();

  // texto de impacto
  if (energyBass > 200 && frameCount % 10 < 3) {
    if (energyTreble > 120) {
      fill(80, 160, 255, 220); // azul
    } else {
      fill(255, 80, 80, 220); // rojo
    }
    textSize(random(32, 64));
    textAlign(CENTER, CENTER);
    text("DEVIL TRIGGER", width / 2 + random(-10, 10), height / 2 + random(-100, 100));
  }

  // limpiar otros elementos
  particles = particles.filter(p => !p.isDead());
  glitchLines = glitchLines.filter(g => g.life > 0);
}

class Particle {
  constructor(x, y, tipo) {
    this.tipo = tipo;
    this.pos = createVector(x, y);
    this.vel = p5.Vector.random2D().mult(random(2, 5));
    this.alpha = 255;
    this.size = this.tipo === "grave" ? random(8, 15) : random(4, 10);
    this.color = this.tipo === "grave"
      ? color(random(200, 255), random(0, 100), random(0, 50), this.alpha)
      : color(0, random(100, 180), 255, this.alpha);
  }

  update(level) {
    this.vel.mult(1 + level * 0.5);
    this.pos.add(this.vel);
    this.alpha -= 4;
  }

  display() {
    fill(this.color);
    ellipse(this.pos.x, this.pos.y, this.size);
  }

  isDead() {
    return this.alpha <= 0;
  }
}

class GlitchLine {
  constructor(tipo) {
    this.x = random(width);
    this.y = random(height);
    this.length = random(20, 200);
    this.life = 10;
    this.thickness = random(1, 4);
    this.tipo = tipo;
  }

  update() {
    this.life--;
  }

  display() {
    if (this.tipo === "grave") {
      stroke(random(150, 255), 0, 0);
    } else {
      stroke(0, random(180, 255), 255);
    }
    strokeWeight(this.thickness);
    line(this.x, this.y, this.x + this.length, this.y + random(-5, 5));
  }
}

class LightningBolt {
  constructor(tipo) {
    this.x = width / 2;
    this.y = height / 2;
    this.tipo = tipo;
    this.life = 6;
    this.points = [];

    let segments = floor(random(5, 10));
    let len = random(100, 300);
    let angle = random(TWO_PI);

    let px = this.x;
    let py = this.y;

    for (let i = 0; i < segments; i++) {
      let dx = cos(angle) * (len / segments);
      let dy = sin(angle) * (len / segments);
      px += dx + random(-10, 10);
      py += dy + random(-10, 10);
      this.points.push(createVector(px, py));
    }
  }

  update() {
    this.life--;
  }

  display() {
    push();
    blendMode(ADD);
    strokeWeight(2);
    if (this.tipo === "grave") {
      stroke(255, 80, 80, 200);
    } else {
      stroke(0, 200, 255, 220);
    }
    noFill();
    beginShape();
    vertex(this.x, this.y);
    for (let pt of this.points) {
      vertex(pt.x, pt.y);
    }
    endShape();
    pop();
  }
}


```

#### VIDEO DEMO
![Captura del resultado de la simulación](../../../../assets/Demo.mp4)
