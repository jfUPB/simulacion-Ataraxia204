### ¿Dónde está el marco Motion 101 en el código?

#### El marco Motion 101 dice que el movimiento de un objeto se basa en tres pasos:

La posición cambia según la velocidad: this.position.add(this.velocity);

La velocidad cambia según la aceleración: this.velocity.add(this.acceleration);

La aceleración debe definirse de alguna manera antes de aplicarse.

### Ejemplos de cómo definíamos la aceleración en la unidad anterior:

#### Aceleración constante:

``` js
this.acceleration = createVector(0.01, -0.01);
```

#### Aceleración aleatoria:

``` js
this.acceleration = p5.Vector.random2D().mult(0.02);
```

#### Aceleración hacia el mouse:

``` js
let mouse = createVector(mouseX, mouseY);
this.acceleration = p5.Vector.sub(mouse, this.position);
this.acceleration.setMag(0.05);
```

### ¿Qué tiene que ver esto con las leyes de Newton?

En la unidad anterior, simplemente decidíamos qué aceleración usar. Ahora, en esta unidad, vamos a calcular la aceleración basándonos en fuerzas. Esto se relaciona con la Segunda Ley de Newton, que dice:

Fuerza = Masa × Aceleración

Esto significa que la aceleración no será un valor cualquiera que elijamos, sino que dependerá de las fuerzas que actúen sobre el objeto.

Antes, poníamos aceleraciones fijas o aleatorias, pero ahora aprenderemos a hacer que los objetos respondan a fuerzas como la gravedad o la fricción de una manera más realista.

