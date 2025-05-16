#### Paso por valor vs. paso por referencia

- Paso por valor: Se crea una copia independiente del valor original. Si modificamos la copia, el valor original no cambia.
  
- Paso por referencia: No se crea una copia nueva, sino que ambas variables apuntan al mismo objeto en memoria. Si cambiamos una, la otra también se modifica.

#### Diferencia entre las dos líneas del código

``` js
let friction = this.velocity.copy();
```
Aquí se esta creando una copia independiente del vector velocity.

Si luego modificamos friction, this.velocity se mantiene igual.

``` js
let friction = this.velocity;
```
Aquí friction no es una copia, sino una referencia al mismo objeto this.velocity.

Si modificamos friction, también estamos modificando this.velocity, lo que puede generar comportamientos inesperados.
