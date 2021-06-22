---
title: "Cursos  Estadísticas descriptivas -14"
classes: "14-25"
publishDate: "2021-06-22"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## Pipelines de procesamiento para variables numéricas

| Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
| ------------- | ------------------------------------------------------------ |
| **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
| **Teacher:**  | Francisco Camacho                                            |
| **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |

## Notes

## Escalamiento Lineal:

Por que usarlo?

> Modelos de `machine learning` eficientes en el rango `[-1, 1]`

Hay diferentes tipos?

> * `Max-min` 
> * `Clipping` (No muy recomendado, omite datos que no deberías descartar)
> * `Z-score` (Es uno de los mas comunes y usados)
> * `Winsorizing` (Es un caso particular del `clipping`)

Cuando usarlos?

> Data simétrica o uniformemente distribuida.

### `Normalización`

> La `normalización` es una técnica que a menudo se aplica como parte de la preparación de datos para el aprendizaje automático. 

> El objetivo de la `normalización` es cambiar los valores de las columnas numéricas en el conjunto de datos para usar una escala común, sin distorsionar las diferencias en los rangos de valores ni perder información.

>  La `normalización` también es necesaria para que algunos algoritmos modelen los datos correctamente.

**Por ejemplo,** suponga que su conjunto de datos de entrada contiene una columna con valores que van de `0 a 1` y otra columna con valores que van de `10,000 a 100,000`. La gran diferencia en la escala de los números podría causar problemas al intentar combinar los valores como características durante el modelado.

La `normalización` evita estos problemas al crear nuevos valores que mantienen la distribución general y las proporciones en los datos de origen, mientras mantienen los valores dentro de una escala aplicada en todas las columnas numéricas utilizadas en el modelo.

#### Tenemos varias opciones para transformar datos numéricos:

- Cambiar todos los valores a una escala de 0 a 1 o transformar los valores representándolos como rangos de `percentiles` en lugar de valores absolutos.
- Aplicar la `normalización` a una sola columna o a varias columnas en el mismo conjunto de datos.
- Si necesita repetir el experimento o aplicar los mismos pasos de `normalización` a otros datos, puede guardar los pasos como una transformación de `normalización` y aplicarlos a otros conjuntos de datos que tengan el mismo esquema.

> Nota importante: Algunos algoritmos requieren que los datos se normalicen antes de entrenar un modelo. Otros algoritmos realizan su propia `normalización` o escalado de datos.

### `Normalización` lineal

#### Algunos de los tipos:

- **`Zscore` :** convierte todos los valores en una puntuación `z`. Los valores de la columna se transforman mediante la siguiente fórmula:

![z score](https://user-images.githubusercontent.com/63415652/122654703-e36b2b00-d112-11eb-847e-5ca8ff3288c5.PNG)

> La media y la desviación estándar se calculan para cada columna por separado. Se utiliza la desviación estándar de la población.

- `MinMax` :

  > el `normalizador` `min-max` cambia la escala `linealmente` cada característica al intervalo `[0,1]`. El cambio de escala al intervalo `[0,1]` se realiza cambiando los valores de cada característica para que el valor mínimo sea `0`, y luego dividiendo por el nuevo valor máximo (que es la diferencia entre los valores máximo y mínimo originales). Los valores de la columna se transforman mediante la siguiente fórmula:

  ![min max](https://user-images.githubusercontent.com/63415652/122654702-e239fe00-d112-11eb-91a6-d08b5ec54b8c.PNG)

#### ¿Cuándo usar la `normalización` lineal?

- En datos simétricos o en datos uniformemente distribuidos.

