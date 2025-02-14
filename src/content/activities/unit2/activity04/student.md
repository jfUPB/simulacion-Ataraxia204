#### 1. ¿Para qué sirve el método mag()?

El método mag() devuelve la magnitud (o longitud) del vector, calculada con la fórmula:

   magnitud = raiz(x^2+y^2+z^2)

#### 2. Diferencia entre mag() y magSq()

- mag() devuelve la magnitud real del vector usando una raíz cuadrada.
  
- magSq() devuelve la magnitud al cuadrado (x^2+y^2+z^2), sin calcular la raíz cuadrada.

#### 3. ¿Cual es mas eficiente?
  
- magSq() es más eficiente porque evita el cálculo costoso de la raíz cuadrada. Se usa cuando solo se necesita comparar magnitudes.


#### 4. ¿Para qué sirve el método normalize()?

Convierte un vector en un vector unitario (longitud 1) manteniendo su dirección. Se usa cuando solo importa la dirección del vector, como en movimientos o direcciones de luz.

#### 5. Explicación del método dot() en una frase para un periodista:

El método dot() calcula la relación entre dos vectores, indicando qué tanto apuntan en la misma dirección.

#### 6. Diferencia entre la versión estática y de instancia de dot().

La versión de instancia (v1.dot(v2)) calcula el producto punto de v1 con v2.

La versión estática (p5.Vector.dot(v1, v2)) hace lo mismo sin modificar los vectores originales.

#### 7. Interpretación geométrica del producto cruz (cross()).

- El producto cruz entre dos vectores en 3D genera un tercer vector perpendicular al plano formado por los dos originales.
  
- La magnitud del vector resultante es igual al área del paralelogramo que forman los vectores originales.
  
- Se usa en gráficos 3D para calcular normales a superficies.

#### 8. ¿Para qué sirve el método dist()?

Calcula la distancia entre dos puntos representados por vectores. Se usa en detección de colisiones o trayectorias.

#### 9. ¿Para qué sirven los métodos normalize() y limit()?

- normalize() ajusta un vector a longitud 1 sin cambiar su dirección.

- limit() impone un valor máximo a la magnitud del vector. Se usa para limitar velocidades o fuerzas en simulaciones.
