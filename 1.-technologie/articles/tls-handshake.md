---
icon: expeditedssl
---

# TLS Handshake

## Préambule

**SSL** et **TLS** servent tous les deux à **chiffrer les échanges** sur Internet.

La différence principale :

* **SSL** = ancien protocole, **obsolète et non sécurisé**
* **TLS** = version **moderne et sécurisée**, utilisée aujourd’hui

En pratique :

* quand on dit encore **“SSL”**, on parle souvent de **TLS** par habitude
* le **HTTPS** actuel utilise **TLS**, et non SSL

**Résumé :** SSL est l’ancienne technologie ; TLS est son successeur. Aujourd’hui, il faut utiliser **TLS**.

***

## Bonnes pratiques

### C'est quoi le TLS Handshake ?

Imaginez un appel téléphonique confidentiel : avant de parler, vous vérifiez l'identité de votre interlocuteur et vous vous mettez d'accord sur une façon de coder vos propos pour que personne d'autre ne puisse les comprendre. C'est exactement ce que fait le **TLS Handshake** (« poignée de main TLS ») entre votre navigateur et un site web, juste avant qu'une connexion sécurisée (HTTPS) ne s'établisse.

```
Client                         Serveur
  |                                |
  | ---- ClientHello -----------> |
  |                                |
  | <--- ServerHello ------------  |
  | <--- Certificat SSL/TLS -----  |
  |                                |
  |   Vérification certificat     |
  |   + négociation des clés      |
  |                                |
  | ===== Connexion chiffrée ==== |
  |        HTTPS sécurisé         |
```

Pendant cet échange, le navigateur et le serveur se mettent d'accord sur quatre choses :

* la **version de TLS** à utiliser ;
* la méthode de chiffrement à employer (on parle de _cipher suite_, voir plus bas) ;
* la manière de générer une clé secrète partagée ;
* l'identité du serveur, grâce à un document numérique appelé **certificat**, un peu comme une carte d'identité.

> **En une phrase :** _« On se met d'accord sur comment sécuriser la communication avant de commencer à communiquer. »_

### Notions clés

Certains termes un peu barbare au premier abord reviennent systématiquement dès qu'on parle de sécurité sur Internet. En voici quelques uns.

### TLS (Transport Layer Security)

C'est le protocole — c'est-à-dire l'ensemble de règles — qui chiffre et authentifie une connexion réseau. C'est le successeur de l'ancien protocole SSL, et c'est lui qui orchestre tout le handshake décrit ci-dessus. Concrètement, TLS garantit qu'une personne malveillante placée entre vous et le site que vous consultez ne peut ni lire, ni modifier ce qui est échangé.

#### Cipher suite (« suite de chiffrement »)

Une _cipher suite_ n'est pas un algorithme unique, mais une combinaison de plusieurs briques qui travaillent ensemble :

<table><thead><tr><th width="242">Cette brique...</th><th>...sert à</th></tr></thead><tbody><tr><td>Échanger une clé secrète</td><td>Permettre au client et au serveur de se mettre d'accord sur un secret commun, sans que quiconque d'autre ne puisse le deviner</td></tr><tr><td>Prouver l'identité du serveur</td><td>Vérifier, via le certificat, que l'on parle bien au bon site</td></tr><tr><td>Chiffrer les données</td><td>Rendre les échanges illisibles pour un tiers</td></tr><tr><td>Vérifier l'intégrité</td><td>S'assurer que les données n'ont pas été modifiées en chemin</td></tr></tbody></table>

Chaque brique a son propre nom (par exemple ECDHE pour l'échange de clé, AES pour le chiffrement...), et c'est l'assemblage de toutes ces briques qui forme une _cipher suite_.

#### ECDSA

Il s'agit d'une méthode mathématique permettant à un certificat de prouver son authenticité, un peu comme une signature manuscrite difficile à imiter. Elle remplit le même rôle qu'une autre méthode plus ancienne (RSA), mais avec des clés beaucoup plus courtes pour un niveau de sécurité équivalent. Résultat : les échanges sont plus rapides et plus légers, ce qui profite directement à la vitesse du handshake.

#### HSTS (HTTP Strict Transport Security)

C'est une instruction envoyée par le serveur qui dit, en substance, au navigateur : _« À partir de maintenant, ne me contacte plus jamais autrement qu'en HTTPS pour ce site, même si on te propose une adresse en http:// »_. Cela empêche un attaquant de rediriger discrètement un visiteur vers une version non sécurisée du site. Le paramètre `max-age` qui accompagne cette instruction indique simplement combien de temps le navigateur doit s'en souvenir (par exemple deux ans).

***

### Pourquoi certaines méthodes de chiffrement sont-elles obsolètes ?

La cryptographie vieillit mal, pour deux raisons principales :

* **La puissance de calcul augmente.** Un chiffrement jugé inviolable il y a quinze ans peut aujourd'hui être cassé en quelques heures avec du matériel courant, simplement parce que les ordinateurs sont devenus bien plus puissants.
* **Des failles sont découvertes avec le temps.** Des chercheurs trouvent régulièrement des défauts dans d'anciens algorithmes, qui permettent à un attaquant de déchiffrer ou de falsifier une communication sans même avoir besoin de « deviner » la clé secrète.

C'est pourquoi certaines versions de TLS (comme TLS 1.0 et 1.1) et certains anciens algorithmes sont aujourd'hui déconseillés, voire interdits par les navigateurs récents : ils n'offrent plus de garantie de sécurité réelle, même s'ils continuent techniquement à « fonctionner ». Utiliser des suites modernes (TLS 1.2/1.3, ECDHE, AES-GCM ou ChaCha20-Poly1305) permet d'éviter ces faiblesses connues.

***

### Configurer un serveur

Configurer un serveur « à la main » revient à choisir, parmi toutes les options disponibles, celles qui offrent le meilleur compromis entre **sécurité** et **compatibilité** avec les visiteurs du site.&#x20;

Le site de référence [**TLSRef**](https://tlsref.org/) (Server-Side TLS) propose deux profils prêts à l'emploi :

<table><thead><tr><th width="135">Profil</th><th width="222">Public cible</th><th width="156">Protocoles autorisés</th><th>Compatibilité</th></tr></thead><tbody><tr><td><strong>Modern</strong></td><td>Clients très récents uniquement, sans besoin de rétrocompatibilité</td><td>TLS 1.3 uniquement</td><td>Très restreinte</td></tr><tr><td><strong>Intermediate</strong> (recommandé)</td><td>Usage général, serveur grand public</td><td>TLS 1.2 + TLS 1.3</td><td>Large (compatible avec la quasi-totalité des clients depuis 5 ans et plus)</td></tr></tbody></table>

#### Appliquer la configuration serveur

<table><thead><tr><th width="149">Serveur</th><th width="231">Où se trouve la configuration</th><th>Ce qu'il faut modifier</th></tr></thead><tbody><tr><td><strong>Nginx</strong></td><td>Bloc <code>server</code> du fichier de configuration du site</td><td>Directives <code>ssl_protocols</code>, <code>ssl_ciphers</code>, <code>ssl_prefer_server_ciphers</code>, <code>add_header Strict-Transport-Security</code></td></tr><tr><td><strong>Apache</strong></td><td>Fichier de configuration du VirtualHost SSL</td><td>Directives <code>SSLProtocol</code>, <code>SSLCipherSuite</code>, <code>Header always set Strict-Transport-Security</code></td></tr><tr><td><strong>IIS (Windows Server)</strong></td><td>Registre Windows (clés SCHANNEL) ou IIS Crypto (outil graphique)</td><td>Activation/désactivation des protocoles et des suites via les clés <code>Enabled</code> sous <code>HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL</code></td></tr><tr><td><strong>Reverse proxy / load balancer</strong> (HAProxy, Traefik...)</td><td>Fichier de configuration du proxy</td><td>Paramètre équivalent à <code>ssl-min-ver</code> / liste de ciphers autorisés</td></tr></tbody></table>

TLSRef génère directement, sur sa page, un bloc de configuration prêt à copier-coller pour chacun de ces logiciels, une fois le profil et la version choisis. Cela évite de devoir mémoriser le nom exact de chaque directive.

#### Vérifier la configuration appliquée

Une fois la configuration modifiée et le service redémarré, il faut vérifier que le changement a bien été pris en compte. Trois méthodes simples :

* **Avec `openssl`** (Linux/macOS, ou WSL sous Windows) :

```bash
openssl s_client -connect exemple.fr:443 -tls1_2
```

Cette commande force une connexion en TLS 1.2 et affiche, entre autres, la cipher suite réellement négociée. En changeant `-tls1_2` par `-tls1` ou `-ssl3`, on peut vérifier que les anciens protocoles sont bien refusés par le serveur.

* **Avec `curl`** :

```bash
curl -v --tlsv1.2 --tls-max 1.2 https://exemple.fr
```

Utile pour tester rapidement, en ligne de commande, qu'une version précise de TLS fonctionne (ou non) sur le site.

* **Avec un outil en ligne** (type SSL Labs ou équivalent) : ces services se connectent au serveur depuis l'extérieur et donnent une note globale, en détaillant les protocoles actifs, les cipher suites proposées, la présence de HSTS et les éventuelles vulnérabilités connues encore ouvertes.

***

### Bonus : Schéma de décision

Voici un Schéma de décision pour configurer ou diagnostiquer un serveur. Ce schéma résume la démarche : choisir un profil adapté au public du site, l'appliquer dans la configuration du serveur concerné, puis vérifier concrètement que seuls les protocoles et suites souhaités sont acceptés.

```
                 Nouveau serveur à sécuriser
                           |
                           v
        Qui se connecte à ce serveur ? (navigateurs, API, objets connectés...)
                           |
         +-----------------+------------------+
         |                                     |
  Clients anciens à supporter          Uniquement clients récents
         |                                     |
         v                                     v
   Profil "Intermediate"                 Profil "Modern"
   (TLS 1.2 + TLS 1.3)                   (TLS 1.3 uniquement)
         |                                     |
         +-----------------+------------------+
                           |
                           v
        Appliquer la configuration (Nginx / Apache / IIS / proxy)
                           |
                           v
            Activer HSTS + certificat ECDSA ou RSA 2048
                           |
                           v
        Vérifier avec openssl s_client / curl / outil en ligne
                           |
                 +---------+---------+
                 |                   |
         Ancien protocole       Tout est conforme
         encore accepté ?             |
                 |                    v
                 v              Configuration validée
      Revoir la configuration
      et redémarrer le service
```

Ce schéma résume la démarche : choisir un profil adapté au public du site, l'appliquer dans la configuration du serveur concerné, puis vérifier concrètement que seuls les protocoles et suites souhaités sont acceptés.
