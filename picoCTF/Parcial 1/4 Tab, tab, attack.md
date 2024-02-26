## Objetivo
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/9689f2b453ad5daeb73ca7534e4d1521/Addadshashanammu.zip)

## Solución

```bash
mrfear@nightmare ~/picoCTF % ls
mrfear@nightmare ~/picoCTF % wget https://mercury.picoctf.net/static/9689f2b453ad5daeb73ca7534e4d1521/Addadshashanammu.zip
--2024-02-26 12:56:45--  https://mercury.picoctf.net/static/9689f2b453ad5daeb73ca7534e4d1521/Addadshashanammu.zip
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4519 (4.4K) [application/octet-stream]
Saving to: ‘Addadshashanammu.zip’

Addadshashanammu.zip          100%[=================================================>]   4.41K  --.-KB/s    in 0s

2024-02-26 12:56:46 (35.2 MB/s) - ‘Addadshashanammu.zip’ saved [4519/4519]

mrfear@nightmare ~/picoCTF % ls
Addadshashanammu.zip
mrfear@nightmare ~/picoCTF % ls -la Addadshashanammu.zip
-rw-r--r-- 1 mrfear mrfear 4519 Mar 15  2021 Addadshashanammu.zip
mrfear@nightmare ~/picoCTF % gzip2 -d Addadshashanammu.zip
zsh: command not found: gzip2
mrfear@nightmare ~/picoCTF % sudo apt install unzip gzip
[sudo] password for mrfear:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
unzip is already the newest version (6.0-28).
gzip is already the newest version (1.12-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mrfear@nightmare ~/picoCTF % unzip Addadshashanammu.zip
Archive:  Addadshashanammu.zip
   creating: Addadshashanammu/
   creating: Addadshashanammu/Almurbalarammi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
  inflating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet
mrfear@nightmare ~/picoCTF % ls
Addadshashanammu  Addadshashanammu.zip
mrfear@nightmare ~/picoCTF % cd Addadshashanammu
mrfear@nightmare ~/picoCTF/Addadshashanammu
 % ls
Almurbalarammi
mrfear@nightmare ~/picoCTF/Addadshashanammu
 % cd Almurbalarammi
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi
 % ls
Ashalmimilkala
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi
 % ls
Ashalmimilkala
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi
 % cd Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku
 % ls
fang-of-haynekhtnamet
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku
 % ls -la fang-of-haynekhtnamet
-rwxr-xr-x 1 mrfear mrfear 8320 Mar 15  2021 fang-of-haynekhtnamet
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku
 % ./fang-of-haynekhtnamet
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_2bcfb2ab}
mrfear@nightmare ~/picoCTF/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku
 %
```

## Notas

## Referencias