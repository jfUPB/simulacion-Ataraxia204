### 🧪 Actividad 02 – Análisis de Flow Fields

#### 1. ¿Cómo se guarda el campo de flujo?
El campo de flujo se guarda como un arreglo muy largo (como una lista) que representa una cuadrícula invisible que cubre toda la pantalla. Cada cuadrito de esa cuadrícula tiene una flecha (un vector) que apunta en alguna dirección, y los agentes (que en este caso son como flechitas también) siguen esas direcciones.

#### 2. ¿Cómo el agente sigue el campo de flujo?
El agente (vehículo) mira dónde está en la pantalla, y con eso calcula en qué parte de la cuadrícula está. Luego busca la flecha (vector) de ese cuadrito, y trata de moverse en esa dirección. No se mueve de una sino que hace un cálculo para acercarse a esa dirección de manera suave.

#### 3. Parámetros clave del código

- Resolución del campo (scl): define qué tan grandes son los cuadritos del campo de flujo.

- maxspeed: qué tan rápido puede ir un agente.

- maxforce: qué tanta fuerza puede usar para cambiar de dirección.

#### 4. Modificación que hice y qué pasó
Cambié la resolución del campo de flujo a un número más grande. Eso hizo que los cuadros del campo fueran más grandes, y como resultado, los agentes se movían más suave y como en caminos más amplios, pero con menos detalle. Parecía que estaban más libres pero con menos curvas.

También probé bajando el maxforce, y con eso los agentes tomaban las curvas mucho más despacio. Parecían más lentos para reaccionar a los cambios del campo.

