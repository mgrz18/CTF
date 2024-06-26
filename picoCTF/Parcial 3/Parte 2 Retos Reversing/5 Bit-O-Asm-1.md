## Objetivo
Can you figure out what is in the eax register? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}. Download the assembly dump [here](https://artifacts.picoctf.net/c/509/disassembler-dump0_a.txt).

## Pistas
- As with most assembly, there is a lot of noise in the instruction dump. Find the one line that pertains to this question and don't second guess yourself!

## Solución
El código que nos proporcionan es el siguiente:
```asm
<+0>:     endbr64
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x4],edi
<+11>:    mov    QWORD PTR [rbp-0x10],rsi
<+15>:    mov    eax,0x30
<+20>:    pop    rbp
<+21>:    ret
```

Y lo que nos preguntan es el valor que contiene al final EAX, en este código está bastante sencillo, ya que la última operación de EAX indica que hay que cargarle el valor 0x30, lo que nos deja con ese valor como bandera, que convertido a decimal equivale al número 48, resultando en nuestra bandera.

## Notas

## Referencias
