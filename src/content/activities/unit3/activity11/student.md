### Los n-cuerpos

``` js
class Body {
  constructor(x, y, mass) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D().mult(2);
    this.acceleration = createVector(0, 0);
    this.mass = mass;
  }

  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }

  attract(others) {
    for (let other of others) {
      if (other !== this) {
        let force = p5.Vector.sub(this.position, other.position);
        let distance = constrain(force.mag(), 10, 100); // Evita valores extremos
        let strength = (0.5 * this.mass * other.mass) / (distance * distance);
        force.setMag(strength);
        other.applyForce(force);
      }
    }
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);

    // Simula una leve resistencia al movimiento para darle un efecto más fluido
    this.velocity.mult(0.99);
  }

  show() {
    fill(200, 100, 255, 150);
    stroke(255);
    circle(this.position.x, this.position.y, this.mass * 5);
  }
}

let bodies = [];

function setup() {
  createCanvas(600, 600);
  for (let i = 0; i < 5; i++) {
    bodies.push(new Body(random(width), random(height), random(5, 15)));
  }
}

function draw() {
  background(20);

  for (let body of bodies) {
    body.attract(bodies);
    body.update();
    body.show();
  }
}

```

El problema de los n-cuerpos trata sobre cómo múltiples objetos con masa interactúan gravitacionalmente entre sí. En lugar de hacer una simulación puramente científica, me inspiré en ciertas esculturas ya hechas, y en una de las simulaciones de ejemplo en el texto guía y diseñé un sistema donde varias esferas flotan en el espacio y se atraen mutuamente de forma elegante y fluida, hasta que se unen entre sí.

Cada cuerpo en la simulación ejerce una atracción gravitacional sobre los demás, y todos se mueven siguiendo esas fuerzas. Para evitar colisiones caóticas, con chatgpt me ayude para limitar la fuerza máxima y agregué una leve resistencia al movimiento, lo que les da un comportamiento más artístico y controlado.

#### Explicación del código
1. Se crean múltiples cuerpos con masa aleatoria.
   
2. Cada cuerpo atrae a los demás usando la ley de gravedad.
   
3. Las fuerzas se aplican y modifican la aceleración, velocidad y posición de cada cuerpo.
   
4. Se agrega una resistencia al movimiento para hacer que los movimientos sean más suaves.

Link de la simulación: https://editor.p5js.org/Ataraxia204/sketches/z565ClH2C

#### Resultado de la simulación
![Captura del resultado de la simulación](../../../../assets/u3-a11-1.png)
   
