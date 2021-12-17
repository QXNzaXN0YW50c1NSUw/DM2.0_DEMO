+++
title = "Découvertes des réseaux"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
tags = ['Question 1', 'Question 2', 'Question 3', 'Question 4']
+++


## Comment le logiciel identifie-t-il le type de matériel suite à au moins une écoute passive du réseau ? 

Le logiciel peut capturer des paquets contenant l'adresse MAC des
machines et ainsi en récupérer des informations comme par exemple le
constructeur ou le type d'appareil.

## Comment le logiciel identifie-t-il le système d'exploitation ?

Le logiciel identifie le type de système d'exploitation grâce à une
empreinte de la pile TCP/IP de la machine ciblée.\
Ainsi, après avoir envoyé des paquets TCP/IP à la machine cible,
l'analyse des réponses de la machine scannée permet (ou non)
d'identifier un système d'exploitation.

## Comment le logiciel identifie-t-il les services exposés ?

Pour Nmap, une fois que les ports TCP et/ou UDP ont été découverts grâce
à l'une des méthodes de scan, la détection de version interroge ces
ports-là pour en savoir plus sur le type de service qui tourne dessus.
La base de données *nmap-service-probes* contient des sondes pour
interroger de multiples services, et comparer les expressions pour
reconnaître les réponses et les analyser. Nmap essaye de déterminer le
protocole du service, le nom de l'application, le numéro de version, le
nom d'hôte, le type de périphérique, et la famille du système
d'exploitation.\
Lorsque des services RPC ont été mis en évidence, le module RPC de Nmap
est utilisé pour déterminer le programme RPC et les numéros de version.
Il prend tous les ports TCP/UDP détectés comme étant du RPC, et les
inonde avec des commandes NULL du programme *SunRPC*, pour tenter de
déterminer s'il s'agit bien de ports RPC, et si oui, de déterminer quel
programme et quel numéro de version ils servent.\
Lorsque Nmap reçoit des réponses d'un service mais qu'il ne peut pas les
faire correspondre à sa base de données, il affiche une empreinte
spéciale ainsi qu'une URL à laquelle il est possible de soumettre ce qui
s'exécute sur ce port ; mais cela uniquement si l'on est certain de ce
qui s'exécute.

## Qu'est-ce qu'un script NSE ?

Les scripts NSE permettent aux utilisateurs d'automatiser un certain
nombre de tâches liées au réseau.
