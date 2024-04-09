**Nom :** PAUNET ANTOINE

**Groupe :** 13

**Année :** 2023-2024

**IUT Le Havre - Cours GIT**

### Compte-rendu TP3 Introduction GIT


Dans ce TP, j’ai demandé de l’aide à un ami afin de pouvoir parvenir au bout de ce TP. J’assumerais le rôle de Athos.

J’ai donc commencé par créer le dépôt tp3 avec les mêmes informations que celui du tp2.

Je suis ensuite aller dans les paramètres de mon dépôt afin d’y ajouter des collaborateurs.

J’y ai ajouter le compte de mon collaborateur puis après avoir accepter l’invitation par mail, nous avons tout les deux pu cloner le dépôt grâce à la commande : 
git clone git@github.com:AntoinePaunet/tp3.git

------------------------------------------------------------------------------------------------------------------------
$ git clone git@github.com:AntoinePaunet/tp3.git
Cloning into 'tp3'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (4/4), done.
------------------------------------------------------------------------------------------------------------------------


Nous vérifions que le tp3 à bien été ajouté :
------------------------------------------------------------------------------------------------------------------------
$ ls
tp1/  tp2/  tp3/
------------------------------------------------------------------------------------------------------------------------


J’ai ensuite placer les README.MD et le src/ dans tp3 afin de le déposer sur github.

------------------------------------------------------------------------------------------------------------------------
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        src/

no changes added to commit (use "git add" and/or "git commit -a")


$ git add *
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it


$ git commit -m "Ajout des documents dans le tp3"
[main 21ffd02] Ajout des documents dans le tp3
 2 files changed, 588 insertions(+), 1 deletion(-)
 create mode 100644 src/Cryptomonnaie.java



$ git push
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 4.91 KiB | 4.91 MiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:AntoinePaunet/tp3.git
   0c161a5..21ffd02  main -> main
------------------------------------------------------------------------------------------------------------------------

Une fois ceci fait, mon collaborateur à pu faire la commande git pull afin de récupérer les fichiers que j’avais envoyé sur le github.




J’ai ensuite placer de nouvelles classes java dans le dossier src/ puis je les ais déposés sur le github :

------------------------------------------------------------------------------------------------------------------------
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        src/CryptoMarche.java
        src/Portefeuille.java
        src/TestCryptoMarche.java

nothing added to commit but untracked files present (use "git add" to track)


$ git add *


$ git commit -m "Ajout de nouvelles classes"
[main 872a832] Ajout de nouvelles classes
 3 files changed, 204 insertions(+)
 create mode 100644 src/CryptoMarche.java
 create mode 100644 src/Portefeuille.java
 create mode 100644 src/TestCryptoMarche.java


$ git push
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 2.36 KiB | 2.36 MiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:AntoinePaunet/tp3.git
   21ffd02..872a832  main -> main
------------------------------------------------------------------------------------------------------------------------


Une fois ceci fait, mon collaborateur à importer les documents sur sa machine locale.



Nous avons ensuite tout les deux compilés les programmes afin de voir si les classes fonctionnent correctement :

------------------------------------------------------------------------------------------------------------------------
Test Portefeuille transfertDevise        ... FAIL
Test Portefeuille achatDevise            ... FAIL
Test CryptoMarche capitalEnEuros         ... FAIL
Test CryptoMarche capitalMonneaie        ... FAIL
------------------------------------------------------------------------------------------------------------------------

Le résultat est bien celui attendu.


J’ai donc compléter la méthode capitalEnEuro sur la classe CryptoMarche pendant que mon collaborateur faisait la méthode de la	classe Portefeuille.

Le code des méthodes est :

------------------------------------------------------------------------------------------------------------------------
    public boolean transfertDevise (Portefeuille destination, double montantJetons)
    {
        System.out.println(this.montant + " " + destination.montant);
        if(this.montant >= montantJetons && this.monnaie == destination.monnaie)
        {
            this.montant -= montantJetons;
            destination.montant += montantJetons;
            return true;
        }
        return false;
    }

------------------------------------------------------------------------------------------------------------------------


------------------------------------------------------------------------------------------------------------------------
    public boolean achatDevise (double montantEuros)
    {
        if(montantEuros >= 0)
        {
            this.montant += montantEuros/this.monnaie.getValeurDeJeton();
            return true;
        }
        return false;
    }
------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------------------
    public double capitalMonneaie(Cryptomonnaie monnaie){

        double total = 0;

        for ( int i = 0 ; i < portefeuilles.size() ; i++ )
        {
            if ( portefeuilles.get(i).getMonnaie() == monnaie )
            {
                total += portefeuilles.get(i).getMontant()*portefeuilles.get(i).getMonnaie().getValeurDeJeton();;
            }
        }

        return total;

    }
------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------------------------------------
    public double capitalEnEuros(String proprietaire){

        double total = 0;

        for ( int i = 0 ; i < portefeuilles.size() ; i++ )
        {
            if ( portefeuilles.get(i).estProprietaire(proprietaire) )
            {
                total += portefeuilles.get(i).getMontant()*portefeuilles.get(i).getMonnaie().getValeurDeJeton();
            }
        }

        return total;
    }
------------------------------------------------------------------------------------------------------------------------





Nous avons donc chacun mis notre code sur le github en faisant la commande :

------------------------------------------------------------------------------------------------------------------------
$ git add src/CryptoMarche.java


$ git commit -m "Ajout de CryptoMarche"
[main c61eb79] Ajout de CryptoMarche
 1 file changed, 22 insertions(+), 8 deletions(-)


$ git push
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 579 bytes | 289.00 KiB/s, done.
Total 4 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To github.com:AntoinePaunet/tp3.git
   872a832..c61eb79  main -> main
------------------------------------------------------------------------------------------------------------------------


Une fois ceci fait, nous avons tout les deux fait un git pull afin de récupérer le code puis nous avons executer le code pour voir que celui-ci marchait :

Test Portefeuille transfertDevise        ... OK
Test Portefeuille achatDevise            ... OK
Test CryptoMarche capitalEnEuros         ... OK
Test CryptoMarche capitalMonneaie        ... OK





Nous avons ensuite décider de créer une nouvelle branche afin de séparer nos projets de test grâce à la commande : git checkout -b test :

------------------------------------------------------------------------------------------------------------------------
$ git checkout -b test
Switched to a new branch 'test'


$ git branch
  main
* test
------------------------------------------------------------------------------------------------------------------------


Nous avons ensuite créer un fichier test dans la branche test :

------------------------------------------------------------------------------------------------------------------------
$ ls
README.md  src/  test.txt


$ git  add test.txt


$ git commit -m "fonction de test ajoutée"
[test 596d912] fonction de test ajoutée
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt

------------------------------------------------------------------------------------------------------------------------

Une fois de retour sur le main avec la commande git checkout main nous avons pu voir avec ls que le fichier test n’était pas présent :

------------------------------------------------------------------------------------------------------------------------
$ ls
README.md  src/
------------------------------------------------------------------------------------------------------------------------


La branche main et test sont donc bien séparées.


Nous allons donc fusionner nos deux branches de test dans la branche principale avec la commande git merge test puis nous avons afficher le contenu de notre branche main : 

------------------------------------------------------------------------------------------------------------------------
$ ls
README.md  src/  test.txt
------------------------------------------------------------------------------------------------------------------------

Comme on peut le voir, le document test.txt viens de réapparaître dans le main.


Nous avons ensuite chacun créé une classe avec notre propre Cryptomonnaie chacun dans une branche différente :


------------------------------------------------------------------------------------------------------------------------
$ git checkout -b AthosCoin
Switched to a new branch 'AthosCoin'


$ git add src/AthosCoin.java


$ git commit -m "Ajout de l'athos coin"
[AthosCoin d3f905a] Ajout de l'athos coin
 1 file changed, 5 insertions(+)
 create mode 100644 src/AthosCoin.java

$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)


$ git merge AthosCoin
Updating 596d912..d3f905a
Fast-forward
 src/AthosCoin.java | 5 +++++
 1 file changed, 5 insertions(+)
 create mode 100644 src/AthosCoin.java


$ ls
AthosCoin.java     Cryptomonnaie.class  Portefeuille.java
CryptoMarche.java  Cryptomonnaie.java   TestCryptoMarche.java

------------------------------------------------------------------------------------------------------------------------

J’ai ensuite envoyé mon dépôt local avec push :


------------------------------------------------------------------------------------------------------------------------
$ git push
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 770 bytes | 385.00 KiB/s, done.
Total 7 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To github.com:AntoinePaunet/tp3.git
   914c036..d3f905a  main -> main
------------------------------------------------------------------------------------------------------------------------


Une fois que mon collaborateur à fini son code je n’ai eu qu’à faire git pull et j’ai ainsi pu récupérer son code pour le PorthosCoin.java.

Une fois ceci fait, mon collaborateur, le dépôt github et moi même avons le même dépôt.




