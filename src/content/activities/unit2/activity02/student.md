#### ¿Qué tuve que hacer para hacer la conversión?

1. Usar p5.Vector: En lugar de usar x e y por separado, creé position y velocity como vectores con createVector().
2. Suma de vectores: En vez de hacer x = x + xspeed y y = y + yspeed, usé position.add(velocity).
3. Acceso a componentes: Como ellipse() necesita valores x e y, los accedí con position.x y position.y.
4. Rebotes: En lugar de manejar xspeed y yspeed por separado, usé velocity.x y velocity.y.

``` js
let position;
let velocity;

function setup() {
  createCanvas(400, 400);
  position = createVector(width / 2, height / 2);
  velocity = createVector(random(-2, 2), random(-2, 2));
}

function draw() {
  background(220);
  
  // Mueve el walker sumando el vector de velocidad
  position.add(velocity);

  // Rebota en los bordes
  if (position.x > width || position.x < 0) {
    velocity.x *= -1;
  }
  if (position.y > height || position.y < 0) {
    velocity.y *= -1;
  }

  // Dibuja el walker
  fill(0);
  ellipse(position.x, position.y, 20, 20);
}

```
