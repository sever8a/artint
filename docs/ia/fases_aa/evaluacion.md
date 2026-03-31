# Evaluación de modelos y pronóstico de instancias de datos ocultos
## Flujo de trabajo

Después de ajustar un modelo con datos de entrenamiento, validamos su rendimiento en el conjunto de prueba para estimar el **error de generalización**. Si los resultados son satisfactorios, aplicamos el modelo a nuevos datos.

**Punto crítico**: Los parámetros de transformación (escalado, reducción dimensional, etc.) se extraen **solo** del conjunto de entrenamiento. Estos mismos parámetros se reutilizan en prueba y datos nuevos. 

⚠️ **Riesgo**: Recalcular parámetros en prueba → rendimiento artificialmente optimista y resultados no confiables.

## Estructura de conceptos clave

### 1. Conjunto de entrenamiento
- Ajusta los parámetros del modelo
- Define la transformación de características

### 2. Conjunto de prueba
- Evalúa el error de generalización
- Utiliza los mismos parámetros del entrenamiento

### 3. Datos nuevos
- Aplicación práctica del modelo
- Transformación con parámetros fijos

## Ejemplos

### Ejemplo 1: Predicción de precios inmobiliarios
- **Entrenamiento**: Se escalan las características (normalización) con datos históricos
- **Prueba**: Se aplican los mismos factores de escala a datos nuevos
- **Error**: Si usas diferentes escalas en prueba, obtendrás resultados engañosamente buenos

### Ejemplo 2: Clasificación de imágenes médicas
- **Entrenamiento**: Se reduce dimensionalidad de las imágenes (PCA)
- **Prueba**: Se usa la misma matriz de reducción PCA
- **Error**: Recalcular PCA en prueba = pérdida de validez en el rendimiento medido

