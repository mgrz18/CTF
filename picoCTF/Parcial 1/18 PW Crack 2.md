## Objetivo
Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.

## Solución

```bash
1   ### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################                                       1 def str_xor(secret, key):
  2     #extend key to secret length
  3     new_key = key
  4     i = 0
  5     while len(new_key) < len(secret):
  6         new_key = new_key + key[i]
  7         i = (i + 1) % len(key)
  8     return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
  9 ###############################################################################
 10
 11 flag_enc = open('level2.flag.txt.enc', 'rb').read()
 12
 13
 14
 15 def level_2_pw_check():
 16     user_pw = input("Please enter correct password for flag: ")
 17     if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
 18         print("Welcome back... your flag, user:")
 19         decryption = str_xor(flag_enc.decode(), user_pw)
 20         print(decryption)
 21         return
 22     print("That password is incorrect")
 23
 24
 25
 26 level_2_pw_check()

Este es el contenido del código, podemos ver que al usuario ingresar los caracteres 0x33, 0x39, 0x63 y 0x65, le va a arrojar la contraseña al usuario, para nosotros poder obtener esa secuencia de caracteres primero debemos de convertirlos a numeros decimales y después en ASCII
0x33 -> 51  -> 3
0x39 -> 57  -> 9
0x63 -> 99  -> c
0x65 -> 101 -> e


mrfear@nightmare ~/picoCTF % vim level2.py
mrfear@nightmare ~/picoCTF % python3 level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
mrfear@nightmare ~/picoCTF %
```

## Notas


## Referencias