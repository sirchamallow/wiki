---
description: Liste de logiciels
---

# 🕸 Internet

## Navigateurs Web

### Mozilla Firefox

#### Firefox



<figure><img src="../../../.gitbook/assets/Capture d’écran du 2024-01-08 16-48-23.png" alt=""><figcaption></figcaption></figure>

```bash
sudo dnf install firefox
```

{% hint style="info" %}
Source : [https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems](https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems)
{% endhint %}

#### Firefox Developer Edition

<figure><img src="../../../.gitbook/assets/Capture d’écran du 2024-01-08 16-52-39.png" alt="" width="320"><figcaption></figcaption></figure>

```bash
sudo dnf copr enable the4runner/firefox-dev # Enable the4runner/firefox-dev Copr repository according to your package manager.
sudo dnf check-update                       # (Optionnal)
sudo dnf install firefox-dev                # Install Firefox Dev
firefox-dev                                 # Launch Firefox Dev
```

{% hint style="info" %}
Source : [https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/](https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/)
{% endhint %}

#### Extensions & Themes

{% content-ref url="../../../tech/software/browsers/firefox-extensions/" %}
[firefox-extensions](../../../tech/software/browsers/firefox-extensions/)
{% endcontent-ref %}

### Google Chrome

#### Google Chrome

<figure><img src="../../../.gitbook/assets/Capture d’écran du 2024-01-08 16-48-07.png" alt=""><figcaption></figcaption></figure>

```bash
sudo dnf install fedora-workstation-repositories	# Install Third Party Repositories
sudo dnf config-manager --set-enabled google-chrome	# Enable the Google Chrome repo
sudo dnf install google-chrome-stable			# Install Google Chrome
```

{% hint style="info" %}
Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/](https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/)
{% endhint %}

#### Google Chrome Developers

<figure><img src="../../../.gitbook/assets/unnamed.png" alt="" width="300"><figcaption></figcaption></figure>

```bash
sudo dnf install google-chrome-unstable
```

{% hint style="info" %}
Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/](https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/)
{% endhint %}

### **Ungoogled Chromium**

<figure><img src="../../../.gitbook/assets/Ungoogled-Chromium.webp" alt="" width="289"><figcaption></figcaption></figure>

_Ungoogled Chromium_ est un navigateur qui conserve l’expérience utilisateur par défaut de **Chromium** mais sans les dépendances aux services web de Google (comme Google Host Detector, Google URL Tracker, Google Cloud Messaging, Google Hotwording, etc.), tout en offrant des tas d’options pour améliorer la confidentialité et le contrôle de vos données.

{% hint style="info" %}
La version RPM / DNF n'est plus maintenu.
{% endhint %}

{% hint style="warning" %}
Vous pouvez la télécharger depuis le repo [https://github.com/ungoogled-software/ungoogled-chromium](https://github.com/ungoogled-software/ungoogled-chromium), et télécharger la version **AppImage** (compatible Fedora).

Second choix, une version **Flatpak** est disponible ici : [https://flathub.org/apps/com.github.Eloston.UngoogledChromium](https://flathub.org/apps/com.github.Eloston.UngoogledChromium)
{% endhint %}

{% hint style="info" %}
Source : [https://github.com/ungoogled-software/ungoogled-chromium-fedora](https://github.com/ungoogled-software/ungoogled-chromium-fedora)
{% endhint %}

### Microsoft Edge



<figure><img src="../../../.gitbook/assets/EdgeNew.jpg" alt="" width="375"><figcaption></figcaption></figure>

Importer la clé GPG pour l'import du fichier RPM:

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

Importer le répertoire de Microsoft Edge

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf config-manager --add-repo https://packages.microsoft.com/yumrepos/edge
</strong></code></pre>

#### Installation Microsoft Edge <a href="#installing-microsoft-edge" id="installing-microsoft-edge"></a>

```bash
sudo dnf install microsoft-edge-stable
```

#### Installation Microsoft Edge dev

```bash
sudo dnf install microsoft-edge-dev
```

{% hint style="info" %}
Notez que celles-ci ne remplacent pas votre version stable, et elles sont installées séparément.
{% endhint %}

{% hint style="info" %}
Source : [https://www.linuxcapable.com/install-microsoft-edge-on-fedora-linux/](https://www.linuxcapable.com/install-microsoft-edge-on-fedora-linux/)
{% endhint %}

## NextDNS

<figure><img src="../../../.gitbook/assets/nextdns.png" alt="" width="375"><figcaption></figcaption></figure>

#### Installation

{% hint style="info" %}
Avant d'aller plus loin dans le guide d'installation, il vous faudra votre user ID (récupérer-le et poursuivez ensuite l'installation)
{% endhint %}

Taper la ligne de commande ci-dessous et suivez les instructions

```bash
sh -c "$(curl -sL https://nextdns.io/install)"
```

#### Installation manuelle

```bash
# Install the binary
sudo curl -Ls https://repo.nextdns.io/nextdns.repo -o /etc/yum.repos.d/nextdns.repo
sudo yum install -y nextdns

# Configuration for a workstation:
sudo nextdns install \
  -config <your config id> \
  -report-client-info \
  -auto-activate

# Configuration for a router/server:
sudo nextdns install \
  -config <your config id> \
  -report-client-info \
  -setup-router
```

#### Basic Usage

```
nextdns start       # Start the daemon
nextdns stop        # Stop the daemon
nextdns restart     # Restart the daemon
nextdns activate    # Activate the local host to point to NextDNS
nextdns desactivate # Desactivate the local host to point to NextDNS
nextdns log         # Show daemon logs
nextdns help        # Show all commands
```

{% hint style="info" %}
Source : [https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution](https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution)
{% endhint %}

## FileZilla

<figure><img src="../../../.gitbook/assets/filezilla-tutorial-pdf.jpg" alt="" width="375"><figcaption></figcaption></figure>

Il s'agit d'un client FTP, FTPS et SFTP, développé sous la licence publique générale GNU.

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf install filezilla
</strong></code></pre>

{% hint style="info" %}
Source : [https://filezilla-project.org/download.php?show\_all=1](https://filezilla-project.org/download.php?show\_all=1)
{% endhint %}

## Client mail

### Thunderbird

<figure><img src="../../../.gitbook/assets/1024x1024@2x.webp" alt="" width="188"><figcaption></figcaption></figure>

Par défaut, Thunderbird est disponible sur le dépôt Fedora et est souvent mis à jour en tant que Flatpak. Utilisez la commande suivante pour installer l'application sur votre système.

```bash
sudo dnf install thunderbird -y
```

{% hint style="info" %}
Source : [https://www.linuxcapable.com/how-to-install-thunderbird-on-fedora-linux/](https://www.linuxcapable.com/how-to-install-thunderbird-on-fedora-linux/)
{% endhint %}

{% hint style="success" %}
Site internet : [https://www.thunderbird.net/fr/](https://www.thunderbird.net/fr/)
{% endhint %}

### Mailspring

<figure><img src="../../../.gitbook/assets/icon-round.png" alt="" width="188"><figcaption></figcaption></figure>

La dernière version de Mailspring est disponible via un paquage RPM [téléchargeable depuis le site web](https://www.getmailspring.com/). Rendez-vous sur la page de téléchargement, sélectionnez "Linux" et cliquez sur "Linux (64-bit .rpm)".&#x20;

Ensuite, ouvrez une fenêtre de terminal et utilisez la commande CD pour le déplacer dans le dossier \~/Downloads.

```bash
cd ~/Downloads
```

Installez le RPM de Mailspring sur votre PC Fedora avec la commande DNF install suivante :

```bash
sudo dnf install mailspring-*.x86_64.rpm -y
```

{% hint style="info" %}
Source : [https://www.addictivetips.com/ubuntu-linux-tips/install-mailspring-on-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-mailspring-on-linux/)
{% endhint %}

{% hint style="success" %}
Site internet :&#x20;
{% endhint %}

## Téléchargement

### Varia

<figure><img src="../../../.gitbook/assets/io.github.giantpinkrobots.varia.svg" alt=""><figcaption></figcaption></figure>

Un gestionnaire de téléchargement avec un GUI moderne adapté à GNOME

```bash
flatpak install flathub io.github.giantpinkrobots.varia
flatpak run io.github.giantpinkrobots.varia
```

{% hint style="info" %}
Source : [https://github.com/giantpinkrobots/varia](https://github.com/giantpinkrobots/varia)
{% endhint %}

{% hint style="success" %}
Site internet : [https://flathub.org/apps/io.github.giantpinkrobots.varia](https://flathub.org/apps/io.github.giantpinkrobots.varia)
{% endhint %}
