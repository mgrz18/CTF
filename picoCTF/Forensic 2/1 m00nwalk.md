## Objetivo
Decode this message from the moon.
https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav


## Solución
Este nivel contiene un archivo de audio WAV que pareciera no tener ningún tipo de sentido en lo que está reproduciendo o al menos eso creemos, según las pistas está codificado con un algoritmo llamado Scottie y además es un mensaje de tipo SSTV, lo que con algún programa puede permitirnos entender que es lo que se está mostrando.

En este caso yo estaré usando windows, y dos herramientas
- RX-SSTV
- vb cable driver

vb cable driver nos permite emular un microfono virtual, que nos va a permitir hacer pensar al programa RXSSTV que está recibiendo algún tipo de señal de algún micrófono cuando en realidad solo estaremos reproduciendo el audio WAV.

Entonces, seleccionamos scottie 1 como algoritmo de codificado, y después reproducimos el audio, podremos ver como poco a poco va a ir cargando la imagen decodificada que contiene la bandera.


## Notas
Hoy en día la ISS todavía transmite imágenes de este tipo que podemos decodificar!!!!

## Referencias
