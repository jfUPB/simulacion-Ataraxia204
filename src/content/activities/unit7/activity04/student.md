#### 1. Flujo de trabajo:
Primero configuré todo en setup(), como el motor de Matter.js y los cuerpos físicos (las letras y el suelo). Luego, en draw(), usé Engine.update(engine) para que se actualice la simulación de física en cada frame. Después dibujé las letras en el canvas con p5.js, usando su posición que va cambiando sola por la física. Aunque al principio me confundía un poco cómo se conectaban ambas librerías, poco a poco fui entendiendo gracias a ejemplos y pruebas.

#### 2. Representación visual vs. simulación física:
Aunque Matter.js se encarga del movimiento, p5.js es quien dibuja, entonces tuve que usar translate() para posicionar las letras en la pantalla. No fue tan complicado porque los cuerpos se movían todos juntos, como si la palabra fuera un bloque entero. Aunque las letras pueden rotar, en mi caso no rotan mucho, así que ese detalle no se nota tanto. Igual, logré que se viera claro que está cayendo.

#### 3. Creación de formas complejas:
Decidí que cada letra fuera un rectángulo simple y le puse encima su carácter con la función text(). Así no me complicaba haciendo cuerpos más complejos. Me pareció una forma más sencilla de representar las letras, y aunque no es súper detallado, el mensaje de que la palabra “cae” se entiende. Hacer letras más detalladas con vértices me parece aún difícil, pero me gustaría intentarlo en el futuro.

#### 4. Física para la semántica:
Usar simulación física ayudó a que la palabra “CAER” se vea como si realmente está cayendo. No es una caída súper dramática, pero se nota el efecto por la gravedad. Creo que este tipo de enfoque funciona bien con palabras relacionadas al movimiento, como “saltar”, “romper” o “rodar”. En cambio, hay palabras más abstractas que serían difíciles de mostrar solo con física.

#### 5. Potencial exploratorio:
Me parece interesante poder animar texto de esta forma, usando física para que se sienta más vivo. No es algo que haría todo el tiempo, pero veo que puede ser útil en animaciones, instalaciones o incluso para ideas más interactivas. Me gustaría seguir probando con palabras que cambien según cómo las toque el usuario o que reaccionen a sonidos.
