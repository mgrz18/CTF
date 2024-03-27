## Objetivo
Now you DON’T see me. This report has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf

## Pistas
- How can you be sure of the redaction?

## Solución
Bueno, esta fue una solución inesperada pero funcional. Podemos observar que el PDF contiene varios espacios cubiertos con recuadros negros, pero ¿que pasa si seleccionamos todo el texto y lo pegamos en otro lado?, ¡¡ahí se puede ver el texto que también está oculto!!

```
Financial Report for ABC Labs, Kigali, Rwanda for the year 2021.
Breakdown - Just painted over in MS word.
Cost Benefit Analysis
Credit Debit
This is not the flag, keep looking
Expenses from the
picoCTF{C4n_Y0u_S33_m3_fully}
Redacted document.
```

## Notas adicionales
## Referencias