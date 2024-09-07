# Fase de diseño
En la fase de diseño, nos centramos en el diseño del proyecto de aprendizaje automático. Definimos el contexto del problema y determinamos el valor añadido del uso del aprendizaje automático. También recopilamos requisitos comerciales y establecemos métricas clave a través de las cuales podemos rastrear el progreso del ciclo de vida del aprendizaje automático. Además, necesitamos recopilar datos y asegurarnos de que la calidad de los datos sea suficiente para desarrollar un modelo de aprendizaje automático.

## Valor añadido
Normalmente, el ciclo de vida del aprendizaje automático comienza con la determinación del valor agregado de crear y ejecutar el modelo de aprendizaje automático. Esto suele expresarse en términos de dinero o tiempo. Determinar el valor de un modelo de aprendizaje automático puede ser un poco aproximado, pero es aconsejable estimar el potencial que tiene un determinado proyecto.

Por ejemplo, podemos tener un modelo de aprendizaje automático que prediga si un cliente se va a dar de baja de nuestro servicio. Tenemos un total de 100000 clientes con una suscripción de 10€ al mes. Si podemos predecir el 80% de los 1000 clientes que usualmente se dan de baja, podemos enviarles un descuento de la suscripción, el cual hace que un 50% de estos clientes finalmente no se den de baja. Esto da como resultado 1000 clientes multiplicados por ochenta por ciento multiplicados por cincuenta por ciento, es decir, 400 clientes que no abandonan. Si les damos a estos 400 clientes una suscripción con descuento de 8€, podemos ahorrar un total de 3200€ por mes.

## Requirimientos de negocio
Aparte del valor añadido del modelo de aprendizaje automático, también debemos considerar los requisitos del negocio. Especialmente en la fase de diseño, es fundamental pensar en el usuario final del modelo de aprendizaje automático. 

Digamos que estamos construyendo un modelo de aprendizaje automático que predice el número de ventas de un producto específico, de modo que podamos comprar la cantidad correcta para poner en nuestra tienda. El modelo de aprendizaje automático generará una cantidad prevista de ventas. Debemos considerar la frecuencia de las predicciones y qué tan rápido las necesitamos. También debemos evaluar la precisión del modelo y si sus resultados son explicables para los no expertos. 

Asimismo, la transparencia se está convirtiendo en un factor cada vez más importante en el desarrollo del aprendizaje automático, ya que nos permite descubrir por qué el modelo hace sus predicciones, por qué está equivocado y cómo podemos mejorar el modelo. Todos estos requisitos tienen un impacto en el algoritmo que usaremos. Dependiendo del problema que estemos tratando de resolver, también podrían existir requisitos legales y de cumplimiento para el uso del aprendizaje automático. Por ejemplo, en finanzas, cuando la ley exige una explicación por parte del sistema.

Por último, también debemos tener en cuenta el presupuesto disponible y el tamaño del equipo.

## Métricas principales
Para ver si el ciclo de vida del aprendizaje automático avanza según lo esperado, suele ser aconsejable realizar un seguimiento del rendimiento del modelo. Sin embargo, hay distintos roles involucrados en los procesos MLOps y, por lo tanto, cada uno también tiene su propia forma de rastrear el desempeño. 

* Un científico de datos analiza la precisión de un modelo, cuántas veces el algoritmo es correcto.
* Un experto en la materia está interesado en el impacto del modelo en el negocio, por ejemplo, en cómo mejora su trabajo gracias al uso del aprendizaje automático. Están interesados principalmente en métricas específicas dentro de la materia.
* Un cargo empresarial estará más interesado en el valor monetario del modelo, en cuántos casos realmente generamos ingresos. Esto suele expresarse en dinero o tiempo. 

Para aprovechar al máximo el aprendizaje automático, debemos alinear las diferentes métricas para asegurarnos de que todos estén en la misma página.

## Preprocesamiento de datos
Durante esta fase, investigamos la calidad de los datos y cómo extraemos los datos requeridos.

### Calidad de los datos
El término **calidad de los datos** se refiere tanto a las características asociadas con datos de alta calidad como a los procesos utilizados para medir o mejorar la calidad de los datos. La calidad de un modelo de aprendizaje automático depende en gran medida de la calidad de los datos. Los datos son el núcleo del modelo de aprendizaje automático. Por lo tanto, tener una visión clara de la calidad de los datos es crucial para el éxito del ciclo de vida del aprendizaje automático. Tener una mala calidad de los datos es perjudicial para el rendimiento del modelo de aprendizaje automático. Mejorar la calidad de los datos suele ser el primer paso para mejorar el rendimiento del modelo. La calidad de los datos puede definirse en base a cuatro características:

* **Exactidud**: describe el grado en que los datos son exactos o correctos para la tarea en cuestión.
* **Completitud**: trata de hasta qué punto los datos describen completamente el problema en cuestión.
* **Consistencia**: trata sobre si los datos tienen distintos significados dentro de un mismo sistema informático.
* **Disponibilidad**: trata de en qué plazo los datos estarán disponibles.

### Extracción y procesamiento de datos
En esta fase también analizamos cómo **extraer y procesar datos**. Esto se hace mediante el uso de un canal de datos automatizado (*data pipeline*). Una canalización de datos suele ser una parte del ciclo de vida del aprendizaje automático a través del cual los datos se procesan automáticamente. Un tipo común de proceso de ingesta de datos es **ETL** (*extract, transform and load*). Los datos se extraen de la fuente, se transforman al formato requerido y se cargan en alguna base de datos interna o propietaria. En un proceso ETL, también podemos incluir verificaciones automatizadas, como las expectativas que tenemos sobre ciertas columnas de datos. Por ejemplo, esperamos que la columna de temperatura siempre contenga un número. Incluir estas comprobaciones automatizadas en un proceso de datos ayuda a acelerar la fase de desarrollo e implementación del ciclo de vida, ya que los datos defectuosos o de baja calidad afectarán el modelo de aprendizaje automático.