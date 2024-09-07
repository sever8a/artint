# Redes neuronales multicapa de regresión
Una RNM puede utilizar para tareas de regresión. Si se quiere predecir un solo valor (por ejemplo, el precio de una casa, dadas muchas de sus características), solo se necesita una neurona de salida: la salida es el valor predicho. Para la regresión multivariable (es decir, para predecir varios valores al mismo tiempo), se necesita una neurona de salida por dimensión de salida. Por ejemplo, para ubicar el centro de un objeto en una imagen, se necesita predecir coordenadas 2D, así que se necesita dos neuronas de salida.

La capa de salida puede no utilizar función de activación, lo que la haría libre de generar cualquier valor que quiera. Por lo general, esto está bien, pero si se quiere garantizar que la salida se siempre positiva, se deberá utilzar la función de activación ReLU o **Softplus** (variante suave de ReLU). Por último si se quiere garantizar que las predicciones queden siempre dentro de un rango de valores determinado, se deberá utilizar la función sigmoide (0 a 1) o la tanh (-1 a 1).

La función de pérdida suele ser el error cuadrático medio (MSE), aunque si se tiene muchos valores atípicos se suele utilizar la función de pérdida **Huber**, la cual es una combinación entre el error cuadrático medio y el error absoluto medio (MAE).

La siguiente tabla resume la arquitectura típica de una RNM de regresión.

| Hiperparámetro | Valor típico |
| -------------- | ------------ |
| Nº de capas ocultas | Depende del problema, pero normalmente entre 1 5 |
| Nº de neuronas por capa oculta | Depende del problema, pero normalmente entre 10 y 100 |
| Nº de neuronas de salida | 1 por dimensión de predicción |
| Función de activación oculta | ReLU |
| Función de activación de salida | Ninguna, o ReLU/Softplus (para salidas positivas) o sigmoide/tanh (para salidas limitadas) |
| Función de pérdida | MSE o Huber (si hay valores atípicos) |



