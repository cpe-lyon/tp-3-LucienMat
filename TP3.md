# Compte-rendu TP 3
## Lucien Mathieu

### **Exercice 1 : Commandes de base**
1. <u>Mettre à jour le système :</u>\
``apt update`` :
Mettre à jour l’index des dépôts \
``apt upgrade`` :
Mettre à jour les paquets qui le peuvent \
Ne pas oublier de rajouter ``sudo`` si on a pas les droits.

2. <u>Création d'un alias:</u>\
``alias nom_de_alias= 'commande de l'alias'``\
A écrire dans le fichier .bashrc ou .bash_aliases : \
```nano .bashrc``` : pour accéder au fichier où on va écrire l'alias.\
On écris l'alias :
```
alias maj='sudo apt update && sudo apt upgrade'
``` 
Bien mettre sudo sur les commandes. On fait ensuite un ``crtl x`` pour enregistrer les changements. Une fois sorti du fichier, on fait ``source .bashrc`` pour compiler.\
On peut lancer l'alias : 
```
maj //pas besoin de sudo ils sont déjà dans les commandes
``` 
3. <u>Liste des paquets installés:</u>\
La liste des paquets en texte est stockée dans /var/log/dpkg.log
```
tail -n 5 /var/log/dpkg.log
```
`tail` affiche les dernières lignes de texte d'un fichier, avec -n 5 on prend les 5 dernières.\

Méthode prof :\
`grep installed /var/log/dpkg.log | tail -5 | cut -d' ' -f5 | cut -d: -f1`\
cut correspond à un délimiteur. Ici on coupe selon les espaces, et on prend le 5ème champ. Ensuite on coupe au : et on récupère le 1er champ :\
`1.`<strike>2021-11-15</strike> `2.`<strike>10:06:08</strike> `3.`<strike>status</strike>  `4.`<strike>installed</strike>  `5.+1.`<u>python3-pil</u> `2.`<strike>:amd64 7.0.0-4ubuntu0.4</strike>

4. <u>Liste des paquets apt `apt install`:</u>
```
apt list installed
```
On cherche les paquets installés avec apt install.

5. <u>Compter les paquets installés:</u>\
Méthode avec apt : `sudo apt list --installed | sudo wc -l`\
On récupère la liste des paquets insallés avec `--installed` puis on compte le nombre de ligne avec `wc -l`. On obtient 596 paquets.\
Méthode avec dpkg : `sudo dpkg -l | sudo wc -l`\
Même principe avec la commande `dpkg list`. On obtient 600 paquets 

6. <u>Nombre de paquets disponibles:</u>\
Pour avoir la liste de tout les paquets disponible on peut faire `sudo apt list` et pour avoir leur nombre :  `sudo apt | wc -l`. Il y en a 67506.

7. <u>Tests des paquets glances, tldr et hollywood:</u>
```
apt install glances tldr hollywood
```
<u>glances</u> : renseigne sur les pérformances de l'ordinateur (CPU, MEM, NETWORK ect) et l'arborescence des fichiers utilisés.\
<u>tldr</u> : un manuel alternatif redigé par la communauté.\
<u>hollywood</u> : simule un faux code digne des films. Très pratique pour faire genre.

8. <u>Insaller un package sudoku:</u>
```
sudo apt instal sudoku
```
Il y a déjà un paquet sudoku qui existe. Attention à ne pas prendre gnome-sudoku ou ksudoku

### **Exercice 2**
On cheche à obtenir le paquet d'origine de la commande ls. 