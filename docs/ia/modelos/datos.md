# Tratamiento de Datos

## Datos Numéricos

Los datos numéricos son la base de muchos modelos de ML, pero a menudo necesitan ser preprocesados para que los funcionen de manera óptima.
> [!IMPORTANT]
> El preprocesamiento de datos numéricos es crítico para el rendimiento del modelo. Datos mal escalados pueden causar convergencia lenta, resultados sesgados o predicciones incorrectas. Técnicas como la estandarización y normalización aseguran que todas las características contribuyan equitativamente al entrenamiento.

### Estandarización

Transforma los datos para que tengan una media de 0 y una desviación estándar de 1. Esto se hace restando la media y dividiendo por la desviación estándar.

- **Cuándo usarla**: Crucial para algoritmos sensibles a la escala (SVM, K-Means)
- **Beneficio**: Evita que características con rangos grandes dominen el cálculo de distancias o gradientes

## Columnas Categóricas
### Definición

Los datos categóricos son variables que toman valores pertenecientes a un conjunto finito de categorías o clases discretas, sin relación numérica inherente. Pueden ser nominales (sin orden: colores, países) u ordinales (con orden: tallas, niveles educativos). A diferencia de los datos numéricos continuos, no pueden operarse matemáticamente de forma directa, por lo que requieren codificación antes de alimentarlos a algoritmos de ML.

> [!WARNING]
> **Ejemplo crítico**: Si alimentas directamente valores categóricos como "rojo"=0, "verde"=1, "azul"=2 a un algoritmo de regresión, el modelo interpretará que "azul" > "verde" > "rojo" numéricamente, creando relaciones falsas. Esto causa predicciones incorrectas. Por eso es imprescindible codificar estas variables antes del entrenamiento.

### One-Hot Encoding

Crea nuevas columnas binarias (0 o 1) para cada categoría única.

- **Uso**: Variables nominales (sin orden) con número razonable de categorías
- **Ventaja**: Evita que el modelo asuma orden o relación numérica

### Dummy Encoding

Similar a One-Hot, pero crea n-1 columnas para n categorías, omitiendo una de referencia.

- **Uso**: Evitar multicolinealidad perfecta en regresión
- **Nota**: La suma de columnas dummy no iguala la columna de intercepción

### Label Encoding

Asigna un número entero único a cada categoría.

- **Uso**: Variables ordinales con orden intrínseco (ej. Pequeño=1, Mediano=2, Grande=3)

### Target Encoding

Reemplaza cada categoría con la media de la variable objetivo para esa categoría.

- **Ventaja**: Muy efectivo para muchas categorías
- **Desventaja**: Propenso al sobreajuste

## Columnas de Fecha y Hora

Las fechas y horas contienen información valiosa que debe extraerse y convertirse a formato numérico.

### Extracción de Componentes

Extraer características numéricas: año, mes, día, día de la semana, día del año, hora, minuto, segundo.

- **Práctica**: Casi siempre es el primer paso
- **Beneficio**: Captura patrones estacionales o cíclicos

### Diferencias de Tiempo

Calcular la diferencia entre una fecha y una fecha de referencia.

- **Uso**: Medir antigüedad o duración
- **Resultado**: Convierte la fecha en característica numérica continua

## Columnas de Texto

Las columnas de texto requieren técnicas específicas para extraer características.

### Split y Extracción de Componentes

Dividir la cadena usando un delimitador para extraer componentes específicos.

- **Uso**: Descomponer estructuras complejas

### Top Prefijos y Sufijos

Identificar los prefijos o sufijos más comunes y crear características binarias basadas en su presencia.

### Longitud de la Cadena

Calcular la longitud del texto.

- **Ejemplo**: URLs largas podrían indicar spam

### Conteo de Caracteres Específicos

Contar caracteres especiales, números o letras mayúsculas.

- **Ejemplo**: Número de guiones en un nombre de host

### TF-IDF

Convertir texto en vectores numéricos que representan la importancia de las palabras (para textos más largos).