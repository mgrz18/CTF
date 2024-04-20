## Objetivo
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! The source code for this vault is here: [VaultDoor5.java](https://jupiter.challenges.picoctf.org/static/9505cca05dc00fecead41106370ee619/VaultDoor5.java)

## Pistas
- You may find an encoder/decoder tool helpful, such as https://encoding.tools/
- Read the wikipedia articles on URL encoding and base 64 encoding to understand how they work and what the results look like. 

## Solución
Para este reto nos proporcionan el siguiente código
```java
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";
        return base64Encoded.equals(expected);
    }
}
```

Podemos observar que la contraseña está en la parte de abajo convertida en base 64, y después en codificado URL. Yo realicé un código en python que realiza lo siguiente:
- Decodifica de base64 y lo muestra como codificado url
- Después concatena las 3 cadenas inicialmente proporcionadas para ahora convertirlas de codificado URL a texto plano
- Imprime el resultado de la bandera

```python
import base64
from urllib.parse import unquote

a = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
b = "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
c = "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1"

da = base64.b64decode(a).decode('utf-8')
db = base64.b64decode(b).decode('utf-8')
dc = base64.b64decode(c).decode('utf-8')

decoded = ''.join([da, db, dc])
decoded_url = unquote(decoded)
print(decoded)
print(decoded_url)
```

Finalmente:
```powershell
C:\Users\mgarcia\Desktop>python vault5.py
%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%38%34%66%64%35%30%39%35
c0nv3rt1ng_fr0m_ba5e_64_84fd5095
```

## Notas

## Referencias
- [Cyberchef for Help](https://cyberchef.org/#recipe=URL_Decode()&input=JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1)
- [URL decoder python library](https://pypi.org/project/URLDecoder/)
- [Decode from base 64 with python](https://stackoverflow.com/questions/3470546/how-do-you-decode-base64-data-in-python#3470583)