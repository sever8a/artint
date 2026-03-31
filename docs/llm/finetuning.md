# Paradigma de Ajuste Fino (Fine-tuning)

 El entrenamiento de un LLm no es un proceso único, sino una escalera de refinamiento. Para entender el (Supervised Fine-Tuning), primero debemos ubicarlo en el **cilo de vida del modelo**.

 1. **Pre-training (Pre-entrenamiento)**, El modelo aprende a predecir el siguiente token a partir de una cantidad masiva de datos. Aquí adquiere "conocimiento del mundo" y gramática, pero no sabe seguir instrucciones. Es un completador de frases.

 2. **SFT (Supervised Fine-Tuning)**, Es el proceso de entrenaar al modelo en un dataset más pequeño y *curado* de pares Instrucción -> Respuesta. Aquí es donde el modelo aprende el formato de chat y a obedecer órdenes.

 Utilizando el *modelo en bruto* (que solo lo tienen las empresas que lo desarrollan), puede quedar manipulado e inoperativos, ya que si se alteran la ética del modelo, diseñada por el creador.

 Solo se modifican las capas lineales. Pierde conocimiento si tocas otras capas.


!!! alert "Nuevo dataset"

    Se compone de ejemplos que se aportan al modelo. Se tienen que aportar casos nuevos orientados al problema que queremos resolver.

    Se genera de manera guiada. Una posibilidad es crear los ejemplos con otra IA más grande.

Aplica **restricciones de comportamiento**, hay que enseñar al modelo a decir "no lo se".

El modelo aprende el lenguaje de manera intrinseca, pero se pueden aportar ejemplos sobre un contexto determinado. Especificando un **dominio del lenguaje**, estableciendo siempre el formato de las respuestas.

La **Estructura y el formato** es importante cuando se utiliza *function calling* ya que suele ser la entrada de otro proceso, y debe ser bien interpretada por la siguiente herramienta.



 3. **Alignment (Alineación - RLFH/DPO)**, SE ajusta el modelo para que sus respuestas sean seguras, útiles y honestas, basandose en preferencias humanas.

!!! info "Entrenamiento por refuerzo humano"

    Cada cierto tiempo se recogen opiniones de los usuarios sobre la elección de la mejor respuesta.

    Revisión de respuestas, para realimentar con las mejores respuestas.

## PEFT: parameter-Efficient Fine Tuning

Entrenar un modelo desde cero es igual de costoso que un fine-tuning completo del modelo.

Un modelo 9B 9.000 millones de parámetros requiere actualizar 9.000 millones de números en cada paso.

### LoRA (Low-Rank Adaptation)

No es necesario modificar todos los parámetros. Los ajustes importantes pueden representarse mediante matrices mucho más pequeñas y sencillas, ocupando un espacio reducido dentro de la red.

Es menos eficiente en su uso. Los valores de las matrices son aleatorios en una distribución normal.
### LoRA (Low-Rank Adaptation)

No es necesario modificar todos los parámetros. Los ajustes importantes pueden representarse mediante matrices mucho más pequeñas y sencillas, ocupando un espacio reducido dentro de la red.

#### Cómo funciona

En lugar de modificar la matriz de pesos original W, que es enorme, LoRA la congela y añade dos matrices pequeñas, A y B, que sí se entrenan. La actualización final del modelo se calcula como:

$$W_{final} = W + (A \times B)$$

Esto significa que solo entrenamos un pequeño subconjunto de parámetros, manteniendo intacta la base del modelo.

#### Ventajas de LoRA

- Reduce hasta un 99% los parámetros que se deben entrenar.
- Disminuye drásticamente el consumo de memoria durante el entrenamiento.
- Los adaptadores resultantes son muy ligeros, lo que facilita su almacenamiento y distribución.

Es menos eficiente en su uso. Los valores de las matrices son aleatorios en una distribución normal.

### QLoRA Cuantización + LoRA

Más eficiente, combina la cuantización con LoRA y otras optimizaciones de memoria. 

* Comprime los pesos del modelo, reduciendo la precisión. Convierte los valores de los parámetros, por ejemplo de float 32 a float 16. Esto supone que pierde capacidades, aunque puede mantener la eficiencia. De esta manera se reduce el tamaño.

* **Normal Float** Comprime los pesos del modelo original a solo 4bits, perdiendo cierta precisión.

* **Paged Optimizers** Gestiona los picos de memoria usando la RAM del sistema cuando la VRAM se llena, evita errores "sin memoria".
#### QLoRA: Cuantización + LoRA

QLoRA lleva la eficiencia aún más lejos, combinando cuantización con LoRA y otras optimizaciones de memoria:

* **4-bit NormalFloat (NF4)** Comprime los pesos del modelo original a solo 4 bits, manteniendo casi toda la precisión sin perder capacidades significativas.

* **Double Quantization** Comprime también las constantes de cuantización, reduciendo aún más el tamaño (float32 a float16).

* **Paged Optimizers** Gestiona los picos de memoria usando la RAM del sistema cuando la VRAM se llena, evitando errores de "Out of Memory".

!!! alert "Resultado"

    Se pueden entrenar modelos de 9B (o incluso 13B) en una sola GPU (RTX 3090 4090).

    Haciendo que el fine-tuning avanzado sea accesible para laboratorios pequeños y desarrolladores individuales.

### Dudas que surgen

Qué es mejor tener modelos con precisión más baja, o modelos.

Al escalar los parámetros aumenta la complejidad, ya que aunque disminuye por la precisión, aumenta por los parámetros.

## Hiperparámetros críticos en el entrenamiento

Los ajustes de estos parámetros puede afectar a un rendimiento más grande.

**Rank (r)** Determina el **tamaño de las matrices A y B en LoRA**. Valores típicos: 8, 16 o 32. Permite que el modelo capture patrones más complejos, pero también aumenta el consume de memoria y tiempo de entrenamiento.

**LoRA Alpha ($ a $)** Normalmente se fija en el doble de Rank. Controla la intensidad de las actualizaciones sin desdeabilizar el modelo.

**Learning Rate**, velocidad a la que el modelo ajusta sus parámetro. Valor bajo, para que aprenda lento. Si es muy alto, el modelo puede olvidar conocimientos previos. Ejemplo $ 2 x 10 -4 $. 

Se establece en función del tamaño del dataset. Si es más grande se puede aumentar.

!!! info "Modelo catastrófico"

    Se genera cuando el valor de *learning rate" no es adecuado, ya que el modelo pierde su conocimiento previo.

**Epoch (Epocas)**, En SFT con 1-3 épocas suele ser suficiente.


!!! alert "Valores recomendados"

    Es aconsejable aplicar los valores por defecto.

    Los valores son con pruebas, ya que no se conocen las relaciones internas.


Lo más aconsejable es poder realizar varios entrenamientos para conseguir un **grid** y elegir el más adecuado.
    

!!! info "Diferencia con Redes neuronales"

    No hay posibilidad de detectar cual es el resultado del entrenamiento.

    La solución es disponer de un **Benchmark**, donde otra Inteligencia Artificial se encarga de evaluar el resultado.


## Evaluación del entrenamiento

Curva *Train/ Eval Loss* si la curva de pérdida sube y la curva del entrenamiento baja, indica **overfitting**.

Evitar el **Catastrophic Forgetting** Es crucial para comprobar que el modelo no ha perdido sus habilidades básicas. 

**Benchmark Cualitativo**, compara respuestas del modelo base y del modelo fine-tuneado ante preguntas diseñadas para evaluar *comprensión*, *coherencia* y *exactitud*. 
