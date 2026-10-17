---
description: L'intelligence cachée des adaptateurs Apple
icon: battery-bolt
---

# Chargeur Apple

En lisant un [article du site francophone MacGeneration](https://www.macg.co/materiel/2025/11/magic-keyboard-trackpad-chargeur-140-w-une-vague-de-mises-jour-firmware-chez-apple-305067), j'apprends qu'Apple déploie une **mise à jour du firmware** de son **adaptateur secteur USB-C 140 W** (de la version 1.4.73 à la 1.4.84). Ma première réaction : une mise à jour de firmware… pour un chargeur ? J'ai donc creusé le sujet.

Sous cette annonce qui peut sembler anecdotique se cache une évolution majeure dans la conception des accessoires d'alimentation. Comme nos smartphones, les chargeurs modernes sont devenus de véritables ordinateurs miniatures, dotés de microcontrôleurs sophistiqués et d'un firmware évolutif (encore faut-il que le constructeur l'exploite).

### Comment ça marche ?

Pour comprendre, il faut d'abord regarder du côté du standard USB, puis de la façon dont Apple utilise le mode DFU, et enfin de ce que contient réellement un chargeur.

#### USB Power Delivery : un protocole qui négocie

Le standard **USB Power Delivery (USB PD)** repose sur un canal de communication dédié entre le chargeur et l'appareil, qui passe par le fil **CC (Configuration Channel)** du câble USB-C.

Adopté par l'**USB Implementers Forum (USB-IF)** en 2012 et régulièrement mis à jour, l'USB PD a révolutionné la charge des appareils électroniques. Là où les anciennes technologies délivraient une tension fixe, il établit une **négociation bidirectionnelle entre la source d'alimentation et l'appareil**.

Selon les spécifications de l'USB-IF, cette communication permet de :

* Négocier dynamiquement la puissance délivrée (jusqu'à 240 W avec l'USB PD 3.1 EPR)
* Adapter la tension et le courant en temps réel
* Inverser le sens du flux d'énergie (un ordinateur portable peut par exemple alimenter un écran externe)
* Echanger des informations de diagnostic et de sécurité.

Cette intelligence distribuée nécessite du code embarqué, donc un firmware susceptible d'évoluer.

#### DFU : une mise à jour standardisée

Le mode **USB DFU (Device Firmware Upgrade)** est un protocole standard qui permet de mettre à jour le firmware d'un périphérique via son interface USB. Il est défini dans la spécification [USB Device Class Specification for Device Firmware Upgrade, version 1.1](http://www.usb.org/developers/devclass_docs/DFU_1.1.pdf) et évite le recours à des pilotes propriétaires.

Le périphérique expose une classe USB dédiée (la _DFU Class_) qui permet à l'hôte de :

* Lire le firmware actuel
* Effacer la mémoire flash
* Télécharger un nouveau firmware
* Vérifier l'intégrité de la mise à jour

Ce mécanisme de bas niveau fonctionne indépendamment du système d'exploitation. Il peut même récupérer un périphérique dont le firmware principal est corrompu, car le bootloader DFU réside dans une zone mémoire protégée.

#### Le DFU chez Apple : de l'iPhone aux Mac

_MacGeneration_ rappelle d'ailleurs que _« le mode DFU est un héritage des appareils iOS qui est passé aux Mac avec la transition Apple Silicon »_. Comme sur iPhone ou iPad, ce mode bas niveau sert **en dernier recours** pour dépanner un Mac qui refuse de démarrer ou dont les fonctions de restauration ne sont plus disponibles.

Apple utilise le DFU de façon systématique depuis l'iPhone original, en 2007. Cette approche s'est révélée efficace pour maintenir un parc d'appareils complexes, y compris dans les cas de récupération les plus critiques.

> **À noter** : Apple ne documente pas publiquement le mécanisme exact utilisé pour mettre à jour ses chargeurs (DFU ou autre protocole). Cette section présente le principe général du DFU et son rôle dans l'écosystème Apple.

> **Bonus** : [Timothy Perfitt](https://about.me/tperfitt), développeur spécialisé dans la gestion de flottes iOS et macOS, a créé un petit utilitaire nommé [DFU Blaster](https://bitbucket.org/twocanoes/dfu-blaster-public/downloads/), qui fera gagner du temps aux gestionnaires de parcs de Mac Apple Silicon.

#### Sous le capot : le cerveau du chargeur

Selon le site spécialisé _ChargerLab_, les adaptateurs [67 W](https://www.chargerlab.com/latest-teardown-of-brand-new-apple-67w-usb-c-power-adapter/) et [140 W](https://www.chargerlab.com/teardown-of-brand-new-apple-140w-usb-c-gan-charger/) d'Apple embarquent tous deux le même contrôleur USB Type-C et Power Delivery : le [CYPD3135](https://www.infineon.com/cms/en/product/universal-serial-bus-usb-power-delivery-controller/usb-c-and-power-delivery/ez-pd-cch3-power-delivery-controllers/cypd3135-40lqxi/), d'Infineon Technologies (anciennement Cypress Semiconductor). D'après la documentation d'Infineon, ce composant intègre :

**Côté matériel**

* Un processeur `ARM Cortex-M0` cadencé à 48 MHz
* 128 Ko de mémoire flash pour le firmware
* Des circuits analogiques de détection et de protection
* Des PHY USB pour la communication sur les lignes CC

**Côté fonctionnalités**

* La gestion complète du protocole `USB PD 3.0`
* La détection automatique de l'orientation du câble
* La protection contre les surtensions, surintensités et surchauffes
* La prise en charge de profils de charge rapide propriétaires (Apple 2.4 A, Samsung AFC, Qualcomm Quick Charge)
* Des mécanismes de sécurité cryptographiques pour l'authentification des accessoires

Cette puissance de calcul est comparable à celle d'un microcontrôleur de système IoT :smile: . Il n'est donc pas si surprenant finalement que ces chargeurs puissent recevoir des mises à jour de firmware, comme n'importe quel objet connecté.

### Quels chargeurs Apple embarquent un contrôleur programmable ?

Les démontages de ChargerLab permettent de confirmer l'architecture de deux modèles :

<table><thead><tr><th width="109.078125">Adaptateur</th><th width="162.265625">Usage</th><th width="138.0625">Contrôleur</th></tr></thead><tbody><tr><td>67 W</td><td>MacBook Pro 13"</td><td>CYPD3135</td></tr><tr><td>140 W</td><td>MacBook Pro 16"</td><td>CYPD3135</td></tr></tbody></table>

Les autres adaptateurs USB-C d'Apple (20 W, 30 W, 35 W double port, 96 W) reposent très probablement sur une architecture comparable, mais leurs références exactes de contrôleurs ne sont pas détaillées dans les sources utilisées ici. La [page de support d'Apple](https://support.apple.com/en-us/HT201700) recense l'ensemble de la gamme. Le 140 W utilise par ailleurs la technologie **`GaN`** (nitrure de gallium) pour la conversion de puissance, associée au contrôleur Infineon pour la gestion intelligente de la charge. Pour en savoir plus sur le `GaN`, le [billet de blog de Belkin](https://www.belkin.com/fr/produits/ressources-produits/recharge-gan/) est une bonne lecture.

### Pourquoi mettre à jour un chargeur :thinking: ?

Apple ne détaille pas le contenu de chaque mise à jour. Voici, de façon générale, ce qu'un nouveau firmware peut apporter à ce type d'accessoire.

**Suivre l'évolution des standards :** L'USB PD évolue en permanence. La version 3.1, ratifiée en 2021, a introduit l'_Extended Power Range_ (EPR), qui permet d'aller jusqu'à 240 W. Une mise à jour peut ajouter de nouveaux profils de tension (28 V, 36 V, 48 V) et améliorer la compatibilité avec les spécifications les plus récentes.

**Améliorer l'efficacité énergétique :** Les réglementations sur l'efficacité énergétique des alimentations sont de plus en plus strictes. Un firmware plus abouti peut affiner la gestion de la conversion et réduire la consommation en veille.

**Corriger les bugs et renforcer la sécurité :** Comme tout logiciel embarqué, un firmware peut contenir des bugs, voire des failles de sécurité. Les contrôleurs USB-C et les implémentations du protocole USB PD ont déjà fait l'objet de travaux de recherche en sécurité. Pour un composant programmable, la mise à jour est le moyen de corriger ce type de problème sans changer le matériel.

**Étendre la compatibilité :** Chaque nouvel appareil Apple (iPhone 16 Pro Max, MacBook Pro M4, etc.) peut introduire de nouveaux profils de charge optimisés. Une mise à jour assure la compatibilité sans changer le matériel.

**Affiner la gestion thermique :** Les algorithmes de régulation thermique peuvent être ajustés pour réduire la température de fonctionnement, ce qui prolonge la durée de vie des composants et améliore la sécurité.

### Et côté Apple, comment ça se passe ?

Apple ne publie pas de documentation détaillée sur la procédure de mise à jour de ses chargeurs.&#x20;

On peut en revanche retenir un point : contrairement à certains fabricants d'accessoires qui exigent une application dédiée, Apple a l'avantage de maîtriser à la fois le chargeur, le câble et le système d'exploitation du Mac. C'est ce qui rend possible, en théorie, une mise à jour discrète du chargeur.

Pour connaître les modalités exactes (déclenchement, durée, conditions), la référence sont les notes de version publiées par Apple.
