## Objetivo
This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program. You can download the file from [here](https://artifacts.picoctf.net/c/506/asciiftw).

## Pistas
- The combined range of hex-ascii for English alphabets and numerical digits is from 30 to 7A.
- Online hex-ascii converters can be helpful.

## Solución
Este archivo proporcionado es un ejecutable, que nos dice que la bandera empieza con 70, pero si lo abrimos con cat o algo parecido veremos caracteres sin sentido, por lo que usaremos para este reto la herramienta **ghidra.**

Iremos a la función main, donde encontraremos el mensaje que dice que la bandera empieza con 70, y ahí mismo este código:
```
        00101184 c6  45  d0       MOV        byte ptr [RBP  + local_38 ],0x70
                 70
        00101188 c6  45  d1       MOV        byte ptr [RBP  + local_37 ],0x69
                 69
        0010118c c6  45  d2       MOV        byte ptr [RBP  + local_36 ],0x63
                 63
        00101190 c6  45  d3       MOV        byte ptr [RBP  + local_35 ],0x6f
                 6f
        00101194 c6  45  d4       MOV        byte ptr [RBP  + local_34 ],0x43
                 43
        00101198 c6  45  d5       MOV        byte ptr [RBP  + local_33 ],0x54
                 54
        0010119c c6  45  d6       MOV        byte ptr [RBP  + local_32 ],0x46
                 46
        001011a0 c6  45  d7       MOV        byte ptr [RBP  + local_31 ],0x7b
                 7b
        001011a4 c6  45  d8       MOV        byte ptr [RBP  + local_30 ],0x41
                 41
        001011a8 c6  45  d9       MOV        byte ptr [RBP  + local_2f ],0x53
                 53
        001011ac c6  45  da       MOV        byte ptr [RBP  + local_2e ],0x43
                 43
        001011b0 c6  45  db       MOV        byte ptr [RBP  + local_2d ],0x49
                 49
        001011b4 c6  45  dc       MOV        byte ptr [RBP  + local_2c ],0x49
                 49
        001011b8 c6  45  dd       MOV        byte ptr [RBP  + local_2b ],0x5f
                 5f
        001011bc c6  45  de       MOV        byte ptr [RBP  + local_2a ],0x49
                 49
        001011c0 c6  45  df       MOV        byte ptr [RBP  + local_29 ],0x53
                 53
        001011c4 c6  45  e0       MOV        byte ptr [RBP  + local_28 ],0x5f
                 5f
        001011c8 c6  45  e1       MOV        byte ptr [RBP  + local_27 ],0x45
                 45
        001011cc c6  45  e2       MOV        byte ptr [RBP  + local_26 ],0x41
                 41
        001011d0 c6  45  e3       MOV        byte ptr [RBP  + local_25 ],0x53
                 53
        001011d4 c6  45  e4       MOV        byte ptr [RBP  + local_24 ],0x59
                 59
        001011d8 c6  45  e5       MOV        byte ptr [RBP  + local_23 ],0x5f
                 5f
        001011dc c6  45  e6       MOV        byte ptr [RBP  + local_22 ],0x33
                 33
        001011e0 c6  45  e7       MOV        byte ptr [RBP  + local_21 ],0x43
                 43
        001011e4 c6  45  e8       MOV        byte ptr [RBP  + local_20 ],0x46
                 46
        001011e8 c6  45  e9       MOV        byte ptr [RBP  + local_1f ],0x34
                 34
        001011ec c6  45  ea       MOV        byte ptr [RBP  + local_1e ],0x42
                 42
        001011f0 c6  45  eb       MOV        byte ptr [RBP  + local_1d ],0x46
                 46
        001011f4 c6  45  ec       MOV        byte ptr [RBP  + local_1c ],0x41
                 41
        001011f8 c6  45  ed       MOV        byte ptr [RBP  + local_1b ],0x44
                 44
        001011fc c6  45  ee       MOV        byte ptr [RBP  + local_1a ],0x7d
                 7d
```
Estas instrucciones nos van a servir, ya que aquí es donde se encuentra la bandera, solo hay que decodificar los datos, que sería con:

```
mrfear@nightmare ~/winhome/Desktop/ctf % cat dump.txt| cut -d "," -f3 | xxd -r -p
picoCTF{ASCII_IS_EASY_3CF4BFAD}%                                                                                        mrfear@nightmare ~/winhome/Desktop/ctf %
```

## Notas

## Referencias
