
## Objetivo
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or http://jupiter.challenges.picoctf.org:44573
## Solución
En este nivel, si nosotros inspeccionamos a detalle el sitio web, en el apartado de red el sitio realiza una solicitud de flag, que solo se muestra cuando el usuario es el administrador, pero, ningún usuario es administrador, lo que el sitio no cuenta es que nosotros podemos editar las cookies. Nosotros podemos observar en el encabezado de flag, hay una leyenda de admin.

Donde solo editamos en encabezado de administrador, de admin=false a admin=true, recargamos el sitio y ahora ya tenemos permisos de administrador.

**Flag**: `picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}`

Alguna solución alternativa
curl https://jupiter.challenges.picoctf.org/problem/44573/flag -H "Cookie:username"

## Notas

## Referencias