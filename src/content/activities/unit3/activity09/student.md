#### Pasos a seguir para modelar una fuerza

1. Definir la fuerza
   
Se debe identificar qué tipo de fuerza se quiere modelar (gravedad, fricción, viento, etc.). Esto puede ser una fuerza realista basada en fórmulas físicas o una fuerza inventada para efectos visuales.

2. Calcular la dirección de la fuerza
   
Como las fuerzas son vectores, es importante definir hacia dónde apuntan.

Por ejemplo, la gravedad siempre apunta hacia abajo, mientras que el viento podría tener una dirección variable.
Si la fuerza es entre dos objetos, la dirección se obtiene restando sus posiciones

3. Calcular la magnitud de la fuerza
   
La intensidad de la fuerza depende de su naturaleza:

La gravedad es proporcional a la masa de los objetos e inversamente proporcional a la distancia al cuadrado.
La fricción depende de la velocidad y la superficie de contacto.
Se puede usar fórmulas físicas o establecer un valor

4. Aplicar la fuerza
   
La fuerza se añade a la aceleración del objeto afectado:

5. Actualizar la simulación
   
Cada frame, se recalculan las fuerzas y se actualizan la aceleración, la velocidad y la posición del objeto:
