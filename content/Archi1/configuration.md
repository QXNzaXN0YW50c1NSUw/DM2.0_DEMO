+++
title = "Configuration de l'architecture"
date = 2021-12-15T01:10:29+01:00
weight = 4
chapter = false
+++

## Pfsense

Démarrer la machine virtuelle Pfsense, comme sur la figure suivante :


![Démarrage de la machine virtuelle
Pfsense](Archi1/Pfsense_Screeshots/14.png){#Pfsense_Screeshots/14}


### Configuration des adresses IP

Sélectionner l'option de configuration des interfaces IP, en tapant
**2**, puis appuyer sur la touche **Entrée** :


![Sélection de l'option de configuration des adresses IP de
Pfsense](Archi1/Pfsense_Screeshots/15.png){#Pfsense_Screeshots/15}


Taper **1**, puis **y**, et **n**. Appuyer sur **Entrée**, puis
ré-entrer **n**. Appuyer une dernière fois sur **Entrée** :


![Configuration des adresses IP de l'interface réseau WAN de
Pfsense](Archi1/Pfsense_Screeshots/16.png){#Pfsense_Screeshots/16}


Sélectionner l'option de configuration des interfaces IP, en tapant
**2**, puis appuyer sur la touche **Entrée** :


![Sélection de l'option de configuration des adresses IP de
Pfsense](Archi1/Pfsense_Screeshots/15.png){#Pfsense_Screeshots/15}


Taper **2**. Entrer l'adresse IP : 192.168.2.1. Taper **24**, puis
appuyer deux fois sur la touche **Entrée**. Taper **n** aux deux
dernières questions :


![Configuration des adresses IP de l'interface réseau LAN de
Pfsense](Archi1/Pfsense_Screeshots/17.png){#Pfsense_Screeshots/17}


Vérifier le bon paramétrage de Pfsense avec la figure suivante :


![Vérification du paramétrage de
Pfsense](Archi1/Pfsense_Screeshots/18.png){#Pfsense_Screeshots/18}


### Configuration des règles Pfsense

Démarrer la machine virtuelle Windows Server 2012. Se connecter sur la
machine Windows Server 2012 avec le compte administrateur et le mot de
passe définit à l'installation :


![Connexion à Windows
Server](Archi1/Pfsense_Screeshots/19.png){#Pfsense_Screeshots/19}


Ouvrir Internet Explorer, et aller à l'adresse : 192.168.2.1. Se
connecter avec les identifiants Pfsense par défaut. Changer le mot de
passe de Pfsense :


![Accès et changement des accès de Pfsense sur Windows
Server](Archi1/Pfsense_Screeshots/20.png){#Pfsense_Screeshots/20}


Accéder à la page `Rules`, située dans **Firewall** :


![Accès aux règles de Pfsense via Windows
Server](Archi1/Pfsense_Screeshots/21.png){#Pfsense_Screeshots/21}


Aller dans la section *LAN*. Les étapes de modification des règles
Pfsense sont les suivantes :

-   Désactiver les deux règles existantes;

-   Créer une règle filtrant les trames IPv4 TCP/UDP provenant de
    192.168.2.2, sur le port 53 (DNS);

-   Créer une règle filtrant les trames IPv4 TCP/UDP provenant de
    192.168.2.0/24, sur le port 443 (HTTPS);

-   Créer une règle filtrant les trames IPv4 TCP/UDP provenant de
    192.168.2.0/24, sur le port 80 (HTTP).

Le résultat attendu est affiché sur la figure suivante :


![Modification des règles de Pfsense via Windows
Server](Archi1/Pfsense_Screeshots/22.png){#Pfsense_Screeshots/22}


## Windows Server 2012

### Ajout de fonctionnalités de Windows Server

Démarrer la machine virtuelle Windows Server 2012. Ouvrir le
gestionnaire de serveur (s'ouvre normalement automatiquement lors du
démarrage de la machine). Cliquer sur \"*Ajouter des rôles et des
fonctionnalités*\" :


![Ajout des rôles et des fonctionnalités sur Windows Server
2012](Archi1/WS2012_Screenshots/17.png){#WS2012_Screenshots/17}


Aller dans la section **Avant de commencer**, puis cliquer sur *Suivant*
:


![Avant de commencer - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](Archi1/WS2012_Screenshots/18.png){#WS2012_Screenshots/18}


Aller dans la section **Type d'installation**, sélectionner la première
option \"*Installation basée sur un rôle ou une fonctionnalité*\", puis
cliquer sur *Suivant* :


![Type d'installation - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](Archi1/WS2012_Screenshots/19.png){#WS2012_Screenshots/19}


Aller dans la section **Sélection du serveur**. Cocher l'option
\"Sélectionner un serveur de pool de serveurs\". Choisir
*DC01.EPITAF.local*, puis cliquer sur *Suivant* :


![Sélection du serveur - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](Archi1/WS2012_Screenshots/20.png){#WS2012_Screenshots/20}


Aller dans la section **Rôles de serveurs**. Cocher les options :

-   Serveur DHCP (installé);

-   Serveur DNS (installé);

-   Services AD DS (Installé).

Cliquer sur *Suivant*, puis cliquer sur *Ajouter des fonctionnalités* :


![Ajout de DHCP - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/21.png){#WS2012_Screenshots/21}


Cliquer sur *Ajouter des fonctionnalités* :


![Ajout de DNS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/22.png){#WS2012_Screenshots/22}


Cliquer sur *Ajouter des fonctionnalités* :


![Ajout de AD DS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/23.png){#WS2012_Screenshots/23}


Cliquer sur *Ajouter des fonctionnalités* :


![Ajout de AD LDS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/24.png){#WS2012_Screenshots/24}


Cliquer sur *Suivant* :


![Etat des ajouts - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/25.png){#WS2012_Screenshots/25}


Aller dans la section **Fonctionnalités**. Cocher l'option de
chiffrement de lecteur BitLocker. Cliquer sur *Ajouter des
fonctionnalités* :


![Ajout du chiffrement de lecteur BitLocker - Assistant d'ajout de rôles
et de fonctionnalités de Windows Server
2012](Archi1/WS2012_Screenshots/26.png){#WS2012_Screenshots/26}


Aller dans la section **Serveur DHCP**. Cliquer sur *Suivant* :


![Finalisation DHCP - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](Archi1/WS2012_Screenshots/27.png){#WS2012_Screenshots/27}


Aller dans la section **Serveur DNS**. Cliquer sur *Suivant* :


![Finalisation DNS - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/28.png){#WS2012_Screenshots/28}


Aller dans la section **Serveur AD DS**. Cliquer sur *Suivant* :


![Finalisation AD DS - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](Archi1/WS2012_Screenshots/29.png){#WS2012_Screenshots/29}


Aller dans la section **Serveur AD LDS**. Cliquer sur *Suivant* :


![Finalisation AD LDS - Assistant d'ajout de rôles et de fonctionnalités
de Windows Server
2012](Archi1/WS2012_Screenshots/30.png){#WS2012_Screenshots/30}


Aller dans la section **Confirmation**. Cliquer sur *Installer* :


![Confirmation des sélections - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](Archi1/WS2012_Screenshots/31.png){#WS2012_Screenshots/31}


Aller dans la section **Résultats**, et attendre la fin de
l'installation :


![Installation - Assistant d'ajout de rôles et de fonctionnalités de
Windows Server 2012](Archi1/WS2012_Screenshots/32.png){#WS2012_Screenshots/32}


Fin de l'installation. Cliquer sur *Fermer* :


![Fin de l'installation - Assistant d'ajout de rôles et de
fonctionnalités de Windows Server
2012](Archi1/WS2012_Screenshots/33.png){#WS2012_Screenshots/33}


### Configuration du DNS

Cliquer sur *Outils*, puis cliquer sur DNS :


![Accès au gestionnaire DNS de Windows Server
2012](Archi1/WS2012_Screenshots/34.png){#WS2012_Screenshots/34}


Cliquer droit sur `Redirecteurs`, puis cliquer sur *Propriétés* :


![Accès aux propriétés des Redirecteurs - Gestionnaire DNS de Windows
Server 2012](Archi1/WS2012_Screenshots/35.png){#WS2012_Screenshots/35}


Entrer la valeur \"8.8.8.8\" dans le nouveau champ :


![Ajout d'une valeur dans les Redirecteurs - Gestionnaire DNS de Windows
Server 2012](Archi1/WS2012_Screenshots/36.png){#WS2012_Screenshots/36}


Cliquer sur *OK* :


![Vérification de la valeur dans les Redirecteurs - Gestionnaire DNS de
Windows Server 2012](Archi1/WS2012_Screenshots/37.png){#WS2012_Screenshots/37}


Cocher l'option \"*Ce serveur assure la maintenance de la zone*\", puis
cliquer sur *Suivant* :


![Assistant configuration d'un serveur DNS - Gestionnaire DNS de Windows
Server 2012](Archi1/WS2012_Screenshots/38.png){#WS2012_Screenshots/38}


Cliquer sur *Appliquer* :


![Application du paramétrage des Redirecteurs - Gestionnaire DNS de
Windows Server 2012](Archi1/WS2012_Screenshots/39.png){#WS2012_Screenshots/39}


### Gestion du DHCP

Cliquer sur *Outils*, puis cliquer sur DHCP :


![Accès au gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/40.png){#WS2012_Screenshots/40}


Cliquer droit sur IPv4, puis cliquer sur *Propriétés* :


![Nouvelle étendue DHCP sur IPv4 - Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/41.png){#WS2012_Screenshots/41}


Cliquer sur *Suivant* :


![Assistant Nouvelle étendue - Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/42.png){#WS2012_Screenshots/42}


Entrer la valeur \"Etendu EPITAF\" dans le champ *Nom*, et
\"192.168.2.10-192.168.2.20\" dans le champ *Description*. Cliquer sur
*Suivant* :


![Nom et description - Assistant Nouvelle étendue du Gestionnaire DHCP
de Windows Server
2012](Archi1/WS2012_Screenshots/43.png){#WS2012_Screenshots/43}


Entrer les valeurs suivantes :

-   Adresse IP de début : 192.168.2.10

-   Adresse IP de fin : 192.168.2.20

-   Longueur : 24

-   Masque de sous-réseau : 255.255.255.0

Cliquer sur *Suivant* :


![Plage d'adresses IP - Assistant Nouvelle étendue du Gestionnaire DHCP
de Windows Server
2012](Archi1/WS2012_Screenshots/44.png){#WS2012_Screenshots/44}


Cliquer sur *Suivant* :


![Ajout d'exclusions et de retard - Assistant Nouvelle étendue du
Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/45.png){#WS2012_Screenshots/45}


Cliquer sur *Suivant* :


![Durée du bail - Assistant Nouvelle étendue du Gestionnaire DHCP de
Windows Server 2012](Archi1/WS2012_Screenshots/46.png){#WS2012_Screenshots/46}


Cocher l'option \"*Oui, je veux configurer ces options maintenant*\", et
cliquer sur *Suivant* :


![Configuration des paramètres DHCP - Assistant Nouvelle étendue du
Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/47.png){#WS2012_Screenshots/47}


Entrer l'adresse IP 192.168.2.1, puis cliquer sur *Ajouter*. Ensuite,
cliquer sur *Suivant* :


![Routeur - Assistant Nouvelle étendue du Gestionnaire DHCP de Windows
Server 2012](Archi1/WS2012_Screenshots/48.png){#WS2012_Screenshots/48}


Remplir les champs comme sur la figure suivante :

-   Domaine parent : EPITAF

-   Nom du serveur : Controleur de domain

-   Adresse IP : 192.168.2.2 et 8.8.8.8

Cliquer sur *Suivant* :


![Nom de domaine et serveurs DNS - Assistant Nouvelle étendue du
Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/49.png){#WS2012_Screenshots/49}


Cliquer sur *Suivant* :


![Serveurs WINS - Assistant Nouvelle étendue du Gestionnaire DHCP de
Windows Server 2012](Archi1/WS2012_Screenshots/50.png){#WS2012_Screenshots/50}


Cocher l'option \"*Oui, je veux activer cette étendue maintenant*\",
puis cliquer sur *Suivant* :


![Activation de l'étendue - Assistant Nouvelle étendue du Gestionnaire
DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/51.png){#WS2012_Screenshots/51}


Cliquer sur *Terminer* :


![Fin de la nouvelle étendue - Assistant Nouvelle étendue du
Gestionnaire DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/52.png){#WS2012_Screenshots/52}


### Création de l'Active Directory

Cliquer sur *Outils*, puis cliquer sur *Centre d'administration Active
Directory* :


![Centre d'administration Active
Directory](Archi1/WS2012_Screenshots/53.png){#WS2012_Screenshots/53}


Dans l'encadré **Serveurs**, cliquer sur *Autres\...* :


![Configuration AD DS de Windows Server
2012](Archi1/WS2012_Screenshots/54.png){#WS2012_Screenshots/54}


Cliquer sur l'action *Promouvoir ce serveur en contrôleur de domaine* :


![Configuration post-déploiement AD DS de Windows Server
2012](Archi1/WS2012_Screenshots/55.png){#WS2012_Screenshots/55}


Aller dans la section *Configuration de déploiement* :


![Configuration de déploiement - Configuration des services de domaine
Active Directory de Windows Server
2012](Archi1/WS2012_Screenshots/56.png){#WS2012_Screenshots/56}


Cocher l'option \"*Ajouter une nouvelle forêt*\", et entrer la valeur
\"*EPITAF.local*\" dans le champ *Nom de domaine racine*. Cliquer sur
*Suivant* :


![Ajout d'une nouvelle forêt - Configuration des services de domaine
Active Directory de Windows Server
2012](Archi1/WS2012_Screenshots/58.png){#WS2012_Screenshots/58}


Aller dans la section *Options du contrôleur de domaine*. Entrer un mot
de passe respectant les bonne pratiques de sécurité, puis cliquer sur
*Suivant* :


![Options du contrôleur de domaine - Configuration des services de
domaine Active Directory de Windows Server
2012](Archi1/WS2012_Screenshots/59.png){#WS2012_Screenshots/59}


Aller dans la section *Options DNS*, puis cliquer sur *Suivant* :


![Options DNS - Configuration des services de domaine Active Directory
de Windows Server
2012](Archi1/WS2012_Screenshots/60.png){#WS2012_Screenshots/60}


Aller dans la section *Options supplémentaires*, puis cliquer sur
*Suivant* :


![Options supplémentaires - Configuration des services de domaine Active
Directory de Windows Server
2012](Archi1/WS2012_Screenshots/61.png){#WS2012_Screenshots/61}


Aller dans la section *Chemins d'accès*, puis cliquer sur *Suivant* :


![Chemins d'accès - Configuration des services de domaine Active
Directory de Windows Server
2012](Archi1/WS2012_Screenshots/62.png){#WS2012_Screenshots/62}


Aller dans la section *Examiner les options*, puis cliquer sur *Suivant*
:


![Examiner les options - Configuration des services de domaine Active
Directory de Windows Server
2012](Archi1/WS2012_Screenshots/63.png){#WS2012_Screenshots/63}


Aller dans la section *Vérification de la configuration requise*, puis
cliquer sur *Installer* :


![Vérification de la configuration requise - Configuration des services
de domaine Active Directory de Windows Server
2012](Archi1/WS2012_Screenshots/64.png){#WS2012_Screenshots/64}


Une fois le serveur redémarré, se connecter au compte administrateur du
domaine EPITAF.


![Accès au compte administrateur du domaine EPITAF de Windows Server
2012](Archi1/WS2012_Screenshots/65.png){#WS2012_Screenshots/65}


Dans le gestionnaire de serveur, aller dans la section **DHCP** via la
colonne de gauche. Cliquer sur *Autres\...* dans l'encart jaune :


![Configuration du serveur DHCP pour AD DS de Windows Server
2012](Archi1/WS2012_Screenshots/66.png){#WS2012_Screenshots/66}


Cliquer sur l'action \"*Terminer la configuration DHCP*\" :


![Configuration post-déploiement du serveur DHCP pour AD DS de Windows
Server 2012](Archi1/WS2012_Screenshots/67.png){#WS2012_Screenshots/67}


Dans la section *Description* cliquer sur *Suivant* :


![Description - Assistant Configuration post-déploiement DHCP pour AD DS
de Windows Server
2012](Archi1/WS2012_Screenshots/68.png){#WS2012_Screenshots/68}


Dans la section *Autorisation*, cocher l'option \"*Utiliser les
informations d'identification de l'utilisateur suivant*\", pour
l'utilisateur `EPITAF\Administrateur`. Cliquer sur *Valider* :


![Autorisation - Assistant Configuration post-déploiement DHCP pour AD
DS de Windows Server
2012](Archi1/WS2012_Screenshots/69.png){#WS2012_Screenshots/69}


Dans la section *Résumé* cliquer sur *Fermer* :


![Résumé - Assistant Configuration post-déploiement DHCP pour AD DS de
Windows Server 2012](Archi1/WS2012_Screenshots/70.png){#WS2012_Screenshots/70}


Cliquer sur *Outils*, puis cliquer sur *DHCP*. Ensuite, dérouler la
section IPv4, et cliquer droit sur *Options de serveur*, puis cliquer
sur *Configurer les options\...* :


![Accès à la configuration des options de serveur DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/71.png){#WS2012_Screenshots/71}


Cocher l'option `003 Routeur`. Dans le champ *Adresse IP*, entrer
l'adresse IP 192.168.2.1, puis cliquer sur *Ajouter* :


![Paramétrage de l'option routeur du serveur DHCP de Windows Server
2012](Archi1/WS2012_Screenshots/72.png){#WS2012_Screenshots/72}


Cocher l'option `006 Servers DNS`. Dans le champ *Adresse IP*, entrer
l'adresse IP 192.168.2.2, puis cliquer sur *Ajouter*. Enfin, cliquer sur
*OK* :


![Paramétrage de l'option DNS de Windows Server
2012](Archi1/WS2012_Screenshots/73.png){#WS2012_Screenshots/73}


### Ajout d'un utilisateur dans le domaine EPITAF

Pour ajouter en toute sécurité un utilisateur dans notre domaine EPITAF,
nous allons :

-   Depuis le **Gestionnaire de serveur**, cliquer sur **Outils** puis
    sur **Utilisateurs et ordinateurs AD** ;

    
    ![Accès aux utilisateurs et ordinateurs AD de Windows Server
    2012](PC01/PC1.png)
    

-   Dérouler le menu comme suit : **Utilisateurs et ordinateurs AD -\>
    EPITAF.local -\> Users**, cliquer droit sur **Users**. Dans le menu
    **Nouveau** cliquer sur **Utilisateur** ;

    
    ![Ajout d'un utilisateur dans le domaine EPITAF de Windows Server
    2012](PC01/PC2.png)
    

-   Renseigner les champs puis cliquer sur **Suivant** ;

    
    ![Initialisation d'un utilisateur dans le domaine EPITAF de Windows
    Server 2012](PC01/PC3.png)
    

-   Renseigner le mot de passe de l'utilisateur puis cliquer sur
    **Suivant** ;

    
    ![Initialisation du mot de passe d'un utilisateur dans le domaine
    EPITAF de Windows Server 2012](PC01/PC4.png)
    

-   Vérifier les informations puis cliquer sur **Terminer**.

    
    ![Fin de l'ajout d'un utilisateur dans le domaine EPITAF de Windows
    Server 2012](PC01/PC5.png)
    

### Ajout d'un ordinateur dans le domaine EPITAF

Pour ajouter un ordinateur dans le domaine EPITAF, il faut :

-   Dérouler le menu comme suit : **Utilisateurs et ordinateurs AD -\>
    EPITAF.local -\> Computers**, cliquer droit sur **Computers**. Dans
    le menu **Nouveau** cliquer sur **Ordinateur** ;

    
    ![Ajout d'un ordinateur dans le domaine EPITAF de Windows Server
    2012](PC01/PC7.png)
    

-   Remplir les champs adéquats puis cliquer sur **Modifier\...** ;

    
    ![Initialisation du nouvel ordinateur sur Windows Server
    2012](PC01/PC8.png)
    

-   Renseigner le nom de l'utilisateur précédemment créé puis cliquer
    sur **OK** ;

    
    ![Paramétrage de l'option DNS de Windows Server 2012](PC01/PC9.png)
    

-   Cliquer sur **OK** :

    
    ![Paramétrage de l'option DNS de Windows Server 2012](PC01/PC10.png)
    

## Windows

### Attribution des paramètres réseaux

Démarrer la machine virtuelle Windows 10. Accéder aux paramètres réseau
et Internet, en cliquant droit sur l'icône de réseau sur la droite de la
barre des tâches. Cliquer sur *Ouvrir les paramètres réseau et Internet*
:


![Accès aux paramètres réseau et Internet de Windows
10](Archi1/W_Screenshots/41.png){#W_Screenshots/41}


Ouvrir les options d'adaptateur, en cliquant sur *Modifier les options
d'adapteur* :


![Ouverture des options d'adaptateur de Windows
10](Archi1/W_Screenshots/42.png){#W_Screenshots/42}


Cliquer droit sur la carte Ethernet, et sélectionner *Propriétés* :


![Accès aux propriétés de la carte Ethernet de Windows
10](Archi1/W_Screenshots/43.png){#W_Screenshots/43}


Décocher *Protocole Internet version 6 (TCP/IPv6)*, et cocher *Protocole
Internet version 4 (TCP/IPv4)*. Cliquer sur *Propriétés* pour IPv4 :


![Modification sur les protocoles Internet et accès aux propriétés IPv4
de Windows 10](Archi1/W_Screenshots/44.png){#W_Screenshots/44}


Renseigner la valeur du serveur DNS préféré : 192.168.2.2. Cliquer sur
*OK* :


![Modification de l'adresse DNS de PC01 de Windows
10](Archi1/W_Screenshots/45.png){#W_Screenshots/45}


### Attribution du domaine

Accéder aux paramètres *Systèmes* :


![Accès à Système sur Windows
10](Archi1/W_Screenshots/46.png){#W_Screenshots/46}


Aller à la section **Informations Système**. Cliquer sur *Informations
système* :


![Accès à Informations Système de Windows
10](Archi1/W_Screenshots/47.png){#W_Screenshots/47}


Cliquer sur *Modifier les paramètres* :


![Accès à la modification des paramètres système de Windows
10](Archi1/W_Screenshots/48.png){#W_Screenshots/48}


Accéder aux propriétés de domaine en cliquant sur *Modifier* :


![Accès aux propriétés de domaine de Windows
10](Archi1/W_Screenshots/49.png){#W_Screenshots/49}


Ajouter le domaine **EPITAF**, et cliquer sur *OK* :


![Modification du domaine de Windows
10](PC01/PC11.png){#W_Screenshots/50}


Rentrer les identifiants demandés, par exemple :

-   *Nom d'utilisateur* : EPITAF\\Ultrae;

-   *Mot de passe* : celui associé à Ultrae.

Un message de bienvenue apparaît si les identifiants sont corrects.
Cliquer sur *OK* puis fermer toutes les fenêtres :


![Modification de domaine effective de Windows
10](Archi1/W_Screenshots/51.png){#W_Screenshots/51}


## Debian

### Attribution des paramètres réseaux

Sur VirtualBox, sélectionner la machine virtuelle \"Debian DM4\", et
cliquer sur *Configuration* :


![Accès à la fenêtre de configuration de la machine virtuelle
Debian](Archi1/Debian_screenshots/Config/1.png){#Debian_screenshots/Config/1}


Accéder à la section **Réseau**, puis dans l'onglet \"Interface 1\",
sélectionner *Réseau interne* comme mode d'accès réseau, avec
\"pfsense\" comme nom :


![Configuration réseau de la machine virtuelle
Debian](Archi1/Debian_screenshots/Config/2.png){#Debian_screenshots/Config/2}


Se connecter sur la machine virtuelle. Cliquer sur l'icône pour les
réseaux, cliquer sur *Connexion de Filaire en \...*, puis sur
*Paramètres filaires* :


![Accès aux paramètres de configuration de
connexion](Archi1/Debian_screenshots/Config/3.png){#Debian_screenshots/Config/3}


Sélectionner *Filaire*, puis cliquer sur le bouton des paramètres :


![Accès aux paramètres de connexion
filaire](Archi1/Debian_screenshots/Config/4.png){#Debian_screenshots/Config/4}


Aller dans la section *IPv4*, puis sélectionner *Manuel* afin de
configurer les adresses suivantes : 192.168.2.2, 255.255.255.0 et
192.168.2.1. Cliquer sur *Appliquer* :


![Configuration des paramètres de connexion filaire en
IPv4](Archi1/Debian_screenshots/Config/5.png){#Debian_screenshots/Config/5}


Ouvrir un navigateur, et se rendre à l'adresse \"https://192.168.2.1\" :


![Accès à la page web de configuration de
pfsense](Archi1/Debian_screenshots/Config/6.png){#Debian_screenshots/Config/6}


Ouvrir la fenêtre de configuration de la machine virtuelle de
**pfsense**, et aller dans la section *Réseau*. Se rendre dans l'onglet
\"Interface 3\", cocher \"*Activer l'interface réseau*\", sélectionner
*Réseau interne* comme mode d'accès réseau, avec pour nom \"dmz\".
Cliquer sur *OK* :


![Création d'un second réseau interne sur
pfsense](Archi1/Debian_screenshots/Config/7.png){#Debian_screenshots/Config/7}


Sur la page web de configuration de pfsense, cliquer sur *Interfaces*
puis *Assignments* :


![Accès à l'assignation des interfaces sur la page web de configuration
de
pfsense](Archi1/Debian_screenshots/Config/8.png){#Debian_screenshots/Config/8}


Cliquer sur le bouton *Add* :


![Ajout d'une interface sur la page web de configuration de
pfsense](Archi1/Debian_screenshots/Config/9.png){#Debian_screenshots/Config/9}


Cliquer sur la nouvelle interface créée, soit *OPT1* :


![Accès à la configuration de l'interface
*OPT1*](Archi1/Debian_screenshots/Config/10.png){#Debian_screenshots/Config/10}


Remplir les champs comme sur la figure ci-dessous :


![Configuration de l'interface
*OPT1*](Archi1/Debian_screenshots/Config/11.png){#Debian_screenshots/Config/11}


Cliquer sur le bouton *Apply Changes* une fois les champs remplis :


![Application des changements sur la configuration de
l'interface](Archi1/Debian_screenshots/Config/12.png){#Debian_screenshots/Config/12}


Cliquer sur *Firewall*, puis sur *Rules* :


![Accès aux règles de pfsense sur l'interface
web](Archi1/Debian_screenshots/Config/13.png){#Debian_screenshots/Config/13}


Sélectionner la première règle ainsi que les deux dernières (d'après la
figure suivante), puis cliquer sur le bouton *Delete* :


![Suppression de trois règles pfsense sur l'interface
web](Archi1/Debian_screenshots/Config/14.png){#Debian_screenshots/Config/14}


Vérifier que la configuration des règles de pfsense soit la même que
celle de la figure ci-dessous :


![Aperçu des règles de pfsense sur l'interface
web](Archi1/Debian_screenshots/Config/15.png){#Debian_screenshots/Config/15}


Cliquer sur l'icône pour les réseaux dans le coin haut-droite de la
machine, puis cliquer sur *Paramètres filaire* :


![Accéder aux paramètres filaire de la
machine](Archi1/Debian_screenshots/Config/16.png){#Debian_screenshots/Config/16}


Aller dans la section *IPv4*, puis sélectionner *Manuel* afin de
configurer les adresses suivantes : 192.168.3.2, 255.255.255.0 et
192.168.3.1. Cliquer sur *Appliquer* :


![Configuration des paramètres de connexion filaire en
IPv4](Archi1/Debian_screenshots/Config/17.png){#Debian_screenshots/Config/17}


Ouvrir la fenêtre de configuration réseau de la machine virtuelle
Debian. Aller dans la section *Réseau*, puis dans l'onglet \"Interface
1\", changer le nom à \"dmz\", puis cliquer sur *OK* :


![Configuration réseau de la machine virtuelle
Debian](Archi1/Debian_screenshots/Config/18.png){#Debian_screenshots/Config/18}


## Interception SSL/TLS

### Objectifs

L'objectif, comme le montre la figure ci-dessous
([250](#Schema_tls/1){reference-type="ref" reference="Schema_tls/1"}),
est :

-   de pouvoir lire les informations transitant entre deux entités
    utilisant une connexion SSL/TLS ;

-   de pouvoir filtrer le mot clé EPITA dans le contenu chargé.

La présente section décrit donc comment obtenir ce résultat en utilisant
le proxy *SQUID* avec l'antivirus intégré *ClamAV* via le pare-feu
*pfSense*.


![Schéma de l'interception
SSL/TLS](Archi1/Interception_Screenshots/schema.jpeg){#Schema_tls/1}


### Accès à Pfsense et installation des paquets

Pour pouvoir obtenir SQUID il faut :

-   Se connecter à Pfsense via Internet Explorer

-   Accéder à **System -\> Package Manager** :

    
    ![image](Archi1/Pfsense_Screeshots/interception/3.png)
    [\[Pfsense_Screeshots/interception/3\]]{#Pfsense_Screeshots/interception/3
    label="Pfsense_Screeshots/interception/3"}
    

-   Cliquer sur **Available Packages** :

    
    ![image](Archi1/Pfsense_Screeshots/interception/4.png)
    [\[Pfsense_Screeshots/interception/4\]]{#Pfsense_Screeshots/interception/4
    label="Pfsense_Screeshots/interception/4"}
    

-   Rechercher **SQUID** :

    
    ![image](Archi1/Pfsense_Screeshots/interception/5.png)
    [\[Pfsense_Screeshots/interception/5\]]{#Pfsense_Screeshots/interception/5
    label="Pfsense_Screeshots/interception/5"}
    

-   Cliquer sur **Install**

-   Cliquer sur **Confirm** :

    
    ![image](Archi1/Pfsense_Screeshots/interception/6.png)
    [\[Pfsense_Screeshots/interception/6\]]{#Pfsense_Screeshots/interception/6
    label="Pfsense_Screeshots/interception/6"}
    

-   Attendre la fin de l'installation.

    
    ![image](Archi1/Pfsense_Screeshots/interception/7.png)
    [\[Pfsense_Screeshots/interception/7\]]{#Pfsense_Screeshots/interception/7
    label="Pfsense_Screeshots/interception/7"}
    

    
    ![image](Archi1/Pfsense_Screeshots/interception/8.png)
    [\[Pfsense_Screeshots/interception/8\]]{#Pfsense_Screeshots/interception/8
    label="Pfsense_Screeshots/interception/8"}
    

### Ajout d'un certificat

Pour ajouter un certificat, il faut :

-   accéder à **System -\> Certificat Manager -\> CAs** ;

-   cliquer sur **Add**;

    
    ![image](Archi1/Pfsense_Screeshots/interception/9.png)
    [\[Pfsense_Screeshots/interception/9\]]{#Pfsense_Screeshots/interception/9
    label="Pfsense_Screeshots/interception/9"}
    

-   renseigner les champs comme ci-dessous :

    
    ![image](Archi1/Pfsense_Screeshots/interception/10.png)
    [\[Pfsense_Screeshots/interception/10\]]{#Pfsense_Screeshots/interception/10
    label="Pfsense_Screeshots/interception/10"}
    

### Ajout du certificat sur tous les postes appartenant à EPITAF via GPO

Afin d'intercepter tous les flux provonant du réseau couvert par le
domaine EPITAF, voici comment propager le certificat CA à tous les
membres du domaine EPITAF :

-   Depuis le tableau de bord, cliquer sur **Outils** puis cliquer sur
    **Gestion des politiques de groupe** ;

    
    ![Accès aux politiques de groupe pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO0.png)
    

-   Dérouler le menu comme suit : **Gestion de stratégie de groupe -\>
    Forêt : EPITAF.local -\> Domaines -\> EPITAF.local -\> Objets de
    stratégie de groupe** puis cliquer sur **Nouveau** ;

    
    ![Nouvelle GPO pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO1.png)
    

-   Indiquer le nom de la GPO et cliquer sur *OK* ;

    
    ![Nom de la nouvelle GPO pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO2.png)
    

-   Cliquer droit sur la nouvelle GPO puis cliquer sur *Modifier\...* ;

    
    ![Modification de la GPO pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO3.png)
    

-   Dérouler le menu comme suit : **Stratégie AC pour IE -\>
    Configuration -\> Paramètres Windows -\> Paramètres de sécurité -\>
    Stratégie de clé publique** puis cliquer droit sur **Autorité de
    certification racines de confiance** ;

-   Cliquer sur **Importer\...** ;

    
    ![Ajout du certificat pour la nouvelle GPO pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO4.png)
    

-   Cliquer sur *Suivant* ;

    
    ![Nouveau CA pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO5.png)
    

-   Cliquer sur **Parcourir\...** ;

-   choisir le certificat puis cliquer sur *Suivant* ;

    
    ![Choix du certificat pour la nouvelle GPO pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO6.png)
    

-   Cliquer sur *Suivant* ;

    
    ![Placement du CA pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO7.png)
    

-   Cliquer sur *Terminer* ;

    
    ![Fin de l'installation du nouveau certificat pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO8.png)
    

-   Cliquer sur *Ok*.

    
    ![Validation de l'ajout du nouveau certificat pour l'interception
    TLS](Archi1/Interception_Screenshots/GPO9.png)
    

### Mise en place de l'antivirus ClamAV

Pour mettre en place l'antivirus ClamAV, il faut :

-   Accéder à **Services -\> Squid Proxy Server** ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/11.png)
    [\[Pfsense_Screeshots/interception/11\]]{#Pfsense_Screeshots/interception/11
    label="Pfsense_Screeshots/interception/11"}
    

-   Changer la valeur du cache par *500*, puis cliquer sur *save* ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/12.png)
    [\[Pfsense_Screeshots/interception/12\]]{#Pfsense_Screeshots/interception/12
    label="Pfsense_Screeshots/interception/12"}
    

-   Cocher **Enable AV**, mettre **Enable Manual Configuration** à
    **enabled**, cliquer sur **Load Advanced** ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/13.png)
    [\[Pfsense_Screeshots/interception/13\]]{#Pfsense_Screeshots/interception/13
    label="Pfsense_Screeshots/interception/13"}
    

-   Ouvrir la configuration avancée puis lire la valeur
    **DatabaseDirectory** dans **freshclam.conf**.

    
    ![image](Archi1/Pfsense_Screeshots/interception/14.png)
    [\[Pfsense_Screeshots/interception/14\]]{#Pfsense_Screeshots/interception/14
    label="Pfsense_Screeshots/interception/14"}
    

```{=html}
<!-- -->
```
-   Accéder à **Services -\> Squid Proxy Server** ;

-   Cocher **Enable Squid Proxy**, cocher **Keep Settings/Data**, mettre
    **Proxy Interface(s)** à **LAN**, cliquer sur **Load Advanced** ;

-   Cocher **Transparent HTTP Proxy** ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/15.png)
    [\[Pfsense_Screeshots/interception/15\]]{#Pfsense_Screeshots/interception/15
    label="Pfsense_Screeshots/interception/15"}
    

-   Cocher **HTTPS/SSL Interception** ;

-   Cocher **Enable Access Logging** ;

-   Cliquer sur **save** ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/16.png)
    [\[Pfsense_Screeshots/interception/16\]]{#Pfsense_Screeshots/interception/16
    label="Pfsense_Screeshots/interception/16"}
    

-   Comme fait précédemment, ajouter une règle sur pfsense ;

    
    ![image](Archi1/Pfsense_Screeshots/interception/17.png)
    [\[Pfsense_Screeshots/interception/17\]]{#Pfsense_Screeshots/interception/17
    label="Pfsense_Screeshots/interception/17"}
    

-   Paramétrer la configuration pour autoriser les ports 3128 et 3129,
    puis cliquer sur *save*;

    
    ![image](Archi1/Pfsense_Screeshots/interception/18.png)
    [\[Pfsense_Screeshots/interception/18\]]{#Pfsense_Screeshots/interception/18
    label="Pfsense_Screeshots/interception/18"}
    

-   Pour interdire tous les navigateurs sauf Internet Explorer en
    version supérieure à 10, il faut ajouter la regex présentée
    ci-dessous dans l'onglet **ACLs**, à **Block User Agents**.

    
    ![image](Archi1/Pfsense_Screeshots/interception/19.png)
    [\[Pfsense_Screeshots/interception/19\]]{#Pfsense_Screeshots/interception/19
    label="Pfsense_Screeshots/interception/19"}
    

### Filtrage du mot clé EPITA via ClamAV

Pour pouvoir filtrer tous les paquets contenant le mot clé **EPITA**
avec *SQUID*, nous utiliserons l'anti-virus intégré : *ClamAV*.\
Lorsque clamAV détecte une page web en entrée, à l'aide d'une balise
HTML valide, il se comporte comme suit [@Clamav-signatures] :

1.  le fichier est normalisé, les commentaires sont supprimés, tout est
    mis en minuscule et les espaces en trop sont supprimés ;

2.  les tags HTML sont enlevés ;

3.  un fichier contenant le javascript est créé.

Nous cherchons donc à créer une signature permettant de détecter le mot
clé **EPITA** et donc nous notifier. Pour cela, plusieurs formats se
présentent à nous. Nous en retiendrons deux :

-   les *.yara* [@yara-signatures] [@yara-hunting-signatures];

-   les *.ndb*[@ndb-signatures].

Ainsi, après avoir lu où se trouve les signatures de *ClamAV* via les
fichiers de configuration de *SQUID*, nous rajouterons les notres (voir
dev.pdf pour le contenu) dans le dossier adéquat.

Ci-dessous, le résultat après une recherche google avec des termes
proches d'epita.


![image](Archi1/Interception_Screenshots/clamAV01.png)
[\[Pfsense_Screeshots/interception/18\]]{#Pfsense_Screeshots/interception/18
label="Pfsense_Screeshots/interception/18"}



![image](Archi1/Interception_Screenshots/clamAV02.png)
[\[Pfsense_Screeshots/interception/18\]]{#Pfsense_Screeshots/interception/18
label="Pfsense_Screeshots/interception/18"}


Ce qui nous donne dans les logs :


![image](Archi1/Interception_Screenshots/clamAV03.png)
[\[Pfsense_Screeshots/interception/18\]]{#Pfsense_Screeshots/interception/18
label="Pfsense_Screeshots/interception/18"}


## Mise en place d'une connexion SSL/TLS mutualisée

### Objectifs et pré-requis

Nous cherchons ici à établir une connexion SSL/TLS mutualisée.\
Pour cela, nous considérons sur le serveur possédant le serveur TLS que
:

-   le serveur est une machine virtuelle hébergée dans le Cloud de
    Google ;

-   l'OS utilisé est un Debian 64 ;

-   le serveur Nginx est déjà installé **mais pas encore configuré** ;

-   le nom de domaine utilisé est *ultrae.eu* ;

-   le site web est déjà créé dans */var/www/html/*.

### Paramétrage du serveur NGINX

Pour pouvoir paramétrer nginx il faut :

1.  Générer à l'aide du pki (voir dev.pdf) :

    -   un certificat CA et sa clé privée ;

    -   un CSR signé par le CA.

    
    ![Affichage des certificats pour le TLS
    mutualisé](Archi1/Interception_Screenshots/mut01.png)
    

2.  Les placer dans un dossier sur le serveur distant.

    
    ![Mise en place des certificats pour le TLS
    mutualisé](Archi1/Interception_Screenshots/mut02.png)
    

3.  Dans la configuration ssl de Nginx rajouter les lignes :

    -   `ssl_certificate "/etc/nginx/cert/ultrae.eu.CA.crt";`

    -   `ssl_certificate_key "/etc/nginx/cert/ultrae.eu.CA.key";`

    -   `ssl_client_certificate "/etc/nginx/cert/ultrae.eu.crt";`

    -   `ssl_verify_client on.`

4.  Ajouter dans le navigateur :

    -   le certificat du CA dans les certificats root trusted ;

    -   le certificat client dans les certificats personnels.

### Interception SSL/TLS sur une connexion TLS mutualisée

Afin de pouvoir intercepter et pouvoir déchiffrer un flux chiffré entre
un serveur TLS et un client s'authentifiant mutuellement, il faut :

-   Se connecter sur pfsense ;

-   Dans **System -\> Cert. Manager**, importer un CA ;

    
    ![Importation du CA pour le TLS
    mutualisé](Archi1/Interception_Screenshots/mut03.png)
    

-   Dans l'onglet **Certificates**, importer un CSR ;

    
    ![Importation du CSR pour le TLS
    mutualisé](Archi1/Interception_Screenshots/mut04.png)
    

-   Ajouter un nouveau certificat, selectionner la méthode *Sign a
    Certificate Signing Request*;

-   Mettre *ultrae.eu* dans *Descriptive name* ;

-   Mettre *ultrae.eu.CA* dans *CA to sign* ;

-   Mettre *sha512* dans *Digest Algorithm* ;

-   Mettre *URI* et *www.ultrae.eu* dans *Alternative Names* ;

-   Cliquer sur save.

    
    ![Signature du CSR pour le TLS
    mutualisé](Archi1/Interception_Screenshots/mut05.png)
    

\-

## Installation et configuration des services

### Ansible

Pour pouvoir construire notre infrastructure
[251](Archi1/#Architecture_Screenshots/2){reference-type="ref"
reference="Architecture_Screenshots/2"}, nous utiliserons Ansible [^1].


![Architecture cible avec
Ansible](Archi1/Architecture_Screenshots/archi2.jpeg){#Architecture_Screenshots/2}


Afin de lancer le déploiement, il suffit d'exécuter la commande suivante
à partir d'une machine présente dans le LAN :

``` shell
    $ ansible-playbook -i hosts full.yml --ask-pass --ask-vault
```

Si Ansible n'est pas installé sur la machine lançant le script, il
faudra :

-   Ajouter à **deb http://ppa.launchpad.net/ansible/ansible/ubuntu
    trusty main** à :\
    **/etc/apt.source.list**

-   Il faudra ensuite exécuter ces commandes pour mettre en place
    Ansible :

    ``` shell
        $ sudo apt-key adv \ 
            --keyserver keyserver.ubuntu.com \ 
            --recv-keys 93C4A3FD7BB9C367
        $ sudo apt update
        $ sudo apt install ansible
    ```

### Nginx

##### Paquets installés

Les paquets nécessaires au fonctionnement du service web Nginx sont:

-   *nginx*

-   *nginx-extras* afin de pouvoir modifier le header et diminuer
    l'empreinte numérique


![Page d'Accueil Nginx avec
Authentification](Archi1/Nginx_Screenshots/4.png){#Nginx_Screenshots/4.png}


##### Rôle

Ce rôle Ansible permet de déployer automatiquement un service web Nginx,
clé en main. Les principales étapes sont les suivantes:

-   Modification du fichier de configuration situé dans
    */etc/nginx/nginx.conf*:

    -   Ajout de *more_set_headers* 'Server: WeAreAnonymous' et
        *server_tokens* off

    -   Journalisation des événements en ajoutant
        `access_log /var/log/nginx/access.log` et
        `error_log /var/log/nginx/error.log`

-   Création de plusieurs pages html personnalisées, notamment pour
    gérer les erreurs 404, 405 et 50x. Le but est de limiter au maximum
    l'identité du service qui est dévoilée avec les pages par défaut.

-   Ecoute sur le port 443 en plus du 80 :

``` bash
      listen 443 ssl default_server;
      listen [::]:443 ssl default_server;
```

-   Redirection automatique des requêtes sur le port 80 vers le port 443

-   Ajout d'une politique de protection :

``` {.bash fontsize="\\footnotesize"}
        add_header Strict-Transport-Security "max-age=31536000; includeSubdomains" always;
        add_header X-Xss-Protection "1; mode=block" always;
        add_header X-Frame-Options "SAMEORIGIN" always;
        add_header X-Content-Type-Options "nosniff" always;
        add_header Referrer-Policy "no-referrer-when-downgrade";
        Politique de sécurité CSP filtrant le contenu :
        add_header Content-Security-Policy "default-src 'self' [...]
        Autorisation des requêtes GET et POST seulement :
        if ( \$reques_method !~ ^(GET|POST)\$ ) { return 405; }
	
```

-   Ajout des certificats générés par la PKI du DM3 :

``` bash
      ssl_certificate /etc/nginx/server.crt;
      ssl_certificate_key /etc/nginx/server.key;
      ssl_client_certificate /etc/nginx/CAcrt.pem;
```

L'utilisateur devra ensuite se connecter avec le certificat p12
utilisateur, émis par la PKI.


![Page d'Accueil Wordpress depuis Nginx Port 80/Apache Port
8000](Archi1/Nginx_Screenshots/5.png){#Nginx_Screenshots/5.png}



![Page d'erreur 404](Archi1/Nginx_Screenshots/6.png){#Nginx_Screenshots/6.png}



![Page d'erreur 405](Archi1/Nginx_Screenshots/7.png){#Nginx_Screenshots/7.png}



![Page d'erreur 50x](Archi1/Nginx_Screenshots/8.png){#Nginx_Screenshots/8.png}



![En-tête de Nginx sécurisée et
préservée](Archi1/Nginx_Screenshots/9.png){#Nginx_Screenshots/9.png}


### MySQL

##### Paquets installés

Les paquets nécessaires au fonctionnement de MariaDB (MySQL) sont:

-   *mysql-server*

-   *php-mysql*

-   *python-mysqldb*

##### Rôle

Ce rôle Ansible permet de déployer automatiquement la base de données
MariaDB (MySQL). Cette base servira au site wordpress joué par le
service Apache2. Ce rôle décrit une commande autonome, mais interactive
toute simple : *mysql_secure_installation*. Cette commande doit être
lancée en tant que root.


![Lancement de la commande pour
MariaDB](Archi1/Wordpress_Screenshots/5.png){#Wordpress_Screenshots/5.png}


Cette commande exécute plusieurs tâches notamment:

-   Changement du mot de passe root de la DB

-   Désactivation de l'authentification root à distance

-   Suppression des utilisateurs anonymes

-   Suppression de la base test

-   Suppression des privilèges de la base test

Bien entendu, cette commande a été reprise en détails dans un rôle
ansible afin de produire le même comportement.

### Apache

##### Paquets installés

Les paquets nécessaires au fonctionnement du serveur Apache sont:

-   *apache2*

-   *php*

-   *libapache2-mod-php*

-   *krb5-user*

-   *libapache2-mod-auth-kerb*

-   *libapache2-modsecurity*

-   *php-curl*

-   *php-gd*

-   *php-intl*

-   *php-json*

-   *php-mbstring*

-   *php-xml*

-   *php-zip*

##### Rôle

Ce rôle Ansible permet de déployer automatiquement le service web
Apache2 prêt à être utilisé, mais aussi le support de l'authentification
via Kerberos.

Pour une installation manuelle d'Apache, les étapes de déploiement sont
les suivantes :

-   Installer les paquets avec un gestionnaire de paquets;

-   Démarrer le service Apache.

Une fois qu'Apache est fonctionnel, il faut installer le blog Wordpress
demandé. Il suffit pour cela de cloner le dépôt WordPress suivant
*https://github.com/WordPress/WordPress.git*, dans
*/var/www/html/wordpress*, afin de pouvoir accéder au site via la boucle
locale soit `https://192.168.3.2/blog`.

En démarrant Wordpress, il faut avoir Apache, PHP et MariaDB en route et
configuré. Dans un second temps, il faudra se connecter à MariaDB afin
d'y créer une table et un utilisateur.

Sur Wordpress, un assistant reprenant tous les éléments configurés nous
guidera afin de générer le fichier *wp-config.php* qui sera à mettre
dans le dossier *wordpress* cité plus haut.

Lors de la première connexion, il faudra remplir le formulaire de
création d'un administrateur du site, selon l'illustration suivante :


![Première connexion sur
Wordpress](Archi1/Wordpress_Screenshots/1.png){#Wordpress_Screenshots/1.png}


À l'étape suivante, il suffit de cliquer sur \"Log In\" pour se
connecter à l'interface administrateur de gestion du site.


![Connexion à l'interface de gestion de
Wordpress](Archi1/Wordpress_Screenshots/2.png){#Wordpress_Screenshots/2.png}


Soyez les bienvenus sur Wordpress !


![Page d'accueil
Wordpress](Archi1/Wordpress_Screenshots/4.png){#Wordpress_Screenshots/4.png}


### OpenSSH

##### Paquets installés

-   *openssh-server*

-   *libpam-google-authenticator*

##### Rôle

###### Gestion des utilisateurs

La liste ci-dessous détaille et explique les commandes à réaliser
concernant la gestion des utilisateurs :

-   Création du groupe TOPGUN : `sudo groupadd TOPGUN`{.bash}

-   Création de l'utilisateur `maverik` : `sudo useradd maverik`{.bash}

-   Création de l'utilisateur `charlie` : `sudo useradd charlie`{.bash}

-   Création de l'utilisateur `goose` : `sudo useradd goose`{.bash}

-   Ajout de `maverik` au groupe TOPGUN :
    `sudo usermod -g TOPGUN maverik`{.bash}

-   Ajout de `charlie` au groupe TOPGUN :
    `sudo usermod -g TOPGUN charlie`{.bash}

-   Ajout de `goose` au groupe TOPGUN :
    `sudo usermod -g TOPGUN goose`{.bash}

Aussi, les utilisateurs `maverik` et `charlie` ne connaissent pas leur
mot de passe ; ceux-ci sont stockés dans un coffre. Étant donné que nous
avons utilisé un coffre pour certaines variables des playbooks Ansible,
nous avons trouvé plus simple d'utiliser ce coffre-là pour y stocker les
mots de passe de `maverik` et `Charlie`. Nous avons pour cela utilisé
l'outil **Ansible Vault**.

###### Attribution de droits

Une fois que les utilisateurs ont été créés, il est possible de leur
attribuer certains droits. En effet :

-   `maverik` doit pouvoir redémarrer le système ou le mettre à jour en
    tant que utilisateur privilégié;

-   `charlie` doit pouvoir effectuer toutes les tâches root sur le
    système;

-   `goose` n'a auncun droit de ce type.

Ces configurations se font dans le fichier */etc/sudoers*. Afin de
faciliter l'ajout de configurations particulières, il est possible de
rajouter ses propres fichiers. C'est ce que nous avons fait, car cela
permet aussi un déploiement par Ansible plus simple. Ainsi, nous avons
créé le fichier */etc/sudoers.d/ssh-users*, qui contient :

-   Le temps pendant lequel un utilisateur ayant utilisé `sudo` n'a pas
    besoin de se ré-authentifier pour exécuter des commandes nécessitant
    `sudo`;

-   L'attribution des droits pour `maverik`;

-   L'attribution des droits pour `charlie`.

Ce fichier doit appartenir à l'utilisateur `root`, et posséder les
permissions suivantes : \"0440\" ; on les lui donne avec
`sudo chmod 0440 /etc/sudoers.d/ssh-users`{.bash}.

###### Google Authenticator

Dans la configuration SSH attendue, il est demandé de permettre
l'authentification via *Google Authenticator*. Afin de l'utiliser, il
faut tout d'abord installer le paquet `libpam-google-authenticator`.
Ensuite, lancer la génération de la clé secrète avec
`google-authenticator`{.bash} pour chacun des utilisateurs, qui sera
exécuté de manière interactive. Plusieurs questions sont en effet
posées, telles que le montrent les figures suivantes :

Il est préférable d'accepter que les jetons d'authentification soient
basés sur le temps.


![Lancement de Google
Authenticator](Archi1/OpenSSH_Screenshots/google_auth-1.png){#OpenSSH_Screenshots/google-auth-1.png}


Affichage du QR Code à flasher avec l'application Google Authenticator,
ainsi que de la clé secrète à entrer dans l'application Google
Authenticator s'il n'est pas possible de la flasher maintenant. Google
authenticator donne également cinq codes récupération en cas de perte ou
de vol du téléphone possédant l'application Google authenticator. Si le
fichier */home/\<user>/.google_authenticator* existe déjà, il est
possible de le templacer par la nouvelle clé secrète


![Génération de la clé secrète et deuxième question de Google
Authenticator](Archi1/OpenSSH_Screenshots/google_auth-2.png){#OpenSSH_Screenshots/google-auth-2.png}


Choisir de ne pas autoriser l'utilisation multiple du même jeton
d'authentification.


![Troisième question de Google
Authenticator](Archi1/OpenSSH_Screenshots/google_auth-3.png){#OpenSSH_Screenshots/google-auth-3.png}


Garder la génération d'un nouveau jeton toutes les 30 secondes, et donc
répondre non à la question :


![Quatrième question de Google
Authenticator](Archi1/OpenSSH_Screenshots/google_auth-4.png){#OpenSSH_Screenshots/google-auth-4.png}


Répondre oui pour permettre la limitation de tentative de connexion :


![Dernière question de Google
Authenticator](Archi1/OpenSSH_Screenshots/google_auth-5.png){#OpenSSH_Screenshots/google-auth-5.png}


Ce programme génère un fichier *.google_authenticator* contenant la clé
secrète à donner à l'application Google Authenticator, dans le dossier
*/home/\<user>/* de l'utilisateur actuel. Cette clé est utile si
l'utilisateur n'a pas pu récupérer le QR Code affiché à l'écran.

Cette étape \"Google Authenticator\" se déroule donc en deux temps : la
génération de la clé secrète et son ajout dans l'application Google
Authenticator, ce qui rend difficile le déploiement avec Ansible. En
effet, la difficulté est ici la récupération des clés générées et leur
distribution aux bons utilisateurs. La solution qui nous a semblé la
plus appropriée est la suivante :

-   Copier le fichier *.google_authenticator* pour chacun des
    utilisateurs dans le dossier d'où est lancé le déploiement par
    Ansible. Ils sont ajoutés au dossier *GoogleAuthenticator* situé au
    niveau du fichier *hosts*;

-   L'administrateur à l'origine du déploiement peut ensuite distribuer
    de manière sécurisée ces fichiers aux utilisateurs concernés.

Aussi, nous avons utilisé Google Authenticator en mode non-interactif
dans le playbook Ansible, contrairement à l'exemple montré sur les
figures ci-dessus, où Google Authenticator est utilisé en mode
interactif.\
Une fois les clés secrètes générées, il faut permettre leur utilisation.
Il faut pour cela modifier les fichiers de PAM - Pluggable
Authentication Modules.

###### PAM

Le comportement attendu est de pouvoir se connecter en SSH en utilisant
un code généré par Google Authenticator pour certains utilisateurs. Pour
faire cela, il faut modifier le fichier */etc/pam.d/sshd*, en tant
qu'utilisateur privilégié. Il faut pour cela commenter la ligne
`@include common-auth`{.bash}, et ajouter la ligne suivante à la fin du
fichier : `auth required pam_google_authenticator.so`{.bash}

Afin que SSH demande cette méthode d'authentification, il faut modifier
le fichier de configuration du serveur SSH, qui est le fichier
*/etc/ssh/sshd_config*. Il faut éditer ce fichier en tant qu'utilisateur
privilégié.

###### charlie

Aussi, l'utilisateur `charlie` peut effectuer toutes les tâches root sur
le système, mais doit se ré-authentifier toutes les 15 minutes avec un
code de vérification de Google Authenticator. La figure ci-dessous
montre que `charlie` peut effectuer toute sorte de commande utilisant
`sudo`{.bash}, sans redemander le code de vérification. Au bout de 15
minutes, `charlie` doit entrer le code de vérification de Google
Authenticator :


![Capture d'écran de la ré-authentification de charlie avec Google
Authenticator au bout de 1
minute](Archi1/OpenSSH_Screenshots/charlie-timeout.png){#OpenSSH_Screenshots/maverik.png}


Pour des raisons pratiques, la capture d'écran montre le comportement
attendu avec un timeout de 1 minute.

Il faut tout d'abord ajouter au fichier */etc/sudoers.d/ssh-users* créé
précedemment, la ligne : `Defaults:charlie timestamp_timeout=15`{.bash}\
Ensuite, il faut configurer PAM pour `sudo`, via le fichier de
configuration */etc/pam.d/sudo*. Le fichier est affiché ci-dessous :

``` bash
#%PAM-1.0
auth [success=ignore default=1] pam_succeed_if.so user ingroup charlie-grp
auth sufficient pam_google_authenticator.so nullok

@include common-auth
@include common-account
@include common-session-noninteractive
```

Pour que cette fonctionnalité soit opérationnelle, il faut créer un
groupe `charlie-grp`, auquel appartient `charlie`.

##### Configuration de SSH

La configuration du serveur SSH se situe dans le fichier
*/etc/ssh/sshd_config*. C'est donc ce fichier que nous avons dû modifier
pour répondre aux conditions requises. La liste ci-dessous détaille les
mots-clés choisis ainsi que leur(s) argument(s), pour chacun des points
demandés :

-   Le service écoute uniquement sur le port 22 en IPv4 :

``` bash
          Port 22
          Protocol 2
          AddressFamily inet
          ListenAddress 0.0.0.0
```

-   Refus des connexions `root` : `PermitRootLogin no`{.bash}

-   Le service log au maximum les interactions et surtout les échecs
    synonymes d'incidents de sécurité : `LogLevel VERBOSE`{.bash}

-   Utilisation du module PAM pour l'authentification ; acceptation,
    uniquement, de l'authentification avec biclé ou via un code de
    sécurité Google Authenticator pour les utilisateurs du serveur :

``` bash
          PasswordAuthentication no
          PermitEmptyPasswords no
          ChallengeResponseAuthentication yes
          UsePAM yes
          
          # Configuration des méthodes d'authentification
          # pour certains utilisateurs
          Match User charlie
            AuthenticationMethods publickey,keyboard-interactive
          Match User goose
            AuthenticationMethods keyboard-interactive
```

Les mots-clés utilisés dans le fichier de configuration que nous avons
mis en place ne sont pas tous décrits dans ce document. Ils ont
néanmoins été choisis pour avoir une configuration durcie du serveur
SSH.

##### Résultats attendus

Ci-dessous des captures d'écran montrant le comportement attendu à la
connexion de chacun des utilisateurs : `maverik`, `charlie` et `goose`.\
La figure ci-dessous montre la connexion SSH de l'utilisateur `maverik`,
avec le code de vérification de Google Authenticator. Les commandes
`apt update`{.bash} et `sudo apt update`{.bash} permettent de montrer
que maverik ne peut exécuter que certaines commandes avec `sudo`{.bash}
:


![Capture d'écran lors de la connexion de
maverik](Archi1/OpenSSH_Screenshots/maverik.png){#OpenSSH_Screenshots/maverik.png}


La figure ci-dessous montre la connexion SSH de l'utilisateur `charlie`,
en mode verbose, afin de voir que l'authentification se fait grâce à un
biclé ainsi que grâce à un code de vérification de Google Authenticator.


![Capture d'écran lors de la connexion de
charlie](Archi1/OpenSSH_Screenshots/charlie2.png){#OpenSSH_Screenshots/charlie2.png}


La figure ci-dessous montre la connexion SSH de l'utilisateur `goose`.
Étant donné que cet utilisateur est un stagiaire qui est là pour
apprendre les bases des commandes UNIX, il nous a semblé judicieux de
lui donner comme shell par défaut un shell restreint : `rbash`.


![Capture d'écran lors de la connexion de
goose](Archi1/OpenSSH_Screenshots/goose.png){#OpenSSH_Screenshots/goose.png}


### Pare-feu

##### Paquets installés

Les paquets nécessaires au fonctionnement du firewall local sont:

-   *iptables*

-   *iptables-persistent*

##### Rôle

Ce rôle Ansible permet de déployer automatiquement un ensemble de règles
consistentes afin de couper le traffic entrant et sortant, sauf aux
ports et protocoles des services utilisés.

Parmi les règles, il y a notamment:

-   INPUT

    -   DROP ipv6

    -   ACCEPT 22/SSH tcp

    -   ACCEPT 53/DNS tcp/udp

    -   ACCEPT 80/HTTP tcp

    -   ACCEPT 443/HTTPS tcp

    -   ACCEPT 8000 tcp

    -   ACCEPT 10000 tcp

    -   ACCEPT ctstate ESTABLISHED,RELATED

    -   GOTO LOGGING

-   LOGGING

    -   LOG tous les paquets (règle primordiale pour le fonctionnement
        de fail2ban : se situe juste avant le DROP). Une limite de
        paquets et de vitesse de réception est appliquée pour ne pas se
        faire \"inonder\";

    -   DROP tout ce qui reste

-   OUTPUT

    -   REJECT ipv6

    -   ACCEPT ctstate ESTABLISHED,RELATED

    -   DROP tout ce qui reste

Les commandes listées ci-dessous correspondent aux règles décrites dans
la liste précedente :

-   `iptables -F`{.bash}

-   `iptables -X`{.bash}

-   `ip6tables -F`{.bash}

-   `ip6tables -X`{.bash}

-   `ip6tables -A INPUT -j DROP`{.bash}

-   `ip6tables -A OUTPUT -j REJECT`{.bash}

-   `iptables -A INPUT --dport 22 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 53 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 53 -p udp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 80 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 443 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 8000 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT --dport 10000 -p tcp -j ACCEPT`{.bash}

-   `iptables -A INPUT -m state --ctstate ESTABLISHED,RELATED -j ACCEPT`{.bash}

-   `iptables -A OUTPUT -m state --ctstate ESTABLISHED,RELATED -j ACCEPT`{.bash}

-   `iptables -N LOGGING`{.bash}

-   `iptables -A LOGGING -j LOG -m limit --limit 1/s --limit-burst 4 --log-prefix "PORT DENIED: " --log-level 6`{.bash}

-   `iptables -A LOGGING -j DROP`{.bash}

-   `iptables -A INPUT -g LOGGING`{.bash}

-   `iptables-save > /etc/iptables/rules`{.bash}

À chaque enregistrement des règles, une copie est sauvegardée avec la
commande : `iptables-save > /etc/iptables/rules`{.bash}

Cette copie sera utilisée à chaque boot par *iptables-persistent* pour
restaurer l'ensemble des règles car *iptables* oublie les règles par
défaut au redémarrage. De cette manière, le filtrage sera permanent.

### Fail2ban

##### Paquets installés

Le paquet nécessaire au fonctionnement de fail2ban est uniquement
*fail2ban*.

##### Rôle

Ce rôle Ansible permet de déployer le service fail2ban. Ce dernier
permet d'analyser à l'aide de filtres puis de bannir, en cas
d'infraction des IPs détectées dans les logs suivis.

Le service bannit les machines qui échouent plusieurs fois lors de:

-   l'authentification ssh abusive (3 tentatives);

-   les requêtes HTTP/HTTPS qui ne sont ni GET ni POST (3 tentatives);

-   les scans de port (ban de 5 minutes).

Pour ce faire, il faut créer des filtres à mettre dans
*/etc/fail2ban/filter.d/*. Chaque filtre est composé d'une *failregex*,
une phrase qui identifie les logs coupables. On peut y rajouter une
exclusion à l'aide cette fois-ci d'une *ignoreregex*, où les logs qui
correspondent sont ignorés. Le fichier de configuration de fail2ban se
situe dans */etc/fail2ban/jail.d/defaults-debian.conf*. Il contient les
scopes des filtres. Le premier est le scope *default* qui contient le
champ *ignoreip* contenant les machines de confiance. Ensuite, il y a un
scope par filtre que l'on appelle des plugins. Chacun dispose de
différents champs dont :

-   *enabled true* : activé;

-   *filter* : nom du filtre utlisé;

-   *port* : ports surveillés dans le cas des requêtes;

-   *logpath /path/to/log* : log du service cible utilisé pour la
    détection;

-   *bantime*: temps de bannissement;

-   *findtime* : temps avant réinitialisation de *maxretry*;

-   *maxretry* : nombre de fois autorisées avant bannissement.

Les illustrations suivantes montrent la configuration à adopter :


![Lancement de la commande pour
MariaDB](Archi1/Fail2ban_Screenshots/1.png){#Fail2ban_Screenshots/1.png}



![Fonctionnement du ban IP pour scan de
port](Archi1/Fail2ban_Screenshots/2.png){#Fail2ban_Screenshots/2.png}



![Fonctionnement du ban IP pour requête avec méthode
interdite](Archi1/Fail2ban_Screenshots/3.png){#Fail2ban_Screenshots/3.png}



![Fonctionnement du ban IP pour abus de connexion
SSH](Archi1/Fail2ban_Screenshots/4.png){#Fail2ban_Screenshots4.png}


## Mise en place d'apache avec Kerberos

### Objectifs et pré-requis

Nous cherchons ici à mettre en place un système d'authentification
sécurisée via Kerberos [^2].\
Pour cela, nous considérons que nous avons un serveur Windows 2012 déjà
configuré via le présent document.

Ci-dessous, le comportement attendu de kerberos sur notre infrastructure
:


![Schéma de la négociation avec le
KDC](Kerberos/kerberos.jpg){#Debian_screenshots/Config/5}


Il faut comprendre :

-   **Mot de passe** : l'utilisateur du domaine `EPITAF` rentre son mot
    de passe ;

-   **Hash** : le mot de passe est ensuite hashé par l'un des
    algorithmes et peut être retrouvé via LSSAS.exe;

-   **AS-REQ** : la machine de l'utilisateur demande un ticket
    d'authentification au serveur windows qui est contrôleur de domaine
    et KDC;

-   **AS-REP** : le KDC vérifie les identifiants et renvoie un ticket
    TGT et une clef de session chiffrés ;

-   **TGS-REQ** : quand l'utilisateur cherchera à se connecter à un
    service, il enverra son ticket TGT et le nom du service auquel il
    veut accéder au Windows Server;

-   **TGS-REP** : le KDC vérifie ensuite le TGT et l'accès au service
    auquel l'utilisateur veut accéder. Il renverra un ticket TGS
    permettant à l'utilisateur d'accéder au service voulu ;

-   **TGS** : le client envoie son ticket TGS récemment reçu au serveur
    pour montrer qu'il peut accéder au service ;

-   **Data** : le serveur fournit le service.

###### 

Afin de pouvoir mettre en place ce comportement, on devra :

-   Configurer le Windows Server (ktpass, création de services, etc) ;

-   Configurer Apache pour qu'il puisse prendre en compte Kerberos ;

-   Configurer les clients qui ne sont pas dans l'AD avec krb5-user ;

-   Modifier la configuration des navigateurs internet pour qu'ils
    puissent prendre en compte la négociation kerberos.

### Configuration de Windows Server

Dans *Gestionnaire de serveur -\> Outils*, cliquer sur DNS


![Accès à la configuration DNS de Windows Server pour
Kerberos](Kerberos/1.png){#Debian_screenshots/Config/5}


Dans *DNS -\> DC01 -\> Zones de recherche directes*, cliquer droit sur
EPITAF.LOCAL puis cliquer sur **Nouvel hôte (A ou AAAA)\...**


![Assertion d'une nouvelle entrée dans la DNS pour
Kerberos](Kerberos/2.png){#Debian_screenshots/Config/5}


Dans **Nom** mettre *infra01* ; dans **Adresse IP** mettre *192.168.3.2*
; cliquer sur **Ajouter un hôte**


![Ajout d'un nouvel hôte pour
Kerberos](Kerberos/3.png){#Debian_screenshots/Config/5}


Dans *Gestionnaire de serveur -\> Outils*, cliquer sur **Centre
d'administration Active Directory**


![Accès au centre d'administration Active
Directory](Kerberos/4.png){#Debian_screenshots/Config/5}


Dans le centre d'administration Active Directory, cliquer droit sur
EPITAF (local) puis dans *Nouveau*, cliquer sur **Utilisateur**


![Création d'un nouvel
utilisateur](Kerberos/5.png){#Debian_screenshots/Config/5}


Dans **Prénom** mettre *apache* ; dans **Ouverture de session** mettre
*apache* ; entrer un mot de passe puis cliquer sur **Ok**


![Ajout de l'utilisateur apache dans
l'AD](Kerberos/6.png){#Debian_screenshots/Config/5}


Entrer la ligne de commande suivante :

``` powershell
  ktpass.exe -princ HTTP/infra01.epitaf.local@EPITAF.LOCAL \ 
  -mapuser apache@EPITAF.LOCAL -pass * \ 
  -crypto AES256-SHA1 -ptype KRB5_NT_PRINCIPAL \ 
  -out C:\http.keytab
```

Lorsque le prompt le demande, entrer le mot de passe, puis entrer la
ligne de commande suivante :

``` powershell
   ktpass.exe -princ HTTPS/infra01.epitaf.local@EPITAF.LOCAL \ 
        -mapuser apache@EPITAF.LOCAL -pass * \ 
        -crypto AES256-SHA1 -ptype KRB5_NT_PRINCIPAL \ 
        -out C:\https.keytab
```

Lorsque le prompt le demande, entrer le mot de passe.

Nous venons de créer le service et mapper l'utilisateur apache dessus.
La commande nous a généré deux fichiers keytab, essentiels pour
qu'Apache2 puisse nous fournir le service attendu.


![Schéma de la négociation avec le
KDC](Kerberos/ktpass.png){#Debian_screenshots/Config/5}


### Configuration du client Kerberos pour un client hors Active Directory

La version client de kerberos pour Windows et linux se trouve ici :
<https://web.mit.edu/kerberos/dist/>.  Sur un debian, il suffit
d'installer le paquet **krb5-user** :

``` shell
$ sudo apt install krb5-user
```

Il suffit ensuite de :

-   Modifier le fichier de configuration **/etc/krb5.conf** comme
    présenté dans le fichier template d'ansible

-   Utiliser `kinit` pour obtenir un ticket de l'utilisateur voulu

-   Utiliser `klist` pour vérifier l'état du cache

-   Utiliser `kvno` (optionnel) pour obtenir un TGS du service voulu

    
    ![Obtention des tickets sur une machine
    linux](Kerberos/k.png){#Debian_screenshots/Config/5}
    

-   Pour pouvoir accéder au site hébergé sur INFRA01 via le navigateur
    web, il faut :

    -   Ouvrir `Firefox` et entrer dans l'url : **about:config**

        
        ![Configuration de firefox pour kerberos -
        about:config](Kerberos/firefox1.png){#Debian_screenshots/Config/5}
        

    -   Cliquer sur **J'accepte le risque** et entrer dans la barre de
        recherche : **network.negotiate-auth.trusted-uris** ; cliquer
        ensuite sur **network.negotiate-auth.trusted-uris**

        
        ![Configuration de firefox pour kerberos -
        network](Kerberos/firefox2.png){#Debian_screenshots/Config/5}
        

    -   Entrer la valeur **192.168.3.2:1000** et cliquer sur *Ok*.

        
        ![Configuration de firefox pour kerberos - valeur du
        serveur](Kerberos/firefox3.png){#Debian_screenshots/Config/5}
        

-   Entrer dans l'url : **192.168.3.2:10000** et appuyer sur *Entrée*.
    Le wordpress devrait être accessible.

    
    ![Accès au wordpress après authentification avec
    kerberos](Kerberos/firefox4.png){#Debian_screenshots/Config/5}
    

### Configuration du serveur Apache avec Kerberos

Pour pouvoir utiliser Kerberos avec apache et respecter les contraintes
imposées, il faut :

-   Installer libapache2-mod-auth-kerb :

    ``` shell
        $ sudo apt install libapache2-mod-auth-kerb
    ```

-   Activer le module auth_kerb :

    ``` shell
        $ sudo a2enmod auth_kerb
    ```

-   Ajouter dans la configuration apache :

    ``` xml
        <VirtualHost *:10000>
            ServerAdmin wordpress@localhost
            DocumentRoot /var/www/html/wordpress/

            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
            DirectoryIndex index.php

            SSLEngine on
            SSLCertificateFile "/etc/apache2/server.crt"
            SSLCertificateKeyFile "/etc/apache2/server.key"


            <Directory "/var/www">
                    Order deny,allow
                    Deny from all
                    Allow from 192.168.2.0/24

                    AuthType Kerberos
                    AuthName "Kerberos Auth"
                    KrbAuthRealms EPITAF.LOCAL
                    KrbServiceName HTTPS
                    Krb5Keytab /etc/apache2/https.keytab
                    KrbMethodNegotiate on
                    KrbMethodK5Passwd off
                    KrbVerifyKDC on
                    Require valid-user
            </Directory>

    </VirtualHost>
    ```

-   Importer les keytabs https.keytab et http.keytab dans
    **/etc/apache2/**

-   Configurer kerberos avec le fichier **/etc/krb5.conf**.

-   Utiliser les commande :

    ``` shell
        $ sudo chown www-data:root /etc/http*.keytab
        $ sudo chmod 640 /etc/http*.keytab
    ```

-   Redémarrer apache :

    ``` shell
        $ sudo systemctl restart apache2
    ```

## Mise en place d'apache Modsecurity

### Objectifs

L'objectif est de mettre en place un pare-feu applicatif permettant de
protéger les applications de INFRA01 ainsi que de filtrer le mot clef
*EPITA* sur les requêtes *POST*, *PUT* et *GET*. Pour cela nous
utiliserons ModSecurity [^3] avec Apache2.\
Le pare-feu présente cependant des limites s'il est utilisé seul.\
Pour palier ce problème, nous utiliserons OWASP Core Set Rule [^4].

La figure [288](#Apache/modsecurity){reference-type="ref"
reference="Apache/modsecurity"} montre le fonctionnement de ModSecurity.
Cela nous permettra de comprendre comment écrire les règles adéquates.


![Phases de traitement de l'information par modsecurity
[@modsecurity-phases]](Apache/modsecurity.jpg){#Apache/modsecurity}


Le cercle représente le processus de traitement de données d'Apache. Les
étiquettes sont les phases avec lesquelles on pourra interférer via
ModSecurity.\
Ce qu'il faut comprendre :

-   **Phase 1** : cette phase se déroule juste après qu'Apache ait fini
    de lire l'en-tête d'une requête. Il est possible d'influer sur la
    façon dont la requête va être traitée.

-   **Phase 2** : lors de cette phase, le corps de la requête est
    accessible, il est donc possible d'en obtenir les arguments.

-   **Phase 3** : cette phase se déroule juste avant que le service
    envoie les en-têtes de la réponse au client. Il est donc possible
    d'acquérir ce qui a été envoyé au client avant qu'il ne le reçoive.

-   **Phase 4** : dans cette phase, le corps de la réponse est
    accessible. Il est possible de détecter des \"information
    disclosure\".

-   **Phase 5** : phase avant l'entrée d'information dans les logs. Il
    est possible d'inspecter les messages d'erreurs d'apache.

### Configuration du serveur Apache avec modsecurity

##### Configuration par défaut

Pour pouvoir utiliser modsecurity avec apache il faut :

-   Installer libapache2-modsecurity :

    ``` shell
        $ sudo apt install libapache2-modsecurity
    ```

-   Activer le module security2 :

    ``` shell
        $ sudo a2enmod security2
    ```

-   Changer **/etc/modsecurity/modsecurity-default.conf** en :\
    **/etc/modsecurity/modsecurity.conf** :

    ``` shell
        $ sudo cp /etc/modsecurity/modsecurity-default.conf \ 
            /etc/modsecurity/modsecurity.conf
    ```

-   Changer dans le fichier; **SecRuleEngine DetectionOnly** en :

    -   **SecRuleEngine On**

-   Redémarrer apache :

    ``` shell
        $ sudo systemctl restart apache2
    ```

##### Changement de la configuration par défaut

Certains paramètres sont à modifier, on obtiendra :

-   **SecResponseBodyLimitation Reject** : par défaut laisse passer les
    réponses qui ne peuvent pas être inspectées dû à leur taille.

-   **SecTmpDir /var/modsecurity/tmp/** : par défaut, écrit les fichiers
    temporaires dans un endroit accessible à tout le monde (/tmp)

-   **SecDataDir /var/modsecurity/persistant/** : par défaut, écrit les
    fichiers persistants dans un endroit accessible à tout le monde
    (/tmp)

-   **SecAuditEngine On** : par défaut ne log que certaines
    transactions.

Il faut ensuite :

-   Créer les dossiers adéquats :

    ``` shell
        $ mkdir -p /var/modsecurity/tmp /var/modsecurity/persistant
    ```

-   Redémarrer apache2

##### Filtrage du mot **EPITA**

On cherche à bloquer le mot clé `EPITA` dans les méthodes *GET*, *PUT*
et *POST*. Pour cela il faut rajouter la ligne suivante dans
**/etc/modsecurity/modsecurity.conf** :

``` shell
    SecRule REQUEST_METHOD "(?:POST|GET|PUT)" \ 
        "phase:2, t:none, chain, deny, msg:'STOP', status:500, id:5555"
    SecRule REQUEST_URI|ARGS|REQUEST_BODY "EPITA" \ 
        "log, auditlog, tag:'KeyWord_EPITA_matched'"
```

On regarde si *EPITA* est présent après avoir regardé si on recevait une
requête GET/POST/PUT. Le message d'erreur sera le 500 et l'évènement
sera placé dans les logs. Tout se passe pendant la phase 2.\
Redémarrer apache :

``` shell
    $ sudo systemctl restart apache2.
```

##### OWASP ModSecurity Core Rule Set

La Configuration par défaut ne suffisant pas, il est possible de se
protéger en utilisant le CRS d'OWASP. OWASP CSR est à ce jour disponible
par défaut avec l'installation de libapache2-mod-security.

Pour installer OWASP ModSecurity CRS manuellement il faut :

-   Cloner le dépôt du CRS :

    ``` shell
        $ git clone https://github.com/SpiderLabs/owasp-modsecurity-crs.git
    ```

-   Inclure **crs-setup.conf** et **rules/\*.conf** dans la
    configuration :

    -   **/etc/apache2/mods-enabled/security2_module**.

-   Redémarrer apache2.

## MISP

### Snort

Se rendre sur la page du gestionnaire de paquets de Pfsense, en cliquant
sur l'onglet **System**, puis sur *Package Manager* :


![image](Archi1/MISP_Screenshots/Snort/1.png)
[\[MISP_Screenshots/Snort/1\]]{#MISP_Screenshots/Snort/1
label="MISP_Screenshots/Snort/1"}



![image](Archi1/MISP_Screenshots/Snort/2.png)
[\[MISP_Screenshots/Snort/2\]]{#MISP_Screenshots/Snort/2
label="MISP_Screenshots/Snort/2"}


Entrer le mot-clé `snort` dans la barre de recherche de paquets :


![image](Archi1/MISP_Screenshots/Snort/3.png)
[\[MISP_Screenshots/Snort/3\]]{#MISP_Screenshots/Snort/3
label="MISP_Screenshots/Snort/3"}


Confirmer l'installation du paquet, en cliquant sur le bouton *Confirm*
:


![image](Archi1/MISP_Screenshots/Snort/4.png)
[\[MISP_Screenshots/Snort/4\]]{#MISP_Screenshots/Snort/4
label="MISP_Screenshots/Snort/4"}


Attendre la fin de l'installation du paquet Snort :


![image](Archi1/MISP_Screenshots/Snort/5.png)
[\[MISP_Screenshots/Snort/5\]]{#MISP_Screenshots/Snort/5
label="MISP_Screenshots/Snort/5"}



![image](Archi1/MISP_Screenshots/Snort/6.png)
[\[MISP_Screenshots/Snort/6\]]{#MISP_Screenshots/Snort/6
label="MISP_Screenshots/Snort/6"}


Afin d'accéder à la page du service Snort sur l'interface web de
Pfsense, cliquer sur l'onglet **Services**, puis sur *Snort* :


![image](Archi1/MISP_Screenshots/Snort/7.png)
[\[MISP_Screenshots/Snort/7\]]{#MISP_Screenshots/Snort/7
label="MISP_Screenshots/Snort/7"}


Ajouter une nouvelle interface WAN en cliquant sur le bouton *Add* :


![image](Archi1/MISP_Screenshots/Snort/8.png)
[\[MISP_Screenshots/Snort/8\]]{#MISP_Screenshots/Snort/8
label="MISP_Screenshots/Snort/8"}


Configurer l'interface WAN, selon la capture d'écran suivante :


![image](Archi1/MISP_Screenshots/Snort/9.png)
[\[MISP_Screenshots/Snort/9\]]{#MISP_Screenshots/Snort/9
label="MISP_Screenshots/Snort/9"}


Ajouter le chemin d'un fichier de configuration dans l'encadré
`Advanced Configuration Pass-Through`. Le texte à écrire est donc :
*include /usr/local/etc/snort/rules/misp.rules* :


![image](Archi1/MISP_Screenshots/Snort/10.png)
[\[MISP_Screenshots/Snort/10\]]{#MISP_Screenshots/Snort/10
label="MISP_Screenshots/Snort/10"}


Dupliquer la configuration de l'interface WAN pour faire une interface
LAN :


![image](Archi1/MISP_Screenshots/Snort/11.png)
[\[MISP_Screenshots/Snort/11\]]{#MISP_Screenshots/Snort/11
label="MISP_Screenshots/Snort/11"}


Configurer la nouvelle interface LAN, tel que sur la capture d'écran
suivante :


![image](Archi1/MISP_Screenshots/Snort/12.png)
[\[MISP_Screenshots/Snort/12\]]{#MISP_Screenshots/Snort/12
label="MISP_Screenshots/Snort/12"}


Comme pour l'interface WAN, ajouter le chemin du fichier de
configuration dans l'encadré `Advanced Configuration Pass-Through` :
*include/usr/local/etc/snort/rules/misp.rules* :


![image](Archi1/MISP_Screenshots/Snort/13.png)
[\[MISP_Screenshots/Snort/13\]]{#MISP_Screenshots/Snort/13
label="MISP_Screenshots/Snort/13"}


De la même manière que pour les interfaces WAN et LAN, créer une
nouvelle interface pour la DMZ :


![image](Archi1/MISP_Screenshots/Snort/14.png)
[\[MISP_Screenshots/Snort/14\]]{#MISP_Screenshots/Snort/14
label="MISP_Screenshots/Snort/14"}


Encore une fois, ajouter le chemin du fichier de configuration dans
l'encadré `Advanced Configuration Pass-Through` : *include
/usr/local/etc/snort/rules/misp.rules* :


![image](Archi1/MISP_Screenshots/Snort/15.png)
[\[MISP_Screenshots/Snort/15\]]{#MISP_Screenshots/Snort/15
label="MISP_Screenshots/Snort/15"}


Cliquer sur le bouton **Play** de chacune des interfaces, dans la
colonne *Snort Status*.


![image](Archi1/MISP_Screenshots/Snort/16.png)
[\[MISP_Screenshots/Snort/16\]]{#MISP_Screenshots/Snort/16
label="MISP_Screenshots/Snort/16"}



![image](Archi1/MISP_Screenshots/Snort/17.png)
[\[MISP_Screenshots/Snort/17\]]{#MISP_Screenshots/Snort/17
label="MISP_Screenshots/Snort/17"}


### Iptables

C'est sur le serveur Web, situé dans la DMZ, que sont gérées les règles
iptables. Celles-ci sont créées suite à la récupération de règles Snort
de la plateforme MISP.\
Un script analysant ces règles Snort, et les traduisant en règles
iptables a été créé. Ce script écrit en Python2.7 est décrit dans le
document *dev.pdf*.

### Squid avec ClamAV

L'installation et la configuration du proxy Squid ayant déjà été
traitées dans le document *archi1.pdf*, il n'est pas nécessaire d'en
reparler ici.\
Lors de l'installation de Squid, l'antivirus ClamAV est également
installé sur le Pfsense. Cet antivirus est capable de traiter des règles
YARA, situées dans le dossier :\
`/var/db/clamav/`\
Aussi, il est possible d'exporter des règles YARA, via la plateforme
MISP, permettant de détecter des malwares ainsi que des outils
d'attaques spécifique à APT17.

Pour cela, nous avons écrit un script Python2.7 utilisant la
bibliothèque PyMISP, récupérant les attributs YARA, et les écrivant dans
le fichier `/var/db/clamav/rules.yara`. Ce script est relancé toutes les
heures à l'aide d'une tâche ajoutée avec crontab.\
Ce script est décrit plus en détail dans le document *dev.pdf*.

## Graylog

Les seules modifications à effectuer sont celles de la configuration
réseau dans le fichier de configuration **/etc/network/interfaces**
selon la figure [289](Archi1/#graylog_screenshots/1.png){reference-type="ref"
reference="graylog_screenshots/1.png"}, et celles concernant le nom
d'hôte dans **/etc/hosts**, tel que sur la figure
[290](Archi1/#graylog_screenshots/2.png){reference-type="ref"
reference="graylog_screenshots/2.png"}.\
Il suffira de redémarrer la machine virtuelle pour que les changements
prennent effet avec la commande suivante : `sudo reboot`{.shell}


![Fichier de configuration
réseau](Archi1/graylog_screenshots/1.png){#graylog_screenshots/1.png}



![Fichier de configuration
réseau](Archi1/graylog_screenshots/2.png){#graylog_screenshots/2.png}


[^1]: Ansible est une plate-forme logicielle libre pour la configuration
    et la gestion des ordinateurs. Elle combine le déploiement de
    logiciels multi nœuds, l'exécution des tâches ad-hoc, et la gestion
    de configuration. Elle gère les différents nœuds à travers SSH et ne
    nécessite l'installation d'aucun logiciel supplémentaire sur
    ceux-ci. Les modules communiquent via la sortie standard en notation
    JSON et peuvent être écrits dans n'importe quel langage de
    programmation. Le système utilise YAML pour exprimer des
    descriptions réutilisables de systèmes, appelés playbook -
    <https://fr.wikipedia.org/wiki/Ansible_(logiciel)>

[^2]: Kerberos est un protocole réseau d'authentification. Il a été
    conçu pour apporter une authentification sûre pour un couple
    client/serveur en utilisant des clés de chiffrement. Il existe une
    implémentation gratuite de ce protocole par le MIT. Kerberos est
    aussi disponible dans plusieurs produits commerciaux -
    <https://web.mit.edu/kerberos/>

[^3]: ModSecurity est un module qui s'intègre au serveur Web Apache et
    qui permet de mettre en place un pare-feu applicatif dédié aux
    applications Web. Il fournit un moteur permettant de détecter et de
    se prémunir des attaques avant qu'elles n'atteignent l'application
    Web protégée.\
    ModSecurity offre les mécanismes suivants :

    -   la journalisation du trafic ;

    -   la surveillance du trafic et détection en temps réel des
        attaques ;

    -   la prévention des attaques et adaptation des règles de détection
        en vue de corriger les vulnérabilités applicatives sans modifier
        réellement les applications Web.

    [@modsecurity]

[^4]: OWASP ModSecurity Core Rule Set (CRS) est un ensemble de règles de
    détection d'attaques génériques à utiliser avec, entre autres,
    ModSecurity. Le CRS a pour but de protéger les applications contre
    une grande variété d'attaques, incluant le top 10 des attaques
    recensées par OWASP. De plus, il génère très peu de fausses
    alertes - <https://modsecurity.org/crs/>
