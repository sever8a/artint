--- 
title: Transformers
summary: Redes con mecanismos de atención.
authors:
    - Reproducción autorizada
    - Jose Robledano
date: 2026-02-12
---
# Fundamentos de los Transformers

## Introducción

Hasta 2017, las redes neuronales recurrentes (RNN), especialmente LSTM y GRU, eran el estado del arte para tareas secuenciales como traducción automática, modelado de lenguaje y reconocimiento de voz. Sin embargo, las RNN procesan las secuencias de forma iterativa, paso a paso, lo que dificulta la paralelización y limita la capacidad de capturar dependencias de largo alcance debido al desvanecimiento del gradiente (aunque LSTM/GRU lo mitigan, no lo eliminan por completo).

En 2017, el artículo **"Attention is All You Need"** (Vaswani et al.) introdujo una nueva arquitectura llamada **Transformer**, que prescinde por completo de la recurrencia y se basa únicamente en mecanismos de **atención**. Esto revolucionó el campo del procesamiento del lenguaje natural y se ha extendido a otras áreas como visión por computador, audio y más.

Este documento explica los fundamentos de los Transformers, su arquitectura, componentes clave, casos de éxito y tendencias actuales.

## Objetivos del documento

- Comprender las limitaciones de las RNN que motivaron los Transformers.
- Describir la arquitectura Transformer: codificador, decodificador y mecanismo de atención.
- Explicar los componentes clave: self-attention, multi-head attention, positional encoding, feed-forward.
- Conocer las ventajas sobre las RNN.
- Identificar aplicaciones exitosas y modelos derivados (BERT, GPT, etc.).
- Explorar las tendencias actuales y el futuro de los Transformers.

---

## 1. Limitaciones de las RNN y necesidad de una nueva arquitectura

Las RNN procesan secuencias elemento por elemento, manteniendo un estado oculto que se actualiza en cada paso. Esto tiene varios inconvenientes:

- **Procesamiento secuencial**: no se puede paralelizar el entrenamiento a lo largo de la secuencia, lo que lo hace lento en GPUs.
- **Dependencias a largo plazo**: aunque LSTM/GRU mejoran, aún pueden tener dificultades para conectar elementos muy distantes.
- **Desvanecimiento del gradiente**: persiste en cierta medida, especialmente en secuencias muy largas.

El Transformer aborda estos problemas utilizando **atención** para ponderar la relevancia de cada elemento de la secuencia con respecto a los demás, permitiendo un procesamiento paralelo y una conexión directa entre posiciones lejanas.

---

## 2. Arquitectura Transformer

El Transformer original se diseñó para tareas de secuencia a secuencia (como traducción). Consta de dos partes principales: un **codificador** y un **decodificador**. Ambas están compuestas por una pila de capas idénticas.

![Arquitectura Transformer](https://miro.medium.com/max/1400/1*BHzGVskWGS_3jE-6oE0yTw.png)

### 2.1 Codificador

El codificador transforma una secuencia de entrada (por ejemplo, una oración en español) en una representación continua que captura el contexto de cada palabra. Está formado por una pila de \(N\) capas (generalmente 6). Cada capa tiene dos subcapas:

1. **Mecanismo de autoatención multi-cabeza (Multi-Head Self-Attention)**.
2. **Red feed-forward totalmente conectada** (dos capas lineales con activación ReLU).

Cada subcapa va seguida de una **conexión residual** (suma de la entrada y la salida) y una **normalización de capa** (Layer Normalization).

La salida del codificador es una secuencia de vectores de la misma longitud que la entrada, pero enriquecidos con información contextual.

### 2.2 Decodificador

El decodificador genera la secuencia de salida (por ejemplo, la traducción al inglés) paso a paso, de forma autorregresiva. También es una pila de \(N\) capas, pero cada capa tiene tres subcapas:

1. **Autoatención multi-cabeza enmascarada** (Masked Multi-Head Self-Attention): evita que el decodificador vea posiciones futuras (para mantener la propiedad autorregresiva).
2. **Atención cruzada (encoder-decoder attention)**: permite que el decodificador atienda a la salida del codificador.
3. **Red feed-forward**.

Al igual que en el codificador, cada subcapa tiene conexión residual y normalización.

### 2.3 Mecanismo de atención

El corazón del Transformer es la **atención escalada por producto punto** (Scaled Dot-Product Attention). Se define como:

\[
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right) V
\]

Donde:
- \(Q\) (queries), \(K\) (keys) y \(V\) (values) son matrices obtenidas a partir de las representaciones de entrada mediante proyecciones lineales.
- \(d_k\) es la dimensión de las keys (factor de escala para evitar gradientes pequeños).

La idea es que cada elemento (query) calcula una puntuación de similitud con todos los elementos (keys), se normaliza con softmax y se usa para ponderar los values.

#### 2.3.1 Autoatención (Self-Attention)

En la autoatención, \(Q\), \(K\) y \(V\) provienen de la misma secuencia (por ejemplo, las palabras de la oración de entrada). Esto permite que cada palabra atienda a todas las palabras de la misma secuencia, capturando relaciones contextuales.

#### 2.3.2 Atención multi-cabeza (Multi-Head Attention)

En lugar de una sola atención, se realizan \(h\) atenciones en paralelo (cabezas), cada una con proyecciones lineales diferentes de \(Q\), \(K\), \(V\). Luego se concatenan y se proyectan nuevamente. Esto permite que el modelo atienda a información de diferentes subespacios representacionales.

\[
\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, ..., \text{head}_h) W^O
\]
con \(\text{head}_i = \text{Attention}(Q W_i^Q, K W_i^K, V W_i^V)\)

### 2.4 Codificación posicional (Positional Encoding)

Como el Transformer no tiene recurrencia ni convolución, no tiene noción del orden de la secuencia. Para inyectar información de posición, se suman a los embeddings de entrada unos vectores que codifican la posición. En el artículo original se usan funciones seno y coseno de diferentes frecuencias:

\[
PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right)
\]
\[
PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right)
\]

Esto permite que el modelo aprenda dependencias relativas fácilmente.

### 2.5 Red feed-forward

Cada capa contiene una red totalmente conectada que se aplica a cada posición por separado (idéntica para todas las posiciones). Suele ser de dos capas lineales con activación ReLU:

\[
\text{FFN}(x) = \max(0, xW_1 + b_1)W_2 + b_2
\]

### 2.6 Conexiones residuales y normalización

Las conexiones residuales ayudan a entrenar redes profundas al permitir que el gradiente fluya directamente. La normalización de capa (LayerNorm) estabiliza el entrenamiento.

---

## 3. Comparación con RNN/LSTM

| Característica | RNN/LSTM | Transformer |
|----------------|----------|-------------|
| Procesamiento | Secuencial | Paralelo (sobre toda la secuencia) |
| Dependencias lejanas | Limitadas (aunque mejoradas en LSTM) | Captura directa mediante atención |
| Complejidad temporal por capa | \(O(n)\) | \(O(n^2 \cdot d)\) (pero paralelizable) |
| Memoria | Estado oculto fijo | Atención sobre todas las posiciones |
| Entrenamiento | Lento (no paralelizable en tiempo) | Rápido en GPU (paralelización total) |

La complejidad cuadrática \(O(n^2)\) de la atención puede ser un problema para secuencias muy largas, pero se han propuesto variantes eficientes.

---

## 4. Casos de uso de éxito

- **Modelos de lenguaje**: GPT (Generative Pre-trained Transformer), BERT (Bidirectional Encoder Representations from Transformers) y sus variantes (RoBERTa, ALBERT, etc.) dominan el NLP.
- **Traducción automática**: el Transformer original superó a las RNN en tareas de traducción.
- **Generación de texto**: GPT-3, ChatGPT, etc., generan texto coherente y contextual.
- **Preguntas y respuestas**, **resumen de texto**, **análisis de sentimiento**.
- **Visión por computador**: Vision Transformer (ViT) aplica Transformers a imágenes dividiéndolas en parches.
- **Audio**: Speech Transformers para reconocimiento de voz, generación de música.
- **Bioinformática**: análisis de secuencias de proteínas (AlphaFold2 usa Transformers).
- **Sistemas de recomendación**: modelado de secuencias de interacciones de usuarios.

---

## 5. Tendencias actuales y evolución

### Modelos pre-entrenados a gran escala

La tendencia es entrenar modelos cada vez más grandes con más datos y luego ajustarlos (fine-tuning) para tareas específicas. Ejemplos:
- **BERT** (110M parámetros) y **GPT-3** (175B parámetros).
- **PaLM**, **Chinchilla**, **LLaMA**, etc., con cientos de miles de millones de parámetros.

### Eficiencia y escalado

La atención cuadrática limita el manejo de secuencias muy largas. Se investigan mecanismos de atención eficientes:
- **Sparse Attention** (solo atiende a ciertas posiciones).
- **Linformer**, **Performer** (aproximaciones de bajo rango).
- **Longformer**, **BigBird** (atención dispersa + global).

### Transformers en visión

- **ViT** (Vision Transformer) y sus mejoras (DeiT, Swin Transformer) compiten con CNN en tareas de clasificación y detección.
- **DALL-E**, **Stable Diffusion** usan Transformers en combinación con otros modelos para generación de imágenes.

### Multimodalidad

Modelos como **CLIP** (texto-imagen), **Flamingo**, **Gato** (agente multimodal) integran diferentes modalidades en una arquitectura Transformer.

### Eficiencia en inferencia

Para dispositivos móviles, se buscan versiones más ligeras: **DistilBERT**, **TinyBERT**, **MobileBERT**.

### Más allá del NLP

Los Transformers se aplican en robótica, control, simulación de física, etc.

---

## 6. Conclusión

Los Transformers han revolucionado el deep learning al eliminar la recurrencia y basarse en atención, permitiendo un entrenamiento paralelo y una capacidad sin precedentes para capturar dependencias contextuales. Modelos como BERT y GPT se han convertido en herramientas fundamentales en NLP y están expandiéndose a otras áreas. A pesar de los retos de eficiencia para secuencias muy largas, la investigación continua en arquitecturas eficientes y modelos multimodales asegura que los Transformers seguirán siendo una pieza clave en la inteligencia artificial.

---

## Referencias

- Vaswani, A., et al. (2017). Attention is all you need. *NeurIPS*.
- Devlin, J., et al. (2019). BERT: Pre-training of deep bidirectional transformers for language understanding. *NAACL*.
- Brown, T., et al. (2020). Language models are few-shot learners. *NeurIPS*.
- Dosovitskiy, A., et al. (2021). An image is worth 16x16 words: Transformers for image recognition at scale. *ICLR*.
- Tay, Y., et al. (2022). Efficient transformers: A survey. *ACM Computing Surveys*.

---
