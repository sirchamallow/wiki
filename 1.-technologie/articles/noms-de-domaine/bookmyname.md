---
description: Custom DNS
icon: b
---

# BookMyName

## Présentation

**BookMyName** est un bureau d’enregistrement (registrar) de noms de domaine français, accrédité ICANN depuis 1999. Il propose l’enregistrement, le renouvellement et le transfert de plus de 350 extensions, avec en plus des services DNS, de redirection et de messagerie de base. BookMyName est une marque commerciale de **Scaleway SAS** (ex-Online SAS), filiale du groupe Iliad (Free). Iliad l’a racheté à LDCom en 2002.

**Points forts**

* Registrar français adossé à un grand groupe, accrédité ICANN et membre de l’AFNIC.
* Tarifs affichés clairement, sans frais cachés.
* Zone DNS personnalisable avec sous-domaines illimités, redirections mail et web, boîtes mail et DNSSEC automatique.
* Authentification à deux facteurs (TOTP) disponible.
* Support par e-mail et hotline.

***

## Zone DNS personnalisée (interface pour utilisateurs avertis)

### Présentation

Le service de zone DNS personnalisée permet de définir soi-même les réponses des serveurs DNS de BookMyName pour un domaine. On peut ainsi faire pointer le domaine vers les serveurs de messagerie (SMTP) et/ou les serveurs web de son choix, y compris ses propres serveurs s'ils ont une adresse IP fixe, et déclarer un nombre illimité de sous-domaines. L'interface pour utilisateurs avertis permet de saisir directement le contenu de la zone sous forme de texte brut.

### Prérequis

* Le domaine doit utiliser les serveurs DNS de BookMyName. Avec d'autres serveurs DNS (hébergeur, serveurs personnels), la zone saisie ici n'est pas utilisée.
* Les services de redirection mail/web, de boîtes mail et de personnalisation de zone exigent tous les DNS de BookMyName. Tout autre choix les invalide.
* Ne choisissez jamais des serveurs DNS au hasard.
* Pour changer les serveurs DNS : MANAGE > Changer les DNS de vos noms de domaine. Il faut indiquer entre 2 et 13 serveurs. Attention : le changement s'applique à tous les domaines listés dans la fenêtre.
* Si vous activez le service de boîtes mail, les DNS de BookMyName remplacent automatiquement les serveurs actuels. Les services gérés par les anciens DNS (ceux d'un hébergeur par exemple) sont alors immédiatement interrompus.

### Règles de saisie

1. Entrez les enregistrements ligne par ligne.
2. Le caractère `@` représente le nom du domaine lui-même.
3. Si le nom est un nom d'hôte complet (FQDN), il faut ajouter un point `.` juste après le dernier caractère.
4. Le type d'enregistrement peut être précédé d'un `TTL` en secondes. Ne pas descendre en dessous de `300`.
5. La partie droite d'un enregistrement `MX` doit être un nom de machine, et non une adresse IP.

### Syntaxe générale

```
<nom> [TTL] <type> <valeur>
```

<table><thead><tr><th width="86.94921875">Élément</th><th>Description</th></tr></thead><tbody><tr><td>nom</td><td><code>@</code> (domaine lui-même) ou nom relatif (<code>www</code>, <code>sousdomaine</code>, etc.)</td></tr><tr><td>TTL</td><td>Optionnel. Durée en secondes dans les caches DNS (minimum <strong>300</strong>)</td></tr><tr><td>type</td><td>Type d'enregistrement (voir ci-dessous)</td></tr><tr><td>valeur</td><td>Contenu de l'enregistrement, selon le type</td></tr></tbody></table>

### Types d'enregistrements pris en charge

```
MX  A  CNAME  NS  AAAA  TXT  SRV  WKS  CAA  TLSA  SSHFP
```

### Compatibilité avec les autres services BookMyName

* **Redirections mail et web :** compatibles avec la personnalisation de zone.
* **Boîtes mail BookMyName :** compatibles, mais ne créez pas dans la zone les noms `pop`, `imap` et `webmail`, pour éviter un conflit de noms.
* **DNSSEC :** il est activé automatiquement lorsque les serveurs DNS de BookMyName sont utilisés en mode parking, redirection ou personnalisation.

### Délais de prise en compte

* La propagation DNS varie de quelques minutes à plusieurs jours. Elle se fait progressivement sur l'ensemble du réseau.
* Une modification de redirection (mail ou web) prend quelques secondes, à condition que le DNS n'ait pas été modifié en même temps.
* Nouveau compte mail sur un domaine auparavant géré par d'autres DNS : il faut attendre l'expiration du TTL de l'ancien enregistrement MX (souvent plus de 24 h). S'il n'y avait pas de MX, comptez environ 30 minutes.
* Avant une migration, baissez le TTL (300 minimum) quelques heures à l'avance.

***

### Exemples de base

**Pointer le domaine vers une adresse IPv4**

```
@ A 88.191.11.16
```

domaine.com pointera vers l'adresse IP 88.191.11.16.

**Pointer www vers une adresse IPv4**

```
www A 88.191.11.16
```

www.domaine.com pointera vers l'adresse IP 88.191.11.16.

**Pointer www vers une adresse IPv6**

```
www AAAA 2a01:e0d:1:2:58bf:f987:0:16
```

www.domaine.com pointera vers l'adresse IPv6 2a01:e0d:1:2:58bf:f987:0:16.

**Définir les serveurs de messagerie (MX)**

```
@ MX 10 smtp.chezmoi.net.
@ MX 30 smtp2.qqpart.com.
```

Le mail sera envoyé à la machine smtp.chezmoi.net (noter le point final). Si elle ne répond pas, il sera envoyé à smtp2.qqpart.com. Le nombre qui précède le nom de machine est la priorité : la valeur la plus basse est utilisée en premier.

**Créer un sous-domaine**

```
www.sousdomaine A 88.191.11.16
```

www.sousdomaine.domaine.com pointera vers l'adresse 88.191.11.16.

**Définir un TTL**

```
sousdomaine2 3600 A 88.191.11.16
```

sousdomaine2.domaine.com pointera vers l'adresse 88.191.11.16 et ne restera pas plus de 3600 secondes (1 h) dans les caches DNS.

***

### Bonnes pratiques

* **Un seul SPF par domaine :** si vous utilisez plusieurs services d'envoi, regroupez-les dans un seul enregistrement TXT SPF (plusieurs `include:` dans la même ligne), jamais deux enregistrements SPF distincts.
* **Priorité MX :** si vous changez de messagerie, supprimez les anciens MX ou donnez au nouveau fournisseur la priorité la plus basse (donc la plus prioritaire).
* **Point final :** sans point final, un nom complet est interprété comme relatif au domaine (`smtp.chezmoi.net` deviendrait `smtp.chezmoi.net.domaine.com`).
* **Valeurs fournies par un service :** copiez-les exactement (noms et valeurs).

***

### Exemples de configurations courantes

#### Vérification de propriété du domaine

**Google**

```
googlefffggghhh12345 CNAME google.com.
@ TXT "google-site-verification=(votre chaîne unique)"
```

Remplacez `(votre chaîne unique)` et le nom du CNAME par les valeurs fournies par Google.

**Office 365**

```
@ 3600 TXT "MS=ms81723891723"
```

#### Messagerie : fournisseurs tiers

Pour chaque fournisseur, les valeurs exactes (code de vérification, valeurs DKIM) sont affichées dans son interface au moment de l'ajout du domaine. Les exemples ci-dessous donnent la forme des enregistrements.

**Proton Mail**

```
@ TXT "protonmail-verification=(code fourni par Proton)"
@ MX 10 mail.protonmail.ch.
@ MX 20 mailsec.protonmail.ch.
@ TXT "v=spf1 include:_spf.protonmail.ch mx ~all"
protonmail._domainkey CNAME (valeur fournie par Proton).
protonmail2._domainkey CNAME (valeur fournie par Proton).
protonmail3._domainkey CNAME (valeur fournie par Proton).
_dmarc TXT "v=DMARC1; p=quarantine"
```

* Les trois CNAME DKIM permettent la rotation automatique des clés. Ils doivent correspondre exactement à ceux affichés dans l'assistant Proton (Paramètres, Noms de domaine, Examiner, onglet DKIM).
* Si un ancien enregistrement TXT DKIM (rotation manuelle) existe, supprimez-le avant d'ajouter les CNAME.
* `~all` : les mails non autorisés sont marqués comme échec SPF mais acceptés. `-all` les fait rejeter.
* DMARC : `p=none` (test), `p=quarantine` (recommandé par Proton), `p=reject` (strict). L'option `rua=mailto:adresse` permet de recevoir des rapports.

**Tuta**

```
@ TXT "t-verify=(code fourni par Tuta)"
@ MX 10 mail.tutanota.de.
@ TXT "v=spf1 include:spf.tutanota.de -all"
s1._domainkey CNAME s1.domainkey.tutanota.de.
s2._domainkey CNAME s2.domainkey.tutanota.de.
_dmarc TXT "(valeur proposée par Tuta)"
```

* La TXT de vérification se saisit avec `@` comme nom et `t-verify=...` comme valeur, sans répéter le `@` dans la valeur.
* L'assistant se trouve dans Paramètres, Paramètres globaux, Domaines de messagerie personnalisés.
* Tuta propose aussi des CNAME pour MTA-STS (`_mta-sts`), optionnels. Reprenez les valeurs affichées par l'assistant.

**Google gère vos emails**

```
@ MX 10 aspmx.l.google.com.
@ MX 30 alt1.aspmx.l.google.com.
@ MX 30 alt2.aspmx.l.google.com.
@ MX 50 aspmx2.googlemail.com.
@ MX 50 aspmx3.googlemail.com.
@ TXT "v=spf1 include:aspmx.googlemail.com ~all"
```

#### Messagerie BookMyName

Serveurs à configurer dans votre client de messagerie (TLS obligatoire, quel que soit le port) :

<table><thead><tr><th width="152.75390625">Service</th><th width="241.65625">Serveur</th><th>Ports</th></tr></thead><tbody><tr><td>Webmail</td><td>webmail.bookmyname.com</td><td>(navigateur)</td></tr><tr><td>POP3 / POP3S</td><td>pop.bookmyname.com</td><td>110 / 995 (995 conseillé)</td></tr><tr><td>IMAP / IMAPS</td><td>imap.bookmyname.com</td><td>143 / 993 (993 conseillé)</td></tr><tr><td>SMTP / SMTPS</td><td>smtp.bookmyname.com</td><td>587 / 465 (465 conseillé)</td></tr></tbody></table>

Limites : de 1 à 20 boîtes, 3 Go au total, 35 Mo maximum par message (pièces jointes comprises).

Le serveur SMTP de BookMyName ne doit pas servir aux envois en masse, aux newsletters ni aux envois automatisés. Son usage abusif entraîne la suspension du compte.

**SPF pour le webmail BookMyName**

```
@ TXT "v=spf1 include:_spf.bookmyname.com ?all"
```

**Webmail BookMyName et SMTP du FAI Free**

```
@ TXT "v=spf1 include:_spf.bookmyname.com include:_spf.free.fr ?all"
```

**Webmail BookMyName et SMTP du FAI Orange**

```
@ TXT "v=spf1 include:_spf.bookmyname.com include:_spf_gp.orange.fr include:spf.email-control.orange-business.com include:_spf_gpf.orange.fr include:_spf_other.orange.fr ?all"
```

#### DKIM générique (sélecteur « mail »)

```
mail._domainkey TXT "v=DKIM1; k=rsa; p=(votre clé publique)"
```

#### DMARC générique

```
_dmarc TXT "v=DMARC1; p=quarantine; rua=mailto:dmarc@domaine.com"
```

DMARC s'appuie sur un SPF et un DKIM valides. Commencez par `p=none` pour observer les rapports, puis durcissez.

#### Services de communication (SRV)

**Skype Entreprise**

```
sip._tls 3600 IN SRV 100 1 443 sipdir.online.lync.com.
```

#### CAA (Certification Authority Authorization)

```
@ CAA 0 issue "letsencrypt.org"
@ CAA 0 issuewild "symantec.com"
@ CAA 0 iodef "mailto:moi@mondomaine.com"
```

Ces enregistrements définissent quelles autorités de certification peuvent émettre des certificats pour le domaine (`issue`), pour les certificats génériques (`issuewild`), et où signaler les demandes non conformes (`iodef`).

#### DNSSEC : ne pas publier de clé au registre

```
@ TXT "NODNSSEC"
```

### Utiliser ses propres serveurs DNS (hors zone personnalisée)

Si vous utilisez vos propres serveurs DNS, **la zone se gère chez vous, pas dans cette interface**.

* Attribution des serveurs : MANAGE > Changer les DNS de vos noms de domaine.
* Si le nom du serveur DNS est un sous-domaine d'un domaine enregistré chez BookMyName, il faut le déclarer au registre avec son adresse IP : MANAGE > Enregistrer vos serveurs DNS (hôtes) au registre. Cela vaut aussi pour mettre à jour son adresse IP.
* De nombreux registres (COM, NET, ORG, BIZ, INFO, etc.) exigent que les serveurs soient déclarés avant de pouvoir les utiliser pour un autre domaine.
* Pour les domaines en .AT, .DE, .IT et .LU, les serveurs doivent être configurés avant leur attribution, sinon le registre refuse l'installation ou la modification.

### Points d'attention

* Un nom complet (FQDN) doit toujours se terminer par un point.
* La valeur d'un MX est un nom de machine, jamais une adresse IP.
* Un TTL inférieur à `300` secondes n'est pas accepté.
* La zone n'est prise en compte que si le domaine utilise les serveurs DNS de BookMyName.
* Ne créez pas les noms `pop`, `imap` et `webmail` si vous utilisez les boîtes mail BookMyName.
