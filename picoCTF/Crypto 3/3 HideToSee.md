## Objetivo
How about some hide and seek heh? Look at this image [here](https://artifacts.picoctf.net/c/236/atbash.jpg).

## Pistas
- Download the image and try to extract it.

## Solución
Primero vamos a decifrar el contenido del cifrado con la herramienta steghide
```zsh
mrfear@nightmare:~/winhome/Desktop$ steghide --extract -sf atbash.jpg
Enter passphrase:
wrote extracted data to "encrypted.txt".
mrfear@nightmare:~/winhome/Desktop$ cat encrypted.txt
krxlXGU{zgyzhs_xizxp_zx751vx6}
mrfear@nightmare:~/winhome/Desktop$
```

Después el contenido lo pasamos con alguna página para decifrar en modo atbash y listo.

## Notas

## Referencias
