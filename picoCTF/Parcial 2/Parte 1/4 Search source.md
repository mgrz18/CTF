## Objetivo
The developer of this website mistakenly left an important artifact in the website source, can you find it? The website is here
http://saturn.picoctf.net:65086/

## Pistas
How could you mirror the website on your local machine so you could use more powerful tools for searching?

## Solución
En este reto, la pista nos dice que podemos descargar el sitio web para poder revisarlo más a fondo, si nosotros utilizamos el comando grep, podemos encontrar alguna cadena que esté dentro de algún archivo para ahorrar tiempo buscando manualmente la cadena, en este caso si ya conocemos que la bandera que buscamos, podemos usar el siguiente comando

```bash
grep -r "cadena a buscar" directorio a buscar

```

```bash
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:65086
 % grep -r "picoCTF" .
./css/style.css:/** banner_main picoCTF{1nsp3ti0n_0f_w3bpag3s_587d12b8} **/
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:65086
 %
```

## Notas adicionales
## Referencias