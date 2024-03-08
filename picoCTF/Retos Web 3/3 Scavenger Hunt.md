## Objetivo
There is some interesting information hidden around this site http://mercury.picoctf.net:39698/. Can you find it?

## Solución
Este reto consiste en encontrar la bandera que está almacenada en partes dentro de el sitio web que nos proporcionaron anteriormente, la bandera se puede encontrar en los siguientes sitios:
- index.html
```html
	</p>
	<!-- Here's the first part of the flag: **picoCTF{t** -->
</div>
```
- mycss.css
```css
#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: **h4ts_4_l0** */
```

- myjs.js nos proporciona una pista de algún reto anteriormente ya resuelto, que nos lleva a
```
/* How can I keep Google from indexing my website? */
```

- robots.txt
```
User-agent: *
Disallow: /index.html
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
```

- .htaccess nos permite configurar nuestros directorios y otros archivos para cambiar su apariencia
```
# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there.
```
- .DS_store
```
Congrats! You completed the scavenger hunt. Part 5: _fa04427c}
```
## Notas

## Referencias
https://en.wikipedia.org/wiki/.DS_Store
