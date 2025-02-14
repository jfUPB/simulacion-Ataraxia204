#### Codigo

``` js
function setup() {
    createCanvas(400, 400);
}

let t = 0; // Variable para la interpolación

function draw() {
    background(200);

    let v0 = createVector(100, 300); // Punto en el ángulo recto
    let v1 = createVector(300, 300); // Extremo derecho
    let v2 = createVector(100, 100); // Extremo superior
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

#### Explicación de lerp() y lerpColor()
lerp()
El método lerp(a, b, t) realiza una interpolación lineal entre dos valores a y b, utilizando un factor t que va de 0 a 1.
Si t = 0, devuelve a.
Si t = 1, devuelve b.
Si t = 0.5, devuelve un punto a la mitad entre a y b.

En este código, lerp() se usa con p5.Vector.lerp(v1, v3, t), lo que mueve la flecha animada entre los puntos v1 y v3 a lo largo de la hipotenusa.

lerpColor()
El método lerpColor(c1, c2, t) mezcla dos colores c1 y c2 según un factor t que va de 0 a 1.
Si t = 0, devuelve c1.
Si t = 1, devuelve c2.
Si t = 0.5, devuelve una combinación equilibrada de ambos colores.

Aquí se usa para hacer que la flecha animada cambie de color a medida que avanza por la hipotenusa.

#### ¿Cómo se dibuja una flecha usando drawArrow()?

La función drawArrow() recibe un punto base (base), un vector (vec) que indica la dirección y el color (myColor).

Se traduce el lienzo a la posición base.x, base.y para que la línea parta desde ahí.
Se dibuja una línea de (0,0) hasta el extremo vec.x, vec.y, usando stroke(myColor).
Se rota el lienzo para alinear la punta de flecha con la dirección del vector.
Se dibuja un triángulo en la punta con triangle(), dando la forma de flecha.
