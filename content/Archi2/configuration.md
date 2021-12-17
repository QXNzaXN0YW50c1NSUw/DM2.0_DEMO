+++
title = "Configuration de l'architecture"
date = 2021-12-15T01:10:29+01:00
weight = 4
chapter = false
+++

## Kali Linux

### Mise à jour de Kali Linux

Afin de pouvoir utiliser les outils de Kali Linux dans leur dernière
version, lancer la commande suivante dans un terminal :

``` shell
sudo apt update
```

Puis lancer la commande :

``` shell
sudo apt upgrade
```

Enfin, valider le choix en entrant **Y** dans le prompt comme le montre
la figure [32](#Kali/upgrade1){reference-type="ref"
reference="Kali/upgrade1"} ci-dessous.


![Prompt d'upgrade de Kali
Linux](/Archi2/Kali_Screenshots/Mise_en_place/upgrade.PNG){#Kali/upgrade1}


### Attribution d'une adresse IPv4 statique

Pour pouvoir être dans le sous-réseau avec une adresse IP statique, il
faut :

-   Se rendre dans le dossier **/etc/network** et ouvrir le fichier
    **interfaces** comme le montre la figure
    [33](#Kali/interfaces){reference-type="ref"
    reference="Kali/interfaces"} ;

    
    ![Ouverture du fichier de configuration de l'interface
    réseau](/Archi2/Kali_Screenshots/Mise_en_place/interfaces.PNG){#Kali/interfaces}
    

-   Écrire à l'identique le contenu de la figure
    [34](#Kali/static){reference-type="ref" reference="Kali/static"} ;

    
    ![Configuration de l'interface
    réseau](/Archi2/Kali_Screenshots/Mise_en_place/static.PNG){#Kali/static}
    

-   Redémarrer le service des interfaces réseau comme montré dans la
    figure [35](#Kali/service){reference-type="ref"
    reference="Kali/service"} :

    
    ![Relance du service
    réseau](/Archi2/Kali_Screenshots/Mise_en_place/service.PNG){#Kali/service}
    

## Mise en place du scanner applicatif

### Lancement des sessions de scan de vulnérabilités applicatives

Afin de lancer *Zap*, cliquer sur **Applications -\> 03 - Web
Application Analysis -\> OWASP zap**, comme le montre la figure
[36](#Vuln/zap){reference-type="ref" reference="Vuln/zap"} :


![Lancement de *Zap*](/Archi2/Zed_Screenshots/main/1.png){#Vuln/zap}


Il suffira ensuite de rentrer une URL dans l'onglet **Quick Start** pour
démarrer une analyse :


![Menu de *Zap*](/Archi2/Zed_Screenshots/main/2.png){#Kali/upgrade}


### Création d'un profil de scan

Afin de ne cibler que les vulnérabilités voulues, *Zap proxy* permet de
créer des profils personnalisés.\
Pour cela, cliquer sur **Analyse** puis sur **Scan Policy Manager\...**
:


![Menu analyse de *Zap*](/Archi2/Zed_Screenshots/profile/1.png){#Kali/upgrade}


Cliquer ensuite sur **Add** :


![Menu d'ajout de profil de
*Zap*](/Archi2/Zed_Screenshots/profile/2.png){#Kali/upgrade}


Nommer le profil comme montré dans la figure
[40](#Vuln/Nommage){reference-type="ref" reference="Vuln/Nommage"} :


![Nommage du profil dans
*Zap*](/Archi2/Zed_Screenshots/profile/3.png){#Vuln/Nommage}


Configurer les injections comme montré dans la figure
[41](#Vuln/Modifications){reference-type="ref"
reference="Vuln/Modifications"} :


![Modification des injections via le profil de
*Zap*](/Archi2/Zed_Screenshots/profile/4.png){#Vuln/Modifications}


### Scan applicatif de l'interface du Pfsense

À partir du menu de *Zap*, entrer l'URL de l'interface du Pfsense, puis
cliquer sur **Launch Browser**. L'opération va ouvrir un navigateur
modifié pour le scan applicatif. La figure
[42](#Vuln/Navigateur){reference-type="ref" reference="Vuln/Navigateur"}
montre le navigateur modifié. Cliquer sur **l'icône représentant une
flamme** pour passer en scan actif :


![Scan du Pfsense via
*Zap*](/Archi2/Zed_Screenshots/main/3.png){#Vuln/Navigateur}


Cliquer **Turn On** :


![Mode attaque de *Zap* sur
Pfsense](/Archi2/Zed_Screenshots/main/4.png){#Kali/upgrade}


Attendre que le scan termine :


![Affichage de *Zap* sur
Pfsense](/Archi2/Zed_Screenshots/main/5.png){#Kali/upgrade}


### Scan applicatif de l'interface du MISP

Comme pour l'analyse du Pfsense, lancer *Zap* sur l'URL de l'interface
MISP.\
Afin de pouvoir avoir un scan applicatif efficace, il faut
s'authentifier sur l'interface du MISP comme le montre la figure
[45](#Vuln/Misp){reference-type="ref" reference="Vuln/Misp"} :


![Authentification sur l'interface
MISP](/Archi2/Zed_Screenshots/misp/1.png){#Vuln/Misp}


Cliquer sur **l'icône représentant une flamme** pour passer en scan
actif puis cliquer sur **Start** pour lancer le scan :


![Lancement du mode attaque de *Zap* sur l'interface du
MISP](/Archi2/Zed_Screenshots/misp/3.png){#Kali/upgrade}


### Générer les exports de OWASP Zap

Afin de pouvoir exporter les résultats des scans, il suffit de :

-   Cliquer sur le menu **Report** puis sur **Generate HTML Report\...**
    ;

    
    ![Accès au menu des exports de
    *Zap*](/Archi2/Zed_Screenshots/main/6.png){#Kali/upgrade}
    

-   Nommer l'export puis cliquer sur **Save** ;

    
    ![Enregistrement de
    l'export](/Archi2/Zed_Screenshots/main/7.png){#Kali/upgrade}
    

-   Pour consulter le rapport, double-cliquer sur celui-ci.\
    La figure [49](#Vuln/Rapport){reference-type="ref"
    reference="Vuln/Rapport"} montre un aperçu d'un rapport d'analyse
    applicative via le logiciel *Zap Proxy* :

    
    ![Consultation du
    rapport](/Archi2/Zed_Screenshots/main/8.png){#Vuln/Rapport}
    

## Windows 8.1

### Attribution des paramètres réseaux

Démarrer la machine virtuelle Windows 8.1. Accéder aux paramètres réseau
et Internet, en cliquant droit sur l'icône de réseau sur la droite de la
barre des tâches. Cliquer sur *Ouvrir le Centre Réseau et partage* :


![Accès aux paramètres réseau et Internet de Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-1.png){#Windows8_screenshots/Config/1}


Dans le panel de gauche, cliquer sur *Modifier les paramètres de la
carte* :


![Ouverture des paramètres de la carte réseau de Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-2.png){#Windows8_screenshots/Config/2}


Cliquer droit sur la carte Ethernet, et sélectionner *Propriétés* :


![Accès aux propriétés de la carte Ethernet de Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-3.png){#Windows8_screenshots/Config/3}


Décocher *Protocole Internet version 6 (TCP/IPv6)*, et cocher *Protocole
Internet version 4 (TCP/IPv4)*. Cliquer sur *Propriétés* pour IPv4 :


![Modification sur les protocoles Internet et accès aux propriétés IPv4
de Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-4.png){#Windows8_screenshots/Config/4}


Renseigner la valeur du serveur DNS préféré : 192.168.2.2. Cliquer sur
*OK* :


![Modification de l'adresse DNS du PC Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-5.png){#Windows8_screenshots/Config/5}


### Attribution du domaine

Accéder aux paramètres *Système* :


![Accès à Système sur Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-6.png){#Windows8_screenshots/Config/6}


Cliquer sur *Modifier les paramètres* :


![Accès à la modification des paramètres système de Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-7.png){#Windows8_screenshots/Config/7}


Accéder aux propriétés de domaine en cliquant sur *Modifier* :


![Accès aux propriétés de domaine du PC Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-8.png){#Windows8_screenshots/Config/8}


Sélectionner \"Membre d'un domaine\", puis entrer le nom du domaine à
intégrer. Ici, `EPITAF.local`, puis cliquer sur *OK* :


![Intégration du PC Windows 8.1 au domaine
EPITAF.local](/Archi2/Windows8_screenshots/Config/Win8-config-9.png){#Windows8_screenshots/Config/9}


Entrer les identifiants demandés, puis cliquer sur *OK* :


![Modification de domaine effective du PC Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-10.png){#Windows8_screenshots/Config/10}


Un message de bienvenue apparaît si les identifiants sont corrects.
Cliquer sur *OK* pour fermer toutes les fenêtres.


![Redémarrage du PC Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-11.png){#Windows8_screenshots/Config/11}


Cliquer sur *Redémarrer maintenant* pour redémarrer le PC Windows 8.1,
afin que le changement de domaine soit effectif :


![Redémarrage du PC Windows
8.1](/Archi2/Windows8_screenshots/Config/Win8-config-12.png){#Windows8_screenshots/Config/12}


## Installation de MBSA

Pour en savoir plus sur MBSA, se réferrer au document
**microsoft.pdf**.\

### Sur Windows 8.1

Il est possible d'installer la version 2.3 du logiciel MBSA sur la
machine Windows 8.1. Cette version de l'exécutable n'est pas disponible
sur le site officiel de Microsoft. Elle est toutefois disponible à l'url
suivante :
<https://www.clubic.com/telecharger-fiche123308-microsoft-baseline-security-analyzer.html>\
Cliquer sur *Enregistrer le fichier* pour enregistrer l'exécutable
d'installation du logiciel MBSA :


![Téléchargement de l'exécutable d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-3.png){#MBSA_screenshots/Install-Win8/3}


Une fois téléchargé, double-cliquer sur l'exécutable pour lancer la
procédure d'installation.\
Cliquer sur *Suivant \>* :


![Gestionnaire d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-4.png){#MBSA_screenshots/Install-Win8/4}


Sélectionner l'option \"*J'accepte le contrat de licence*\". Cliquer sur
*Suivant \>* :


![Acceptation du contrat de licence du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-5.png){#MBSA_screenshots/Install-Win8/5}


Choisir un dossier de destination, puis cliquer sur *Suivant \>* :


![Choix du dossier d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-6.png){#MBSA_screenshots/Install-Win8/6}


Cliquer sur *Installer* :


![Démarrage de l'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-7.png){#MBSA_screenshots/Install-Win8/7}


Patienter pendant l'installation du logiciel MBSA :


![Progression de l'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-8.png){#MBSA_screenshots/Install-Win8/8}


Afin de finaliser l'installation, cliquer sur *OK* :


![Finalisation de l'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-Win8/WS-MBSA-install-9.png){#MBSA_screenshots/Install-Win8/9}


### Sur Windows Server 2012

Il est possible d'installer la version 2.1.1 du logiciel MBSA sur la
machine Windows Server 2012. L'exécutable est disponible sur le site web
de Microsoft, à l'url suivante :
<https://www.microsoft.com/fr-fr/download/details.aspx?id=19892>\
Sélectionner la langue, puis cliquer sur *Télécharger* :


![Site de téléchargement du logiciel MBSA sur le site de
Microsoft](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-1.png){#MBSA_screenshots/Install-WS/1}


Sélectionner l'exécutable en fonction de la plateforme ; ici, le fichier
`MBSASetup-x64-FR.msi`, puis cliquer sur *Next* :


![Sélection du format du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-2.png){#MBSA_screenshots/Install-WS/2}


Cliquer sur *Enregistrer le fichier* pour enregistrer l'exécutable
d'installation du logiciel MBSA :


![Téléchargement de l'exécutable d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-34.png){#MBSA_screenshots/Install-WS/34}


Une fois téléchargé, double-cliquer sur l'exécutable pour lancer la
procédure d'installation.\

Cliquer sur *Exécuter* :


![Fenêtre d'avertissement de
sécurité](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-35.png){#MBSA_screenshots/Install-WS/35}


Cliquer sur *Suivant \>* :


![Gestionnaire d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-36.png){#MBSA_screenshots/Install-WS/36}


Sélectionner l'option \"*J'accepte le contrat de licence*\". Cliquer sur
*Suivant \>* :


![Acceptation du contrat de licence du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-37.png){#MBSA_screenshots/Install-WS/37}


Choisir un dossier de destination, puis cliquer sur *Suivant \>* :


![Choix du dossier d'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-38.png){#MBSA_screenshots/Install-WS/38}


Cliquer sur *Installer* :


![Démarrage de l'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-39.png){#MBSA_screenshots/Install-WS/39}


Afin de finaliser l'installation, cliquer sur *OK* :


![Finalisation de l'installation du logiciel
MBSA](/Archi2/MBSA_screenshots/Install-WS/WS-MBSA-install-40.png){#MBSA_screenshots/Install-WS/40}


### Installation de nouveaux rôles et fonctionnalités

Installation des fonctionnalités IIS et WSUS dans le cadre du logiciel
MBSA.\
Démarrer la machine virtuelle Windows Server 2012. Ouvrir le
gestionnaire de serveur (s'ouvre normalement automatiquement lors du
démarrage de la machine). Cliquer sur l'onglet **Gérer**, puis sur
*Ajouter des rôles et fonctionnalités* :


![Ajout de rôles et de fonctionnalités sur Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-22.png){#WS_Screenshots/Features_install/22}


Aller dans la section **Avant de commencer**, puis cliquer sur *Suivant*
:


![Avant de commencer - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-23.png){#WS_Screenshots/Features_install/23}


Aller dans la section **Type d'installation**, sélectionner la première
option \"*Installation basée sur un rôle ou une fonctionnalité*\", puis
cliquer sur *Suivant* :


![Type d'installation - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-24.png){#WS_Screenshots/Features_install/24}


Aller dans la section **Sélection du serveur**. Cocher l'option
\"Sélectionner un serveur de pool de serveurs\". Choisir
*DC01.EPITAF.local*, puis cliquer sur *Suivant* :


![Sélection du serveur - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-25.png){#WS_Screenshots/Features_install/25}


Aller dans la section **Rôles de serveurs**. Cocher les options :
\"Serveur FTP\" du *Serveur Web (IIS)* et \"Services WSUS\". Cliquer sur
*Suivant*, puis cliquer sur *Ajouter des fonctionnalités* :


![Sélection des rôles de serveurs - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-26.png){#WS_Screenshots/Features_install/26}


Cliquer sur *Ajouter des fonctionnalités* :


![Ajout de WSUS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-27.png){#WS_Screenshots/Features_install/27}


Aller dans la section **Fonctionnalités**. Cliquer sur *Suivant \>* :


![Onglet d'ajout de fonctionnalités - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-28.png){#WS_Screenshots/Features_install/28}


Aller dans la section **WSUS**. Cliquer sur *Suivant* :


![Finalisation WSUS - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-29.png){#WS_Screenshots/Features_install/29}


Dans la section *Services de rôles*, cocher \"WID Database\" ainsi que
\"WSUS Services\". Cliquer sur *Suivant* :


![Services de rôle de WSUS - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-30.png){#WS_Screenshots/Features_install/30}


Dans la section *Contenu*, renseigner un chemin pour stocker les mises à
jour, tel que sur la capture d'écran ci-après, puis cliquer sur
*Suivant* :


![Contenu de WSUS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-31.png){#WS_Screenshots/Features_install/31}


Aller dans la section **Confirmation**. Cliquer sur *Installer* :


![Confirmation des sélections - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-32.png){#WS_Screenshots/Features_install/32}


Aller dans la section **Résultats**, et attendre la fin de
l'installation. Cliquer sur *Fermer* une fois terminé :


![Installation - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server
2012](/Archi2/WS_Screenshots/Features_install/WS-MBSA-install-33.png){#WS_Screenshots/Features_install/33}


Une fois l'installation terminée, accepter le redémarrage du serveur.
