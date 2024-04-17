## Objetivo
In RSA, a small e value can be problematic, but what about N? Can you decrypt this? [values](https://mercury.picoctf.net/static/2604f8b51a5cc62d38a3736938f19cef/values)

## Pistas
Bits are expensive, I used only a little bit over 100 to save money

## Solución
```powershell
Microsoft Windows [Versión 10.0.19045.4291]
(c) Microsoft Corporation. Todos los derechos reservados.

C:\Users\mgarcia>curl https://mercury.picoctf.net/static/2604f8b51a5cc62d38a3736938f19cef/values
Decrypt my super sick RSA:
c: 861270243527190895777142537838333832920579264010533029282104230006461420086153423
n: 1311097532562595991877980619849724606784164430105441327897358800116889057763413423
e: 65537
C:\Users\mgarcia>python
Python 3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()

C:\Users\mgarcia>factordb 1311097532562595991877980619849724606784164430105441327897358800116889057763413423
1955175890537890492055221842734816092141 670577792467509699665091201633524389157003

C:\Users\mgarcia>python
Python 3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> p = 1955175890537890492055221842734816092141
>>> q = 670577792467509699665091201633524389157003
>>> p*q
1311097532562595991877980619849724606784164430105441327897358800116889057763413423
>>> n=p*q
>>> e=65537
>>> c=861270243527190895777142537838333832920579264010533029282104230006461420086153423
>>> tn=(p-1)*(q-1)
>>> d=pow(e,-1,tn)
>>> m=pow(c,d,n)
>>> bytes.fromhex(hex(m)[2:])
b'picoCTF{sma11_N_n0_g0od_13686679}'
>>> exit
Use exit() or Ctrl-Z plus Return to exit
>>> exit()

C:\Users\mgarcia>
```

## Notas

## Referencias
