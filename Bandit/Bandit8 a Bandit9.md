### Bandit8 -> Bandit9

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt y es la única línea de texto que aparece solo una vez.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: zbqXMhsLoFPqc2Mf0TJwI7H6KXp75PSi
- Usuario: bandit8
### Solución

```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
bandit7@bandit:~$ grep -A1 millionth data.txt
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
Roderick's      zbqXMhsLoFPqc2Mf0TJwI7H6KXp75PSi
bandit7@bandit:~$
bandit7@bandit:~$
```

### Notas adicionales



### Referencias