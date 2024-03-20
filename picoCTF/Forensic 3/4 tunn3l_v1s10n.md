## Objetivo
We found this file. Recover the flag.

## Pistas
Weird that it won't display right...

## Solución
La solución consiste en abrir el archivo con algún editor hexadecimal para darnos cuenta de que este archivo es una imagen BMP, entonces como primer paso podemos darle una extensión .bmp, después verificar los encabezados de un bmp, en mi caso mis ediciones fueron las siguientes.

```powershell
C:\Users\mgarcia\Downloads>xxd tunn3l_v1s10n
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........
```

```powershell
C:\Users\mgarcia\Downloads>xxd tunn3l_v1s10n.bmp
00000000: 424d 8e26 2c00 0000 0000 8a00 0000 7c00  BM.&,.........|.
00000010: 0000 6e04 0000 4803 0000 0100 1800 0000  ..n...H.........
```
Con ayuda de python para determinar a que resolución iba a establecer el BMP
```python
C:\Users\mgarcia>python
Python 3.12.2 (tags/v3.12.2:6abddd9, Feb  6 2024, 21:26:36) [MSC v.1937 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> hex(1134)
'0x46e'
>>> hex(306)
'0x132'
>>> hex(850)
'0x352'
>>> hex(500)
'0x1f4'
>>> hex(700)
'0x2bc'
>>> hex(800)
'0x320'
>>> hex(820)
'0x334'
>>> hex(840)
'0x348'
>>>

Y el editor HxD para windows para manejar el archivo.
```

## Notas

## Referencias