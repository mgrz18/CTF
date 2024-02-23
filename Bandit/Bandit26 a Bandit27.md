### Objetivo
¡Buen trabajo consiguiendo un caparazón! ¡Ahora date prisa y consigue la contraseña de bandit27!
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
- Usuario: bandit26
### Solución

```bash
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ ls -la
total 44
drwxr-xr-x  3 root     root      4096 Oct  5 06:19 .
drwxr-xr-x 70 root     root      4096 Oct  5 06:20 ..
-rwsr-x---  1 bandit27 bandit26 14876 Oct  5 06:19 bandit27-do
-rw-r--r--  1 root     root       220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root      3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root       807 Jan  6  2022 .profile
drwxr-xr-x  2 root     root      4096 Oct  5 06:19 .ssh
-rw-r-----  1 bandit26 bandit26   258 Oct  5 06:19 text.txt
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
bandit26@bandit:~$
```

### Notas adicionales



### Referencias
