#### ¿Cómo funciona la suma de dos vectores?

Un vector es como una flecha que indica una dirección y una velocidad. Cuando sumamos dos vectores, es como juntar dos flechas: tomamos la punta de la primera y la movemos según la segunda.

En este caso, el vector position indica dónde está la pelota, y velocity indica cuánto y en qué dirección se mueve. Al sumarlos, actualizamos la posición de la pelota.

Sería sumar la parte "x" y "y" de ambos verctores para así tener un nuevo vector con una posición actualizada.


#### ¿Por qué esta línea position = position + velocity; no funciona?

JavaScript no sabe cómo sumar vectores directamente porque position y velocity no son simples números, son objetos. Es como intentar sumar dos imágenes en lugar de dos números.

Para hacerlo bien, usamos el método add(), que le dice a p5.js cómo hacer la suma correctamente: "position.add(velocity);"

Esto actualiza la posición de la pelota sumando los valores de velocity sin problemas.
