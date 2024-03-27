## Objetivo
Files can always be changed in a secret way. Can you find the flag? cat.jpg

## Pistas
- Look at the details of the file
- Make sure to submit the flag as picoCTF{XXXXX}

## Solución
Si nosotros miramos los metadatos obtenemos:
```cmd
C:\Users\mgarcia\Downloads>exiftool cat.jpg
ExifTool Version Number         : 12.78
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
Zone Identifier                 : Exists
File Modification Date/Time     : 2024:03:26 21:33:42-06:00
File Access Date/Time           : 2024:03:26 21:33:42-06:00
File Creation Date/Time         : 2024:03:26 21:33:41-06:00
File Permissions                : -rw-rw-rw-
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```

Si nos enfocamos en decodificar el campo correspondiente a la licencia obtenemos nuestra bandera


```bash
mgarcia@nightmare ~/mgarcia/Downloads
 % echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}%
```

## Notas adicionales
## Referencias