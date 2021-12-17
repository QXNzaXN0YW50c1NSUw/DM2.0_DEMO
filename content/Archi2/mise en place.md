+++
title = "Mise en place de l'architecture"
date = 2021-12-15T01:10:29+01:00
weight = 3
chapter = false
tags = ['Installation de la Kali']
+++


## Kali

### Adresse du fichier d'installation

Une machine virtuelle Kali est mise à disposition à l'adresse

Pour VirtualBox, il faut télécharger le fichier OVA. Avant de procéder à
l'importation de la machine virtuelle, il faut vérifier l'intégrité du
fichier téléchargé. La signature de ce fichier est également disponible,
à côté du lien de téléchargement du fichier OVA.\
Sur la figure ci-après sont mis en exergue le fichier à télécharger
ainsi que sa signature. Sélectionner l'onglet **KALI LINUX VIRTUALBOX
IMAGES** pour récupérer l'image VirtualBox de Kali Linux. Ensuite,
cliquer sur la version de Kali voulue - ici la version 64-bit. La
signature de cette image est également disponible afin de vérifier
l'intégrité de l'image :


![Récupération de la machine virtuelle Kali mise à
disposition](Archi2/Kali_Screenshots/Installation/1.png){#Kali_Screenshots/Installation/1}


### Procédure d'installation

Dans VirtualBox, cliquer sur l'onglet **Fichier**, puis cliquer sur
*Importer un appareil virtuel\...*, tel que montré sur la figure
suivante :


![Importation de l'image de Kali Linux dans
VirtualBox](Archi2/Kali_Screenshots/Installation/2.png){#Kali_Screenshots/Installation/2}


Sélectionner le fichier OVA à importer, puis cliquer sur *Suivant \>* :


![Sélection de l'appareil virtuel à importer dans
VirtualBox](Archi2/Kali_Screenshots/Installation/3.png){#Kali_Screenshots/Installation/3}


Sélectionner les paramètres voulus pour la machine virtuelle Kali Linux
qui est importée. Ici, il a été choisi de générer de nouvelles adresses
MAC pour toutes les interfaces réseau, par exemple. Une fois cela fait,
cliquer sur *Importer* :


![Sélection des paramètres de l'appareil virtuel à importer dans
VirtualBox](Archi2/Kali_Screenshots/Installation/4.png){#Kali_Screenshots/Installation/4}


Accepter les termes du contrat de licence logiciel affichés, en cliquant
sur *Accepter* :


![Acceptation des termes du contrat de licence logiciel de la machine
virtuelle Kali
Linux](Archi2/Kali_Screenshots/Installation/5.png){#Kali_Screenshots/Installation/5}


Patienter pendant l'importation de l'appareil virtuel Kali Linux dans
VirtualBox :


![Importation de l'appareil virtuel Kali Linux dans
VirtualBox](Archi2/Kali_Screenshots/Installation/6.png){#Kali_Screenshots/Installation/6}


## Windows 8

Une machine Windows 8 est installée et intégrée au domaine dans le cadre
de l'utilisation de l'outil MBSA, qui n'est pas compatible avec Windows
10.

### Adresse du fichier d'installation

L'ISO de Windows 8 n'est plus mise à disposition sur le site de
Microsoft. Il est tout de même possible d'en trouver une en version
d'évaluation au lien suivant :
<https://www.clubic.com/telecharger-fiche410822-windows-8-release-preview.html>

### Procédure d'installation de l'ISO dans la machine virtuelle

Créer la nouvelle machine virtuelle :


![Création d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-1.png){#Windows8_screenshots/Install/1}


Nommer la machine virtuelle `Windows 8.1`, de type `Microsoft Windows`
et comme version, `Windows 8.1 (64-bit)`. Cliquer sur *Suivant* :


![Initialisation d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-2.png){#Windows8_screenshots/Install/2}


Attribuer la RAM qui sera allouée pour cette machine ; 2048 Mo
suffisent. Cliquer sur *Suivant* :


![Attribution de la RAM d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-3.png){#Windows8_screenshots/Install/3}


Choisir de créer un disque dur virtuel maintenant. Cliquer sur *Créer* :


![Attribution d'un disque d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-4.png){#Windows8_screenshots/Install/4}


Choisir VDI comme type de disque dur. Cliquer sur *Suivant* :


![Attribution du type de disque d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-5.png){#Windows8_screenshots/Install/5}


Choisir l'option \"Dynamiquement alloué\". Cliquer sur *Suivant* :


![Attribution du type d'espace d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-6.png){#Windows8_screenshots/Install/6}


Choisir un emplacement de la machine virtuelle ; 20 Go suffisent.
Cliquer sur *Créer* :


![Attribution de l'espace disque d'une nouvelle machine virtuelle
Windows
8.1](Archi2/Windows8_screenshots/Install/VM-7.png){#Windows8_screenshots/Install/7}


Cliquer droit sur la machine virtuelle Windows 8.1, puis sur
*Configuration\...* afin d'ouvrir le menu de configuration :


![Configuration d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-8.png){#Windows8_screenshots/Install/8}


Accéder à **Stockage**. Choisir l'ISO de Windows 8.1 téléchargée
précédemment :


![Attribution de l'ISO d'une nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-9.png){#Windows8_screenshots/Install/9}


### Configuration de l'interface réseau de la machine

Pour pouvoir accéder au réseau interne, il faut :\
Accéder au menu **Réseau** de la configuration, volet *Interface 1*, et
cocher `Activer l’interface réseau`. Il faut ensuite choisir le mode
d'accès réseau : `Réseau interne`. Le nom doit être : *pfsense*. Enfin,
cliquer sur *OK* :


![Configuration de l'interface de la nouvelle machine virtuelle Windows
8.1](Archi2/Windows8_screenshots/Install/VM-10.png){#Windows8_screenshots/Install/10}


### Installation de Windows 8.1

Lancer la machine virtuelle Windows 8.1. Renseigner les champs :


![Initialisation de l'installation de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-11.png){#Windows8_screenshots/Install/11}


Cliquer sur *Installer maintenant* :


![Lancement de l'installation de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-12.png){#Windows8_screenshots/Install/12}


Lire \"Avis et conditions du contrat de licence applicables\". Si vous
êtes en accord avec ce texte, cocher la case \"J'accepte les termes du
contrat de licene\". Cliquer sur *Suivant* :


![Acceptation du contrat de licence de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-13.png){#Windows8_screenshots/Install/13}


Choisir l'option : *Personnalisé : installer uniquement Windows
(avancé)* :


![Type d'installation de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-14.png){#Windows8_screenshots/Install/14}


Choisir le lecteur 0. Cliquer sur *Suivant* :


![Sélection du lecteur de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-15.png){#Windows8_screenshots/Install/15}


Attendre pendant l'installation de Windows :


![Installation de Windows
8.1](Archi2/Windows8_screenshots/Install/VM-16.png){#Windows8_screenshots/Install/16}


Sélectionner une couleur pour le thème du PC, et choisir le nom du PC.
Ici, `PC02`. Cliquer sur *Suivant* :


![Personnaliser la couleur ainsi que le nom du PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-17.png){#Windows8_screenshots/Install/17}


Cliquer sur *Personnaliser* :


![Configuration des paramètres du PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-18.png){#Windows8_screenshots/Install/18}


Cliquer sur *Oui* :


![Configuration réseau du PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-19.png){#Windows8_screenshots/Install/19}


Choisir les paramètres concernant les mises à jour, ainsi que ceux
concernant la protection du PC et de la vie privée de l'utilisateur.
Cliquer sur *Suivant* :


![Configuration personnalisée de paramètres du PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-20.png){#Windows8_screenshots/Install/20}


Choisir les paramètres concernant la recherche de solutions en ligne
ainsi que la participation à l'amélioration des produits et services
Microsoft. Cliquer sur *Suivant* :


![Configuration personnalisée de paramètres du PC Windows 8.1
(/Archi2/suite)](Windows8_screenshots/Install/VM-21.png){#Windows8_screenshots/Install/21}


Choisir les paramètres concernant le partage des informations avec
Microsoft et d'autres services. Cliquer sur *Suivant* :


![Configuration personnalisée de paramètres du PC Windows 8.1
(/Archi2/fin)](Windows8_screenshots/Install/VM-22.png){#Windows8_screenshots/Install/22}


Cliquer sur *Créer un nouveau compte* :


![Connexion ou création d'un nouveau compte Microsoft sur le PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-23.png){#Windows8_screenshots/Install/23}


Cliquer sur *Se connecter sans compte Microsoft* :


![Création d'un nouveau compte
Microsoft](Archi2/Windows8_screenshots/Install/VM-24.png){#Windows8_screenshots/Install/24}


Choisir un nom d'utilisateur, ainsi qu'un mot de passe et une indication
de mot de passe, puis cliquer sur *Terminer* :


![Création d'un compte sur le PC Windows
8.1](Archi2/Windows8_screenshots/Install/VM-25.png){#Windows8_screenshots/Install/25}

