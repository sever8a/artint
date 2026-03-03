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
Una red neuronal artificial (RNA) imita el comportamiento de las neuronas biológicas. Las neuronas biológicas son células nerviosas del cerebro interconectadas que participan en el procesamiento y en la transmisión de señales químicas y eléctricas.

<figure style="align: center;">
    <img src="./images/neurona-biologica.png">
    <figcaption>Neurona biológica</figcaption>
</figure>

Warren McCulloch y Walter Pitts describieron en 1943 una célula nerviosa de este tipo como una simple puerta lógica con salidas binarias; a las dentritas llegan múltiples señales, que se integran en el cuerpo celular y, si la señal acumulada supera un determinado umbral, se genera una señal de salida que será transmitida por el axón.

!!! alert "Neuronas sintéticas"
    Este modelo permitía ser aplicado a una neurona artificial. 
    McCulloch y Pitts demostraron que incluso con un modelo simplificado es posible construir una red de neuronas artificiales que pueda calcular cualquier proposición lógica. 
    
    En el contexto del *aprendizaje supervisado* y de la clasificación, se podría utilizar para pronosticar si un nuevo punto de datos pertenece a una clase o a otra (dependiendo si se activa o no una neurona).

### Tarea reflexión

¿Qué aplicaciones de IA conoces, que probablemente utilicen redes neuronales?

## Elementos Red neuronal

Las neuronas almacenan un número. Cada neurona se multiplica por el peso del vector de conexión, para obtener el resultado de la siguiente neuronal.

Finalmente se aplica una función de activación, para obtener el valor de la neurona.

### Capa entrada

Las variables independientes se representan con un vector. Cada elemento sdle vector es una neurona de entrada.

### Capas ocultas y conexiones entre neuronas

Cada neurona en la capa oculta recibe señales de toas las neuronas de la capa anterior **feedforward** y de todas las neuronas de su misma capa en el paso de tiempo anterior **recurrente**. La candiad de capas ocultas y neuronas determina la capacidad de modelar secuencias complejas.

!!! alert "Prueba error"

    No es posible establecer una configuración óptima. Hay que seguir un procedimiento de prueba error probando con diferentes estructuras de la red neuronal.

### Función de activación

Cada neurona oculta aplica una función de activiación a la suma ponderada de sus entradas.

### Capa de salida


