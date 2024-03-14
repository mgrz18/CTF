## Objetivo
I stopped using YellowPages and moved onto WhitePages... but the page they gave me is all blank!

## Solución
El código parece no contener absolutamente nada hasta que con un editor hexadecimal empezamos a revisar el archivo más a detalle y nos damos cuenta de que, dentro de todo el archivo se repiten dos patrones
- E2 80 83
- 20
Entonces podemos asumir que se trata de algún mensaje cifrado en binario, que podemos decodificar con el siguiente código escrito en python por hackadvisermx

```python
from pwn import *

file = open('whitepages.txt', 'rb')
data = bytearray(file.read())
data = data.replace(b'\xe2\x80\x83',b'0')
data = data.replace(b'\x20',b'1')
data = data.decode('ascii')
data = unbits(data)

print(data)
```

```powershell
C:\Users\mgarcia\Desktop>python decoder.py
b'\n\t\tpicoCTF\n\n\t\tSEE PUBLIC RECORDS & BACKGROUND REPORT\n\t\t5000 Forbes Ave, Pittsburgh, PA 15213\n\t\tpicoCTF{not_all_spaces_are_created_equal_7100860b0fa779a5bd8ce29f24f586dc}\n\t\t'

C:\Users\mgarcia\Desktop>

```
## Bandera

## Notas

## Referencias