---
description: Quelques astuces pour Fedora
---

# 💡 Astuces

### Commandes de bases

**Dandified Yum** ou **DNF** est un [gestionnaire de paquets](https://fr.wikipedia.org/wiki/Gestionnaire\_de\_paquets). C’est le successeur de [YUM](https://fr.wikipedia.org/wiki/Yellowdog\_Updater,\_Modified). Pour les commandes les plus courantes, son usage est identique à celui de yum.\
\
C'est un gestinnaire de paquet basé sur RPM qui est utilisé pour installer et mettre à jour les paquets dans diverses distributions Linux tel que CentOS, RHEL et Fedora.

```bash
dnf help			# Get Help
dnf list available | more	# List All Packages
dnf list installed 		# List Installed Packages
dnf info <package>		# View Package Information
sudo dnf repolist all		# List All Repositories
sudo dnf install <package>	# Install Package
sudo dnf remove <package>	# Remove Package
sudo dnf check-update 		# Check for Updates
sudo dnf upgrade --refresh      # Update All Packages
sudo dnf update <package>	# Update Package
sudo dnf autoremove		# Remove Orphan Packages
sudo dnf distro-sync		# Synchronise All Packages
```

### Mise à niveau Fedora (upgrade)

{% hint style="info" %}
Cette méthode est celle recommandée par Fedora.
{% endhint %}

Il faut tout d'abord installer le greffon de DNF & mettre à jour votre version actuelle de Fedora.

```bash
sudo dnf install dnf-plugin-system-upgrade
sudo dnf upgrade && dnf clean all
```

Ensuite, télécharger les paquets, puis redémarrer pour appliquer la mise à niveau.

```bash
sudo dnf system-upgrade download --releasever=34
sudo dnf system-upgrade reboots
```

{% hint style="info" %}
Une mise à niveau peu parfois être longue. Durant ce laps de temps votre machine sera indisponible
{% endhint %}

Pour résoudre certains problèmes signalés lors d'un premier lancement, l'option --allowerasing peut permettre de les résoudre :

```bash
sudo dnf system-upgrade download --releasever=34 --allowerasing
```

Source : [https://doc.fedora-fr.org/wiki/Mise\_%C3%A0\_niveau\_de\_Fedora](https://doc.fedora-fr.org/wiki/Mise\_%C3%A0\_niveau\_de\_Fedora)

### Passer en user root

Pour passer en user root sur Fedora, taper

```bash
sudo su -
```

Et le mot de passe qui va avec :)

### Reset mot de passe root / session

{% embed url="https://blog.microlinux.fr/chroot-secours/" %}

{% embed url="https://www.linuxtricks.fr/wiki/reinitialiser-le-mot-de-passe-root-depuis-grub-fedora-et-red-hat" %}

### Activer le clique droit du touchpad&#x20;

Celui-ci est par défaut comme le clique gauche, ce qui est bien pénible :/

{% hint style="info" %}
Pour régler le problème, il faudra d'abord installer **gnome-tweaks**
{% endhint %}

```bash
sudo dnf install gnome-tweaks
```

Et ensuite, taper la commande suivante

```bash
gsettings set org.gnome.desktop.peripherals.touchpad click-method 'areas'
```

### Créer une clé USB d’installation bootable

<figure><img src="../../.gitbook/assets/63905e57364473528de52e1a_Etcher_steps.gif" alt="balenaEtcher"><figcaption></figcaption></figure>

Voici comment créer une clé USB Bootable Windows à l’aide de [balenaEtcher](https://www.balena.io/etcher#download-etcher). \
\
Il s’agit d’un flasheur USB multiplateforme disponible en téléchargement sur Windows, macOS et Linux. Flasher avec balenaEtcher est simple et facile. Il vous suffit de télécharger son fichier AppImage et de l’exécuter.

#### Mettre à jour Fedora

```bash
sudo dnf upgrade --refresh -y
```

#### Ajouter les repos rpm de Etcher :

```bash
curl -1sLf \
   'https://dl.cloudsmith.io/public/balena/etcher/setup.rpm.sh' \
   | sudo -E bash
```

#### Installer Etcher

```bash
sudo dnf install balena-etcher-electron -y
```

#### Mise à jour Etcher

```bash
sudo dnf upgrade --refresh -y
```

#### Désinstaller Etcher

```bash
sudo dnf remove balena-etcher-electron -y
sudo rm /etc/yum.repos.d/balena-etcher.repo
```

Source : [https://github.com/balena-io/etcher?d\_id=8404469d-719a-43bb-bffb-9633908820b6\&s\_id=1674729937970#dnf](https://github.com/balena-io/etcher?d\_id=8404469d-719a-43bb-bffb-9633908820b6\&s\_id=1674729937970#dnf)

### Faire une capture d'écran

{% hint style="info" %}
Depuis Fedora 37, un raccourci est disponible dans la barre de menu
{% endhint %}

Deux méthodes possible, avec les raccourcis clavier ou avec Shutter

#### Capture d'écran avec sauvegarde

{% hint style="info" %}
Ces méthodes de capture d'écran sont automatiquement enregistrées dans le dossier "**Images**".
{% endhint %}

* PrtScr - une capture d'écran de l'ensemble du bureau.&#x20;
* Alt + PrtScr - une capture d'écran de la fenêtre active.&#x20;
* ⇧ Shift + PrtScr - un instantané de la zone souhaitée de l'écran.

#### Capture d'écran avec copie dans le presse-papiers

{% hint style="info" %}
Ces méthodes de création d'une capture d'écran la copient dans le presse-papiers sans l'enregistrer.
{% endhint %}

* Ctrl + PrtScr - un instantané de l'ensemble du bureau.
* Ctrl + Alt + PrtScr - un instantané de la fenêtre du programme en cours.
* Ctrl + ⇧ Shift + PrtScr - un instantané de la zone souhaitée de l'écran.

Source : [https://fedoramagazine.org/take-screenshots-on-fedora/](https://fedoramagazine.org/take-screenshots-on-fedora/)

#### Avec Shutter, un outil de capture d'écran

Vous pouvez sinon utliser une gestionner de capture d'écran. \
**Shutter** est un excellent outil en la matière tout comme _Greenshot_ sur Windows.

```bash
sudo dnf install shutter    # Install Shutter
sudo dnf upgrade shutter    # Upgrade Shutter
```

Source : [https://www.fosslinux.com/39264/install-screenshot-tool-shutter-fedora.htm](https://www.fosslinux.com/39264/install-screenshot-tool-shutter-fedora.htm)l

### Rendre visible votre Dock (toujours)

{% hint style="info" %}
Il s'agit d'extensions GNOME
{% endhint %}

Deux possibilités. Soit vous garder celle de Fedora persistance avec Dash to Dock for Cosmic ou alors vous changer votre dock par une barre persistante (façon windows) avec Dash-to-Panel

#### Dash to Dock for COSMIC <a href="#extension_name" id="extension_name"></a>

```
https://extensions.gnome.org/extension/5004/dash-to-dock-for-cosmic/
```

#### Dash to Panel <a href="#extension_name" id="extension_name"></a>

```
https://extensions.gnome.org/extension/1160/dash-to-panel/
```

### Shell

#### Vérifier la version du shell

```bash
bash --version        # Check Bash version
zsh --version         # Check ZSH version
fish --version        # Check fish version
gnome-shell --version # Check GNOME version
```

Source : [https://askcodez.com/comment-trouver-ma-version-de-shell-a-laide-de-commande-de-linux.html](https://askcodez.com/comment-trouver-ma-version-de-shell-a-laide-de-commande-de-linux.html)

#### Changer le shell par défaut

{% hint style="info" %}
Pour changer de shell, un utilisateur doit exécuter la commande **chsh** et préciser où se trouve son nouveau shell.
{% endhint %}

```bash
sudo dnf install util-linux-user    # install chsh
cat /etc/shells			    # list all the shells from your system
chsh				    # change the shell for your user
/bin/zsh			    # Example: change the shell Bash to ZSH
```

Source : [https://www.linuxuprising.com/2021/01/how-to-change-default-shell-in-linux.html](https://www.linuxuprising.com/2021/01/how-to-change-default-shell-in-linux.html)

#### Remplacer Bash par ZSH avec Oh-My-ZSH

```bash
sudo yum install zsh
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

Source : [https://www.it-connect.fr/passer-de-bash-a-zsh/](https://www.it-connect.fr/passer-de-bash-a-zsh/)

#### Thème pour Oh-My-ZSH

1 - Ouvrir le fichier .zhrc

```bash
open ~/.zshrc
```

2 - Changer le thème par défaut par “agnoster”

Parcourez votre fichier afin de trouver cette ligne ZSH\_THEME et ajouter agnoster

```bash
ZSH_THEME="agnoster"
```

{% hint style="info" %}
La liste complète est thèmes est [disponible ici](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes).
{% endhint %}

3 - Mettre à jour le fichier de config ZSH

```bash
source ~/.zshrc
```

#### Activer les mise à jour de Oh-My-ZSH

Mise à jour manuel

```bash
omz update
```

Mise à jour automatique

```shell
zstyle ':omz:update' mode auto	    # Activer mise à jour automatique
zstyle ':omz:update' mode disabled  # Désactiver mise à jour automatique
```

Source : [https://github.com/ohmyzsh/ohmyzsh#getting-updates](https://github.com/ohmyzsh/ohmyzsh#getting-updates)

### Changer le serveur d'affichage&#x20;

(exemple : Wayland > XORG)

{% hint style="info" %}
Ce type de changement est parfois nécéssaire quand certaines applications ne fonctionnent pas correctement au niveau de l'affichage (ex: le partage d'écran de Discord via Wayland fait un écran noir, du coup il faut changer le serveur d'affichage sur XORG et c'est bon :)
{% endhint %}

#### Ecran de connexion

* Vérifiez le système de fenêtrage actuellement utilisé : allez dans **Paramètres** et sélectionnez **À propos** > **Système de fenetrage.**
* Sur l'écran de connexion, sélectionner l'icône ⚙️ et définir **GNOME sur Xorg.**
* Ouvrez votre session, normalement le système de fenêtrage XORG (X11) sera utilisé.
* Pour vérifier, retournez dans **Paramètres** et sélectionnez **À propos** > **Système de fenetrage.**
* Pas de panique, votre changement persistera après une déconnexion ou un redémarrage

#### Editer le fichier de configuration

Changer la session GNOME par défaut en éditant le fichier de configuration

Ouvrez /etc/gdm/custom.conf et décommentez la ligne :&#x20;

```bash
WaylandEnable=false
```

Ajoutez la ligne suivante à la section \[daemon]&#x20;

```bash
DefaultSession=gnome-xorg.desktop 
```

Sauvegardez le fichier custom.conf.

Déconnectez-vous ou redémarrez pour entrer dans la nouvelle session.

{% hint style="success" %}
Pour plus d'informations : [https://docs.fedoraproject.org/fr/quick-docs/configuring-xorg-as-default-gnome-session/](https://docs.fedoraproject.org/fr/quick-docs/configuring-xorg-as-default-gnome-session/)
{% endhint %}

### Désinstaller une application

```bash
yum list <nom du paquet>	# Rechercher un paquet - Méthode 1
yum list kernel\*		# Rechercher un paquet - Méthode 2
yum list "kernel*"		# Rechercher un paquet - Méthode 3
yum search <mot clef>		# Rechercher un paquet - Méthode 4

yum remove <nom du paquet>	# Supprimer un paquet
# Attention aux dépendances, bien lire ce qui est proposé à la suppression. 
```

### Kernel Devel

Le paquet kernel-devel contient les fichiers d'en-têtes du noyau, des fichiers permettant au développeur d'accéder aux différentes fonctionnalités du noyau . De façon plus simple, il est nécessaire au développement et à la compilation de pilotes.

```bash
sudo dnf in kernel-devel
```

Source : [https://www.reddit.com/r/Fedora/comments/nl6arp/how\_do\_i\_install\_kernel\_headers\_for\_fedora/](https://www.reddit.com/r/Fedora/comments/nl6arp/how\_do\_i\_install\_kernel\_headers\_for\_fedora/)

### Faire un Dig

#### Introduction

La commande **dig** signifie **Domain Information Groper,** il collecte des données sur les serveurs de noms de domaine. **Dig** est utile pour résoudre les problèmes DNS

{% hint style="warning" %}
Dig n’est pas une commande de base Linux.
{% endhint %}

#### Installation

```bash
sudo dnf install bind bind-utils
```

#### Recherche DNS

```bash
dig www.lewifi.fr
```

#### Recherche DNS ipv4 & ipv6

```bash
dig www.lewifi.fr A www.lewifi.fr AAAA +short
```

Sourcr : Source: [http://linux.die.net/man/1/dig](http://linux.die.net/man/1/dig) -- under the 'Multiple Queries' section

#### Spécifier un serveur DNS

{% hint style="info" %}
Par défaut, **Dig** utilise la configuration locale (/etc/resolv.conf) pour décider quel serveur de noms utiliser. Il est possible de lui spécifier un autre résolveur DNS comme celui de Quad9
{% endhint %}

```bash
dig @9.9.9.9 www.lewifi.fr
```

#### Recherche DNS avec option Trace

{% hint style="info" %}
L’option **+trace** répertorie chaque serveur différent que la requête passe jusqu’à sa destination finale. Pratique pour identifier l’adresse IP où le trafic tombe
{% endhint %}

```bash
dig www.lewifi.fr +trace
```

### Tweaks

Fedy est un outil graphique qui vous permet de modifier votre système Fedora en quelques clics. Des applications normales aux thèmes, en passant par les diverses modifications du système, Fedy peut faire presque tout ce dont vous pouvez avoir besoin sur Fedora.

{% hint style="info" %}
Pour installer Fedy sur la dernière version de Fedora, assurez-vous que vous avez que vous avez déjà activé les dépôts RPM Fusion
{% endhint %}

#### Installation

```bash
sudo dnf copr enable kwizart/fedy
sudo dnf install fedy -y
```

Source : [https://fosspost.org/things-to-do-after-installing-fedora-37/](https://fosspost.org/things-to-do-after-installing-fedora-37/)

### Connaitre la taille du disque ou répertoire

#### Taille du disque&#x20;

La commande `df -h` (_disk free human-readable_) permet d’afficher à l’écran la taille de l’espace disque occupée, et la taille de l’espace disque libre de manière lisible (sans le -h la taille des fichiers serait en octet)&#x20;

Taper `df -h` pour afficher le résultat ;)

#### Taille des répertoires

La commande `du -h` (_disk usage human-readable_) permet d’afficher la taille d’un répertoire et de tous les sous répertoires récursifs qu’il contient.&#x20;

1. `pwd` : pour savoir dans quel répertoire vous vous trouvez actuellement.
2. `ls` ou `tree` : pour afficher la liste des fichiers&#x20;
3. `du -h` : pour connaitre la taille occuper par les fichiers du répertoires.&#x20;
4. d`u -sh .` : pour afficher le taille du répertoire (et non pas fichier par fichier)
5. `du -sh * | sort -hk1` : pour lister les répertoires, leurs tailles par ordre croissant
