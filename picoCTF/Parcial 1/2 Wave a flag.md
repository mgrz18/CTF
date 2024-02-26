## Objetivo
Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm) has extraordinarily helpful informaºººtion...

---
## Solución

```bash
mrfear@nightmare ~ % ls
c  home  zphisher
mrfear@nightmare ~ % wget https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm
--2024-02-26 12:28:35--  https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: ‘warm’

warm                          100%[=================================================>]  10.68K  --.-KB/s    in 0s

2024-02-26 12:28:37 (76.2 MB/s) - ‘warm’ saved [10936/10936]

mrfear@nightmare ~ % ls
c  home  warm  zphisher
mrfear@nightmare ~ % ./warm
zsh: permission denied: ./warm
mrfear@nightmare ~ % chmod +x warm
mrfear@nightmare ~ % ./warm
Hello user! Pass me a -h to learn what I can do!
mrfear@nightmare ~ % ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_f0668f62}
mrfear@nightmare ~ %

```

## Notas
El comando wget sirve para descargar archivos de manera remota
## Referencias