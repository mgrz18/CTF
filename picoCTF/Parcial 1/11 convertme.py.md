## Objetivo
Run the Python script and convert the given number from decimal to binary to get the flag. [Download Python script](https://artifacts.picoctf.net/c/22/convertme.py)
## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://artifacts.picoctf.net/c/22/convertme.py
--2024-02-26 19:46:35--  https://artifacts.picoctf.net/c/22/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: ‘convertme.py’

convertme.py                  100%[=================================================>]   1.16K  --.-KB/s    in 0s

2024-02-26 19:46:35 (6.00 MB/s) - ‘convertme.py’ saved [1189/1189]

mrfear@nightmare ~/picoCTF % ls
convertme.py
mrfear@nightmare ~/picoCTF % python3 convertme.py
If 17 is in decimal base, what is it in binary base?
Answer: 10001
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias