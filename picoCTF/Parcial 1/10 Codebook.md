## Objetivo
Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/3/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/3/codebook.txt)
## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/3/code.py
--2024-02-26 19:44:18--  https://artifacts.picoctf.net/c/3/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: ‘code.py’

code.py                       100%[=================================================>]   1.25K  --.-KB/s    in 0s

2024-02-26 19:44:18 (21.4 MB/s) - ‘code.py’ saved [1278/1278]

mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/3/codebook.txt
--2024-02-26 19:44:24--  https://artifacts.picoctf.net/c/3/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: ‘codebook.txt’

codebook.txt                  100%[=================================================>]      27  --.-KB/s    in 0s

2024-02-26 19:44:25 (238 KB/s) - ‘codebook.txt’ saved [27/27]

mrfear@nightmare ~/picoCTF % ls
codebook.txt  code.py
mrfear@nightmare ~/picoCTF % python3 code.py
picoCTF{c0d3b00k_455157_197a982c}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias