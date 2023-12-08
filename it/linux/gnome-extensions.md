---
description: Liste d'extensions pour GNOME
---

# 👣 Ext. GNOME

## Présentation

[GNOME Extensions](https://gitlab.gnome.org/GNOME/gnome-shell-extensions) est une petite application pour gérer les extensions Shell de GNOME.

{% hint style="info" %}
Si **Extensions** n'est pas déjà installé sur votre système GNOME, je vous recommande de le télécharger depuis [Flathub](https://flathub.org/apps/details/org.gnome.Extensions).
{% endhint %}

## Téléchargement

{% hint style="success" %}
Les extensions sont disponibles sur [https://extensions.gnome.org/](https://extensions.gnome.org/)
{% endhint %}

## Extensions

### Vitals

Vitals est une extension de GNOME Shell pour afficher la température, la tension, la vitesse du ventilateur, l'utilisation de la mémoire, la charge de traitement, les ressources du système, la vitesse du réseau et les statistiques de stockage dans la barre de menu supérieure de votre GNOME Shell.

<figure><img src="../../.gitbook/assets/Vitals.GIF" alt=""><figcaption></figcaption></figure>

#### Installation

```bash
sudo dnf install libgtop2-devel lm_sensors
```

#### Activation

Rendez-vous ensuite sur [le site web de Gnome Extensions](https://extensions.gnome.org/extension/1460/vitals/), recherchez **Vitals** et cliquez sur l'icône switch.

{% hint style="success" %}
À ce stade, Vitals devrait fonctionner. Si vous inversez les étapes 1 et 2 ci-dessus, vous devrez redémarrer votre session en vous déconnectant, puis à nouveau.
{% endhint %}

{% hint style="info" %}
Source : [https://github.com/corecoding/Vitals](https://github.com/corecoding/Vitals)
{% endhint %}

### Dash to Dock for COSMIC

Un fork de Dash to Dock. Un dock pour bureau sur Linux.

<figure><img src="../../.gitbook/assets/screenshot (2).jpg" alt=""><figcaption></figcaption></figure>

#### Installation & Activation

Rendez-vous sur [le site web de Gnome Extensions](https://extensions.gnome.org), recherchez [**Dash to Dock for COSMIC**](https://extensions.gnome.org/extension/5004/dash-to-dock-for-cosmic/) et cliquez sur l'icône switch.

{% hint style="info" %}
Source : [https://github.com/halfmexican/dash-to-dock-pop/tree/ubuntu-dock](https://github.com/halfmexican/dash-to-dock-pop/tree/ubuntu-dock)
{% endhint %}

### Media Controls

Affiche les contrôles et les informations du média en cours de lecture dans le panneau.

<figure><img src="../../.gitbook/assets/mediacontrols.png" alt=""><figcaption></figcaption></figure>

#### Installation

```bash
sudo dnf install gnome-shell-extension-mediacontrols
```

#### Activation

Rendez-vous ensuite sur le [site web de Gnome Extensions](https://extensions.gnome.org/), recherchez [**Media Controls**](https://extensions.gnome.org/extension/4470/media-controls/) et cliquez sur l'icône switch.

{% hint style="info" %}
Source : [https://github.com/cliffniff/media-controls/](https://github.com/cliffniff/media-controls/blob/main/README.md)
{% endhint %}

### NVIDIA GPU Stats Tool <a href="#extension_name" id="extension_name"></a>

Affiche les statistiques du GPU NVIDIA dans la barre d'outils.&#x20;

{% hint style="warning" %}
Pré-requis : Nécessite [nvidia-settings](https://download.nvidia.com/XFree86/Linux-x86\_64/396.51/README/nvidiasettings.html) ou [nvidia-smi](https://download.nvidia.com/XFree86/Linux-x86\_64/396.51/README/nvidia-smi.html).
{% endhint %}

{% hint style="info" %}
Inclut le support de [Bumblebee](https://www.bumblebee-project.org/).
{% endhint %}

<figure><img src="../../.gitbook/assets/nvidia-gpu_stats.png" alt=""><figcaption></figcaption></figure>

#### Activation

Rendez-vous sur le site web de [Gnome Extensions](https://extensions.gnome.org/), recherchez [**Nvidia GPU Stats Tool**](https://extensions.gnome.org/extension/1320/nvidia-gpu-stats-tool) et cliquez sur l'icône switch.

{% hint style="info" %}
Source : [https://github.com/ethanwharris/gnome-nvidia-extension](https://github.com/ethanwharris/gnome-nvidia-extension)
{% endhint %}

### Clipboard Indicator

Extension du gestionnaire du presse-papiers pour Gnome.\
Ajoute un indicateur du presse-papiers dans le panneau supérieur et met en cache l'historique du presse-papiers.

<figure><img src="../../.gitbook/assets/screenshot_779_z38Ay1y.png" alt=""><figcaption></figcaption></figure>

#### Installation

#### Option 1 - Installation via git

L'installation via git s'effectue en clonant le dépôt dans votre répertoire local des extensions de gnome-shell (généralement \~/.local/share/gnome-shell/extensions/)

```bash
git clone https://github.com/Tudmotu/gnome-shell-extension-clipboard-indicator.git <extensions-dir>/clipboard-indicator@tudmotu.com
```

Après avoir cloné le repo, l'extension est pratiquement installée mais désactivée. \
Afin de l'activer, exécutez la commande suivante :

```bash
gnome-extensions enable clipboard-indicator@tudmotu.com
```

#### Option 2 - Installation depuis GNOME Extensions

Rendez-vous sur le site web de [Gnome Extensions](https://extensions.gnome.org/), recherchez **Clipboard Indicator** et cliquez sur l'icône switch.

{% hint style="info" %}
Source : [https://github.com/Tudmotu/gnome-shell-extension-clipboard-indicator](https://github.com/Tudmotu/gnome-shell-extension-clipboard-indicator)
{% endhint %}

### Just Perfection GNOME Shell Extension

Désactiver les éléments de l'interface utilisateur de GNOME, modifier le comportement et personnaliser votre bureau GNOME.

<figure><img src="../../.gitbook/assets/Juste_perfection.svg" alt=""><figcaption></figcaption></figure>

#### Activation

Rendez-vous sur le site web de [Gnome Extensions](https://extensions.gnome.org/extension/3843/just-perfection/), recherchez [**Just Perfection**](https://extensions.gnome.org/extension/3843/just-perfection/) et cliquez sur l'icône switch

{% hint style="info" %}
Source : [https://gitlab.gnome.org/jrahmatzadeh/just-perfection](https://gitlab.gnome.org/jrahmatzadeh/just-perfection)
{% endhint %}

### Tray Icons: Reloaded <a href="#extension_name" id="extension_name"></a>

Ramène les icônes de plateau au panneau supérieur, avec des fonctionnalités supplémentaires.\


<figure><img src="../../.gitbook/assets/screenshot_2890.png" alt=""><figcaption></figcaption></figure>

#### Activation

Rendez-vous sur le site web de [Gnome Extensions](https://extensions.gnome.org/extension/2890/tray-icons-reloaded/), recherchez [Tray Icons: Reloaded](https://app.gitbook.com/s/Pp6PcTwYyYLWwFxkG4Q4/the-basics/change-requests) et cliquez sur l'icône switch

{% hint style="info" %}
Source : [https://github.com/MartinPL/Tray-Icons-Reloaded](https://github.com/MartinPL/Tray-Icons-Reloaded)
{% endhint %}

#### &#x20;<a href="#extension_name" id="extension_name"></a>

