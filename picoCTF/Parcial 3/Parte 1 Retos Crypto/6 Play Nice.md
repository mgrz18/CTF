## Objetivo
Not all ancient ciphers were so bad... The flag is not in standard format. nc mercury.picoctf.net 19860 [playfair.py](https://mercury.picoctf.net/static/3f082e143dd5b4ffe1a0aaaf317872b8/playfair.py)

## Pistas

## Solución
Para determinar cuál era el texto desencriptado, primero utilicé un [decodificador](https://www.dcode.fr/playfair-cipher) en línea, al que le modifiqué el parámetro del tamaño del alfabeto de 5X5 a 6X6, ya que el código que nos proporcionaron en python, contenía esa cifra para el tamaño del alfabeto, después introduje el código transformado a letras minúsculas dentro de la conexión remota de netcat para obtener la bandera.

```powershell
C:\Users\mgarcia\Desktop\pico>python -c "print('LHXM62I5LWOI0RLJOR647XQ9WH7WIE'.lower())"
lhxm62i5lwoi0rljor647xq9wh7wie

C:\Users\mgarcia\Desktop\pico>ncat mercury.picoctf.net 19860
Here is the alphabet: lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9
Here is the encrypted message: 1x5hqlod8x7oa88h0de1b5r6xja5sd
What is the plaintext message? lhxm62i5lwoi0rljor647xq9wh7wie
Congratulations! Here's the flag: f391b621282ef5063ab2de93ab9e4bff
^C
C:\Users\mgarcia\Desktop\pico>
```

## Notas
La bandera no requiere el formato picoCTF{}

## Referencias
