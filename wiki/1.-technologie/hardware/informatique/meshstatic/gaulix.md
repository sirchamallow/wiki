# 🇫🇷 Gaulix

## Gaulix (France)

{% embed url="https://gaulix.fr/docs-parametrage/" %}

Gaulix est un regroupement de passionnés autour de la création d’un réseau de communication ouvert. Cela inclue des profils très différents : du geek au radio-amateur en passant par l’électronicien, l’informaticien et le simple curieux. Ces différentes compétences se complètent afin que chacun puisse apporter sa brique dans la construction de ce maillage. Par ailleurs une association est en cours de création pour fédérer ces profils et unifier la communauté.

***

## Paramétrage Meshtastic <a href="#meshtastic" id="meshtastic"></a>

{% embed url="https://gaulix.fr/docs-parametrage/regle-de-nommage-meshtastic-formatage-des-noms-longs/" %}

{% embed url="https://gaulix.fr/docs-parametrage/nous-nutilisons-pas-les-reglages-par-defaut/" %}

{% embed url="https://gaulix.fr/docs-parametrage/parametrage-rapide-flash-reglages-ajout-de-canaux-via-qr-code/" %}

{% embed url="https://gaulix.fr/docs-parametrage/lintegralite-des-parametres-meshtastic-expliques/" %}

{% embed url="https://gaulix.fr/docs-parametrage/choix-du-role-dans-meshtastic/" %}

***

{% hint style="info" %}
La configuration ci dessus est extrait de la page [_110- MQTT Config V_](https://gaulix.fr/1100-mqtt-config-v25x/) _._ Ce n'est qu'une version plus lisible et compréhensible pour le plus grand nombre que je publie icie.
{% endhint %}

***

## MQTT Configuration

Config (Meshtastic 2.5.x), configuration pour le réseau Gaulix.

Le module MQTT permet à votre nœud de servir de **passerelle** (gateway). S'il est connecté à Internet en Wi-Fi ou en Ethernet, il transfère les paquets vers un serveur MQTT. Les utilisateurs de votre maillage local peuvent alors échanger avec ceux d'un autre maillage via Internet.

{% hint style="info" %}
Vous pouvez ignorer cette partie si vous ne souhaitez pas utiliser votre nœud comme passerelle.
{% endhint %}

### Prérequis

* Un ou plusieurs canaux doivent être activés en **liaison montante (uplink)** et/ou **descendante (downlink)** pour que les paquets circulent depuis et/ou vers votre maillage (voir la section Canaux).
* Sans ces réglages, le nœud se connecte quand même au serveur MQTT, mais il n'envoie que des messages d'état.

### Bonnes pratiques

* Gaulix vise un réseau à l'échelle nationale. Il faut donc au moins un nœud passerelle pour la « bulle » locale que vous constituez. C'est ce qui permet à un message émis depuis votre zone d'atteindre toute la France.
* **Ne multipliez pas les passerelles pour une même bulle**, car cela provoque des répétitions de messages.

### Paramètres

| Paramètre                   | Rôle                                                               | Valeur par défaut            | Valeur Gaulix                                     |
| --------------------------- | ------------------------------------------------------------------ | ---------------------------- | ------------------------------------------------- |
| **MQTT enabled**            | Active/désactive le module MQTT du nœud                            | –                            | `Enabled`, **uniquement** pour un nœud passerelle |
| **Address**                 | Adresse du serveur MQTT, sans le préfixe `mqtt://` (implicite)     | `mqtt.meshtastic.org`        | `mqtt.gaulix.fr`                                  |
| **Username**                | Nom d'utilisateur de connexion au serveur MQTT                     | `meshdev`                    | Identifiant du site Gaulix.fr                     |
| **Password**                | Mot de passe de connexion au serveur MQTT                          | `large4cats`                 | Mot de passe du site Gaulix.fr                    |
| **Encryption enabled**      | Chiffrement des données MQTT                                       | `Enabled`                    | `Disabled`                                        |
| **JSON output enabled**     | Module JSON pour la communication MQTT                             | `Disabled`                   | `Disabled`                                        |
| **TLS enabled**             | Connexion chiffrée avec le serveur MQTT (partie réseau uniquement) | `Disabled`                   | `Disabled`                                        |
| **Root topic**              | Topic racine de publication sur le serveur MQTT                    | Laisser la valeur par défaut | `msh/EU_868`                                      |
| **Proxy to client enabled** | Le nœud passe par l'application mobile pour accéder à Internet     | –                            | Voir ci-dessous                                   |
| **Map reporting**           | Envoi périodique d'un rapport de carte non chiffré (v2.3.2+)       |  –                           | `Enabled`, **uniquement** pour la passerelle      |
| **Precise location**        | Précision de la position dans le rapport de carte                  | ≈ 1459 m d'écart max.        | Non précisé                                       |
| **Map reporting interval**  | Fréquence d'envoi du rapport, en secondes                          | `900`                        | `900`                                             |

### Détail des paramètres

* **MQTT enabled :** Active ou désactive le module MQTT. Pour Gaulix, activez-le uniquement sur le nœud qui joue le rôle de passerelle.
* **Address, Username et Password :** Saisissez l'adresse sans `mqtt://`. Pour Gaulix, utilisez `mqtt.gaulix.fr`, avec les identifiants de votre compte sur Gaulix.fr.
* **Encryption enabled :** Sur Gaulix, cette option est à `Disabled`. Quand elle n'est pas activée, tous les messages sont envoyés au broker MQTT **en clair**, même si vos canaux de liaison montante ont des clés de chiffrement définies.
* **JSON output enabled** : Ce module publie les paquets au format JSON. Ils ne sont pas chiffrés, mais s'intègrent facilement à des systèmes capables de lire du JSON. Il charge davantage le nœud et n'est **pas pris en charge sur la plateforme nRF52**. Sur Gaulix, laissez-le à `Disabled`.
* **TLS enabled** : Active le chiffrement de la connexion avec le serveur MQTT. Cela ne concerne que la partie réseau. Sur Gaulix, laissez-le à `Disabled`.
* **Root topic** : Laissez la valeur par défaut. Sur Gaulix, le topic est `msh/EU_868`, quelle que soit la bande utilisée par le nœud. Cela permet un **crossband** (passage d'une bande à une autre) via le serveur MQTT.
* **Proxy to client enabled : `Enabled`** : le nœud se connecte au serveur MQTT via l'application en Bluetooth. Il utilise la connexion Internet de l'appareil connecté (par exemple votre téléphone). // **`Disabled`** : le nœud utilise son propre point d'accès Wi-Fi, que vous devez configurer dans les paramètres réseau. **Il faut désactiver cette option si le Wi-Fi de la carte est activé.**
* **Map reporting** : Disponible à partir de la version **2.3.2** du micrologiciel. Si l'option est sur `Enabled`, votre nœud envoie périodiquement un **rapport de carte non chiffré** au serveur MQTT. Ce rapport est affiché par les cartes en ligne qui prennent en charge ce paquet.
* **Réseau Gaulix :** `Enabled`, **uniquement pour votre passerelle**. Sur les autres nœuds, ce réglage n'a pas d'importance.
* **Precise location :** Définit la précision de la position transmise dans le rapport de carte. Par défaut, l'écart maximal est d'environ **1459 m**. || **`Enabled`** : la position GPS exacte est transmise. // **`Disabled`** : la position du nœud est représentée dans un cercle. Un curseur apparaît alors pour définir le rayon maximum de ce cercle.
* **Map reporting interval (seconds) :** Fréquence de publication du rapport de carte sur le serveur MQTT, en secondes. `900` (soit 15 minutes) identique au réglage de base.

### Informations

{% hint style="info" %}
Le réseau Gaulix utilise **son propre serveur MQTT**. Cela permet de le modifier et de l'ajuster en permanence pour garantir un fonctionnement optimal aux utilisateurs.

L'équipe analyse son utilisation en continu. Malgré les précautions prises, des erreurs de paramétrage ou des pannes peuvent survenir et entraîner une saturation rapide.
{% endhint %}

### Compte Gaulix

Au moment de la rédaction de cette documentation, chaque utilisateur doit créer un compte sur le site [gaulix.fr](https://gaulix.fr) pour obtenir ses identifiants de connexion.

* Les identifiants se composent d'un **nom d'utilisateur** et d'un **mot de passe**.
* Ils sont **uniques à chaque utilisateur** et valables pour **tous les équipements** qu'il administre.
* Pour se connecter au serveur MQTT Gaulix, il faut utiliser **les mêmes identifiants que ceux du site**.

Cette démarche n'a rien à voir avec un contrôle des utilisateurs. L'objectif est de disposer d'une **adresse e-mail fiable** pour vous contacter rapidement en cas de problème avec votre matériel, afin que vous puissiez intervenir et rétablir le bon fonctionnement de votre réseau.

Par transparence, ce système permet aussi de **suspendre un accès** dans les rares cas où les corrections nécessaires ne seraient pas effectuées. Cela préserve la qualité d'utilisation pour tous les membres de la communauté.

{% hint style="warning" %}
⚠️ Les comptes non identifiés peuvent être **bannis sans préavis**, puisque l'utilisateur est alors injoignable en cas de problème sur le serveur MQTT
{% endhint %}

#### Créer vos identifiants

1. Rendez-vous sur le site [gaulix.fr](https://gaulix.fr).
2. Si vous êtes nouveau sur Gaulix, **créez un compte**, puis identifiez-vous.
3. Utilisez ces mêmes identifiants (nom d'utilisateur et mot de passe) dans les paramètres `Username` et `Password` du module MQTT.
