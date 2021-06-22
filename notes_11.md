---
title: "Cursos  Estadísticas descriptivas - 15"
classes: "15-25"
publishDate: "2021-06-22"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## Transformación no lineal

| Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
| ------------- | ------------------------------------------------------------ |
| **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
| **Teacher:**  | Francisco Camacho                                            |
| **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |

## Notes

## Transformación no lineal 

### ¿Por qué usarlos?

- En el caso donde haya datos fuertemente sesgados y no simétricos.

### Algunos tipos:

> Logaritmos, Sigmoides, polinomiales, etc.

- **Logística:** los valores de la columna se transforman mediante la siguiente fórmula:

![log](https://user-images.githubusercontent.com/63415652/122654862-cedb6280-d113-11eb-9d0e-26a1991537d2.PNG)



- **`LogNormal`:** esta opción convierte todos los valores a una escala logarítmica normal. Los valores 1 de la columna se transforman mediante la siguiente fórmula:

![lognormal](https://user-images.githubusercontent.com/63415652/122654861-ce42cc00-d113-11eb-92cc-64fc408fa338.PNG)

> Aquí `μ y σ` son los parámetros de la distribución, calculados empíricamente a partir de los datos como estimaciones de máxima verosimilitud, para cada columna por separado.

- **TanH:** (Tangente Hiperbólica) todos los valores se convierten a una tangente hiperbólica. Los valores de la columna se transforman mediante la siguiente fórmula:

![Tha](https://user-images.githubusercontent.com/63415652/122654864-cf73f900-d113-11eb-9b7d-09ff12d92ca4.PNG)



### ¿Cuándo usarlos?

Justo **antes de aplicar el escalamiento lineal**, las transformaciones no lineales solo son para que nuestros datos queden lineales para luego aplicar la `normalización` lineal. Siempre se debe aplicar la `normalización` lineal.

## Proceso a seguir:

Distribución no simétrica > Convertirla a simétrica > aplicar escalamiento lineal > Modelo de Machine Learning

