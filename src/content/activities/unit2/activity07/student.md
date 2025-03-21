#### ¿En qué consiste motion 101?

Motion 101 es una forma básica de programar movimiento en p5.js usando vectores. La idea principal es que un objeto tiene dos propiedades clave:

Posición (dónde está en la pantalla).
Velocidad (cómo cambia su posición con el tiempo).
El movimiento se logra sumando la velocidad a la posición en cada fotograma. Luego, el objeto se dibuja en su nueva posición.

El código básico para esto es:

``` js
position.add(velocity);
circle(position.x, position.y, 48);
```

Esto hace que el objeto se mueva en cada ciclo de draw().

Para organizar mejor el código, se usa una clase Mover, que encapsula el movimiento en un objeto con sus propios métodos:

- update(): Suma la velocidad a la posición.
- show(): Dibuja el objeto en la pantalla.
- checkEdges(): Hace que el objeto reaparezca en el otro lado si se sale de los límites.

Este enfoque hace que sea fácil manejar múltiples objetos en movimiento sin repetir código innecesario.

Ejemplo:

``` js
let mover;

function setup() {
  createCanvas(400, 400);
  mover = new Mover();
}

function draw() {
  background(220);
  
  mover.update();
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(random(-2, 2), random(-2, 2));
  }

  update() {
    this.position.add(this.velocity);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    } else if (this.position.y < 0) {
      this.position.y = height;
    }
  }

  show() {
    stroke(0);
    fill(175);
    circle(this.position.x, this.position.y, 48);
  }
}
```

