## Objetivo
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with nc jupiter.challenges.picoctf.org 39894.

## Pistas
- Flag is not in the usual flag format

## Solución
Cuando realizamos la conexión al servidor con netcat podemos observar que el contiene el siguiente texto.

```powershell
C:\Users\mgarcia\Desktop>ncat jupiter.challenges.picoctf.org 39894
-------------------------------------------------------------------------------
pnrudqef jwdw gf anyd bvqu - bdwtywrpa_gf_p_nlwd_vqkmoq_qubvpueayw
-------------------------------------------------------------------------------
iw iwdw rne kypj kndw ejqr q tyqdewd nb qr jnyd nye nb nyd fjgs egvv iw fqi jwd fgrz, qro ejwr g yrowdfenno bnd ejw bgdfe egkw ijqe iqf kwqre ma q fjgs bnyrowdgru gr ejw fwq.  g kyfe qpzrnivwouw g jqo jqdova wawf en vnnz ys ijwr ejw fwqkwr envo kw fjw iqf fgrzgru; bnd bdnk ejw knkwre ejqe ejwa dqejwd sye kw gren ejw mnqe ejqr ejqe g kguje mw fqgo en un gr, ka jwqde iqf, qf ge iwdw, owqo igejgr kw, sqdeva igej bdguje, sqdeva igej jnddnd nb kgro, qro ejw ejnyujef nb ijqe iqf awe mwbndw kw.
^C
C:\Users\mgarcia\Desktop>
```
Según las pistas es un cifrado por sustitución, por lo que usando algún decifrador de cifrado por sustitución obtenemos el siguiente código.

```
Key to decrypt the message: YFXRTSIZWHMVBODCANPQGLEJUK
Key used to encrypt the message: QMPOWBUJGXZVKRNSTDFEYLICAH

Decrypted text
-------------------------------------------------------------------------------
CONGRATS HERE IS YOUR FLAG - FREQUENCY_IS_C_OVER_LAMBDA_AGFLCGTYUE
-------------------------------------------------------------------------------
WE WERE NOT MUCH MORE THAN A QUARTER OF AN HOUR OUT OF OUR SHIP TILL WE SAW HER SINK, AND THEN I UNDERSTOOD FOR THE FIRST TIME WHAT WAS MEANT BY A SHIP FOUNDERING IN THE SEA.  I MUST ACKNOWLEDGE I HAD HARDLY EYES TO LOOK UP WHEN THE SEAMEN TOLD ME SHE WAS SINKING; FOR FROM THE MOMENT THAT THEY RATHER PUT ME INTO THE BOAT THAN THAT I MIGHT BE SAID TO GO IN, MY HEART WAS, AS IT WERE, DEAD WITHIN ME, PARTLY WITH FRIGHT, PARTLY WITH HORROR OF MIND, AND THE THOUGHTS OF WHAT WAS YET BEFORE ME.
```

## Notas

## Referencias
https://planetcalc.com/8047/
