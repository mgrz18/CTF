## Objetivo
We have several pages hidden. Can you find the one with the flag? The website is running here.

## Pistas
folders folders folders

## Solución
El primer paso es inspeccionar el código funete, para darse cuenta de que existe un sitio llamado secret
> http://saturn.picoctf.net:64727/secret/

Si nosotros inspeccionamos el código fuente de esa nueva página, podemos observar que existe un nuevo archivo oculto.
> http://saturn.picoctf.net:64727/secret/hidden/

Si lo volvemos a inspeccionar encontraremos otra página oculta
> http://saturn.picoctf.net:64727/secret/hidden/superhidden/

Ahí adentro se encuentra la bandera, que se puede ver seleccionando la página o inspeccionando su código fuente.

## Notas adicionales
## Referencias