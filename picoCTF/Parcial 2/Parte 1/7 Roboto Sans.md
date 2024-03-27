## Objetivo
The flag is somewhere on this web application not necessarily on the website. Find it. Check this out.
http://saturn.picoctf.net:56615/

## Pistas
(None)

## Solución
Primero que nada, podemos descargar el sitio web con este comando
```
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://saturn.picoctf.net:56615/
```

La segunda parte consiste en buscar la bandera, como no existe en formato picoCTF, podemos buscar la palabra flag
```bash
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:56615
 % grep -r "flag" .
./index.html:            end six_box   The flag is not here but keep digging :)-- >
./index.html:            var image = 'images/maps-and-flags.png';
./robots.txt:Think you have seen your flag or want to keep looking.
```


Podemos ver que el archivo robots.txt nos muestra alguna información interesante sobre la bandera.
Si nosotros observamos el archivo robots.txt, podemos ver que ahí adentro hay algo sospechoso codificado en base 64
```bash
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:56615
 % cat robots.txt
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/% 
```

Y por último si nosotros decodificamos el código, podemos ver que hay algo bastante interesante

```
mgarcia@nightmare ~/mgarcia/Desktop/saturn.picoctf.net:56615
 % echo anMvbXlmaWxlLnR4dA== | base64 -d
js/myfile.txt% 
```

Este path proporcionado, nos arroja la bandera que estamos buscando.


## Notas adicionales
## Referencias