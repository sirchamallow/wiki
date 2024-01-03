---
description: Des outils de vidéos
---

# 📺 Video

## VLC

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
