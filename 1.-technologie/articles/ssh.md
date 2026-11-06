---
description: Trucs & Astuces
icon: key
---

# SSH

### Notes

`OpenSSH` est parfois confondu avec _OpenSSL_, qui porte un nom proche; cependant, les projets ont des objectifs différents et sont développés par des équipes différentes, la similitude du nom est uniquement due à des objectifs similaires.

***

### Aide à la configuration

{% embed url="https://infosec.mozilla.org/guidelines/openssh.html" %}

_Ce document a pour but d'aider les équipes opérationnelles à configurer le serveur et le client OpenSSH_

***

### Auditer vos clés SSH existantes

Les clés SSH existantes sont généralement stockées dans : `~/.ssh/` (Linux/OSX) or `%APPDATA%` (Windows). Recherchez notamment les fichiers : `id_rsa`, `id_ed25519`, `id_ecdsa`, `id_dsa`, `identity`, `IdentityFile`, `*.pem`, qui peuvent contenir une **clé d'identité SSH**.

***

### Afficher les informations d'une clé SSH

```bash
# Vous pouvez exécuter cette commande pour n'importe quel fichier de clé SSH que vous possédez
ssh-keygen -lf id_rsa

# Exemple de résultat
2048 bc:4f:46:2b:3d:f1:e2:0f:ac:40:99:49:ed:c9:81:a2 Mozilla key for xyz (RSA)
# ^^                    ^^^^^^^^^                      ^^^^               ^^^
# |__ Taille de la clé  |__ Empreinte (Fingerprint)     |__ Commentaire   |__ Type
```

***

### Outils

{% embed url="https://github.com/jtesta/ssh-audit" %}
