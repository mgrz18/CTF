## Objetivo
Decrypt this message.
https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext

## Pistas
- caesar cipher tutorial
## Solución
Como primer paso podemos observar que al descargar el archivo ya viene la bandera, pero encriptada en cifrado césar, un algoritmo de cifrado muy parecido al rot13, pero con un desplazamiento diferente, en este caso, en vez de 13 caracteres, 22, en la página de cyberchef podremos decifrar fácilmente el código.

```powershell
C:\Users\mgarcia\Desktop>curl -O https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    35  100    35    0     0    106      0 --:--:-- --:--:-- --:--:--   108

C:\Users\mgarcia\Desktop>type ciphertext
picoCTF{gvswwmrkxlivyfmgsrhnrisegl}
C:\Users\mgarcia\Desktop>
```

## Notas
https://cyberchef.org/#recipe=ROT13(true,true,false,22)&input=Z3Zzd3dtcmt4bGl2eWZtZ3NyaG5yaXNlZ2w

## Referencias
