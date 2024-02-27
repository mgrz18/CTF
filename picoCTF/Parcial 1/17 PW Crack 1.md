## Objetivo
Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

## Solución

```bash
mrfear@nightmare ~/picoCTF % ls
level1.flag.txt.enc  level1.py
mrfear@nightmare ~/picoCTF % python3 level1.py
Please enter correct password for flag: ^CTraceback (most recent call last):
  File "/home/mrfear/picoCTF/level1.py", line 28, in <module>
    level_1_pw_check()
  File "/home/mrfear/picoCTF/level1.py", line 18, in level_1_pw_check
    user_pw = input("Please enter correct password for flag: ")
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
KeyboardInterrupt

mrfear@nightmare ~/picoCTF % cat level1.flag.txt.enc
FPR
  umw
 iK
_i
   UD%                                                                                                                 mrfear@nightmare ~/picoCTF % vim level1.flag.txt.enc
mrfear@nightmare ~/picoCTF % vim level1.py
mrfear@nightmare ~/picoCTF % python3 level1.py
Please enter correct password for flag: ^CTraceback (most recent call last):
  File "/home/mrfear/picoCTF/level1.py", line 28, in <module>
    level_1_pw_check()
  File "/home/mrfear/picoCTF/level1.py", line 18, in level_1_pw_check
    user_pw = input("Please enter correct password for flag: ")
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
KeyboardInterrupt

mrfear@nightmare ~/picoCTF % vim level1.py
mrfear@nightmare ~/picoCTF % python3 level1.py
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419}
mrfear@nightmare ~/picoCTF %
```

## Notas
En este nivel abrí el código de python que compara la contraseña ingresada por el usuario, encontrando así que era 691d, esto automáticamente regresa la flag sin tener que desencriptar el archivo .enc

## Referencias