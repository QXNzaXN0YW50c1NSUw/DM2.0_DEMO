+++
title = "Déroulé d'une analyse avec MBSA"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
+++

## Présentation générale de l'utilisation de MBSA

Tout d'abord, MBSA doit être exécuté avec un compte à privilèges. En
effet, un simple utilisateur du domaine n'a pas le droit d'exécuter ce
logiciel :


![Contrôle de compte
utilisateur](Microsoft/Screenshots/WS-MBSA-install-11.png){#11}


Ensuite, MBSA peut être utilisé de deux manières :

-   Via l'interface graphique : *mbsa.exe*

-   Via l'invite de commande : *mbsacli.exe*

L'analyse peut être réalisée sur une seule machine ou bien sur
plusieurs. L'analyse sur une machine est traitée dans la suite de ce
document. L'analyse de plusieurs machines d'un parc est traitée dans le
document **microsoft-annexe.pdf**.\
Ainsi, pour analyser une machine avec MBSA, il faut donner le nom de la
machine à analyser, ou bien son adresse IPv4. Il faut également
sélectionner les options qui seront utilisées pour l'analyse.\
Une fois l'analyse terminée, MBSA génère un rapport au format XML. Ces
rapports sont stockés dans le dossier suivant :
`C:\Users\<nom_utilisateur>\SecurityScans`.

## Exécution de MBSA en local sur PC01

Le PC01 est une machine sous Windows 8.1, sur laquelle MBSA 2.3 a été
installé.

### Utilisation de MBSA par son interface graphique

Ouvrir le logiciel MBSA en double-cliquant sur le raccourci créé à
l'installation sur le bureau. Cliquer sur *Analyser un ordinateur* :


![Sélection du périmètre pour l'analyse avec
MBSA](Microsoft/Screenshots/Win8-local/Rapport-1.png){#Screenshots/Win8-local/1}


Choisir l'ordinateur à analyser, soit en donnant son nom, soit en
donnant son adresse IPv4. Ici, c'est la machine PC01 du domaine EPITAF
(`EPITAF\PC01`). Il faut également sélectionner les options pour
l'analyse MBSA.\
Pour le scan de la capture d'écran ci-dessous, nous avons choisi de
garder toutes les options, c'est-à-dire que l'analyse va porter sur :

-   les vulnérabilités d'administration de Windows ;

-   les mots de passe vulnérables ;

-   les vulnérabilités d'administration de IIS ;

-   les vulnérabilités de SQL ;

-   les mises à jour de sécurité.

Cliquer sur *Démarrer l'analyse* :


![Paramétrage des options pour l'analyse
MBSA](Microsoft/Screenshots/Win8-local/Rapport-2.png){#Screenshots/Win8-local/2}


Patienter pendant l'analyse MSBA


![Analyse MBSA en cours sur la machine
`EPITAF\PC01`](Microsoft/Screenshots/Win8-local/Rapport-3.png){#Screenshots/Win8-local/3}


Une fois l'analyse terminée, le rapport est affiché. Il indique le
niveau de sécurité, soit *Risque important* selon la capture d'écran
suivante. Les résultats portent sur de multiples catégories :


![Détails du rapport de l'analyse MBSA sur
`EPITAF\PC01`](Microsoft/Screenshots/Win8-local/Rapport-4.png){#Screenshots/Win8-local/4}


Ainsi, on peut voir que le PC01 n'a pas toutes les mises à jour de
sécurité installées. En regardant dans les *Détails* de cette catégorie,
MBSA liste les mises à jour de sécurité manquantes, ainsi que celles qui
sont bien installées, dans les figures
[9](Microsoft/#Screenshots/Win8-local/6){reference-type="ref"
reference="Screenshots/Win8-local/6"} et
[10](Microsoft/#Screenshots/Win8-local/7){reference-type="ref"
reference="Screenshots/Win8-local/7"}.\

Également, cet ordinateur possède une vulnérabilité d'administration,
concernant des mots de passe qui n'expirent jamais. En cliquant sur
*Détails du résultat* pour cette vulnérabilité, on obtient :


![Détails concernant la catégorie *Expiration des mots de passe* dans
les résultats de l'analyse Windows, sur les vulnérabilités
d'administration](Microsoft/Screenshots/Rapport/Rapport-9.png){#Screenshots/Rapport/9}


Pour la catégorie de vulnérabilité *Test des mots de passe des comptes
locaux*, la fenêtre de détails est la suivante (obtenue en cliquant sur
*Détails*) :


![Détails concernant la catégorie *Test des mots de passe des comptes
locaux* dans les résultats de l'analyse Windows, sur les vulnérabilités
d'administration](Microsoft/Screenshots/Rapport/Rapport-10.png){#Screenshots/Rapport/10}


La figure ci-dessous est la suite du rapport de l'analyse MBSA pour
PC01.


![Détails du rapport de l'analyse MBSA sur `EPITAF\PC01`
(/Microsoft/fin)](Screenshots/Win8-local/Rapport-5.png){#Screenshots/Win8-local/5}


MBSA permet aussi d'obtenir des informations système supplémentaires,
portant notamment sur l'audit, les services, les partages, ou encore la
version de Windows. Aussi, les services IIS et SQL Server n'étant pas
activés sur cette machine, MBSA informe seulement qu'ils ne sont pas
activés sur cet ordinateur.

Sur certains résultats de l'analyse, il est possible d'accéder à des
détails. Sur la figure
[9](Microsoft/#Screenshots/Win8-local/6){reference-type="ref"
reference="Screenshots/Win8-local/6"}, ce sont les détails concernant
les mises à jour de sécurité. Cette partie du rapport permet de donner
les ID des éléments qui ne sont pas présents sur le système, telle que
la mise à jour **MS13-098** :


![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de
sécurité](Microsoft/Screenshots/Win8-local/Rapport-6.png){#Screenshots/Win8-local/6}


La capture d'écran suivante
(/Microsoft/[10](#Screenshots/Win8-local/7){reference-type="ref"
reference="Screenshots/Win8-local/7"}) est la suite de la figure
précédente (/Microsoft/[9](#Screenshots/Win8-local/6){reference-type="ref"
reference="Screenshots/Win8-local/6"}), et montre les mises à jour qui
sont actuellement présentes sur le système :


![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de sécurité
(/Microsoft/fin)](Screenshots/Win8-local/Rapport-7.png){#Screenshots/Win8-local/7}


### Utilisation de MBSA par invite de commande

L'analyse d'une machine par Microsoft Baseline Security Analyzer peut
également se faire en utilisant une invite de commande. Pour cela, il
faut ouvrir une invite de commande en ayant les droits suffisants.
Ensuite, la commande permettant d'effectuer une analyse équivalente à
celle présentée précédemment est la suivante :
`mbsacli.exe /target EPITAF\PC01 /n OS+IIS+SQL+PASSWORD`{.powershell}.\
L'exécution de cette commande est montrée sur la figure ci-dessous :


![Exemple d'exécution d'une analyse MBSA via une invite de
commande](Microsoft/Screenshots/Win8-local/Rapport-8.png){#Screenshots/Win8-local/8}


Ce rapport est également stocké sous format XML. Le fichier est situé
dans le dossier `doc/scan/MBSA/Local-PC01`.

## Exécution de MSBA en local sur DC01

Le DC01 est une machine sous Windows Server 2012, qui est un contrôleur
domaine, et sur lequel MBSA 2.1 a été installé.\
L'utilisation de MBSA se fait de la même manière sur Windows Server 2012
que sur Windows 8.1. La démarche reste la même : utilisation du nom de
la machine à analyser (ici, `EPITAF\DC01`), et sélection des options à
analyser.\
Sur la machine Windows Server 2012 (DC01), ouvrir le logiciel MBSA. Tout
comme sur la machine Windows 8.1 (PC01), sélectionner le périmètre sur
lequel l'analyse MBSA va porter. Ici, l'on choisit d'analyser un
ordinateur.


![Sélection du périmètre pour l'analyse avec
MBSA](Microsoft/Screenshots/WS-local/Rapport-0.png){#Screenshots/WS-local/0}


L'analyse porte ici sur la machine Windows Server 2012. Le nom de
l'ordinateur est donc `EPITAF\DC01`. Il faut également sélectionner les
options pour l'analyse MBSA. Ces options sont les mêmes que pour
l'analyse sur PC01. Cliquer sur *Démarrer l'analyse* :


![Paramétrage des options pour l'analyse
MBSA](Microsoft/Screenshots/WS-local/Rapport-1.png){#Screenshots/WS-local/1}


Patienter pendant l'analyse MSBA :


![Analyse MBSA en cours sur la machine
`EPITAF\DC01`](Microsoft/Screenshots/WS-local/Rapport-2.png){#Screenshots/WS-local/2}


Ci-dessous, le rapport obtenu après analyse du DC01, sous forme de
captures d'écran :


![Détails du rapport de l'analyse MBSA sur
`EPITAF\DC01`](Microsoft/Screenshots/WS-local/Rapport-3.png){#Screenshots/WS-local/3}



![Détails du rapport de l'analyse MBSA sur `EPITAF\DC01`
(/Microsoft/suite)](Screenshots/WS-local/Rapport-4.png){#Screenshots/WS-local/4}



![Détails du rapport de l'analyse MBSA sur `EPITAF\DC01`
(/Microsoft/fin)](Screenshots/WS-local/Rapport-5.png){#Screenshots/WS-local/5}


De la même manière que pour PC01, le DC01 ne possède pas toutes les
mises à jour de sécurité. En effet, le rapport indique que 91 mises à
jour de sécurité sont absentes, de même que 10 Service Packs ou
correctifs cumulatifs (figure
[15](Microsoft/#Screenshots/WS-local/3){reference-type="ref"
reference="Screenshots/WS-local/3"}).

En cliquant sur *Détails* pour la catégorie des mises à jour, MBSA liste
toutes les mises à jour de sécurité qui ne sont pas installées et qui
devraient l'être :


![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de
sécurité](Microsoft/Screenshots/Rapport/Rapport-11.png){#Screenshots/Rapport/11}



![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de sécurité
(/Microsoft/suite)](Screenshots/Rapport/Rapport-12.png){#Screenshots/Rapport/12}



![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de sécurité
(/Microsoft/suite)](Screenshots/Rapport/Rapport-13.png){#Screenshots/Rapport/13}



![Détails concernant la catégorie *Windows - Mises à jour de sécurité*
dans les résultats sur les mises à jour de sécurité
(/Microsoft/fin)](Screenshots/Rapport/Rapport-14.png){#Screenshots/Rapport/14}


De plus, du point de vue de l'analyse Windows, il existe plusieurs
vulnérabilités d'administration, dont notamment :

-   Le service de mise à jour automatique qui n'est pas configuré pour
    être lancé automatiquement ;

-   Présence de plus de deux administrateurs sur cet ordinateur ;

-   Deux comptes d'utilisateurs possèdent un mot de passe qui n'expire
    jamais, tout comme pour PC01.

Contrairement au PC01, les services Internet IIS sont activés sur le
DC01. C'est pour cela que certaines vulnérabilités sont listées dans la
catégorie *Résultats de l'analyse des services Internet IIS -
Vulnérabilités d'administration* (figure
[16](Microsoft/#Screenshots/WS-local/4){reference-type="ref"
reference="Screenshots/WS-local/4"}).\
De même, SQL Server est installé sur le DC01, d'où la présence d'une
liste de vulnérabilités dans la catégorie *Résultats de l'analyse de SQL
Server - Vulnérabilités d'administration* (figure
[17](Microsoft/#Screenshots/WS-local/5){reference-type="ref"
reference="Screenshots/WS-local/5"}).\
Ce rapport est également stocké sous format XML. Le fichier est situé
dans le dossier `doc/scan/MBSA/Local-DC01`.
