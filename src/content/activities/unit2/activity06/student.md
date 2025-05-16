#### Codigo

``` js
function setup() {
    createCanvas(400, 400);
}

let t = 0; // Variable para la interpolación

function draw() {
    background(200);

    // La base del triángulo cambia con el mouse
    let baseX = map(mouseX, 0, width, 50, 200);
    let baseY = map(mouseY, 0, height, 200, 350);

    // Escala de los vectores
    let scaleFactor = map(mouseX, 0, width, 0.5, 1.5);

    let v0 = createVector(baseX, baseY); // Punto en el ángulo recto
    let v1 = createVector(baseX + 200 * scaleFactor, baseY); // Extremo derecho
    let v2 = createVector(baseX, baseY - 200 * scaleFactor); // Extremo superior
    let v3 = p5.Vector.lerp(v1, v2, abs(sin(t))); // Flecha móvil

    // Flechas del triángulo
    drawArrow(v0, v1, 'red');
    drawArrow(v0, v2, 'blue');
    drawArrow(v1, v2, 'green');

    // Color interpolado de la flecha móvil
    let c1 = color(255, 0, 0);
    let c2 = color(0, 0, 255);
    let movingColor = lerpColor(c1, c2, abs(sin(t)));

    // Flecha móvil recorriendo la hipotenusa
    drawArrow(v0, v3, movingColor);

    t += 0.02;
}

function drawArrow(base, vec, myColor) {
    push();
    stroke(myColor);
    strokeWeight(3);
    fill(myColor);
    line(base.x, base.y, vec.x, vec.y);
    let angle = atan2(vec.y - base.y, vec.x - base.x);
    translate(vec.x, vec.y);
    rotate(angle);
    let arrowSize = 7;
    triangle(-arrowSize, arrowSize / 2, -arrowSize, -arrowSize / 2, 0, 0);
    pop();
}

```

#### Explicación:
Para hacer que todo se mueva con el mouse, cambié la posición base del triángulo usando mouseX y mouseY.

Base de las flechas:

baseX y baseY ahora dependen del mouse.
map() los ajusta para que el triángulo no salga de la pantalla.
Escala de los vectores:

scaleFactor cambia el tamaño del triángulo con mouseX.
Así, el triángulo se agranda o se encoge.
