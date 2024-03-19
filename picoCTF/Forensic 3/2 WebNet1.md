## Objetivo
We found this packet capture and key. Recover the flag.

## Solución
Este nivel es bastante parecido al anterior, hay que abrir una captura con wireshark y añadir una llave para poder desencriptar el tráfico capturado, la diferencia es que aquí no vamos a encontrar la palabra picoCTF por ningún lado, esta vez está oculta dentro de una imagen transferida durante la captura, a la que si le hacemos un dump hexadecimal, daremos con la bandera


```powershell
C:\Users\mgarcia\Downloads>xxd vulture.jpg
00000000: ffd8 ffe0 0010 4a46 4946 0001 0100 0001  ......JFIF......
00000010: 0001 0000 ffe1 0082 4578 6966 0000 4d4d  ........Exif..MM
00000020: 002a 0000 0008 0005 011a 0005 0000 0001  .*..............
00000030: 0000 004a 011b 0005 0000 0001 0000 0052  ...J...........R
00000040: 0128 0003 0000 0001 0001 0000 013b 0002  .(...........;..
00000050: 0000 001f 0000 005a 0213 0003 0000 0001  .......Z........
00000060: 0001 0000 0000 0000 0000 0001 0000 0001  ................
00000070: 0000 0001 0000 0001 7069 636f 4354 467b  ........picoCTF{
00000080: 686f 6e65 792e 726f 6173 7465 642e 7065  honey.roasted.pe
00000090: 616e 7574 737d 0000 ffe2 021c 4943 435f  anuts}......ICC_
000000a0: 5052 4f46 494c 4500 0101 0000 020c 6c63  PROFILE.......lc
```

## Notas

## Referencias

