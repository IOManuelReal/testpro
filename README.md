# testpro

# Pruebas de Markdown
# Examen 
## Instructions
> Desarrollar las siguientes instrucciones en Spark con el leguaje de programación Scala,
> utilizando solo la documentacion de la librería de Machine Learning Mllib de Spark y
> Google.

- ### Activity 1
> Cargar en un dataframe Iris.csv que se encuentra en
> https://github.com/jcromerohdz/iris, elaborar la liempieza de datos necesaria para ser
> procesado por el siguiente algoritmo (Importante, esta limpieza debe ser por
> medio de un script de Scala en Spark) . 
> 
> a. Utilice la librería Mllib de Spark el algoritmo de Machine Learning multilayer
> perceptron

Set the csv file with the optimal configuration. <br>
The header option is to set the first column of the file as the header of my dataframe. <br>
The inferSchema option, check all the rows of my table and infers the columns type of data. <br>

```
val df = spark.read.format("csv").option("header", "true").option("inferSchema", "true").load("C:/Users/GAMER/Desktop/iris.csv")
```

- ### Activity 7
 > Construya el modelo de clasificación y explique su arquitectura.
 
Split de csv data in a 7:3 ratio for training and testing respectively. <br>
First make the Logistic Regression training model and then the final model. <br>

```
val seed = 5043
val Array(trainingData, testData) = labelDf.randomSplit(Array(0.7, 0.3), seed)

val logisticRegression = new LogisticRegression().setMaxIter(100).setRegParam(0.02).setElasticNetParam(0.8)

val logisticRegressionModel = logisticRegression.fit(trainingData)

val predictionDf = logisticRegressionModel.transform(testData)
```
