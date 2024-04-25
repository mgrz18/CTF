## Objetivo
What can you do with this file? I forgot the key to my safe but this [file](Download and try to decompile the file.) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?

## Pistas
- Download and try to decompile the file.

## Solución
Después de descargar el archivo nos damos cuenta de que es un archivo .class, para descubrir cuál es el código en java contenido usaremos una [herramienta](http://www.javadecompilers.com/) en línea, que nos va a permitir decompilar facilmente el archivo .class, después, el código obtenido sería el siguiente:

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Base64;
import java.util.Base64.Encoder;

public class SafeOpener {
   public static void main(String[] args) throws IOException {
      BufferedReader keyboard = new BufferedReader(new InputStreamReader(System.in));
      Encoder encoder = Base64.getEncoder();
      String encodedkey = "";
      String key = "";

      for(int i = 0; i < 3; ++i) {
         System.out.print("Enter password for the safe: ");
         key = keyboard.readLine();
         encodedkey = encoder.encodeToString(key.getBytes());
         System.out.println(encodedkey);
         boolean isOpen = openSafe(encodedkey);
         if (isOpen) {
            break;
         }

         System.out.println("You have  " + (2 - i) + " attempt(s) left");
      }

   }

   public static boolean openSafe(String password) {
      String encodedkey = "picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_de45efd6}";
      if (password.equals(encodedkey)) {
         System.out.println("Sesame open");
         return true;
      } else {
         System.out.println("Password is incorrect\n");
         return false;
      }
   }
}

```

Finalmente podemos observar que ahí entre el código se encuentra la bandera que estamos buscando.
## Notas

## Referencias
