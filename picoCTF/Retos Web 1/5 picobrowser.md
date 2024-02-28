## Objetivo
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/28921/` ([link](https://jupiter.challenges.picoctf.org/problem/28921/)) or http://jupiter.challenges.picoctf.org:28921

## Solución
Con el comando curl podemos modificar los encabezados, en este caso el nivel pide verificar que somos picobrowser, para poder lograr hacer creer al sitio esto, le mandamos el encabezado "User-Agent:picobrowser" 

```powershell
C:\Users\Miguel García>curl https://jupiter.challenges.picoctf.org/problem/28921/flag -H "User-Agent:picobrowser" | findstr pico
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2115  100  2115    0     0   6054      0 --:--:-- --:--:-- --:--:--  6112
         <!-- <strong>Title</strong> --> picobrowser!
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}</code></p>

C:\Users\Miguel García>

```


## Notas

## Referencias