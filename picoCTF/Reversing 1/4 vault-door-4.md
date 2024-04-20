## Objetivo
This vault uses ASCII encoding for the password. The source code for this vault is here: [VaultDoor4.java](https://jupiter.challenges.picoctf.org/static/834acd392e0964a41f05790655a994b9/VaultDoor4.java)

## Pistas
- Use a search engine to find an "ASCII table".
- You will also need to know the difference between octal, decimal, and hexadecimal numbers.

## Solución
Primero nos proporcionan el siguiente código
```java
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
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

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}
```

Del cual puedo ver que todo está en bases convertido, por lo que con un pequeño código en python podemos arreglarlo
```python
#106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
#0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
#0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
#'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e'

passBytes = [None] * 32
myBytes = [
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            '0x55', '0x6e', '0x43', '0x68', '0x5f', '0x30', '0x66', '0x5f',
            '0o142', '0o131', '0o164', '0o63' , '0o163', '0o137', '0o146' , '0o64' ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
	]

# base10
for i in range(0,8):
	passBytes[i] =  chr(myBytes[i])

# base16
for i in range(8,16):
	#passBytes[i] =  bytearray.fromhex(myBytes[i].replace('0x', '')).decode()
	passBytes[i] =  chr(int(myBytes[i], 16))

# base8
for i in range(16,24):
	passBytes[i] =  chr(int(myBytes[i], 8))

for i in range(24,32):
	passBytes[i] =  myBytes[i]

print("picoCTF{{{}}}".format(''.join(passBytes)))
```

Que nos va a mostrar la siguiente salida:
```powershell
C:\Users\mgarcia\Desktop>python converter.py
picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}
```

## Notas

## Referencias
