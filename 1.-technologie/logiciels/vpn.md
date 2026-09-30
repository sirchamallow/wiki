---
icon: shield-check
---

# VPN

## ProtonVPN x NextDNS

Voici un guide complet pour configurer `ProtonVPN` et `NextDNS` ensemble sur plusieurs OS (Fedora, macOS, iPhone/iPad et Android). Utiliser un VPN casse généralement le filtrage DNS personnalisé (et c'est bien dommage) car dès que le tunnel s'établit, le fournisseur du VPN impose ses propres résolveurs DNS. Mais depuis peu, Proton à fait évoluer l'application et permets désormais de changer ceux de base.

Ce guide explique comment garder **`NextDNS`** **actif** — filtrage des pubs, trackers, contenus malveillants — **tout en restant connecté en permanence à `ProtonVPN`**.

{% hint style="success" %}
Source : [https://protonvpn.com/fr/support/custom-dns](https://protonvpn.com/fr/support/custom-dns)
{% endhint %}

### Pré-requis

<table><thead><tr><th width="122.08203125">Logiciel</th><th width="285.33203125">Plan nécessaire</th><th>Pourquoi</th></tr></thead><tbody><tr><td><strong>Proton VPN</strong></td><td><strong>Plus</strong> (à partir de ~3 à 10 €/mois selon l'engagement) ou <strong>Unlimited</strong></td><td>Le DNS personnalisé est réservé aux offres payantes. Le plan <code>Free</code> ne le propose pas.</td></tr><tr><td><strong>NextDNS</strong></td><td>Free (300 000 requêtes/mois, toutes les fonctions de filtrage incluses)</td><td>L'IP liée et le <code>DoH</code> sont disponibles gratuitement. Le plan <strong><code>Pro</code></strong> (1,99 $/mois) retire seulement le plafond de requêtes — utile si plusieurs appareils tournent dessus en continu.</td></tr></tbody></table>

{% hint style="success" %}
En résumé : `ProtonVPN Plus` est **obligatoire**, `NextDNS Pro` est confortable mais pas indispensable.
{% endhint %}

### Point clé à retenir

En **`IPv6`** ou en **`DoH`,** l'identifiant de ta configuration NextDNS est intégré dans l'adresse elle-même. Pas besoin de lier une IP, ni d'automatiser quoi que ce soit — ça fonctionne du premier coup, à chaque connexion, sur n'importe quel serveur ! C'est la méthode à privilégier partout où elle est disponible.&#x20;

{% hint style="warning" %}
Seule l'app ProtonVPN sur **iOS** et **MacOS** limite son champ DNS personnalisé à l'`IPv4`, ce qui oblige à passer par la liaison d'IP (voir plus bas).
{% endhint %}

{% hint style="warning" %}
Pour les utilisateurs de la version **Proton VPN** intégré à **Vivaldi**, cette intégration s'apparente plus à un **"secure web proxy"** qui ne protège que le trafic du navigateur Vivaldi et non celui du reste du système. De plus certaines connexions internes du navigateur peuvent contourner l'extension selon les limitations imposées par le navigateur. Source : https://protonvpn.com/fr/support/browser-extension-limitations.\
Le résultat est trop improbable pour vous le garantir.\

{% endhint %}

### NextDNS credentials

{% hint style="info" %}
Sur la page `my.nextdns.io`, dans l'onglet **Installation**, bloc **IP liée** vous trouverez :

* 2x adresses **IPv4** dédiées à votre compte (`45.90.xx.xxx` et `45.90.xx.xxx`)
* 2x adresses **IPv6** au format `2a07:a8c0::<ton-id>` et `2a07:a8c1::<ton-id>`
* Une URL **DoH** : `https://dns.nextdns.io/<ton-id>` (ajoute `/<nom-appareil>` à la fin pour identifier l'appareil dans les logs)
* Le lien personnel de liaison d'IP : `https://link-ip.nextdns.io/<ton-id>/<jeton>` (ne le partage jamais)
{% endhint %}

***

### MacOS&#x20;

1. Barre de menus → **Proton VPN** → **Réglages…** → onglet **Paramètres avancés** → **DNS personnalisé**
2. Active le toggle, accepte l'avertissement _`NetShield`_ (les deux fonctions sont incompatibles)
3. Ajoute directement tes deux adresses **IPv4** NextDNS (`45.90.xx.xxx` et `45.90.xx.xxx`). Aucune liaison d'IP n'est nécessaire
4. Vérifie que le protocole est **WireGuard** (Réglages → Sécurité → Protocole)
5. Teste sur `https://test.nextdns.io` une fois connecté : `status: ok` et ton `profile` doivent apparaître

***

### Linux (Fedora)

1. Installe l'application officielle ProtonVPN :

{% hint style="success" %}
Source : [https://protonvpn.com/support/official-linux-vpn-fedora](https://protonvpn.com/support/official-linux-vpn-fedora)
{% endhint %}

<pre class="language-bash"><code class="lang-bash">wget https://repo.protonvpn.com/fedora-$(cat /etc/fedora-release | tr -dc '0-9')-stable/protonvpn-stable-release/protonvpn-stable-release-1.0.2-1.noarch.rpm # Téléchargez le package ProtonVPN (GUI +CLI)
sudo dnf install ./protonvpn-stable-release-1.0.2-1.noarch.rpm # Installez le package ProtonVPN (GUI +CLI)
s<a data-footnote-ref href="#user-content-fn-1">udo dnf check-update</a>                     # Vérifier les mise à jour
sudo dnf install proton-vpn-gnome-desktop # Installez ProtonVPN pour Fedora/GNOME
</code></pre>

1. Dans l'application : Réglages → Connexion → DNS personnalisé → ajoute tes deux adresses **IPv6** NextDNS. Là aussi, pas de liaison d'IP nécessaire
2. Ou en CLI :

```bash
protonvpn config set custom-dns --dns 2a07:a8c0::<ton-id>,2a07:a8c1::<ton-id> on
```

Vérifier le résultat avec `curl -s https://test.nextdns.io | jq`

***

### Android

1. Ouvrir l'application ProtonVPN → **Réglages** → **Connexion** → **Paramètres avancés** → **DNS personnalisé**
2. Ajouter un nouveau serveur DNS et _accepter l'avertissement NetShield_
3. Renseigne tes deux adresses **IPv6** NextDNS. L'app Android accepte nativement l'IPv6, donc aucune automatisation à mettre en place
4. Reconnecter le VPN et vérifier la connexion sur `test.nextdns.io`

***

### iPhone / iPad (iOS)

C'est la seule plateforme où le champ DNS personnalisé de Proton VPN n'accepte que l'**IPv4**, ce qui impose la liaison d'IP.

1. **Réglages → Connexion → DNS personnalisé** : ajoute `45.90.28.192` et `45.90.30.192` (tes IPv4 dédiées).
2. Accepter l'avertissement NetShield
3. Vérifier que le protocole est **WireGuard**
4. **Automatiser la liaison d'IP** avec l'app `Raccourcis`, puisque sans IP dédiée côté Proton, l'IP de sortie change à chaque reconnexion ou changement de serveur :
   * Raccourcis → Automatisation → Créer une automatisation personnelle
   * Déclencheur : **VPN** → ta config ProtonVPN → **Se connecte**
   * Action : **Obtenir le contenu de l'URL** avec ton lien `link-ip.nextdns.io/<ton-id>/<ton-jeton>` (méthode **`GET`**)
   * Désactive **Demander avant d'exécuter**
5. Teste sur `test.nextdns.io`. Le champ `client` doit afficher l'IP du serveur Proton, et `status` doit être `ok`

[^1]: 
