#### ¿Qué resultado espero obtener?

Creo que el código cambiará los valores de posicion. Primero será (6,9), pero luego, dentro de playingVector(), se cambiará a (20,30). También espero que la consola muestre "Only once".

#### ¿Qué resultado obtuve?

La consola muestra: "Only once"

Si agrego console.log(posicion.toString()); después de playingVector(posicion);, veo que posicion ahora es (20,30). Esto confirma que la función cambió el vector.

#### Paso por valor vs. paso por referencia

Paso por valor (para números, textos, etc.):

Se envía una copia del valor a la función, por lo que el original no cambia.

``` js
function cambiarNumero(n) {
    n = 10;
}

let x = 5;
cambiarNumero(x);
console.log(x); // Sigue siendo 5, porque solo se copió el valor

```

Paso por referencia (para objetos, como p5.Vector):

Se envía la ubicación del objeto en memoria, por lo que si la función cambia algo, el original también cambia.

``` js
function cambiarVector(v) {
    v.x = 10;
    v.y = 15;
}

let vec = createVector(5, 5);
cambiarVector(vec);
console.log(vec.toString()); // Ahora es (10,15), porque se pasó la referencia

```

#### ¿Qué tipo de paso ocurre en el código?

Se usa paso por referencia, porque posicion es un objeto (p5.Vector). La función playingVector(v) modifica v, y eso también cambia posicion.

#### ¿Qué aprendí?

-Cuando paso un número a una función, solo se copia y no cambia el original.

-Cuando paso un objeto (como p5.Vector), la función puede cambiarlo directamente.

-La diferencia entre pasar por valor o referencia en JS
