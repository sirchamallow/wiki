# 📺 Video

## VLC

```bash
su -
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install vlc
```

Source : [https://www.videolan.org/vlc/download-fedora.html](https://www.videolan.org/vlc/download-fedora.html)

## YouTube-DL

{% hint style="danger" %}
Il ne s'agit pas d'une version officiel maintenu par Google
{% endhint %}

{% hint style="info" %}
**Pré-requis :** python package manager (pip) est requis pour l'installation
{% endhint %}

```bash
sudo dnf install python-pip
```

### Installation

```bash
sudo pip install youtube-dl
```

### Mise à jour

```bash
sudo pip install --upgrade youtube-dl
```

### Désinstallation

```bash
sudo pip uninstall youtube-dl
```

{% hint style="info" %}
Source : [https://lintut.com/install-youtube-dl-on-linux-and-how-to-use-it/](https://lintut.com/install-youtube-dl-on-linux-and-how-to-use-it/)
{% endhint %}

## YouTubeDL-GUI

<figure><img src="../../../../.gitbook/assets/Capture d’écran du 2022-11-08 16-55-08.png" alt=""><figcaption><p>Youtube Downloader</p></figcaption></figure>

### Installation

```bash
flatpak install flathub io.github.JaGoLi.ytdl_gui
```

