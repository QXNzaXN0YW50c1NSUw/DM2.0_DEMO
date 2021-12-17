+++
title = "Exécution d'un déploiement de MBSA"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
+++

## Présentation

**Microsoft Baseline Security Analyzer** offre la possibilité
d'effectuer une analyse sur un ensemble de machines. Cet ensemble peut
être défini selon deux manières :

-   Sur un domaine

-   Sur une plage d'adresses IPv4

Cependant, afin que les machines de l'ensemble à analyser puissent être
examinées, il faut tout d'abord faire certaines configurations, autant
sur le contrôleur de domaine duquel l'analyse sera lancée que sur les
machines qui seront analysées.\

## Configurations requises

### Configurations sur Windows Server 2012

Afin que MBSA puisse analyser les machines autres que celle à partir de
laquelle le scan est lancé, il faut que le service *Remote Registry* (ou
*Registre à distance*) soit démarré. Ainsi, pour le démarrer sur toutes
les machines, il est possible de créer une GPO.\
Pour cela, il faut ouvrir le gestionnaire des stratégies de groupe :


![Accès au gestionnaire des stratégies de
groupe](/Microsoft_annexe/Screenshots/Config/Config-1.png){#Screenshots/Config/1}


Dérouler les `Domaines` dans l'onglet gauche. Cliquer droit sur le
domaine *EPITAF.local*, puis cliquer sur *Créer un objet GPO dans ce
domaine, et le lier ici\...* :


![Initiation de création d'une nouvelle GPO dans le domaine
`EPITAF.local`](/Microsoft_annexe/Screenshots/Config/Config-2.png){#Screenshots/Config/2}


Donner un nom à la nouvelle GPO ; ici `Remote Registry`. Cliquer sur
*OK* :


![Création d'un nouvel objet
GPO](/Microsoft_annexe/Screenshots/Config/Config-3.png){#Screenshots/Config/3}


Une fois la nouvelle GPO créée, il faut la configurer. Pour cela,
cliquer droit sur la GPO *Remote Registry* puis cliquer sur *Modifier* :


![Accès à l'éditeur de gestion des stratégies de groupe pour éditer la
GPO](/Microsoft_annexe/Screenshots/Config/Config-4.png){#Screenshots/Config/4}


Aller dans : `Configuration ordinateur` \> `Paramètres Windows` \>
`Paramètres de sécurité` \> `Services système`. Enfin, rechercher le
service *Registre à distance* dans la liste, puis cliquer droit dessus
pour accéder à ses **Propriétés** :


![Accès aux propriétés du service
`Registre à distance`](/Microsoft_annexe/Screenshots/Config/Config-5.png){#Screenshots/Config/5}


Sélectionner les mêmes informations que sur la figure suivante, puis
cliquer sur *OK* :


![Propriétés du service
`Registre à distance`](/Microsoft_annexe/Screenshots/Config/Config-6.png){#Screenshots/Config/6}


Au prochain redémarrage des machines du domaine, la GPO prendra effet,
et le service *Registre à distance* sera démarré automatiquement.\

Maintenant, il faut configurer le Pare-feu Windows.\
Il faut tout d'abord autoriser l'application MBSA à communiquer à traver
le Pare-feu. Ouvrir le Pare-feu Windows, via la recherche Windows ou via
le `Panneau de configuration`, dans *Système et sécurité*, puis
*Pare-feu Windows*. Cliquer sur \"*Autoriser une application ou une
fonctionnalité via le Pare-feu Windows*\"


![Accès aux autorisations d'applications du pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-7.png){#Screenshots/Config/7}


Cliquer sur *Autoriser une autre application* :


![Autorisations des applications à communiquer à travers le Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-8.png){#Screenshots/Config/8}


Sélectionner *Microsoft Baseline Security Analyzer 2.1* dans la liste,
puis cliquer sur *OK* :


![Sélection de l'application MBSA à ajouter aux autorisations du
Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-9.png){#Screenshots/Config/9}


Vérifier que MBSA est bien autorisé sur le Domaine. Cliquer sur *OK* :


![Vérification de l'autorisation de MBSA du Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-10.png){#Screenshots/Config/10}


Sélectionner la fonctionnalité *Service Accès réseau* en cochant pour le
`Domaine`, puis cliquer sur *OK* :


![Autorisation de la fonctionnalité *Service Accès réseau* sur le
Domaine](/Microsoft_annexe/Screenshots/Config/Config-11.png){#Screenshots/Config/11}


###### Configurations sur les machines du domaine

Sur la machine Windows 8.1 (PC01), ouvrir le pare-feu Windows, via la
recherche Windows ou via le `Panneau de configuration`, dans *Système et
sécurité*, puis *Pare-feu Windows*. Cliquer sur \"*Autoriser une
application ou une fonctionnalité via le Pare-feu Windows*\" :


![Accès aux autorisations d'applications du Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-12.png){#Screenshots/Config/12}


Cliquer sur *Modifier les paramètres* :


![Obtention des privilèges pour modifier les paramètres concernant les
applications autorisées à communiquer à travers le Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-13.png){#Screenshots/Config/13}


Entrer les identifiants d'un utilisateur ayant suffisamment de
privilèges pour apporter des modifications aux paramètres concernant les
applications autorisées à communiquer à travers le Pare-feu Windows,
puis cliquer sur *Oui* :


![Utilisation d'un compte Administrateur pour modifier les paramètres
concernant les applications autorisées à communiquer à travers le
Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-14.png){#Screenshots/Config/14}


Sélectionner les deux fonctionnalités suivantes, pour le `Domaine` :
*Recherche du réseau* et *Service Accès réseau*. Enfin, cliquer sur *OK*
:


![Sélection des fonctionnalités autorisées à communiquer à travers le
Pare-feu
Windows](/Microsoft_annexe/Screenshots/Config/Config-15.png){#Screenshots/Config/15}


## Déploiement d'une analyse MBSA sur le domaine

Pour ce déploiement, le domaine comporte deux machines sous Windows 8.1
: PC01 et PC02.\
Sur la machine Windows Server 2012 (DC01), ouvrir MBSA. Cliquer sur
*Analyser plusieurs ordinateurs* :


![Sélection du périmètre pour l'analyse avec MBSA sur le domaine
`EPITAF`](/Microsoft_annexe/Screenshots/Rapport/Rapport-0-0.png){#Screenshots/Rapport/00}


Donner le nom du domaine sur lequel exécuter l'analyse MBSA, ou bien la
plage d'adresses IPv4. Sur la figure
[17](/Microsoft_annexe/#Screenshots/Rapport/01){reference-type="ref"
reference="Screenshots/Rapport/01"}, l'analyse est effectuée sur le
domaine `epitaf`. Il faut également sélectionner les options pour
l'analyse MBSA. Cliquer sur *Démarrer l'analyse* :


![Paramétrage des options pour l'analyse MBSA sur le domaine
`EPITAF`](/Microsoft_annexe/Screenshots/Rapport/Rapport-0-1.png){#Screenshots/Rapport/01}


Patienter pendant l'analyse MSBA :


![Analyse MBSA en cours sur le domaine
`EPITAF`](/Microsoft_annexe/Screenshots/Rapport/Rapport-0-2.png){#Screenshots/Rapport/02}


Une fois l'analyse terminée, des rapports sont générés pour chaque
machine analysée. Sélectionner en premier le rapport pour la machine
`DC01`, en cliquant dessus :


![Écran présentant les rapports d'analyse de sécurité générés par
MBSA](/Microsoft_annexe/Screenshots/Rapport/Rapport-1.png){#Screenshots/Rapport/1}



![Détails du rapport de l'analyse MBSA sur
`EPITAF\DC01`](/Microsoft_annexe/Screenshots/Rapport/Rapport-2.png){#Screenshots/Rapport/2}



![Détails du rapport de l'analyse MBSA sur `EPITAF\DC01`
(/Microsoft_annexe/suite)](Screenshots/Rapport/Rapport-3.png){#Screenshots/Rapport/3}



![Détails du rapport de l'analyse MBSA sur `EPITAF\DC01`
(/Microsoft_annexe/fin)](Screenshots/Rapport/Rapport-4.png){#Screenshots/Rapport/4}


Pour voir le rapport suivant, il faut revenir en arrière en cliquant sur
la flèche retour en haut à gauche de la fenêtre, ou bien cliquer sur
*OK*, en bas à droite de la fenêtre. Sélectionner le rapport suivant,
concernant la machine `PC02` :


![Détails du rapport de l'analyse MBSA sur
`EPITAF\PC02`](/Microsoft_annexe/Screenshots/Rapport/Rapport-5.png){#Screenshots/Rapport/5}



![Détails du rapport de l'analyse MBSA sur `EPITAF\PC02`
(/Microsoft_annexe/fin)](Screenshots/Rapport/Rapport-6.png){#Screenshots/Rapport/6}


Comme précédemment, revenir à l'écran de choix des rapports générés par
MBSA, afin de choisir le rapport de la machine `PC01` :


![Détails du rapport de l'analyse MBSA sur
`EPITAF\PC01`](/Microsoft_annexe/Screenshots/Rapport/Rapport-7.png){#Screenshots/Rapport/7}



![Détails du rapport de l'analyse MBSA sur `EPITAF\PC01`
(/Microsoft_annexe/fin)](Screenshots/Rapport/Rapport-8.png){#Screenshots/Rapport/8}


Les rapports des machines DC01 et PC01 sont les mêmes que ceux générés
par leur analyse MBSA locale détaillée expliquée dans le document
**microsoft.pdf**.\
Également, ces rapports sont stockés sous format XML. Les fichiers sont
situés dans le dossier `doc/scan/MBSA/Scan-parc`.
