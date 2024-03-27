## Objetivo
Can you get the flag? Go to this website and see what you can discover.
http://saturn.picoctf.net:50920/

## Pistas
How is the password checked on this website?

## Solución
Si nosotros nos ponemos a inspeccionar el código de la página Web, nos daremos cuenta de que hay un archivo que se llama _**login.php**_ entonces abrimos ese código, dentro de el, hay una función.

```php
if ( usernameFilterPassed && passwordFilterPassed ) {
      
        loggedIn = checkPassword(window.username, window.password);
        
        if(loggedIn)
        {
          document.getElementById('msg').innerHTML = "Log In Successful";
          document.getElementById('adminFormHash').value = "2196812e91c29df34f5e217cfd639881";
          document.getElementById('hiddenAdminForm').submit();
        }
        else
        {
          document.getElementById('msg').innerHTML = "Log In Failed";
        }
      }
      else {
        document.getElementById('msg').innerHTML = "Illegal character in username or password."
      }
```

Podemos ver que hay una función que se llama _**loggedIn = checkPassword(window.username, window.password);**_ pero no está dentro de ese código, lo que si existe es una referencia a un código que se llama secure.js, que ¡oh sorpresa!, contiene la contraseña

```javascript
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}


```
## Notas adicionales
## Referencias