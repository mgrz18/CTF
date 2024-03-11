## Objetivo
We found this packet capture. Recover the flag.
https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap

## Solución
El archivo que nos proporcionan se encuentra en el formato pcap, un formato perteneciente al Sniffer Wireshark, entonces nosotros debemos de descargar Wireshark en caso de que no lo tengamos descargado.
Abrimos Wireshark, seleccionamos el archivo .pcap descargado, después si nosotros hacemos click en un paquete UDP, y le damos en seguir el stream del paquete, podremos ver que hay varias secuencias de stream de paquetes, y si nosotros saltamos de una en una, en este caso hasta el stream 6, daremos con la bandera.

## Notas

## Referencias
