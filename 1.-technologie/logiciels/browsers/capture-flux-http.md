---
icon: globe-pointer
---

# Capture flux HTTP

Capturer le flux HTTP consiste à **enregistrer l'ensemble du trafic HTTP** échangé entre le poste utilisateur et un serveur web lors de l'exécution d'une action sur le site : ouverture d'une page, exécution d'une requête, validation d'un formulaire, chargement progressif de données lors du défilement d'une page, téléchargement d'un fichier…

Ces informations sont souvent indispensables à différents Support technique (web) pour réaliser un **diagnostic précis** en cas de **lenteurs** sur votre environnement&#x20;

{% hint style="info" %}
### Avant d'exécuter la procédure de capture du flux HTTP, assurez-vous d'être dans les conditions exactes du problème : utilisez le poste concerné, avec le même navigateur sur lequel vous constater le problème <a href="#bonnes-pratiques" id="bonnes-pratiques"></a>
{% endhint %}

***

Extension Chrome

{% embed url="https://chromewebstore.google.com/detail/har-recorder/emfabjnfjiknifjlfpjobbecfepplhkd" %}

***

### Google Chrome <a href="#navigateur-chrome" id="navigateur-chrome"></a>

* Connectez vous sur le site avec votre compte concerné par le problème.
* Lancez l'outil de capture du trafic HTTP : `<`**`F12`**`>`
* Allez sur l'onglet **Réseau**.
* Cochez la case **Preserve log** pour conserver l'historique des requêtes au cours de la navigation.
* Lancez l'enregistrement via 🔴
* Reproduisez le problème en effectuant toutes les étapes depuis le début

{% hint style="warning" %}
N'effectuez pas simplement un rafraîchissement de l'écran.
{% endhint %}

* Arrêtez l'enregistrement via ⚪

Une nouvelle ligne correspondant à la capture du trafic HTTP est ajoutée au tableau.

Enregistrez le fichier de résultats.

* Cliquez droit sur la ligne correspondant à la capture du trafic HTTP.
* Sélectionnez l'option _`Save as HAR with content`_ dans le menu contextuel.

Le fichier de résultats est sauvegardé au format `.har`

***

### Mozilla Firefox

* Connectez vous sur le site avec votre compte concerné par le problème.
* Lancez l'outil de capture du trafic HTTP : `<`**`F12`**`>` ou menu _Outils > Développement web > Réseau_.
* Allez sur l'onglet **Réseau**.
* Cochez la case **Conserver les journaux** pour conserver l'historique des requêtes au cours de la navigation.
* Lancez l'enregistrement via ⏸️

Reproduisez le problème en effectuant toutes les étapes depuis le débu

{% hint style="warning" %}
N'effectuez pas simplement un rafraîchissement de l'écran.
{% endhint %}

* Arrêtez l'enregistrement via ▶️
* Une nouvelle ligne correspondant à la capture du trafic HTTP est ajoutée au tableau.

Enregistrez le fichier de résultats.

* Cliquez droit sur la ligne correspondant à la capture du trafic HTTP.
* Sélectionnez l'option _`Tout enregistrer en tant que HAR`_ dans le menu contextuel.

Le fichier de résultats est sauvegardé au format `.har`
