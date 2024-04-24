## Objetivo
What does asm3(0xba6c5a02,0xd101e3dd,0xbb86a173) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/cb753ae52bca4aa303deca5fbfb01bfb/test.S)

## Pistas
- more(?) [registers](https://wiki.skullsecurity.org/index.php?title=Registers)

## Solución
Nos proporcionan un código que más adelante ejecutaremos paso a paso

```powershell
C:\Users\mgarcia\Desktop\ctf>type test.S
asm3:
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   xor    eax,eax
        <+5>:   mov    ah,BYTE PTR [ebp+0xb]
        <+8>:   shl    ax,0x10
        <+12>:  sub    al,BYTE PTR [ebp+0xd]
        <+15>:  add    ah,BYTE PTR [ebp+0xc]
        <+18>:  xor    ax,WORD PTR [ebp+0x12]
        <+22>:  nop
        <+23>:  pop    ebp
        <+24>:  ret


C:\Users\mgarcia\Desktop\ctf>
```


En la página mencionada más abajo, este es el código efectivo que funcionaria
```asm
push 0xbb86a173
push 0xd101e3dd
push 0xba6c5a02
call asm3

asm3:
        push   ebp
        mov    ebp,esp
        xor    eax,eax
        mov    ah,BYTE PTR [ebp+0xb]
        shl    ax,0x10
        sub    al,BYTE PTR [ebp+0xd]
        add    ah,BYTE PTR [ebp+0xc]
        xor    ax,WORD PTR [ebp+0x12]
        nop
        pop    ebp
        ret
```

Y el resultado del registro final sería:
EAX  	0x0000669B	  	EBX  	0x00000000
ECX  	0x00000000	  	EDX  	0x00000000
ESI  	0x00000000	  	EDI  	0x00000000
EBP  	0x000203EC	  	ESP  	0x000203EC
EIP  	0x00020434	Ln 16, Col 9

Tomando nosotros EAX
## Notas
- Este editor simula el código, nos va a ayudar mucho para ejecutar rápido el código (Asm 86 Emulator)[https://carlosrafaelgn.github.io/Asm86/]

## Referencias
