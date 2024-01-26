# 🎵 Audio

## YouTube Music Desktop

{% hint style="danger" %}
Il ne s'agit pas d'une version officiel maintenu par Google
{% endhint %}

### Installation via Snapcraft

{% hint style="info" %}
Pré-requis : **Snapd** est nécéssaire
{% endhint %}

```bash
sudo dnf install snapd
```

```bash
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install youtube-music-desktop-app
```

Source : [https://snapcraft.io/install/youtube-music-desktop-app/fedora](https://snapcraft.io/install/youtube-music-desktop-app/fedora)

### Installation avec un paquet RPM

{% hint style="info" %}
Vérifier la denrière version en date sur [https://github.com/th-ch/youtube-music/releases](https://github.com/th-ch/youtube-music/releases)
{% endhint %}

#### Télécharger le fichier RPM le plus récent

```bash
wget https://github.com/th-ch/youtube-music/releases/download/v1.18.0/youtube-music-1.18.0.x86_64.rpm
```

#### Installation du paquet

```bash
sudo dnf install https://github.com/th-ch/youtube-music/releases/download/v1.18.0/youtube-music-1.18.0.x86_64.rpm
```

***

## Foobar2000

{% hint style="info" %}
Pré-requis : **Snapd** est nécéssaire
{% endhint %}

```bash
sudo dnf install snapd
```

```bash
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install foobar2000
```

{% hint style="info" %}
Source : [https://snapcraft.io/install/foobar2000/fedora](https://snapcraft.io/install/foobar2000/fedora)
{% endhint %}
