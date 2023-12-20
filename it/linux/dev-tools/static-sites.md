---
description: Pour faire des sites statiques :)
---

# 🏠 Static Sites

## Jekyll

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

## Hugo

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

Liste de thèmes pour HUGO

* Stack : [https://github.com/CaiJimmy/hugo-theme-stack/](https://github.com/CaiJimmy/hugo-theme-stack/)
* Hextra : [https://imfing.github.io/hextra/](https://imfing.github.io/hextra/)

## Flarum

Flarum est une plateforme opensource conçue pour créer et gérer des forums communautaires

#### Installation

Suivre les étapes ici : [https://docs.flarum.org/install](https://docs.flarum.org/install)

Si l'installation s'avère trop complexe, vous pouvez créer votre forum en quelques secondes sur [**Free Flarum**](https://www.freeflarum.com), un service communautaire (qui n'est pas affilié à l'équipe en chage de Flarum)

{% hint style="info" %}
Source : [https://github.com/flarum](https://github.com/flarum/framework)
{% endhint %}
