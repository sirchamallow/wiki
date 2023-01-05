---
description: Tools pour devs sous Fedora
---

# ⛓ Git

## Installation

```bash
sudo dnf install git-all # Install Git
git version              # Check your git version
```

## Autocomplétion

### Activer autocomplétion des commandes

Activer la correction automatique pour les commandes Git

{% hint style="info" %}
Vous devez attribuer une valeur au paramètre de configuration help.autocorrect.
{% endhint %}

```bash
git config --global help.autocorrect 1
```

### Désactiver la correction automatique

```bash
git config --global --unset help.autocorrect
```

## GitHub CLI

```bash
sudo dnf install 'dnf-command(config-manager)'
sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
sudo dnf install gh
sudo dnf update gh
```

Source : [https://cli.github.com/manual/installation](https://cli.github.com/manual/installation)

###

###
