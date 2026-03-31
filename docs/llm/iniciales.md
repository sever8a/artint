# Ingeniería de características

Se basan en el trabajo generado por especialistas, construyendo sistemáticamente todas las reglas para el modelo.

No considera situaciones fuera de las programadas.

## Bolsas de palabras (Bag of Words)

Los primeros modelos (como Naive Bayes o SVM) trataban el texto como un conjunto de frecuencias. Si la palabra "oferta" aparecía mucho, el correo era clasificado como "Spam".

El principal problema era que se perdía el orden de las palabras. "El perro mordió al hombre" y "El hombre mordió al perro" eran representados de la misma forma, sin capturar diferencias semánticas cruciales.

### Feature Engineering manual

Los ingenieros pasaban meses diseñando "características": diccionarios de sinónimos, analizadores sintácticos y reglas de lematización. El éxito dependía más del lingüista que del algoritmo.


## La revolución de los embeddings

Las palabras se tratan como vectores numéricos.

Se construye un mapa de distancias de palabras y expresiones. Este mapa vectorial sirve para ver las relaciones entre las palabras.

Es posible realizar operaciones con estos vectores, que tienen sentido.

Establece el contexto de la frase.

!!! info "Problema"

    Depende del contexto y el significado de varias palabras que tienen diferente significado. También depende del contexto, el significado real.

### Word2Vec y GloVe

En 2013, Google publicó **Word2Vec**, un avance fundamental que permitió a las máquinas aprender relaciones semánticas como "Rey - Hombre + Mujer = Reina".

**Significado por cercanía**: Las palabras con significados similares se agrupaban en un espacio multidimensional, permitiendo operaciones algebraicas sobre vectores de palabras.

**Limitación crítica**: Los embeddings eran estáticos. La palabra "banco" tenía el mismo vector independientemente de si se refería a una entidad financiera o a un mueble para sentarse. El contexto seguía siendo el gran enemigo, ya que no se capturaban los múltiples significados de una palabra según su uso.


## La Era de las redes recurrentes (RNN y LSTM)

Para solucionar el problema del orden y el contexto, aparecieron las Redes Neuronales Recurrentes (RNN).

### RNN

La idea era procesar el texto palabra por palabra, manteniendo una **"memoria" de lo anterior**.

El problema era que las RNN tenían memoria a corto plazo. Al llegar al final de una frase larga, olvidaban cómo había empezado (el problema del gradiente desvaneciente).

### LSTM

Las LSTM (Long Short-Term Memory) mejoraron esto, ampliando la capacidad de memoria. Sin embargo, eran extremadamente lentas porque no podían procesar en paralelo; había que esperar a la palabra anterior para procesar la siguiente.


### Big Bang del NLP: Transformer

Surge en 2017. Es totalmente diferente porque incorpora un **mecanismo de atención**.

El idioma no es lineal, hay que conocer todo el contexto a la vez para dar una respuesta correcta.

Requiere mucho coste de GPU.


!!! info "Mecanismo de atención"

    En lugar de interpretar el texto de manera secuencial, se realiza en paralelo. Mira todo a la vez, estableciendo relaciones entre palabras, para decidir qué palabras son importantes para otras.

*OpenAI* toma la iniciativa, entrena modelos.

El entranamiento se realiza sin datos etiquetados. Tan solo obtiene patrones de frecuencia entre las relaciones con diferentes palabras.

## Pre-entrenamiento y transfer learning

A partir de 2018, la tendencia cambió a entrenar modelos gigantes de forma genérica y luego ajustarlos para tareas en específico.


## BERT y GPT: La especialización de modelos

**BERT (Google)** es un especialista en entender. Se enfoca en clasificación de texto y extracción de información. Aunque revolucionario, no fue optimizado para generación de texto.

**GPT (OpenAI)** es un especialista en generar. Su arquitectura se basa en completar texto, prediciendo secuencialmente las siguientes palabras según lo ya generado.

### Capacidades emergentes

Al escalar estos modelos a miles de millones de parámetros, aparecieron capacidades inesperadas: razonamiento lógico, programación y traducción, sin haber sido entrenados específicamente para ello.


!!! alert "Descubrimiento"

    Se descubren capacidades no esperadas "programar", "razonamiento".

## La era actual - LLMs

Son modelos reentrenados con feedback humano. Destaca **Gemma2**.

Los modelos actuales no solo predicen la siguiente palabra; han sido "alineados" mediante **SFT** (Supervised Fine-Tuning) y **RLHF** (Reinforcement Learning from Human Feedback) para actuar como **asistentes**.


Hoy en día no nos conformamos con que el modelo *hable*. Se exige:

- **Fiabilidad**, que no invente (evitar alucinaciones).
- **Actualización**, límite en las fuentes externas (*RAG*). Búsqueda en Internet. El modelo también se limita a las fuentes del contexto. Hay que decir al modelo que no responda.
- **Acciones**, los modelos se especializan en tareas más específicas. Ejecutan herramientas (Tools / Function Calling).
- **Autonomía**, uso de agentes sin flujos definidos. La IA decide cuando usar las herrameintas de manera autónoma. Que razone pasos complejos.

!!! info "Herramientas de acción"

    Basada en una orquestación de modelos de IA, ya creados, pero creando un nuevo programa completo de todo el flujo del problema que queremos solucionar.

    Los modelos especialistas se combinan.

    El caso *MEGA*.