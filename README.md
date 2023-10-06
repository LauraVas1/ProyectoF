# __Proyecto Final Bootcamp.__

## Enlace del Google Slides

## Descripción del proyecto.
Mi proyecto se centra en un Dataset que trata sobre la diabetes en personas jóvenes alrededor del mundo, ya que esta enfermedad se presenta cada vez a edades más tempranas. La clínica EVER realiza análisis de desarrollo relacionados con la sangre. Los abuelos a menudo experimentan tristeza al ver a los jóvenes enfrentar problemas de salud, ya que sus familias necesitan realizar exámenes de manera regular. Esta investigación busca comprender mejor y abordar la incidencia temprana de la diabetes en la población joven, ofreciendo información valiosa para mejorar la salud y el bienestar de las generaciones futuras. <br>


## Scripts
[Scripts de Python](https://colab.research.google.com/drive/1oghrKEsMio9rhX7O1bDV9IoijGLimeKl?usp=sharing)

* Importamos las bibliotecas necesarias para visualización de datos y análisis exploratorio. <br>
-__*matplotlib.pyplot:*__ Biblioteca para crear gráficos y visualizaciones estáticas, animadas e interactivas en Python. <br>
-__*seaborn:*__ Biblioteca para crear gráficos estadísticos atractivos y informativos en Python. <br>
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


## Documentación
La tabla de correlación proporciona información sobre las relaciones entre diferentes variables en el conjunto de datos sobre diabetes. Los valores de correlación varían de -1 a 1, donde: <br>
Una correlación positiva (más cercana a 1) indica una fuerte relación positiva, lo que significa que a medida que una variable aumenta, la otra tiende a aumentar también. <br>
Una correlación negativa (más cercana a -1) indica una fuerte relación negativa, lo que significa que a medida que una variable aumenta, la otra tiende a disminuir. <br>
Un valor de correlación cercano a 0 sugiere una relación lineal débil o nula entre las variables.

