---
description: 'LocalSend, PeerDrop.online, Smash et SwissTransfer : comparatif'
icon: upload
---

# Envoi de Fichiers

### Introduction

Les messageries plafonnent les pièces jointes autour de 20 à 25 Mo, ce qui exclut les vidéos, les sauvegardes et les dossiers volumineux. Quatre outils répondent à ce besoin selon trois approches :

* **Pair à pair dans le navigateur** : PeerDrop.online
* **Réseau local** : LocalSend
* **Transfert hébergé par lien** : Smash et SwissTransfer

Cette fiche les compare sur le fonctionnement, la sécurité, la localisation des données et le caractère open source. Les informations proviennent des sites et de la documentation officiels des éditeurs. Ce qui n'a pas pu être confirmé est signalé comme « non annoncé ».

### Comparatif

| Nom                           |                                            PeerDrop&#xA;(navigateur)                                            |                       LocalSend &#xA;(local)                      |        Smash&#xA;(multizone)        |                                                                                     SwissTransfer&#xA;(Suisse)                                                                                    |
| ----------------------------- | :-------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------: | :---------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| **Principe**                  | Pair à pair (WebRTC) entre navigateurs ; connexion par détection à proximité, lien ou QR code, ou code de salle | Application sur réseau local (HTTPS) ; application web via WebRTC | Dépôt sur serveur, partage par lien |                                                                                Dépôt sur serveur, partage par lien                                                                                |
| **Installation**              |                                                    Navigateur                                                   |                            Application                            |              Navigateur             |                                                                                             Navigateur                                                                                            |
| **Limite de taille**          |                                                      Aucune                                                     |                               Aucune                              |   <p>Aucune<br>(plan gratuit)</p>   |                                                                                          50 Go par envoi                                                                                          |
| **Durée de disponibilité**    |                                                 (échange direct)                                                |                          (échange direct)                         |   Jusqu'à 14 jours (plan gratuit)   |                                                                              <p>De 1 à 30 jours<br>(plan gratuit)</p>                                                                             |
| **Chiffrement du transfert**  |                                    Chiffré (WebRTC), algorithme non détaillé                                    |              HTTPS (certificat généré par l'appareil)             |        TLS ; AES-256 au repos       |                                                                    <p>AES-GCM en transit ; <br>LUKS et AES-256 au stockage</p>                                                                    |
| **Localisation des serveurs** |                                            Aucun stockage de fichier                                            |                           Aucun serveur                           |      <p>9 régions<br>(AWS)</p>      |                                                                                   <p>Suisse<br>(Infomaniak)</p>                                                                                   |
| **Open source**               |                                                       Non                                                       |                              **Oui**                              |                 Non                 | **Partiel** (GPL-3.0 : [Android](https://github.com/Infomaniak/android-SwissTransfer) · [iOS](https://github.com/Infomaniak) · [cœur](https://github.com/Infomaniak/multiplatform-SwissTransfer)) |
| **Usage recommandé**          |                            Transfert ponctuel entre deux appareils, sans installation                           |            Appareils sur le même réseau, sans Internet            |    Très gros fichiers à distance    |                                                                                       Fichiers jusqu'à 50 Go                                                                                      |

**Précaution sur PeerDrop** : les informations de cette fiche ne concernent que **peerdrop.online**. Plusieurs autres services portent le même nom (peerdrop.io, peerdrop.app, peerdrop.co.in, peerdrop.dev etc.), avec des fonctionnalités et des promesses de sécurité différentes. C'est un terme quasiment générique. Soyez vigilants. PeerDrop.online est également un copycat, mais de bonne facture. Il faut plus le voir comme une interface

### Apparté : Thunderbird Send (ex-Firefox Send)

`Firefox Send`, développé par Mozilla, a longtemps été la référence de cette catégorie d'outils.

* **Chronologie** : ouvert le 1er août 2017 (programme Test Pilot), public le 12 mars 2019, suspendu le 7 juillet 2020, arrêté définitivement le 17 septembre 2020 après des abus (logiciels malveillants, hameçonnage).
* **Principe** : fichier chiffré dans le navigateur avant l'envoi (AES-GCM), avec une clé placée dans le lien après le `#` et donc jamais transmise à Mozilla. Limite de 1 Go sans compte, 2,5 Go avec un compte.
* **Code source** : licence MPL-2.0, dépôt [mozilla/send](https://github.com/mozilla/send) archivé depuis le 22 mai 2021.
* **Successeur** : Thunderbird Send, annoncé en juillet 2023 et intégré à l'offre Thundermail. Il annonce un chiffrement de bout en bout, des fichiers jusqu'à 20 Go et un code ouvert ; l'accès se fait par invitations (état de juin 2026). Un audit externe publié fin 2025 a relevé deux failles, corrigées, et 22 recommandations de durcissement.

Aucun des quatre outils comparés n'annonce ce modèle « clé dans le lien » avec un serveur d'hébergement.

### Bonnes pratiques

* **Données sensibles** : chiffrer les fichiers avant l'envoi et transmettre le mot de passe par un canal distinct (téléphone, SMS). La CNIL précise que les plateformes de dépôt grand public constituent rarement un moyen sûr sans mesure complémentaire, et recommande la suppression automatique des fichiers transmis.
* **Services hébergés** : activer le mot de passe et choisir la durée de disponibilité la plus courte possible.
* **LocalSend** : activer le PIN et utiliser l'outil sur un réseau maîtrisé.
* **Contexte professionnel** : vérifier que l'outil est autorisé par la politique de sécurité de l'organisation.
