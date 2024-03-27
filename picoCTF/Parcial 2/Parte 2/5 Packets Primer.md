## Objetivo
Download the packet capture file and use packet analysis software to find the flag.
Download packet capture -> https://artifacts.picoctf.net/c/195/network-dump.flag.pcap

## Pistas
- Wireshark, if you can install and use it, is probably the most beginner friendly packet analysis software product.

## Solución
Si nosotros analizamos el paquete, podemos ver que un paquete contiene una cadena de datos hexadecimales que podemos convertir a datos legibles para el humano.

```bash
mgarcia@nightmare ~/mgarcia/Downloads
 % echo -n 7020692063206f204320542046207b207020342063206b20332037205f2035206820342072206b205f20622039206420352033203720362035207d0a | xxd -r -p
p i c o C T F { p 4 c k 3 7 _ 5 h 4 r k _ b 9 d 5 3 7 6 5 }
mgarcia@nightmare ~/mgarcia/Downloads
 % echo -n 7020692063206f204320542046207b207020342063206b20332037205f2035206820342072206b205f20622039206420352033203720362035207d0a | xxd -r -p | sed 's/ //g'
picoCTF{p4ck37_5h4rk_b9d53765}
```


## Notas adicionales
## Referencias