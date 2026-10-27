---
icon: poo
---

# Navigateur intégré

## Réseaux Sociaux

### Contexte

Quand on touche un lien dans X, Instagram, Facebook, Snapchat, LinkedIn ou TikTok, il s'ouvre par défaut dans le **navigateur intégré** de l'application et non dans Chrome ou Safari. Ce navigateur intégré est une simple « vue web » embarquée dans l'application. Ce n'est pas votre vrai navigateur.

Selon l'application, on peut le **désactiver une fois pour toutes**, ou seulement **lien par lien**.

### Pourquoi le désactiver ?

#### Confidentialité et sécurité

* **Suivi de l'activité** : l'éditeur de l'application voit ce que vous consultez et peut l'utiliser pour alimenter son algorithme. Pour Facebook, c'est même l'un des principaux intérêts du navigateur interne.
* **Injection de code** : Facebook et Instagram (Meta) ont été pris en train d'injecter du JavaScript dans les pages ouvertes. Cela leur permet d'observer les saisies dans les formulaires, les zones touchées et les textes sélectionnés, y compris sur des sites qui ne leur appartiennent pas.
* **Pas de contrôle** : les protections de votre navigateur (navigation privée, réglages de confidentialité, bloqueurs de publicités) ne s'appliquent pas.
* **Faux sentiment de sécurité** : on saisit des identifiants ou des données bancaires dans une fenêtre dont on ne voit pas toujours l'adresse complète ni le cadenas, et qui n'est pas le navigateur de confiance.

#### Fonctionnalités perdues

* **Déconnexion systématique** : le navigateur intégré ne partage pas vos sessions. Sur un site où vous êtes habituellement connecté, il faut se reconnecter.
* **Mots de passe, cartes et passkeys indisponibles** : le gestionnaire de mots de passe (Bitwarden, Proton Pass, 1Password…), le remplissage automatique et les moyens de paiement enregistrés ne suivent pas. Un paiement en ligne ou un accès à un compte devient pénible.
* **Pas d'extensions ni de bloqueur de publicités.**
* **Partage limité** : selon l'application, il est difficile de copier le lien, de l'envoyer par SMS ou par e-mail, de l'imprimer ou de l'enregistrer.
* **Liens « Ouvrir dans l'application » inopérants** : un lien YouTube, Spotify ou Amazon reste coincé dans le navigateur intégré au lieu d'ouvrir l'application native.

#### Confort d'utilisation

* **Pas d'historique** : impossible de retrouver plus tard un lien consulté, car il n'apparaît pas dans l'historique de Chrome ou Safari.
* **Interface réduite** : peu d'onglets, peu de commandes, et un comportement parfois capricieux ou bogué.
* **Temps de lecture** : le temps passé sur le site externe est comptabilisé comme du temps passé dans l'application.
* **Filtrage imposé** : par exemple, Snapchat vérifie les liens avec un service de filtrage de Google et affiche une alerte si le site est signalé, même à tort.

### Tableau récapitulatif

<table><thead><tr><th width="112">Application</th><th width="169">Android : désactivation globale</th><th width="200">iOS : désactivation globale</th><th>Solution lien par lien</th></tr></thead><tbody><tr><td>X (Twitter)</td><td>Oui</td><td>Selon la version (parfois absent)</td><td>Menu du lien → ouvrir dans le navigateur</td></tr><tr><td>Facebook</td><td>Oui (limitée)</td><td>Non</td><td>Menu ⋯ du lien → ouvrir dans le navigateur</td></tr><tr><td>LinkedIn</td><td>Oui (selon version)</td><td>Selon la version</td><td>Menu du lien → ouvrir dans le navigateur</td></tr><tr><td>Instagram</td><td>Non</td><td>Non</td><td>Menu ⋯ → ouvrir dans le navigateur</td></tr><tr><td>TikTok</td><td>Non</td><td>Non</td><td>Menu ••• → ouvrir dans le navigateur</td></tr><tr><td>Snapchat</td><td>Non</td><td>Non</td><td>Copier le lien puis le coller dans le navigateur</td></tr></tbody></table>

### Prérequis

* **Android** : définir son navigateur par défaut. _Paramètres → Applications → Applis par défaut → Appli de navigateur_.
* **iOS** : le navigateur par défaut se règle dans _Réglages → \[nom du navigateur] → App de navigation par défaut_. Safari est utilisé si rien n'a été changé.

{% hint style="info" %}
Les menus changent souvent d'une version à l'autre. En cas de doute, cherchez « navigateur » ou « liens » dans les paramètres de l'application.
{% endhint %}

### X (Twitter)

{% tabs %}
{% tab title="Android" %}
1. Touchez votre **photo de profil** (en haut à gauche).
2. **Paramètres et assistance** → **Paramètres et confidentialité**.
3. **Accessibilité, affichage et langues** → **Affichage et son**.
4. Désactivez **Utiliser le navigateur intégré à l'application**.
{% endtab %}

{% tab title="iOS" %}
Le chemin est le même (_Accessibilité, affichage et langues → Affichage et son_), mais l'option a été retirée de certaines versions de l'application.

Si elle est absente, ouvrez le lien puis utilisez le menu du navigateur intégré pour l'ouvrir dans Safari.
{% endtab %}
{% endtabs %}

### Facebook

{% tabs %}
{% tab title="Android" %}
1. Touchez le **menu** (☰ ou votre photo de profil, en haut à droite).
2. **Paramètres et confidentialité** → **Paramètres**.
3. Descendez jusqu'à **Contenu multimédia** (ou _Médias et contacts_).
4. Cochez **Ouvrir les liens dans un navigateur externe**.

{% hint style="warning" %}
Sur les versions récentes, ce réglage ne s'applique qu'aux liens reçus dans **Messenger / messages**. Les liens des publications et pages s'ouvrent toujours dans le navigateur intégré.
{% endhint %}
{% endtab %}

{% tab title="iOS" %}
Le réglage global n'est pas disponible. Pour chaque lien :

1. Touchez le lien, puis les **trois points ⋯** du navigateur intégré.
2. Choisissez **Ouvrir dans le navigateur du système** (Safari).
{% endtab %}
{% endtabs %}

### LinkedIn

Même procédure sur Android et iOS :

1. Touchez votre **photo de profil**.
2. **Paramètres** → **Préférences du compte**.
3. Désactivez **Ouvrir les liens web dans l'application**.

{% hint style="info" %}
L'option n'apparaît pas dans toutes les versions de l'application. Si elle est absente, ouvrez le lien puis utilisez le bouton « ouvrir dans le navigateur » du lecteur intégré.
{% endhint %}

### Instagram

{% hint style="warning" %}
Aucun réglage global disponible, sur Android comme sur iOS.
{% endhint %}

Pour chaque lien :

1. Touchez le lien (il s'ouvre dans le navigateur d'Instagram).
2. Touchez les **trois points** en haut à droite.
3. Choisissez **Ouvrir dans le navigateur**.

Alternative : appui long sur la barre d'adresse → **Copier le lien** → collez-le dans votre navigateur.

### TikTok

{% hint style="warning" %}
Aucun réglage global disponible, sur Android comme sur iOS.
{% endhint %}

Pour chaque lien :

1. Touchez le lien (navigateur intégré de TikTok).
2. Touchez **Plus d'options (•••)** en haut de la page.
3. Choisissez l'option pour **ouvrir dans le navigateur**. Le libellé varie selon la version : _Ouvrir dans le navigateur_, _Safari_, etc.

Si l'option n'existe pas : **Copier le lien**, puis collez-le dans Chrome ou Safari.

### Snapchat

{% hint style="warning" %}
Aucun réglage pour désactiver le navigateur intégré, sur Android comme sur iOS.
{% endhint %}

Le navigateur de Snapchat s'ouvre par-dessus la Story et propose peu de commandes. Si le menu du lien propose d'ouvrir dans le navigateur, utilisez-le. Sinon, copiez le lien et collez-le dans votre navigateur.

### À retenir

* Seuls **X, Facebook (liens des messages) et LinkedIn** proposent un réglage global, surtout sur Android.
* Sur **iOS**, il faut le plus souvent passer par le menu **⋯ / •••** de chaque lien.
* **Instagram, TikTok et Snapchat** n'ont aucun réglage : l'ouverture se fait manuellement, lien par lien.
