#### Concepto de aplicación:

“Tinta digital”
Quise representar cómo se dispersa la tinta líquida en una hoja al contacto con gotas. En lugar de pájaros o peces moviéndose en sincronía, los agentes representan gotas de tinta que, al acercarse, se alinean, se separan o se agrupan creando formas orgánicas que recuerdan una ilustración en crecimiento. La idea es que se genere algo parecido a un boceto colectivo, pero hecho por las "gotas".

#### Adaptación del algoritmo:
Los boids se comportan como gotas de tinta flotando en agua.

- La cohesión da la sensación de que buscan formar manchas.

- La separación permite que no colapsen en un punto.

- La alineación crea un flujo visual armónico como si la tinta se expandiera.

- Cambié los colores a tonos negros y grises translúcidos para parecerse a tinta china.

- Añadí un efecto de trazo leve para simular la textura del papel mojado.

#### Interacción:
-Cada clic del mouse agrega gotas nuevas de tinta.

- Con las teclas ↑ y ↓ puedes aumentar o disminuir la percepción de los agentes (así se comportan más o menos juntos).

- Con la tecla “c” puedes limpiar la pantalla para iniciar otro dibujo.

``` js
let boids = [];

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 100);
  background(0);
  for (let i = 0; i < 100; i++) {
    boids.push(new Boid(random(width), random(height)));
  }
}

function draw() {
  noStroke();
  fill(0, 0, 0, 5); // fondo con más transparencia para mantener las estelas
  rect(0, 0, width, height);

  for (let boid of boids) {
    boid.edges();
    boid.flock(boids);
    boid.update();
    boid.show();
  }
}

function mousePressed() {
  for (let i = 0; i < 10; i++) {
    boids.push(new Boid(mouseX, mouseY));
  }
}

function keyPressed() {
  if (keyCode === UP_ARROW) {
    for (let b of boids) b.perceptionRadius += 5;
  }
  if (keyCode === DOWN_ARROW) {
    for (let b of boids) b.perceptionRadius = max(10, b.perceptionRadius - 5);
  }
  if (key === 'c') {
    background(0);
  }
}

class Boid {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D().mult(random(1, 2));
    this.acceleration = createVector();
    this.maxForce = 0.2;
    this.maxSpeed = 2;
    this.perceptionRadius = 50;
    this.hue = random(360); // Color individual
  }

  edges() {
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }

  align(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius) {
        steering.add(other.velocity);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  separation(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius / 2) {
        let diff = p5.Vector.sub(this.position, other.position);
        diff.div(d);
        steering.add(diff);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  cohesion(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius) {
        steering.add(other.position);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.sub(this.position);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  flock(boids) {
    let alignment = this.align(boids);
    let cohesion = this.cohesion(boids);
    let separation = this.separation(boids);

    alignment.mult(1.0);
    cohesion.mult(0.8);
    separation.mult(1.5);

    this.acceleration.add(alignment);
    this.acceleration.add(cohesion);
    this.acceleration.add(separation);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxSpeed);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    stroke(this.hue, 80, 100, 60);
    strokeWeight(map(this.velocity.mag(), 0, this.maxSpeed, 1, 4));
    point(this.position.x, this.position.y);
  }
}

```

#### Resultado de la simulación
![Captura del resultado de la simulación](../../../../assets/u6-a4-1.gif)
