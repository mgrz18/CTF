## Objetivo
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled1.png) [scrambled2.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled2.png)

## Pistas
- https://en.wikipedia.org/wiki/Visual_cryptography
- Think of different ways you can "stack" images

## Solución
En este reto usaremos una herramienta llamada ImageMagick que nos va a permitir decifrar el mensaje de este reto.
```zsh
mrfear@nightmare:~/winhome/Desktop$ sudo dnf install ImageMagick
Last metadata expiration check: 0:00:13 ago on Wed 17 Apr 2024 01:06:19 PM CST.
Package ImageMagick-1:7.1.1.26-2.fc39.x86_64 is already installed.
Dependencies resolved.
Nothing to do.
Complete!
mrfear@nightmare:~/winhome/Desktop$ convert scrambled1.png scrambled2.png -compose Add -composite flag.png
mrfear@nightmare:~/winhome/Desktop$
```
Después de ejecutar estos comandos, podremos ver que ya se habrá generado una nueva imagen con la bandera buscada.

```powershell

```

## Notas

## Referencias
