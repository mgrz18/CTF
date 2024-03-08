## Objetivo
Who doesn't love cookies? Try to figure out the best one. http://mercury.picoctf.net:29649/

## Solución
En este nivel, nosotros sabemos que el sitio web nos solicita ingresar el nombre de alguna galleta para ver si coincide con una galleta previamente registrada que nos arroje la bandera que nosotros estamos buscando.

Cada que nosotros ingresamos el nombre de una galleta, podemos observar que se almacena una cookie de manera local en nuestro navegador, por ejemplo si nosotros ingresamos el nombre de la galleta que está ahí en un gris tenue, podemos ver que se almacena una cookie con el valor de 1, pero si nosotros editamos la cookie por el número 2 podemos ver que en el campo de texto nos aparece una galleta con un valor diferente, aquí es donde nosotros podemos observar que podemos aprovecharnos de eso y editar la cookie a nuestro favor, así podemos modificar la cookie al número 20 por ejemplo, y ver que contiene, esta oportunidad nos permite crear un código como el siguiente y de esta manera revisar cada cookie que hay hasta encontrar el resultado que nosotros estamos bsucando.

```bash
gr18-picoctf@webshell:~$ for i in {0..20}; do curl -s http://mercury.picoctf.net:29649/check -H "Cookie: name=$i"; done | grep "pico"
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_a1f5bdb7}</code></p>
gr18-picoctf@webshell:~$
```


## Notas

## Referencias
