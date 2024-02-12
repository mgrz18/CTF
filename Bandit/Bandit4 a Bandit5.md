### Bandit4 -> Bandit5

### Objetivo
La contraseña para el siguiente nivel se almacena en el único archivo legible por humanos en el directorio interno. Consejo: si tu terminal está estropeado, prueba el comando “reset”.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
- Usuario: bandit4
### Solución

```bash
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ find . -type f -exec file {}
find: missing argument to `-exec'
bandit4@bandit:~/inhere$ find . -type f -exec file {} +
./-file01: data
./-file02: data
./-file08: data
./-file06: data
./-file00: data
./-file04: data
./-file05: data
./-file07: ASCII text
./-file03: data
./-file09: data
bandit4@bandit:~/inhere$
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
bandit4@bandit:~/inhere$
```

### Notas adicionales

### Referencias