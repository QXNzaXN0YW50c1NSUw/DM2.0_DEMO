+++
title = "Partie 2"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
tags = ['Critère 1', 'Critère 2']
+++


## Comparaisons des résultats des scans des machines

Afin de pouvoir réaliser certains scans de machine, il est important de
positionner le paramètre *Consider Alive* via l'option **Alive Test**
lors de la création des profils des machines. La figure
[\[PART2/1\]](#PART2/1){reference-type="ref" reference="PART2/1"} montre
l'opération :


![image](Analyse/Screenshots/PART2/ping.png) [\[PART2/1\]]{#PART2/1
label="PART2/1"}


### Comparaison des scans *simple* et *ultimate*

Les scans dits **Ultimate** ont été réalisés avec les données
d'authentification des machines du parc, contrairement aux scans
simples.\
Les scans Ultimate ont une meilleure pénétration, puisqu'il est possible
de scanner avec des privilèges élevés.\
Cela se traduit par un plus grand nombre de vulnérabilités découvertes.\
Les figures [\[PART2/2\]](#PART2/2){reference-type="ref"
reference="PART2/2"} et [\[PART2/3\]](#PART2/3){reference-type="ref"
reference="PART2/3"} montrent la différence entre les scans Windows
Server :


![image](Analyse/Screenshots/PART2/ws_simple.PNG) [\[PART2/2\]]{#PART2/2
label="PART2/2"}



![image](Analyse/Screenshots/PART2/ws_ultimate.PNG) [\[PART2/3\]]{#PART2/3
label="PART2/3"}


Les figures [\[PART2/4\]](#PART2/4){reference-type="ref"
reference="PART2/4"} et [\[PART2/5\]](#PART2/5){reference-type="ref"
reference="PART2/5"} montrent la différence entre les scans MISP.


![image](Analyse/Screenshots/PART2/misp_simple.PNG) [\[PART2/4\]]{#PART2/4
label="PART2/4"}



![image](Analyse/Screenshots/PART2/misp_ultimate.PNG) [\[PART2/5\]]{#PART2/5
label="PART2/5"}


La figure [\[PART2/6\]](#PART2/6){reference-type="ref"
reference="PART2/6"} montre l'analyse d'une bibliothèque dynamique sur
le disque de Windows Server 2012.\
La vulnérabilité trouvée n'est possible qu'avec des droits privilégiés,
via l'utilisation des secrets fournis dans le scan Ultimate de Windows
Server.


![image](Analyse/Screenshots/PART2/ws_ultimate_exemple.PNG)
[\[PART2/6\]]{#PART2/6 label="PART2/6"}

