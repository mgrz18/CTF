## Objetivo
Find the flag in this picture. https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png

## Solución
Podemos usar la herramienta _xxd_ que permite ver cuál es el contenido hexadecimal de un archivo, en este caso primero intenté resolver el reto utilizando la herramienta hexiftool porque el título era So Meta, pensando en que la bandera estaría dentro de los metadatos de la foto, pero al revisarla de nuevo con un editor hexadecimal, me doy cuenta que al igual que en el anterior reto, la bandera se encuentra al final de los bytes de la imagen.

```bash
0001a8c0: 576c 1700 0000 2074 4558 7441 7274 6973  Wl.... tEXtArtis
0001a8d0: 7400 7069 636f 4354 467b 7330 5f6d 3374  t.picoCTF{s0_m3t
0001a8e0: 615f 6438 3934 3439 3239 7d4b f261 ca00  a_d8944929}K.a..
0001a8f0: 0000 0049 454e 44ae 4260 82              ...IEND.B`.
mgarcia@nightmare:~/mgarcia/Downloads$
```

Para el editor de código, en este caso yo usaré vim
```
vim pico_img.jpg
/pico
<CR>
```

Después podemos observar que en la última linea se encuentra la bandera que estamos buscando

## Bandera
picoCTF{s0_m3ta_d8944929}

## Notas

## Referencias
