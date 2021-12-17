+++
title = "Périmètre fonctionnel"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
tags = ['Critère 1', 'Critère 2']
+++

## Architecture attendue

Comme le présentent les figures
[\[Architecture_Screenshots/1\]](Archi1/#Architecture_Screenshots/1){reference-type="ref"
reference="Architecture_Screenshots/1"} et
[250](#Schema_tls/1){reference-type="ref" reference="Schema_tls/1"} pour
l'interception SSL/TLS, une fois la documentation mise en œuvre, il sera
obtenu :

-   1 machine virtuelle Windows Server 2012 :

    -   Rôle de domaine contrôleur \"`EPITAF`\";

    -   Nom de machine : DC01;

    -   IP fixe 192.168.2.2, route par défaut 192.168.2.1;

    -   Serveur DHCP -- plage distribuable : 192.168.2.10 -- 20.

-   1 machine virtuelle Windows 10 :

    -   Membre du domaine \"`EPITAF`\";

    -   Nom de machine : PC01;

    -   IP par DHCP.

-   1 machine virtuelle Debian :

    -   Nom de la machine : **INFRA01**;

    -   IP fixe 1920168.3.2, route par défaut 192.168.3.1z;

    -   Toutes les connexions se font sous pfSense.

-   1 machine virtuelle : Virtual appliance (VA) MISP :

    -   Nom de machine : SECU01

    -   IP fixe 192.168.2.3, route par défaut 192.168.2.1

    -   Toutes les connexions à internet se font à travers le PFSense.

-   1 machine virtuelle : Virtual appliance Graylog

    -   Nom de machine : SECU02

    -   IP fixe 192.168.2.4, route par défaut 192.168.2.1

    -   Toutes les connexions à internet se font à travers le PFSense.

-   1 machine virtuelle PFSense :

    -   Routeur par défaut du réseau 192.168.2.0/24 et 192.168.3.0/24 ;

    -   Interface LAN : IP fixe 192.168.2.1

        -   Seuls les flux DNS, HTTP et HTTPs sortant sont autorisés
            depuis 192.168.2.0/24 avec la configuration du DM2.

    -   Interface DMZ : IP fixe 192.168.3.1

        -   Seuls les flux DNS, HTTP et HTTPs sortant sont autorisés
            depuis 192.168.3.0/24 ;

        -   Seuls les flux DNS, HTTP/HTTPs et SSH entrant sont autorisés
            depuis l'interface LAN ;


![image](Archi1/Architecture_Screenshots/archi2.jpeg)
[\[Architecture_Screenshots/1\]]{#Architecture_Screenshots/1
label="Architecture_Screenshots/1"}

