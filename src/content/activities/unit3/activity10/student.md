### Modelando fuerzas

#### Fricción

La fricción es una fuerza que se opone al movimiento. En esta simulación, cada vez que el objeto se mueve, se le aplica una fuerza de fricción en dirección contraria a su velocidad. La magnitud de la fricción es proporcional a la velocidad del objeto, simulando cómo los objetos reales pierden velocidad cuando se deslizan sobre una superficie.

```js
class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(random(-2, 2), random(-2, 2));
    this.acceleration = createVector(0, 0);
    this.mass = 1;
  }

  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }

  applyFriction() {
    let friction = this.velocity.copy();
    friction.mult(-1); // Dirección opuesta al movimiento
    friction.setMag(0.1); // Magnitud constante de fricción
    this.applyForce(friction);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    fill(127);
    stroke(0);
    circle(this.position.x, this.position.y, 20);
  }
}

let mover;

function setup() {
  createCanvas(400, 400);
  mover = new Mover();
}

function draw() {
  background(220);
  
  mover.applyFriction(); // Aplicar fricción en cada frame
  mover.update();
  mover.show();
}

```

Link: https://editor.p5js.org/Ataraxia204/sketches/Q5gs0quEv

#### Resistencia del aire y fluidos

Aquí se simula la resistencia del aire o de un fluido. La fuerza de resistencia depende de la velocidad del objeto y se opone a su movimiento. A medida que el objeto se mueve más rápido, la resistencia del aire es mayor.

```js
class Mover {
  constructor() {
    this.position = createVector(width / 2, 50);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = 1;
  }

  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }

  applyDrag() {
    let drag = this.velocity.copy();
    drag.mult(-1);
    let speed = this.velocity.mag();
    let dragMagnitude = 0.05 * speed * speed; // Resistencia proporcional a la velocidad al cuadrado
    drag.setMag(dragMagnitude);
    this.applyForce(drag);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    fill(127);
    stroke(0);
    circle(this.position.x, this.position.y, 20);
  }
}

let mover;

function setup() {
  createCanvas(400, 400);
  mover = new Mover();
}

function draw() {
  background(220);
  
  let gravity = createVector(0, 0.2);
  mover.applyForce(gravity);
  
  mover.applyDrag(); // Aplicar resistencia del aire
  mover.update();
  mover.show();
}

```

Link: https://editor.p5js.org/Ataraxia204/sketches/bzUOT0s0I

#### Atracción gravitacional

Esta simulación muestra la atracción gravitacional entre dos objetos. Se usa la ecuación de la gravedad de Newton, donde la fuerza de atracción depende de la distancia entre los objetos y sus masas.

```js
class Mover {
  constructor(x, y, mass) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = mass;
  }

  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }

  attract(target) {
    let force = p5.Vector.sub(this.position, target.position);
    let distance = constrain(force.mag(), 5, 25); // Limitar valores extremos
    let strength = (0.5 * this.mass * target.mass) / (distance * distance); // Ley de gravedad
    force.setMag(strength);
    target.applyForce(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    fill(127);
    stroke(0);
    circle(this.position.x, this.position.y, this.mass * 5);
  }
}

let mover;
let attractor;

function setup() {
  createCanvas(400, 400);
  attractor = new Mover(width / 2, height / 2, 10);
  mover = new Mover(width / 3, height / 3, 2);
}

function draw() {
  background(220);

  attractor.attract(mover);
  
  mover.update();
  mover.show();
  attractor.show();
}

```

Link: https://editor.p5js.org/Ataraxia204/sketches/hNtC5287t
