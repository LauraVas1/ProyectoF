# __Proyecto Final Bootcamp.__
Bienvenidos a mi proyecto final, resultado del intenso trabajo realizado en el Bootcamp de Análisis de Datos. Enfocado en la diabetes, este análisis ofrece información detallada respaldada por el dataset "diabetesDataAnslysis" de Kaggle. El objetivo es proporcionar una visión clara y educativa sobre la diabetes, con el deseo de contribuir al entendimiento de esta condición. ¡Acompáñenme en este recorrido informativo!

Saludos, Laura Arango.
R.jpg

## Enlace del Google Slides
[Google Slides](https://docs.google.com/presentation/d/e/2PACX-1vR6NvXstAIkeumXwV7QvKLFAMQNAtwRPYEboTpqVFpq2JdrBqby8e7J1Lv7zU4JmA/pub?start=false&loop=false&delayms=3000&slide=id.p23)

## Descripción del proyecto.
Este proyecto destaca un conjunto de datos enfocado en la diabetes entre la población joven a nivel global. La preocupante tendencia de que la diabetes afecte a personas más jóvenes es el centro de esta investigación. La clínica EVER juega un papel crucial al realizar análisis de desarrollo relacionados con la sangre, proporcionando información valiosa para comprender mejor esta problemática.

La conexión emocional entre los abuelos y los jóvenes es evidente, ya que los primeros experimentan tristeza al ver a sus seres queridos enfrentar problemas de salud. Este escenario se agrava cuando sus familias necesitan realizar exámenes de manera regular. A través de esta investigación, busco arrojar luz sobre la incidencia temprana de la diabetes en la población joven y ofrecer información que contribuya a mejorar la salud y el bienestar de las generaciones futuras. ¡Acompáñenme en este viaje para comprender y abordar este desafío de salud global! <br>


## Scripts
[Scripts de Python](https://colab.research.google.com/drive/1oghrKEsMio9rhX7O1bDV9IoijGLimeKl?usp=sharing)

* Importamos las bibliotecas necesarias para visualización de datos y análisis exploratorio. <br>
-__*matplotlib.pyplot:*__ Biblioteca para crear gráficos y visualizaciones estáticas, animadas e interactivas en Python. <br>
-__*seaborn:*__ Biblioteca para crear gráficos estadísticos atractivos e informativos en Python. <br>
-__*pandas:*__ Biblioteca la cual es una poderosa herramienta para manipulación y análisis de datos. <br>
```ruby
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```
* Leemos datos desde archivo __CSV__. <br>
```ruby
csv_path="https://raw.githubusercontent.com/LauraVas1/ProyectoF/main/diabetes.csv"
laura = pd.read_csv(csv_path, sep=",")
```
* Creamos la lista __headers__. <br>
-IMC=ÍNDICE DE MASA CORPORAL.
```ruby
headers = ["Embarazos","Glucosa","Presion-arterial","Grosor-piel","Insulina","IMC","Funcion-PedigriDiabetes","Edad","Resultado"] 
laura.columns = headers

laura.head()
```
* La función __dtype__ genera una tabla con el tipo de dato de cada columna.
```ruby
laura.dtypes
```
* Reemplazamos 1 por __"Positivo"__ y 0 por __"Negativo"__.
```ruby
laura['Resultado'] = laura['Resultado'].replace({1: 'Positivo', 0: 'Negativo'})
laura.head()
```
* Comprobación de la cantidad de filas y columnas del conjunto de datos.
```ruby
laura.shape
```
-__*count:*__ Número total de observaciones o elementos en un conjunto de datos. <br>
-__*mean:*__ El valor promedio de un conjunto de datos. <br>
-__*std:*__ Mide la dispersión o la variabilidad de un conjunto de datos. <br>
-__*min:*__ El valor más pequeño en un conjunto de datos. <br>
-__*max:*__ El valor más grande en un conjunto de datos. <br>
```ruby
laura.describe()
```
* Información concisa sobre el DataFrame llamado __"laura"__.
```ruby
laura.info()
```
* La función __dtype__ genera una tabla con el tipo de dato de cada columna.
```ruby
laura.dtypes
```
* Eliminamos filas con valores __nulos__. <br>
* Eliminamos filas __duplicadas__ basadas en todas las columnas. <br>
```ruby
laura= laura.dropna()
laura = laura.drop_duplicates()
```
* Creamos un __histograma__ para la columna __'Edad'__ del DataFrame __laura__. <br>
* Figsize=(5,5) especifica las dimensiones del gráfico en pulgadas. <br>
```ruby
laura['Edad'].hist(figsize=(5,5))
```
* Utilizamos __Seaborn__ para crear un __diagrama__ de distribución (histograma y KDE) para la columna __'Edad'__ del DataFrame __laura__.
```ruby
sns.distplot(laura['Edad'])
```
* Creamos una figura con dimensiones específicas (5x5 pulgadas). <br>
* Creamos un diagrama de caja __(boxplot)__ para la columna __'Embarazos'__ del DataFrame __laura__. <br>
-Esto ayuda a visualizar la distribución de los datos, identificar outliers, y observar la tendencia central y dispersión. <br>
```ruby
fig=plt.figure(figsize=(5,5))
sns.boxplot(y=laura["Embarazos"])
```
* Calculamos estadísticas descriptivas para la columna __'Embarazos'__ del DataFrame __laura__. <br>
-__*mean:*__ Calcula la media (promedio). <br>
-__*median:*__ Calcula la mediana. <br>
-__*mode:*__ Calcula la moda. <br>
-__*skew:*__ Calcula la asimetría (skewness). <br>
-__*kurt:*__ Calcula la curtosis (kurtosis). <br>
```ruby
mean = laura['Embarazos'].mean()  
median = laura['Embarazos'].median() 
mode = laura['Embarazos'].mode()  
skew = laura['Embarazos'].skew()  
kurt = laura['Embarazos'].kurt()

print("La media es :",mean)
print("La mediana es :",median)
print("La moda es :",mode)
print("El sesgo es :",skew)
print("La kurtosis es :",kurt)
```
* Creamos un __histograma__ para la columna __'Resultado'__ del DataFrame __laura__. <br>
* Figsize=(5,5) especifica las dimensiones del gráfico en pulgadas. <br>
```ruby
laura['Resultado'].hist(figsize=(5,5))
```
* Esta biblioteca proporciona un __informe__ de análisis exploratorio de datos __(EDA)__ con una sola línea de código. <br>
```ruby
!pip install pandas_profiling==3.0.0
!pip install pandas_profiling --upgrade
```
* Importamos la biblioteca __pandas_profiling__. <br>
* Esta biblioteca proporciona herramientas para el análisis exploratorio de datos, permitiendo generar informes detallados de un DataFrame. <br>
```ruby
import pandas_profiling
```
* Generamos el __informe__.<br>
* Guardamos el informe como un archivo __HTML__. <br>
-Si deseas visualizar el informe dentro del notebook puedes usar la siguiente línea: __diabetesDataAnslysis.to_notebook_iframe()__ <br>
```ruby
diabetesDataAnslysis = pandas_profiling.ProfileReport(laura)
diabetesDataAnslysis.to_file(output_file="diabetesDataAnslysis.html")
diabetesDataAnslysis.to_notebook_iframe()
```
* Guardamos nuestro dataframe como archivo __csv__. <br>
* __Descargamos__ el archivo csv. <br>
```ruby
from google.colab import files
laura.to_csv('diabetesDataAnslysis.csv') 
files.download('diabetesDataAnslysis.csv')
```


* Enlace o referencia al dataset elegido
[Enlace](https://www.kaggle.com/datasets/willianoliveiragibin/diabetesdataanslysis/data)


## Documentación del Proyecto: Análisis de Datos sobre la Diabetes

### Introducción:

Este proyecto se desarrolló con el objetivo de explorar y compartir información valiosa sobre la diabetes. Se utilizaron diversas herramientas a lo largo del proceso, incluyendo Kaggle, Google Colab, Power BI y GitHub.

### Herramientas Utilizadas:

- __Kaggle:__ La plataforma proporcionó el dataset "diabetesDataAnslysis", esencial para la investigación y análisis.

- __Google Colab:__ Se empleó para llevar a cabo la limpieza de datos y preparar el dataset de manera adecuada, asegurando la calidad de la información.

- __Power BI:__ La herramienta facilitó la creación de informes visuales detallados, permitiendo una comprensión más profunda de los datos.

- __GitHub:__ Se utilizó para alojar y compartir el proyecto de manera accesible.

### Proceso:

- __Exploración de Datos:__ Kaggle proporcionó el dataset necesario, que fue analizado y limpiado en Google Colab para garantizar la validez y precisión de los resultados.

- __Visualización y Análisis:__ Power BI fue instrumental para representar visualmente los datos y obtener insights significativos.

- __Presentación:__ Se creó una presentación en PowerPoint para resumir los hallazgos y proporcionar una visión general del proyecto.

### Experiencia y Aprendizajes:

Realizar este proyecto fue una experiencia fascinante. Aprender sobre la diabetes, desde sus causas hasta su tratamiento, fue enriquecedor. La investigación y el análisis permitieron comprender la importancia de la conciencia sobre la diabetes, y la creación de recursos accesibles es clave para llegar a un público más amplio.

### Desafíos y Recompensas:

El proyecto no estuvo exento de desafíos, pero cada obstáculo superado se tradujo en un aprendizaje valioso. La dedicación y el tiempo invertido fueron fundamentales para lograr resultados significativos. Realizar este proyecto fue un proceso divertido y educativo.

### Mensaje Final:

Este proyecto no solo fue un ejercicio técnico, sino también una oportunidad para contribuir al conocimiento público sobre la diabetes. Si bien fue un desafío, la experiencia resultó gratificante y ofrece una base sólida para futuros proyectos similares. ¡A seguir aprendiendo y compartiendo!
[Imagen](https://th.bing.com/th/id/R.b4ef62457cdaa01a89fbbbf33800dbc0?rik=rCd%2fEX35K%2bvt8g&riu=http%3a%2f%2f2.bp.blogspot.com%2f-pShIPwSptN8%2fTw8Zn3ITo-I%2fAAAAAAAAAAg%2fKybT4wVlHks%2fs1600%2fhoratierra1.jpg&ehk=YsNYOXrDUhEJyPNSOJ8GmB2w7fKccIjvNtioMliAoDU%3d&risl=&pid=ImgRaw&r=0)
