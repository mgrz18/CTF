## Objetivo
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell. [Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)

## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/34/runme.py
--2024-02-26 20:34:47--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: ‘runme.py’

runme.py                      100%[=================================================>]     270  --.-KB/s    in 0s

2024-02-26 20:34:47 (184 MB/s) - ‘runme.py’ saved [270/270]

mrfear@nightmare ~/picoCTF % ls
runme.py
mrfear@nightmare ~/picoCTF % python3 runme.py
picoCTF{run_s4n1ty_run}
mrfear@nightmare ~/picoCTF %
```

## Notas

Este script estuvo bastante sencillo, solo había que ejecutar el código de python
## Referencias