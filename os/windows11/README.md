---
description: Astuces & Liste d'appplications pour Windows 10/11
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# 🐸 Microsoft | Windows 11

{% hint style="info" %}
Avant-Propos : j'utilise principalement Fedora. Toutefois quand j'ai besoin de jouer à des jeux vidéos, je bascule sur Windows11 (et j'ai longtemps utiliser cet OS)
{% endhint %}

## **Chocolatey**

Après une installation de [**Windows 10/11**](https://www.microsoft.com/fr-fr/windows/) sur votre ordinateur, la prochaine étape consistera à remettre "clean" votre système d'exploitation et de désinstaller les applications inutiles que Microsoft pré-installepré-installent par défaut et sans votre accord.&#x20;

Et dans certains cas, vous devrez même renouveller l'opération en désinstallant cette fois-ci ceux pré-installer par le fabricant de votre ordinateur.

Puis il vous faudra installer vos logiciels.&#x20;

Afin de vous faire gagner du temps dans cette étape (parfois très longue), il existe plusieurs gestionnaires de paquet pour Windows11. Nous allons nous concentrer sur [**Chocolatey**](https://chocolatey.org/)**.** \
\
Celui-ci vous permettra d'installer un paquet de logiciels en un temps records :)

{% hint style="success" %}
Il existe une interface graphique pour le gestionnaire > [Chocolatey-GUI](https://community.chocolatey.org/packages/ChocolateyGUI)
{% endhint %}

### Installation

Taper cette commande avec les droits administateur :

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

{% hint style="info" %}
En cas de problème, lire [la documentation d'installation.](https://chocolatey.org/install#individual)
{% endhint %}

### Liste de logiciels (non-exhaustifs)

<pre class="language-powershell"><code class="lang-powershell"><strong>## Utilitaires ##
</strong>choco install 7zip                         # 7zip
choco install adobereader                  # Adobe Reader DC
choco install chocolateygui                # Chocolatey GUI
choco install cpu-z                        # CPU-Z
choco install defraggler                   # Defraggler
choco install greenshot                    # Greenshot
choco install netbalancer                  # Net Balancer
choco install playnite                     # Playnite
choco install rufus                        # Rufus
choco install speccy                       # Speccy
choco install vlc                          # VLC Media Player
choco install windirstat                   # Windirstat
choco install winaero-tweaker              # Winaero-Tweaker
choco install youtube-dl                   # YouTube-DL

## Web ##
choco install discord                      # Discord
choco install thunderbird                  # Mozilla Thunderbird
choco install nextdns                      # NextDNS
choco install nextdns-cli                  # NextDNS-CLI
choco install qbittorrent                  # qBittorent
choco install slack                        # Slack

## Securité ##
choco install 1password                    # 1password
choco install bitwarden                    # Bitwarden
choco install malwarebytes                 # Malwarebytes
choco install protonvpn                    # ProtonVPN

## Drivers ##
choco install dellcommandupdate            # Dell Command Update
choco install nvidia-display-driver        # NVIDIA Display Driver
choco install disable-nvidia-telemetry     # Disable Nvidia Telemetry

## Navigateurs ##
choco install brave                        # Brave
choco install chromium                     # Chromium
choco install googlechrome                 # Google Chrome
choco install microsoft-edge               # Microsoft Edge
choco install firefox                      # Mozilla Firefox
choco install tor-browser                  # Tor Browser

## DEV ##
choco install cyberduck                    # Cyberduck
choco install duck                         # Cyberduck-CLI
choco install git                          # Git
choco install microsoft-windows-terminal   # Microsoft Windows Terminal
choco install notepadplusplus              # Notepad++
choco install ruby                         # Ruby
choco install pgadmin4                     # PGadmin 4
choco install postman                      # Postman
choco install virtualbox                   # VirtualBox
choco install vscode                       # Visual Studio Code
choco install winscp                       # WinSCP
</code></pre>

{% hint style="info" %}
La liste complète est disponible sur la [page du repo](https://community.chocolatey.org/packages) publique.
{% endhint %}

### Mise à jour

Pour la mise à jour de vos apps via Chocolatey, ouvrir le terminal (avec les droits administrateurs)

```powershell
choco upgrade chocolatey                        # Upgrade chocolatey first
choco upgrade notepadplusplus googlechrome 7zip # Specific upgrade software examples
choco upgrade nodejs.install --version 0.10.35  # Exammples : Upgrade NodeJS specific version
choco upgrade all                               # Upgrade all software installed with Chocolatey
choco upgrade all --except="'skype,conemu'"     # Examples : Upgrade all software exptedted Skype, Conemu
```

## Microsoft Store

* [Microsoft Edge Browser](https://apps.microsoft.com/store/detail/microsoft-edge-browser/XPFFTQ037JWMHS) : navigateur web de Microsoft
* [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?) : le terminal de windows
* [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/ubuntu-20045-lts/9MTTCL66CPXJ) : Installation complète de Ubuntu 20.04.5 LTS

{% hint style="info" %}
#### Mise à jour

Pour mettre à jour le **Microsoft Store** : sélectionnez le bouton **Démarrer** , puis Microsoft Store dans la liste des applications. Dans le Microsoft Store, sélectionnez **En savoir plus** > Téléchargements et mises à jour > Obtenir des **mises à jour**.
{% endhint %}

## Téléchargement direct

* [KeyScrambler](https://www.qfxsoftware.com/download.htm) : Chiffrement logiciel de vos frappes de votre clavier
* [Comodo Personal Firewall](https://personalfirewall.comodo.com/firewall-for-windows-10.php) : Pare-feu gratuit pour Windows10
* [Captvty](https://captvty.fr/) : Télécharger le replay d'émissions TV francophones
* [Tweak-SSD v2](http://www.totalidea.com/products/tweak-ssd/) : Optimise votre SSD pour Windows10

## Astuces

{% content-ref url="astuces-de-la-win.md" %}
[astuces-de-la-win.md](astuces-de-la-win.md)
{% endcontent-ref %}
