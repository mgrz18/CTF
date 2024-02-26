## Objetivo
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/static)? This [BASH script](https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/ltdis.sh) might help!


## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/static
--2024-02-26 13:03:05--  https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: ‘static’

static                        100%[=================================================>]   8.18K  --.-KB/s    in 0s

2024-02-26 13:03:06 (192 MB/s) - ‘static’ saved [8376/8376]

mrfear@nightmare ~/picoCTF % wget https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/ltdis.sh
--2024-02-26 13:03:11--  https://mercury.picoctf.net/static/0f6ea599582dcce7b4f1ba94e3617baf/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: ‘ltdis.sh’

ltdis.sh                      100%[=================================================>]     785  --.-KB/s    in 0s

2024-02-26 13:03:12 (6.21 MB/s) - ‘ltdis.sh’ saved [785/785]

mrfear@nightmare ~/picoCTF % ls
ltdis.sh  static
mrfear@nightmare ~/picoCTF % chmod +x ltdis.sh
mrfear@nightmare ~/picoCTF % ./ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset
mrfear@nightmare ~/picoCTF % ls
ltdis.sh  static  static.ltdis.strings.txt  static.ltdis.x86_64.txt
mrfear@nightmare ~/picoCTF % cat static.ltdis.strings.txt | grep pico
   1020 picoCTF{d15a5m_t34s3r_6f8c8200}
mrfear@nightmare ~/picoCTF %
```

## Notas
El comando wget sirve para descargar archivos de manera remota
## Referencias