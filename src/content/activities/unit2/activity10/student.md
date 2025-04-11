#### Intención de diseño

Quiero crear una pieza de arte generativo que represente un enjambre de partículas en movimiento, simulando el comportamiento de un grupo de luciérnagas. 
Las partículas se moverán con aceleraciones controladas por el usuario mediante el mouse o el teclado. La intención es que el usuario pueda influir en su 
comportamiento y crear patrones visuales dinámicos.

#### Aplicación del marco MOTION 101

1. Posición y velocidad: Cada partícula tendrá una posición y una velocidad inicial aleatoria dentro del canvas.

2. Aceleración: Se implementarán distintos tipos de aceleraciones según la interacción del usuario:
   
  - Aceleración constante: Para generar un flujo continuo de movimiento.
    
  - Aceleración aleatoria: Para dar un efecto más orgánico, como si las partículas "bailaran" en el espacio.
  
  - Aceleración hacia el mouse: Para que las partículas reaccionen a la presencia del usuario, creando un efecto de atracción o repulsión.
  
3. Interacción en tiempo real:

  - El usuario podrá mover el mouse y las partículas se sentirán atraídas hacia él.

  - Usando el teclado, se podrá cambiar el comportamiento de la aceleración (constante, aleatoria o dirigida al mouse).

  - Se puede agregar un efecto visual de color que cambie con la velocidad o la aceleración.

#### Referentes utilizados

- "Boids" de Craig Reynolds: Un modelo de comportamiento grupal que encontré en google.

- Una colmena de insectos
