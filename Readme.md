# TP1 - Installation Linux sur une VM - V0.4

## Groupe 

1. Yazan (YAD) 		- Noé (NAM) 
2. Siméon (SAR) 	- Gaëtan (GFR)
3. Tristan (TCK) 	- Nicolas (NTN)
4. Matéo (MCN) 		- Thomas (TBT)
5. Noah (NRN) 		- Guillaume (GFE)
6. Benjamin (BSC) 	- Valentin (VBC)
7. Gabriel (GOM) 	- Nikola (NDC)

## But 

Cette manipulation a pour but d'installer une distribution linux [Sparky Linux](https://sparkylinux.org/) dans une machine virtuelle VMware 
Workstation Player, à l’aide d’une image disque (ISO).

## Materiels à disposition 

- VMware Workstation Player - V17
- Image disque (ISO) : sparkylinux-6.4-x86_64-minimalcli.iso

## Création d’une machine virtuelle 

**A.** Lancez VMware Workstation Player (logiciel)  

**B.** Sélectionnez **Create a New Virtual Machine** 

**C-A.** Placez le fichier `.iso` dans une repertoire connu : 

`C:\VosInitiales\VM\ISO`

**C-B.** Indiquez le chemin d’accès de l’image iso comme indiqué sous l’image ci-dessous :

![install image disk](/Images/Install_ISO.jpg) 

**D-A.** Choisissez un nom d'OS : `Linux - Debian 11.x` 

![OS name choice](Images/OS_Choice.jpg) 

**D-B.** Nommez la machine virtuelle : `SparkyLinux-VosInitiales` 

**E.** Creez un disque virtuel -> capcité : **20GB** 

> Remarque 1 : Cocher **store virtual disk a single file**

![Virtual disk](/Images/VirtualDisk.jpg) 

> Remarque 2 : Ci-dessous, la configuration de la VM 

![Virtual disk](/Images/VM_Config.jpg) 

**F.** Lancez la machine virtuelle : **Play virtual machine** 

## Lancement de l'image ISO (Linux - Live CD) 

**G.** Lancement du live CD : 

![Placer votre capture d'écran](/Capture/G1.png) 

Shell Linux : 

![Placer votre capture d'écran](/Capture/G2.png) 

> **ATTENTION** : par défaut, le clavier est configuré est **Clavier Americain**

Q1. disposition du clavier américain ?

qwerty (en_US)

Q2. disposition du clavier suisse-romand ?

qwertz (fr_CH)

Q3. disposition du le clavier français ? 

azerty (fr) ou (fr_FR)

**H.** Déplacez-vous à la **racine du système** en utilisant la commande suivante : `cd` 

Q4. votre commande ?!

cd /

**I.** Affichez le contenu de la racine avec la commande : `ls –l`	

![Placer votre capture d'écran](/Capture/H.png) 

Q5. Que signifie l'option `-l` avec la commande `ls` 

Affiche le résultat de ls en une list, avec plus d'information (permission de fichier, date de modif etc)

Q6. Décrypter la ligne où se trouve le répertoire **home**    

drwxr-xr-x 1 root root 60 Sep 17 13:11 home

dr -> c'est un dossier
wxr -> les permission du proprio du dossier (Ici write, execute, read)
\-
xr -> permission du group utilisateur dans lequelle le dossier est (Ici execute, read)
\-
x -> permission du reste des utilisateur (ceux qui ne ont pas de le groupe ou pas proprio, Ici execute)

1 -> le dossier a un seul hard link

root -> l'utilisateur root est le proprio

root -> le groupe utilisateur dans lequelle le dossier est

60 -> la taille du dossier

Sep 17 13:11 -> Date de dernier modif 

home -> le dossier

**J.** Créez un répertoire de travail nommé « EMSY_VosInitiales» 

Q7. dans quel dossier racine allez-vous le placer (justifiez votre réponse) 

home/live

Q8. Quelle commande allez-vous utiliser pour faire ceci ?  

mkdir /home/live/EMSY_NRN

**K.** Dans ce répertoire, créez un fichier texte que vous nommerez `TESTSLO_XXX_XXX` et éditez celui en écrivant un texte, exemple : "TP linux by XXX et XXX".
	   Utiliser la commande `vi`

vi /home/live/EMSY_NRN/TESTSLO_NRN

Q9. Pouvez-vous éditez un fichier uniquement avec la commande `vi` 

oui

Q10. Si vous éteignez la machine virtuelle et que vous la rallumez, est-ce que le répertoire créé ci-dessus existe toujours (justifiez votre réponse) ? 

Non car nous somme dans l'ISO, le systeme est actuallement une image chargé du disque, elle n'est pas sauvegarder ??

**L.** Tapez la commande `ls -l /dev/sda` 

![Placer votre capture d'écran](/Capture/K2.png) 

Q11. Que signifie **sda** ? 

Le disque dure (sd)a. SD voulant dire SCSI Disk. a étant la lettre du disque.

Q12. Quelle différence y a-t-il entre le répertoire de la question Q6 et celui du point L (justifiez votre réponse) ?

home est un dossier normal. /dev/sda n'est pas un dossier, c'est un fichier représentant le disque, un pointeur vers le disque. écrir dans le fichier sda reviens a écrir dans le disque.

## Installation de SparkyLinux sur la VM

**M.** Installez SparkyLinux

![Virtual disk](/Images/Screen_Installer_Sparkylinux.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux2.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux3.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux4.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux5.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux6.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux7.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux8.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux9.jpg)
![Virtual disk](/Images/Screen_Installer_Sparkylinux10.jpg)

Pour le nom cours -> noah
Pour le nom longs -> noah
hostname -> sparky

Q13. Quelle est la taille de disque minimum recommandée pour installer la distribution Sparky en mode cli 

2G

Q14. A quoi sert la partition swap ? Est-ce que ce principe existe-t-il sur les OS Microsoft Windows ? 

C'est l'équivalent du Pagefile sur windows. Elle permet d'écrire des données de la ram dans le disque dur.

Q15. Quel format pourriez-vous utiliser pour la 3ème partition afin qu’elle soit également accessible depuis un OS Microsoft ? 

Microsoft basic data (Fat32)

Q16. Durant l’installation, on vous demande deux noms d’utilisateur. A quoi correspondent-ils ? 

Le nom long est le nom complet de l'utilisateur( par ex. John Doe), le nom court est celui qui est utiliser par linux pour référer a l'utilisateur (par ex le dossier home sera le nom court, par ex. john)

**N.** Une fois l’installation de Linux terminée, prenez une capture d’écran du démarrage de votre système (GRUB)

![Placer votre capture d'écran](/Capture/N.png) 

**O.** Trouvez la ou les lignes de commande permettant de changer le clavier et procédez à la configuiration 

sudo nano /etc/default/keyboard, écrir Layout="ch", variant="fr" ou sudo dpkg-reconfigure keyboard-configuration

![Placer votre capture d'écran](/Capture/O1.png) 

![Placer votre capture d'écran](/Capture/O2.png)

![Placer votre capture d'écran](/Capture/O3.png)

![Placer votre capture d'écran](/Capture/O4.png)

![Placer votre capture d'écran](/Capture/O5.png)

![Placer votre capture d'écran](/Capture/O6.png)

**P.** Tapez la commande : `nano -version`

![Placer votre capture d'écran](/Capture/P.png) 

Q17. A quoi sert `nano` ? 

C'est un éditeur de texte

**Q.** Testez si l’application `git` est installée sur votre distribution, si ce n’est pas le cas installez un client git. 

Q18. Comment savoir si `git` est déjà installé ? 

L'on peut simplement essayer d'utiliser la commande git, si elle est présente nous aurons une erreur d'argument manquans, si git n'est pas installer l'erreur seras "command not found"

git

Q19. Si le client `git` n'est pas installé, quelle(s) commande(s) utilisez-vous pour l’installer ? 

sudo apt install git

Q20. Que veut dire `apt` ? 

C'est le package manager (l'installateur de logiciel). Son nom veux dire "Advanced Packaging Tool"

Q21. Est-ce que cette commande (`apt`) peut être utilisée sur toutes les distributions Linux (justifiez votre réponse)? 

Pas tous ! Pas toutes les distros linux utilise le meme package manager, certaine utilise pacman, nix, guix, portage, etc..

**R.** Créez un sous-répertoire « EMSY_TP1_XXX-YYY » dans le répertoire de votre utilisateur. 
       
**Attention** : Ici on veut que l’utilisateur (vous) ait les droits de lecture, d’écriture et d’exécution.

mkdir ~/EMSY_TP1_NRN -m=rwx

Q22. Quel est le répertoire utilisateur ?  

~/ ou /home/noah

Q23. Quelles sont les commandes pour changer les droits d'utilisateurs (lecture - écriture - execution) ?  

chmod u+rwx ~/EMSY_TP1_NRN (u pour l'utilisateur possédent le fichier, a pour tous les utilisateus, g pour les utilisateurs dans le group dans le quelle le fichier est, o pour les utilisateur n'étant pas dans le group du fichier), + pour ajouter une permission (- pour enlever, = pour définir). r pour read, w pour write, x pour execute, X pour appliquer execute a un dossier, s pour change l'UID ou GID, t pour définir le sticky bit.

**S.** Dans ce répertoire, tapez la commande : `git clone https://github.com/votreDepot/EMSY_TP1_Source`

***Remarque*** : Il faut au préalable que vous ayez mis en place à cette adresse un fork du dépôt fourni lors de ce TP.

Q24. Qu’observez-vous dans ce répertoire ?

![Placer votre capture d'écran](/Capture/S.png)

**T.** Editez le fichier source `.c` avec l’éditeur de texte « nano ». -> Réalisez un petit programme en C (par exemple de type « Hello world »).

![Placer votre capture d'écran](/Capture/T.png)

**U.**	Vérifiez si le compilateur `gcc` est bien installé. Notez la version du logiciel

![Placer votre capture d'écran](/Capture/U.png)

**U-A.** Tapez les commandes suivantes :
```Shell 
gcc -Wall -o fichier.o -c fichier.c 
gcc -o fichier fichier.o 
```
Remarque : « fichier » est à remplacer par le nom de votre choix

![Placer votre capture d'écran](/Capture/U-A.png)

Q25. Quels sont les fichiers qui ont été générés 

![Placer votre capture d'écran](/Capture/Q25.png)

**V.** Entrez la commande suivante : `./fichier`

![Placer votre capture d'écran](/Capture/V.png)

Q26. Que se passe-t-il ?

Le program est executé.

...A compléter...

## Tips 

> Tip 1 : sortir de la VM -> appuyer simultanément sur `Ctrl` et `Alt` 

> Tip 2 :  
> Pour arrêter un Linux proprement : 	`shutdown`  
> Pour forcer l’arrêt d’un système :	`halt` ou `poweroff`  
> Seul un administrateur peut exécuter ces commandes !

> Tip 3 : [commande vi avec ses options](https://www.linuxtricks.fr/wiki/guide-de-sur-vi-utilisation-de-vi)

> Tip 4 : [éditer un fichier type markdown (.md)](https://ashki23.github.io/markdown-latex.html)

