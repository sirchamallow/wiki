---
icon: shield-check
---

# VPN

## ProtonVPN x NextDNS

Le guide complet pour configurer `ProtonVPN` et `NextDNS` ensemble (Fedora, macOS, iPhone/iPad, Android). Utiliser un VPN casse généralement le filtrage DNS personnalisé : dès que le tunnel s'établit, le fournisseur du VPN impose ses propres résolveurs DNS. \
\
Ce guide explique comment garder `NextDNS` actif — filtrage des pubs, trackers, contenus malveillants — tout en restant connecté en permanence à `ProtonVPN`, sur quatre environnements différents.

### Avant de commencer

<table><thead><tr><th width="122.08203125">Logiciel</th><th width="285.33203125">Plan nécessaire</th><th>Pourquoi</th></tr></thead><tbody><tr><td><strong>Proton VPN</strong></td><td><strong>Plus</strong> (à partir de ~3 à 10 $/mois selon l'engagement) ou <strong>Unlimited</strong></td><td>Le DNS personnalisé est réservé aux offres payantes. Le plan <code>Free</code> ne le propose pas.</td></tr><tr><td><strong>NextDNS</strong></td><td><strong>Free suffit techniquement</strong> (300 000 requêtes/mois, toutes les fonctions de filtrage incluses)</td><td>L'IP liée et le <code>DoH</code> sont disponibles gratuitement. Le plan <strong><code>Pro</code></strong> (1,99 $/mois) retire seulement le plafond de requêtes — utile si plusieurs appareils tournent dessus en continu.</td></tr></tbody></table>

En résumé : `ProtonVPN Plus` est **obligatoire**, `NextDNS Pro` est confortable mais pas indispensable.

### Point clé à retenir

En **`IPv6`** ou en **`DoH`, l'identifiant de ta configuration NextDNS est intégré dans l'adresse elle-même**. Pas besoin de lier une IP, ni d'automatiser quoi que ce soit — ça fonctionne du premier coup, à chaque connexion, sur n'importe quel serveur. C'est la méthode à privilégier partout où elle est disponible.

Seule l'app ProtonVPN sur **iOS** limite son champ DNS personnalisé à l'`IPv4`, ce qui oblige à passer par la liaison d'IP (voir plus bas).

### NextDNS credentials (

Sur `my.nextdns.io`, dans l'onglet **Setup**, tu trouveras :

* Deux adresses **IPv4** dédiées à ton compte (`45.90.28.xxx` et `45.90.30.xxx`)
* Deux adresses **IPv6** au format `2a07:a8c0::<ton-id>` et `2a07:a8c1::<ton-id>`
* Une URL **DoH** : `https://dns.nextdns.io/<ton-id>` (ajoute `/<nom-appareil>` à la fin pour identifier l'appareil dans les logs)
* Le lien personnel de liaison d'IP : `https://link-ip.nextdns.io/<ton-id>/<jeton>` (ne le partage jamais)

***

### MacOS

1. Barre de menus → **Proton VPN** → **Settings…** → onglet **Advanced** → **Custom DNS**.
2. Active le toggle, accepte l'avertissement NetShield (les deux fonctions sont incompatibles).
3. Ajoute directement tes deux adresses **IPv6** NextDNS (`2a07:a8c0::<ton-id>` et `2a07:a8c1::<ton-id>`). Aucune liaison d'IP n'est nécessaire.
4. Vérifie que le protocole est **WireGuard** (Réglages → Sécurité → Protocole).
5. Teste sur `https://test.nextdns.io` une fois connecté : `status: ok` et ton `profile` doivent apparaître.

***

### Fedora (Linux)

1.  Installe l'application officielle ProtonVPN :

    ```bash
    wget https://repo.protonvpn.com/fedora-$(cat /etc/fedora-release | tr -dc '0-9')-stable/protonvpn-stable-release/protonvpn-stable-release-1.0.2-1.noarch.rpm
    sudo dnf install ./protonvpn-stable-release-1.0.2-1.noarch.rpm
    sudo dnf check-update
    sudo dnf install proton-vpn-gnome-desktop
    ```
2. Dans l'app : Réglages → Connexion → DNS personnalisé → ajoute tes deux adresses **IPv6** NextDNS. Là aussi, pas de liaison d'IP nécessaire.
3.  Ou en CLI :

    ```bash
    protonvpn config set custom-dns --dns 2a07:a8c0::<ton-id>,2a07:a8c1::<ton-id> on
    ```
4. Vérifie avec `curl -s https://test.nextdns.io | jq`.

***

### Android

1. Ouvre l'app ProtonVPN → **Réglages** → **Connexion** → **Paramètres avancés** → **DNS personnalisé**.
2. Ajoute un nouveau serveur DNS, accepte l'avertissement NetShield.
3. Renseigne tes deux adresses **IPv6** NextDNS. L'app Android accepte nativement l'IPv6, donc aucune automatisation à mettre en place.
4. Reconnecte le VPN et vérifie sur `test.nextdns.io`.

***

### iPhone / iPad (iOS)

C'est la seule plateforme où le champ DNS personnalisé de Proton VPN n'accepte que l'**IPv4**, ce qui impose la liaison d'IP.

1. **Réglages → Connexion → DNS personnalisé** : ajoute `45.90.28.192` et `45.90.30.192` (tes IPv4 dédiées).
2. Accepte l'avertissement NetShield.
3. Vérifie que le protocole est **WireGuard**.
4. **Automatise la liaison d'IP** avec l'app Raccourcis, puisque sans IP dédiée côté Proton, l'IP de sortie change à chaque reconnexion ou changement de serveur :
   * Raccourcis → Automatisation → Créer une automatisation personnelle
   * Déclencheur : **VPN** → ta config ProtonVPN → **Se connecte**
   * Action : **Obtenir le contenu de l'URL** avec ton lien `link-ip.nextdns.io/<ton-id>/<ton-jeton>` (méthode GET)
   * Désactive **Demander avant d'exécuter**
5. Teste sur `test.nextdns.io`. Le champ `client` doit afficher l'IP du serveur Proton, et `status` doit être `ok`.

_Si tu changes souvent de serveur et que l'automatisation te semble fragile,_ une alternative consiste à importer une config WireGuard Proton dans une app tierce comme **Passepartout**, qui permet de renseigner directement l'URL DoH de NextDNS. L'inconvénient est l'absence de kill switch, à mettre en balance avec le confort gagné.
