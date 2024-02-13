### Bandit11 -> Bandit12

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt, donde todas las letras minúsculas (a-z) y mayúsculas (A-Z) se han rotado 13 posiciones.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
- Usuario: bandit11
### Solución

```bash
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
bandit11@bandit:~$ tr
tr: missing operand
Try 'tr --help' for more information.
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
bandit11@bandit:~$

```

### Notas adicionales
El comando _**tr**_ traduce caracteres de un conjunto a otro. En los comandos proporcionados, _**A-Za-z**_ representa todas las letras mayúsculas y minúsculas del alfabeto. _**N-ZA-Mn-za-m**_ representa los caracteres rotados, que realiza efectivamente la operación rot13.

### Referencias
https://askubuntu.com/questions/1085069/how-can-i-decode-a-file-where-each-letter-has-been-replaced-with-the-letter-13-l