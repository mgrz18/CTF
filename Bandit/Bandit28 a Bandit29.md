### Objetivo
Hay un repositorio git en ssh://bandit28-git@localhost/home/bandit28-git/repo a través del puerto 2220. La contraseña para el usuario bandit28-git es la misma que para el usuario bandit28.

Clona el repositorio y busca la contraseña para el siguiente nivel.
### Datos de acceso
- Puerto: 2220
- Dirección: bandit.labs.overthewire.org
- Contraseña: AVanL161y9rsbcJIsFHuw35rjaOM19nR
- Usuario: bandit28
### Solución

```bash
bandit28@bandit:/tmp$ mkdir holamundo1234
bandit28@bandit:/tmp$ cd holamundo1234
bandit28@bandit:/tmp/holamundo1234$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password:
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
bandit28@bandit:/tmp/holamundo1234$ ls
repo
bandit28@bandit:/tmp/holamundo1234$ cd repo/
bandit28@bandit:/tmp/holamundo1234/repo$ ls
README.md
bandit28@bandit:/tmp/holamundo1234/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/holamundo1234/repo$ ssh -l bandit29 bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

bandit29@bandit.labs.overthewire.org: Permission denied (publickey).
bandit28@bandit:/tmp/holamundo1234/repo$ ls -la
total 16
drwxrwxr-x 3 bandit28 bandit28 4096 Feb 22 22:43 .
drwxrwxr-x 3 bandit28 bandit28 4096 Feb 22 22:43 ..
drwxrwxr-x 8 bandit28 bandit28 4096 Feb 22 22:43 .git
-rw-rw-r-- 1 bandit28 bandit28  111 Feb 22 22:43 README.md
bandit28@bandit:/tmp/holamundo1234/repo$ cd -git
-bash: cd: -g: invalid option
cd: usage: cd [-L|[-P [-e]] [-@]] [dir]
bandit28@bandit:/tmp/holamundo1234/repo$ cd .git
bandit28@bandit:/tmp/holamundo1234/repo/.git$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  packed-refs  refs
bandit28@bandit:/tmp/holamundo1234/repo/.git$ cd branches/
bandit28@bandit:/tmp/holamundo1234/repo/.git/branches$ ls
bandit28@bandit:/tmp/holamundo1234/repo/.git/branches$ cd ..
bandit28@bandit:/tmp/holamundo1234/repo/.git$ cat HEAD
ref: refs/heads/master
bandit28@bandit:/tmp/holamundo1234/repo/.git$ cd logs/
bandit28@bandit:/tmp/holamundo1234/repo/.git/logs$ ls
HEAD  refs
bandit28@bandit:/tmp/holamundo1234/repo/.git/logs$ cd ..
bandit28@bandit:/tmp/holamundo1234/repo/.git$ cd ..
bandit28@bandit:/tmp/holamundo1234/repo$ git log
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

commit f08b9cc63fa1a4602fb065257633c2dae6e5651b
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    add missing data

commit a645bcc508c63f081234911d2f631f87cf469258
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    initial commit of README.md
bandit28@bandit:/tmp/holamundo1234/repo$ git checkout f08b9cc63fa1a4602fb065257633c2dae6e5651b
Note: switching to 'f08b9cc63fa1a4602fb065257633c2dae6e5651b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at f08b9cc add missing data
bandit28@bandit:/tmp/holamundo1234/repo$ ls
README.md
bandit28@bandit:/tmp/holamundo1234/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S

bandit28@bandit:/tmp/holamundo1234/repo$
```

### Notas adicionales



### Referencias
