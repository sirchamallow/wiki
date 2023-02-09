---
description: Liste de logiciels
---

# 🕸 Internet

## Mozilla Firefox

#### Firefox

```bash
sudo dnf install firefox
```

Source : [https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems](https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems)

#### Firefox Developer Edition

```bash
sudo dnf copr enable the4runner/firefox-dev # Enable the4runner/firefox-dev Copr repository according to your package manager.
sudo dnf check-update                       # (Optionnal)
sudo dnf install firefox-dev                # Install Firefox Dev
firefox-dev                                 # Launch Firefox Dev
```

Source : [https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/](https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/)

### Extensions & Themes

{% content-ref url="../../../tech/software/browsers/firefox-extensions/" %}
[firefox-extensions](../../../tech/software/browsers/firefox-extensions/)
{% endcontent-ref %}

## Google Chrome

#### Google Chrome

```bash
sudo dnf install fedora-workstation-repositories	# Install Third Party Repositories
sudo dnf config-manager --set-enabled google-chrome	# Enable the Google Chrome repo
sudo dnf install google-chrome-stable			# Install Google Chrome
```

Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/](https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/)

#### Google Chrome Developers

```bash
sudo dnf install google-chrome-unstable
```

Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/](https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/)

## Brave

```bash
sudo dnf install dnf-plugins-core
sudo dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/
sudo rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
sudo dnf install brave-browser
```

Source : [https://brave.com/linux/](https://brave.com/linux/)

### Microsoft Edge

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

Source : [https://www.linuxcapable.com/install-microsoft-edge-on-fedora-linux/](https://www.linuxcapable.com/install-microsoft-edge-on-fedora-linux/)

## NextDNS

#### Installation

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
nextdns start      # Start the daemon
nextdns stop       # Stop the daemon
nextdns restart    # Restart the daemon
nextdns log        # Show daemon logs
nextdns help       # Show all commands
```

Source : [https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution](https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution)

## Client email

### Thunderbird

Par défaut, Thunderbird est disponible sur le dépôt Fedora et est souvent mis à jour en tant que Flatpak. Utilisez la commande suivante pour installer l'application sur votre système.

```bash
sudo dnf install thunderbird -y
```

Source : [https://www.linuxcapable.com/how-to-install-thunderbird-on-fedora-linux/](https://www.linuxcapable.com/how-to-install-thunderbird-on-fedora-linux/)

### Mailspring

La dernière version de Mailspring est disponible via un paquage RPM [téléchargeable depuis le site web](https://www.getmailspring.com/). Rendez-vous sur la page de téléchargement, sélectionnez "Linux" et cliquez sur "Linux (64-bit .rpm)".&#x20;

Ensuite, ouvrez une fenêtre de terminal et utilisez la commande CD pour le déplacer dans le dossier \~/Downloads.

```bash
cd ~/Downloads
```

Installez le RPM de Mailspring sur votre PC Fedora avec la commande DNF install suivante :

```bash
sudo dnf install mailspring-*.x86_64.rpm -y
```

Source : [https://www.addictivetips.com/ubuntu-linux-tips/install-mailspring-on-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-mailspring-on-linux/)
