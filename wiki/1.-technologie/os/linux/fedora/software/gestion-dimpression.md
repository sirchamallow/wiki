---
description: 'SavaPage : une solution libre de gestion des impressions'
icon: print
---

# Gestion d'impression

[SavaPage](https://www.savapage.org/) est une solution libre et open source de gestion centralisée des impressions (_Print Management_), distribuée sous licence AGPL. Contrairement à un simple serveur d'impression, qui se contente de transmettre les travaux aux imprimantes, SavaPage ajoute une couche de gestion entre les utilisateurs et l'infrastructure d'impression.

{% embed url="https://www.savapage.org/" %}

Il permet de centraliser les impressions, d'authentifier les utilisateurs et de gérer leurs droits. Il offre aussi des quotas, une comptabilisation, un portail Web et de l'impression sécurisée. Il est donc adapté aux environnements qui comptent beaucoup d'utilisateurs et d'imprimantes, comme les établissements scolaires, les universités, les bibliothèques, les collectivités ou les entreprises.

***

## Principe de fonctionnement

Dans une infrastructure classique, un poste envoie directement son travail vers une imprimante ou vers un serveur d'impression

```
Poste utilisateur > Serveur d'impression > Imprimante
```

Avec SavaPage, une couche supplémentaire est introduite :

```
Utilisateur > SavaPage > Imprimante
```

SavaPage s'occupe de la gestion du travail d'impression et de l'utilisateur. \
Cela permet de centraliser les règles d'impression indépendamment des postes clients.

***

## Authentification

SavaPage peut être intégré à un annuaire existant afin que les utilisateurs se connectent avec leur compte habituel. Il prend en charge les environnements basés sur `LDAP` et sur `Active Directory`.

```
Active Directory
       │
       │ authentification
       ▼
   SavaPage
       │
       ▼
   Impression
```

Dans une entreprise qui dispose déjà d'un Active Directory, les comptes existants peuvent ainsi être réutilisés directement pour l'impression :)

Cela évite de maintenir une base d'utilisateurs spécifique au système d'impression.

***

## Portail Web

Une des particularités de SavaPage est **son portail Web**. **L'utilisateur se connecte depuis son navigateur pour gérer ses impressions**. Dans certains scénarios, il n'est donc plus nécessaire d'installer et de configurer toutes les imprimantes sur chaque poste.

L'utilisateur peut déposer un document dans SavaPage, puis choisir les options d'impression avant de lancer le travail. Ce fonctionnement est pratique pour les ordinateurs portables, les postes personnels, les smartphones, les tablettes et plus généralement les environnements BYOD (_Bring Your Own Device_).

***

## Impression sécurisée

Dans une infrastructure classique, un document envoyé vers une imprimante est imprimé immédiatement. Il peut alors rester oublié dans le bac de sortie, être consulté par une autre personne ou partir vers la mauvaise imprimante.

SavaPage évite ce problème en conservant le document avant son impression effective :

```
Utilisateur
    │
    │ envoie le document
    ▼
 SavaPage
    │
    │ document en attente
    ▼
Utilisateur s'identifie
    │
    ▼
Impression libérée
    │
    ▼
  Imprimante
```

Le document n'est donc réellement imprimé qu'au moment où l'utilisateur le demande.

***

## Follow-Me

Le `Follow-Me Printing` pousse cette logique plus loin. Au lieu d'envoyer son document vers une imprimante déterminée à l'avance, l'utilisateur l'envoie dans une file d'attente centrale. \
Il peut ensuite se rendre sur n'importe quel équipement compatible pour le libérer.

```
PC salle 201
     │
     ▼
  SavaPage
     │
     │ document de Pierre
     ▼
File d'attente
   │       │
   │       │
   ▼       ▼
Copieur A  Copieur B
```

Ce fonctionnement améliore la confidentialité et limite les impressions oubliées ou lancées par erreur. Il permet aussi de se rabattre sur un autre copieur lorsqu'un équipement est en panne.

***

## Badge NFC

SavaPage peut également être utilisé avec des systèmes d'identification qui permettent de libérer une impression à proximité d'un équipement, notamment avec des badges NFC. \
Ce mode est particulièrement intéressant pour les documents confidentiels.

Le déroulement est le suivant :

```
1. L'utilisateur lance son impression
            │
            ▼
2. Le document reste dans SavaPage
            │
            ▼
3. L'utilisateur se rend au copieur
            │
            ▼
4. Il présente son badge
            │
            ▼
5. Le document est libéré
            │
            ▼
6. Le copieur imprime
```

***

## Quotas

SavaPage permet de comptabiliser les impressions et de suivre la consommation par utilisateur, par compte, par nombre de pages, par type d'impression ou par imprimante.\
\
Des quotas et des politiques d'impression peuvent ensuite être appliqués. Très pratique dans une entreprise, PME ou établissement public

Le but n'est pas nécessairement de facturer les utilisateurs. \
La comptabilisation sert aussi à suivre les consommations, repérer les équipements les plus sollicités, limiter les abus et évaluer le coût réel de l'impression.

***

## Comptes

Une impression ne doit pas obligatoirement être imputée à un seul utilisateur. SavaPage gère différentes logiques de comptes, ce qui est utile lorsqu'une impression doit être rattachée à une activité particulière. Le suivi des coûts s'en trouve amélioré lorsque plusieurs services ou projets utilisent la même infrastructure d'impression.

```
Technicien
   │
   ├── Compte personnel George Abitbol
   │
   ├── Projet "La Classe Américaine"
   │
   └── Administration
```

***

## Source

Un portail d'impression centralisé réduit la dépendance à l'installation locale d'une imprimante.\
\
Selon la configuration, SavaPage propose plusieurs moyens d'envoi : le navigateur, IPP, AirPrint, Android Print Service, le dépôt de documents ou l'envoi par courrier électronique. Cette approche peut s'avérer utile pour les appareils qui ne sont pas administrés directement par le service informatique

***

## Avantages / Inconvénients

SavaPage est une solution open-source qui peut être auto-hébergée :) , ce qui donne la maîtrise complète de l'infrastructure. Il s'intègre aux annuaires LDAP et Active Directory et propose une gestion centralisée avec une interface Web. Il apporte l'impression sécurisée, le Follow-Me Printing, les quotas et le suivi des impressions, et il prend en charge différents types de clients. Il constitue ainsi une alternative intéressante aux plateformes commerciales de gestion d'impression.

Pour autant, SavaPage ne supprime pas toute la complexité d'une infrastructure d'impression. \
Il faut d'abord **vérifier la compatibilité des imprimantes et des photocopieurs**, le comportement des pilotes et la prise en charge d'IPP. Les méthodes d'authentification disponibles sur les copieurs et les lecteurs de badges utilisés demandent la même vérification.

Il faut ensuite **valider l'intégration avec LDAP ou Active Directory**, le dimensionnement du serveur, les besoins de haute disponibilité et les procédures de sauvegarde. Les fonctions avancées de certains photocopieurs multifonctions peuvent dépendre du constructeur ou d'une intégration spécifique. Un test avec les modèles réellement présents dans une entreprise reste donc indispensable avant un déploiement à grande échelle.

***

## SavaPage vs PaperCut

Dans son principe, `SavaPage` peut être rapproché de solutions commerciales telles que `PaperCut`. Les deux répondent à des besoins similaires : identification des utilisateurs, contrôle des impressions, suivi des consommations, quotas, impression sécurisée et impression depuis différents équipements.

SavaPage se distingue par sa philosophie : c'est une solution libre qui peut être auto-hébergée.\
Il mérite d'être étudié lorsque l'on recherche une solution libre, la maîtrise de l'hébergement et l'utilisation de standards ouverts. À l'inverse, une infrastructure qui s'appuie sur des fonctions très spécifiques intégrées aux photocopieurs devra vérifier soigneusement leur prise en charge avant d'envisager le remplacement d'une solution commerciale existante.

***

## Bonus

**OpenPrinting et CUPS**

SavaPage s'inscrit dans l'écosystème des technologies d'impression libres.\
[OpenPrinting](https://openprinting.github.io/) développe et maintient plusieurs briques utilisées pour l'impression sous GNU/Linux, dont [CUPS](https://openprinting.github.io/cups/) (_Common UNIX Printing System_). Le projet travaille aussi autour des standards modernes comme IPP, IPPS et IPP Everywhere, ainsi que de l'impression sans pilote (_driverless printing_) et des Printer Applications. L'objectif est de réduire progressivement la dépendance aux pilotes spécifiques de chaque constructeur.

```
OpenPrinting / CUPS
        │
        │ infrastructure d'impression
        ▼
     SavaPage
        │
        │ gestion de l'utilisation
        ▼
    Utilisateurs
```

CUPS est le système d'impression libre utilisé notamment sous GNU/Linux.\
Il gère les files d'impression, les imprimantes, les travaux et les protocoles d'impression, alors que SavaPage intervient à un niveau supérieur : celui de la gestion des utilisateurs et de leurs impressions (authentification, quotas, comptabilisation, impression sécurisée, Follow-Me, libération par badge).

OpenPrinting et SavaPage ne sont donc pas concurrents : ils sont complémentaires. OpenPrinting et CUPS fournissent l'infrastructure d'impression, et SavaPage gère l'utilisation qui en est faite.
