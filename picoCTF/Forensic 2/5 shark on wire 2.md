## Objetivo
We found this packet capture. Recover the flag that was pilfered from the network.
https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap

## Pistas
No hay

## Solución
El archivo proporcionado esta vez es un archivo de captura hecho en Wireshark, donde nosotros podremos darnos cuenta de que hay una secuencia UDP que parecería tener la bandera, pero en realidad ninguna contiene la bandera completa, hasta que después de empesar a revisar los paquetes UDP y empezamos a notar que hay un host en particular al que se enviaron paquetes con una numeración especial y repetitiva. Esto nos da un indicio de que algo ahí no es normal. Podremos ver que la información de los paquetes pareciera estar en ASCII pero con 5000 caracteres de desplazamiento, el siguiente código puede contrarestar eso y además transformar el restante en código ASCII

```python
from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
	if UDP in p and p[UDP].dport == 22:
		if p[UDP].sport > 5000:
			flag += chr(p[UDP].sport - 5000)

print(flag)
```

```powershell
C:\Users\mgarcia\Desktop>python decoder2.py
WARNING: Wireshark is installed, but cannot read manuf !
picoCTF{p1LLf3r3d_data_v1a_st3g0}

```

## Notas

## Referencias