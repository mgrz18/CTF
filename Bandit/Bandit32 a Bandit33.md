### Objetivo
Después de todo este tema con git, es hora de otro escape. ¡Buena suerte!
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
- Usuario: bandit32
### Solución

```bash
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> sh
sh: 1: SH: Permission denied
>> exit
sh: 1: EXIT: Permission denied
>> bash
sh: 1: BASH: Permission denied
>> /bin/bash
sh: 1: /BIN/BASH: not found
>> help
sh: 1: HELP: Permission denied
>> $0
$ ls
uppershell
$ cat upershell
cat: upershell: No such file or directory
$ ls
uppershell
$ whoami
bandit33
$ /bin/bash
bandit33@bandit:~$ cat /etc/bandit_pass/bandit33
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
bandit33@bandit:~$
```

### Notas adicionales



### Referencias
