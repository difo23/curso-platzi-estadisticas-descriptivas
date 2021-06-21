---
title: "Cursos de matemáticas para data science: Estadísticas descriptivas"
classes: "4-25"
publishDate: "2021-06-21"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## ¿Cómo usar Deepnote?

- | Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
  | ------------- | ------------------------------------------------------------ |
  | **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
  | **Teacher:**  | Francisco Camacho                                            |
  | **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |


## Notes 

> **Deepnote recientemente liberó una manera avanzada de visualizaciones sin código en las celdas del notebook,** esta funcionalidad fue liberada luego de grabar este curso, es decir no existía al momento de grabar esta clase, les dejo el link del vídeo que ellos hicieron para publicar este update del producto: [DeepNote new char features without code](https://www.youtube.com/watch?v=3PhEO41WVLQ)

### Tipos de datos en estadística inferencial

- Datos categóricos: ordinales y nominales
- Datos numéricos: discretos y continuos

### Descripción del dataset utilizado

> [Kaggle dataset](https://www.kaggle.com/lepchenkov/usedcarscatalog) The dataset is collected from various web resources in order to explore the used cars market and try to build a model that effectively predicts the price of the car based on its parameters (both numerical and categorical)
>
> ### Content
>
> The data is scraped in Belarus (western Europe) on the 2nd of December 2019, so the dataset is pretty fresh and relevant.

### Atajos de teclado en Deepnote:

Si quieres moverte mas rápido por los bloques de código, te invito a que revises la paleta de comandos que ofrece Deepnote, puedes acceder con `ctrl+p` , presionado `Esc` o dando clic al icono de la parte inferior izquierda.

![Screenshot 2021-06-18 202048.jpg](https://static.platzi.com/media/user_upload/Screenshot%202021-06-18%20202048-e1bd8794-8eac-4ea9-aecc-6c04186ec7ba.jpg)

Se te desplegara un menú, es muy parecido a las `jupyter notebook` pero si tiene un par de diferencias para insertar celdas por debajo o encima. Dejo un pequeño resumen de los comandos mas utilizados a mi criterio.

- `ctrl + k` añadir un bloque de código por encima del bloque actual
- `ctrl + j` añadir un bloque de código por debajo del bloque actual
- `ctrl+enter` ejecutar el bloque actual
- `alt + shift + flecha arriba` mover un bloque arriba
- `alt + shift + flecha abajo` mover un bloque abajo
- `ctrl + shift + D` duplicar el bloque

### Load CSV

```python
import pandas as pd
df = pd.read_csv('cars.csv') # Crea un dataframe desde un archivo .csv
```

### Tipos de datos - (Estadística vs Python types)

```Python
df.dtypes # Muestra los tipos de datos en el dataframe
```

Aquí vemos que los tipos de datos se identifican de la siguiente manera:

- Categóricos: `object`, `bool`
- Numéricos: `int64` (discreto), `float64` (continuo)

### Generando estadísticos con pandas:

```python 
df.describe()
```

* Count  - Cuenta el numero de filas

* Mean   - El promedio de los valores de cada columna

* STD  - Desviación estándar

* Min   - Valor mínimo 

* 25%  -  El 25% de los datos esta por debajo de este valor

* 50%  - El 50% de los datos esta por debajo de este valor (Median)

* 75%  - El 75% de los datos esta por debajo de este valor

* Max  - Valor máximo

  

## Medidas de tendencia central

> Estadísticas en la in-gesta de datos

* **Media (Promedio)**

* **Mediana (Dato central)**
* **Moda (Dato que mas se repite)**

## Otras medidas centrales menos usadas

- **Media ponderada:** es una medida de tendencia central, que es apropiada cuando en un conjunto de datos cada uno de ellos tiene una importancia relativa (o peso) respecto de los demás datos. Se obtiene multiplicando cada uno de los datos por su ponderación (peso) para luego sumarlos, obteniendo así una suma ponderada; después se divide esta entre la suma de los pesos, dando como resultado la media ponderada.
- **Media armónica:** La media armónica es igual al número de elementos de un grupo de cifras entre la suma de los inversos de cada una de estas cifras.
  En otras palabras, la media armónica es una medida estadística recíproca a la media aritmética, que es la suma de un conjunto de valores entre el número de observaciones.
- **Media geométrica:** es una cantidad arbitraria de números (por decir n números) es la raíz n-ésima del producto de todos los números; es recomendada para datos de progresión geométrica, para promediar razones, interés compuesto y números índice.

## Tabla de frecuencias y Diagrama de frecuencia

![Screenshot_4.png](https://static.platzi.com/media/user_upload/Screenshot_4-8b680ddc-98de-4392-8bd9-ceae687c85a4.jpg)

![Untitled (1).png](https://static.platzi.com/media/user_upload/Untitled%20%281%29-6c9ab365-1d8c-4325-96ab-37f9687a2371.jpg)

## Cuando usar? 

* La media es susceptible a valores atípicos.
* La moda no aplica para datos numéricos continuos. 

## Metáfora de Bill Gates en un bar

![media.jpg](https://static.platzi.com/media/user_upload/media-c8e7f52b-5ffa-47e4-b3ec-a9e2959b8a63.jpg)

**Nota:** La mediana no se ve afectada por valores sesgados o desviados,  el promedio si se ve afectados por estos valores. La mediana resulta ser una medida de valor central mas adecuada para observar distribuciones. El ejemplo de Bill Gates representa muy bien esta característica de la mediana, si comparamos los salarios de personas en un bar y agregamos un valor desviado como el salario de Bill Gates. 


$$
\frac{1}{N} \sum_{i=1}^N x_i
$$
Mediana (impar) = 
$$
x_{(n+1)/2}^{\text{ordered}}
$$
Mediana (par ) =
$$
\frac{x_{n/2}^{\text{ordered}} + x_{n/2+1}^{\text{ordered}}}{2}
$$
Moda = 
$$
x_k
$$
Donde 
$$
\text{Freq}(x_k) = \max{(\text{Freq}(x_i))}
$$
  



## Pandas en acción medidas centrales y gráficas

```python
import pandas as pd 
import seaborn as sns

df = pd.read_csv('cars.csv')
df.head()

df['price_usd'].mean()
df['price_usd'].median()

df['price_usd'].plot.hist(bins=20)

sns.displot(df, x = 'price_usd', hue = 'manufacturer_name')
sns.displot(df, x="price_usd", hue="engine_type")
sns.displot(df, x='price_usd', hue = 'engine_type', multiple='stack')


df.groupby('engine_type').count()

#RETO: Inspeccionemos precios de una marca y modelo particular !

Q7_df = df[(df['manufacturer_name']=='Audi') & (df['model_name']=='Q7')]
sns.histplot(Q7_df, x='price_usd', hue = 'year_produced')

```

