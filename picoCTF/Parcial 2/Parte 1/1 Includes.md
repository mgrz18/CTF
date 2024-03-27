## Objetivo
Can you get the flag? Go to this website and see what you can discover.
http://saturn.picoctf.net:58519/

## Pistas
Is there more code than what the inspector initially shows?

## Solución
En la página hay que inspeccionar el código HTML, la bandera consta de dos partes, la primera está en el archivo css y la segunda en el archivo javascript

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="style.css">
    <title>On Includes</title>
  </head>
  <body>
    <script src="script.js"></script>
  </body>
</html>
```

```css
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */

```

```javascript
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_b8f4b022}

```


## Notas adicionales
## Referencias