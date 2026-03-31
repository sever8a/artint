# Entrenamiento y selección de modelos

## Comparación de algoritmos

Se han desarrollado numerosos algoritmos de aprendizaje automático para resolver problemas diversos. Cada algoritmo de clasificación posee sesgos inherentes, y ningún modelo goza de superioridad universal sin asumir características específicas de la tarea. Por tanto, es esencial:

- Comparar varios algoritmos de aprendizaje diferentes
- Entrenar cada uno de ellos
- Seleccionar el modelo con mejor desempeño

### Métricas de rendimiento

Para comparar modelos necesitamos establecer una métrica. La **precisión de clasificación** es una métrica común, definida como la proporción de instancias clasificadas correctamente.

## Validación cruzada

¿Cómo evaluamos el rendimiento real sin comprometer nuestro conjunto de prueba final?

La validación cruzada responde esta pregunta dividiendo el conjunto de datos en subconjuntos de entrenamiento y validación para estimar el rendimiento de generalización del modelo. Esta técnica permite evaluar el modelo sin utilizar los datos de prueba en la selección.

## Optimización de hiperparámetros

Los parámetros por defecto de los algoritmos raramente son óptimos para cada problema específico. Es necesario aplicar técnicas de optimización de hiperparámetros para ajustar el rendimiento.

Los **hiperparámetros** son parámetros no deducidos de los datos, sino variables controlables del modelo que permiten mejorar su desempeño.
