## Objetivo
Find the flag in this picture. https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png

## Solución
Podemos usar la herramienta _xxd_ que permite ver cuál es el contenido hexadecimal de un archivo, en este caso primero intenté resolver el reto utilizando la herramienta hexiftool porque el título era So Meta, pensando en que la bandera estaría dentro de los metadatos de la foto, y así es, pero al revisarla de nuevo con un editor hexadecimal, me doy cuenta que al igual que en el anterior reto, la bandera se encuentra al final de los bytes de la imagen, lo que nos da paso a dos posibles soluciones

**En el apartado artist**
```
C:\Users\mgarcia\Downloads>"exiftool(-k).exe" pico_img.png
ExifTool Version Number         : 12.78
File Name                       : pico_img.png
Directory                       : .
File Size                       : 109 kB
Zone Identifier                 : Exists
File Modification Date/Time     : 2024:03:10 21:24:46-06:00
File Access Date/Time           : 2024:03:10 21:24:47-06:00
File Creation Date/Time         : 2024:03:10 21:24:46-06:00
File Permissions                : -rw-rw-rw-
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 600
Image Height                    : 600
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B
Document ID                     : xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B
Derived From Instance ID        : xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B
Derived From Document ID        : xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B
Warning                         : [minor] Text/EXIF chunk(s) found after PNG IDAT (may be ignored by some readers)
Artist                          : picoCTF{s0_m3ta_d8944929}
Image Size                      : 600x600
Megapixels                      : 0.360
-- press ENTER --


C:\Users\mgarcia\Downloads>nvim pico_img.png
```

**Con el editor hexadecimal**
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

## Notas

## Referencias
