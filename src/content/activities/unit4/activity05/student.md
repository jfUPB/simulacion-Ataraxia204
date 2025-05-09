#### 1. Relación entre r y theta con x e y en coordenadas polares

El código usa coordenadas polares, que en vez de trabajar con (x, y) directamente, usa:

- r: la distancia desde el centro.

- theta: el ángulo de rotación.

Para convertirlas a coordenadas normales (cartesianas), se usa:

``` js
let x = r * cos(theta);
let y = r * sin(theta);

```

¿Qué pasa aquí?

El punto se mueve en un círculo alrededor del centro porque theta cambia en cada frame (theta += 0.02), haciendo que el ángulo aumente poco a poco.

#### 2. Modificación con p5.Vector.fromAngle(theta)

Aquí el código cambia a:

``` js
let v = p5.Vector.fromAngle(theta);
circle(v.x, v.y, 48);

```

¿Qué cambia?

- p5.Vector.fromAngle(theta) crea un vector con un radio de 1 por defecto.

- Como no le damos r, el círculo queda pegado al centro y apenas se mueve.

Antes se movía en un círculo grande, ahora casi no se mueve porque su radio es fijo en 1.

#### 3. Modificación con p5.Vector.fromAngle(theta, r)

Código:

``` js
let v = p5.Vector.fromAngle(theta, r);
circle(v.x, v.y, 48);

```

¿Qué cambia?

- Ahora sí usamos r, así que el círculo gira en un círculo grande otra vez.

- Es lo mismo que x = r * cos(theta), y = r * sin(theta), pero más fácil de escribir.
  
El círculo vuelve a moverse bien porque el radio ya no es fijo en 1.
