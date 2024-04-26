## Objetivo
Can you decrypt this [message](https://artifacts.picoctf.net/c/159/cipher.txt)? Decrypt this message using this key "CYLAB".

## Pistas
- https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher

## Solución
Este código consta de un cifrado de tipo Vigenère, con el que para solucionarlo usaré la herramienta [CyberChef](https://cyberchef.org)
```powershell
C:\Users\mgarcia\Desktop\pico>curl -O https://artifacts.picoctf.net/c/159/cipher.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    43  100    43    0     0     97      0 --:--:-- --:--:-- --:--:--    99

C:\Users\mgarcia\Desktop\pico>type cipher.txt
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_f85729e7}
```
[Solución](https://cyberchef.org/#recipe=Vigen%C3%A8re_Decode('CYLAB')&input=cmdub0RWRHtPME5VX1dRM19HMUczTzNUM19BMUFIM1NfZjg1NzI5ZTd9) que demuestra la entrada dentro de CyberChef

## Notas

## Referencias
