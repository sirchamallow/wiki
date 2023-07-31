---
description: Liste d'utilitaires
---

# 🛠 Utilitaires

## CPU-X

Il s'agit d'un **logiciel gratuit qui recueille des informations sur le processeur, la carte mère etc.** CPU-X est similaire à [CPU-Z](https://es.wikipedia.org/wiki/CPU-Z) (_Windows_), à la différence que celui-ci est un logiciel libre et open source conçu pour GNU / Linux.

```bash
sudo dnf install cpu-x
```

Source : [https://itsfoss.com/cpu-x-alternative-cpu-z-linux/](https://itsfoss.com/cpu-x-alternative-cpu-z-linux/)

## P7zip

[p7zip](http://p7zip.sourceforge.net/) est un portage de [7-Zip](http://www.7-zip.org/) pour les systèmes [POSIX](http://fr.wikipedia.org/wiki/POSIX) incluant GNU/Linux. \
Il permet entre autres d'extraire les archives ZIP, GZIP, TAR, GZIP, DEB et RPM.

```bash
sudo dnf install p7zip
```

## GParted

Parmi les différents éditeurs de partitions pour Linux, ma préférance va pour GParted. \
Il est multi-plateforme (Linux, Windows, Mac OS X) et simple d'utilisation. Il même possible d'en faire une version Live CD/USB. Bien pratique pour dépanner.\


```bash
su -c "yum install gparted"
```

Source : [GParted](https://gparted.org/download.php)

## GPaste

Il s'agit d'une extension qui permet aux utilisateurs de gérer le contenu et l’historique du presse-papier, grâce à une icône située dans le panel supérieur de gnome. Vous pourrez ainsi copier rapidement du texte, des url, des images, des lignes de commande et tout un tas d’autres choses.

#### Mise à jour du cache

{% hint style="info" %}
Télécharger d'abord et mettre en cache les fichiers de métadonnées du référentiel
{% endhint %}

```bash
sudo dnf makecache --refresh
```

#### Installation

Ensuite, procéder à l'installation

```bash
sudo dnf -y install gpaste
```

Source : [https://installati.one/fedora/34/gpaste/](https://installati.one/fedora/34/gpaste/)

## KolourPaint

KolourPaint est logiciel de dessin simple qui permet de créer rapidement des images. Il est pratique pour retoucher ou modifier simplement des images.

#### Installation via [AppStream](appstream://org.kde.kolourpaint)

#### Installation via Flatpak

```bash
flatpak install flathub org.kde.kolourpaint
```

#### Installation via Snapcraft

{% hint style="info" %}
Pré-requis : **Snapd** est nécéssaire
{% endhint %}

```bash
sudo dnf install snapd
```

```bash
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install kolourpaint
```

{% hint style="info" %}
Source : [https://apps.kde.org/fr/kolourpaint/](https://apps.kde.org/fr/kolourpaint/)
{% endhint %}

{% hint style="success" %}
Site internet : [https://www.kolourpaint.org/](https://www.kolourpaint.org/)
{% endhint %}

## Htop

**htop** est un moniteur système pour les systèmes d’exploitation type Unix très similaire à **top**, qui fonctionne également en mode Terminal, mais qui dispose d'un environnement en mode texte plus convivial que ce dernier.

**Installation**

```bash
sudo dnf install htop
```

{% hint style="info" %}
Source : [https://htop.dev/downloads.html](https://htop.dev/downloads.html)
{% endhint %}

## Discord

```bash
sudo dnf update
sudo dnf install discord
```

{% hint style="info" %}
Source : [https://itsfoss.com/install-discord-fedora/](https://itsfoss.com/install-discord-fedora/)
{% endhint %}

#### Désactiver le pop de mise à jour automatique (parfois bloquant)

Ouvrer le fichier `settings.json` qui se trouve dans le dossier `.config/discord/`\
et ajouter la valeur suivante : `"SKIP_HOST_UPDATE": true`

## Facebook Messenger

{% hint style="info" %}
Il n'existe pas de package linux pour **FB Messenger**, en lieu et place nous utiliserons **Caprine.** Une application non officielle disponible sur _SnapCraft_, axée sur la vie privée avec de nombreuses fonctionnalités utiles.
{% endhint %}

```bash
sudo dnf install snapd                # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap  # Enable classic snap support, enter the following to create a symbolic link
sudo snap install caprine             # Install Caprine
```

Source : [https://www.zdnet.com/article/how-to-get-a-facebook-messenger-client-on-linux/](https://www.zdnet.com/article/how-to-get-a-facebook-messenger-client-on-linux/)

## VirtualBox

Édité et distribué gratuitement pour une utilisation personnelle par _Oracle_, VirtualBox est un **hyperviseur type 2** permettant de créer une machine virtuelle en quelques clics.

{% hint style="warning" %}
Ce guide d'installation est pour la version 36 de Fedora
{% endhint %}

```bash
## Recommended to perform OS upgrade before you install VirtualBox #
sudo dnf -y upgrade
sudo reboot

## Install Dependencies
sudo dnf -y install @development-tools
sudo dnf -y install kernel-headers kernel-devel dkms elfutils-libelf-devel qt5-qtx11extras

## Add VirtualBox RPM repository
cat <<EOF | sudo tee /etc/yum.repos.d/virtualbox.repo 
[virtualbox]
name=Fedora $releasever - $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/fedora/36/\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc
EOF

## Import VirtualBox GPG Key
sudo dnf search virtualbox

## Install VirtualBox 7.0 on Fedora 36
sudo dnf install VirtualBox-7.0

## Add your user to the vboxusers group
sudo usermod -a -G vboxusers $USER
newgrp vboxusers
id $USER
uid=1000(jmutai) gid=1000(jmutai) groups=1000(jmutai),10(wheel),976(vboxusers)

## Launch VirtualBox
virtualbox
```

Source : [https://computingforgeeks.com/how-to-install-virtualbox-on-fedora-linux/](https://computingforgeeks.com/how-to-install-virtualbox-on-fedora-linux/)

## Bleachbit

Un utilitaire open-source pour libérer le cache, supprimer les cookies, effacer l'historique d'Internet, déchiqueter des fichiers temporaires, supprimer des journaux etc. \
Disponible sur Linux et Windows.

{% hint style="info" %}
Source : [https://www.bleachbit.org/download](https://www.bleachbit.org/download)
{% endhint %}

## Stacer

Un utilitaire d'optimisation et de monitoring open-source pour Linux avec un GUI.

{% hint style="info" %}
Source : [https://github.com/oguzhaninan/Stacer/releases](https://github.com/oguzhaninan/Stacer/releases)
{% endhint %}
