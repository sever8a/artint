# Ingeniería de características

Se basan en el trabajo generado por especialistas, construyendo sistemáticamente todas las reglas para el modelo.

No considera situaciones fuera de las programadas.

## La revolución de los embeddings

Las palabras se tratan como vectores numéricos.

Se construye un mapa de distancias de palabras y expresiones. Este mapa vectorial sirve para ver las relaciones entre las palabras.

Es posible realizar operaciones con estos vectores, que tienen sentido.

Establece el contexto de la frase.

!!! info "Problema"

    De pende del contexto y el significado de varias palabras que tienen diferente significado. También depende del contexto, el significado real.

## La Era de las redes recurrentes (RNN y LSTM)

Solucionan el problema del orden y contexto, aparecieron las Redes Neuronales Recurrentes.

### RNN

Mantienen **memoria** de lo anterior.

Pero la memoria queda a corto plazo.

### LSTM

Modelos que amplian la capacidad de memoria, pero no lográn mejorar los resultados.

### Big Bang del NLP: Transformer

Surge en 2017. Es totalmente diferente porque incorpora un **mecanismo de atención**.

El idioma no es lineal, hay que conocer todo el contexto a la vez para dar una respuesta correcta.

Requiere mucho coste de GPU.


!!! info "Mecanismo de atención"

    En lugar de interpretar el texto de manera secuencial, se realiza en paralelo. Mira todo a la vez, estableciendo relaciones entre palabras, para decidir qué palabras son importantes para otras.

*OpenAI* toma la iniciativa, entrena modelos.

El entranamiento se realiza sin datos etiquetados. Tan solo obtiene patrones de frecuencia entre las relaciones con diferentes palabras.

## Pre-entrenamiento y transfer learning

**BERT (Google)** Especialista en entender (clasificación de texto, extracción de información). No se desplegó completamente. Clasifica texto y extrae información. No era bueno para generación de texto.

**GPT** Especialista para generar texto. Se basa en completar el texto. En función de lo que ya está predicho, genera las siguientes palabras.

!!! alert "Descubrimeinto"

    Se descubren capacidades no esperadas "programar", "razonamiento".

## La era actual - LLMs

Son modelos reentrenados con feedback humano. Destaca **Gemma2**.

Hoy en día no nos conformamos con que el modelo *hable*. Se exige:

- **Fiabilidad**, que no invente (evitar alucinaciones).
- **Actualización**, límite en las fuentes externas (*RAG*). Búsqueda en Internet. El modelo también se limita a las fuentes del contexto. Hay que decir al modelo que no responda.
- **Acciones**, los modelos se especializan en tareas más específicas. Ejecutan herramientas (Tools / Function Calling).
- **Autonomía**, uso de agentes sin flujos definidos. La IA decide cuando usar las herrameintas de manera autónoma.

!!! info "Herramientas de acción"

    Basada en una orquestación de modelos de IA, ya creados, pero creando un nuevo programa completo de todo el flujo del problema que queremos solucionar.

    Los modelos especialistas se combinan.

    El caso *MEGA*.