#### 1. Identificación de Motion 101 y modificaciones para agregar fuerzas acumulativas

En Motion 101, los objetos se mueven sumando su velocidad a su posición en cada frame. Sin embargo, cuando agregamos fuerzas, también debemos modificar la aceleración.

El código sigue este orden:

``` js
this.velocity.add(this.acceleration);
this.position.add(this.velocity);
this.acceleration.mult(0); // Reinicia la aceleración

```

¿Por qué se multiplica la aceleración por 0?

Porque las fuerzas se aplican en cada frame y si no las reiniciamos, se seguirían acumulando y el objeto aceleraría sin control.

#### 2. Identificación del Attractor y cambio de color

El Attractor es el objeto que genera la atracción. Se dibuja en esta parte del código:

``` js
display() {
  fill(175, 200); 
  stroke(0);
  ellipse(this.position.x, this.position.y, this.mass * 2);
}

```
Para cambiar su color, solo modifiqué fill():

``` js
fill(255, 0, 0); // Ahora es rojo

```

#### 3. Permitir mover el Attractor con el mouse y cambiar su color al pasar el cursor

Para hacer esto, agregué detección de colisión y eventos de mouse:

- Detectar si el mouse está encima

``` js
overMouse() {
  let d = dist(mouseX, mouseY, this.position.x, this.position.y);
  this.rollover = d < this.mass;
}

```

Se ejecuta en draw() para actualizarse en cada frame.

- Cambiar el color cuando el mouse está encima

``` js
display() {
  if (this.rollover) {
    fill(0, 255, 0); // Verde si el mouse está encima
  } else {
    fill(255, 0, 0); // Rojo por defecto
  }
  ellipse(this.position.x, this.position.y, this.mass * 2);
}

```

- Permitir arrastrarlo con el mouse

``` js
mousePressed() {
  let d = dist(mouseX, mouseY, this.position.x, this.position.y);
  this.dragging = d < this.mass;
}

mouseDragged() {
  if (this.dragging) {
    this.position.set(mouseX, mouseY);
  }
}

mouseReleased() {
  this.dragging = false;
}

```
