### Objetivo
Iniciar sesión en bandit26 desde bandit25 debería ser bastante fácil... El shell para el usuario bandit26 no es /bin/bash, sino algo más. Descubra qué es, cómo funciona y cómo salir de él.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
- Usuario: bandit25
### Solución

```bash
:shell
[No write since last change]
bandit26@bandit:~$
bandit26@bandit:~$
bandit26@bandit:~$
bandit26@bandit:~$
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
bandit26@bandit:~$
```

### Notas adicionales

Cuando uno minimiza lo suficiente la terminal, se puede hacer que el comando more no sea cerrado, esto permite no cerrar nuestra conexión, además el comando more permite ejecutar vim dentro de el, lo que ahora si permite modificar la shell.

Vim utiliza el comando SET para establecer preferencias del usuario, pero también nos permite establecer una shell personalizada, lo que nos permite establecer la shell como set shell=/bin/bash y consultar nuestra contraseña desde ``/etc/bandit_pass/bandit26

### Referencias
