+++
title = "Développement"
date = 2021-12-15T01:10:29+01:00
weight = 3
chapter = false
+++

## Fonctions

## Description des fonctions

### Create-CA

Cette fonction s'occupe de la création du certificat de la root CA
(Autorité de certification). En premier lieu, il faut créer
l'arborescence, puis verrouiller l'accès au dossier de l'AC. Les
fichiers d'index et de serial sont initialisés. Enfin, on génère le
certificat AC à l'aide d'une clé RSA. Des données spécifiques à l'AC
sont demandées à l'administrateur. Ce certificat est un tiers de
confiance permettant d'identifier l'identité des correspondants.

### User-req

Cette fonction s'occupe de générer les clés privée et publique de
l'utilisateur en paramètre. Ensuite, on établit la demande de signature
de certificat (CSR) à l'aide de cette clé. Le but sera de l'adresser à
l'AC afin d'obtenir un certificat numérique signé. Encore une fois, il
est demandé, cette fois-ci à l'utilisateur, de saisir les informations
qui lui sont propres.

### User-sign

Cette fonction s'occupe simplement de soumettre la demande de signature
(CSR) à l'autorité de certification. Afin d'être validé, le certificat
devra respecter une police stricte, par exemple avoir le même pays ou
nom d'organisation. En cas de succès et de confirmation par
l'utilisateur, un certificat signé par l'AC est émis.

### Revoke

Cette fonction révoque le certificat donné en paramètre en l'inscrivant
dans la base de données correspondant à la liste de révocation de
certificats (CRL). Ce certificat sera par la suite refusé même s'il est
toujours en cours de validité.

### GenCRL

Cette fonction génère un fichier, à partir de la base de données
correspondante, qui est la CRL et qui comprend tous les certificats
révoqués.

### GenOCSP

Cette fonction réalise deux actions : demande de création d'un
certificat pour le serveur OCSP, et génération du certificat par la root
CA.\
Pour la première action, on fait une requête CSR. La commande utilise
l'extension `v3_OCSP`, présente dans le fichier de configuration
*openssl-ca.cnf*. Cette commande crée un fichier *ocsp.csr* dans le
dossier *miniCA\\csr*, et génère une clé privée *ocsp.pem*, située dans
le dossier *miniCA\\private*.\
Pour la deuxième action, on génère le certificat, signé par la root CA.
On utilise une seconde fois l'extension `v3_OCSP`. Le certificat généré
est *ocsp.pem*, et est situé dans le dossier *miniCA\\cert*.

### LaunchOCSP

Cette fonction permet de lancer le serveur OCSP, afin d'éviter de le
lancer à la main. Il utilise le certificat *miniCA\\cert\\ocsp.pem* pour
signer les réponses OCSP, ainsi que la clé privée
*miniCA\\private\\ocsp.pem*, également pour signer les réponses OCSP.

## Gestion des arguments

Nous utilisons un `Switch`{.powershell} pour savoir quelle action est
attendue du script `mini-pki.ps1`. Les actions possibles sont :

-   `create-ca` : appelle la fonction `Create-CA`{.powershell}

-   `user-req` : appelle la fonction `User-req`{.powershell}

-   `user-sign` : appelle la fonction `User-sign`{.powershell}

-   `revoke` : appelle la fonction `Revoke`{.powershell}

-   `gencrl` : appelle la fonction `GenCRL`{.powershell}

-   `genocsp` : appelle la fonction `GenOCSP`{.powershell}

-   `ocsp` : appelle la fonction `LaunchOCSP`{.powershell}.

## Signatures ClamAV

ClamAV utilise plusieurs formats de signature. Dans le cadre de cette
documentation, nous en retiendrons deux :

-   les *.yara* [@yara-signatures] [@yara-hunting-signatures];

-   les *.ndb*[@ndb-signatures].

## Description des formats de signature

### yara

est un outil développé par *VirusTotal* qui permet notamment
d'identifier ou de classifier des échantillons de malware. Ici, yara
nous est utile dans la mesure où il permet de reconnaître une suite de
caractères dans un document.

### ndb

est un format de signature basique utilisé par CalmAV pour la detection
de virus dans les corps des objets.\
Ce format permet de spécifier plus d'informations à rechercher lors de
l'analyse des données.

## Description des signatures

### yara

utilise une syntaxe simple.\
Notre fichier src/epita.yara fonctionne comme suit :

1.  Il déclare une variable contenant *epita* via le mot clé `strings`.

2.  Il déclare ensuite la condition de détection via le mot clé
    `condition`.

``` c
rule epita
{
	strings:
		$a = /epita/ 
	condition:
		$a
}
```

### ndb

utilise aussi une syntaxe simple.\
Il se présente sous la forme :

``` c
MalwareName:TargetType:Offset:HexSignature[:min_flevel:[max_flevel]]
```

Avec :

-   **MalwareName** : nom du malware => il existe une nomenclature mise
    en place par clamAV.

-   **TargetType** : valeur de 0 à 7

    -   0 : tout type de fichier

    -   1 : les exécutables Windows (format PE)

    -   2 : les scripts

    -   3 : HTML normalisé (voir archi.pdf)

    -   4 : fichier mail

    -   5 : graphiques

    -   6 : les exécutables au format ELF

    -   7 : fichier texte ASCII normalisé

-   **Offset** : valeur à laquelle débuter la recherche.

-   **HexSignature** : le mot clé que nous voulons chercher dans le
    document

-   **\[:min_flevel:\[max_flevel\]\]** : ce sont des options ; elles
    permettent d'indiquer un niveau de compression pour pouvoir, par
    exemple, détecter les virus avec un certain niveau de compression.
    Nous n'utiliserons pas ces options.

Dans notre cas la signature sera donc :

``` c
HTML.EPITA:0:*:6570697461
```
