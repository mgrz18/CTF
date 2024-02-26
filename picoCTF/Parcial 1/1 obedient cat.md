## Objetivo
This file has a flag in plain sight (aka "in-the-clear").
## Solución

```bash
gr18-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag
--2024-02-26 18:20:07--  https://mercury.picoctf.net/static/0e428b2db9788d31189329bed089ce98/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: 'flag'

flag                                        100%[===========================================================================================>]      34  --.-KB/s    in 0s      

2024-02-26 18:20:07 (16.2 MB/s) - 'flag' saved [34/34]

gr18-picoctf@webshell:~$ ls
README.txt  flag
gr18-picoctf@webshell:~$ cat flag 
picoCTF{s4n1ty_v3r1f13d_2fd6ed29}
gr18-picoctf@webshell:~$ 
```

## Notas
El comando wget sirve para descargar archivos de manera remota
## Referencias