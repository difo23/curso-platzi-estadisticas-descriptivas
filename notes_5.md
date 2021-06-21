---
title: "Cursos de matemáticas para data science: Estadísticas descriptivas"
classes: "4-25"
publishDate: "2021-06-21"
thumbnailImage: ""
shareText: " Description: Curso complementario en la escuela de DS con platzi "
hashtags: ['learn']
draft: false

---

## Medidas de tendencia central en Python

- | Source:       | https://platzi.com/clases/estadistica-descriptiva/           |
  | ------------- | ------------------------------------------------------------ |
  | **Course:**   | Curso de Matemáticas para Data Science: Estadística Descriptiva |
  | **Teacher:**  | Francisco Camacho                                            |
  | **Notebook:** | [Personal deepnote](https://deepnote.com/project/curso-estadistica-descriptiva-2021-Duplicate-7uTueWZDQ-aKrq24bLdf2A) |


## Notes

### Pandas en acción medidas centrales y gráficas

```python
import pandas as pd 
import seaborn as sns

df = pd.read_csv('cars.csv')
df.head()

# Valores centrales promedio y mediana
df['price_usd'].mean()
df['price_usd'].median()

# Diagrama de frecuencias o Histograma (Las barras corresponde a un rango de valores)
df['price_usd'].plot.hist(bins=20)

# Seaborn libreria con enfoque estadistico
# Hue separa los datos en categorias

# Separar el precio por fabricante
sns.displot(df, x = 'price_usd', hue = 'manufacturer_name')

# Separar el precio por tipo de motor
sns.displot(df, x="price_usd", hue="engine_type")

# multiple = tack sirve para mostrar las barras apiladas una encima d ela otra.
sns.displot(df, x='price_usd', hue = 'engine_type', multiple='stack')

# Otro estadistico descritivo es el conteo, usando groupby podemos usar estadisticos
df.groupby('engine_type').count()

#RETO: Inspeccionemos precios de una marca y modelo particular !
Q7_df = df[(df['manufacturer_name']=='Audi') & (df['model_name']=='Q7')]

# Grafica para el modelo Q7
sns.histplot(Q7_df, x='price_usd', hue = 'year_produced')

```

[Mas información sobre Seaborn...](https://seaborn.pydata.org/tutorial/distributions.html)

