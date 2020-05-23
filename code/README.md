# Read data
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pilo1961/QuestionAnswer_System/blob/master/code/read_data.ipynb) Abrir en colab

Read, explore and format data
inputs:
* train-v1.0.json
Output:
* df_train.pkl - pickle with train data
* word2vec_cbow.okl - Pickle con modelo entrenado de word2Vec usando CBOW
* word2vec_skipgram.okl - Pickle con modelo entrenado de word2Vec usando skip-gram

# Sentence embedding
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pilo1961/QuestionAnswer_System/blob/master/code/SentenceEncoder.ipynb) Abrir en colab

Carga los datos y genera los embeddings de oraciones.
Inputs:
* df_train.pkl - Datos de entrenamiento
* df_test.pkl - Datos de prueba
* models.py - Modulo de funciones de InferSent
* infersent1.pkl - Pickle de embedding de infersent
* glove.840B.300d.txt - Embedding preentrenado GloVE
* 
Outputs:
* train_dict.pkl - Pickle con el embedding de las oaciones de los contextos de entrenamiento
* train_question.pkl - Pickle con el embedding de las preguntas de entrenamiento
* test_dict.pkl - Pickle con el embedding de las oaciones de los contextos de prueba
* test_question.pkl - Pickle con el embedding de las preguntas de entrenamiento

# Processing
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pilo1961/QuestionAnswer_System/blob/master/code/Processing.ipynb) Abrir en colab

Se genera la variable target, se calculan las distancias euclidiana y coseno a los datos.
Se hace una predicción utlizando las distancias entre las oraciones.
Se hace el análsis de raíz de las oracioens y se hace el df con el encoder de que oración tiene la misma raíz que las pregutnas.

Inputs:
* df_train.pkl - Data frame que contiene los datos de los contextos y las pregutnas
* train_question.pkl - Embedding con la información de las preguntas
* train_dict.pkl - diccionario que contiene el embedding de los contextos y las oraciones

Output:
* dist_cosine.pkl - Pickle que tiene las distancias coseno entre las preguntas y las oraciones del contexto 
* dist_euclid.pkl - Pickle que tiene las distancias euclidianas entre las preguntas y las oraciones del contexto 
* question_root.pkl - Pickle que tiene la palabra raíz de las preguntas
* question_root.pkl - Pickle que contiene las palabras raíz de las oraciones
* root_ohe.pkl - Pickle con el one hot encoder de la raices que coinciden entre oraciones y preguntas

# Model
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pilo1961/QuestionAnswer_System/blob/master/code/Models.ipynb) Abrir en colab

Se hacen transformaciones a los datos, se contruye la matriz de ML.
Se corre un magic loop y se escoge el mejor modelo.
Se presenta la matriz de confusión.

Inputs:
* root_ohe.pkl - Pickle que contiene el ohe de la raiz de las oraciones.
* dist_euclid.pkl - Pickle con una lista que tiene las distancias euclidians entre la pregunta y las oraciones del contexto.
* dist_cosine.pkl - Pickle con una lista que tiene las distancias coseno entre la pregunta y las oraciones del contexto.
* train_target.pkl - Data frame que contiene 

Outputs:
