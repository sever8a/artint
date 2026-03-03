 # NLP

 Modelos específicos para cada tarea.

 Siempre centrados en el procesamiento del lenguaje.

 ## Era simbólica basada en reglas
 
 1954 experimento de IBM, basada en reglas. Modelos muy frágiles, fallan cuando salen de las reglas.

 60s-70s **Gramáticas formales** los modelos se basan en reglas lingüísticas abstractas.

 80s **Parsers sintácticos** las reglas se organizan de manera jerárquica para su analisis.

 ## Era de la estadística

 1990-1995 Reglas de Markov para lenguaje, se predice la siguiente palabra en base a las últimas palabras. Es muy ineficiente, ya que es necesario el contexto de toda la frase.

 1996-1999 Bayes, utiliza sus avances en la estadística para hacer modelos de clasificación de tipos de texto (análisis de sentimiento). Basados exclusivamente en probabilidad, no son útiles. Se utilizaron para la clasificación.

 2000-2005 Representación vectorial del texto. TF-IDF, lo embedings.

 2005-2010 SVM Estado del arte en clasificación, etiquetado de secuencias.

 2010-2012 Feature Engineering, el rendimiento depende de la ingeniería manual. Requiere mucho diseño humando y no generaliza bien.

 ## Era de las Redes Nueroalnes y Deep Learning

 ### Primer deep learnign para NLP

 2013 Word2Vec Palabras representadas como vectores. Realizado por Google, los humanos no entienden los valores numéricos que componen los vectores. No se puede interpretar la procedencia de esos valores.

 2014: GloVe, captura mejor las relaciones globales del texto.

 2014-2016 RNN, analizan secuencialmente el texto. Pero tienen poca memoria, demasiado poco para poder tener un contexto global del texto. Dificultad para capturar dependencias lógicas.

 ### RNN Avanzadas

 2015:LSTM y GRU Mejora la memoria a largo plazo. Problemas de límite físico por el alto consumo de hardware.

 2016: Seq2Seq con atención, grandes avances en traducción automática. Establece la función de las palabras, teniendo la información completa del texto. El problema es el coste computacional.

 ### Revolución transformer

 2017, Transformer, con auto atención y paralelismo.

 2018 BERT, tiene un entrenamiento bidirección. Tiene la estructura transformer que permite ver el texto en diferentes direcciones.

 2019 GPT2 Modelos generativos a gran escala. Comienza el impacto transversal de la Ia en todos los ámbitos. Comienza la comercialización, y aumenta la investigación en algoritmos y hardware.

 2020 GPT3 Modelos gigantes especializados en una tarea concreta (modelos foundation). Aprende de todos los datos de Internet.

 2022 Multimodalidad, una vez dominada la generación de texto, se generan otros elementos, audio, vídeo, imágenes. Un modelo es multimodal cuando admite varias entradas, o varias salidas. 

 !!! info "No todos son multimodales"

        Hay modelos que no son multimodales, son orquestaciones. Admiten diferentes formatos de entrada pero actuan diferentes modelos.

        Al hacerlo de manera orquestada se pierde rendimiento. Por ejemplo, un audio transcrito en texto por un modelo, pierde el contexto de ruidos de fondo. Para que diga un texto, cantando o recitando, tiene que ser multimodal, porque debe mantener el contexto.





