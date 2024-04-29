## Objetivo
Can you figure out what is in the eax register? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}. Download the assembly dump [here](https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt).

## Pistas
- PTR's or 'pointers', reference a location in memory where values can be stored.

## Solución
El código que nos proporcionan en esta ocasión es:
```asm
<+0>:     endbr64
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    mov    eax,DWORD PTR [rbp-0x4]
<+25>:    pop    rbp
<+26>:    ret
```

De igual manera nos preguntan por el valor con el que el registro EAX termina, en este caso, el registro contiene el valor 0x9fe1a, que convertido a decimla nos daría la bandera.

## Notas

## Referencias
