## Objetivo
Morse code is well known. Can you decrypt this? Download the file [here](https://artifacts.picoctf.net/c/79/morse_chal.wav). Wrap your answer with picoCTF{}, put underscores in place of pauses, and use all lowercase.

## Pistas
- Audacity is a really good program to analyze morse code audio.

## Solución
Después de descargar el audio, utilicé este [decodificador en línea](https://morsecode.world/international/decoder/audio-decoder-adaptive.html), donde solo subí el audio para que decodificara el mensaje enviado. Después añadí guines bajos en el resultado obtenido y le di el formato de una bandera de picoCTF

1. WH47 H47H 90D W20U9H7
2. WH47_H47H_90D_W20U9H7
3. picoCTF{WH47_H47H_90D_W20U9H7}

## Notas

## Referencias
