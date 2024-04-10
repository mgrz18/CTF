## Objetivo
Theres tapping coming in from the wires. What's it saying nc jupiter.challenges.picoctf.org 48247.

## Pistas
- What kind of encoding uses dashes and dots?
- The flag is in the format PICOCTF{}

## Solución
Lo primero que podemos observar al conectarnos al servidor de netcat es:
```powershell
C:\Users\mgarcia\Desktop>ncat jupiter.challenges.picoctf.org 48247
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- }
```
Como podemos observar solo hay puntos y guiones que se pueden interpretar como código morse, entonces debemos de buscar un decodificador de morse para poder interpretar este mensaje.

En este caso yo usé cyberchef, que me arrojó el siguiente resultado
PICOCTF M0RS3C0D31SFUN1261438181 
## Notas

## Referencias
