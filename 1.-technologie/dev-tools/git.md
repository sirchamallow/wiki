---
description: Tools pour devs sous Fedora
icon: git
---

# Git

## Git

Logiciel de versionning

{% embed url="https://git-scm.com/download/linux" %}

#### Installation

```bash
sudo dnf install git-all # Install Git
git version              # Check your git version
```

### Autocomplétion

#### Activer autocomplétion des commandes

Activer la correction automatique pour les commandes Git

{% hint style="info" %}
Vous devez attribuer une valeur au paramètre de configuration help.autocorrect.
{% endhint %}

```bash
git config --global help.autocorrect 1
```

#### Désactiver la correction automatique

```bash
git config --global --unset help.autocorrect
```

***

## GitHub CLI

GitHub CLI est un outil open source pour utiliser GitHub depuis votre terminal.

```bash
sudo dnf install 'dnf-command(config-manager)'
sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
sudo dnf install gh
sudo dnf update gh
```

{% embed url="https://github.com/cli/cli/blob/trunk/docs/install_linux.md#fedora-centos-red-hat-enterprise-linux-dnf" %}

***

## Gac

Un script permettant de faire une commande `git add -A && git commit -m "message"` plus rapidement :)

{% embed url="https://github.com/devpolo/gac" %}

### Commandes disponible

```bash
gac                     # print available semantics
gac c <your message>    # git add -A && git commit -m "chore: <your message>"
gac d <your message>    # git add -A && git commit -m "docs: <your message>"
gac f <your message>    # git add -A && git commit -m "feat: <your message>"
gac r <your message>    # git add -A && git commit -m "refactor: <your message>"
gac s <your message>    # git add -A && git commit -m "style: <your message>"
gac t <your message>    # git add -A && git commit -m "test: <your message>"
gac x <your message>    # git add -A && git commit -m "fix: <your message>"
gac <your message>      # git add -A && git commit -m "<your message>"
```
