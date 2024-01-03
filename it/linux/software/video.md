---
description: Des outils de vidéos
---

# 📺 Video

## VLC

#### Description

VLC (VideoLAN Client) est un lecteur multimédia open source. \
Il est capable de lire une large gamme de formats audio et vidéo, y compris les fichiers multimédias locaux, les flux réseau, les DVD, les CD audio, et même les flux de diffusion en continu.&#x20;

VLC est apprécié pour sa compatibilité étendue, sa simplicité d'utilisation, sa légèreté et sa capacité à fonctionner sur plusieurs plates-formes, notamment Windows, macOS, Linux, Android et iOS. En outre, il est connu pour son support des codecs variés, éliminant ainsi le besoin d'installer des codecs tiers.

#### Installation&#x20;

```bash
su -
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install vlc
```

{% hint style="info" %}
Source : [https://www.videolan.org/vlc/download-fedora.html](https://www.videolan.org/vlc/download-fedora.html)
{% endhint %}

## YouTube-DL

#### Description

Youtube-dl est un utilitaire en ligne de commande open source qui permet de télécharger des vidéos depuis de nombreuses plateformes de diffusion en ligne, telles que YouTube, Vimeo, Dailymotion, et bien d'autres

L'outil est écrit en Python et fonctionne sur divers systèmes d'exploitation, notamment Windows, macOS et Linux. \
L'utilisation de `youtube-dl` est relativement simple : vous fournissez l'URL de la vidéo que vous souhaitez télécharger en ligne de commande, et l'outil se charge du téléchargement en extrayant la vidéo dans le format disponible de la meilleure qualité possible.

#### Installation

{% hint style="danger" %}
Il ne s'agit pas d'une version officiel maintenu par Google
{% endhint %}

```bash
sudo dnf install python-pip
```

{% hint style="info" %}
**Pré-requis :** python package manager (pip) est requis pour l'installation
{% endhint %}

```bash
sudo pip install youtube-dl              # Installation
sudo pip install --upgrade youtube-dl    # Mise à jour
sudo pip uninstall youtube-dl            # Désinstallation
```

{% hint style="info" %}
Source : [https://lintut.com/install-youtube-dl-on-linux-and-how-to-use-it/](https://lintut.com/install-youtube-dl-on-linux-and-how-to-use-it/)
{% endhint %}

## YouTubeDL-GUI

<figure><img src="../../../.gitbook/assets/Capture d’écran du 2022-11-08 16-55-08.png" alt=""><figcaption><p>Youtube Downloader</p></figcaption></figure>

```bash
flatpak install flathub io.github.JaGoLi.ytdl_gui
```

## OBS Studio

<figure><img src="../../../.gitbook/assets/hero.png" alt=""><figcaption></figcaption></figure>

#### Description

OBS Studio (Open Broadcaster Software Studio), est un logiciel open source et gratuit conçu pour l'enregistrement vidéo et la diffusion en direct. Il offre des fonctionnalités avancées pour la capture de contenu à partir de différentes sources, telles que des webcams, des fenêtres d'application, des captures d'écran, des cartes de capture et plus encore.

#### Installation

```bash
sudo dnf install obs-studio       # OBS Studio
sudo dnf install obs-studio-devel # OBS Studio’s development packages
```

{% hint style="info" %}
Source : [https://github.com/obsproject/obs-studio](https://github.com/obsproject/obs-studio)
{% endhint %}

{% hint style="success" %}
Site internet : [https://obsproject.com/fr](https://obsproject.com/fr)
{% endhint %}
