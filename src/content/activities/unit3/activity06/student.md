### La fuerza neta debe ser acumulativa

#### ¿Por qué se multiplica la aceleración por cero en cada frame?

Cuando aplicamos fuerzas en un objeto, estas se suman a la aceleración en cada frame usando applyForce(). Pero si no reseteamos la aceleración después de actualizar la posición y la velocidad, la aceleración seguiría acumulándose en cada ciclo, lo que haría que el objeto se acelerara de forma irreal y cada vez más rápido sin control.

Por eso, al final de update(), se usa:

``` js
this.acceleration.mult(0);
```

Esto hace que la aceleración vuelva a cero para el siguiente frame, asegurando que en cada ciclo del draw() solo se tengan en cuenta las fuerzas que se aplican en ese momento.

Se Hace justo al final del update porque si la aceleración se pusiera en cero antes de actualizar la velocidad, entonces la aceleración no tendría efecto y el objeto no cambiaría su velocidad correctamente. Primero se debe usar la aceleración para modificar la velocidad y la posición, y solo después de eso se borra para empezar el siguiente frame sin acumulaciones erróneas.
