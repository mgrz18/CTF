## Objetivo
The name of the game is [speed](https://www.youtube.com/watch?v=8piqd2BWeGI). Are you quick enough to solve this problem and keep it above 50 mph? [need-for-speed](https://jupiter.challenges.picoctf.org/static/f9abc386dfb1309e687344783f208b20/need-for-speed).

## Pistas
- What is the final key?

## Solución
Nosotros tenemos que realizar una depuración del programa, para darnos cuenta de que ahí dentro existen funciones que nos van a ser útiles más adelante, como **get_key** o **print_flag**.

```gdb
mrfear@nightmare ~/winhome/Desktop/pico % wget https://jupiter.challenges.picoctf.org/static/f9abc386dfb1309e687344783f208b20/need-for-speed
--2024-04-24 20:55:02--  https://jupiter.challenges.picoctf.org/static/f9abc386dfb1309e687344783f208b20/need-for-speed
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8888 (8.7K) [application/octet-stream]
Saving to: ‘need-for-speed’

need-for-speed                           100%[=================================================================================>]   8.68K  --.-KB/s    in 0.003s

2024-04-24 20:55:03 (3.32 MB/s) - ‘need-for-speed’ saved [8888/8888]

mrfear@nightmare ~/winhome/Desktop/pico % chmod +x need-for-speed
mrfear@nightmare ~/winhome/Desktop/pico % gdb need-for-speed
GNU gdb (Fedora Linux) 14.2-1.fc39
Copyright (C) 2023 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-redhat-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from need-for-speed...

This GDB supports auto-downloading debuginfo from the following URLs:
  <https://debuginfod.fedoraproject.org/>
Enable debuginfod for this session? (y or [n])
Debuginfod has been disabled.
To make this setting permanent, add 'set debuginfod enabled off' to .gdbinit.
(No debugging symbols found in need-for-speed)
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x00000000000005d8  _init
0x0000000000000600  putchar@plt
0x0000000000000610  puts@plt
0x0000000000000620  alarm@plt
0x0000000000000630  __sysv_signal@plt
0x0000000000000640  exit@plt
0x0000000000000650  __cxa_finalize@plt
0x0000000000000660  _start
0x0000000000000690  deregister_tm_clones
0x00000000000006d0  register_tm_clones
0x0000000000000720  __do_global_dtors_aux
0x0000000000000760  frame_dummy
0x000000000000076a  decrypt_flag
0x00000000000007f1  calculate_key
0x000000000000080e  alarm_handler
0x000000000000082f  set_timer
0x000000000000087d  get_key
0x00000000000008ac  print_flag
0x00000000000008d8  header
0x000000000000091a  main
0x0000000000000960  __libc_csu_init
0x00000000000009d0  __libc_csu_fini
0x00000000000009d4  _fini
(gdb) set disassemb
disassemble-next-line  disassembler-options   disassembly-flavor
(gdb) set disassembly-flavor intel
(gdb) disassemble main
Dump of assembler code for function main:
   0x000000000000091a <+0>:     push   rbp
   0x000000000000091b <+1>:     mov    rbp,rsp
   0x000000000000091e <+4>:     sub    rsp,0x10
   0x0000000000000922 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x0000000000000925 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x0000000000000929 <+15>:    mov    eax,0x0
   0x000000000000092e <+20>:    call   0x8d8 <header>
   0x0000000000000933 <+25>:    mov    eax,0x0
   0x0000000000000938 <+30>:    call   0x82f <set_timer>
   0x000000000000093d <+35>:    mov    eax,0x0
   0x0000000000000942 <+40>:    call   0x87d <get_key>
   0x0000000000000947 <+45>:    mov    eax,0x0
   0x000000000000094c <+50>:    call   0x8ac <print_flag>
   0x0000000000000951 <+55>:    mov    eax,0x0
   0x0000000000000956 <+60>:    leave
   0x0000000000000957 <+61>:    ret
End of assembler dump.
(gdb) call (int) get_key()
You can't do that without a process to debug.
(gdb) break main
Breakpoint 1 at 0x91e
(gdb) run
Starting program: /mnt/c/Users/mgarcia/Desktop/pico/need-for-speed
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib64/libthread_db.so.1".

Breakpoint 1, 0x000055555540091e in main ()
Missing separate debuginfos, use: dnf debuginfo-install glibc-2.38-18.fc39.x86_64
(gdb) disassemble main
Dump of assembler code for function main:
   0x000055555540091a <+0>:     push   rbp
   0x000055555540091b <+1>:     mov    rbp,rsp
=> 0x000055555540091e <+4>:     sub    rsp,0x10
   0x0000555555400922 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x0000555555400925 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x0000555555400929 <+15>:    mov    eax,0x0
   0x000055555540092e <+20>:    call   0x5555554008d8 <header>
   0x0000555555400933 <+25>:    mov    eax,0x0
   0x0000555555400938 <+30>:    call   0x55555540082f <set_timer>
   0x000055555540093d <+35>:    mov    eax,0x0
   0x0000555555400942 <+40>:    call   0x55555540087d <get_key>
   0x0000555555400947 <+45>:    mov    eax,0x0
   0x000055555540094c <+50>:    call   0x5555554008ac <print_flag>
   0x0000555555400951 <+55>:    mov    eax,0x0
   0x0000555555400956 <+60>:    leave
   0x0000555555400957 <+61>:    ret
End of assembler dump.
(gdb) call (int) get_key()
Creating key...
Finished
$1 = 9
(gdb) call (int) print_flag()
Printing flag:
PICOCTF{Good job keeping bus #190ca38b speeding along!}
$2 = 56
(gdb)
```

## Notas

## Referencias
