
<div align='center'>
  
# Pipeline: Implementación del Sistema de Preguntas y Respuestas

</div>

***

<div align='justify'>

##  1. Análisis Exploratorio de los Datos

Read, explore and format data

>Inputs:

* train-v1.0.json

>Output:

* df_train.pkl - pickle with train data
* word2vec_cbow.okl - Pickle con modelo entrenado de word2Vec usando CBOW
* word2vec_skipgram.okl - Pickle con modelo entrenado de word2Vec usando skip-gram

>Notebook asociado: [`01-eda.ipynb`](https://github.com/Pilo1961/QuestionAnswer_System/blob/master/code/01-eda.ipynb).


## 2. Embeddings

Carga los datos y genera los embeddings de oraciones.

>Inputs:

* df_train.pkl - Datos de entrenamiento
* df_test.pkl - Datos de prueba
* models.py - Modulo de funciones de InferSent
* infersent1.pkl - Pickle de embedding de infersent
* glove.840B.300d.txt - Embedding preentrenado GloVE

>Outputs:

* train_dict.pkl - Pickle con el embedding de las oaciones de los contextos de entrenamiento
* train_question.pkl - Pickle con el embedding de las preguntas de entrenamiento
* test_dict.pkl - Pickle con el embedding de las oaciones de los contextos de prueba
* test_question.pkl - Pickle con el embedding de las preguntas de entrenamiento

>Notebook asociado: [`02-embeddings.ipynb`](https://github.com/Pilo1961/QuestionAnswer_System/blob/master/code/02-embeddings.ipynb)

## 3. Processing and feature engineering

i) Generación de la variable target; ii) Calculo de las distancias euclidiana y coseno a los datos; iii) Análisis de raíz de las oraciones; iv) Definición del dataframe con el encoder que indica qué oración tiene la misma raíz que las preguntas.

En el intermedio, implementamos un modelo no supervisado con las distancias cosenos y euclidianas y generamos las primeras predicciones.

>Inputs:

* df_train.pkl - Data frame que contiene los datos de los contextos y las pregutnas
* train_question.pkl - Embedding con la información de las preguntas
* train_dict.pkl - diccionario que contiene el embedding de los contextos y las oraciones

>Output:

* dist_cosine.pkl - Pickle que tiene las distancias coseno entre las preguntas y las oraciones del contexto 
* dist_euclid.pkl - Pickle que tiene las distancias euclidianas entre las preguntas y las oraciones del contexto 
* question_root.pkl - Pickle que tiene la palabra raíz de las preguntas
* question_root.pkl - Pickle que contiene las palabras raíz de las oraciones
* root_ohe.pkl - Pickle con el one hot encoder de la raices que coinciden entre oraciones y preguntas.

> Notebook asociado: [`03-processing.ipynb`](https://github.com/Pilo1961/QuestionAnswer_System/blob/master/code/03-processing.ipynb)

## 4. Transform and Supervised Modelling 

i) Transformaciones a los datos, se contruye la matriz de ML.
Se corre un magic loop y se escoge el mejor modelo.
Se presenta la matriz de confusión.

>Inputs:

* root_ohe.pkl - Pickle que contiene el ohe de la raiz de las oraciones.
* dist_euclid.pkl - Pickle con una lista que tiene las distancias euclidians entre la pregunta y las oraciones del contexto.
* dist_cosine.pkl - Pickle con una lista que tiene las distancias coseno entre la pregunta y las oraciones del contexto.
* train_target.pkl - Data frame que contiene 

>Outputs:
* hyperparameters.pkl - Archivo con la información de los mejores parámetro encontrados en el magic loop
* model.pkl - Modelo entrenado con los mejores parámetros.

>Notebook asociado:[`04-modelling.ipynb`](https://github.com/Pilo1961/QuestionAnswer_System/blob/master/code/04-modelling.ipynb)

## 5. Prueba
En este notebook se replican las transformaciones que se le hacen a los datos de entrenamiento para los datos de prueba.
Se hacen las predicciones con el modelo que mejor ajusta a los datos de entrenamiento.

>Inputs:

* model.pkl - Modelo entrenado
* dev-v1.0.json - Datos originales de prueba
* df_test.pkl
* test_dict.pkl - Embedding de contextos para los datos de prueba
* test_question.pkl - Embedding de preguntas para los datos de prueba

Outputs:
* root_ohe_test.pkl - Pickle que contiene el ohe de la raiz de las oraciones.
* dist_euclid_test.pkl - Pickle con una lista que tiene las distancias euclidians entre la pregunta y las oraciones del contexto.
* dist_cosine_test.pkl - Pickle con una lista que tiene las distancias coseno entre la pregunta y las oraciones del contexto.

>Notebook asociado:[`05-testing.ipynb`](https://github.com/Pilo1961/QuestionAnswer_System/blob/master/code/05-testing.ipynb)


</div>
