#### Desafíos encontrados y lecciones aprendidas en la fase APPLY

Al implementar la aplicación interactiva, me di cuenta de que hacer arte generativo no es solo cuestión de escribir código y esperar que salga algo interesante. Hubo varios desafíos que enfrenté:

Controlar la aleatoriedad
Al principio, los elementos generados parecían demasiado caóticos. Usar ruido Perlin ayudó a hacer las transiciones más suaves, pero encontrar el equilibrio entre lo aleatorio y lo estructurado fue complicado.

Interactividad que realmente aporte
Quería que la interacción con el mouse o el teclado se sintiera natural, pero algunas veces los cambios eran muy bruscos o no se notaban mucho. Tuve que ajustar bastante los valores para que la interacción se sintiera bien.

Eficiencia del código
A medida que agregaba más elementos, la aplicación empezó a volverse más lenta. No sabía que la cantidad de elementos generados podía afectar el rendimiento tanto, así que tuve que optimizar el código, 
reducir cálculos innecesarios y mejorar la forma en la que dibujaba los objetos.

#### Lecciones aprendidas

1. La aleatoriedad es útil, pero hay que controlarla para que el resultado sea interesante y no simplemente un desorden de formas.
2. Hacer que la interacción tenga un impacto visible en la pieza mejora la experiencia del usuario.
3. Optimizar el código es clave cuando se trabaja con gráficos generativos para evitar problemas de rendimiento.
