### Objetivo
Hay un repositorio git en ssh://bandit30-git@localhost/home/bandit30-git/repo a través del puerto 2220. La contraseña para el usuario bandit30-git es la misma que para el usuario bandit30.

Clona el repositorio y busca la contraseña para el siguiente nivel.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
- Usuario: bandit30
### Solución

```bash
bandit30@bandit:/tmp/hola$ ls                                                                         repo                                                                                                  bandit30@bandit:/tmp/hola$ cd repo/                                                                   bandit30@bandit:/tmp/hola/repo$ ls                                                                    README.md                                                                                             bandit30@bandit:/tmp/hola/repo$ cat README.md                                                         just an epmty file... muahaha                                                                         bandit30@bandit:/tmp/hola/repo$ git log                                                               commit d39631d73f786269b895ae9a7b14760cbf40a99f (HEAD -> master, origin/master, origin/HEAD)          Author: Ben Dover <noone@overthewire.org>                                                             Date:   Thu Oct 5 06:19:45 2023 +0000                                                                                                                                                                           initial commit of README.md                                                                       bandit30@bandit:/tmp/hola/repo$ git branch -a                                                         * master                                                                                                remotes/origin/HEAD -> origin/master                                                                  remotes/origin/master                                                                               bandit30@bandit:/tmp/hola/repo$ git checkout HEAD                                                     Your branch is up to date with 'origin/master'.                                                       bandit30@bandit:/tmp/hola/repo$ ls                                                                    README.md                                                                                             bandit30@bandit:/tmp/hola/repo$ cat README.md                                                         just an epmty file... muahaha                                                                         bandit30@bandit:/tmp/hola/repo$ git tag                                                               secret                                                                                                bandit30@bandit:/tmp/hola/repo$ git show secret                                                       OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt                                                                      bandit30@bandit:/tmp/hola/repo$     
```

### Notas adicionales



### Referencias
