---
icon: shield-check
---

# VPN

## ProtonVPN

### Utiliser NextDNS et Proton VPN en même temps sur iPhone

Sur iOS, ProtonVPN impose par défaut ses propres résolveurs DNS dès qu'il est connecté. Mais depuis peu, l'application ProtonVPN propose un **DNS personnalisé** natif sur iOS et macOS, réservé aux offres payantes.

{% hint style="warning" %}
Le DNS personnalisé est incompatible avec NetShield, le bloqueur de pubs de Proton. \
L'application affiche d'ailleurs un avertissement à l'activation.
{% endhint %}

#### Limites de la fonction

* Le champ DNS personnalisé de l'app iOS n'accepte qu'une adresse **IPv4** (et hélas pas de `DoH`, de `DoT` ni `d'IPv6`).&#x20;
* L'identifiant de config NextDNS ne peut donc pas être transmis dans la requête. Il faut dans ce cas passer par la méthode **IP liée** de NextDNS, qui associe une IP publique à une configuration.

### Configuration

#### 1. Renseigner les DNS de NextNDS dans ProtonVPN

Réglages → Connexion → DNS personnalisé → Ajouter un nouveau serveur DNS.

Utilise les deux `IPv4` propres à ton compte, affichées dans le dashboard NextDNS (Setup → IP liée). Elles ont la forme suivante : `45.90.xx.xxx` et `45.90.xx.xxx`

#### 2. Lier l'IP de sortie du serveur Proton

L'IP à lier est celle du **serveur Proton. En effet, celle-ci** change à chaque changement de serveur ou reconnexion (sauf pour ceux qui bénéfice de l'option payante « IP dédiée »). Il faut donc appeler le **lien personnel de NextDNS** une fois connecté au VPN. L'adresse ressemble à ceci : `https://link-ip.nextdns.io/<identifiant>/<jeton>`

{% hint style="danger" %}
Ce lien est secret : il permet d'associer n'importe quelle IP à ta config. Ne le partage pas et ne le publie pas dans le wiki.
{% endhint %}

#### 3. Automatiser avec Raccourcis

1. Ouvre **Raccourcis** → Automatisation → Créer une automatisation personnelle
2. Déclencheur : **`VPN`** → ta configuration Proton VPN → **Se connecte**
3. Action : **Obtenir le contenu de l'URL** avec ton lien de liaison (méthode **`GET`**, par défaut, sans en-têtes ni corps).
4. Désactive **Demander avant d'exécuter**.

### Vérification

Une fois connecté au VPN, ouvre l'url `https://test.nextdns.io`

Résultat attendu :

| Champ     | Valeur attendue                      |
| --------- | ------------------------------------ |
| `status`  | `ok`                                 |
| `profile` | renseigné (identifiant de ta config) |
| `destIP`  | l'une de tes IP DNS NextDNS          |
| `client`  | l'IP de sortie du serveur Proton     |

Si le test affiche « `unconfigured` » après un changement de serveur, l'automatisation ne s'est pas déclenchée :/ . Il faudra vérifier le déclencheur et l'option « Demander avant d'exécuter ». Les requêtes apparaissent bien dans les **Logs** NextDNS mais sans le nom de l'appareil (`clientName: unknown`), ce qui est normal avec une IP liée ;) .

{% hint style="info" %}
Alternative : l'application **Passepartout** (app WireGuard open source) permet d'utiliser NextDNS en DoH ou DoT sans liaison d'IP. En contrepartie, tu perds le kill switch et une partie des fonctions de l'app Proton VPN.
{% endhint %}
