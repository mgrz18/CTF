### Objetivo
La contraseña para el siguiente nivel se almacena en un archivo Léame en el directorio de inicio. Desafortunadamente, alguien ha modificado .bashrc para cerrar tu sesión cuando inicias sesión con SSH.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
- Usuario: bandit18
### Solución

```bash
C:\Users\Miguel García\Desktop>ssh -l bandit18 bandit.labs.overthewire.org -p 2220 /bin/bash
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password:

ls
readme
cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

### Notas adicionales

Al final de la conexión SSH nosotros podemos añadir la ejecución de un comando, lo que permite ejecutar otra shell para poder realizar lo que ocupemos
### Referencias
