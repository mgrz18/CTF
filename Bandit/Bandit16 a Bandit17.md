### Objetivo
Las credenciales para el siguiente nivel se pueden recuperar enviando la contraseña del nivel actual a un puerto en localhost en el rango 31000 a 32000. Primero averigüe cuál de estos puertos tiene un servidor escuchando en ellos. Luego averigüe cuáles de ellos hablan SSL y cuáles no. Solo hay 1 servidor que le dará las siguientes credenciales, los demás simplemente le enviarán todo lo que les envíe.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: JQttfApK4SeyHwDlI9SXGR50qclOAil1
- Usuario: bandit16
### Solución

```bash
bandit16@bandit:~$ nc -vz localhost 30000-32000 2>&1 grep succ
nc: port number invalid: grep
bandit16@bandit:~$ nc -vz localhost 30000-32000 2>&1 | grep succ
Connection to localhost (127.0.0.1) 30000 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 30001 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 30002 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 31046 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 31518 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 31691 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 31790 port [tcp/*] succeeded!
Connection to localhost (127.0.0.1) 31960 port [tcp/*] succeeded!
bandit16@bandit:~$ nmap localhost -p 30000-33000
Starting Nmap 7.80 ( https://nmap.org ) at 2024-02-21 18:14 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 2993 closed ports
PORT      STATE SERVICE
30000/tcp open  ndmps
30001/tcp open  pago-services1
30002/tcp open  pago-services2
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.18 seconds
bandit16@bandit:~$ nc -vz localhost 30000-32000 2>/dev/null | grep succ
bandit16@bandit:~$ openssl s_client -connect 31046
80DBF0F7FF7F0000:error:8000006F:system library:BIO_connect:Connection refused:../crypto/bio/bio_sock2.c:125:calling connect()
80DBF0F7FF7F0000:error:10000067:BIO routines:BIO_connect:connect error:../crypto/bio/bio_sock2.c:127:
connect:errno=111
bandit16@bandit:~$ openssl s_client -connect localhost:31046
CONNECTED(00000003)
80DBF0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 293 bytes and written 300 bytes
Verification: OK
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
bandit16@bandit:~$ openssl s_client -connect localhost:31518
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Feb 20 17:51:07 2024 GMT
verify return:1
depth=0 CN = localhost
notAfter=Feb 20 17:51:07 2024 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Feb 20 17:50:07 2024 GMT; NotAfter: Feb 20 17:51:07 2024 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIED6TmQjANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjQwMjIwMTc1MDA3WhcNMjQwMjIwMTc1MTA3WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDG
ItRI0YQSg7GaQar1vRzAkcuAUsO/ZdTZtFmzkN6TyBt24ZrKKBWpLll6cDGt6+V/
G4w+kQpc3wRpfihFiudZxYahIsEoMvaSS3VsAKP1oeqOk6ya9l4v7wXZE/HnxmT/
N+rB/Fnpqo4Wxbi+nbIJSPU7xmK5BslH6RsJxveZOWmePnzVSkJbFmuj7EcLuYZV
asT1RoEYjkkNRM1+T7729Rv3ZkCF7S7AIV/9RobP+qUGWaweIcSIK73ZZwySaaYU
q087YDcrl+YteXLFJukqBLiDrl2QeBGjKnJ2JcNfGt8lgUDzGR85rZy/bJZuNNKG
2DIe6zfO4Qtd14aS1Hk1AgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQDF
AbYvgfNCh6RFSe1tNefMqhZoywHtMdo2G1WGxGOgbXG0bJkjQ/BEHMeflkVmpv3A
/DoAGLW/ZO1VBgb9HImrYWDWGiXUo+cJxWiLLW9ewP6l1yCpOjPyT9DPUBzlKMdA
FFI3W0ehvIB6vv2YPvLsbgfDKWO+yh1OPZW+DQ0kAbIRiUlbuQrTYdK4mkckaj7h
oJQ93yBr80uGuErR+unKW2Vj0JI4KxglZVH9ekekbTBxNVqMkpnr2n/eEfnmFRuJ
IlAlXbdIC/5Fo0Llk/sERLUQA6FZ5eqykUvVeoJTj9kodi03AkNL2mxDTy1KaW+B
sPf9vsFkDW8mfXcNDFK2
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
    Session-ID: CFF07B568EEB7F2850A54D9424D5E5F3566191553C0B7CFE1E5FD54F1FE945ED
    Session-ID-ctx:
    Resumption PSK: 6E103830FB7CFF342D1E92F96FD4998A6D7B7E15E22656403136E7B2079EF794376E6837328D752B09478090E8387B31
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 67 62 ad 30 72 ef 35 8b-4b 97 68 8c 1c f3 24 79   gb.0r.5.K.h...$y
    0010 - ce 7e df 84 bf 97 bc 57-84 24 87 3f 4d 89 a1 d6   .~.....W.$.?M...
    0020 - 7c 5d c1 46 04 57 6c 6d-a5 05 54 af 4a 64 99 cb   |].F.Wlm..T.Jd..
    0030 - 5c e4 c4 ae e2 7e 37 4f-18 f3 07 77 cc 6b 7f ac   \....~7O...w.k..
    0040 - bb 54 5f b3 d5 51 c2 83-96 f1 bd e2 f4 e0 38 f9   .T_..Q........8.
    0050 - d4 97 31 1a 43 48 51 81-5e b2 49 d5 68 6f 18 eb   ..1.CHQ.^.I.ho..
    0060 - 49 d9 44 81 16 da ca 71-61 00 cd a5 dd fa 85 64   I.D....qa......d
    0070 - 0b 37 7d 4d c0 72 07 25-6b 53 ae bb 44 10 d0 b3   .7}M.r.%kS..D...
    0080 - a6 9b 66 f6 bf 84 34 46-1f be 73 e3 e9 1d f8 cc   ..f...4F..s.....
    0090 - ba 28 fb 7f 4a 0c 3f 76-bb 22 23 0b e0 29 e9 40   .(..J.?v."#..).@
    00a0 - f8 2d 4c 67 e9 23 b3 0e-af 1a 36 79 3e 51 bf 12   .-Lg.#....6y>Q..
    00b0 - 24 be ca 42 d4 14 f0 fa-f1 e7 aa a2 85 58 ae b1   $..B.........X..
    00c0 - 29 4d 16 c0 74 22 37 ef-03 8c 31 02 03 2c 28 42   )M..t"7...1..,(B

    Start Time: 1708539382
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
    Session-ID: EAEEC2B73DA2E1EB80E17ADFD8D36B62A29B7774C3EEECA4D055F92A027633D1
    Session-ID-ctx:
    Resumption PSK: A72425A72C33930E06D643EE46D7921F1C3727A0ED84E9FDCB4EE26BEF320BC76C0A62FAD799A169B12436E5ADDF7068
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 67 62 ad 30 72 ef 35 8b-4b 97 68 8c 1c f3 24 79   gb.0r.5.K.h...$y
    0010 - 1d 3d a7 4a 7d 52 08 fa-74 2a ed 03 57 08 fb d3   .=.J}R..t*..W...
    0020 - 1e a6 69 01 59 ca 8c fb-d8 35 dd b6 d3 89 b5 bd   ..i.Y....5......
    0030 - af 72 ee a2 8e 9d 19 76-0f 24 a0 0f 4a 43 4b 5c   .r.....v.$..JCK\
    0040 - bc 83 d4 64 1b d9 ee 28-3b c5 ab 20 a6 de c3 8d   ...d...(;.. ....
    0050 - b8 d0 a2 b7 ac 61 5a 7b-92 3e 5e 6d 2d 50 85 ab   .....aZ{.>^m-P..
    0060 - cd 88 bb db c4 a7 30 fb-2a 7c d1 4a 40 e3 94 5d   ......0.*|.J@..]
    0070 - a4 ed 85 b6 40 a1 d6 90-a9 de 84 ec 5c ae e9 42   ....@.......\..B
    0080 - b5 bd 19 dc f4 02 b9 37-95 98 98 18 6a c1 aa ca   .......7....j...
    0090 - c7 e6 ff bb cf 2e ee 04-b4 28 ee d7 2b d2 82 da   .........(..+...
    00a0 - 0f e7 85 08 b3 24 a9 c1-0f b5 4e e4 33 5a 13 c6   .....$....N.3Z..
    00b0 - 11 57 88 7f 7d 6d d9 ff-8a f7 75 d6 32 16 d1 4f   .W..}m....u.2..O
    00c0 - 66 c5 c6 2a 7b e5 35 3f-73 ee 23 b5 94 10 a9 66   f..*{.5?s.#....f

    Start Time: 1708539382
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
JQttfApK4SeyHwDlI9SXGR50qclOAil1
JQttfApK4SeyHwDlI9SXGR50qclOAil1
^C
bandit16@bandit:~$ openssl s_client -connect localhost:31691
CONNECTED(00000003)
80DBF0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 293 bytes and written 300 bytes
Verification: OK
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Feb 20 17:51:06 2024 GMT
verify return:1
depth=0 CN = localhost
notAfter=Feb 20 17:51:06 2024 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Feb 20 17:50:06 2024 GMT; NotAfter: Feb 20 17:51:06 2024 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEQ9wEgDANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjQwMjIwMTc1MDA2WhcNMjQwMjIwMTc1MTA2WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDA
gdd50zQdwKnADuCYAoUSFvGreD2Mr/e6QZK+31XsKXCd/+cGHdmkqerggVlwno8T
3lmAaRw+Pk/nNdn3xJEGGq5guV2YhAnT+IQgP6+76ii/4gUCQxnaTtmslJDSfv7i
km+qYsFRL1YdtOo5od2etkLdorXGqGcIrB6ilCgKgQ2Q7FqMjh7n37HPk8yaWCwX
M/JZ7jkXw4mf2Un9UILgo/oJfR0JhMq6cDkHztG0E6j5ruknDeeOMGimH9pmzaa9
xdJe1GTtk+v03FIng0IfHi0HVPUCN8dl9rKLzn/LKZ3UftyffIErE7nDCLaGpVBK
DQzkq5gMPShGa1RT7nkFAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQBh
XmVUELbEPhoHaMrhwHyd24bRzYiiOemi75OA6QywOLh7moC8MGKvtI0mHhhA+lfB
eEvOOPwL5om4culG+KnC24fdWzwX/PPtkYKocNSrIQINrVhTwBbGwnC+WCSYizZS
43Zav+szrJ6H66qO4x4wXU9p1qC24dIpY5dfBsy4m8P/XzUtg68YJng1EIuGM6DF
CnMWXUB0cfUgBsbWPMrQlJd5sHifKeglK3kBCXn3zb9T881YbLNAwMK2a5SnPdh8
eTg1e7pdNYwPvHcxYPySGyQCkLpLHduWUxVNrUfsVHrxI6rrHynZ5vv4+ulAmhAc
YoU33/wx/D1oycw1GLHh
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
    Session-ID: 94302D19C8725846F23EBB03C5C2CE8D89704C344F05A4D2F574AE0FDCB3F7B0
    Session-ID-ctx:
    Resumption PSK: 5E21C9DA78779D5800D269460C43F202366481B1A3885D19D18E48445EDC818F70D6BCF1908B7AFC3C3C5BE2F3C6285E
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 92 ed 0d d5 75 f9 0c 95-ed 08 73 73 af f3 6c c3   ....u.....ss..l.
    0010 - 66 ec 66 bf 2f 42 aa 59-5b 0d 1c e5 ea c2 c8 01   f.f./B.Y[.......
    0020 - 42 f3 a5 d4 37 39 02 b9-62 19 82 3e be 4f 6d 9b   B...79..b..>.Om.
    0030 - 1d c9 eb 90 d3 79 55 f4-f3 b9 6d 2e 07 40 9c 81   .....yU...m..@..
    0040 - a6 00 49 60 84 c4 c8 e4-a8 a9 9d 39 d5 8a fb 61   ..I`.......9...a
    0050 - 09 b4 37 c5 ed 6b 87 4c-e4 b7 a8 12 3a bc 36 c6   ..7..k.L....:.6.
    0060 - 94 05 ca 46 b5 ef 2a 07-dd 02 64 f4 c8 f3 ed e5   ...F..*...d.....
    0070 - 41 b6 86 ac 8c 04 2a 2b-2a d5 ab 8e 2e eb db 2a   A.....*+*......*
    0080 - 4b e6 dc 51 88 38 42 1a-5d 0a 6c dd ae 42 08 03   K..Q.8B.].l..B..
    0090 - 4a 1c 8b 6f 06 2b 50 7d-d7 00 3c 23 22 48 4f 5c   J..o.+P}..<#"HO\
    00a0 - e7 c6 bd 2e 8f 89 68 cd-c3 a7 88 96 50 71 6f 8b   ......h.....Pqo.
    00b0 - c5 5c 7c ce 34 e9 d1 21-b8 8b 6c e8 23 5c d4 43   .\|.4..!..l.#\.C
    00c0 - 6a 0b de e4 2e 6e 19 64-f0 d8 91 2d 91 72 f0 5d   j....n.d...-.r.]

    Start Time: 1708539435
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
    Session-ID: 77851D7DD895FD571B9364C8092D1BD6982591A4D43258F02B4FA2C7482F5C37
    Session-ID-ctx:
    Resumption PSK: BE66BD997C0A53C06B5E16B95A365EF8D6A55CA4E4C240ED76F95567CD5674DE2FBBC177A82A36925CCA0B7EB263D4D9
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 92 ed 0d d5 75 f9 0c 95-ed 08 73 73 af f3 6c c3   ....u.....ss..l.
    0010 - b7 67 1c f8 be b6 36 6d-e6 2c 9d e0 eb ff 50 a4   .g....6m.,....P.
    0020 - 41 e1 99 9e 66 c9 6d f8-f2 79 57 b8 53 cd e0 7b   A...f.m..yW.S..{
    0030 - a7 96 f3 4d 3f ec ac d5-bc 5c d3 6e 69 52 b7 04   ...M?....\.niR..
    0040 - cf 37 cb 8b a3 99 f0 0f-ca 68 76 02 27 97 9f 45   .7.......hv.'..E
    0050 - a2 fe 6a 74 1d 07 1c 08-4b 4a 29 e4 5c 8c 9d 8d   ..jt....KJ).\...
    0060 - fc 20 dc 74 90 52 ca 00-b5 e1 90 fa 89 6b 4b f7   . .t.R.......kK.
    0070 - 8d 20 76 b4 f0 68 23 be-7c 47 13 2f cd f2 52 e2   . v..h#.|G./..R.
    0080 - 18 ef 80 28 48 7f b5 ac-36 13 39 7b 7b 5c bc d9   ...(H...6.9{{\..
    0090 - 99 e2 70 e9 e3 bf 2d 53-0c 98 f6 e5 23 40 01 23   ..p...-S....#@.#
    00a0 - 99 6d 11 c0 9f 6a 54 7e-84 95 73 71 c0 f5 89 c6   .m...jT~..sq....
    00b0 - 1e 89 ea 60 ad 62 91 ab-f8 a6 fd b3 5c 6d 4f 61   ...`.b......\mOa
    00c0 - ac dd 9b 30 01 63 3f fa-60 e8 c5 cd b1 91 2b 77   ...0.c?.`.....+w

    Start Time: 1708539435
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi


Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
bandit16@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

C:\Users\Miguel García>cd Desktop

C:\Users\Miguel García\Desktop>dir
 El volumen de la unidad C no tiene etiqueta.
 El número de serie del volumen es: B0CA-F869

 Directorio de C:\Users\Miguel García\Desktop

21/02/2024  12:04    <DIR>          .
21/02/2024  11:23    <DIR>          ..
               0 archivos              0 bytes
               2 dirs  315,042,455,552 bytes libres

C:\Users\Miguel García\Desktop>nvim bandit17.private
```

### Notas adicionales


### Referencias
