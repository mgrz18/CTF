### Objetivo
La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30001 en localhost mediante cifrado SSL.

Nota útil: ¿Obtienes “HEARTBEATING” y “Read R BLOCK”? Utilice -ign_eof y lea la sección "COMANDOS CONECTADOS" en la página de manual. Junto a 'R' y 'Q', el comando 'B' también funciona en esta versión de ese comando...
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
- Usuario: bandit15
### Solución

```bash
bandit15@bandit:~$ nmap localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2024-02-19 19:17 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
30000/tcp open  ndmps

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Feb 18 10:54:16 2024 GMT
verify return:1
depth=0 CN = localhost
notAfter=Feb 18 10:54:16 2024 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Feb 18 10:53:16 2024 GMT; NotAfter: Feb 18 10:54:16 2024 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEcjY6OTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjQwMjE4MTA1MzE2WhcNMjQwMjE4MTA1NDE2WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCz
TX1NLedZhpQfXiWbWWD2BlNYjANpj+TnzUOI9ZbKJnOQJAbFfWZLA6No7XOStgje
+RPIoAHrX42G95VDfWtRms+qCsCTlUaS9291dZJQ3iOjBIE+PvmRcGdUlFJXDYa6
E61L2DKLbb8YSAnSuUPG3K7CtdxJpA5DpCBCmHEA9t5gZ5HGo9Gt9Kay9lhApX78
ocytwwHG15LplXI6LQB3ykhyCAcfljR3azd90T83dz7kLyM7yIMt60k1kemuX6RW
qSvkCvxmckRFoQPjwKZUopGLlhcC58Kb2xlwEGK+9j/ibBRkmEdBkOOeb5pJol7K
Wkd9LdG0nTWrggni7EKbAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQCA
j53OECoyjZMkHINZj35xk2kKQc9Jj9XjoCE0HlooUWd1ETik/2TkIbdWenozDrgH
10Jqmu/zAEhQkfFALBXCR7Vo0319yvR3rlnC2TdzMeBeUQ/n6ivPsCCL6SF8UTWT
XZJoTEfmp+Ma4zup/mEs23uO/FQ0J3LmSgICtXzPCA09M/ffj2UgTENdTHDltQxl
nQpzF+U40+bg/2PQ83XOTQJbZVbU2FnP/MitSYycxemLJXzbdsIxQhQy0VmTY73E
ZFemHVTbzEzcsCJRak4AyPZ9Zpi2uozHA8r1PqtnDzsN5FBFwuJxCuc+F8QeHh9e
QoyfsotkA6BO0LBqWNvE
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 21F7623A99F4126B5E9DAD7E6E96C2BC4A69D40B4C3EF43FC918302A98AB14D1
    Session-ID-ctx:
    Resumption PSK: A409A693F76709C9DDA290B0ADDB457CD8BF4BFF18CE16662B69CCD5373AC18E50F57981A283D8640195162022C41D4E
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - dc 1b 67 7e 6b 49 ec f9-e1 0a 8a 6e cb ac b4 e6   ..g~kI.....n....
    0010 - ab 4c 96 5b 42 4d 4b 6e-5a 48 39 72 53 b0 a7 31   .L.[BMKnZH9rS..1
    0020 - 94 dd 3f 5a 2c 05 03 ae-a4 e0 96 51 6a 3b 9b 72   ..?Z,......Qj;.r
    0030 - 2a 92 f5 c2 f9 02 4a 00-8a 5b ef 4d 9e e4 6e d5   *.....J..[.M..n.
    0040 - 7e 23 23 6d 87 cb 70 49-72 3e 92 bf 60 4a 1d 6c   ~##m..pIr>..`J.l
    0050 - 3c 75 03 3e f6 9a 83 8f-c0 64 3a 2f 92 d6 a1 6a   <u.>.....d:/...j
    0060 - f0 34 17 27 ff 82 19 6e-5a c2 79 20 97 4d c1 92   .4.'...nZ.y .M..
    0070 - db 60 4a 80 28 3c ae 18-bd 92 40 72 26 5b 28 15   .`J.(<....@r&[(.
    0080 - 47 95 f7 bb 34 cd 9f 53-1c fa 9f 3a ae 66 de 34   G...4..S...:.f.4
    0090 - 2f a1 7f b8 a8 f4 45 35-4f dc 0a 84 8b d0 cc 51   /.....E5O......Q
    00a0 - ef 1c 4f 93 5c 6e 13 bd-e4 61 c7 7e 98 06 de f6   ..O.\n...a.~....
    00b0 - 85 f4 db d8 5e 85 ad b0-4b 98 46 23 34 f1 78 f0   ....^...K.F#4.x.
    00c0 - 4e 21 0b 6f 04 a7 1c 19-5a d3 13 a5 08 bd 43 f8   N!.o....Z.....C.

    Start Time: 1708370613
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 739A235A2ACCB5AAA2FD665D087E42A1A696A370DDCFD98F2E39ACBB405E0DB0
    Session-ID-ctx:
    Resumption PSK: 5411B8D2B4224C83100C120C2E9E3FABCBDACED95D910EE7E635F0FBB0F2CD74F9F9A05B709D54C8DBAF9E2C9905D68A
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - dc 1b 67 7e 6b 49 ec f9-e1 0a 8a 6e cb ac b4 e6   ..g~kI.....n....
    0010 - 3e fb d7 01 87 1f aa 9f-d5 c9 a5 e5 ea 74 22 51   >............t"Q
    0020 - 4d 62 24 ee 5f 71 ce c6-f8 7b 08 4b bf a4 45 22   Mb$._q...{.K..E"
    0030 - 46 2c cd fa bd cc 72 fc-4e a3 2b 91 e3 6c 57 89   F,....r.N.+..lW.
    0040 - 66 ec 4b 2e f3 44 36 37-ab a0 46 6b 75 3d 7c f3   f.K..D67..Fku=|.
    0050 - 55 16 17 c9 68 a4 3d 47-02 d6 f7 4e 8b 9c ec f9   U...h.=G...N....
    0060 - 15 22 54 d4 1d 2e ac 5d-8d ee 69 6b 70 d0 f4 58   ."T....]..ikp..X
    0070 - 07 d2 3a 72 9d d3 27 8d-59 06 0d 80 c1 ba 0d 74   ..:r..'.Y......t
    0080 - d3 b1 23 e0 ff 2b fe 83-0f e3 e8 0c c5 f9 cf 58   ..#..+.........X
    0090 - 92 21 0c aa 9c 08 87 cd-20 91 22 e8 8b e0 b4 2e   .!...... .".....
    00a0 - 8e 4b dc 79 d9 10 d1 39-75 48 a3 ea cc d0 11 f4   .K.y...9uH......
    00b0 - 30 ff 03 7d 8b 04 c0 83-b5 57 65 d8 5c 61 4f e8   0..}.....We.\aO.
    00c0 - 11 1b 8e db ee 30 41 16-0b a5 9d c6 8f 96 f5 ed   .....0A.........

    Start Time: 1708370613
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
bandit15@bandit:~$
```

### Notas adicionales


### Referencias
