#### Concepto: Visuales para "Devil Trigger" (DMC)
Mi idea es que la visualización acompañe la energía de la canción “Devil Trigger” de Devil May Cry. Quiero que los gráficos se sientan oscuros, caóticos y potentes, como si estuvieran sacados del juego. También quiero que parezca que el caos está contenido dentro de un sistema, como si la música lo estuviera controlando.

#### Algoritmo Generativo (Proceso)
Técnicas que voy a usar:
Sistema de partículas: cada nota fuerte genera partículas que salen disparadas como explosiones visuales.

Flow Field (campo de flujo): las partículas no se mueven al azar, sino que siguen un patrón dinámico de movimiento (como una corriente de energía).

Ruido Perlin + FFT: el flujo de las partículas cambia dependiendo de la energía de ciertas frecuencias.

Aleatoriedad controlada: para que no sea igual cada vez, usaré valores aleatorios al inicio, pero con límites.

#### Cómo usaré los inputs de audio e interacción:

- Volumen: Cantidad de partículas que se generan

- Graves:	Color y tamaño de las partículas

- Agudos:	Velocidad máxima de las partículas

- Mouse:	Cambia la dirección del flujo y cambio de la opacidad en las partículas

#### Lógica general (pseudocódigo simplificado)

``` js
// En cada frame
leerAmplitud();
leerEspectroDeFrecuencias();

if (amplitud > umbral) {
  generarParticulas();
}

para cada particula {
  aplicarFuerzaDesdeFlowField();
  ajustarTamañoPorGraves();
  ajustarVelocidadPorAgudos();
  mover();
  mostrar();
}

```

#### Outputs visuales

-Partículas que parecen chispas o energía.

-Líneas o rastros que dejan esas partículas para generar una sensación de flujo.

-Cambios de color en tonos oscuros con toques de rojo, púrpura o azul dependiendo del espectro.

-Ondas de distorsión pequeñas cuando hay picos de audio muy fuertes.

#### Naturaleza generativa
- Uso de ruido Perlin y condiciones aleatorias para los campos de flujo.

- Cada vez que se corre, se siente distinto aunque suene la misma canción.

- Partículas aparecen y desaparecen en momentos distintos dependiendo del ritmo.
