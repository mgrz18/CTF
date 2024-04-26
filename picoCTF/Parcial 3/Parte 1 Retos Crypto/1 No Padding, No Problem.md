## Objetivo
Oracles can be your best friend, they will decrypt anything, except the flag's ciphertext. How will you break it? Connect with nc mercury.picoctf.net 60368.

## Pistas
- What can you do with a different pair of ciphertext and plaintext? What if it is not so different after all...

## Solución
Este código nos solicita conectarnos a través de netcat a un servidor remoto que nos va a poner una serie de pruebas para encotnrar la bandera, todos estos retos relacionados con RSA básico.

El primer acercamiento con la conexión remota se vería de esta manera
```powershell
C:\Users\mgarcia>ncat mercury.picoctf.net 60368
Welcome to the Padding Oracle Challenge
This oracle will take anything you give it and decrypt using RSA. It will not accept the ciphertext with the secret message... Good Luck!


n: 110465056308628058826941836426387002364202175335409304664456936320883446639395242975361950284349928261470235975461201265978361165799287215396229951711264799576513034609041839299912234947901994393202174008619184013490588810379220459328251567052390228512423881032942378102939975474010898459605515861436602999483
e: 65537
ciphertext: 95993485174331363093309976948485734539722066034846016059191588476727446134876444582122641104266676407685099664965235433397980076776872094625468857504894670562038843992602438004004344304356696784062403879128760681678673478476272863038175759160457502047911454017094947765465902926722410842072653742512110147973
```

Anteriormente habíamos automatizado un proceso muy parecido, por lo que, volveremos a hacer lo mismo para poder solucionar este reto...
```python
from pwn import *
import binascii

r = remote("mercury.picoctf.net", 60368)

# Recibir valores del servidor
print(r.recvuntil(b"n:"))
n = int(r.recvline().strip())
print(n)

print(r.recvuntil(b"e:"))
e = int(r.recvline().strip())
print(e)

print(r.recvuntil(b"ciphertext:"))
c = int(r.recvline().strip())
print(c)

print(r.recvuntil(b"to decrypt:"))

# Calcular el mensaje cifrado
encrypted_message = pow(2, e, n) * c

# Enviar el mensaje cifrado al servidor (convertido a bytes)
r.sendline(str(encrypted_message).encode())

print(r.recvuntil(b"Here you go:"))
p2 = int(r.recvline().strip())
print(p2)

# Decodificar el mensaje descifrado y mostrarlo
decrypted_message = p2 // 2
hex_message = "{:x}".format(decrypted_message)
print(binascii.unhexlify(hex_message))

```
Y con esto obtendríamos la bandera directamente

## Notas

## Referencias
