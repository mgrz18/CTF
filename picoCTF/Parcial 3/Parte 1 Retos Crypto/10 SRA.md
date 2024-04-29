## Objetivo
I just recently learnt about the SRA public key cryptosystem... or wait, was it supposed to be RSA? Hmmm, I should probably check...
Additional details will be available after launching your challenge instance.

## Pistas
(None)

## Solución
Vamos a utilizar el código proporcionado llamado chal.py, pero corregido a lo que de verdad está buscando resolver el reto, quedando así:
```python
from Crypto.Util.number import isPrime, long_to_bytes
from string import ascii_letters, digits
from itertools import combinations
from sympy import divisors
from math import log2

anger = int(input("anger = "))
envy = int(input("envy = "))
sloth = 65537

ds = divisors(envy * sloth - 1)
primes = [x + 1 for x in ds if isPrime(x + 1)]
correct_size_primes = [x for x in primes if log2(x) // 1 == 127]

valid_plaintexts = []
charset = ascii_letters + digits
for p, q in combinations(correct_size_primes, 2):
    try:
        s = long_to_bytes(pow(anger, envy, p * q)).decode("ascii")
        if all([c in charset for c in s]):
            valid_plaintexts.append(s)
    except Exception:
        continue

print(valid_plaintexts)
```

Donde la ejecución del código y del reto se verían de la siguiente forma.
```powershell
C:\Users\mgarcia\Desktop\ctf>ncat saturn.picoctf.net 54700
anger = 46390800763544930736700170661463720160209822175372651655602195464710651054637
envy = 33069474929757624307540487509432186917414609007785419966180784931003272514865
vainglory?
> fWMXBCG5LQAFwP66
fWMXBCG5LQAFwP66
Conquered!
picoCTF{7h053_51n5_4r3_n0_m0r3_38268294}
```

```bash
mrfear@nightmare ~/winhome/Desktop/ctf % python sra.py
anger = 46390800763544930736700170661463720160209822175372651655602195464710651054637
envy = 33069474929757624307540487509432186917414609007785419966180784931003272514865
['fWMXBCG5LQAFwP66']
mrfear@nightmare ~/winhome/Desktop/ctf %
```

## Notas

## Referencias
