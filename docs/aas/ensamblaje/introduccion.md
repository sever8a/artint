# Introducción
Si se suman las predicciones de un grupo de predictores (como clasificadores o regresores), a menudo se obtendrán predicciones mejores que con el mejor predictor individual. Un grupo de predictores se denomina **ensamble**. Esta técnica se conoce como **ensamblaje** y un algoritmo de ensamblaje se llama **método de ensamblaje**.

Un ejemplo de método de ensamblaje puede ser un grupo de árboles de decisión, cada uno en un subconjunto aleatorio del conjunto de entrenamiento diferente. Posteriormente se obtienen las predicciones de todos los árboles individuales y la clase que consigue más votos es la predicción del ensamble.

A menudo se usan los métodos de ensamblaje cerca del final de un proyecto, para combinarlos y formar un predictor aún mejor.
