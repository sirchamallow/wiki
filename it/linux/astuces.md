---
description: Quelques astuces pour Fedora
---

# 😉 Astuces

## Astuces

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

### Faire une capture d'écran

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

#### Remplacer Bash par ZSH

```bash
sudo yum install zsh
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

Source : [https://www.it-connect.fr/passer-de-bash-a-zsh/](https://www.it-connect.fr/passer-de-bash-a-zsh/)

#### Activer mise à jour de ZSH

Mise à jour manuel

```shell
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