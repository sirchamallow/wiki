---
description: Pour faire des sites statiques :)
icon: globe-pointer
---

# Static Sites

## Jekyll

{% embed url="https://jekyllrb.com/docs/installation/" %}

```bash
# Pré-requis
sudo dnf install ruby ruby-devel openssl-devel redhat-rpm-config gcc-c++ @development-tools

# Ajout des variables d'environnement à votre ~/.bashrc pour config chemin d'installation gems
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

gem install jekyll bundler  # Installation gem jekyll
jekyll new my-site 		      # Create new site
cd my-site			            # Navigate to new site
jekyll serve			          # Launch server (http://localhost:4000)
```

***

## Hugo

{% embed url="https://gohugo.io/" %}

```bash
sudo dnf install hugo		# Installation
hugo new site my-site		# Creating a new website
cd my-site			        # Navigate to new site
git init			          # Add a theme (ex: themes/ananke)
git submodule add https://github.com/budparr/gohugo-theme-ananke.git
hugo server			        # Launch server
```

### Thèmes

Une sélection de liste de thèmes pour HUGO

* Stack : [https://github.com/CaiJimmy/hugo-theme-stack/](https://github.com/CaiJimmy/hugo-theme-stack/)
* Hextra : [https://imfing.github.io/hextra/](https://imfing.github.io/hextra/)

***

### Astro

{% embed url="https://docs.astro.build/en/install-and-setup/" %}

{% embed url="https://github.com/withastro/astro" %}
