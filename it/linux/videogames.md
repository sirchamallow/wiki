---
description: Quelques jeux disponibles sur Linux
---

# 🕹 Jeux vidéos

## OpenRCT2

<figure><img src="../../.gitbook/assets/OpenRCT2-Game-Logo.png" alt=""><figcaption></figcaption></figure>

OpenRCT2 est un jeu vidéo de simulation de construction et de gestion qui simule la gestion d'un parc d'attractions. Il s'agit d'une réimplémentation et d'une extension gratuites et open-source du jeu vidéo **RollerCoaster Tycoon 2** de 2002.

### Installation des dépendances

```bash
sudo dnf install gcc gcc-c++ json-devel \\
openssl-devel SDL2-devel libicu-devel \\
speexdsp-devel libcurl-devel \\
cmake fontconfig-devel freetype-devel \\
libpng-devel libzip-devel mesa-libGL-devel \\
duktape-devel
```

### Compiler le jeu

```bash
git clone --depth=1 https://github.com/OpenRCT2/OpenRCT2.git && cd ./OpenRCT2 && mkdir build && cd build && cmake ../ && make
```

### Paramétrages des fichiers

```bash
cp -r ../data/ ./data/ && make g2 && mv ./g2.dat ./data/g2.dat
```

### Sélection du dossier d'installation pour le jeu

```bash
openrct2 set-rct2 /path/to/rct2-install
```

Source : [https://openrct2.org/quickstart/install/linux/fedora](https://openrct2.org/quickstart/install/linux/fedora)

## OpenTTD

<figure><img src="../../.gitbook/assets/openttd.jpg" alt=""><figcaption></figcaption></figure>

**OpenTTD** est un jeu vidéo de « gestion et planification urbanistique » dans lequel le joueur a pour but de gagner de l'argent par transport de passagers et du fret sur route, rail, eau et dans l'air. Il est une réécriture libre du jeu original Transport Tycoon Deluxe de Chris Sawyer, sorti en 1995. [Wikipédia](https://fr.wikipedia.org/wiki/OpenTTD)

### Installation via Snapcraft

{% hint style="info" %}
Pré-requis : **Snapd** est nécéssaire
{% endhint %}

```bash
sudo dnf install snapd
```

```bash
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install openttd
```

{% hint style="info" %}
Source : [https://snapcraft.io/install/openttd/fedora](https://snapcraft.io/install/openttd/fedora)
{% endhint %}

{% hint style="success" %}
Site internet : [https://www.openttd.org/](https://www.openttd.org/)
{% endhint %}

