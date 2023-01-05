---
description: Liste de logiciels
---

# 🕸 Internet

## Mozilla Firefox

### Firefox

```bash
sudo dnf install firefox
```

Source : [https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems](https://fedoraproject.org/wiki/How\_to\_debug\_Firefox\_problems)

### Firefox Developer Edition

```bash
sudo dnf copr enable the4runner/firefox-dev # Enable the4runner/firefox-dev Copr repository according to your package manager.
sudo dnf check-update                       # (Optionnal)
sudo dnf install firefox-dev                # Install Firefox Dev
firefox-dev                                 # Launch Firefox Dev
```

Source : [https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/](https://copr.fedorainfracloud.org/coprs/the4runner/firefox-dev/)

### Extensions & Themes

{% content-ref url="../../../internet/software/extensions-chrome-firefox-etc./firefox/" %}
[firefox](../../../internet/software/extensions-chrome-firefox-etc./firefox/)
{% endcontent-ref %}

## Google Chrome

### Google Chrome

```bash
sudo dnf install fedora-workstation-repositories	# Install Third Party Repositories
sudo dnf config-manager --set-enabled google-chrome	# Enable the Google Chrome repo
sudo dnf install google-chrome-stable			# Install Google Chrome
```

Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/](https://docs.fedoraproject.org/en-US/quick-docs/installing-chromium-or-google-chrome-browsers/)

### Google Chrome Developers

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

## NextDNS

### Installation

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

### Basic Usage

```
nextdns start      # Start the daemon
nextdns stop       # Stop the daemon
nextdns restart    # Restart the daemon
nextdns log        # Show daemon logs
nextdns help       # Show all commands
```

Source : [https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution](https://github.com/nextdns/nextdns/wiki/RPM-Based-Distribution)
