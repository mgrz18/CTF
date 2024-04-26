## Objetivo
A musician left us a [message](https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt). What's it mean?

## Pistas
- None

## Solución
El archivo de texto que nos proporciona el músico contiene una cantidad de coordenadas, que nos van a indicar lugares a lo largo del mapa y que nos van a servir para encontrar la bandera utilizando la inicial de cada lugar indicado por las coordenadas.

El archivo se ve de la siguiente manera
```powershell
C:\Users\mgarcia\Desktop\pico>curl -O https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   278  100   278    0     0    543      0 --:--:-- --:--:-- --:--:--   553

C:\Users\mgarcia\Desktop\pico>type message.txt
picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}
C:\Users\mgarcia\Desktop\pico>
```

Primero que nada, hay que acomodar las coordenadas de una manera que sea más cómodo consultarlas:
```
picoCTF{
(35.028309, 135.753082)
(46.469391, 30.740883)
(39.758949, -84.191605)
(41.015137, 28.979530)
(24.466667, 54.366669)
(3.140853, 101.693207)
_
(9.005401, 38.763611)
(-3.989038, -79.203560)
(52.377956, 4.897070)
(41.085651, -73.858467)
(57.790001, -152.407227)
(31.205753, 29.924526)
}
```

Después de ingresar las ubicaciones a google maps, el resultado fue el siguiente:
```
picoCTF{
(35.028309, 135.753082)  Kyoto
(46.469391, 30.740883)   Odessa
(39.758949, -84.191605)  Dayton
(41.015137, 28.979530)   Istanbul
(24.466667, 54.366669)   Abu Dhabi
(3.140853, 101.693207)   Kuala Lumpur
_
(9.005401, 38.763611)    Adis Abeba   
(-3.989038, -79.203560)  Loja 
(52.377956, 4.897070)    Amsterdam    
(41.085651, -73.858467)  Sleepy Hollow  
(57.790001, -152.407227) Kodiak 
(31.205753, 29.924526)   Alexandria   
}

picoCTF{KODIAK_ALASKA}
```

## Notas

## Referencias
