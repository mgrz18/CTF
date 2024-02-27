## Objetivo
Fix the syntax error in the Python script to print the flag. [Download Python script](https://artifacts.picoctf.net/c/4/fixme2.py)

## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/4/fixme2.py
--2024-02-26 20:06:18--  https://artifacts.picoctf.net/c/4/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.64, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: ‘fixme2.py’

fixme2.py                     100%[=================================================>]   1.00K  --.-KB/s    in 0s

2024-02-26 20:06:19 (3.06 MB/s) - ‘fixme2.py’ saved [1029/1029]

mrfear@nightmare ~/picoCTF % python3 fixme2.py
  File "/home/mrfear/picoCTF/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
mrfear@nightmare ~/picoCTF % vim fixme2.py
mrfear@nightmare ~/picoCTF % python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
mrfear@nightmare ~/picoCTF %
```

## Notas

Solo se requirió cambiar el flag = "" a flag == ""
## Referencias