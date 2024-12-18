---
icon: box-open
description: Liste de dépôts
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Dépôts

## RPM Fusion

<figure><img src="../../../../.gitbook/assets/rpm_fusion.png" alt="" width="250"><figcaption></figcaption></figure>

#### Description

RPM  est un système de gestion de paquets utilisés par certaines distributions GNU/Linux : CentOS, Fedora, OpenSuse, Mageia.&#x20;

{% hint style="info" %}
Notes: un paquet RPM ne gère pas les dépendances.
{% endhint %}

Par défaut, les dépôts de Fedora ne contiennent pas tous les logiciels. \
Il est ainsi parfois nécéssaire d'avoir de drivers propriétaires, autres codecs ou logiciels non libres.&#x20;

Du coup, il faut passer par un dépôt qui disposent de plus de logiciels. [\
RPM Fusion](https://rpmfusion.org) est un des ces dépôts incontournable.

### Installation

Il propose deux dépôts : _**free**_ (contient des logiciels libres non packagés par la communauté Fedora) & _**non-free**_ (contient des logiciels propriétaires non packagés par la communauté Fedora)

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm           # RPM Fusion free
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-relbasease-$(rpm -E %fedora).noarch.rpm  # RPM Fusion non-free  
```

### Mise à jour

```bash
sudo dnf update
```

### AppStream medatda

Les dépôts RPM Fusion fournissent également des métadonnées [Appstream](https://www.freedesktop.org/wiki/Distributions/AppStream/) pour permettre aux utilisateurs d'installer des paquets en utilisant Gnome Software/KDE Discover.

```bash
sudo dnf groupupdate core
```

{% hint style="info" %}
Source : [https://rpmfusion.org/Configuration](https://rpmfusion.org/Configuration)
{% endhint %}

### Cheatsheet

* **`rpm -i`** : installer
* **`rpm -e`** : supprimer
* **`rpm -U`** : mettre à jour
* **-v`h`** : En mode verbeux, et avec une barre de progression.
* **`rpm -E %{macro}`** : donne la valeur de la macro ( rpm -E %{\_lib} )

***

## Flatpak

<figure><img src="https://fedoramagazine.org/wp-content/uploads/2018/03/flathub.png" alt="" width="375"><figcaption></figcaption></figure>

**Flatpak** est un système de virtualisation d’application pour les distributions GNU/Linux de bureau.\
Il fournit un environnement isolé du reste du système (_sandbox_), où l'utilisateur peut faire fonctionner des applications de manière sûre.  Les paquets logiciels flatpak **fonctionnant sur toutes les distributions linux** :clap:&#x20;

On trouve les logiciels sur le principal dépôt (**Flathub**). \
Certains ne sont même parfois disponibles que dans ce format.\
\
Bonne nouvelle, Flatpak est installé par défaut sur Fedora Workstation :)&#x20;

{% hint style="success" %}
Pour télécharger des applications, [rendez-vous sur **Flathub**](https://flathub.org/)
{% endhint %}

#### Installation manuel

Si pour une raison quelquonque ça ne marche pas, vous pouvez ajouter manuellement la télécommande **Flathub** en exécutant :

```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

***

## Snap

<figure><img src="https://assets.ubuntu.com/v1/4726d040-Snap+logo+white+bg.jpg" alt="" width="375"><figcaption></figcaption></figure>

#### Description

Le format _snap_ vise à permettre l'installation de nouvelles versions de logiciels dans les systèmes _Linux._ Celui-ci est propulsé par Canonical Ltd. qui est l'entreprise qui édite la distribution Ubuntu.

#### Installation

```bash
sudo dnf install snapd
```

{% hint style="info" %}
Source : [https://snapcraft.io/docs/installing-snap-on-fedora](https://snapcraft.io/docs/installing-snap-on-fedora)
{% endhint %}

### Exemple de commandes de base <a href="#exemple-de-commandes-de-base" id="exemple-de-commandes-de-base"></a>

* Installer un paquet : `sudo snap install <nom_du_snap>`
* Lister les paquets installés : `sudo snap list`
* Mettre à jour les snaps : `sudo snap refresh`
* Supprimer un paquet : `sudo snap remove <nom_du_snap>`

### Commandes avancées <a href="#commandes-avancees" id="commandes-avancees"></a>

* Changer le cannal du snap (beta, stable, ...) : `sudo snap install <nom_du_snap> -channel=<cannal_souhaité>`
* Repasser le snap sur le cannal stable : `sudo snap revert <nom_du_snap>`

***

## AppImage

#### **Description**

**AppImage est un format de paquet de logiciel** qui permet aux développeurs de distribuer leurs applications sous la forme d’un **fichier unique.** Les fichiers de ce format sont autonomes et contiennent toutes les dépendances dont l’application a besoin pour fonctionner.&#x20;

Particularité, ils peuvent être exécutés sur n’importe quelle distribution Linux sans nécessiter les privilèges de l’administrateur. Ce format de fichier est portable, c’est à dire qu’il n’installe aucun fichier dans le système et ne dépend d’aucune dépendance du système.

### Comment lancer une AppImage ?

```bash
chmod a+x Subsurface*.AppImage # Rendre votre AppImage éxécutable
./Subsurface*.AppImage         # Lancer votre AppImage
```

### Comment simplifier l'installation de mes AppsImages ?

Pour cela, vous pouvez utiliser _AppImage Launcher_ et télécharger la dernière version disponible sur le repo GitHub. Notes, chercher ceux avec `.rpm` pour les systèmes basés sur Fedora.

{% hint style="info" %}
Source : [https://github.com/TheAssassin/AppImageLauncher/releases](https://github.com/TheAssassin/AppImageLauncher/releases)
{% endhint %}

* Installez le paquet téléchargé à l'aide du gestionnaire de paquets de Fedora.&#x20;
* exécutez ensuite `sudo dnf install appimagelauncher_<version>.rpm`&#x20;

### Ou trouver des fichiers AppImages ?

Une liste complète des AppImages disponibles au téléchargement peut être consultée sur le site [**AppImage Hub**](https://appimage.github.io/apps/).

{% embed url="https://appimage.github.io/apps/" %}
