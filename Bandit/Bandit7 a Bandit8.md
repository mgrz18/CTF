### Bandit7 -> Bandit8

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt junto a la palabra millionth
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
- Usuario: bandit7
### Solución

```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
bandit7@bandit:~$
```

### Notas adicionales
El comando grep por si solo puede mostrarnos la línea que contiene la palabra que nosotros estamos buscando, pero si el requerimiento solicita mostrar la siguiente línea a la que encontramos, podemos usar el argumento A seguido del numero de líneas que queremos que nos muestre el resultado de la búsqueda.

>
OPTIONS
       -A NUM, --after-context=NUM
              Print NUM lines of trailing context after matching lines.  Places a line containing -- between contiguous groups of matches.
       -B NUM, --before-context=NUM
              Print NUM lines of leading context before matching lines.  Places a line containing -- between contiguous groups of matches.
       -C NUM, --context=NUM
              Print NUM lines of output context.  Places a line containing -- between contiguous groups of matches.



### Referencias