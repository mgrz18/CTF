## Objetivo
Find the flag being held on this server to get ahead of the competition http://mercury.picoctf.net:34561/

## Solución
En este reto, la solución del problema consiste, como dice el título en obtener el encabezado de la página web que estamos visitando, un comando que nos puede facilitar mucho este tipo de consultas es el comando _curl_ este nos permite enviar el argumento -I para obtener un encabezado.

```powershell
C:\Users\mgarcia>curl -I http://mercury.picoctf.net:34561/
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_8f878508}
Content-type: text/html; charset=UTF-8
```

## Bandera
picoCTF{r3j3ct_th3_du4l1ty_8f878508} 

## Notas

## Referencias
