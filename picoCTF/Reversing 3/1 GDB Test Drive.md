## Objetivo
Can you get the flag? Download this [binary](https://artifacts.picoctf.net/c/86/gdbme). Here's the test drive instructions:
   - $ chmod +x gdbme
   - $ gdb gdbme
   - (gdb) layout asm
   - (gdb) break *(main+99)
   - (gdb) run
   - (gdb) jump *(main+104)


## Pistas
- None

## Solución
Realmente este reto no estuvo tan complejo como otros, me hubiera gustado mostrar la salida del depurador pero en ningún momento pude copiar los contenidos... Simplemente hay que seguir las instrucciones y todo saldrá bien. En mi caso la distro no incluía el paquete gdb, pero lo instalé con el comando _**sudo dnf install gdb**_

## Notas

## Referencias
