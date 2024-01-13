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

# 🤔 Windows 11

**Pré-requis :** que ce soit après une installation de [**Windows 10/11**](https://www.microsoft.com/fr-fr/windows/) sur votre ordinateur, votre prochaine étape consistera à remettre "clean" votre système d'exploitation et désinstaller les applications inutiles que Microsoft pré-installepré-installent par défaut et sans votre accord. \
\
Et dans certains cas, il faudra renouveller l'opération en désinstallant cette fois ceux du fabricant de votre ordinateur.



Dans un **second temps**, il vous faudra installer vos logiciels. \
\
Pour vous faire gagner du temps dans cette étape (parfois très longue), il existe un gestionnaire de paquet pour Windows. Son nom ? [**Chocolatey**](https://chocolatey.org/)**.** \
\
Il vous permettra d'installer un paquet de logiciels en un temps records !&#x20;

{% hint style="success" %}
Il existe une interface graphique pour le gestionnaire > [Chocolatey-GUI](https://community.chocolatey.org/packages/ChocolateyGUI)
{% endhint %}

## Logiciels Windows

### Installation via Chocolatey

#### Installer chocolatey sur votre machine

D'abord vous devez installer le gestionnaire de paquet (avec les droits administateur).

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

{% hint style="info" %}
En cas de problème, lire [la documentation d'installation.](https://chocolatey.org/install#individual)
{% endhint %}

#### Liste de logiciels disponibles (non-exhaustifs)

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
choco install windirstat                   # Windirsta
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

#### Mise à jour

Pour la mise à jour de vos apps via Chocolatey, ouvrir le terminal (avec les droits administrateurs)

```powershell
choco upgrade chocolatey                        # Upgrade chocolatey first
choco upgrade notepadplusplus googlechrome 7zip # Specific upgrade software examples
choco upgrade nodejs.install --version 0.10.35  # Exammples : Upgrade NodeJS specific version
choco upgrade all                               # Upgrade all software installed with Chocolatey
choco upgrade all --except="'skype,conemu'"     # Examples : Upgrade all software exptedted Skype, Conemu
```

### Installation via le Microsoft Store

#### Ouvrir le Microsoft Store ou depuis votre navigateur :

* [Prime Video pour Windows](https://apps.microsoft.com/store/detail/prime-video-pour-windows/9P6RC76MSMMJ) : Amazon Prime Video
* [Disney+](https://apps.microsoft.com/store/detail/disney/9NXQXXLFST89) : plateforme SVOD de Disney
* [Netflix](https://apps.microsoft.com/store/detail/netflix/9WZDNCRFJ3TJ) : plateforme SVOD
* [Pluto TV](https://apps.microsoft.com/store/detail/pluto-tv/9P9LV240KQ9R) : plateforme AVOD
* [Adobe Acrobat Reader DC](https://apps.microsoft.com/store/detail/adobe-acrobat-reader-dc/XPDP273C0XHQH2) : lecteur pdf
* [Microsoft Edge Browser](https://apps.microsoft.com/store/detail/microsoft-edge-browser/XPFFTQ037JWMHS) : navigateur web de Microsoft
* [Mozilla Firefox](https://apps.microsoft.com/store/detail/mozilla-firefox/9NZVDKPMR9RD) : navigateur web de la fondation Mozilla
* [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?) : le terminal de windows
* [Windows Subsystem for Linux (WSL)](https://apps.microsoft.com/store/detail/ubuntu-20045-lts/9MTTCL66CPXJ) : Installation complète de Ubuntu 20.04.5 LTS

{% hint style="info" %}
#### Mise à jour

Pour mettre à jour le **Microsoft Store** : sélectionnez le bouton **Démarrer** , puis Microsoft Store dans la liste des applications. Dans le Microsoft Store, sélectionnez **En savoir plus** > Téléchargements et mises à jour > Obtenir des **mises à jour**.
{% endhint %}

### Téléchargement direct

* [KeyScrambler](https://www.qfxsoftware.com/download.htm) : Chiffrement logiciel de vos frappes de votre clavier
* [Comodo Personal Firewall](https://personalfirewall.comodo.com/firewall-for-windows-10.php) : Pare-feu gratuit pour Windows10
* [Captvty](https://captvty.fr/) : Télécharger le replay d'émissions TV francophones
* [Tweak-SSD v2](http://www.totalidea.com/products/tweak-ssd/) : Optimise votre SSD pour Windows10

## Astuces

### Télémétrie pilotes carte graphique Nvidia

Penser à désactiver la télémétrie activé par défaut de la suite _GeForce Experience_, un logiciel de **Nvidia** accompagnant bien souvent les drivers de la carte graphique. Ils remontent automatiquement des informations sur votre système au fabricant. \
Avec le refrain classique "nous nous servons de cette télémétrie pour améliorer ses pilotes et l'expérience de ses utilisateurs". Mais comme tout est chiffré, il n'y aucun moyen de savoir ce qui est envoyé réellement. Il n'est possible de désactiver cette option depuis l'interface des pilotes.\
\
Il vous sera nécessaire soit de vous plonger dans les tâches planifiées, le registre et les services de Windows en suivant par exemple [ce guide de PC-Astuces](https://www.pcastuces.com/pratique/astuces/4871.htm), ou un installant [ce package depuis Chocolatey](https://chocolatey.org/packages/disable-nvidia-telemetry).

**Désactiver les services inutiles**

Pour des solutions officielles concernant l'optimisation de windows, afin de Désactiver les services inutiles il y a le site de Microsoft :

{% embed url="https://learn.microsoft.com/fr-fr/windows/iot/iot-enterprise/optimize-your-device/services" %}
