#### Análisis de resultados

Uno de los mayores desafíos al aplicar los conceptos fue entender cómo combinar múltiples fuerzas en una simulación. Al principio, me costaba visualizar cómo se sumaban las fuerzas y afectaban la aceleración de los objetos. Por ejemplo, en la simulación de fricción, al principio olvidé que la fuerza debía ser proporcional a la velocidad, lo que hacía que el objeto se detuviera de golpe en lugar de disminuir su velocidad gradualmente.

Lecciones aprendidas
- Las fuerzas se deben sumar, no sobrescribir. En cada frame, todas las fuerzas deben acumularse antes de actualizar la velocidad. Si no se resetea la aceleración en cada frame, los objetos se aceleran sin control.

- Los vectores en p5.js se pasan por referencia. Hay que usar .copy() para evitar modificar el vector original sin querer.

- El prueba y error es clave. Muchas veces tuve que modificar valores, probar diferentes formas de aplicar fuerzas y corregir errores antes de lograr el efecto deseado.


Cuando hice la simulación de resistencia del aire, primero aplicaba una fuerza fija en contra del movimiento. Pero luego me di cuenta que la resistencia debe aumentar con la velocidad, así que con la ayuda de chatgpt, la corregí usando:

``` js
let dragMagnitude = 0.05 * speed * speed;
drag.setMag(dragMagnitude);

```

