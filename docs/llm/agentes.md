# Agentes

En desarrollo. Utiliza herramientas.

## Cadena de pensamiento

Un mismo modelo utiliza la respuesta de salida como entrada para realimentar la respuesta.

Utiliza la herramienta de buscar en Internet.

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

