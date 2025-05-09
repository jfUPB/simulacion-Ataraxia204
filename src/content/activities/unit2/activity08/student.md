### Experimento

#### ¿Qué pasa si…?

¿Qué pasa si, en lugar de que el objeto reaparezca en el otro lado de la pantalla cuando toca un borde, hago que rebote en los bordes cambiando su dirección?

#### ¿Qué te imaginas que pasará?

Creo que cuando el círculo llegue a un borde, su dirección cambiará en lugar de desaparecer y aparecer en el lado opuesto. 
Esto haría que el movimiento parezca más realista, como si la pelota estuviera rebotando en una pared.

``` js
let mover;

function setup() {
  createCanvas(640, 240);
  mover = new Mover();
}

function draw() {
  background(255);
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

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }

  checkEdges() {
    // En lugar de reiniciar la posición, invertimos la velocidad en el eje correspondiente.
    if (this.position.x > width || this.position.x < 0) {
      this.velocity.x *= -1;
    }
    if (this.position.y > height || this.position.y < 0) {
      this.velocity.y *= -1;
    }
  }
}

```

#### ¿Qué pasó?

Efectivamente, al tocar un borde, la dirección de la velocidad cambia, haciendo que el círculo rebote en lugar de atravesar la pantalla.

#### ¿Por qué?

Esto ocurre porque, en la función checkEdges(), en lugar de restablecer la posición del círculo cuando llega a un borde, 
simplemente multiplicamos por -1 la velocidad en el eje correspondiente (velocity.x o velocity.y). Esto invierte su dirección y le da un efecto de rebote.

#### Conclusión

Este cambio hace que el movimiento del objeto sea más natural, similar a una pelota rebotando dentro de un espacio cerrado. 
Puede ser útil para simular colisiones en juegos o animaciones.

