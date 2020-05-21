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
