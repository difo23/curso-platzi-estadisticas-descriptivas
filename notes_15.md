---
title: "Cursos  Estadísticas descriptivas - 15"
classes: "19-25"
publishDate: "2021-06-22"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## Cálculo de valores propios de una matriz

| Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
| ------------- | ------------------------------------------------------------ |
| **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
| **Teacher:**  | Francisco Camacho                                            |
| **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |

## Notes

Como viste en la clase anterior, cuando tenemos un conjunto de datos con muchas variables, la matriz de covarianza es el objeto matemático que permite identificar cuáles variables están altamente correlacionadas.

Cuando dos variables están altamente correlacionadas, quiere decir que aportan básicamente la misma información del problema y eso podría indicar que solo necesitaríamos una sola de ellas. En la próxima clase veremos que esa **reducción de variables** se puede hacer con una técnica matemática denominada **PCA (principal component analysis)**.

Esta técnica está basada en un concepto del álgebra de vectores y matrices, que llamamos el cálculo de los valores propios de una matriz, y en esta lectura profundizaremos sobre qué significa ese procedimiento.

## Repaso de matrices

Las matrices en general son objetos matemáticos que tienen un cierto número de filas y columnas *(estos números los denominamos dimensiones de la matriz).*

Las matrices tienen una operación especial, que llamamos transponer, la cual consiste en ubicar cada fila como una columna en una nueva matriz, el resultado de una transposición se denomina matriz transpuesta y se ve así:

![https://i.imgur.com/zEGhv9B.png](https://i.imgur.com/zEGhv9B.png)

Así también, entre las matrices podemos definir reglas de suma y resta de forma similar a como hacemos con los números naturales o decimales, con una condición especial: ambas matrices deben tener las mismas dimensiones y cuando las dimensiones de una matriz son iguales entre ellas **(# filas = # columnas)** decimos que la matriz es cuadrada.

Con esto en mente resumimos lo anterior con un ejemplo de suma entre dos matrices cuadradas así:

![https://i.imgur.com/EINCqZt.png](https://i.imgur.com/EINCqZt.png)

Donde vemos que la suma de matrices se hace elemento a elemento para dar origen a otra matriz con las mismas dimensiones. Entonces para obtener el elemento de la primera fila y primera columna de la matriz suma, se suman los elementos correspondientes a cada matriz ubicados en la primera fila y primera columna:

```
1 + (-1) = 0
```

Ahora bien, las matrices también tienen una operación de multiplicación entre ellas que es más compleja de definir que la suma, sin embargo aquí vamos a desglosarla. Vamos a reemplazar los elementos numéricos de las matrices del ejemplo anterior por variables algebraicas, indicando que pueden ser cualquier número para así exponer el proceso con la mayor generalidad posible. De esta manera, vamos a definir el producto de dos matrices cuadradas de tal manera que el resultado sea otra matriz de las mismas dimensiones así:

![https://i.imgur.com/DOf9N1J.png](https://i.imgur.com/DOf9N1J.png)

Donde cada expresión algebraica tiene la forma de dos índices que denotan la fila y columna donde está posicionado el número, respectivamente. Y la manera de calcular cada elemento de la matriz resultante viene dado por una regla sencilla que ilustraremos con el siguiente ejemplo:

![https://i.imgur.com/pA7qH2a.png](https://i.imgur.com/pA7qH2a.png)

Que equivale a decir que el elemento de la fila 1 y columna 1 de la matriz resultado se calcula como la suma de los productos de los elementos de la primera fila de la primera matriz por los elementos de la primera columna de la segunda matriz

![https://i.imgur.com/pjuZwlE.png](https://i.imgur.com/pjuZwlE.png)

Veamos otro ejemplo para tenerlo más claro:

![https://i.imgur.com/2WoNK6j.png](https://i.imgur.com/2WoNK6j.png)

En este caso el elemento de la **fila 1 y columna 2** de la matriz resultado se calcula como la suma de los productos de los elementos de la **primera fila de la primera matriz** por los elementos de la segunda columna de la segunda matriz.

En python el producto de matrices se calcula fácil usando la librería numpy:

```python
np.matmul(A, B)
```

Donde, por ejemplo, una matriz:

![https://i.imgur.com/BJPv2tR.png](https://i.imgur.com/BJPv2tR.png)

Se escribe en python como:

```python
A = np.array([[2, 4], [-1, 2]])
```

Esta definición se hizo para matrices de dos filas y dos columnas que denominamos matrices 2x2. Pero se aplica de la misma manera para matrices cuadradas de cualquier tamaño NxN. Por ahora solo nos interesará esta definición restringida para matrices cuadradas, pero en cualquier curso de álgebra de matrices podrás darte cuenta de que esta definición se puede hacer más general para matrices que no sean necesariamente cuadradas.

Ahora, así como cada número tiene su inverso, donde el inverso se define como aquel número tal que la multiplicación de ambos da 1:

![https://i.imgur.com/SGKZXka.png](https://i.imgur.com/SGKZXka.png)

En este caso ⅙ es el inverso de 6. Así también, las matrices también pueden tener su inversa (aunque no siempre), la matriz inversa A-1de una matriz dada A se define como aquella matriz donde (supongamos que A es 2x2):

![https://i.imgur.com/kEiv8fB.png](https://i.imgur.com/kEiv8fB.png)

El cálculo de matriz inversa se hace rápido usando NumPy nuevamente así:

```python
A = np.array([[2, 4], [-1, 2]])
Ainversa = np.linalg.inv(A)
```

Donde, el resultado de `Ainversa` en este caso particular sería:

```python
array([[ 0.25 , -0.5  ],
	[ 0.125,  0.25 ]])
```

Para comprobar que esto está bien, puedes multiplicar ambas matrices para ver que da lo correcto:

```python
np.matmul(A, Ainversa)
```

## Repaso de Vectores

Como caso particular adicional a la definición anterior, consideremos el producto de una matriz cuadrada por un vector (aquí entendemos un vector como una matriz de una sola columna, también se le denomina por eso vectores columna en muchos libros de álgebra lineal) cuya longitud es igual al número de filas de la matriz así:

![https://i.imgur.com/1aFGNYg.png](https://i.imgur.com/1aFGNYg.png)

Donde definimos que el producto de una matriz por un vector resulta en otro vector de las mismas dimensiones (filas). Y la regla que consideramos para el caso de matrices cuadradas también aplica de manera que los elementos del vector resultante se obtendrían de multiplicar filas por columnas así:

![https://i.imgur.com/9vuSATV.png](https://i.imgur.com/9vuSATV.png)

También tenemos una operación entre vectores que denominamos el producto punto o producto interior. Normalmente al considerar esta definición se representa el primer vector como una sola fila y el segundo como una sola columna así (sigamos pensando con base en el ejemplo anterior de la matriz por el vector, pero ahora la matriz solo tiene una fila):

![https://i.imgur.com/596zIHK.png](https://i.imgur.com/596zIHK.png)

Y como ya te estás dando cuenta (teniendo en mente la misma definición de multiplicación de matrices) al solo haber una fila en la primera matriz y una columna en la segunda matriz, el resultado solo podrá tener un elemento y es por esto que el resultado de multiplicar dos vectores de esta manera es siempre un número:

![https://i.imgur.com/IGNqY7n.png](https://i.imgur.com/IGNqY7n.png)

Simplifiquemos la notación así:

![https://i.imgur.com/ONdFb8h.png](https://i.imgur.com/ONdFb8h.png)

Y esto nos recuerda la clásica regla de multiplicar vectores como *x por x más y por y*. Y si los vectores tienen más dimensiones, entonces *… más z por z* y así. Recuerda que la notación simplificada es porque ahora tenemos que la primera componente es el eje X del vector y la segunda componente el eje Y del vector cuando lo dibujamos en un plano cartesiano.

![https://i.imgur.com/bP7C40X.png](https://i.imgur.com/bP7C40X.png)

Ahora, cuando pensamos en multiplicar un vector por el mismo, la misma definición aplica:

![https://i.imgur.com/doQIHFe.png](https://i.imgur.com/doQIHFe.png)

Y nos damos cuenta de que esto se relaciona con el Teorema de Pitágoras al ver que el producto de un vector por el mismo nos da el cuadrado de la longitud de la flecha que representa al vector en el plano cartesiano:

![https://i.imgur.com/7441gI8.png](https://i.imgur.com/7441gI8.png)

![https://i.imgur.com/qzk7KN3.png](https://i.imgur.com/qzk7KN3.png)

Así vemos que la longitud de un vector, también conocida como norma del vector se calcula como:

![https://i.imgur.com/OUmWoRs.png](https://i.imgur.com/OUmWoRs.png)

Listo, con esto terminamos un repaso básico de lo mínimo de matrices y vectores para lo que viene.

## Vectores y Valores propios de una matriz

En álgebra lineal podemos tener ecuaciones donde la incógnita es un vector, supongamos la siguiente ecuación:

![https://i.imgur.com/mee9AMt.png](https://i.imgur.com/mee9AMt.png)

Aquí A es una matriz cuadrada NxN cuyos elementos conocemos perfectamente y X es un vector columna cuyas componentes desconocemos. Aquí recordemos que multiplicar un vector por un número es simplemente multiplicar cada componente del vector por dicho número.

Entonces lo que esta ecuación nos pregunta es:

¿Existen vectores X tales que al multiplicarlos por la matriz A eso es equivalente a simplemente multiplicarlos por un número?

Si tal vector existe y está asociado a un valor específico de , entonces decimos que el vector X es un **vector propio de la matriz A** y x es su **valor propio correspondiente**.

Consideremos esto para el caso de una matriz 2 x 2, como la siguiente:

![https://i.imgur.com/5AlP07v.png](https://i.imgur.com/5AlP07v.png)

Esto se traduce en el sistema de ecuaciones (haciendo el producto matriz por vector):

![https://i.imgur.com/LVyLKYe.png](https://i.imgur.com/LVyLKYe.png)

Aquí entonces debemos encontrar las combinaciones de x, y e que satisfacen el sistema de ecuaciones. En general, hacer esto requiere otros conceptos más detallados del álgebra de matrices como el cálculo de determinantes y resolver ecuaciones polinomiales cuya explicación solo puede dejarse a un [curso exclusivo de álgebra lineal](https://platzi.com/cursos/algebra-lineal/). Pero no te preocupes, ya que podemos hacer este cálculo de manera rápida con python así:

```python
import numpy as np

A = np.array([[1, 2], [1, 0]])
values, vectors = np.linalg.eig(A)
```

Donde la **matriz A** contiene los elementos exactos de la matriz anterior y el comando `np.linalg.eig(A)` lo que hace es calcular directamente los valores y vectores propios, llamados **values y vectors** en el código, respectivamente.

Verás que esta matriz tiene dos valores propios:

```python
array([ 2., -1.])
```

Con sus respectivos vectores propios asociados:

```python
array([[ 0.89442719, -0.70710678 ],
	[ 0.4472136 , 0.70710678 ]])
```

Aquí es importante anotar que los vectores que entrega la función `np.linalg.eig(A)` son vectores columna de manera que los elementos de la primera columna de `vectors` corresponden con el primer valor de `values` y así sucesivamente. Entonces en nuestro lenguaje matemático usual, escribimos las dos soluciones como:

![vector_uno](https://i.imgur.com/7k3ZwIF.png)

![vector_dos](https://i.imgur.com/ZsJ3LAt.png)

Puedes verificar que cada vector y su respectivo valor propio cumplen la ecuación original ejecutando cada parte así:

```python
np.matmul(A, vectors.T[1])
```

Que te da como resultado:

```python
array([ 0.70710678, -0.70710678])
```

Mientras que por otro lado calculando:

```python
values[1]*vectors.T[1]
```

Resulta en lo mismo:

```python
array([ 0.70710678, -0.70710678])
```

Donde hemos considerado el segundo vector y valor propio respectivamente tomando `λ = -1` y el vector incógnita `X` igual a `vectors.T[1]`.

Uno de los hechos más importantes de obtener los vectores y valores propios de una matriz es poder diagonalizarla. En general se define que una matriz A es diagonalizable si es posible escribirla como el producto de:

![img](https://i.imgur.com/yWyi48D.png)

Donde D es una matriz diagonal (matriz donde todos los elementos por fuera de la diagonal son cero), un ejemplo de matriz diagonal sería:

![img](https://i.imgur.com/tRw3bAM.png)

Y aquí un resultado matemático bien conocido es que si una matriz es diagonalizable, la matriz D se construye colocando sus valores propios en la diagonal y la matriz P se construye colocando en cada columna el vector propio,siguiendo el mismo orden de valores propios correspondientes de la matriz D, así:

![img](https://i.imgur.com/NNiVLu3.png)

Lo importante de estudiar este procedimiento en nuestro curso, es que cuando aplicamos este cálculo de vectores y valores propios a una **matriz de covarianza**, los vectores representan las direcciones a lo largo de las cuales percibimos la mayor cantidad de varianza de ese conjunto de datos, donde la cantidad de varianza es proporcional al valor propio de cada vector propio.

Y es importante tener en cuenta que este procedimiento aplica para un conjunto de datos con N variables al que le corresponde una matriz de covarianza de tamaño NxN.

Ahora, el último factor importante de esta técnica es que para matrices de covarianza, sus vectores propios siempre son independientes unos de otros y esto es justamente lo que queremos en un proceso de reducción de variables, porque direcciones independientes implica que estos vectores representan nuevas variables cuya correlación es la más baja posible y así cada nueva variable es lo más representativa posible.

En álgebra lineal se dice más precisamente que los vectores propios de una matriz de covarianza son ortogonales y esto quiere decir que el producto interno de cualquier par de estos vectores siempre da como resultado cero:

![img](https://i.imgur.com/IygBQDo.png)

Como consecuencia la matriz se denomina matriz ortogonal, y se sabe en matemáticas que la inversa de una matriz ortogonal es igual a la transpuesta, de manera que:

![img](https://i.imgur.com/20Iqk5V.png)

En la próxima clase veremos esto de forma más detallada y visual, te veo allí.

## OJO error arreglado

En esta clase, hay un error muy grave, sobre todo para quienes no conocen los vectores propios. Me refiero a que los vectores propios que entrega`np.linalg.eig(A)`
son vectores columnas, es decir v[:, 0], esta asociado al valor propio lambda_0, v[:, 1]
será el vector asociado a lambda_1 y así sucesivamente. Para este ejemplo la matriz construida a raíz de los vectores propios es:

```
array([[ 0.89442719, -0.70710678 ],
	        [ 0.4472136 , 0.70710678 ]])
```

y los valores propios

```
array([ 2., -1.])
```

Esto quiere decir que el vector

```
array([[0.89442719],
		[0.4472136]])
```

está asociado al eigen valor 2
el vector

```
array([[-0.70710678 ],
		[0.70710678]])
```

esta asociado al valor propio -1
otro dato, esque los vectores que entrega está función están normalizados y se cumple que `sqrt((0.89442719)^2 + (0.4472136)^2)=1`
`sqrt((-0.70710678)^2 + (0.70710678)^2)=1`
Esto pasa desapercibido en este ejemplo, pero es importante

