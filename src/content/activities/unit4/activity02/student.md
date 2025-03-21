### Primera simulación (manejo de ángulos)

#### ¿Qué está pasando en la simulación? ¿Cuál es la interacción?

En esta simulación, hay una línea con dos círculos en sus extremos que rota alrededor del centro de la pantalla. La rotación ocurre cuando se presiona una tecla, lo que aumenta el valor de angle.

#### ¿Por qué se traslada el origen al centro de la pantalla?

Se hace para que la rotación ocurra alrededor del centro en lugar de la esquina superior izquierda (que es el origen por defecto en p5.js). Si no se hiciera esta traslación, la rotación sucedería respecto a la esquina en lugar del centro del lienzo.

#### ¿Cuál es la relación entre el sistema de coordenadas y la función rotate()?

rotate() gira todos los elementos que se dibujan después de llamarla, pero la rotación ocurre alrededor del punto de origen del sistema de coordenadas. Por eso se usa translate(width/2, height/2), para que el origen esté en el centro y la rotación sea alrededor de ese punto.

#### ¿Por qué los elementos gráficos parecen estar en (0,0) pero rotan?

Después de hacer translate(width/2, height/2), el nuevo (0,0) es el centro del canvas. La línea y los círculos se dibujan en coordenadas relativas a este nuevo origen, por lo que coloca la línea centrada. Aunque el código de dibujo no cambia en cada frame, la rotación aplicada por rotate(angle) hace que todo el conjunto gire.

### Segunda simulación (elementos que siguen la velocidad)

#### ¿Dónde está el marco Motion 101 y qué hace?

El marco Motion 101 está en la forma en que el objeto se mueve. Se actualiza la posición sumando la velocidad, lo que hace que el objeto se desplace de manera controlada y fluida.

#### ¿Qué hace la función heading()?

heading() devuelve el ángulo de un vector en relación con el eje X. En este caso, se usa para obtener la dirección en la que se mueve el objeto y girar su representación gráfica en la misma dirección.

#### ¿Qué hacen las funciones push() y pop()?

Estas funciones sirven para guardar y restaurar la configuración del lienzo:

- push(): guarda la configuración actual (posición, rotación, estilos, etc.).
  
- pop(): restaura la configuración guardada antes de push().

#### ¿Qué hace rectMode(CENTER)?

Cambia el modo en que se dibujan los rectángulos. Por defecto, rect(x, y, w, h) usa la esquina superior izquierda como punto de referencia. Con rectMode(CENTER), el rectángulo se dibuja desde su centro, lo que facilita alinearlo con el origen y rotarlo correctamente.

#### ¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad?

El ángulo de rotación se obtiene directamente del vector de velocidad con heading(). Esto hace que el objeto apunte en la dirección en la que se está moviendo. Si dibujamos un vector en un papel, veremos que su dirección es la misma que la del objeto en la simulación.
