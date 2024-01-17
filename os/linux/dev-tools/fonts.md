---
description: Quelques outils, astuces de devs sur les polices d'écritures
---

# 📝 Fonts

## BunnyFonts

#### Description

[Bunny Fonts](https://fonts.bunny.net/) est une alternative à _Google Fonts_ qui est open source, axée sur la confidentialité et conforme à la réglementation RGPD. L'API Bunny Fonts a été conçue pour être entièrement compatible avec l'API Google Fonts CSS v1, ce qui rend le changement aussi facile que de changer le nom d'hôte :) .

Il suffit d'intervertir "**https://fonts.bunny.net/css**" à la place de "**https://fonts.googleapis.com/css**" dans le code source de votre site Web et de laisser vos utilisateurs profiter d'une meilleure confidentialité :tada:

{% hint style="success" %}
Site internet : [https://fonts.bunny.net/](https://fonts.bunny.net/)
{% endhint %}

***

## Cloudflare Fonts

#### Description

Cloudflare Fonts est une fonctionnalité conçue pour les sites Web qui utilisent Google Fonts.\
Elle permet de réécrire les polices Google pour qu'elles soient livrées à partir de l'origine du site Web, ce qui élimine la nécessité de dépendre de fournisseurs de polices tiers.

Ce service de fonts permet de réduire la latence et d'améliorer les performances d'un site Web mais également de masquer ces informations aux serveurs de Google. Cela permet ainsi d'améliorer la confidentialité des utilisateurs et de réduire le risque de suivi.

C'est une sevice de CDN pour les polices d'écritures pour faire simple.

{% embed url="https://blog.cloudflare.com/cloudflare-fonts-enhancing-website-privacy-speed/" %}

***

## Powerline-fonts

#### Description

Les polices Powerline, sont un ensemble de polices de caractères spécialement conçues pour être utilisées avec des interfaces en ligne de commande (CLI). Elles sont populaires parmi les utilisateurs de terminaux, en particulier dans l'écosystème des utilisateurs de lignes de commande, tels que ceux qui travaillent avec des shells comme Bash, Zsh, et d'autres.

L'objectif principal des polices Powerline est d'améliorer l'esthétique et la lisibilité des symboles utilisés dans les interfaces en ligne de commande, en particulier pour afficher des informations telles que le statut du système, l'emplacement du répertoire, le statut de la source du shell, etc.

#### Installation

```bash
sudo dnf install powerline-fonts
```

{% hint style="info" %}
Source  : [https://github.com/powerline/fonts](https://github.com/powerline/fonts)
{% endhint %}
