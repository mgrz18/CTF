## Objetivo
I wonder what this really is... [enc](https://mercury.picoctf.net/static/a757282979af14ab5ed74f0ed5e2ca95/enc)

''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])

## Pistas
- You may find some decoders online

## Solución
La solución está dentro de este código:

```python
enc = '灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彤㔲挶戹㍽'

flag = ''

for i in range(len(enc)):
    flag += chr(ord(enc[i]) >> 8)
    flag += chr(ord(enc[i]) - (ord(flag[-1]) << 8))

print(flag)
```
En este código se está revirtiendo la instrucción mencionada anteriormente como parte de la descripción del reto, algo que hay que tomar en cuenta es que hay que utilizar un visor compatible con el codificado de texto UTF-8 para poder visualizar los caracteres, de otra forma, no será posible resolver este reto.


```powershell

```

## Notas

## Referencias
