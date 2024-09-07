# Sistemas de razonamiento impreciso
Los sistemas de razonamiento pueden describirse por la exactitud que necesitan al realizar cualquier paso de su proceso de razonamiento. Los sistemas de razonamiento más preciso son aquellos que sólo se ocupan de las relaciones lógicamente válidas, conocidas con certeza. En estos casos, las conclusiones son verdaderas, si las premisas son verdaderas.

Existen metodologías que permiten el razonamiento bajo condiciones de **incertidumbre**. El uso de estos sistemas cobra gran importancia cuando se trata de construir agentes que van a operar en situaciones reales en las que, por tanto, se manejará incertidumbre.

Entre las aproximaciones existentes para el manejo de la incertidumbre se incluyen el uso de métodos probabilísticos como las redes bayesianas y la lógica difusa.

## Redes bayesianas
El teorema de Bayes nos permite actualizar las probabilidades de variables cuyo estado no hemos observado dada una serie de nuevas observaciones. Las redes bayesianas automatizan este proceso, permitiendo que el razonamiento avance en cualquier dirección a través de la red de variables. Las redes bayesianas están constituidas por una **estructura en forma de grafo**, en la que cada **nodo representa variables aleatorias** (discretas o continuas) y cada **arista representa las conexiones directas entre ellas**.

No entraremos en detalle del funcionamiento de una red bayesiana, aunque sí veremos el teorema de Bayes, que se usa en numerosos ámbitos de la vida real.

La probabilidad de ocurrencia de un evento A se expresa como:

$$ P(A) = {nº\\_ocurrencias\\_A \over nº\\_total\\_eventos} $$

La probabilidad de ocurrencia de un evento A condicionada a que ocurra otro evento B se especifica mediante el teorema de Bayes de la forma:

$$ P(A|B) = {P(B|A) * P(A) \over P(B)} $$

### Ejemplo. Infección zombi
Una nueva epidemia se extiende por Elche. Los afectados se convierten en zombis apenas un par de días después del contagio. La prevalencia de esta epidemia es de 5 infectados por cada mil habitantes. Para intentar controlar la epidemia se ha desarrollado un test de antígenos muy preciso, con una sensibilidad del 99.9% y especificidad de 99.0%. Realmente es un test muy bueno. Cuando hay infección zombi, el test da positivo el 99.9% de las veces y negativo el 0.1%. Cuanto no hay infección zombi, el test da negativo el 99.0% de las veces y positivo el 1.0%.

Lo podemos ver mejor en la siguiente tabla:

|               | Infección zombi              | No infección                 |
| ------------- | ---------------------------- | ---------------------------- |
| Test positivo | 0,999 (verdaderos positivos) | 0,010 (falsos positivos)     |
| Test negativo | 0,001 (falsos negativos)     | 0,990 (verdaderos negativos) |

Has ido a una fiesta y sospechas que puedes haberte contagiado, pero no sabes si estás infectado o no, por lo que recurres a hacerte un test. Lamentablemente, el test da un resultado POSITIVO.

PANICO: el test te está diciendo que con un 99.9% de probabilidad estás contagiado, eso es casi una certeza. Una vez superado el shock inicial, asumes lo inevitable y te preparas para lo peor, pero hay algo que no cuadra…

Si hubiese recurrido a Bayes desde el principio me habría ahorrado el susto:

$$ P(infeccion|test\\_positivo) = {P(test\\_positivo|infeccion) * P(infeccion) \over P(test\\_positivo)} $$

$$ P(test\\_positivo) = P(verdadero\\_positivo) * P(infeccion) + P(falso\\_positivo ) ∗ P(no\\_infeccion)$$

$$ P(test\\_positivo) = 0.999 ∗ 0.005 + 0.01 ∗ 0.995 = 0.015 $$

$$ P(infeccion|test\\_positivo)= {0.999 ∗ 0.005 \over 0.015} = 0.33 $$

¡Menudo susto! Tengo un 33% de probabilidad de estar infectado. Mis posibilidades son mucho mejores de lo había imaginado inicialmente.

## Lógica difusa
La lógica difusa es capaz de procesar distintos grados de verdad, pero estos no deben ser interpretados en el sentido de probabilidades, pues lo que representan dentro del ámbito de la lógica difusa es la **probabilidad de pertenencia a cierto conjunto**, en vez de la probabilidad de que ocurra un evento.

Un ejemplo. Si se dispone de una botella numerada como 1 con agua que tiene un grado de pertenencia difuso del 80% al conjunto de agua potable. Por otro lado, la botella numerada como 2 tiene una probabilidad del 80% de ser potable. ¿De qué botella es menos arriesgado beber?

Se ha de interpretar que la primera botella tiene un contenido de agua que es bastante similar al de otras botellas que son potables, alrededor de un 80%, mientras que en el caso de la segunda botella lo que se quiere decir es que, si se bebe el agua de una botella de ese tipo, el 80% de las veces que se han analizado contenían agua potable. Pero cuidado, que en un 20% de las ocasiones su contenido completo era de agua no potable.