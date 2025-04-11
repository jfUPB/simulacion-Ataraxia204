### ¿Y qué relación tiene esto de las leyes de Newton con al arte generativo?

#### Problema del planteamiento

El código applyForce(force) { this.acceleration = force; } tiene un problema: cada vez que se llama a applyForce(), la aceleración se sobrescribe en lugar de acumular todas las fuerzas.

Si en un mismo frame aplicamos dos fuerzas como wind y gravity, en lugar de sumarlas, la última fuerza que se aplique será la única que afecte al objeto. Esto significa que, si aplicamos primero el viento y luego la gravedad, solo la gravedad tendrá efecto, ignorando el viento.

Solución
En lugar de sobrescribir la aceleración, debemos sumarle todas las fuerzas que se aplican en el frame. Para hacer esto, en la función applyForce(), en vez de usar =, usamos .add(), que nos permite acumular las fuerzas:

``` js
applyForce(force) {
  this.acceleration.add(force);
}
```

De esta manera, cada vez que llamemos a applyForce(), la aceleración se actualizará sumando la nueva fuerza sin perder las anteriores.

#### Implementación en p5.js

``` js
class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = 1; // La masa es 1, así que F = a
  }

  applyForce(force) {
    this.acceleration.add(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0); // Reseteamos la aceleración para el siguiente frame
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

  let wind = createVector(0.01, 0);
  let gravity = createVector(0, 0.1);

  mover.applyForce(wind);
  mover.applyForce(gravity);

  mover.update();
  mover.show();
}

```
