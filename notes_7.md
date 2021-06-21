---
title: "Cursos de matemáticas para data science: Estadísticas descriptivas"
classes: "10-25"
publishDate: "2021-06-21"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## Desviación estándar

- | Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
  | ------------- | ------------------------------------------------------------ |
  | **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
  | **Teacher:**  | Francisco Camacho                                            |
  | **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |


## Notes

## Desviación estándar

La desviación estándar es la medida de **dispersión más común**, que indica qué tan dispersos están los datos con respecto a la media. Mientras mayor sea la desviación estándar, mayor será la dispersión de los datos. El símbolo `σ` `(sigma)` se utiliza frecuentemente para representar la **desviación estándar de una población**, mientras que `s` se utiliza para representar la **desviación estándar de una muestra**. La desviación estándar se puede utilizar para establecer un valor de referencia para estimar la variación general de un proceso.

___

#### Solo para aclarar, ya que el termino de varianza se abordo muy rápidamente:

#### Varianza:

Es una medida de dispersión que representa la variabilidad de una serie de datos respecto a su media. Formalmente se calcula como la suma de los residuos al cuadrado divididos entre el total de observaciones. Su fórmula es la siguiente:

- `X` → Variable sobre la que se pretenden calcular la varianza
- $x_i$ → Observación número i de la variable X. i puede tomarar valores entre 1 y n.
- `N` → Número de observaciones.
- `x̄​` → Es la media de la variable X.

La **diferencia entre la desviación estándar o típica y la varianza**, es que la la desviación típica es la raíz cuadrada de la varianza.  

Y no nos podemos olvidar de otra medida de dispersión muy importante, que es **el coeficiente de variación:**

Su cálculo se obtiene de dividir la desviación típica entre el valor absoluto de la media del conjunto y por lo general se expresa en porcentaje para su mejor comprensión.
- `X` → Variable sobre la que se pretenden calcular la varianza
- $σ_x$ → Desviación típica de la variable X.
- `| x̄ |` → Es la media de la variable X en valor absoluto con x̄ ≠ 0

El coeficiente de variación de utiliza para comparar la dispersión (variación) de conjuntos de datos de medidas diferentes o con medias aritméticas diferentes.

> **Outliers** -  valores desviados 

### Why “1.5” in IQR Method of Outlier Detection?

[Mas informacion sobre este tema ...](https://towardsdatascience.com/why-1-5-in-iqr-method-of-outlier-detection-5d07fdc82097)

```
Lower Bound: (Q1 - 1.5 * IQR)
Upper Bound: (Q3 + 1.5 * IQR)
```

```
Taking scale = 1.5:

Lower Bound:
= Q1 - 1.5 * IQR
= Q1 - 1.5 * (Q3 - Q1)
= -0.675σ - 1.5 * (0.675 - [-0.675])σ
= -0.675σ - 1.5 * 1.35σ
= -2.7σ

Upper Bound:
= Q3 + 1.5 * IQR
= Q3 + 1.5 * (Q3 - Q1)
= 0.675σ + 1.5 * (0.675 - [-0.675])σ
= 0.675σ + 1.5 * 1.35σ
= 2.7σ
```

![img](https://miro.medium.com/max/1566/1*ARpoeY3MdhFImq0JXAXtRw.png)

