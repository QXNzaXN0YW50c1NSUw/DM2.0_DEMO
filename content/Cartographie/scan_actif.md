+++
title = "Scan actif"
date = 2021-12-15T01:10:29+01:00
weight = 3
chapter = false
+++



## Découverte des machines présentes sur le réseau

Afin de pouvoir identifier les machines d'un réseau, il est possible de
lancer un scan de découverte avec NMAP.

Plusieurs scans de découverte sont possibles. Cependant, certaines
configurations de logiciels de sécurité permettent de bloquer la
découverte du réseau.

Les commandes suivantes permettent un scan de découverte sur l'ensemble
des adresses IPv4 privées :

``` shell
nmap -PU -sn -n 192.168.0.0/16
nmap -PU -sn -n 10.0.0.0/8
nmap -PU -sn -n 172.16.0.0/12
```

Ces commandes utilisent UDP pour pouvoir détecter la présence de
machines sur le réseau.\
L'utilisation d'UDP étant peu courante, il est probable que les
équipements de sécurité ne soient pas configurés pour la détection de ce
type de scan.

Les options sont :

-   -PU : permet d'ouvrir et de fermer les sondes TCP proprement et donc
    de maîtriser le nombre de connexions utilisées sur la machine
    scannée ;

-   -n : évite de faire une requête DNS, permet de réduire l'empreinte
    réseau du scan ;

-   -sn : empêche le scan de ports.

### Résultat du scan de découverte du réseau

Le scan des adresses IP 192.168.0.0/16 via la commande énoncée plus haut
a permis d'obtenir :


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/discovery_scan_PU.png){#discovery/1}


Ainsi, nous avons pu identifier sur 192.168.0.0/16, 6 machines :

-   **192.168.2.1**, adresse MAC : `08:00:27:CD:BF:EE` ;

-   **192.168.2.2**, adresse MAC : `08:00:27:29:C9:C2` ;

-   **192.168.2.3**, adresse MAC : `08:00:27:96:D4:C3` ;

-   **192.168.2.11**, adresse MAC : `08:00:27:8F:E3:1D` ;

-   **192.168.2.21**, Kali Linux ;

-   **192.168.3.2**, adresse MAC : inconnue car pas dans le même
    sous-réseau.

Pour pouvoir scanner avec des adresses IPv6 il suffit d'utiliser la
commande NMAP :

``` shell
nmap -6 -n -sn fd00::/8
```

Les options sont :

-   -6 : permet d'indiquer l'utilisation de IPv6 ;

-   -n : évite de faire une requête DNS, permet de réduire l'empreinte
    réseau du scan ;

-   -sn : empêche le scan de ports.

### Résultat du scan de découverte des systèmes d'exploitation

Il est possible de faire un deuxième scan sur les machines découvertes
pour identifier leur système d'exploitation. La commande NMAP utilisée
est :

``` shell
nmap -O -n -Pn --osscan-guess 192.168.x.x
```

Les options sont :

-   -O : permet d'activer la détection de système d'exploitation ;

-   -n : évite de faire une requête DNS, permet de réduire l'empreinte
    réseau du scan ;

-   -Pn : considère que la machine cible est en ligne ;

-   --osscan-guess : permet d'indiquer les systèmes d'exploitation
    proches du résultat de la détection.

##### Résultat du scan de découverte pour 192.168.2.1


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/pfsense_os.png){#discovery/1}


##### Résultat du scan de découverte pour 192.168.2.2


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/ws_os.png){#discovery/1}


##### Résultat du scan de découverte pour 192.168.2.3


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/misp_os.png){#discovery/1}


##### Résultat du scan de découverte pour 192.168.2.11


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/w_os.png){#discovery/1}


##### Résultat du scan de découverte pour 192.168.3.2

La figure ci-après nous indique une distance de 2 hops pour joindre la
machine 192.168.3.2 :


![Résultat de la découverte
réseau](Cartographie/Screenshots/discovery/debian_os.png){#discovery/1}


### Empreintes réseau des scans de découverte

Pour chaque machine, **1050 paquets** réseaux ont du être envoyés à la
machine cible pour réaliser le scan.\
Le PCAP de la capture réseau est disponible dans l'archive de la
documentation.

## Recherche des systèmes SCADA

Les infrastructures critiques ont besoin d'être scannés avec précaution.
Afin de déterminer si des systèmes ICS/SCADA sont présents, nous lançons
la commande NMAP suivante :

``` shell
nmap -sT \ 
    -p 80,102,443,502,530,593,789,1089-1091,1911,1962,2222,2404, \ 
       4000,4840,4843,4911,9600,34964,34980,44818,46823,46824,55000-55003 \
    -T1 -v -n --max-parallelism 1 -Pn --packet-trace 192.168.x.x
```

Les options sont :

-   -sT : permet d'ouvrir et de fermer les sondes TCP proprement et donc
    de maîtriser le nombre de connexions utilisées sur la machine
    scannée ;

-   -p *ports* : les ports spécifiés dans la commande NMAP sont les
    ports utilisés le plus fréquemment par les systèmes ICS/SCADA, une
    réponse positive de l'un de ces ports peut indiquer la présence d'un
    ICS/SCADA (hormis les ports 80/443) ;

-   -T1 : le -T est une option permettant de gérer le timing des scans
    de port. Mettre cette option à 1 permet de s'assurer que le scan
    n'est pas détecté par les IDS et ne surcharge pas les machines
    scannées ;

-   -v : permet d'avoir le premier niveau d'information sur le scan en
    cours ;

-   -n : évite de faire une requête DNS, permet de réduire l'empreinte
    réseau du scan ;

-   --max-parallelism 1 : garantit qu'une seule probe est utilisée à la
    fois ;

-   -Pn : empêche le système de ping la machine scannée pour vérifier
    son état, nous considérons que la machine est en ligne. Nous avons
    cette information grâce aux scans précédents ;

-   --packet-trace : permet de suivre l'envoi et la réception des
    paquets. Cette option donne plus d'informations sur comment NMAP
    gère les paquets.

Les ports utilisés correspondent aux tableaux ci-dessous :


![Tableau des ports SCADA/ICS - Partie
1](Cartographie/Screenshots/scada/SCADA1.jpg){#MBSA_screenshots/Install-Win8/8}



![Tableau des ports SCADA/ICS - Partie 2](Cartographie/Screenshots/scada/SCADA2.jpg)


### Scan de la machine 192.168.2.1


![Résultat du scan ICS/SCADA sur la machine
192.168.2.1](Cartographie/Screenshots/scada/scada_pfsense_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan de la machine 192.168.2.2


![Résultat du scan ICS/SCADA sur la machine
192.168.2.2](Cartographie/Screenshots/scada/scada_pfsense_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan de la machine 192.168.2.3


![Résultat du scan ICS/SCADA sur la machine
192.168.2.3](Cartographie/Screenshots/scada/scada_misp_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan de la machine 192.168.2.11


![Résultat du scan ICS/SCADA sur la machine
192.168.2.11](Cartographie/Screenshots/scada/scada_pfsense_scan.png){#MBSA_screenshots/Install-Win8/8}


### Empreintes réseau des scans SCADA/ICS

Pour chaque machine, **224 paquets** réseaux ont du être envoyés à la
machine cible pour réaliser le scan.\
Le PCAP de la capture réseau correspondant à un scan réseau SCADA/ICS
est disponible dans l'archive de la documentation.

## Scan agressif sur les machines du parc

Pour pouvoir identifier les services associés aux ports d'une machine et
détecter certaines vulnérabilités, nous pouvons utiliser une version
agressive de NMAP. Cette variante de NMAP peut faire dysfonctionner les
machines cibles.\
De plus, lors de l'exécution de la commande, l'attaquant s'expose
fortement à la détection des pare-feux et autres composants de sécurité
du réseau ciblé.

La commande ci-dessous permet de lancer un scan agressif sur les
machines dont l'adresse IP est associée :

``` shell
nmap -A \ 
    -n -Pn \ 
    --script http-brute,http-cookie-flags,http-cors,http-csrf, \
    http-date,http-enum,http-errors,http-favicon, \
    ssh-brute,sshv1,ssl-heartbleed,ssl-poodle 192.168.x.x
```

Les options sont :

-   -A : cette option permet d'activer la détection agressive de NMAP.
    En mode agressif, NMAP active la détection de système d'exploitation
    (**-o**), la détection de version (**-sV**), le scan de scripts
    (**-sC**) et le traçage du chemin (**--traceroute**);

-   -n : évite de faire une requête DNS, permet de réduire l'empreinte
    réseau du scan ;

-   -Pn : empêche le système de ping la machine scannée pour vérifier
    son état, nous considérons que la machine est en ligne. Nous avons
    cette information grâce aux scans précédents ;

-   -script *scripts* : cette option permet d'utiliser des scripts NSE
    lors du scan ;

Les scripts utilisés sont :

-   http-brute : permet de brute-force les secrets d'une
    authentification http basique, d'un digest ou d'une authentification
    NTLM ;

-   http-cookie-flag : permet d'examiner les cookies des services HTTP.
    Rapporte toutes les mauvaises configurations des cookies ;

-   http-cors : permet d'identifier des serveurs HTTP vulnérables à une
    Cross-Origin Resource Sharing (CORS) ;

-   http-csrf : permet de détecter les serveurs HTTP vulnérables à des
    Cross Site Request Forgeries (CSRF) ;

-   http-enum : permet d'énumérer les dossiers d'un serveur HTTP à
    partir des plus connus ;

-   http-errors : permet de retourner toutes les pages d'erreurs
    trouvées sur le site ;

-   http-favicon : permet de comparer la favicon du serveur HTTP avec
    une base de données de favicon pour pouvoir identifier le service ;

-   ssh-brute : tente d'établir une connexion SSH avec un brute-force
    des secrets d'authentification ;

-   sshv1 : permet d'identifier si le serveur cible permet une
    communication avec le protocole sshv1 ;

-   ssl-heartbleed : permet d'identifier si le serveur est vulnérable à
    heartbleed ;

-   ssl-poodle : permet d'identifier si le serveur est vulnérable à
    poodle.

### Scan agressif de la machine 192.168.2.1

La figure ci-dessous est le résultat du scan sur 192.168.2.1 :


![Résultat du scan agressif sur la machine
192.168.2.1](Cartographie/Screenshots/agressif/_pfsense_aggressif_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan agressif de la machine 192.168.2.2

Les figures ci-dessous sont le résultat du scan sur 192.168.2.2.\
Le scan permet de nous révéler un Windows Server 2012 R2, vulnérable à
poodle :


![Résultat du scan agressif sur la machine 192.168.2.2 - Partie
1](Cartographie/Screenshots/agressif/_ws_agressif_scan.png){#MBSA_screenshots/Install-Win8/8}



![Résultat du scan agressif sur la machine 192.168.2.2 - Partie
2](Cartographie/Screenshots/agressif/_ws_agressif2_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan agressif de la machine 192.168.2.3

Les figures ci-dessous sont le résultat du scan sur 192.168.2.3.\
Le scan nous permet d'identifier un serveur Linux avec comme information
d'hôte : **misp.circl.lu**.\
La machine est une MISP. Les services tels que SMTP ou encore ZMTP sont
caractéristiques d'une virtual appliance MISP.


![Résultat du scan agressif sur la machine 192.168.2.3 - Partie
1](Cartographie/Screenshots/agressif/_misp_a0_scan.png){#MBSA_screenshots/Install-Win8/8}



![Résultat du scan agressif sur la machine 192.168.2.3 - Partie
2](Cartographie/Screenshots/agressif/_misp_a1_scan.png){#MBSA_screenshots/Install-Win8/8}



![Résultat du scan agressif sur la machine 192.168.2.3 - Partie
3](Cartographie/Screenshots/agressif/_misp_a2_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan agressif de la machine 192.168.2.11

La figure ci-dessous est le résultat du scan sur 192.168.2.11.\
Le scan permet d'identifier un service de Windows. Il s'agit d'une
machine d'un AD :


![Résultat du scan agressif sur la machine
192.168.2.11](Cartographie/Screenshots/agressif/_w_agressif_scan.png){#MBSA_screenshots/Install-Win8/8}


### Scan agressif de la machine 192.168.3.2

La figure ci-dessous permet d'identifier un serveur http nginx :


![Résultat du scan agressif sur la machine
192.168.3.2](Cartographie/Screenshots/agressif/_debian_aggressif_scan.png){#MBSA_screenshots/Install-Win8/8}


### Empreintes réseau des scans agressifs

Le scan agressif a généré plus de **24500 paquets** réseau par machine
scannée.\
Le PCAP associé au scan est disponible dans l'archive de la
documentation.

## Annexe 1


![Représentation graphique des résultats des scans
réseau](Cartographie/Screenshots/SCAN.jpeg){#Annexe/2}


## Annexe 2


![Tableau récapitulatif par IP](Cartographie/Screenshots/annexe2.PNG){#Annexe/2}

