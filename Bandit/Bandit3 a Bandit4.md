### Bandit3 -> Bandit4

### Objetivo
La contraseña para el siguiente nivel se almacena en un archivo oculto en el directorio interno.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
- Usuario: bandit3
### Solución

```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
bandit3@bandit:~/inhere$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit3@bandit:~/inhere$
```

### Notas adicionales

### Referencias