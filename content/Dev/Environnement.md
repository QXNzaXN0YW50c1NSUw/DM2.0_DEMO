+++
title = "Environnement"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
tags = ['Critère 1', 'Critère 2']
+++


## Architecture des sources

Le fichier `mini-pki.ps1` est le script PowerShell permettant de créer
une PKI. Il contient tout ce qui est nécessaire à :

-   La création d'un certificat de la root CA

-   La création utilisateur de certificat de chiffrement ou de signature

-   La création et la mise à jour de la CRL

-   La création du certificat nécessaire au serveur OCSP.

## Modules

Afin de mettre en œuvre une PKI, nous avons utilisé l'utilitaire
cryptographique `OpenSSL`. Cette boîte à outils permet en effet de
générer des certificats, les signer, les révoquer ou encore lancer un
serveur OCSP. Il faut ainsi installer OpenSSL sur les machines Windows
de notre domaine.\

## Téléchargement et installation d'OpenSSL

La première étape consiste à télécharger l'exécutable permettant
d'installer OpenSSL. Il faut tout d'abord se rendre sur la page wiki
d'OpenSSL, pour savoir où télécharger l'exécutable. Il faut pour cela se
rendre à l'url suivante : <https://wiki.openssl.org/index.php/Binaries>.
Sur le tableau - montré sur la figure ci-dessous - cliquer sur le lien
encadré en rouge sur la figure :


![Tableau du wiki OpenSSL montrant les distributions binaires tierces
liées à OpenSSL](OpenSSL/2.png)


Cliquer sur le bouton *EXE* de la cellule *Win64 OpenSSL v1.1.1b* -
prendre la plus récente version :


![Tableau listant les exécutables par architecture](OpenSSL/3.png)


Cliquer sur *Oui* dans la fenêtre \"Setup\" :


![Fenêtre de téléchargement du composant *Microsoft Visual C++ 2017
Redistributables (64-bit)*](OpenSSL/4.png)


Cliquer sur *Enregistrer le fichier* :


![Fenêtre de téléchargement du composant *Microsoft Visual C++ 2017
Redistributables (64-bit)*](OpenSSL/5.png)


Cocher \"*J'accepte les conditions générales de la licence*\", puis
cliquer sur *Installer* :


![Fenêtre de lancement d'installation du composant *Microsoft Visual C++
2017 Redistributables (64-bit)*](OpenSSL/6.png)


Cliquer sur *Fermer* :


![Fenêtre de fin de téléchargement du composant *Microsoft Visual C++
2017 Redistributables (64-bit)*](OpenSSL/7.png)


Cocher \"*I accept the agreement*\", puis cliquer sur *Next* :


![Fenêtre pour accepter la licence pour OpenSSL](OpenSSL/8.png)


Cliquer sur *Next* :


![Fenêtre de sélection du chemin de destination de l'installation
d'OpenSSL](OpenSSL/9.png)


Cliquer sur *Next* :


![Fenêtre de sélection du dossier du menu démarrer](OpenSSL/10.png)


Cocher l'option \"*The OpenSSL binaries (/bin) directory*\" puis cliquer
sur *Next* :


![Fenêtre de sélection de tâches additionnelles](OpenSSL/11.png)


Cliquer sur *Install* :


![Fenêtre d'installation d'OpenSSL](OpenSSL/12.png)


Décocher toutes les options, puis cliquer sur *Finish* :


![Fenêtre de fin d'installation d'OpenSSL](OpenSSL/13.png)


## Configuration d'OpenSSL

Ouvrir le panneau de configuration, aller dans la section *Système et
sécurité*, puis aller dans *Système*. Cliquer sur \"*Paramètres système
avancés*\" :


![Section Système du panneau de configuration](OpenSSL/14.png)


Aller dans l'onglet \"Paramètres système avancés\" et cliquer sur
*Variables d'environnement\...* :


![Fenêtre de propriétés système](OpenSSL/15.png)


Sélectionner la ligne de la variable `Path`, puis cliquer sur *Modifier*
:


![Fenêtre des variables d'environnement](OpenSSL/16.png)


Ajouter \"`;C:\Program Files\OpenSSL-Win64\bin`\" à la valeur de la
variable, puis cliquer sur *Ok* :


![Fenêtre de modification de la variable système](OpenSSL/17.png)


Cliquer sur *Ok* :


![Fenêtre des variables d'environnement](OpenSSL/18.png)


Cliquer sur *Ok* :


![Fenêtre de propriétés système](OpenSSL/19.png)


## Exécution du script

Afin de récupérer les scripts PowerShell sur les machines virtuelles, il
est possible d'utiliser la fonctionnalité de partage de fichiers de
VirtualBox. Il est alors possible de partager un dossier présent sur la
machine hôte avec la machine virtuelle. Les deux sections suivantes
déroulent la procédure d'installation.

## Installer Additions Invité

Allumer l'une des deux machines virtuelles Windows et s'y connecter.
Dans l'onglet `Périphériques`, choisir \"Installer l'image CD des
Additions invité\...\" :


![Bouton périphériques de VirtualBox](Partage_de_dossier/1.PNG)



![Bouton permettant d'installer les éléments nécessaires au partage de
fichiers](Partage_de_dossier/2.PNG)


Ouvrir le gestionnaire de fichiers, et aller dans la section **Ce PC**.
Double cliquer sur l'icône VirtualBox :


![Icône pour installer les Additions Invité](Partage_de_dossier/3.PNG)


L'exécutable se met en route. Cliquer sur *Suivant* :


![Page d'accueil de l'installation des Additions
Invité](Partage_de_dossier/4.PNG)


Cliquer sur *Suivant* :


![Chemin de destination de l'installation des Additions
Invité](Partage_de_dossier/5.PNG)


Cliquer sur *Suivant* :


![Choix des composants à installer avec les Additions
Invité](Partage_de_dossier/6.PNG)


Attendre la fin de l'installation des Additions invité :


![Installation des Additions Invité](Partage_de_dossier/7.PNG)


Sélectionner l'option `Redémarrer maintenant` et cliquer sur *Terminer*
:


![Installation des Additions Invité terminée](Partage_de_dossier/8.PNG)


Si l'icône des Additions invité n'est pas un exécutable mais un dossier,
aller dans le dossier puis double cliquer sur l'exécutable sélectionné
sur la figure suivante :


![Exécutable situé dans le dossier Additions
Invité](Partage_de_dossier/9.PNG)


Ensuite, cliquer sur *Oui* sur la fenêtre générée :


![Demande d'accord pour autoriser l'application à
s'installer](Partage_de_dossier/10.PNG)


Enfin, suivre la procédure telle que décrite précédemment et redémarrer
la machine.

## Configurer le partage de fichiers

Une fois la machine redémarrée, aller dans `Périphériques`, puis
`Dossiers partagés`. Cliquer sur *Réglages des dossiers partagés* :


![Accès à la configuration du partage de
fichiers](Partage_de_dossier/11.PNG)


Aller dans la section **Dossiers partagés**. Sélectionner la ligne
*Dossiers permanents*, puis cliquer sur l'icône de dossier avec le plus
:


![Page de configuration du partage de
fichiers](Partage_de_dossier/12.PNG)


Donner le chemin du dossier à partager ; cocher *Montage automatique* et
*Configuration permanente*. Cliquer sur *OK* :


![Configuration du partage de fichiers](Partage_de_dossier/13.PNG)


Cliquer sur *OK* :


![Page de configuration du partage de fichiers après la
configuration](Partage_de_dossier/14.PNG)


Redémarrer la machine virtuelle.

Lorsque la machine a redémarré, ouvrir le gestionnaire de fichiers. Le
disque réseau est créé, et contient les fichiers partagés entre la
machine hôte et la machine virtuelle :


![Gestionnaire de fichiers avec le disque réseau
créé](Partage_de_dossier/15.PNG)


## Exécution du script

Par défaut, la police d'exécution Windows est en mode `Restricted`, cela
signifie qu'il n'est pas possible d'exécuter un script PowerShell.
Ainsi, afin d'avoir la possibilité d'exécuter le script, il faut
contourner la police d'exécution. La solution choisie est de lancer le
script avec la commande suivante :

``` powershell
powershell -ExecutionPolicy Bypass .\mini-pki.ps1 <arguments...>
```

Il n'y a alors pas besoin d'utiliser la commande
`Set-ExecutionPolicy`{.powershell} pour changer le mode afin d'exécuter
le script, puis de le remettre en `Restricted`.

Également, les fichiers de configuration *openssl-ca.cnf* et
*openssl-user.cnf* doivent se situer dans le même dossier que le script
*mini-pki.ps1*. De plus, il ne faut pas lancer le script *mini-pki.ps1*
dans le dossier partagé. En effet, le champ 'nsRevocationUrl' nous
oblige à mettre les trois fichiers *openssl-ca.cnf*, *openssl-user.cnf*
et *mini-pki.ps1*, dans le dossier `C:\User\admin`, et lancer le script
dans celui-ci.

