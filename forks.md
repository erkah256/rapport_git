# Forks

## Exercice 1

### Réalisation d'un fork

![](figures/depot_forked.png)

On commence par forker le dépôt public "DepotThomas" de Thomas. On nomme "DepotThomasCopie" le fork puis on le clone dans un dépôt local.

```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto
$ git clone http://gogs.m2cci.sciences.univ-tours.fr/rudy.kajdan/DepotThomas_copie.git
Cloning into 'DepotThomas_copie'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.

Rudy@Hermes MINGW64 /d/masterCCI/Toto
$ ls
'batch collabo githu.sh'   batch2.sh   DepotCollabo/        rudy.txt
'batch collabo.sh'         batch3.sh   DepotThomas_copie/
 batch.sh                  bob/        repdistant/

Rudy@Hermes MINGW64 /d/masterCCI/Toto
$ cd depotthomas_copie

Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ ls
README.md
```
### Mise à jour du dépôt forké

On ajoute ensuite un nouveau fichier nommé "rudy.txt" dans le dépôt forké.
```bash
Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ echo "modifications de rudy" >> rudy.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ git add rudy.txt
warning: LF will be replaced by CRLF in rudy.txt.
The file will have its original line endings in your working directory.

Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   rudy.txt


Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ git commit -am "modif de rudy"
[master 92e3c5e] modif de rudy
 1 file changed, 1 insertion(+)
 create mode 100644 rudy.txt

Rudy@Hermes MINGW64 /d/masterCCI/Toto/depotthomas_copie (master)
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 295 bytes | 295.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To http://gogs.m2cci.sciences.univ-tours.fr/rudy.kajdan/DepotThomas_copie.git
   abd47af..92e3c5e  master -> master
```

### Pull request

![](figures/demande_pull_request.png)

On fait un pull request (figure ci-dessus). Après acceptation, on constate que le dépôt d'origine et le dépôt forké se sont bien synchronisés. (figure ci-dessous)

![](figures/apres_acceptation.png)


## Exerice 2








