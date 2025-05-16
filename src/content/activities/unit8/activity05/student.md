### Consolidación de la experiencia audiovisual generativa

#### Conexión sonido-visión
Siento que la conexión entre el sonido y los visuales fue bastante efectiva. Usar los graves y agudos para controlar distintos aspectos como el color, el tipo de partícula o los rayos ayudó a que se sintiera como si la música realmente estuviera “moviendo” todo. En especial los pulsos rojos en los bajos y los efectos azules en los agudos daban una sensación de ritmo muy clara. Lo más difícil fue lograr que las diferencias entre graves y agudos se notaran de forma visual sin que uno opacara al otro.

#### Generatividad vs. Control
Creo que logré un buen equilibrio. Los visuales responden al audio, pero también hay elementos que aparecen con cierta aleatoriedad (como los rayos, el texto fugaz, las partículas). Usé condiciones que dependen de valores del audio combinadas con random() o con frameCount, para que cada vez que se ejecuta sea diferente, pero siga “siguiendo” la música.

#### Integración de conceptos
Apliqué varias ideas de las unidades anteriores: los sistemas de partículas los usé para simular fuego; la idea de fuerzas (como multiplicar la velocidad de las partículas según el volumen) viene del motion 101; usé algo parecido a los rayos de la unidad de ondas para los efectos eléctricos, y todo fue pensado como una especie de sistema de elementos que interactúan en tiempo real con un input (la música). No apliqué física de Matter.js, pero sí muchas ideas de simulación.

#### Desafíos de p5.sound
Lo más difícil fue entender bien cómo usar fft.getEnergy() para controlar cosas específicas. A veces no respondía como yo pensaba, y tuve que probar muchos valores para que se notara. También fue un reto probar el código con música real y que se sincronizara bien. Por suerte, con ayuda de ChatGPT pude entender mejor cómo funciona fft.analyze() y cómo usar la energía de diferentes rangos de frecuencia.

#### Resultado final
Sí, se acerca bastante a lo que imaginaba. Quería algo caótico, energético y con un estilo un poco glitch, que tuviera fuerza como la canción "Devil Trigger", y creo que se logró. Lo que más me gusta es la mezcla de fuego, glitch y rayos que reaccionan distinto según el sonido. Si tuviera más tiempo, intentaría que las partículas se conecten entre ellas o hagan más efectos entre graves y agudos, para hacer la composición aún más rica visualmente.

