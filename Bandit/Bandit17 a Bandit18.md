### Objetivo
Hay 2 archivos en el directorio de inicio: contraseñas.antiguas y contraseñas.nuevas. La contraseña para el siguiente nivel está en contraseñas.nueva y es la única línea que se ha cambiado entre contraseñas.antiguas y contraseñas.nuevas.

NOTA: si has resuelto este nivel y ves "¡Adiós!" al intentar iniciar sesión en bandit18, esto está relacionado con el siguiente nivel, bandit19.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: Llave SSH / VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
- Usuario: bandit17
### Solución

```bash
C:\Users\Miguel García\Desktop>ssh -l bandit17 bandit.labs.overthewire.org -p 2220 -i bandit17.private
bandit17@bandit:~$ cat /etc/bandit_pass/bandit17
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ wc -l passwords.new
100 passwords.new
bandit17@bandit:~$ wc -l passwords.old
100 passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new --color
42c42
< p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
bandit17@bandit:~$
```

### Notas adicionales

Diff -> Sirve para comparar archivos línea por línea
### Referencias
