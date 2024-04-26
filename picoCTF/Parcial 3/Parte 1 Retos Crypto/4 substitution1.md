## Objetivo
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again. Download the message [here](https://artifacts.picoctf.net/c/183/message.txt).

## Pistas
- Try a frequency attack
- Do the punctuation and the individual words help you make any substitutions?

## Solución
Igual que en el anterior reto, tenemos un cifrado de sustitución dentro del texto

```powershell
C:\Users\mgarcia\Desktop\pico>curl -O https://artifacts.picoctf.net/c/183/message.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   638  100   638    0     0    969      0 --:--:-- --:--:-- --:--:--   989

C:\Users\mgarcia\Desktop\pico>type message.txt
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
C:\Users\mgarcia\Desktop\pico>
```

Para determinar que se encuentra dentro de el, ejecuté la herramienta usada para el ejercicio pasado, mostrando la siguiente salida:

```
Key to decrypt the message: JSQWRVAUKETCBZFXPMLINOHGYD
Key used to encrypt the message: GMLZJOXWTAISRUVQCEBKHFDPYN
Decrypted text
CTFS (SHORT FOR CAPTURE THE FLAG) ARE A TYPE OF COMPUTER SECURITY COMPETITION. CONTESTANTS ARE PRESENTED WITH A SET OF CHALLENGES WHICH TEST THEIR CREATIVITY, TECHNICAL (AND GOOGLING) SKILLS, AND PROBLEM-SOLVING ABILITY. CHALLENGES USUALLY COVER A NUMBER OF CATEGORIES, AND WHEN SOLVED, EACH YIELDS A STRING (CALLED A FLAG) WHICH IS SUBMITTED TO AN ONLINE SCORING SERVICE. CTFS ARE A GREAT WAY TO LEARN A WIDE ARRAY OF COMPUTER SECURITY SKILLS IN A SAFE, LEGAL ENVIRONMENT, AND ARE HOSTED AND PLAYED BY MANY SECURITY GROUPS AROUND THE WORLD FOR FUN AND PRACTICE. FOR THIS PROBLEM, THE FLAG IS: PICOCTF{FR3JU3NCY_4774CK5_4R3_C001_6E0659FB}
```

Como última correción, una parte del código de la bandera dice Frejuency, yo solo cambié la j por una q y la bandera pasó a ser válida.
## Notas

## Referencias
