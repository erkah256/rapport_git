# Dépôt local

## Initialisation d'un dépôt

On commence par créer un répertoire Toto que l'on initialise comme un dépôt
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto
$ mkdir bob

Rudy@Hermes MINGW64 /d/masterCCI/Toto
$ cd bob

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob
$ git init
Initialized empty Git repository in D:/masterCCI/Toto/bob/.git/
```
## Affichage de l'état du dépôt nouvellement créé
On vérifie l'état du dépôt avec la commande git status.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
## Ajout de fichiers

On ajoute trois fichiers dans le répertoire contenant les fichiers du dépôt.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ echo "Premier fichier" >> f1.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ echo "Second fichier" >> f2.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ echo ls >> liste.txt
```

Ces trois fichiers sont ajoutés à l'arbre du dépôt à l'aide de la commande add.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git add f1.txt
warning: LF will be replaced by CRLF in f1.txt.
The file will have its original line endings in your working directory.

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git add f2.txt
warning: LF will be replaced by CRLF in f2.txt.
The file will have its original line endings in your working directory.

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git add liste.txt
warning: LF will be replaced by CRLF in liste.txt.
The file will have its original line endings in your working directory.
```

La commande git status permet de vérifier que ces fichiers ont bien été ajoutés.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   f1.txt
        new file:   f2.txt
        new file:   liste.txt
```

## Validation des modifications

On réalise un premier commit à l'aide de la command git commit.

```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git commit -am "premier commit"
warning: LF will be replaced by CRLF in f1.txt.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in f2.txt.
The file will have its original line endings in your working directory.
warning: LF will be replaced by CRLF in liste.txt.
The file will have its original line endings in your working directory.
[master (root-commit) 21c07c2] premier commit
 3 files changed, 3 insertions(+)
 create mode 100644 f1.txt
 create mode 100644 f2.txt
 create mode 100644 liste.txt
```

Afin de pouvoir se repérer dans les évolutions du projet, on ajoute à ce commit un tag servant à l'identifier.

```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git tag v1
```

## Evolutions du projet

On réalise plusieurs évolution, chacune suivie d'un commit associé à un tag.

On commence par modifier f2.txt.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ echo "Second fichier version 2" >> f2.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   f2.txt

no changes added to commit (use "git add" and/or "git commit -a")

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git commit -am  "modif de f2"
warning: LF will be replaced by CRLF in f2.txt.
The file will have its original line endings in your working directory.
[master a643457] modif de f2
 1 file changed, 1 insertion(+)
 ```
 Un fichier f3.txt est ajouté et l'on étiquette la modification correspondante avec le tag v2.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ echo "Troisième fichier" >> f3.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git add f3.txt
warning: LF will be replaced by CRLF in f3.txt.
The file will have its original line endings in your working directory.

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   f3.txt


Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git commit -am  "ajout de f3"
[master a317aa4] ajout de f3
 1 file changed, 1 insertion(+)
 create mode 100644 f3.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git tag v2
```

On renomme f3.txt en f4.txt.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git mv f3.txt f4.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        renamed:    f3.txt -> f4.txt


Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git commit -am  "renommage de f3 en f4"
[master 059e0a0] renommage de f3 en f4
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename f3.txt => f4.txt (100%)

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git tag v3
```

f2 est alors supprimé
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git rm f2.txt
rm 'f2.txt'

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        deleted:    f2.txt


Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git commit -am  "suppression de f2"
[master 94d98a3] suppression de f2
 1 file changed, 2 deletions(-)
 delete mode 100644 f2.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git tag v4
```

## Affichage de l'historique des modifications

La commande git log permet d'afficher les commitssuccessifs avec leurs tags respectifs et leurs messages.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git log
commit 94d98a30bc2220e519ea8aa14286adc34e444e32 (HEAD -> master, tag: v4)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:25 2018 +0200

    suppression de f2

commit 059e0a0707668efba55841ad7c33561a764bf146 (tag: v3)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:25 2018 +0200

    renommage de f3 en f4

commit a317aa45c036bb472e52d250e60a10d271b626c2 (tag: v2)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:24 2018 +0200

    ajout de f3

commit a643457c17e7c6cb4d28da55d5eb0a1e2cc1f971
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:23 2018 +0200

    modif de f2

commit 21c07c2be5ce03bd1463e5a91839e7af95e0b330 (tag: v1)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:22 2018 +0200

    premier commit
```

## Supprimer les modifications courantes et retour sur un commit précédent

On décide de revenir en arrière en sélectionnant le commit v2, correspondant à l'ajout du fichier f3.txt.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git reset v2
Unstaged changes after reset:
D       f2.txt
D       f3.txt
```
L'affichage du statut permet de vérifier que dans ce commit, la suppresion de f2.txt et la renommage f4.txt survenus ensuite ne sont pas prises en compte.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    f2.txt
        deleted:    f3.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        f4.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

## Suppression de commits précédents

On se place sur le commit v3 et on surpprime les commits ultérieurs (commande git reset), ainsi que les modifications qu'ils ont apportées (option --hard)
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git reset --hard v3
HEAD is now at 059e0a0 renommage de f3 en f4
```
On vérifie que ces suppressions ont bien été prises en compte.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/bob (master)
$ git log
commit 059e0a0707668efba55841ad7c33561a764bf146 (HEAD -> master, tag: v3)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:25 2018 +0200

    renommage de f3 en f4

commit a317aa45c036bb472e52d250e60a10d271b626c2 (tag: v2)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:24 2018 +0200

    ajout de f3

commit a643457c17e7c6cb4d28da55d5eb0a1e2cc1f971
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:23 2018 +0200

    modif de f2

commit 21c07c2be5ce03bd1463e5a91839e7af95e0b330 (tag: v1)
Author: erkah256 <erkah256@gmail.com>
Date:   Tue Oct 2 20:57:22 2018 +0200

    premier commit
```


