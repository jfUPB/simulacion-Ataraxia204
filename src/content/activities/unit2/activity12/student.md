### Análisis de Resultados

Al aplicar los conceptos de vectores en código, me encontré con varios desafíos porque, aunque entiendo la lógica básica de programación, 
todavía me cuesta aterrizar algunas ideas en código. Tuve que apoyarme en la experimentación y en explicaciones adicionales para lograr que las cosas 
funcionaran como esperaba.

#### Desafíos Encontrados y Lo Que Aprendí

1. Entender cómo se relacionan aceleración, velocidad y posición

  Al principio, me costó visualizar cómo estos tres valores interactúan entre sí. Sabía que la aceleración afecta la velocidad y esta a su vez la posición, 
  pero en el código no siempre veía el resultado que esperaba.
  
  Lo que aprendí: Con pruebas y ajustes, entendí que aunque la aceleración sea pequeña, con el tiempo puede hacer que el objeto gane mucha velocidad. 
  También vi que cambiar directamente la velocidad o la posición sin seguir esta lógica puede romper la fluidez del movimiento.
  
2. Controlar la velocidad para que no se vuelva incontrolable

  Algunas pruebas hicieron que los objetos aceleraran demasiado y desaparecieran de la pantalla, lo que me hizo pensar que algo estaba mal.
  
  Lo que aprendí: Descubrí que la función limit() en los vectores ayuda a mantener la velocidad dentro de un rango manejable, evitando que los objetos se 
  muevan demasiado rápido.

3. Hacer que los objetos reaccionen al mouse de manera natural

  Intenté que el objeto se moviera hacia el cursor, pero al principio se movía raro o demasiado rápido.
  
  Lo que aprendí: No basta con restar la posición del mouse a la del objeto; también hay que normalizar el vector para que la aceleración no dependa de 
  la distancia. Esto hizo que el movimiento fuera más suave.
