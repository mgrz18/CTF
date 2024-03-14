## Objetivo
We found this file. Recover the flag.
https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery

## Solución
En este reto, la solución bastó con corregir los encabezados de el archivo, como podemos observar, algunos de los chunks contenidos están relacionados con una imagen, por ejemplo sRGB que nos indica el espacio de color en el que está trabajando la "imagen", esto nos comienza a dar indicios de que efectivamente es una imagen, y después de estos, gAMA y PHYs.

Comenzando a editar el encabezado, lo primero que hay que corregir es la firma inicial
```
8950 4e47 0d0a 1a0a 0000 000d 4948 4452
```
Que es la firma que de ley está contenida en todos los PNG, después corregir IHDR corregir IDAT, y eliminar los bytes que están antes de PHYs y también después. esto nos bastaría para por último cambiar la extensión de nuestro archivo a PNG y obtener la bandera


```bash
mgarcia@nightmare ~/mgarcia/Desktop
 % xxd ~/mgarcia/Downloads/mystery | head
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
mgarcia@nightmare ~/mgarcia/Desktop
 % xxd mystery | head
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 0000 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f000 00ff a549 4441 5478 5eec bd3f  R$.....IDATx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
mgarcia@nightmare ~/mgarcia/Desktop
 %

```
## Bandera

## Notas

## Referencias