### 🎯 Análisis del algoritmo de Flocking

#### Las 3 reglas del Flocking (mi resumen sencillo):
#### 1. Separación:

¿Para qué sirve? Evita que los agentes estén demasiado cerca unos de otros.

¿Cómo lo hace? Revisa quiénes están cerca (dentro de un cierto radio), y genera un vector para alejarse de ellos.

#### 2. Alineación:

¿Para qué sirve? Hace que los agentes traten de moverse hacia la misma dirección.

¿Cómo lo hace? Mira cómo se están moviendo los vecinos y trata de moverse en promedio igual.

#### 3. Cohesión:

¿Para qué sirve? Mantiene el grupo unido, como si todos quisieran ir hacia el centro del grupo.

¿Cómo lo hace? Calcula el punto medio de los vecinos cercanos y crea una fuerza que lleva al agente hacia allí.

#### ⚙️ Parámetros clave que encontré:
- perceptionRadius: define hasta qué distancia un agente ve a otros y decide si son vecinos.

- separationWeight, alignmentWeight, cohesionWeight: controlan qué tan fuerte afecta cada regla el movimiento.

- maxSpeed y maxForce: limitan la velocidad y la fuerza que puede aplicar un agente para que se vea natural.

#### Modificación que probé:
Yo hice que la cohesión tenga peso cero, o sea que los agentes ya no sienten esa necesidad de agruparse.
Cambiar esa parte fue tan simple como poner esta línea:

``` js
let cohesionForce = this.cohesion(boids).mult(0); // desactivada
```

#### ¿Qué pasó cuando lo cambié?
Los agentes ya no se juntan tanto. Se siguen moviendo parecido en dirección (porque alineación sigue activa) y se evitan entre sí (por la separación), pero ya no tienden a formar grupos. Se ven más dispersos por la pantalla, como si cada quien hiciera la suya pero aún se llevaran bien 
