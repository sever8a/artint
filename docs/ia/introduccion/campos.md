--- 
title: Usos
summary: Los usos son múltiples, pero es necesario afinar la imaginación y la inventiva para ampliar sus posibilidades.
authors:
    - Revisión autorizada
    - Jose Robledano
date: 2024-10-01
---
# Campos de aplicación de la inteligencia de artificial.
A continuación, vamos a entrar en detalle en los distintos campos de aplicación de la inteligencia artificial.

## Visión artificial
La visión artificial ha experimentado una transformación radical gracias al aprendizaje profundo y las redes convolucionales en la última década. Estos avances han dado lugar a una amplia gama de aplicaciones, que van desde la clasificación de imágenes hasta la identificación de rostros, pasando por la detección de objetos y el seguimiento de movimientos.

En el ámbito de la **clasificación de imágenes**, se han desarrollado algoritmos que pueden distinguir y categorizar objetos en fotografías, como reconocer la diferencia entre perros y gatos o interpretar los números en las matrículas de los vehículos.

Los **algoritmos de seguimiento** han permitido que drones equipados con cámaras realicen búsquedas y rastreos de personas desaparecidas, y sigan a posibles delincuentes. Combinados con cámaras térmicas, estos algoritmos se han convertido en herramientas de seguridad esenciales, utilizadas para supervisar áreas naturales y bosques con el objetivo de prevenir incendios.

En el ámbito de la seguridad, los **detectores de objetos** se utilizan en sistemas de inspección para evitar la introducción de armas u objetos prohibidos en trenes y aviones.

Los **segmentadores de imágenes** permiten aislar objetos del fondo en una imagen, y esta tecnología se emplea con éxito en la construcción de modelos tridimensionales de órganos a partir de imágenes médicas bidimensionales.

Los **identificadores de rostros**, una forma especializada de los detectores de caras, posibilitan la creación de sistemas avanzados de control de acceso. Un ejemplo destacado es un ascensor desarrollado por la empresa asturiana "ATI Ascensores" que puede identificar automáticamente a los residentes y llevarlos a su destino, lo que representa un avance importante para las personas con discapacidades motoras o sensoriales.

Las redes generativas antagónicas (*Generative Adversarial Networks*, GAN) han causado un impacto revolucionario en la industria cinematográfica, permitiendo la **creación de rostros** extremadamente realistas de personas reales, incluso después de su fallecimiento. Sin embargo, también han dado lugar a la proliferación del software DeepFake, que puede modificar caras en imágenes y videos para hacer parecer que una persona es otra, inundando las tiendas de aplicaciones de dispositivos móviles con estas herramientas.

Además, los autoencoders se utilizan para mejorar la calidad de las fotografías y videos, eliminando el ruido y restaurando la claridad de las imágenes.

## Proceso y adquisión de vídeo

Al igual que en el anterior apartado, el procesamiento de videos (secuencias de imágenes en movimiento) y la representación de escenas mediante técnicas como el trazado de rayos, el superescalado, DLSS y otros algoritmos de mejora han marcado un nuevo estándar en la industria de los videojuegos. Esto ha llevado la calidad de la gran pantalla directamente al hogar, aunque es importante tener en cuenta que los requisitos de hardware para lograrlo no deben subestimarse. Por ejemplo, para llevar a cabo estas tareas en videojuegos con resolución Full HD o 2K (dependiendo del título), se requiere una tarjeta gráfica potente y moderna, como una RTX3060 de la familia Ampere o equivalente.

El **trazado de rayos** (*Ray Tracing*) utiliza algoritmos avanzados que permiten determinar los lugares donde la luz se refleja o refracta para representar de manera precisa los reflejos y refracciones en tiempo real. En la década de 2000, esta técnica se usaba principalmente para generar gráficos estáticos como apoyo a la venta, por ejemplo, para renderizar imágenes de proyectos urbanísticos complejos. Esto se hacía utilizando múltiples tarjetas gráficas en paralelo a través de tecnologías como SLI (Scalable Link Interface) o CrossFire.

El **superescalado** (*Supersampling*) en términos sencillos implica mejorar artificialmente una imagen para obtener una mayor resolución en una pantalla, como una pantalla 4K, sin sacrificar la velocidad de cuadros por segundo (fps) generada por la tarjeta gráfica. Existen diversas tecnologías para lograrlo, siendo la más establecida la de NVIDIA con su Deep Learning Super Sampling (DLSS), seguida de cerca por AMD con FidelityFX Super Resolution (FSR).

Además, cabe mencionar **DeepStream**, que aunque no está directamente relacionado con las tecnologías mencionadas anteriormente, consiste en un conjunto de bibliotecas de procesamiento de video que se está implementando en aplicaciones industriales para el control, análisis y procesamiento de videos, así como datos de sensores ópticos.

## Reconocimiento de voz y lenguaje natural.

Estas dos disciplinas están estrechamente relacionadas entre sí, al punto que varios expertos consideran el reconocimiento automático del habla (ASR, *Automatic Speech Recognition*) como una subdisciplina del procesamiento de lenguaje natural (NLP, *Natural Language Processing*).

El reconocimiento de voz y el procesamiento de lenguaje natural permiten buscar información específica, realizar **traducciones automáticas** y ofrecer una interfaz amigable para **asistentes virtuales y chatbots**.

Los productos robóticos basados en la plataforma **NVIDIA Jetson** pueden aprovechar algoritmos de inteligencia artificial tanto en unidades de procesamiento gráfico (GPU) como en unidades de procesamiento central (CPU) para llevar a cabo tareas de reconocimiento de voz y NLP. Es importante señalar que el uso de NLP no siempre implica la utilización de inteligencia artificial, como se puede ver al emplear la Software Development Kit (SDK) de NLTK (*Natural Language Tool Kit*). En el caso de las tecnologías propietarias de NVIDIA, NeMo y Jarvis son las interfaces de programación de aplicaciones (API) encargadas de estas tareas, e incluso incluyen un motor de síntesis de texto a voz (TTS).

## Asistentes virtuales y recomendadores.

En diversas modalidades, **asistentes virtuales** como Alexa, Siri o Google están ingresando en los hogares con el propósito de simplificar la automatización del entorno doméstico a un costo asequible.

Los **sistemas de recomendación** y otros chatbots tienen la función de desempeñar el rol de asistentes de ventas. Cuando se combinan con técnicas de visión mejorada y realidad aumentada, permiten a los usuarios visualizar cómo les quedaría una prenda específica o les sugieren otros productos que podrían interesarles, basándose en la relación de datos de compras realizadas por otros usuarios que han adquirido productos similares.

## Ciencias de datos y *Data Mining*
Dentro del ámbito de la ciencia de datos, la inteligencia artificial ha tenido un impacto significativo al permitir la **identificación de patrones y relaciones** a través de métodos no supervisados. Además, facilita la realización de agrupaciones y aplicaciones heurísticas. Existen diversos algoritmos y herramientas disponibles, como por ejemplo, **nVidia RAPIDS**, que utiliza los núcleos CUDA de una unidad de procesamiento gráfico (GPU) para acelerar el proceso de entrenamiento y la inferencia en redes neuronales. En este campo, también se incluyen heurísticas y sistemas de detección de anomalías que se aplican en el ámbito del mantenimiento industrial.

## Ciberseguridad.
Sistemas como **nVidia Morpheus** pueden hacer las funciones de un **IDS** (*Intruder Detector System*) mediante la búsqueda de anomalías en el tráfico de red.