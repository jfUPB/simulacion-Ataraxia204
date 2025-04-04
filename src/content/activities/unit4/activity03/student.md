

#### Linkd de la simulación:

https://editor.p5js.org/Ataraxia204/sketches/_l5tlfJGt

``` js
let vehicle;

function setup() {
  createCanvas(600, 400);
  vehicle = new Vehicle(width / 2, height / 2);
}

function draw() {
  background(220);

  vehicle.update();
  vehicle.edges();
  vehicle.show();
}

class Vehicle {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }

  applyForce(force) {
    this.acceleration.add(force);
  }

  update() {
    // Movimiento con teclas
    if (keyIsDown(LEFT_ARROW)) {
      this.applyForce(createVector(-0.1, 0)); // Aceleración a la izquierda
    }
    if (keyIsDown(RIGHT_ARROW)) {
      this.applyForce(createVector(0.1, 0)); // Aceleración a la derecha
    }

    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0); // Reiniciar la aceleración en cada frame
  }

  edges() {
    // Si el vehículo sale de la pantalla, reaparece en el otro lado
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }
  }

  show() {
    let angle = this.velocity.heading(); // Obtener el ángulo de dirección

    push();
    translate(this.position.x, this.position.y);
    rotate(angle + PI / 2); // Ajustar para que apunte correctamente

    // Dibujar un triángulo como el vehículo
    fill(150, 0, 255);
    stroke(0);
    triangle(-10, 10, 10, 10, 0, -15);

    pop();
  }
}

```

#### Resultado de la simulación
![Captura del resultado de la simulación](../../../../assets/u4-a3-1.png)
