+++
title = "Mise en place de l'architecture"
date = 2021-12-15T01:10:29+01:00
weight = 3
chapter = false
tags = ['Critère 1', 'Critère 2']
+++

## VirtualBox

L'architecture du projet est construite via un outil de virtualisation.
Nous utilisons VirtualBox.

### Adresse du fichier d'installation

VirtualBox est disponible à cette adresse :
<https://www.virtualbox.org/wiki/Downloads>\
Dans la section \"*VirtualBox \<version> plateform packages*\", choisir
son système d'exploitation.

### Procédure d'installation

Merci de bien vouloir suivre la partie 1.6 de
<https://download.virtualbox.org/virtualbox/6.0.4/UserManual.pdf> pour
pouvoir installer l'outil.

### Utilisation

Merci de bien vouloir lire la partie 1.7 de
<https://download.virtualbox.org/virtualbox/6.0.4/UserManual.pdf> pour
pouvoir utiliser VirtualBox.

## Pfsense

### Adresse du fichier d'installation

Pfsense est disponible à cette adresse :
<https://www.pfsense.org/download/>

Comme le montre la figure [154](#1){reference-type="ref" reference="1"}
:

1.  Choisir votre architecture, AMD64 pour une architecture 64bits;

2.  Choisir ISO;

3.  Télécharger le contenu.\


![Récupération de l'ISO de Pfsense](Archi1/Pfsense_Screeshots/pfsense.png){#1}


###### 

### Procédure d'installation

Afin d'obtenir une machine virtuelle opérationnelle, il faut suivre les
étapes suivantes.

Créer la nouvelle machine virtuelle :


![Création d'une nouvelle machine virtuelle pour
Pfsense](Archi1/Pfsense_Screeshots/1.png){#2}


Nommer la machine virtuelle `pfSense`, de type `BSD` et comme version,
`FreeBSD (64-bit)`. Cliquer sur *Suivant* :


![Initialisation d'une nouvelle machine virtuelle
Pfsense](Archi1/Pfsense_Screeshots/2.png){#3}


Attribuer la RAM qui sera allouée pour cette machine ; 1024 Mo
suffisent. Cliquer sur *Suivant* :


[\[4\]]{#4 label="4"} ![image](Archi1/Pfsense_Screeshots/3.png)


Choisir de créer un disque dur virtuel maintenant. Cliquer sur *Créer* :


[\[5\]]{#5 label="5"} ![image](Archi1/Pfsense_Screeshots/4.png)


Choisir VDI comme type de disque dur. Cliquer sur *Suivant* :


[\[6\]]{#6 label="6"} ![image](Archi1/Pfsense_Screeshots/5.png)


Choisir l'option \"Dynamiquement alloué\". Cliquer sur *Suivant* :


[\[7\]]{#7 label="7"} ![image](Archi1/Pfsense_Screeshots/6.png)


Choisir un emplacement de la machine virtuelle ; 8 Go suffisent. Cliquer
sur *Créer* :


[\[8\]]{#8 label="8"} ![image](Archi1/Pfsense_Screeshots/9.png)


Ouvrir le menu de configuration :


[\[9\]]{#9 label="9"} ![image](Archi1/Pfsense_Screeshots/Configuration.png)


Accéder à **Stockage** :


[\[10\]]{#10 label="10"} ![image](Archi1/Pfsense_Screeshots/10.png)


Dans stockage, choisir l'ISO pfSense téléchargé précédemment :


[\[11\]]{#11 label="11"} ![image](Archi1/Pfsense_Screeshots/11.png)


### Configuration des interfaces réseaux de la machine virtuelle

Pour pouvoir accéder au réseau interne et externe, il faut :

Accéder au menu **Réseau** de la configuration, volet *Interface 1*,
puis cocher `Activer l’interface réseau`. Il faut aussi mettre comme
mode d'accès réseau : `Accès par pont`. Enfin, choisir le nom de sa
carte réseau ayant un accès à internet :


[\[12\]]{#12 label="12"} ![image](Archi1/Pfsense_Screeshots/12.png)


Accéder au volet *Interface 2*, puis cocher
`Activer l’interface réseau`. Il faut de plus choisir le mode d'accès
réseau comme `Réseau interne`, dont le nom doit être \"*pfsense*\".
Enfin, cliquer sur *OK* :


[\[13\]]{#13 label="13"} ![image](Archi1/Pfsense_Screeshots/13.png)


### Procédure d'installation

Démarrer la machine virtuelle Pfsense. Attendre que la commande
s'exécute seule ou appuyer sur la touche `Entrée` :


![Menu de démarrage de
Pfsense](Archi1/Pfsense_Screeshots/Install/1.PNG){#Pfsense_Install/1}


Attendre la fin de l'initialisation de Pfsense :


![Lancement de
Pfsense](Archi1/Pfsense_Screeshots/Install/2.PNG){#Pfsense_Install/2}


Appuyer sur la touche `Entrée` :


![Acceptation de la licence
Pfsense](Archi1/Pfsense_Screeshots/Install/3.PNG){#Pfsense_Install/3}


Sélectionner l'option \"Install pfSense\". Appuyer sur la touche
`Entrée` :


![Demande sur le comportement attendu de la session actuelle
Pfsense](Archi1/Pfsense_Screeshots/Install/4.PNG){#Pfsense_Install/4}


Sélectionner la configuration clavier en utilisant les flèches haut et
bas. Une fois la configuration choisie, sélectionner *Select* avec les
flèches, puis appuyer sur la touche `Entrée` :


![Choix de la configuration clavier de
Pfsense](Archi1/Pfsense_Screeshots/Install/5.PNG){#Pfsense_Install/5}


Sélectionner \"\>\>\> Continue with \... keymap\", tout en haut de
l'écran. Sélectionner *Select* avec les flèches et appuyer sur la touche
`Entrée` :


![Confirmation du choix de configuration clavier de
Pfsense](Archi1/Pfsense_Screeshots/Install/6.PNG){#Pfsense_Install/6}


Sélectionner l'option \"Auto (UFS) Guided Disk Setup\". Sélectionner
*OK* avec les flèches, puis appuyer sur la touche `Entrée` :


![Choix du type de partitionnage du disque de la machine virtuelle
Pfsense](Archi1/Pfsense_Screeshots/Install/7.PNG){#Pfsense_Install/7}


Attendre que l'installation se déroule :


![Installation de
Pfsense](Archi1/Pfsense_Screeshots/Install/8.PNG){#Pfsense_Install/8}


Sélectionner *No* avec les flèches, puis appuyer sur la touche `Entrée`
:


![Demande d'ouverture d'un shell à la fin de l'installation de
Pfsense](Archi1/Pfsense_Screeshots/Install/9.PNG){#Pfsense_Install/9}


Sélectionner *Reboot* avec les flèches, puis appuyer sur la touche
`Entrée` :


![Fin de l'installation de
Pfsense](Archi1/Pfsense_Screeshots/Install/10.PNG){#Pfsense_Install/10}


Éteindre la machine virtuelle quand celle-ci commence à se rallumer.
Accéder au menu de **Stockage** du menu de configuration de la machine
Pfsense (**1**). Suivre les étapes à l'aide des chiffres sur la figure
[14](#Pfsense_Install/11){reference-type="ref"
reference="Pfsense_Install/11"}. Sélectionner le disque Pfsense (**2**
et **3**), et cliquer sur \"Retirer le disque du lecteur virtuel\"
(**4**) :


![Section Stockage du menu de configuration de
Pfsense](Archi1/Pfsense_Screeshots/Install/11.PNG){#Pfsense_Install/11}


Redémarrer la machine virtuelle Pfsense. Attendre que la commande
s'exécute seule ou appuyer sur la touche `Entrée` :


![Menu de démarrage de
Pfsense](Archi1/Pfsense_Screeshots/Install/12.PNG){#Pfsense_Install/12}


Taper `n` à la question : \"Should VLANs be set up now \[y\|n\]?\", et
appuyer sur la touche `Entrée` :


![Configuration VLANs de
Pfsense](Archi1/Pfsense_Screeshots/Install/13.PNG){#Pfsense_Install/13}


Taper le nom de l'interface WAN. Ici, *em0*, puis appuyer sur la touche
`Entrée` :


![Choix de l'interface WAN de
Pfsense](Archi1/Pfsense_Screeshots/Install/14.PNG){#Pfsense_Install/14}


Appuyer sur la touche `Entrée` lors de la question sur la configuration
de l'interface LAN :


![Choix de l'interface LAN de
Pfsense](Archi1/Pfsense_Screeshots/Install/15.PNG){#Pfsense_Install/15}


Taper `y` pour confirmer la configuration réalisée, puis appuyer sur la
touche `Entrée` :


![Confirmation des configurations
précédentes](Archi1/Pfsense_Screeshots/Install/16.PNG){#Pfsense_Install/16}


Arrêter la machine en tapant `6`, puis `y`, et en appuyant sur la touche
`Entrée` :


![Arrêt de la machine virtuelle
Pfsense](Archi1/Pfsense_Screeshots/Install/17.PNG){#Pfsense_Install/17}


## Windows Server 2012

### Adresse du fichier d'installation

L'ISO de Windows Server 2012 est disponible à l'url suivante :
<https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2012?filetype=ISO>

### Procédure d'installation de l'ISO dans la machine virtuelle

Créer la nouvelle machine virtuelle :


![Création d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/1.png){#Windows_Server/1}


Nommer la machine virtuelle `Windows Server 2012`, de type
`Microsoft Windows` et comme version, `Other Windows (64-bit)`. Cliquer
sur *Suivant* :


![Initialisation d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/2.png){#Windows_Server/2}


Attribuer la RAM qui sera allouée pour cette machine ; 2048 Mo
suffisent. Cliquer sur *Suivant* :


![Attribution de la RAM d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/3.png){#Windows_Server/3}


Choisir de créer un disque dur virtuel maintenant. Cliquer sur *Créer* :


![Attribution d'un disque d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/4.png){#Windows_Server/4}


Choisir VDI comme type de disque dur. Cliquer sur *Suivant* :


![Attribution du type de disque d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/5.png){#Windows_Server/5}


Choisir l'option \"Dynamiquement alloué\". Cliquer sur *Suivant* :


![Attribution du type d'espace disque d'une nouvelle machine virtuelle
Windows Server](Archi1/WS_Screenshots/6.png){#Windows_Server/6}


Choisir un emplacement de la machine virtuelle ; 20 Go suffisent.
Cliquer sur *Créer* :


![Attribution de l'espace disque d'une nouvelle machine virtuelle
Windows Server](Archi1/WS_Screenshots/7.png){#Windows_Server/7}


Ouvrir le menu de configuration :


![Configuration d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/8.png){#Windows_Server/8}


Accéder à **Stockage**. Choisir l'ISO WinServer 2012 téléchargée
précédemment :


![Attribution de l'ISO d'une nouvelle machine virtuelle Windows
Server](Archi1/WS_Screenshots/9.png){#Windows_Server/9}


### Configuration de l'interface réseau de la machine virtuelle

Pour pouvoir accéder au réseau interne, il faut :

Accéder au menu **Réseau** de la configuration, volet *Interface 1*, et
cocher `Activer l’interface réseau`. Il faut ensuite choisir le mode
d'accès réseau : `Réseau interne`. Le nom doit être : *pfsense*. Enfin,
cliquer sur *OK* :


![Configuration de l'interface réseau de la nouvelle machine virtuelle
Windows Server](Archi1/WS_Screenshots/10.png){#Windows_Server/10}


### Installation de Windows 2012

Lancer la machine virtuelle Windows Server 2012. Renseigner les champs :


![Initialisation de l'installation de Windows Server
2012](Archi1/WS2012_Screenshots/1.png){#WS2012_Screenshots/1}


Cliquer sur *Installer maintenant* :


![Lancement de l'installation de Windows Server
2012](Archi1/WS2012_Screenshots/2.png){#WS2012_Screenshots/2}


Sélectionner la deuxième option proposée : *Windows Server 2012 Standard
Evaluation (expérience de bureau)*. Cliquer sur *Suivant* :


![Sélection du système d'exploitation à installer de Windows Server
2012](Archi1/WS2012_Screenshots/3.png){#WS2012_Screenshots/3}


Lire \"Avis et conditions du contrat de licence applicables\". Si vous
êtes en accord avec ce texte, cocher la case \"J'accepte les termes du
contrat de licence\". Cliquer sur *Suivant* :


![Acceptation du contrat de licence de Windows Server
2012](Archi1/WS2012_Screenshots/4.png){#WS2012_Screenshots/4}


Choisir l'option : *Personnalisé : installer uniquement Windows
(avancé)* :


![Type d'installation de Windows Server
2012](Archi1/WS2012_Screenshots/5.png){#WS2012_Screenshots/5}


Choisir le lecteur 0. Cliquer sur *Suivant* :


![Sélection du lecteur de Windows Server
2012](Archi1/WS2012_Screenshots/6.png){#WS2012_Screenshots/6}


Attendre pendant l'installation de Windows :


![Installation de Windows Server
2012](Archi1/WS2012_Screenshots/7.png){#WS2012_Screenshots/7}


Créer un nouveau mot de passe pour le compte Administrateur :


![Ecran de verrouillage de Windows Server
2012](Archi1/WS2012_Screenshots/8.png){#WS2012_Screenshots/8}


Se connecter avec le nouveau mot de passe :


![Accès à la session Administrateur de Windows Server
2012](Archi1/WS2012_Screenshots/9.png){#WS2012_Screenshots/9}


Cliquer sur `Oui` :


![Acceptation du partage réseau de Windows Server
2012](Archi1/WS2012_Screenshots/10.png){#WS2012_Screenshots/10}


Cliquer droit sur le logo des réseaux puis cliquer sur *Ouvrir les
paramètres réseau et Internet* :


![Ouverture du centre réseau et partage de Windows Server
2012](Archi1/WS2012_Screenshots/11.png){#WS2012_Screenshots/11}


Dans la section **Ethernet**, cliquer sur *Centre Réseau et partage*.
Dans la nouvelle fenêtre, cliquer sur *Modifier les paramètres de la
carte* :


![Modification des paramètres de la carte sur Windows Server
2012](Archi1/WS2012_Screenshots/12.png){#WS2012_Screenshots/12}


Cliquer droit sur la carte Ethernet. Cliquer sur *Propriétés* :


![Accès aux propriétés de la carte réseau sur Windows Server
2012](Archi1/WS2012_Screenshots/13.png){#WS2012_Screenshots/13}


Décocher `Protocole Internet version 6 (TCP/IPv6)`. Cliquer sur
`Protocole Internet version 4 (TCP/IPv4)` puis sur *Propriétés* :


![Modification et accès aux propriétés IPv4 de la carte réseau sur
Windows Server 2012](Archi1/WS2012_Screenshots/14.png){#WS2012_Screenshots/14}


Configurer les adresses IP comme suit :

-   Adresse IP : 192.168.2.2;

-   Masque de sous-réseau : 255.255.255.0;

-   Passerelle par défaut : 192.168.2.1.

Aussi, configurer l'adresse du serveur DNS préféré avec : 8.8.8.8.
Cliquer sur *OK* :


![Paramétrage de l'IPv4 de la carte réseau sur Windows Server
2012](Archi1/WS2012_Screenshots/15.png){#WS2012_Screenshots/15}


Cliquer sur *Fermer* :


![Fermeture des propriétés de la carte réseau sur Windows Server
2012](Archi1/WS2012_Screenshots/16.png){#WS2012_Screenshots/16}


## Windows

### Adresse du fichier d'installation

L'ISO de Windows 10 Entreprise est disponible à cette adresse :
<https://www.microsoft.com/fr-fr/evalcenter/evaluate-windows-10-enterprise1>

### Procédure d'installation

Créer la nouvelle machine virtuelle :


![Création d'une nouvelle machine virtuelle pour Windows
10](Archi1/W_Screenshots/1.png){#W_Screenshots/1}


Nommer la machine virtuelle `Windows 10`, de type `Microsoft Windows` et
comme version, `Windows (64-bit)`. Cliquer sur *Suivant* :


![Initialisation de la nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/2.png){#W_Screenshots/2}


Attribuer la RAM qui sera allouée pour cette machine ; 2048 Mo
suffisent. Cliquer sur *Suivant* :


![Attribution de la RAM de la nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/3.png){#W_Screenshots/3}


Choisir de créer un disque dur virtuel maintenant. Cliquer sur *Suivant*
:


![Attribution d'un disque d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/4.png){#W_Screenshots/4}


Choisir VDI comme type de disque dur. Cliquer sur *Suivant* :


![Attribution du type de disque d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/5.png){#W_Screenshots/5}


Choisir l'option \"Dynamiquement alloué\". Cliquer sur *Suivant* :


![Attribution du type d'espace disque d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/6.png){#W_Screenshots/6}


Choisir un emplacement de la machine virtuelle arbitrairement ; 20 Go
suffisent. Cliquer sur *Créer* :


![Attribution de l'espace disque d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/7.png){#W_Screenshots/7}


Ouvrir le menu de configuration :


![Configuration d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/8.png){#W_Screenshots/8}


Accéder à **Stockage**. Choisir l'ISO Windows 10 téléchargée
précédemment :


![Attribution de l'ISO d'une nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/9.png){#W_Screenshots/9}


### Configuration de l'interface réseau de la machine virtuelle

Pour pouvoir accéder au réseau interne, il faut:

Accéder au menu **Réseau** de la configuration, volet *Interface 1*, et
cocher `Activer l’interface réseau`. Il faut ensuite choisir le mode
d'accès réseau : `Réseau interne`. Le nom doit être \"*pfsense*\".
Enfin, cliquer sur *OK* :


![Configuration de l'interface réseau de la nouvelle machine virtuelle
Windows](Archi1/W_Screenshots/10.png){#W_Screenshots/10}


### Installation de Windows

Lancer la machine virtuelle Windows 10 :


![Démarrage de la machine virtuelle Windows
10](Archi1/W_Screenshots/11.png){#W_Screenshots/11}


Renseigner les champs demandés, puis cliquer sur *Suivant* :


![Initialisation de Windows 10](Archi1/W_Screenshots/12.png){#W_Screenshots/12}


Cliquer sur *Installer maintenant* :


![Confirmation de l'installation Windows
10](Archi1/W_Screenshots/13.png){#W_Screenshots/13}


Cliquer sur \"Je n'ai pas de clé de produit (Product Key)\" :


![Activation de Windows 10](Archi1/W_Screenshots/14.png){#W_Screenshots/14}


Sélectionner l'option suivante : *Windows 10 Professionnel pour les
Stations de travail*. Cliquer sur *Suivant* :


![Sélection du système d'exploitation de Windows
10](Archi1/W_Screenshots/15.png){#W_Screenshots/15}


Lire \"Avis et conditions du contrat de licence applicables\". Si vous
êtes en accord avec ce texte, cocher la case \"J'accepte les termes du
contrat de licence\". Cliquer sur *Suivant* :


![Avis et conditions du contrat de licence applicables de Windows
10](Archi1/W_Screenshots/16.png){#W_Screenshots/16}


Choisir l'option : *Personnalisé : installer uniquement Windows
(avancé)* :


![Type d'installation de Windows
10](Archi1/W_Screenshots/17.png){#W_Screenshots/17}


Choisir le lecteur 0. Cliquer sur *Suivant* :


![Choix du lecteur de Windows
10](Archi1/W_Screenshots/18.png){#W_Screenshots/18}


Attendre pendant l'installation de Windows :


![Installation de Windows 10](Archi1/W_Screenshots/19.png){#W_Screenshots/19}


Écran de présentation de Windows 10 :


![Présentation de Windows 10](Archi1/W_Screenshots/20.png){#W_Screenshots/20}


Choisir la région de la machine, puis cliquer sur *Oui* :


![Choix de la région de Windows
10](Archi1/W_Screenshots/21.png){#W_Screenshots/21}


Choisir la disposition du clavier, puis cliquer sur *Oui* :


![Choix de la disposition de clavier de Windows
10](Archi1/W_Screenshots/22.png){#W_Screenshots/22}


Possibilité d'ignorer l'ajout d'une deuxième disposition de clavier en
cliquant sur *Ignorer* :


![Choix d'une deuxième disposition de clavier de Windows
10](Archi1/W_Screenshots/23.png){#W_Screenshots/23}


Cliquer sur *Ignorer pour le moment* :


![Connexion à un réseau sur Windows
10](Archi1/W_Screenshots/24.png){#W_Screenshots/24}


Donner un nom d'utilisateur, puis cliquer sur *Suivant* :


![Nom d'utilisateur de Windows
10](Archi1/W_Screenshots/25.png){#W_Screenshots/25}


Choisir un mot de passe pour l'utilisateur, puis cliquer sur *Suivant* :


![Choix du mot de passe de l'utilisateur de Windows
10](Archi1/W_Screenshots/26.png){#W_Screenshots/26}


Confirmer le mot de passe saisi précédemment. Cliquer sur *Suivant* :


![Confirmation du mot de passe de l'utilisateur Windows
10](Archi1/W_Screenshots/27.png){#W_Screenshots/27}


Sélectionner la première question de sécurité de l'utilisateur et
renseigner sa réponse. Cliquer sur *Suivant* :


![Première question de sécurité de l'utilisateur de Windows
10](Archi1/W_Screenshots/28.png){#W_Screenshots/28}


Sélectionner la deuxième question de sécurité de l'utilisateur et
renseigner sa réponse. Cliquer sur *Suivant* :


![Deuxième question de sécurité de l'utilisateur de Windows
10](Archi1/W_Screenshots/29.png){#W_Screenshots/29}


Sélectionner la troisième question de sécurité de l'utilisateur et
renseigner sa réponse. Cliquer sur *Suivant* :


![Troisième question de sécurité de l'utilisateur de Windows
10](Archi1/W_Screenshots/30.png){#W_Screenshots/30}


Cliquer sur *Refuser* pour désactiver l'utilisation de Cortana :


![Choix de l'utilisation de Cortana de Windows
10](Archi1/W_Screenshots/31.png){#W_Screenshots/31}


Cliquer sur *Non* pour ne pas activer l'historique des activités Windows
10 :


![Historique des activités de Windows
10](Archi1/W_Screenshots/32.png){#W_Screenshots/32}


Sélectionner l'option \"Ne pas utiliser la reconnaissance vocale en
ligne\". Cliquer sur *Accepter* :


![Reconnaissance vocale de Windows
10](Archi1/W_Screenshots/33.png){#W_Screenshots/33}


Sélectionner l'option \"Non\", puis cliquer sur *Accepter* :


![Partage des données de géolocalisation avec les applications de
Windows 10](Archi1/W_Screenshots/34.png){#W_Screenshots/34}


Sélectionner l'option \"Non\", puis cliquer sur *Accepter* :


![Partage des données de géolocalisation de Windows
10](Archi1/W_Screenshots/35.png){#W_Screenshots/35}


Sélectionner l'option \"Basique\", puis cliquer sur *Accepter* :


![Envoi des données de diagnostic de Windows
10](Archi1/W_Screenshots/36.png){#W_Screenshots/36}


Sélectionner l'option \"Non\", puis cliquer sur *Accepter* :


![Partage de données sur l'écriture et la saisie de Windows
10](Archi1/W_Screenshots/37.png){#W_Screenshots/37}


Sélectionner l'option \"Non\", puis cliquer sur *Accepter* :


![Obtention d'expériences personnalisées avec des données de diagnostic
de Windows 10](Archi1/W_Screenshots/38.png){#W_Screenshots/38}


Sélectionner l'option \"Non\", puis cliquer sur *Accepter* :


![Partage de l'identifiant de publicité de Windows
10](Archi1/W_Screenshots/39.png){#W_Screenshots/39}


### Utilisation

Se connecter à la machine virtuelle Windows 10 nouvellement créée et
installée, via le nom d'utilisateur renseigné lors de l'installation, et
le mot de passe associé, tel que sur la figure suivante :


![Connexion au compte utilisateur USER01 de Windows
10](Archi1/W_Screenshots/40.png){#W_Screenshots/40}


## Linux MINT

### Installation de Linux Mint

Double-cliquer sur l'icône représentant un disque, nommé \"Install Linux
Mint\" :


![Ecran d'accueil Linux
Mint](Archi1/Mint_Screenshots/1.png){#Mint_Screenshots/1}


Sélectionner la langue pour l'installation, puis cliquer sur *Continuer*
:


![Choix de la langue - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/2.png){#Mint_Screenshots/2}


Choisir la disposition du clavier, puis cliquer sur *Continuer* :


![Disposition du clavier - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/3.png){#Mint_Screenshots/3}


Cocher l'option pour installer les logiciels tiers, puis cliquer sur
*Continuer* :


![Installation des logiciels tiers - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/4.png){#Mint_Screenshots/4}


Sélectionner \"Effacer le disque et installer Linux Mint\", puis cocher
les deux options suivant ce choix. Cliquer sur *Continuer* :


![Type d'installation - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/5.png){#Mint_Screenshots/5}


Choisir une clé de sécurité pour le chiffrement du disque, cocher
\"Ecraser l'espace disque vide\", puis cliquer sur *Installer
maintenant* :


![Choix de la clé de sécurité - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/6.png){#Mint_Screenshots/6}


Confirmer votre choix en cliquant sur *Continuer* :


![Confirmation du choix du chiffrement - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/7.png){#Mint_Screenshots/7}


Sélectionner le fuseau horaire vous correspondant, puis cliquer sur
*Continuer* :


![Sélection du fuseau horaire - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/8.png){#Mint_Screenshots/8}


Créer un nouvel utilisateur, tel que montré sur la figure ci-dessous.
Cliquer sur *Continuer* :


![Création de l'utilisateur de Linux
Mint](Archi1/Mint_Screenshots/9.png){#Mint_Screenshots/9}


Attendre la fin de l'installation de Linux Mint :


![Installation de Linux Mint - Assistant d'installation Linux
Mint](Archi1/Mint_Screenshots/10.png){#Mint_Screenshots/10}


Une fois l'installation terminée, cliquer sur *Redémarrer maintenant*
sur la nouvelle fenêtre :


![Redémarrage du système pour la finalisation de l'installation de Linux
Mint](Archi1/Mint_Screenshots/11.png){#Mint_Screenshots/11}


Attendre la fin de l'installation de Linux Mint :


![Finalisation de l'installation de Linux
Mint](Archi1/Mint_Screenshots/12.png){#Mint_Screenshots/12}


Écran demandant la clé de déchiffrement du disque :


![Accès à Linux Mint](Archi1/Mint_Screenshots/13.png){#Mint_Screenshots/13}


Écran de déchiffrement du disque :


![Déchiffrement du disque de Linux
Mint](Archi1/Mint_Screenshots/14.png){#Mint_Screenshots/14}


Se connecter en entrant les identifiants de l'utilisateur créé lors de
l'installation :


![Accès à la session Linux Mint sur
L01](Archi1/Mint_Screenshots/15.png){#Mint_Screenshots/15}


Page d'accueil à la première connexion sur Linux Mint :


![Ecran de bienvenue de Linux
Mint](Archi1/Mint_Screenshots/16.png){#Mint_Screenshots/16}


## Debian

### Adresse du fichier d'installation

L'ISO de Debian 9.9 est disponible à cette adresse :
<https://cdimage.debian.org/debian-cd/current/multi-arch/iso-cd/debian-9.9.0-amd64-i386-netinst.iso>

### Procédure d'installation

Nommer la machine virtuelle - ici nous avons opté pour \"Debian DM4\" -
puis choisir le type `Linux`, avec pour version `Debian (64-bits)`.
Cliquer sur *Suivant* :


![Initialisation d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/1.png){#Debian_screenshots/Install/1}


Attribuer la RAM qui sera allouée pour cette machine ; 1024 Mo
suffisent. Cliquer sur *Suivant* :


![Attribution de la RAM d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/2.png){#Debian_screenshots/Install/2}


Choisir de créer un disque dur virtuel maintenant. Cliquer sur *Suivant*
:


![Attribution d'un disque d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/3.png){#Debian_screenshots/Install/3}


Choisir VDI comme type de disque dur. Cliquer sur *Suivant* :


![Attribution du type de disque d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/4.png){#Debian_screenshots/Install/4}


Choisir l'option \"Dynamiquement alloué\". Cliquer sur *Suivant* :


![Attribution du type d'espace disque d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/5.png){#Debian_screenshots/Install/5}


Choisir l'emplacement de la machine virtuelle, ainsi que la taille du
disque dur virtuel ; 8 Go suffisent. Cliquer sur *Créer* :


![Attribution de l'espace disque d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/6.png){#Debian_screenshots/Install/6}


Ouvrir le menu de configuration :


![Configuration d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/7.png){#Debian_screenshots/Install/7}


Accéder à **Stockage**. Choisir l'ISO Debian téléchargée précédemment :


![Attribution de l'ISO d'une nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/8.png){#Debian_screenshots/Install/8}


### Installation de Debian

Démarrer la machine virtuelle Debian :


![Démarrage de la nouvelle machine virtuelle
Debian](Archi1/Debian_screenshots/Install/9.png){#Debian_screenshots/Install/9}


Sélectionner l'option `Graphical install` en s'aidant des flèches.
Appuyer sur la touche `Entrée` :


![Démarrage de l'installation graphique de
Debian](Archi1/Debian_screenshots/Install/10.png){#Debian_screenshots/Install/10}


Sélectionner la langue utilisée pour l'installation de Debian. Cliquer
sur la langue - \"French\" ici - puis cliquer sur *Continue* :


![Sélection du langage d'installation de
Debian](Archi1/Debian_screenshots/Install/11.png){#Debian_screenshots/Install/11}


Choisir la situation géographique. Les choix sont basés par rapport au
choix précédent. Cliquer sur *France*, puis sur *Continuer* :


![Sélection de la situation géographique pour définir le fuseau horaire
et les paramètres régionaux du système
Debian](Archi1/Debian_screenshots/Install/12.png){#Debian_screenshots/Install/12}


Configurer la disposition du clavier. Sélectionner *Français*, puis
cliquer sur *Continuer* :


![Configuration de la disposition du clavier du système
Debian](Archi1/Debian_screenshots/Install/13.png){#Debian_screenshots/Install/13}


Attendre la fin du chargement des composants d'installation :


![Chargement des composants d'installation de
Debian](Archi1/Debian_screenshots/Install/14.png){#Debian_screenshots/Install/14}


Ensuite, la fenêtre pour la configuration réseau s'ouvre. La première
étape est d'indiquer le nom du système en installation. Ici,
\"INFRA01\". Cliquer sur *Continuer* :


![Saisie du nom du système Debian - configuration
réseau](Archi1/Debian_screenshots/Install/15.png){#Debian_screenshots/Install/15}


Laisser le champ du domaine vide, et cliquer sur *Continuer* :


![Saisie du domaine du système Debian - configuration
réseau](Archi1/Debian_screenshots/Install/16.png){#Debian_screenshots/Install/16}


La fenêtre suivante consiste en la création du mot de passe du
superutilisateur 'root'. Le mot de passe doit respecter les bonnes
pratiques de l'ANSSI. Une fois le mot de passe choisi, cliquer sur
*Continuer* :


![Saisie du mot de passe du superutilisateur - création des
utilisateurs](Archi1/Debian_screenshots/Install/17.png){#Debian_screenshots/Install/17}


Donner le nom complet de l'utilisateur en création. Dans la figure
ci-dessous, nous avons entré \"User01\". Cliquer sur *Continuer* :


![Saisie du nom complet du compte utilisateur - création des
utilisateurs](Archi1/Debian_screenshots/Install/18.png){#Debian_screenshots/Install/18}


Donner un identifiant pour le compte utilisateur. Dans la figure
suivante, nous avons entré \"user01\". Cliquer sur *Continuer* :


![Saisie de l'identifiant du compte utilisateur - création des
utilisateurs](Archi1/Debian_screenshots/Install/19.png){#Debian_screenshots/Install/19}


Comme pour le superutilisateur, définir un mot de passe pour
l'utilisateur \"user01\" en création. Ce mot de passe doit respecter les
bonnes pratiques de l'ANSSI. Cliquer sur *Continuer* :


![Saisie du mot de passe du compte utilisateur - création des
utilisateurs](Archi1/Debian_screenshots/Install/20.png){#Debian_screenshots/Install/20}


Attendre la fin du chargement de configuration de l'horloge :


![Configuration de
l'horloge](Archi1/Debian_screenshots/Install/21.png){#Debian_screenshots/Install/21}


La fenêtre suivante s'occupe du partitionnement des disques.
Sélectionner la première option : *Assisté - utiliser un disque entier*,
puis cliquer sur *Continuer* :


![Sélection de la méthode de partitionnement - partitionnement des
disques](Archi1/Debian_screenshots/Install/22.png){#Debian_screenshots/Install/22}


Sélectionner le disque à partitionner, puis cliquer sur *Continuer* :


![Sélection du disque à partitionner - partitionnement des
disques](Archi1/Debian_screenshots/Install/23.png){#Debian_screenshots/Install/23}


Ensuite, sélectionner le schéma de partitionnement \"*Tout dans une
seule partition (recommandé pour les débutants)*\", puis cliquer sur
*Continuer* :


![Sélection du schéma de partitionnement - partitionnement des
disques](Archi1/Debian_screenshots/Install/24.png){#Debian_screenshots/Install/24}


Vérifier que la configuration ressemble à celle de la figure suivante,
puis sélectionner \"*Terminer le partitionnement et appliquer les
changements*\". Cliquer sur *Continuer* :


![Fin de la configuration de partitionnement des disques -
partitionnement des
disques](Archi1/Debian_screenshots/Install/25.png){#Debian_screenshots/Install/25}


Choisir *Oui* puis cliquer sur *Continuer* :


![Application des changements sur les disques - partitionnement des
disques](Archi1/Debian_screenshots/Install/26.png){#Debian_screenshots/Install/26}


Patienter pendant l'installation du système :


![Installation du système de
base](Archi1/Debian_screenshots/Install/27.png){#Debian_screenshots/Install/27}


Ensuite, choisir *Non* dans la fenêtre de configuration de l'outil de
gestion des paquets, puis cliquer sur *Continuer* :


![Configuration de l'outil de gestion des
paquets](Archi1/Debian_screenshots/Install/28.png){#Debian_screenshots/Install/28}


Sélectionner le pays du miroir de l'archive Debian le plus proche. Ici,
sélectionner \"France\". Cliquer sur *Continuer* :


![Sélection du pays du miroir de l'archive Debian - configuration de
l'outil de gestion des
paquets](Archi1/Debian_screenshots/Install/29.png){#Debian_screenshots/Install/29}


Sélectionner le miroir de l'archive Debian. Ici `ftp.fr.debian.org`.
Cliquer sur Continuer :


![Sélection du miroir de l'archive Debian - configuration de l'outil de
gestion des
paquets](Archi1/Debian_screenshots/Install/30.png){#Debian_screenshots/Install/30}


Laisser le champ sur le mandataire HTTP vide, et cliquer sur *Continuer*
:


![Saisie du mandataire HTTP - configuration de l'outil de gestion des
paquets](Archi1/Debian_screenshots/Install/31.png){#Debian_screenshots/Install/31}


Attendre la fin de la configuration de l'outil de gestion des paquets :


![Application de la configuration de l'outil de gestion des
paquets](Archi1/Debian_screenshots/Install/32.png){#Debian_screenshots/Install/32}


Sélectionner *Non* pour la configuration de popularity-contest, et
cliquer sur *Continuer* :


![Configuration de
popularity-contest](Archi1/Debian_screenshots/Install/33.png){#Debian_screenshots/Install/33}


Attendre la fin de l'installation des logiciels :


![Sélection et installation des
logiciels](Archi1/Debian_screenshots/Install/34.png){#Debian_screenshots/Install/34}


Ensuite, sélectionner les options comme sur la figure suivante :
\"*environnement de bureau Debian*\", \"*serveur d'impression*\" et
\"*utilitaires usuels du système*\", ainsi que \"*serveur SSH*\".
Cliquer sur *Continuer* :


![Sélection des logiciels à
installer](Archi1/Debian_screenshots/Install/35.png){#Debian_screenshots/Install/35}


Patienter jusqu'à la fin de la configuration et de l'installation des
logiciels :


![Installation des
logiciels](Archi1/Debian_screenshots/Install/36.png){#Debian_screenshots/Install/36}


Sélectionner *Oui* pour installer le programme de démarrage GRUB sur le
secteur d'amorçage. Cliquer sur *Continuer* :


![Choix de l'installation du programme de démarrage GRUB sur le secteur
d'amorçage](Archi1/Debian_screenshots/Install/37.png){#Debian_screenshots/Install/37}


Sélectionner le périphérique où sera installé le programme de démarrage
GRUB, tel que montré sur la figure ci-dessous. Cliquer sur *Continuer* :


![Sélection du périphérique sur lequel sera installé le programme de
démarrage
GRUB](Archi1/Debian_screenshots/Install/38.png){#Debian_screenshots/Install/38}


Attendre la fin de l'installation du programme de démarrage GRUB sur le
disque dur :


![Installation du programme de démarrage
GRUB](Archi1/Debian_screenshots/Install/39.png){#Debian_screenshots/Install/39}


Cliquer sur *Continuer* afin de terminer l'installation :


![Fenêtre de fin
d'installation](Archi1/Debian_screenshots/Install/40.png){#Debian_screenshots/Install/40}


Attendre que la machine redémarre :


![Redémarrage de la machine après la fin de
l'installation](Archi1/Debian_screenshots/Install/41.png){#Debian_screenshots/Install/41}


Une fois la machine redémarrée, il est possible de se connecter en tant
que `User01`, comme montré sur la figure suivante :


![Fenêtre de connexion à la machine
Debian](Archi1/Debian_screenshots/Install/42.png){#Debian_screenshots/Install/42}


## MISP

### Adresse du fichier d'installation

Une machine virtuelle MISP est mise à disposition à l'adresse :
<https://www.circl.lu/misp-images/latest/> Pour VirtualBox, il faut
télécharger le fichier OVA.\
Avant de procéder à l'importation de la machine virtuelle, il faut
vérifier l'intégrité du fichier téléchargé. La signature de ce fichier
est également disponible, dans le fichier ayant pour extension :
\"`.ova.asc`\". La méthode pour vérifier les signatures se trouve dans
le fichier *verify.txt*, mis à disposition. Sur la figure suivante sont
mis en exergue les trois fichiers concernés :


![Récupération de la machine virtuelle MISP mise à
disposition](Archi1/MISP_Screenshots/Prerequis/1.PNG){#1}


### Procédure d'installation

Dans VirtualBox, il faut commencer par *Importer un appareil virtuel*,
en cliquant sur \"*Fichier*\" puis sur *Importer un appareil
virtuel\...*, tel que sur la figure suivante :


![Importation de la machine virtuelle MISP
téléchargée](Archi1/MISP_Screenshots/Mise_en_place/2.PNG){#1}


Il faut ensuite choisir le fichier OVA concerné ; celui téléchargé
précédemment, puis cliquer sur *Suivant \>* :


![Sélection du fichier OVA
téléchargé](Archi1/MISP_Screenshots/Mise_en_place/3.PNG){#1}


Les caractéristiques de la machine virtuelle sont listées. Il est
possible de modifier chacun des champs, en double-cliquant dessus, puis
modifier le champ sélectionné. Ici, nous avons changé le nom de la
machine virtuelle à \"SECU01\". Il est également possible de choisir où
seront sauvegardés les fichiers de la machine virtuelle. Cliquer sur
*Importer* :


![Choix des caractéristiques de la machine
virtuelle](Archi1/MISP_Screenshots/Mise_en_place/4.PNG){#1}


Cliquer sur *Accepter* :\


![Acceptation du contrat de licence du logiciel
importé](Archi1/MISP_Screenshots/Mise_en_place/5.PNG){#1}


Attendre pendant l'importation de l'appareil virtuel :


![Importation de l'appareil
virtuel](Archi1/MISP_Screenshots/Mise_en_place/6.PNG){#1}


Démarrer la machine virtuelle \"SECU01\" nouvellement importée. Les
identifiants par défaut de la machine virtuelle sont :

-   MISP Login : misp

-   Mot de passe : Password1234


![Connexion à la machine virtuelle
MISP](Archi1/MISP_Screenshots/Mise_en_place/8.PNG){#1}


## Graylog

Graylog est la solution de gestion de logs centralisée, afin de donner
une autre signification plus visuelle que de simples lignes de texte.

### Adresse d'installation

L'installation de la machine virtuelle est simple : il suffit de se
rendre sur le lien suivant.\
<https://packages.graylog2.org/releases/graylog-omnibus/ova/graylog-2.5.1-1.ova>.\
Ce fichier est une sauvegarde de machine virtuelle prête à l'emploi
qu'il suffit d'importer avec **VirtualBox**.

### Procédure d'installation

De la même manière que pour MISP, il faut commencer par *Importer un
appareil virtuel*, en cliquant sur \"*Fichier*\" puis sur *Importer un
appareil virtuel\...*.

Il faut ensuite choisir le fichier OVA concerné ; celui téléchargé
précédemment, puis cliquer sur *Suivant \>* :


![Sélection du fichier OVA téléchargé](Archi1/graylog_screenshots/4.png){#1}


On peut encore modifier chacun des champs, en double-cliquant dessus,
puis modifier le champ sélectionné. Ici, nous avons aussi changé le nom
de la machine virtuelle à \"SECU02\". Cliquer sur *Importer* :


![Choix des caractéristiques de la machine virtuelle
graylog](Archi1/graylog_screenshots/5.png){#1}


Attendre pendant l'importation de l'appareil virtuel :


![Importation de l'appareil virtuel](Archi1/graylog_screenshots/6.png){#1}


Démarrer la machine virtuelle \"SECU02\" nouvellement importée. Les
identifiants par défaut de la machine virtuelle sont :

-   Login : ubuntu

-   Mot de passe : ubuntu
