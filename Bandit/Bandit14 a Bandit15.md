### Objetivo
La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30000 en localhost.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
- Usuario: bandit14
### Solución

```bash
bandit14@bandit:~$ nc localhost 4040
^C
bandit14@bandit:~$ nc -lnvp 9000
Listening on 0.0.0.0 9000
Connection received on 127.0.0.1 46584
Hola
Quien eres
Tu conciencia
no
un ratero
^C
bandit14@bandit:~$ netstat -anpt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
netstat: no support for `AF INET (tcp)' on this system.
tcp6       0      0 :::31790                :::*                    LISTEN      -
tcp6       0      0 :::30001                :::*                    LISTEN      -
tcp6       0      0 :::30002                :::*                    LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
tcp6       0      0 :::2220                 :::*                    LISTEN      -
tcp6       0      0 :::2231                 :::*                    LISTEN      -
tcp6       0      0 :::2230                 :::*                    LISTEN      -
tcp6       0      0 :::2232                 :::*                    LISTEN      -
tcp6       0      0 :::31518                :::*                    LISTEN      -
bandit14@bandit:~$ nmap localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2024-02-19 19:07 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00014s latency).
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
5120/tcp  open  barracuda-bbs
8000/tcp  open  http-alt
30000/tcp open  ndmps

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
bandit14@bandit:~$ nc localhost 30000
^C
bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

^C
bandit14@bandit:~$
```

### Notas adicionales


### Referencias
