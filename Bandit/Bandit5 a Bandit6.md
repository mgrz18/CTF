### Bandit5 -> Bandit6

### Objetivo
La contraseña para el siguiente nivel se almacena en un archivo en algún lugar del directorio interno y tiene todas las siguientes propiedades:

     legible por humanos
     1033 bytes de tamaño
     no ejecutable
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
- Usuario: bandit5
### Solución

```bash
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
bandit5@bandit:~/inhere$
```

### Notas adicionales

### Referencias