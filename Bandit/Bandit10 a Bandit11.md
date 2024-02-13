### Bandit10 -> Bandit11

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt, que contiene datos codificados en base64.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
- Usuario: bandit10
### Solución

```bash
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
bandit10@bandit:~$ echo -n 'VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==' | base64 --decode
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
bandit10@bandit:~$
```

### Notas adicionales
El argumendo _**decode**_ nos permite decifrar el código encriptado en base64

### Referencias
https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-base64-encode-and-decode-from-command-line/