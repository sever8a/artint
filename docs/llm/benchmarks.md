# Benchmarks

Surge a partir de 2018 por la inquietud de los usuarios por saber cual funcionaba mejor.

Utilizamos otro modelo para evaluar el resultado (también se puede usar el mismo modelo).

Las métricas clásicas ya no sirven. Las metricas basadas en solape de palabras presentan limitaciones críticas con LLMs.

Llega un momento que las métricas no mejoran, con los nuevos modelos. De esta manera los benchmarks más pretigionsos, se utilizaron como referencia para conseguir el mejor resultado.

* **No miden la veracidad**, una respuesta puede tener las palabras esperadas, pero por ejemplo agregar un "no" cambia completamente el sentido.
* **No miden la semátnica**, Expresiones equivalentes no se consideran solapadas. El solape requiere una semejanza.
* **No evalúan el razonamiento**

## Dimensiones de evaluación en sistemas RAG y Agentes

**Fidelidad (faithfulness)**

**Relevancia de la respuesta**

**Precisión de la recuparación**, si estamos obteniendo los chunks más apropiados.

## LLM como juez: El modelo como evaluador

**Rúbricas claras**, Hay que diseñar rúbricas de evaluación evaluativas, para que se pueda evaluar una respuesta, deben ser detalladas.

**Justificación obligatoria**, debe explicar el razonamiento.

**Formato estructurado**

### Problemas

- **Sesgo de posición** Puntua mejor la primera respuesta que analiza.
- **Sesgo de longitud** favorecer respuestas más largas, aunque no sean mejores. 
- **Sesgo de Auto-preferencia** Modelos de la misma familia tienden a evaluarse mejor entre sí.
- **Mitigación**

### El contrato de salida: Etiquetas de control

Hay que interpretar si el modelo pone mal la salida.

### Construcción de un banco de pruebas.

Un **benchmark** es un conjunto estructurado de pregutnas de referencia, que reflejan.

Un agente, a diferencia de un chatbot tradicional, toma decisiones intermedias y no solo generar texto.

Es crucial hay que ver como *actua* a la vez que cómo responde.



