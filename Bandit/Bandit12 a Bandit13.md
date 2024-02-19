### Bandit12 -> Bandit13

### Objetivo
La contraseña para el siguiente nivel se almacena en el archivo data.txt, que es un volcado hexadecimal de un archivo que se ha comprimido repetidamente. Para este nivel puede resultar útil crear un directorio en /tmp en el que pueda trabajar utilizando mkdir. Por ejemplo: mkdir /tmp/minombre123. Luego copie el archivo de datos usando cp y cámbiele el nombre usando mv (¡lea las páginas de manual!).
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
- Usuario: bandit12
### Solución

```bash
bandit12@bandit:~$ cat data.txt
00000000: 1f8b 0808 6855 1e65 0203 6461 7461 322e  ....hU.e..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 5948 1b32 0200 0019 ffff faee cff7  &SYH.2..........
00000030: f6ff e4f7 bfbc ffff bff7 ffb9 39ff 7ffb  ............9...
00000040: bd31 eeff b9fb fbbb b9bf f77f b001 3b2c  .1............;,
00000050: d100 0d03 d200 6868 0d00 0069 a00d 0340  ......hh...i...@
00000060: 1a68 00d0 0d01 a1a0 0001 a680 0003 46d4  .h............F.
00000070: 6434 3234 611a 340d 07a4 c351 068f 5000  d424a.4....Q..P.
00000080: 069a 0680 0000 0006 8006 8da4 681a 6868  ............h.hh
00000090: 0d06 8d00 6834 3400 d07a 9a00 01a0 0341  ....h44..z.....A
000000a0: ea1e a190 da40 3d10 ca68 3468 6800 00c8  .....@=..h4hh...
000000b0: 1a1a 1b50 0683 d434 d069 a0d0 3100 d000  ...P...4.i..1...
000000c0: 001e a680 00d0 1a00 d0d0 6864 d0c4 d0d0  ..........hd....
000000d0: 000c 8641 7440 0108 032e 86b4 4cf0 22bb  ...At@......L.".
000000e0: 6682 2b7e b3e2 e98d aa74 dacc 0284 330d  f.+~.....t....3.
000000f0: bbb2 9494 d332 d933 642a 3538 d27e 09ce  .....2.3d*58.~..
00000100: 53da 185a 505e aada 6c75 59a2 b342 0572  S..ZP^..luY..B.r
00000110: 249a 4600 5021 25b0 1973 c18a 6881 1bef  $.F.P!%..s..h...
00000120: 3f9b 1429 5b1d 3d87 68b5 804f 1d28 42fa  ?..)[.=.h..O.(B.
00000130: 16c2 3241 98fb 8229 e274 5a63 fe92 3aca  ..2A...).tZc..:.
00000140: 70c3 a329 d21f 41e0 5a10 08cb 888f 30df  p..)..A.Z.....0.
00000150: f3da ce85 418b 0379 6a65 cfa2 eeb7 9f01  ....A..yje......
00000160: 782c da0e 288b e0c3 fe13 7af5 45ab 2b22  x,..(.....z.E.+"
00000170: a432 bf2f e32d b9e6 1465 2296 d805 a45e  .2./.-...e"....^
00000180: d1c1 eacb 7483 6aac ca0e cf24 8864 bd40  ....t.j....$.d.@
00000190: 118c 644a 1dc6 a127 375c b7a6 c124 bdae  ..dJ...'7\...$..
000001a0: 6d31 63a0 a223 3ea0 61d4 bdf0 450f 56fb  m1c..#>.a...E.V.
000001b0: a546 8d34 08a2 4f1d 43d3 9063 404d dd43  .F.4..O.C..c@M.C
000001c0: b4f2 e65d bcb7 5932 0f5e 6802 3892 a988  ...]..Y2.^h.8...
000001d0: 443d 8e89 7e09 4fb0 499d ee4e 4470 46c0  D=..~.O.I..NDpF.
000001e0: 2ba6 7c62 234a 7f76 151b aec0 23ee 4a97  +.|b#J.v....#.J.
000001f0: bc64 e34c de8a 5724 a1c3 9b89 cd96 1879  .d.L..W$.......y
00000200: d560 0cbb 5c26 09e4 efaf 5b94 402a 7780  .`..\&....[.@*w.
00000210: 4d87 30ce b8a3 946e 72c1 a643 1db7 a060  M.0....nr..C...`
00000220: 6524 629c 0c7e 8e7b e0f8 820c d5cb 60a0  e$b..~.{......`.
00000230: 003c a584 d4c1 61ef eb02 3f65 3a54 a3a2  .<....a...?e:T..
00000240: a565 c154 34c2 b162 d206 1ff8 bb92 29c2  .e.T4..b......).
00000250: 8482 40d9 9010 b3a9 e478 3d02 0000       ..@......x=...
bandit12@bandit:~$ xxd -r data.txt | file -
/dev/stdin: gzip compressed data, was "data2.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix
bandit12@bandit:~$ mkdir /tmp/1506
bandit12@bandit:~$ cd /tmp/1506
bandit12@bandit:/tmp/1506$ cp ~/data.txt .
bandit12@bandit:/tmp/1506$ ls
data.txt
bandit12@bandit:/tmp/1506$ xxd -r data.txt > data
bandit12@bandit:/tmp/1506$ ls
data  data.txt
bandit12@bandit:/tmp/1506$ ls /tmp
ls: cannot open directory '/tmp': Permission denied
bandit12@bandit:/tmp/1506$ rm data.txt
bandit12@bandit:/tmp/1506$ ls -la
total 408
drwxrwxr-x    2 bandit12 bandit12   4096 Feb 19 18:38 .
drwxrwx-wt 1469 root     root     405504 Feb 19 18:39 ..
-rw-rw-r--    1 bandit12 bandit12    606 Feb 19 18:37 data
bandit12@bandit:/tmp/1506$ mv data data.gz
bandit12@bandit:/tmp/1506$ gzip data.gz
gzip: data.gz already has .gz suffix -- unchanged
bandit12@bandit:/tmp/1506$ gzip -d data.gz
bandit12@bandit:/tmp/1506$ ls
data
bandit12@bandit:/tmp/1506$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/1506$ bzip2 -d data
bzip2: Can't guess original name for data -- using data.out
bandit12@bandit:/tmp/1506$ ls
data.out
bandit12@bandit:/tmp/1506$ cp ~/data.txt .
bandit12@bandit:/tmp/1506$ xxd -r data.txt data
bandit12@bandit:/tmp/1506$ rm data.out
bandit12@bandit:/tmp/1506$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 573
bandit12@bandit:/tmp/1506$ mv data data.gz
bandit12@bandit:/tmp/1506$ gzip -d data.gz
bandit12@bandit:/tmp/1506$ ls
data  data.txt
bandit12@bandit:/tmp/1506$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/1506$ mv data data.gz
bandit12@bandit:/tmp/1506$ mv data.gz data.bz2
bandit12@bandit:/tmp/1506$ ls
data.bz2  data.txt
bandit12@bandit:/tmp/1506$ bzip2 -d data.bz2
bandit12@bandit:/tmp/1506$ ls
data  data.txt
bandit12@bandit:/tmp/1506$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/1506$ mv data data.gz
bandit12@bandit:/tmp/1506$ gzip data.gz
gzip: data.gz already has .gz suffix -- unchanged
bandit12@bandit:/tmp/1506$ gzip -d data.gz
bandit12@bandit:/tmp/1506$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/1506$ ls
data  data.txt
bandit12@bandit:/tmp/1506$ mv data data.tar
bandit12@bandit:/tmp/1506$ tar xf data.tar
bandit12@bandit:/tmp/1506$ ls
data5.bin  data.tar  data.txt
bandit12@bandit:/tmp/1506$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/1506$ mv data5.bin data5.tar
bandit12@bandit:/tmp/1506$ tar xf data5.tar
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6.bin  data.tar  data.txt
bandit12@bandit:/tmp/1506$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/1506$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/1506$ bzip2 -d data6.bz2
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6  data.tar  data.txt
bandit12@bandit:/tmp/1506$ file data6
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/1506$ mv data6 data6.tar
bandit12@bandit:/tmp/1506$ tar xf data6.tar
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6.tar  data8.bin  data.tar  data.txt
bandit12@bandit:/tmp/1506$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/1506$ mv data8.bin data8.gzip
bandit12@bandit:/tmp/1506$ mv data8.gzip data8.gz
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6.tar  data8.gz  data.tar  data.txt
bandit12@bandit:/tmp/1506$ tar xf data8.gz
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6.tar  data8.gz  data.tar  data.txt
bandit12@bandit:/tmp/1506$ file data8.gz
data8.gz: gzip compressed data, was "data9.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/1506$ ls -la
total 456
drwxrwxr-x    2 bandit12 bandit12   4096 Feb 19 18:45 .
drwxrwx-wt 1473 root     root     405504 Feb 19 18:46 ..
-rw-r--r--    1 bandit12 bandit12  10240 Oct  5 06:19 data5.tar
-rw-r--r--    1 bandit12 bandit12  10240 Oct  5 06:19 data6.tar
-rw-r--r--    1 bandit12 bandit12     79 Oct  5 06:19 data8.gz
-rw-rw-r--    1 bandit12 bandit12  20480 Feb 19 18:41 data.tar
-rw-r-----    1 bandit12 bandit12   2582 Feb 19 18:41 data.txt
bandit12@bandit:/tmp/1506$ gzip -d data8.gz
bandit12@bandit:/tmp/1506$ ls
data5.tar  data6.tar  data8  data.tar  data.txt
bandit12@bandit:/tmp/1506$ cat data8
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
bandit12@bandit:/tmp/1506$ file data8
data8: ASCII text
bandit12@bandit:/tmp/1506$
```

### Notas adicionales
XXD es para realizar un vaciado hexadecimal de un archivo
.gz -> gzip -d -> zcat
.bz2 -> bzip2 -d -> bzcat
.tar -> tar xf -> tar x0


### Referencias
