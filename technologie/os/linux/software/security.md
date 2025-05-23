---
description: Liste de logiciels de sécurités
icon: shield-halved
---

# Sécurité

## firewalld

<figure><img src="../../../../.gitbook/assets/firewalld.png" alt=""><figcaption></figcaption></figure>

firewalld est un pare-feu open-source

{% code fullWidth="true" %}
```bash
sudo dnf install firewalld	    # Install firewalld
sudo firewall-cmd --state	    # Checking the firewalld status
firewall-config			    # Viewing current firewalld settings using GUI
sudo systemctl unmask firewalld	    # Start firewalld, by entering the following commands
sudo systemctl start firewalld		
sudo systemctl enable firewalld	    # make firewalld start automatically at system start
```
{% endcode %}

{% hint style="info" %}
Source : [https://docs.fedoraproject.org/fr/quick-docs/firewalld/](https://docs.fedoraproject.org/fr/quick-docs/firewalld/)
{% endhint %}

***

## UFW (Uncomplicated Firewall)

**UFW** pour **Uncomplicated Firewal**l est un utilitaire en ligne de commande simplifié de **Netfilter**, c’est une alternative simple à iptables, qui permet de gérer les règles du pare-feu

{% code fullWidth="true" %}
```bash
sudo dnf install ufw        # Installez UFW en utilisant la commande suivante :
sudo ufw enable             # Activez UFW avec la commande
sudo ufw status             # Vérifiez l'état de UFW pour vous assurer qu'il est actif
sudo ufw status verbose     # Plus d’information sur la paramétrage du pare-feu (logging, règle par défaut…)
sudo ufw allow 80           # Ouvrir le trafic entrant sur le port 80 (http).
sudo ufw allow 443/tcp      # Exemple pour ouvrir le 443 (https) seulement sur en TCP
sudo ufw status numbered    # Afficher le statut sur les règles
sudo ufw logging on         # Enregistrer enregistrer les événements du firewall

# Autoriser un service
less /etc/services          # Afficher la liste des services utiliser
sudo ufw allow ssh          # Autoriser le service ssh
sudo ufw allow from X.Y.Z.W # Si vous souhaitez autoriser tous le trafic entrant depuis une adresse IP
```
{% endcode %}

{% hint style="info" %}
Source : [https://launchpad.net/ufw](https://launchpad.net/ufw)
{% endhint %}

***

## ClamAV

<figure><img src="../../../../.gitbook/assets/clamav.png" alt="" width="227"><figcaption></figcaption></figure>

ClamAV est Antivirus open-source

#### Guide d'installation

{% hint style="warning" %}
Pré-requis : mettre à jour le système d'exploitation
{% endhint %}

```bash
sudo dnf upgrade --refresh -y
```

#### Installation des dépendances

```bash
sudo dnf install dnf-plugins-core -y
```

#### Installer ClamAV

```bash
sudo dnf install clamav clamd clamav-update
```

{% hint style="info" %}
Vérifier si l'installation a réussi, une version et le numéro de build devrait s'afficher
{% endhint %}

```bash
clamd --version
```

Fedora utilise [SELinux](https://www.redhat.com/fr/topics/linux/what-is-selinux) ; étant donné le fonctionnement de ClamAV, vous devrez le configurer pour qu'il n'y ait pas d'interférences.

```bash
sudo setsebool -P antivirus_can_scan_system 1
```

#### Mettre à jour la bade de données de virus

Après avoir installé ClamAV, il est conseillé de mettre à jour votre base de données de définitions de virus avant de commencer à utiliser le scanner de virus

```bash
sudo systemctl stop clamav-freshclam  # Arreter le service
sudo freshclam                        # Mise à jour de la bdd
sudo systemctl start clamav-freshclam # Démarrer le service
systemctl status clamav-freshclam     # Vérifier le statut
```

#### Activer ou désactiver ClamAV au démarrage

```bash
sudo systemctl enable clamav-freshclam  # Activer ClamAV au démarrage
sudo systemctl disable clamav-freshclam # Désactiver ClamAV au démarrage
```

#### Désinstaller ClamAV

```bash
sudo dnf autoremove clamav clamd clamav-update
```

{% hint style="warning" %}
Notez que cela supprimera toutes les dépendances inutilisées installées avec ClamAV pour une désinstallation complète.
{% endhint %}

{% hint style="info" %}
Source : [https://www.clamav.net/documents/clam-antivirus-user-manual](https://www.clamav.net/documents/clam-antivirus-user-manual) &  [https://www.linuxcapable.com/how-to-install-clamav-on-fedora-35/](https://www.linuxcapable.com/how-to-install-clamav-on-fedora-35/#Update_Operating_System)
{% endhint %}

***

### ClamTk

ClamTk est un GUI (une interface) pour ClamAV (Clam Antivirus). \
Il est destiné à être facile d'utilisation, léger et facile à utiliser pour les systèmes Linux.

#### Installation

```bash
sudo dnf install clamtk
```

#### Désinstallation

```bash
sudo dnf erase clamtk
```

{% hint style="info" %}
Source : [https://github.com/dave-theunsub/clamtk](https://github.com/dave-theunsub/clamtk)
{% endhint %}

***

## Bitwarden

<figure><img src="../../../../.gitbook/assets/Bitwarden_2022_Logo.png" alt="" width="375"><figcaption></figcaption></figure>

Il existe plusieurs possiblités d'installer Bitwarden sur Fedora, je préfère vous sélectionner celles-ci (via Snap), car il sera possible de mettre à jour le soft régulièrement.&#x20;

#### Installation manuel

Il est possible d'installer Bitwarden avec un paquet RPM officiel

```bash
https://vault.bitwarden.com/download/?app=desktop&platform=linux&variant=rpm
```

{% hint style="warning" %}
Cependant celui-ci n'est pas mise à jour automatiquement.
{% endhint %}

#### Installation via Snapcraft

{% hint style="info" %}
Pré-requis : **Snapd** est nécéssaire
{% endhint %}

```bash
sudo dnf install snapd
```

```bash
sudo snap install bitwarden
```

{% hint style="success" %}
Source : [https://bitwarden.com/download/](https://bitwarden.com/download/)
{% endhint %}

{% hint style="info" %}
Il existe également une CLI pour Bitwarden, vous pouvez la télécharger depuis la page d'aide : [https://bitwarden.com/help/cli/](https://bitwarden.com/help/cli/)
{% endhint %}

***

## 1Password

<figure><img src="../../../../.gitbook/assets/1password.jpg" alt="" width="375"><figcaption></figcaption></figure>

Installation de 1Password en utilisant votre gestionnaire de paquets

1.  Ajout de la clé du repo yum 1Password :

    ```bash
     sudo rpm --import https://downloads.1password.com/linux/keys/1password.asc
    ```
2.  Ajouter le repo yum 1Password :

    ```bash
     sudo sh -c 'echo -e "[1password]\nname=1Password Stable Channel\nbaseurl=https://downloads.1password.com/linux/rpm/stable/\$basearch\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=\"https://downloads.1password.com/linux/keys/1password.asc\"" > /etc/yum.repos.d/1password.repo'
    ```
3.  Installer 1Password:

    ```bash
     sudo dnf install 1password
    ```

{% hint style="info" %}
Source : [https://1password.com/fr/downloads/linux/](https://1password.com/fr/downloads/linux/)
{% endhint %}

***

## Sniffnet

<figure><img src="../../../../.gitbook/assets/overview_page.png" alt="" width="375"><figcaption></figcaption></figure>

#### Description

Sniffnet est un outil technique open-source qui se concentre fortement sur l'ensemble de l'expérience de l'utilisateur. La plupart des analyseurs de réseau sont encombrants à utiliser, tandis que l'une des pierres angulaires de Sniffnet est d'être utilisable avec facilité par tout le monde.

#### Installation

{% hint style="success" %}
Site internet : [https://sniffnet.net/download/](https://sniffnet.net/download/)
{% endhint %}

***

## CVEmap

<figure><img src="../../../../.gitbook/assets/cvemap.png" alt=""><figcaption></figcaption></figure>

Un outil d'interface de ligne de commande (CLI) conçu pour fournir une interface structurée et facilement navigable à diverses bases de données de vulnérabilité (CVE)

Notes : pratique pour les amoureux du terminal. Pour les autres, vous avez aussi [CVEdetails](https://www.cvedetails.com/) qui est une bonne référence en la matière

#### Installation

{% hint style="info" %}
Pré-requis : **Go** est nécéssaire
{% endhint %}

```bash
## Installer Go
sudo dnf install golang

## Installer CVEmap
sudo go install github.com/projectdiscovery/cvemap/cmd/cvemap@latest
```

{% hint style="success" %}
Site : [https://github.com/projectdiscovery/cvemap](https://github.com/projectdiscovery/cvemap)
{% endhint %}
