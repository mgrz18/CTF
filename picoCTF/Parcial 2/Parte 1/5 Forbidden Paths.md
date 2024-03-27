## Objetivo
Can you get the flag? Here's the website. We know that the website files live in /usr/share/nginx/html/ and the flag is at /flag.txt but the website is filtering absolute file paths. Can you get past the filter to read the flag?
http://saturn.picoctf.net:55793/

## Pistas
NONE

## Solución
En este reto, nos dicen donde se encuentran los archivos que posee el servidor, y nos dicen que las rutas absolutas las está filtrando el sitio, entonces si nosotros no usamos rutas absolutas y en vez de eso usamos .. podremos llegar a la bandera que estamos buscando.

```
../../../../flag.txt
```

## Notas adicionales
## Referencias