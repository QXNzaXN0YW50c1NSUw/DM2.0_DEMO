+++
title = "Gestions des vulnérabilités avec un scanner de type host-based"
date = 2021-12-15T01:10:29+01:00
weight = 3
chapter = false
tags = ['Question 9']
+++

## Quelle est la différence entre un scanner de type host-based et network-based ?

Un scanner de type host-based examine les configurations du système, les
systèmes de fichiers, les paramètres des registres, et toutes sortes
d'autres informations qu'un hôte possède. Ces outils permettent
d'apporter une vision \"administrateur\" de l'environnement et de son
exposition.\
Un scanner de type network-based est conçu pour découvrir l'existence de
vulnérabilités au sein d'un réseau. Ces outils permettent de donner un
aperçu de l'environnement au niveau du réseau. Ce type de scanner adopte
en général une vision \"attaquant\" de l'environnement.\
Également, un scanner de type network-based est rapide et facilement
déployable. Ils sont utiles pour détecter des périphériques escrocs sur
le réseau, ou encore des services étranges en fonctionnement. Un scanner
de type host-based est en général plus difficile à déployer qu'un
scanner de type network-based, notamment car il requiert souvent
l'installation d'un agent sur les systèmes. Aussi, ils vont permettre
d'évaluer les dommages potentiels qui peuvent être causés autant par des
personnes internes qu'externes, une fois qu'un certain niveau d'accès
est accordé (légitimement ou non) sur un système.
