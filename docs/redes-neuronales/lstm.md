--- 
title: Redes Neuronales LSTM GRU
summary: Redes neuronales LSTM y GRU (Gated Recurrent Unit).
authors:
    - Reproducción autorizada
    - Jose Robledano
date: 2026-02-12
---
# Redes Neuronales Convolucionales (CNN)
## Concepto
Un tipo de red neuronal profunda, especializada en procesar datos con estructura de matríz (cuadrídula). Por ejemplo: imágenes. a red neuronal artificial (RNA).

Se utilizan para visión por computador, procesamiento de imágenes y vídeo, y reconocimiento de patrones espaciales.

## Diferencia con las redes densas

Conservan la relación con los pixeles vecinos, las redes densas no tienen ninguna referencia.

Comparten pesos, convolución.

Invariantes a pequeñas transformaciones.

!!! info "Convolución"

    En una red neuronal convolucional, una convolución es una operación matemática que toma una pequeña ventana de valores (llamada filtro o kernel) y la desliza sobre los datos de entrada para extraer patrones locales, como bordes, texturas o formas.  

    En cada posición, el filtro multiplica sus valores por los de la región correspondiente de la entrada y suma el resultado, produciendo un único número. Al repetir esto en todas las posiciones, se genera un mapa de características que resalta dónde aparece ese patrón en la imagen.


Warren McCulloch y Walter Pitts describieron en 1943 una célula nerviosa de este tipo como una simple puerta lógica con salidas binarias; a las dentritas llegan múltiples señales, que se integran en el cuerpo celular y, si la señal acumulada supera un determinado umbral, se genera una señal de salida que será transmitida por el axón.

!!! alert "Neuronas sintéticas"

    Este modelo permitía ser aplicado a una neurona artificial. 
    McCulloch y Pitts demostraron que incluso con un modelo simplificado es posible construir una red de neuronas artificiales que pueda calcular cualquier proposición lógica. 
    
    En el contexto del *aprendizaje supervisado* y de la clasificación, se podría utilizar para pronosticar si un nuevo punto de datos pertenece a una clase o a otra (dependiendo si se activa o no una neurona).

## Componentes principales

* **Capa de entrada**. Representada como un tensor (alto, ancho, canales). Ej. 32 x 32 x 3 (RGB).
* **Capa convolucional**. 
    - Filtros **kernels** pequeñas matrices (ej. 3x3) que se deslizan sobre la imagen.
    - **Operacion** producto escalar entre el *kernel* y una región de la imagen.
    - **Mapa de características** resultado de aplicar el filtro.
    - **Parámetros**:
        * Tamaño del filtro.
        * Stride (paso).
        * Padding (relleno).
    - **Activación** normalmente RELU (Rectified Linear Unit) para introducir no linealidad.
* **Capa de agrupación**. Reduce la dimensionalidad espacial. Mantiene las características importantes. Ejemplos: **MaxPooling**, **AveragePooling**.
* **Capas completamente conectadas**. Antes de utilizar la primera capa hay que realizar un aplanamiento (flatten) para convertir los mapas de características 2D en un vector 1D.
* **Capa de salida**. Es la última capa completamente conectada antes de la salida. Su número de neuronas es igual al número de clases del problema.
    - **Clasificación binaria**: 1 neurona con **Sigmoide** (probabilidad entre 0 y 1).
    - **Clasificación multiclase**: N neuronas con **Softmax** (probabilidades que suman 1).
    - **Regresión**: 1 neurona (o varias) sin activación lineal.

