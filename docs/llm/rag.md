 # RAG

 El modelo responde con las fuentes indicadas.

 **Memoria Paramétrica** Corresponde a todo lo que lmodelo aprendió durante el pre-entrenamiento. Está codificada en los pesos de la red neuranal, lo que significa que es estática. Solo dispone de información hasta esa fecha

 **Memoria no paramátrica**

 ## Ventajas RAG

 **Actualización inmediata** La legislación, normativa o datos que puedan cambiar. No hace falta reentrenar el modelo.

 **Trazabilidad** Com la respuesta se genra a partir de fuentes concretas, se pueden citar referencias precisas.

 **Reducción de alucinaciones** Al forzar el modelo a basarse en un contexto externo validado, se minimizan la generanción de información inventada.

 !!! info "RAG y sistemas híbridos"

    El RAG convierte un modelo LLM en un sistema híbrido. Mantiene fluidez y creatividad de los LLMs, pero con la capacidad de acceder a información externa actualizada, confiable y trazable, superando los límites de la memoria paramétrica tradicional.


## Pipeline de ingesta: preparación del conocimiento

Los datos deben prepararse cuidadosamente. La efectivdad del modelo depende de esto. Se trata de transformar información bruta en un formato que el modelo pueda comprender y consultar de forma eficiente.

**Fixed-size chunking** Fragmenta el texto cada Xcaracteres o palabras. Es rápido, pero puede cortar frases o ideas a la mitad. Ni grandes ni pequeños, para no perder el contexto.

**Recursive Character Chunking** Divide primero por párrafos.

**Solape**

Embeddings, representación semántica.

Cada vector se compara con los existentes. Utlizando una función de similitud (sene).

!!! info "Información válida"

    Hay expresiones y textos que son propias del contexto del usuario, que se aporta de manera accesoria a los datos relevantes.


Al elegir las similitudes hay que observar las similitudes, y posteriormente coger todos los relevantes. Esta lógica de elección se programa a mano, es clave para el resultado, elegir bien los **chumks**.

Pipeline de recuperacxión

Agrupar los vectores en clusters, de esta manera primera se eleige el cluster y luego el vector. Se agiliza la respuesta.

Pripeline de Generación

Tenemos la pregunta del usuario, y los chunks de la pregunta del usuario. Responder a esta pregunta de usuario basadao en el contexto dado. "Si no está en las fuentes, que no responda".

!!! info "Chunks muy grandes"

    La ventana de contexto, se pierde. Hay que pasar


Documento --> Texto plano --> Segmentación (chunks)

### Fallos posibles

**Fallo de recuperación** al comparar toda la frase con un vector, aparecen muchos chunks que no son claves, y pueden salir resultados genéricos, basados en expresiones genéricas.

!!! alert "Modelo previo"

    Crear un modelo con un modelo, para ajustar la pregunta. Transformar la pregunta en otro texto.

    Hay que preparar un prompt para que expanda la consulta inicial, a un nuevo prompt donde se distinga e identifique mejor el contexto de la pregunta.

Pregunta --> Modelo LLM --> Pregunta expandida


**Fallo en la generación** al seleccionar muchos chunks, y se genera un texto demasiado grande para qu eel modelo lo pueda analizar bien. Hay que bajar el contexto. 

Una opción es redimensonar el tamaño del chunk, para que se ajuste el tamaño.

**Lost in the Middle** Los LLMs tienden a prestar más atención al inicio y final del contexto, perdiendo detalles situados en los fragmentos intermedios.

Dividir en problemas más pequeños.


### Técnicas de mejora

**QueryExpansion**. Obtener el resultado que corresponde a la pregunta, sin tener 

**Re-ranking** Se recupera en un primer modelo y luego en otro más específico.

**Hybrid Search** Busca palabras para dar más peso a los tengan cierta palabra en específica.
