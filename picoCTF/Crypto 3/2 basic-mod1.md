## Objetivo
We found this weird message being passed around on the servers, we think we have a working decryption scheme. Download the message [here](https://artifacts.picoctf.net/c/129/message.txt). Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore. Wrap your decrypted message in the picoCTF flag format (i.e. picoCTF{decrypted_message})

## Pistas
- Do you know what mod 37 means?
- mod 37 means modulo 37. It gives the remainder of a number after being divided by 37.

## Solución
Primero hacemos un cat al archivo message.txt
```
C:\Users\mgarcia\Desktop>type message.txt
350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213
C:\Users\mgarcia\Desktop>
```

Ejecutamos el script de python en el mismo directorio del archivo message.txt
```python
datos = open("message.txt").read().split()
flag=""
c=""
for n in datos:
    i = int(n) % 37
    if i >= 0 and i <= 25:
        c = chr(i+65)
    elif i >= 26 and i < 35:
        c = chr(i+22)
    elif i == 36:
        c = "_"
    flag = flag + c
print(flag)
```

## Notas

## Referencias
