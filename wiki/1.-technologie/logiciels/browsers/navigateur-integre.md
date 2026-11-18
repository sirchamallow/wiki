---
icon: poo
---

# Navigateur intégré

## Smartphones

Sur la plupart des smartphones, le constructeur définit son propre navigateur comme application par défaut. Chaque lien touché dans un SMS, un e-mail ou une notification s'ouvre alors dans ce navigateur. Cet article liste les principaux navigateurs constructeurs et explique comment les remplacer sur Android et iOS.

{% hint style="info" %}
Il n'existe pas de bouton « désactiver » universel. La méthode consiste à **définir un autre navigateur par défaut**. Sur certaines marques, on peut aussi désactiver l'application du constructeur.
{% endhint %}

### Navigateurs proposés par les constructeurs

<table><thead><tr><th width="99">Fabricant</th><th width="158">Navigateur intégré</th><th>Remarque</th></tr></thead><tbody><tr><td>Apple</td><td>Safari</td><td>Navigateur par défaut sur iPhone et iPad</td></tr><tr><td>Samsung</td><td>Samsung Internet</td><td>Navigateur par défaut sur les Galaxy</td></tr><tr><td>Xiaomi (Redmi, POCO)</td><td>Mi Browser (ou Mint Browser selon la ROM)</td><td>Souvent imposé par défaut, avec publicités et notifications</td></tr><tr><td>Huawei</td><td>Huawei Browser</td><td>Les liens externes dépendent du réglage système des applications par défaut</td></tr><tr><td>Vivo</td><td>Vivo Browser</td><td>Remplaçable depuis les applications par défaut</td></tr><tr><td>Google (Pixel)</td><td>Chrome</td><td>Navigateur d'origine de Google, préinstallé sur les Pixel</td></tr><tr><td>Oppo</td><td>Chrome</td><td>Chrome est défini par défaut sur les Oppo récents (ColorOS)</td></tr></tbody></table>

{% hint style="warning" %}
Les chemins de menu varient selon la marque, la version d'Android et la surcouche (One UI, HyperOS, ColorOS, etc.). Les libellés ci-dessous peuvent légèrement différer sur votre appareil.
{% endhint %}

### Prérequis

1. Installer le navigateur souhaité (Chrome, Firefox, Edge, Brave, etc.) depuis le Play Store ou l'App Store.
2. L'ouvrir **une fois** pour qu'il se déclare comme navigateur auprès du système. Sans cela, il peut ne pas apparaître dans la liste.

### Changer le navigateur par défaut

{% tabs %}
{% tab title="Google Pixel / Android" %}
1. Ouvrir **Paramètres**.
2. Appuyer sur **Applications**.
3. Sous « Général », appuyer sur **Applications par défaut**.
4. Appuyer sur **Application de navigateur**.
5. Sélectionner le navigateur voulu.
{% endtab %}

{% tab title="Samsung" %}
1. Ouvrir **Paramètres** > **Applications**.
2. Appuyer sur **Choisir les applications par défaut**.
3. Choisir **Application de navigateur**.
4. Sélectionner le navigateur voulu.

**Option : désactiver Samsung Internet**

**Paramètres** > **Applications** > **Samsung Internet** > **Désactiver**.

{% hint style="warning" %}
Sur certains Galaxy, le navigateur par défaut peut revenir à Samsung Internet tout seul. Vérifiez que l'économiseur de batterie du navigateur choisi n'est pas sur **Restreint** (le mode **Optimisé** convient).
{% endhint %}
{% endtab %}

{% tab title="Xiaomi / Redmi / POCO" %}
1. Ouvrir **Paramètres** > **Applications**.
2. Appuyer sur **Gérer les applications**.
3. Appuyer sur les **trois points** en haut à droite, puis sur **Applications par défaut**.
4. Appuyer sur **Navigateur** et choisir le navigateur voulu.

Mi Browser reste installé. Il est possible de désactiver ses notifications pour supprimer les messages indésirables.
{% endtab %}

{% tab title="Huawei" %}
1. Ouvrir **Paramètres** > **Applications**.
2. Appuyer sur **Applications par défaut**.
3. Appuyer sur **Application de navigateur**.
4. Choisir le navigateur voulu.
{% endtab %}

{% tab title="Vivo" %}
1. Ouvrir **Paramètres** > **Applications et autorisations**.
2. Aller dans **Gestion des autorisations** > **Paramètres des applications par défaut**.
3. Ouvrir **Navigateur**.
4. Choisir un navigateur autre que Vivo Browser.
{% endtab %}

{% tab title="Oppo" %}
**ColorOS 11 et versions ultérieures**

1. Ouvrir **Paramètres** > **Gestion des applications**.
2. Appuyer sur **Applications par défaut** > **Navigateur par défaut**.
3. Choisir le navigateur voulu.
{% endtab %}

{% tab title="iPhone / iPad" %}
**iOS / iPadOS 18.2 et versions ultérieures**

1. Ouvrir **Réglages** > **Apps**.
2. Appuyer sur **Apps par défaut**.
3. Appuyer sur **Navigateur**.
4. Choisir une autre application que Safari.

**iOS / iPadOS 14 à 17**

1. Ouvrir **Réglages**.
2. Descendre jusqu'à l'application du navigateur voulu (Chrome, Firefox, etc.).
3. Appuyer sur **Application de navigateur par défaut**.
4. Sélectionner ce navigateur.

{% hint style="info" %}
Un navigateur n'apparaît dans la liste que s'il remplit les conditions d'Apple et dispose de l'autorisation « navigateur par défaut ». Dans l'Union européenne, un écran de choix du navigateur est aussi proposé au premier lancement.
{% endhint %}
{% endtab %}
{% endtabs %}

***

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
