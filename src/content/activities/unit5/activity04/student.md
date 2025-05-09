####  1. ¿Cómo se gestiona la creación y la desaparición de las partículas y cómo se gestiona la memoria?

En los ejemplos que trabajé, las partículas se van creando cada vez que ocurre un evento, como mover el mouse o en cada frame, dependiendo del sistema. Para evitar que se acumulen infinitamente (y el programa se vuelva lento), normalmente hay una condición que revisa si la partícula ya “murió”, cuando eso pasa, se elimina. Esto ayuda a que la memoria se libere y no se guarde información innecesaria de partículas viejas.

#### 2. ¿Cómo se aplica el marco de movimiento motion 101 en los sistemas de partículas que analizaste en la actividad anterior?

En los sistemas de partículas eso está casi siempre en el update. Cada partícula tiene sus vectores de posición, velocidad y aceleración, y se actualizan frame por frame para que parezca que la partícula se mueve.

#### 3. ¿Cómo se aplican fuerzas externas a los sistemas de partículas que trabajaste en la unidad? ¿Qué fuerzas se aplicaron y cómo están modeladas?

En la unidad trabajé con fuerzas como la gravedad y la fricción especialmente, Para aplicar esas fuerzas, se por ejemplo el applyForce, que suma el vector de la fuerza a la aceleración de la partícula. Por ejemplo, la gravedad es un vector constante hacia abajo, y la fricción depende de la velocidad de la partícula.

#### 4. ¿Cómo se aplicaste los conceptos de herencia y polimorfismo en los sistemas de partículas que trabajaste en la unidad?

En la actividad 3 de esta unidad, lo que hice fue crear un sistema de partículas con diferentes comportamientos visuales y de movimiento. Para eso, usé herencia creando una clase base que se llamaba Particle, que tenía lo básico: posición, velocidad, aceleración, vida útil, etc...  Luego, hice clases que heredaban de esa para hacer los distintos tipos de particulas especificas.
