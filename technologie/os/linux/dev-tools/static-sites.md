---
description: Pour faire des sites statiques :)
icon: globe-pointer
---

# Static Sites

## Jekyll

<figure><img src="../../../../.gitbook/assets/jekyll-og.png" alt="" width="375"><figcaption></figcaption></figure>

#### Installation

```bash
sudo dnf install ruby-devel	# Installation
gem install jekyll		# Installation gem jekyll
jekyll new my-site 		# Create new site
cd my-site			# Navigate to new site
jekyll serve			# Launch server (http://localhost:4000)
```

{% hint style="info" %}
Source : [https://developer.fedoraproject.org/start/sw/web-app/jekyll.html](https://developer.fedoraproject.org/start/sw/web-app/jekyll.html)
{% endhint %}

#### Hébergement

{% content-ref url="../../../articles/markdown/" %}
[markdown](../../../articles/markdown/)
{% endcontent-ref %}

## Hugo

<figure><img src="../../../../.gitbook/assets/hugo.png" alt="" width="323"><figcaption></figcaption></figure>

#### Installation

```bash
sudo dnf install hugo		# Installation
hugo new site my-site		# Creating a new website
cd my-site			# Navigate to new site
git init			# Add a theme (ex: themes/ananke)
git submodule add https://github.com/budparr/gohugo-theme-ananke.git
hugo server			# Launch server
```

{% hint style="info" %}
Source : [https://developer.fedoraproject.org/start/sw/web-app/hugo.html](https://developer.fedoraproject.org/start/sw/web-app/hugo.html)
{% endhint %}

### Thèmes

Une sélection de liste de thèmes pour HUGO

* Stack : [https://github.com/CaiJimmy/hugo-theme-stack/](https://github.com/CaiJimmy/hugo-theme-stack/)
* Hextra : [https://imfing.github.io/hextra/](https://imfing.github.io/hextra/)

## Flarum

<figure><img src="../../../../.gitbook/assets/flarum-ar21.png" alt="" width="375"><figcaption></figcaption></figure>

Flarum est une plateforme opensource conçue pour créer et gérer des forums communautaires

{% hint style="info" %}
Site : [https://github.com/flarum](https://github.com/flarum/framework)
{% endhint %}

#### Installation

Suivre les étapes ici : [https://docs.flarum.org/install](https://docs.flarum.org/install)

Si l'installation s'avère trop complexe, vous pouvez créer votre forum en quelques secondes sur [**Free Flarum**](https://www.freeflarum.com), un service communautaire (qui n'est pas affilié à l'équipe en chage de Flarum)

### Themes

Une sélection de liste de thèmes pour Flarum

* BetterFLarum - Next Admin UI : [https://github.com/betterflarum/nextadmintheme](https://github.com/betterflarum/nextadmintheme)
* Asirem : [https://github.com/afrux/asirem](https://github.com/afrux/asirem)
* Flarum-theme-fedora-fr : [https://github.com/Fedora-Fr/flarum-theme-fedora-fr](https://github.com/Fedora-Fr/flarum-theme-fedora-fr)
* OXO theme : [https://github.com/yannisme/flarum-oxo-theme](https://github.com/yannisme/flarum-oxo-theme)
