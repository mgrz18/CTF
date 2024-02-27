## Objetivo
Fix the syntax error in this Python script to print the flag. [Download Python script](https://artifacts.picoctf.net/c/27/fixme1.py)
## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/27/fixme1.py
--2024-02-26 19:51:14--  https://artifacts.picoctf.net/c/27/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.61, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: ‘fixme1.py’

fixme1.py                     100%[=================================================>]     837  --.-KB/s    in 0s

2024-02-26 19:51:14 (4.65 MB/s) - ‘fixme1.py’ saved [837/837]

mrfear@nightmare ~/picoCTF % python3 fixme1.py
  File "/home/mrfear/picoCTF/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
mrfear@nightmare ~/picoCTF % vim fixme1.py
mrfear@nightmare ~/picoCTF % vim fixme1.py
mrfear@nightmare ~/picoCTF % vim fixme1.py
mrfear@nightmare ~/picoCTF % python3 fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_182342f7}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias