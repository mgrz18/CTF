## Objetivo
Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too. There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Solución

```bash
level_3_pw_check()
 11
 12
 13 # The strings below are 7 possibilities for the correct password.
 14 #   (Only 1 is correct)
 15 pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]
 16

Al examinar el código podemos ver que nos ofrece algunas posibilidades de las cuales una si es la contraseña correcta, entonces podemos probar de una por una para encontrar cuál es la contraseña correcta

mrfear@nightmare ~/picoCTF % ls
level3.flag.txt.enc  level3.hash.bin  level3.py
mrfear@nightmare ~/picoCTF % vim level3.py
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: 6997
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: 3ac8
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: f0ac
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: 4b17
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: ec27
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: 4e66
That password is incorrect
mrfear@nightmare ~/picoCTF % python3 level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias