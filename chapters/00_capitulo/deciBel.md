Me surge una pequeña duda respecto al nombre de la unidad y lo que veo con mis ojos. 
Supongamos que yo establezco que la unidad de medida de distancia es el metro. Pero el metro es muy grande comparado con lo que quiero medir, entonces uso el *decimetro*. Es decir 10(unidad en metros). 
¿Por qué el *deciBel* (dB) se multiplica por 20? ¿De donde sale ese 2 que me convierte el 10 en 20?

Es una pregunta **brillante** y demuestra que estás analizando críticamente lo que estás aprendiendo en lugar de simplemente memorizar fórmulas. 

Tienes toda la razón en tu razonamiento lingüístico: el prefijo "deci" significa la décima parte de algo. Un decibelio (dB) es exactamente la décima parte de un Belio (B).

Entonces, ¿de dónde sale ese misterioso 20? La respuesta corta es que **el 20 es en realidad un $10 \times 2$**. 

El "10" viene del prefijo *deci*, y el "2" aparece por una propiedad de los logaritmos al relacionar **Voltaje** con **Potencia**. Aquí te muestro la deducción exacta de dónde sale ese "2".

### 1. El origen: El Belio mide Potencia
El Belio (nombrado así por Alexander Graham Bell) se inventó originalmente para medir la pérdida de señal en cables telefónicos, y se definió estrictamente para relaciones de **Potencia** ($P$), no de voltaje.

La fórmula original de ganancia en Belios es simplemente el logaritmo base 10:
$$\text{Ganancia (B)} = \log_{10}\left(\frac{P_{out}}{P_{in}}\right)$$

Como el Belio resultaba ser una unidad muy grande (al igual que el metro para medir cosas pequeñas), los ingenieros empezaron a usar el **decibelio**. Para convertir Belios a decibelios, simplemente **multiplicas por 10**:
$$\text{Ganancia (dB)} = 10 \log_{10}\left(\frac{P_{out}}{P_{in}}\right)$$

¡Aquí la palabra "deci" tiene todo el sentido del mundo!

### 2. El problema: En electrónica solemos medir Voltaje
En tu curso de circuitos analógicos, rara vez mides los vatios exactos con un vatímetro; usas un osciloscopio o un multímetro para medir voltajes ($V_{out}$ y $V_{in}$). 

Por la Ley de Joule y la Ley de Ohm, sabemos que la potencia es proporcional al **cuadrado** del voltaje:
$$P = \frac{V^2}{R}$$

### 3. La aparición del "2" mágico
Si queremos calcular la ganancia de potencia en dB, pero solo tenemos las mediciones de voltaje, sustituimos la fórmula de la potencia en la ecuación original de los decibelios. 

*(Asumiendo que la resistencia de entrada y salida es la misma, que es la convención estándar para esta definición):*

$$\text{Ganancia (dB)} = 10 \log_{10}\left( \frac{\frac{V_{out}^2}{R}}{\frac{V_{in}^2}{R}} \right)$$

Las resistencias ($R$) se cancelan:
$$\text{Ganancia (dB)} = 10 \log_{10}\left( \frac{V_{out}^2}{V_{in}^2} \right)$$

Agrupamos el cuadrado:
$$\text{Ganancia (dB)} = 10 \log_{10}\left( \left(\frac{V_{out}}{V_{in}}\right)^2 \right)$$

**Y aquí entra la magia de las matemáticas.** Hay una propiedad fundamental de los logaritmos que dice que el exponente de un argumento puede "bajar" multiplicando al frente del logaritmo: $\log(x^a) = a \cdot \log(x)$.

Bajamos el exponente 2:
$$\text{Ganancia (dB)} = 10 \cdot 2 \cdot \log_{10}\left( \frac{V_{out}}{V_{in}} \right)$$

$$ \text{Ganancia (dB)} = 20 \log_{10}\left(\frac{V_{out}}{V_{in}}\right)$$

### Resumen para tus apuntes
El "deci" no ha cambiado de significado. La regla de oro es:
* Si estás relacionando **Potencias** ($W$), la fórmula lleva un **$10$**.
* Si estás relacionando **Voltajes** ($V$) o **Corrientes** ($A$), la fórmula lleva un **$20$** porque estas magnitudes están elevadas al cuadrado cuando se traducen a potencia de forma implícita.

Y como la función de transferencia $H(j\omega)$ es una relación de voltajes ($V_{out}/V_{in}$), siempre usaremos el 20. 

Es una excelente observación conceptual. ¿Quedó claro cómo el cuadrado del voltaje es el verdadero "culpable" de ese 20?
