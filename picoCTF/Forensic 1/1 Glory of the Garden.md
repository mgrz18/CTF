## Objetivo
This garden contains more than it seems.
https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg

## Solución
Este reto a mi parecer tiene dos posibles formas de solucionarse. A simple vista parece que la foto del jardin que encontramos es una simple foto sin ningún mensaje aparente, pero no nos hemos preguntado que es lo que contiene adentro, como es que en realidad se almacenan cada uno de esos pixeles que nosotros podemos ver en la imagen, para ver eso, nosotros tenemos dos opciones
- Editor de texto
- Editor hexadecimal

Para el editor hexadecimal
```bash
mgarcia@nightmare:/mnt/c/Users/mgarcia/Downloads$ xxd garden.jpg
00230550: a2bb bdac 9687 98e4 d3b2 e87f ffd9 4865  ..............He
00230560: 7265 2069 7320 6120 666c 6167 2022 7069  re is a flag "pi
00230570: 636f 4354 467b 6d6f 7265 5f74 6861 6e5f  coCTF{more_than_
00230580: 6d33 3374 735f 7468 655f 3379 3333 6464  m33ts_the_3y33dd
00230590: 3265 4546 357d 220a                      2eEF5}".
mgarcia@nightmare:/mnt/c/Users/mgarcia/Downloads$
```

Para el editor de código, en este caso yo usaré vim
```
vim garden.jpg
/pico
<CR>
```

Después podemos observar que en la última linea se encuentra la bandera que estamos buscando

## Bandera
picoCTF{more_than_m33ts_the_3y33dd2eEF5}

## Notas

## Referencias
