 # Function Calling

Utilizar los LLMs para toma de decisiones, acceder a sistemas externos y coordinar acciones.

 El LLM como orquestador, apoyado en **Tools** y **Function calling**.

 ## Tool

 Compenente externo al modelo que le permite intereacuar con el mundo real o cnsistmeas especializados. Puede ser una *búsqueda web*, una consulta a una base de datos *SQL*, un *script* de Python, una *llamada a una API* corporativa oincluso un sistema de *gestión de archivos*. 

 !!! alert "Punto clave"

    El modelo no ejecuta la lógica, sino que decide cuándo y cómo debe invocarse esa herramienta para obetner información fiable o realizar una acción concreta.


Supone un cambio profundo en el rol del modelo. En lugar de responder a todo usando unicamente su conocimiento interno, el LLM actúa como un sistema de control inteligente que evalúa cada situación antes de actuar.

Flujo

- **Analizar la intención** del usuario, entendiendo si setrata de una pregunta, una acción o una consulta técnica.
- **Evaluar si dispone de la información** necesaria en su contexto o memoria paramétirica.
- **Seleccionar la herramienta** adecuada cuando detecta que necesita datos externos o capacidades que no posee.
- **Formatear la petición** de forma estructurada y precisa para que la herramienta pueda ejecutarse sin ambigüedades.

!!! info "Nuevo valor"

    El valor del LLM no reside solo enlo que *"sabe"*, sino en su capacidad para **coordinar recursos**, combinar resultados y devolver una respuesta final coherente, verificable y alineada con los sistemas.

## Mecánica del Function Calling

Ejemplo router de convenios laborales

Uso de **description.json**

Salidas Estructuradas y validación por Regex

Se consigue al indicar al modelo, indicando el prompt las limitaciones. Ayuda poner la salida con un formato JSON. De esta manera mantiene mejor el esquema de la respuesta.

- **Validación del esquema**, si la salida esperada, debe comprobarse que sea sintácticamente válido y que incluya todos los campos obligatorios con los tipos correctos. 

Cualquier desviación de be provocar fallo explícito, no una ejemcución parcial.

!!! alert "Propósito"

    El conjunto convierte el proceso, en una acción determinista.


El modelo se controla con **system prompt**. Hay que realizar la pregunta completa (si no se dispone de esta posibilidad).

Hay que establecer criterios de abstención.

Se tiene que definir reglas claras. El router actua como un filtro de preguntas correctas.

Que no tenga sobre confianza y las respuestas no responda a otros requerimientos
