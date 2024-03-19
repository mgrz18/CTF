## Objetivo

## Pistas

## Solución
El pptm sabemos que a final de cuentas es un zip con información del documento, así se ha manejado Microsoft a lo largo de los años.

Dentro de ese comprimido hay algo interesante, un archivo llamado hidden, que se encuentra en la ruta:
```
./ppt/slideMasters/hidden
```

Este archivo tiene un código con espacios, el siguiente comando elimina los espacios y además decodifica de base64

```bash
mgarcia@nightmare ~ % echo "Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q" | tr -d " " | base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}base64: invalid input
mgarcia@nightmare ~ %

```

## Notas

## Referencias