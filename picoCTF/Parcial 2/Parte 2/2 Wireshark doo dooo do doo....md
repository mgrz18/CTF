## Objetivo
Can you find the flag? shark1.pcapng.

## Pistas
(None)

## Solución
Este reto pide encontrar la badera dentro de una captura de Wireshark, en este caso yo realicé lo siguiente:
- Abrí la captura
- Seguí el stream TCP
- Cambié de secuencia hasta llegar a la secuencia 5 y encontrar una cadena con un formato parecido al de las banderas.
- Conté el desplazamiento entre la primera palabra de esa bandera y una bandera con el formato correcto de picoCTF
- Como me dí cuenta de que eran 13 caracteres, le apliqué ROT13.

```bash
mgarcia@nightmare ~/mgarcia/Downloads
 % echo 'cvpbPGS{c33xno00_1_f33_h_qrnqorrs}' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
picoCTF{p33kab00_1_s33_u_deadbeef}
```

## Notas adicionales
## Referencias