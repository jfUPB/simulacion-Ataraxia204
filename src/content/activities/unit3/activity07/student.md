#### Problema en el planteamiento

El problema en el código está en esta línea:

``` js
force.div(10);
```

Aquí estamos dividiendo la fuerza por 10, lo cual en teoría está bien porque Fuerza = Masa × Aceleración, y si la masa es 10, la aceleración debería ser Fuerza / 10.

Pero hay un error importante:

"force" es un objeto de la clase p5.Vector, y en JavaScript los objetos se pasan por referencia.
Esto significa que al hacer force.div(10);, estamos modificando directamente el vector original.
Si wind y gravity son vectores definidos antes de aplicar la fuerza, también se modificarán fuera de la función, lo cual puede causar problemas en otros cálculos.

#### Solución

En lugar de modificar force directamente, hay que crear una copia antes de dividirla por la masa. Así evitamos afectar la fuerza original

``` js
applyForce(force) {
    let f = force.copy(); // Crear una copia de la fuerza original
    f.div(10); // Ahora sí, dividimos por la masa
    this.acceleration.add(f); // Sumamos la fuerza ajustada a la aceleración
}

```

#### Implementación en p5.js

``` js
class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = 10; // Definir la masa
  }

  applyForce(force) {
    let f = force.copy(); // Crear copia para no modificar la original
    f.div(this.mass); // Aplicar la ecuación F = m * a
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    fill(127);
    stroke(0);
    circle(this.position.x, this.position.y, this.mass * 2); // Dibujar el objeto con tamaño proporcional a la masa
  }
}

let mover;

function setup() {
  createCanvas(400, 400);
  mover = new Mover();
}

function draw() {
  background(220);

  let wind = createVector(0.2, 0);
  let gravity = createVector(0, 0.5);

  mover.applyForce(wind);
  mover.applyForce(gravity);

  mover.update();
  mover.show();
}

```
