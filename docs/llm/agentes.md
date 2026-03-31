# Agentes

Un agente es un sistema de inteligencia artificial que utiliza un modelo de lenguaje para realizar tareas específicas, como responder preguntas, generar contenido o tomar decisiones.

## Cadena de pensamiento

Un mismo modelo utiliza la respuesta de salida como entrada para realimentar la respuesta.

Por ejemplo, un modelo de lenguaje puede generar una pregunta a partir de una pregunta inicial, y luego responder a esa pregunta generada.

Un agente puede tener varios pasos en su cadena de pensamiento, y cada paso puede ser realizado por un modelo diferente.

## Recuperación de información

Los agentes pueden recuperar información de diversas fuentes, como bases de datos, documentos o la web. Esta capacidad es fundamental para proporcionar respuestas precisas y contextualizadas.

### Técnicas de recuperación

**Retrieval Augmented Generation (RAG)** es un enfoque clave que combina la generación de texto con la recuperación de información relevante. El proceso funciona en dos fases:

1. **Búsqueda**: El agente identifica y recupera documentos o fragmentos pertinentes según la consulta.
2. **Generación**: El modelo utiliza esa información como contexto para generar respuestas más precisas y fundamentadas.

### Herramientas de acceso a información

Los agentes pueden utilizar diversas herramientas:

- Búsqueda en Internet para información actualizada
- Consultas a bases de datos estructuradas
- Indexación semántica de documentos locales
- APIs especializadas para dominios particulares

Esta integración de recuperación y generación mejora significativamente la calidad y fiabilidad de las respuestas.

## Arquitecturas de razonamiento

No está únicamente limitado a la investigación profunda.

**Repetición** mejora ostensiblemente el resultado de la herramienta.

Se puede verificar las respuestas por otro modelo.

Modelo de evaluación del resultado de otro modelo.

## Componentes críticos.

Por ejemplo, Claud no vuelve a generar el código, modifica el generado anteriormente.

## Buble de control y manejo de errores

Hay que establecer mecanísmos de control. Hay que incluir **salvaguardas explícitas** que limiten su comportamiento para evitar respuesta incorrectas o ciclos ineficientes.

El **límite de iteraciones** impide que el agente quede atrapado en bucles infinitos, por ejemplo repetir búsquedas sobre la misma fuente.

De esta manera se limita el coste computacional.

La **validación de salida** actúa como una última capa de seguridad antes de mostrar la respuesta al usuario. Puede consistir en reglas o scripts que detecten inconsistencias, afirmaciones prohibidas o respuestas excesivamente largas que, en realidad, no aportan información verificable.


## Razonamiento multi-fuente y síntesis

Lo importante de un agente NLP es sintetizar correctamente la información. Cuando intervienen múltiples convenios o documentos, no basta con concatener fragmentos de texto sin contexto.

Debe analizar posibles **contradicciones** y **sesgos**.

## Ética y responsabilidad

El usuario debe saber en qué se basan las respuestas. 

Por ejemplo, se puede abrir la cadena de razonamiento.

Realizar una auditoría.

La **abstención** es importante para que no se invente respuestas cuando no tiene una respuesta correcta.

