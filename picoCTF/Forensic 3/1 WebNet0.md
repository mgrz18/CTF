## Objetivo
We found this packet capture and key. Recover the flag.

## Solución
Hay que seleccionar el archivo llave del cifrado TLS que se manejó en la captura que nos proporicionan, con eso nosotros ya podemos ver el tráfico que anteriormente estaba encriptado.

Si buscamos por los detalles de un paquete de TLS, en el formato de cadena, la palabra picoCTF, vamos a encontrar la respuesta que buscamos.


```
Frame 35: 576 bytes on wire (4608 bits), 576 bytes captured (4608 bits)
Ethernet II, Src: 06:41:fb:0d:59:be (06:41:fb:0d:59:be), Dst: 06:72:25:91:2d:68 (06:72:25:91:2d:68)
Internet Protocol Version 4, Src: 172.31.22.220, Dst: 128.237.140.23
Transmission Control Protocol, Src Port: 443, Dst Port: 57567, Seq: 1266, Ack: 1291, Len: 510
Transport Layer Security
Hypertext Transfer Protocol
    HTTP/1.1 200 OK\r\n
    Date: Fri, 23 Aug 2019 15:56:36 GMT\r\n
    Server: Apache/2.4.29 (Ubuntu)\r\n
    Last-Modified: Mon, 12 Aug 2019 16:47:05 GMT\r\n
    ETag: "62-58fee462bf227-gzip"\r\n
    Accept-Ranges: bytes\r\n
    Vary: Accept-Encoding\r\n
    Content-Encoding: gzip\r\n
    Pico-Flag: picoCTF{nongshim.shrimp.crackers}\r\n
    Content-Length: 100\r\n
    Keep-Alive: timeout=5, max=100\r\n
    Connection: Keep-Alive\r\n
    Content-Type: text/css\r\n
    \r\n
    [HTTP response 1/2]
    [Time since request: 0.000442000 seconds]
    [Request in frame: 34]
    [Next request in frame: 37]
    [Next response in frame: 38]
    [Request URI: https://ec2-18-223-184-200.us-east-2.compute.amazonaws.com/starter-template.css]
    Content-encoded entity body (gzip): 100 bytes -> 98 bytes
    File Data: 98 bytes
Line-based text data: text/css (7 lines)


```

## Notas

## Referencias