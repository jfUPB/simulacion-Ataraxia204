#### Experimento

``` js
let mover1, mover2, mover3;

function setup() {
  createCanvas(640, 240);
  mover1 = new Mover("Constant");
  mover2 = new Mover("Random");
  mover3 = new Mover("Mouse");
}

function draw() {
  background(255);

  mover1.update();
  mover1.checkEdges();
  mover1.show();

  mover2.update();
  mover2.checkEdges();
  mover2.show();

  mover3.update();
  mover3.checkEdges();
  mover3.show();
}

class Mover {
  constructor(type) {
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.type = type;
  }

  update() {
    if (this.type === "Constant") {
      this.acceleration.set(-0.001, 0.01);
    } else if (this.type === "Random") {
      this.acceleration.set(random(-0.01, 0.01), random(-0.01, 0.01));
    } else if (this.type === "Mouse") {
      let mouse = createVector(mouseX, mouseY);
      this.acceleration = p5.Vector.sub(mouse, this.position);
      this.acceleration.setMag(0.05);
    }
    
    this.velocity.add(this.acceleration);
    this.velocity.limit(5);
    this.position.add(this.velocity);
  }

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 24);
  }

  checkEdges() {
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }
}

```

#### 1. ¿Qué encontré para cada tipo de aceleración?

- Aceleración constante: El objeto se mueve en una dirección específica y su velocidad aumenta de manera predecible.
  
- Aceleración aleatoria: El objeto se mueve de forma errática, sin una dirección clara.
  
- Aceleración hacia el mouse: El objeto cambia de dirección constantemente para acercarse al mouse.

#### 2. ¿Por qué ocurre esto?

- Aceleración constante:

  Esto ocurre porque la aceleración es el cambio en la velocidad. Como la aceleración es constante, cada cuadro se suma el mismo valor a la velocidad,
  haciendo que el objeto se mueva cada vez más rápido. Al final, la velocidad del objeto crece indefinidamente en la misma dirección.

- Aceleración aleatoria: 

  La aceleración se genera con valores aleatorios en cada cuadro, lo que significa que la velocidad cambia en direcciones inesperadas todo el tiempo. 
  Como resultado, el movimiento es caótico, ya que la dirección del objeto nunca es la misma por mucho tiempo.

- Aceleración hacia el mouse: 

  La aceleración se calcula restando la posición del objeto con la del mouse, lo que hace que siempre apunte en esa dirección. 
  Sin embargo, debido a que la velocidad también se ve afectada por la aceleración, el objeto no se mueve directamente al mouse de inmediato, 
  sino que ajusta su trayectoria de manera gradual. Este comportamiento es similar al de los objetos físicos que responden a una fuerza, 
  como una pelota siendo atraída por un imán.
