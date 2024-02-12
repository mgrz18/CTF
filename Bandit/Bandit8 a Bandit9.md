### Bandit8 -> Bandit9

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt y es la única línea de texto que aparece solo una vez.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: TESKZC0XvTetK0S9xNwm25STk5iWrBvP
- Usuario: bandit8
### Solución

```bash
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
bandit8@bandit:~$
```

### Notas adicionales

El argumento -u sirve para restringir las palabras a mostrar solo las ocurrencias únicas y repetidas

### Referencias