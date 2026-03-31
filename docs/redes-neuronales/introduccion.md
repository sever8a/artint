--- 
title: Redes Neuronales
summary: Fundamentos y evolución de las redes neuronales.
authors:
    - Reproducción autorizada
    - Jose Robledano
date: 2026-02-11
---
# Introducción a las redes neuronales artificiales

## Concepto de red neuronal artificial

Una red neuronal artificial (RNA) es un modelo computacional que imita el funcionamiento de las neuronas biológicas. Las neuronas biológicas son células nerviosas del cerebro interconectadas que procesan y transmiten señales químicas y eléctricas.

<figure style="align: center;">
    <img src="./images/neurona-biologica.png">
    <figcaption>Neurona biológica</figcaption>
</figure>

En 1943, Warren McCulloch y Walter Pitts modelaron una neurona biológica como una puerta lógica simple con salidas binarias. El modelo funciona así: múltiples señales llegan a las dendritas, se integran en el cuerpo celular y, si la suma supera un umbral específico, se genera una señal de salida transmitida por el axón.

!!! alert "Neuronas sintéticas"
    Este modelo se adaptó para crear neuronas artificiales. McCulloch y Pitts demostraron que, incluso con un modelo simplificado, es posible construir redes de neuronas artificiales capaces de calcular cualquier proposición lógica.
    
    En *aprendizaje supervisado* y clasificación, se pueden usar para predecir si un nuevo dato pertenece a una clase u otra según se active o no una neurona.

### Tarea de reflexión

¿Qué aplicaciones de IA conoces que probablemente utilicen redes neuronales?

## Elementos de una red neuronal

Una red neuronal procesa información en capas. Cada neurona almacena un valor que se multiplica por un peso de conexión y se transmite a la siguiente capa, aplicando una función de activación al resultado.

### Capa de entrada

Las variables independientes se representan en un vector. Cada elemento es una neurona de entrada que recibe los datos.

### Capas ocultas y conexiones entre neuronas

Cada neurona oculta recibe señales de todas las neuronas de la capa anterior (conexiones **feedforward**) y, en redes recurrentes, de su propia capa en el paso de tiempo anterior. El número de capas ocultas y neuronas determina la capacidad para modelar patrones complejos.

!!! alert "Configuración mediante prueba-error"
    No existe una configuración óptima predefinida. Debes probar diferentes arquitecturas de red neuronal para encontrar la que mejor se ajuste a tu problema.

### Función de activación

Cada neurona oculta aplica una función de activación a la suma ponderada de sus entradas. Esta función introduce no-linealidad, permitiendo que la red aprenda patrones más complejos.

### Capa de salida

La capa de salida produce el resultado final de la red según la tarea (regresión, clasificación, etc.).

## Ejemplo de arquitectura de una red neuronal

Consideremos un problema de clasificación: predecir si un cliente comprará un producto basándose en edad e ingresos.

**Paso 1: Capa de entrada**
- 2 neuronas de entrada: edad e ingresos del cliente

**Paso 2: Capas ocultas**
- 1ª capa oculta: 4 neuronas conectadas a las 2 neuronas de entrada
- 2ª capa oculta: 2 neuronas conectadas a las 4 neuronas anteriores

**Paso 3: Función de activación**
- Aplicamos ReLU en las capas ocultas para introducir no-linealidad

**Paso 4: Capa de salida**
- 1 neurona con función sigmoid (para clasificación binaria: compra/no compra)

Esta arquitectura (2 → 4 → 2 → 1) con conexiones feedforward permite que la red aprenda patrones no-lineales en los datos de entrada para realizar la predicción.

