---
description: 'Les switchs PoE : principe, normes, câblage et cas d''usage'
icon: network-wired
---

# Switchs PoE

Un switch PoE (_Power over Ethernet_) remplit le même rôle qu'un switch réseau classique, avec une fonction en plus : il **fournit l'alimentation électrique dans le câble RJ45**, en même temps que les données. Un seul câble suffit donc pour raccorder et alimenter une borne Wi-Fi, une caméra IP ou un téléphone IP.

Cet article présente le fonctionnement du PoE, les différentes normes, les appareils concernés, le câblage nécessaire, les pièges à éviter, le coût et la place du PoE par rapport aux switchs optiques.

***

### Principe de fonctionnement

Le PoE fait intervenir deux types d'équipements :

* le **PSE** (_Power Sourcing Equipment_) : l'équipement qui fournit le courant, en général le switch ;
* le **PD** (_Powered Device_) : l'appareil alimenté (borne Wi-Fi, caméra, téléphone…).

Le courant continu circule dans le même câble que les données, jusqu'à **100 mètres**. Avant d'envoyer du courant, le switch **vérifie que l'appareil est compatible PoE** et lui attribue une classe de puissance. Un appareil non PoE, comme un PC, peut donc être branché sans risque sur un port PoE : il ne recevra pas de courant.

***

### Les normes : PoE, PoE+ et PoE++

Les normes se distinguent surtout par la **puissance disponible par port**.

|                                | **PoE**                                     | **PoE+**                                              | **PoE++ Type 3**                         | **PoE++ Type 4**                                    |
| ------------------------------ | ------------------------------------------- | ----------------------------------------------------- | ---------------------------------------- | --------------------------------------------------- |
| Norme IEEE                     | 802.3af                                     | 802.3at                                               | 802.3bt                                  | 802.3bt                                             |
| Année                          | 2003                                        | 2009                                                  | 2018                                     | 2018                                                |
| Puissance max. côté switch     | 15,4 W                                      | 30 W                                                  | 60 W                                     | 90 W                                                |
| Puissance reçue par l'appareil | \~13 W                                      | 25,5 W                                                | 51 W                                     | 71,3 W                                              |
| Paires du câble utilisées      | 2                                           | 2                                                     | 4                                        | 4                                                   |
| Usages typiques                | Téléphone IP, caméra fixe, lecteur de badge | Borne Wi-Fi, caméra avec infrarouge, interphone vidéo | Caméra motorisée (PTZ), borne Wi-Fi 6E/7 | PTZ chauffée, écran, caméra multicapteur, éclairage |

#### Points à retenir

* **Les normes sont rétrocompatibles.** Un switch PoE++ alimente sans problème un appareil PoE ou PoE+. L'inverse ne fonctionne pas : un appareil PoE+ branché sur un port PoE ne démarre pas, ou fonctionne en mode dégradé.
* **L'appareil reçoit moins que ce que le switch envoie**, car une partie de la puissance se perd dans le câble.
* **Le PoE++ utilise les 4 paires du câble**, ce qui lui permet de monter en puissance.
* **« PoE++ » n'est pas un nom officiel.** C'est une appellation commerciale ; certains fabricants parlent aussi de « Hi-PoE » ou « UPoE ». Sur une fiche technique, il faut vérifier la **norme (802.3bt)** et le **type (3 ou 4)**.
* **Le PoE passif (24 V ou 48 V) ne fait partie d'aucune norme IEEE.** Le courant est envoyé sans vérifier l'appareil branché, ce qui peut l'endommager. On le trouve encore sur certains anciens équipements.

***

### Appareils nécessitant PoE++

Le PoE++ n'est nécessaire que pour les appareils qui consomment **plus de 25,5 W**, c'est-à-dire au-delà de ce que le PoE+ peut fournir.

| Famille                           | Exemples                                                          | Pourquoi ils ont besoin de PoE++                         | Type habituel                  |
| --------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------- | ------------------------------ |
| Caméras PTZ                       | Dômes motorisés, caméras extérieures avec chauffage ou dégivrage  | Moteurs, infrarouge longue portée, résistance chauffante | Type 3, ou Type 4 si chauffées |
| Caméras multicapteurs / IA        | Caméras panoramiques, analyse vidéo embarquée                     | Plusieurs capteurs et calcul local                       | Type 3                         |
| Bornes Wi-Fi haut de gamme        | Wi-Fi 6E / 7 tri-bande, 4×4 MIMO, uplink 5 ou 10 Gb/s             | Plusieurs radios en parallèle, puce plus gourmande       | Type 3                         |
| Écrans et terminaux               | Affichage dynamique, bornes interactives, clients légers, mini-PC | Dalle et rétroéclairage, ou un vrai PC à alimenter       | Type 3 ou Type 4               |
| Visioconférence                   | Barres de visio, systèmes tout-en-un pour salles de réunion       | Caméra, haut-parleurs et calcul embarqué                 | Type 3 ou Type 4               |
| Éclairage et bâtiment intelligent | Luminaires LED PoE, capteurs, stores motorisés                    | Une partie des luminaires dépasse 30 W                   | Type 3 ou Type 4               |
| Équipements réseau en cascade     | Mini-switchs alimentés en PoE qui redistribuent du PoE            | Le switch en aval doit alimenter ses propres appareils   | Type 4                         |

#### À vérifier avant l'achat

* **La consommation maximale et la classe PoE demandée** par l'appareil : classes 5–6 pour le Type 3, classes 7–8 pour le Type 4.
* **Le fonctionnement en mode dégradé.** Beaucoup de bornes Wi-Fi démarrent en PoE+, mais elles coupent alors une radio, limitent le MIMO ou désactivent le port USB.
* **Le cas des PTZ chauffées.** Elles fonctionnent souvent sans problème en été en PoE+, puis redémarrent en boucle au premier froid, quand le chauffage s'active.

Les téléphones IP, les caméras fixes classiques, les lecteurs de badge et la plupart des bornes Wi-Fi 5 / Wi-Fi 6 standard se contentent du PoE ou du PoE+.

***

### Câblage selon norme PoE

Pour **toutes les normes PoE**, le minimum est un câble **Cat5e en cuivre plein**, sur **100 m au maximum**. Plus la puissance augmente, plus la qualité du câble compte, à cause de **l'échauffement** et des **pertes**.

|                                      | **PoE**      | **PoE+** | **PoE++ Type 3** | **PoE++ Type 4** |
| ------------------------------------ | ------------ | -------- | ---------------- | ---------------- |
| Câble minimum                        | Cat5e        | Cat5e    | Cat5e            | Cat5e (à éviter) |
| Câble recommandé                     | Cat5e / Cat6 | Cat6     | Cat6 / Cat6A     | **Cat6A**        |
| Échauffement dans les gros faisceaux | Négligeable  | Faible   | Sensible         | Important        |
| Distance max.                        | 100 m        | 100 m    | 100 m            | 100 m            |

#### Critères importants

* **Cuivre plein obligatoire.** Les câbles en aluminium cuivré (CCA) sont à proscrire : plus résistants, ils chauffent, font chuter la tension et peuvent faire échouer la négociation PoE. On les trouve souvent dans les câbles « Cat6 » bon marché.
* **Section des conducteurs.** Un fil plus gros (AWG 23) chauffe moins qu'un fil plus fin (AWG 24 ou 26). Les cordons de brassage très fins sont à éviter sur les ports PoE++.
* **Chute de tension.** Sur les liaisons longues, l'appareil peut ne plus recevoir assez de tension pour fonctionner correctement.
* **Gros faisceaux de câbles.** Quand de nombreux câbles PoE++ passent ensemble dans un chemin de câbles ou une gaine, la chaleur s'accumule. Il vaut mieux limiter la taille des faisceaux et préférer du Cat6A, de préférence blindé.
* **Connecteurs RJ45.** À forte puissance, débrancher un câble sous tension crée un petit arc électrique sur les contacts. Il faut des connecteurs et des prises de qualité, conformes au PoE.

#### En pratique

* **Câblage existant en Cat5e** : il convient pour le PoE et le PoE+, et pour quelques ports PoE++ si les liaisons sont courtes et le câble de qualité.
* **Nouvelle installation** : **Cat6A en cuivre plein**. Ce câble supporte le PoE++ Type 4 et le 10 Gb/s, ce qui évite de recâbler plus tard.

***

### Avantages du PoE

* **Un seul câble** pour les données et l'alimentation : pas besoin de faire tirer du 230 V jusqu'au plafond ou en façade.
* **Alimentation centralisée** : un seul onduleur dans la baie suffit pour secourir les bornes Wi-Fi, les téléphones et les caméras.
* **Redémarrage à distance** : couper puis réactiver un port suffit pour redémarrer un appareil bloqué.
* **Moins d'adaptateurs secteur** et une maintenance simplifiée.

***

### Problèmes et pièges

* **Le budget PoE total n'est pas égal au nombre de ports multiplié par la puissance maximale.** Un switch vendu « 24 ports PoE+ » ne peut pas forcément fournir 30 W sur les 24 ports en même temps. Si le budget est dépassé, certains ports sont coupés ou limités, parfois sans alerte visible. Il est recommandé de garder **au moins 20 % de marge**.
* **Des pannes qui ressemblent à autre chose** : caméras qui redémarrent la nuit (quand l'infrarouge s'allume), bornes Wi-Fi qui décrochent. La cause est souvent un switch sous-dimensionné, pas l'appareil.
* **Le switch devient un point de panne unique** : s'il tombe, les données et l'alimentation tombent ensemble.
* **Chaleur, bruit et consommation** : le bloc d'alimentation est plus gros et les ventilateurs souvent plus bruyants.
* **Compatibilité** : les appareils en PoE passif ne fonctionnent pas sur un switch conforme aux normes IEEE.

***

### Coût par rapport à un switch standard

Un switch standard coûte en général **environ 30 à 40 % de moins** qu'un switch PoE de même débit. Le surcoût dépend surtout :

* de la **norme** : le PoE++ est nettement plus cher que le PoE+ ;
* du **budget total en watts** : les constructeurs proposent souvent le même modèle avec des blocs d'alimentation de puissances différentes ;
* des **blocs d'alimentation doublés** si on a besoin de redondance.

Pour une comparaison complète, il faut aussi compter ce que le PoE permet d'éviter : prises électriques à créer, adaptateurs secteur, intervention d'un électricien. Dès que les appareils sont en hauteur ou à l'extérieur, le PoE revient souvent moins cher au total.

***

### Quand privilégier un switch PoE ?

| Switch PoE recommandé                                               | Switch standard suffisant                            |
| ------------------------------------------------------------------- | ---------------------------------------------------- |
| Bornes Wi-Fi au plafond                                             | Postes fixes, imprimantes, NAS                       |
| Caméras IP, interphones, contrôle d'accès                           | Salles serveurs, cœur de réseau                      |
| Téléphonie IP                                                       | Sites où chaque poste a déjà une prise électrique    |
| Capteurs, objets connectés, bâtiment intelligent                    | Budget serré, aucun appareil PoE prévu               |
| Besoin de redémarrage à distance ou de secours par onduleur central | Bureaux où le bruit compte (switch sans ventilateur) |

En pratique, on choisit du **PoE+ pour les switchs d'accès** (étage, salle, couloir) dès qu'il y a du Wi-Fi ou de la téléphonie IP. On réserve le **PoE++** aux ports qui alimentent des appareils gourmands. Une solution courante consiste à mélanger les deux : des switchs PoE pour les bornes Wi-Fi, caméras et téléphones, et des switchs classiques pour les postes de travail.

***

### Le PoE va-t-il devenir un standard ?

En entreprise, au niveau des switchs d'accès, **le PoE est déjà presque devenu la norme**. Les bornes Wi-Fi 7, les caméras « intelligentes » et l'éclairage PoE demandent de plus en plus de puissance, ce qui pousse vers le PoE+ et le PoE++. Le 802.3bt est aujourd'hui courant dans les déploiements professionnels.

Pour les petites installations, à la maison ou dans une petite entreprise, le switch standard reste suffisant dans la plupart des cas.

***

### PoE et switchs optiques : deux rôles complémentaires

Les switchs PoE et les switchs optiques ne sont pas en concurrence, car **la fibre ne transporte pas de courant**. Ils s'utilisent à des endroits différents du réseau.

|                                     | Switch cuivre PoE                                     | Switch optique (SFP/SFP+/QSFP)                             |
| ----------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------- |
| Rôle                                | Accès : raccorder et alimenter les appareils          | Liens montants, liaisons entre bâtiments, cœur de réseau   |
| Distance                            | 100 m max                                             | De quelques centaines de mètres à plusieurs dizaines de km |
| Alimentation des appareils          | Oui                                                   | Non                                                        |
| Immunité électromagnétique / foudre | Faible                                                | Totale (isolation électrique)                              |
| Débit                               | 1 Gb/s ; 2,5 à 10 Gb/s pour les bornes Wi-Fi récentes | 10 à 100 Gb/s et plus                                      |
| Coût                                | Switch plus cher, câble bon marché                    | Modules optiques et raccordement à prévoir                 |

#### L'architecture type

L'architecture la plus répandue combine les deux :

* une **dorsale en fibre** entre le cœur de réseau et les baies d'étage ou de bâtiment ;
* des **switchs PoE dans chaque baie**, avec un lien montant SFP vers le cœur et des ports PoE pour les bornes Wi-Fi, téléphones et caméras.

Il existe aussi l'approche **fibre jusqu'au bureau (FTTO)** : la fibre va jusqu'à de petits switchs installés dans les salles, qui fournissent le PoE localement. Ces petits switchs ont alors besoin d'une prise électrique sur place.

***

### Conclusion

Le PoE simplifie le déploiement des équipements réseau en regroupant les données et l'alimentation dans un seul câble. Son intérêt est évident pour le Wi-Fi, la vidéoprotection et la téléphonie IP. Il demande en revanche de bien dimensionner le budget de puissance et de soigner le câblage, surtout en PoE++. Avec la fibre, il forme le schéma classique des réseaux d'entreprise : **la fibre pour le transport, le PoE pour l'accès et l'alimentation**.Les switchs PoE : principe, normes, câblage et cas d'usage
