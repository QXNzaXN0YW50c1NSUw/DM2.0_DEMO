+++
title = "Périmètre fonctionnel"
date = 2021-12-15T01:10:29+01:00
weight = 2
chapter = false
+++


## Architecture attendue

Comme le présentent les figures
[\[Architecture_Screenshots/1\]](Archi2/#Architecture_Screenshots/1){reference-type="ref"
reference="Architecture_Screenshots/1"}, une fois la documentation mise
en œuvre, il sera obtenu en complément de l'architecture de la
documentation archi1.pdf :

-   1 machine virtuelle : Virtual appliance kali

    -   Nom de machine : KALI01

    -   IP fixe 192.168.2.21, route par défaut 192.168.2.1

    -   Toutes les connexions à internet se font à travers le PFSense.

-   1 machine virtuelle : Windows 8.1

    -   Nom de machine : PC02

    -   IP par DHCP, route par défaut 192.168.2.1

    -   Toutes les connexions à internet se font à travers le PFSense.


![image](Archi2/Architecture_Screenshots/Archi2_dm6.jpeg)
[\[Architecture_Screenshots/1\]]{#Architecture_Screenshots/1
label="Architecture_Screenshots/1"}

