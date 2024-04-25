## Objetivo
We have recovered a [binary](https://jupiter.challenges.picoctf.org/static/48babf8f8c4c6b8baf336680ea5b9ddf/rev) and a [text file](https://jupiter.challenges.picoctf.org/static/48babf8f8c4c6b8baf336680ea5b9ddf/rev_this). Can you reverse the flag.

## Pistas
- objdump and Gihdra are some tools that could assist with this

## Solución
Primero debemos de instalar ghidra, después abriremos el archivo binario **rev**, que nos dará dos códigos, el código en ensamblador y un código decompilado, nosotros usaremos la segunda:

```c
void main(void)

{
  size_t sVar1;
  char local_58 [23];
  char local_41;
  int local_2c;
  FILE *local_28;
  FILE *local_20;
  uint local_14;
  int local_10;
  char local_9;
  
  local_20 = fopen("flag.txt","r");
  local_28 = fopen("rev_this","a");
  if (local_20 == (FILE *)0x0) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (local_28 == (FILE *)0x0) {
    puts("please run this on the server");
  }
  sVar1 = fread(local_58,0x18,1,local_20);
  local_2c = (int)sVar1;
  if ((int)sVar1 < 1) {
                    /* WARNING: Subroutine does not return */
    exit(0);
  }
  for (local_10 = 0; local_10 < 8; local_10 = local_10 + 1) {
    local_9 = local_58[local_10];
    fputc((int)local_9,local_28);
  }
  for (local_14 = 8; (int)local_14 < 0x17; local_14 = local_14 + 1) {
    if ((local_14 & 1) == 0) {
      local_9 = local_58[(int)local_14] + '\x05';
    }
    else {
      local_9 = local_58[(int)local_14] + -2;
    }
    fputc((int)local_9,local_28);
  }
  local_9 = local_41;
  fputc((int)local_41,local_28);
  fclose(local_28);
  fclose(local_20);
  return;
}

```
Este código nos va a permitir ver el proceso con el que se encripto, la bandera, que podremos revertir, a mano o con algún script, he aquí un ejemplo:
```python
cifrado = open('rev_this','r').read()

print(cifrado)

flag = ''

for i in range (8, len(cifrado)-1):
    if i& 1==0:
        flag+= chr(ord(cifrado[i]) - 5)
    else:
        flag+= chr(ord(cifrado[i]) + 2)

print('picoCTF{',flag,'}')

```
Este código automáticamente nos va a arrojar la bandera que estamos buscando.
## Notas

## Referencias
