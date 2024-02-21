### Objetivo
Hay un binario setuid en el directorio de inicio que hace lo siguiente: establece una conexión con el host local en el puerto que especifica como argumento de la línea de comando. Luego lee una línea de texto de la conexión y la compara con la contraseña del nivel anterior (bandit20). Si la contraseña es correcta, transmitirá la contraseña para el siguiente nivel (bandit21).

NOTA: Intente conectarse a su propio demonio de red para ver si funciona como cree
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
- Usuario: bandit20
### Solución

```bash
bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
bandit20@bandit:~$ nc -lnvp 56781 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
[1] 3064855
bandit20@bandit:~$ Listening on 0.0.0.0 56781

bandit20@bandit:~$ jobs
[1]+  Running                 nc -lnvp 56781 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
bandit20@bandit:~$ ./suconnect 56781
Connection received on 127.0.0.1 47264
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
bandit20@bandit:~$
```

### Notas adicionales


### Referencias
