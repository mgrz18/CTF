## Objetivo
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?

## Solución

```bash
mrfear@nightmare ~/picoCTF % wget https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
--2024-02-26 20:02:03--  https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: ‘strings’

strings                       100%[=================================================>] 757.84K  2.60MB/s    in 0.3s

2024-02-26 20:02:03 (2.60 MB/s) - ‘strings’ saved [776032/776032]

mrfear@nightmare ~/picoCTF % ls
strings
mrfear@nightmare ~/picoCTF % strings strings > convertido.txt
mrfear@nightmare ~/picoCTF % cat convertido.txt | grep pico
picoCTF{5tRIng5_1T_7f766a23}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias