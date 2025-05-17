Análisis Exploratorio de Datos (EDA) - Dataset Iris
📌 Introducción
Este proyecto realiza un Análisis Exploratorio de Datos (EDA) en el famoso dataset Iris, que contiene medidas de pétalos y sépalos de distintas especies de flores.
Los atributos del dataset incluyen:
- Longitud del sépalo (sep_l)
- Anchura del sépalo (sep_a)
- Longitud del pétalo (pet_l)
- Anchura del pétalo (pet_a)
- Especie (Especies) (categórico)
El objetivo es comprender la estructura y distribución de los datos, así como identificar patrones y relaciones entre las variables.

📂 Instalación y Configuración
Para ejecutar el análisis, asegúrate de tener instaladas las siguientes librerías en Python:
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


También configuramos el estilo de los gráficos:
plt.style.use("bmh")  # Estilo predeterminado
sns.set(style="whitegrid")  # Fondo con cuadrícula blanca



📊 Carga y Preprocesamiento de Datos
El dataset se carga con:
df = pd.read_csv("/content/IRIS - IRIS.csv")  # Cargar datos


Se renombraron las columnas para facilitar el código:
df.rename({
    'sepal-length': 'sep_l',
    'sepal-width': 'sep_a',
    'petal-length': 'pet_l',
    'petal-width': 'pet_a',
    'species': 'Especies'
}, axis=1, inplace=True)



🔍 Análisis Descriptivo
Para conocer el dataset, analizamos:
- Dimensiones: df.shape
- Tipo de datos: df.info()
- Estadísticas generales: df.describe()
- Cantidad de especies: df['Especies'].value_counts()
También verificamos valores nulos:
df.isnull().sum()



📈 Análisis Univariado
Se realizaron gráficos de distribución para cada variable, incluyendo:
- Histogramas con KDE para observar distribuciones.
- Boxplots para detectar valores atípicos.
- Violin plots para ver densidad y variabilidad.
Ejemplo de análisis para la longitud del sépalo:
sns.histplot(df['sep_l'], kde=True, bins=20, color='purple')
sns.boxplot(y=df['sep_l'], color='lightgreen')
sns.violinplot(y=df['sep_l'], color='lightblue')



🔗 Análisis Multivariado
Comparamos variables entre especies con:
- Histogramas apilados
- Boxplots
- Violin plots
- Gráficos de dispersión
Ejemplo:
sns.scatterplot(data=df, x='sep_l', y='pet_l', hue='Especies', palette='Set1')



📌 Correlación entre Variables
Para analizar relaciones numéricas, calculamos la matriz de correlación y la visualizamos con un heatmap:
correlation_matrix = df.drop(columns=['Especies']).corr()
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', vmin=-1, vmax=1)


También usamos un pairplot para visualizar dependencias:
sns.pairplot(df, hue='Especies', markers=["o", "s", "d"], palette='Set1')



✅ Conclusiones
El análisis sugiere que:
- Longitud y anchura de pétalos son clave para identificar la especie.
- Las distribuciones muestran diferencias significativas entre las especies.
- La matriz de correlación indica relaciones fuertes entre longitud y ancho de pétalos.
Este EDA proporciona una base sólida para estudios posteriores, como clasificación de especies con modelos de Machine Learning. 🚀


