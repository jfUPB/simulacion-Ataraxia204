#### Caminatas Aleatorias

1. Descripción del experimento:
Voy a modificar el código de la caminata aleatoria para que el color del walker cambie según su posición en la pantalla.

2. Pregunta del experimento:
¿Qué patrones de color aparecerán si el walker cambia de color según su posición?

3. Resultados esperados:

Si el walker se mueve hacia la derecha, se verá más rojo.
Si se mueve hacia abajo, se verá más azul.
En la parte superior izquierda será oscuro.
En la parte inferior derecha será violeta (rojo + azul).

4. Resultados obtenidos:

El walker dejó un rastro de puntos de diferentes colores.
Se notaron zonas más rojas a la derecha y más azules abajo.
La combinación de colores creó una transición de tonos en la pantalla.

5. Aprendizaje del experimento:
El color ayuda a visualizar los movimientos del walker y muestra patrones en su desplazamiento que no se notaban con un punto negro.

``` js
class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    let r = map(this.x, 0, width, 0, 255);
    let b = map(this.y, 0, height, 0, 255);

    stroke(r, 0, b);
    strokeWeight(3);
    point(this.x, this.y);
  }

  step() {
    let choice = floor(random(4));
    if (choice === 0) {
      this.x++;
    } else if (choice === 1) {
      this.x--;
    } else if (choice === 2) {
      this.y++;
    } else {
      this.y--;
    }

    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }
}

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

```
