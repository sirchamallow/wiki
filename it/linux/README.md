---
description: Linux
---

# 🐧 Fedora Workstation

## Présentation

Fedora Linux est un système d’exploitation libre et une distribution Linux communautaire développée par le projet Fedora et sponsorisée par l’entreprise Red Hat, qui lui fournit des développeurs ainsi que des moyens financiers et logistiques. ([Wikipedia](https://fr.wikipedia.org/wiki/Fedora\_Linux))

### Navigation

{% content-ref url="astuces.md" %}
[astuces.md](astuces.md)
{% endcontent-ref %}

{% content-ref url="dev-tools/" %}
[dev-tools](dev-tools/)
{% endcontent-ref %}

{% content-ref url="software/" %}
[software](software/)
{% endcontent-ref %}

{% content-ref url="gnome-extensions.md" %}
[gnome-extensions.md](gnome-extensions.md)
{% endcontent-ref %}

{% content-ref url="hardware/" %}
[hardware](hardware/)
{% endcontent-ref %}

## Commandes des bases

Voici une liste de commandes de bases pour Linux (pas spécifique à Fedora)

### Renommer un fichier ou un répertoire

Voic un exemple pour renommer un fichier/répertoire du nom de "paris" en "lyon":

```bash
mv paris lyon
```

### Déplacer un fichier ou répertoire

Voici comment déplacer un fichier/répertoire du dossier courant vers le répertoire distant "/home/georges/Bureau" :

```bash
mv lyon /home/georges/Bureau
```

### Déplacer tout les fichiers/répertoires

On va déplacer tout les fichiers/répertoires du dossier courant vers le répertoire distant "/home/georges/Bureau/marseille":

```bash
mv * /home/georges/Bureau/marseille
```
