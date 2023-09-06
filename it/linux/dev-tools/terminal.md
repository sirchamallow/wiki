---
description: Quelques astuces pour configurer votre terrminal
---

# 📟 Terminal

## Shell

### Changer le shell par défaut

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

### Remplacer Bash par Zsh&#x20;

#### **Description**

**Zsh** (abréviation de **Z Shell**) est un programme shell riche en fonctionnalités pour les systèmes d'exploitation de type Unix (dont Linux est un dérivé) avec de nombreuses fonctionnalités.\
Il s'agit d'une version étendue du **Bourne Shell (sh).** L'intérêt de _Zsh_ par rapport à la plupart des autres commandes cd, l'extension de chemin récursif et la correction orthographique et la sélection interactive de fichiers et de répertoires.

Zsh se trouvat dans les référentiels Fedora et peut être installé avec la commande dnf suivante.

#### Installation de ZSH

```bash
sudo dnf install zsh
```

{% hint style="info" %}
Source : [https://sourceforge.net/projects/zsh/files/](https://sourceforge.net/projects/zsh/files/)
{% endhint %}

### Framework Oh-My-ZSH (OMZ)

**Oh My Zsh** est un framework pour ZSH, il fournit de nombreux thèmes, plugins (support de PHP, Python, PostgreSQL ...).

Pour l'installer, lancer la commande suivante :&#x20;

```bash
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

Une fois "Oh My Zsh" d'installé, il suffit de redémarrer ZSH pour prendre en compte les changements. (CTRL + D puis "zsh")

{% hint style="info" %}
Source : [https://www.it-connect.fr/passer-de-bash-a-zsh/](https://www.it-connect.fr/passer-de-bash-a-zsh/)
{% endhint %}

#### Thème pour Oh-My-ZSH

Il existe plusieurs thèmes pour OMZ, voici comme installer l'un d'entre eux (agnoster)

{% hint style="success" %}
La liste complète est thèmes est [disponible ici](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes).
{% endhint %}

1 - Ouvrir le fichier .zhrc

```bash
open ~/.zshrc
```

2 - Changer le thème par défaut par “agnoster”

Parcourez votre fichier afin de trouver cette ligne ZSH\_THEME et ajouter **agnoster**

```bash
ZSH_THEME="agnoster"
```

3 - Mettre à jour le fichier de config ZSH

```bash
source ~/.zshrc
```

#### Activer les mise à jour de Oh-My-ZSH

Il est possible de mettre à jour OMZ de deux façons, manuellement ou de façon automatique\
\
**Mise à jour manuel**

```bash
omz update
```

**Mise à jour automatique**

```shell
zstyle ':omz:update' mode auto	    # Activer mise à jour automatique
zstyle ':omz:update' mode disabled  # Désactiver mise à jour automatique
```

{% hint style="info" %}
Source : [https://github.com/ohmyzsh/ohmyzsh#getting-updates](https://github.com/ohmyzsh/ohmyzsh#getting-updates)
{% endhint %}

#### Plugins pour Oh-My-ZSH

Voici deux plugins très utile pour OMZ que j'utilise au quotidien :

* [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/tree/master) : un plugin pour rendre la syntax plus agréable à lire
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) : un plugin de suggestion d'autocomplétion

**1 -** Pour les installer, cloner ces répertoires dans le dossier plugins de oh-my-zsh. \
Par défaut celui-ci si trouve ici : `~/.oh-my-zsh/custom/plugins`)

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting  # zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions              # zsh-autosuggestions
```

**2 -** Ouvrir le fichier .zhrc

```bash
open ~/.zshrc
```

**3 -** Ajouter vos plugins à ceux existant. \
Parcourez votre fichier afin de trouver cette ligne plugins=( et remplacer par :&#x20;

```
plugins=(
   git
   zsh-syntax-highlighting
   zsh-autosuggestions
)
```

**3 -** Mettre à jour le fichier de config ZSH

```bash
source ~/.zshrc
```

{% hint style="info" %}
Sources : [https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) & [https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)
{% endhint %}

## TMUX

<figure><img src="../../../.gitbook/assets/Tmux_logo.png" alt=""><figcaption></figcaption></figure>

### **Description**

**tmux** est un multiplexeur de terminaux libre en mode texte. Il permet d'utiliser plusieurs terminaux virtuels dans une seule fenêtre de terminal ou une session sur un terminal distant. tmux peut être détaché d'une session et continuer de fonctionner en arrière-plan, on peut également s'y rattacher plus tard. [Wikipédia](https://fr.wikipedia.org/wiki/Tmux)

### Cheatsheet

{% hint style="info" %}
Tmux Cheat Sheet : [https://tmuxcheatsheet.com](https://tmuxcheatsheet.com/)
{% endhint %}

### Installation

```bash
sudo dnf -y install tmux
```

{% hint style="success" %}
Site web : [https://fedoramagazine.org/use-tmux-more-powerful-terminal/](https://fedoramagazine.org/use-tmux-more-powerful-terminal/)
{% endhint %}

## Dog

<figure><img src="../../../.gitbook/assets/dog-screenshot.png" alt=""><figcaption><p>Dog screenshot</p></figcaption></figure>

### **Description**

dog est un client DNS en ligne de commande comme dig. Il utilise une syntax colorée qui comprend la syntaxe normale des arguments en ligne de commande. Le client supporte les protocoles DNS-over-TLS et DNS-over-HTTPS, et peut émettre du JSON.

{% hint style="success" %}
Site web : [https://github.com/ogham/dog](https://github.com/ogham/dog)&#x20;
{% endhint %}

### Installation

Sur Fedora, vous pouvez installer dog via Snapcraft ou manuellement

#### Installation via Snap

```bash
sudo dnf install snapd		      # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap  # Enable classic snap support, enter the following to create a symbolic link
sudo snap install dog		      # Install dog
```

{% hint style="info" %}
Source : [https://snapcraft.io/install/dog/fedora](https://snapcraft.io/install/dog/fedora)
{% endhint %}

#### Installation manuelle

Installer `gcc`, `tar`, et les librairies SSL nécéssaire : `libssl` or `openssl`.

```bash
sudo dnf install gcc tar openssl-devel
```

{% hint style="warning" %}
Note : You may need to update your system’s version of the GNU C library (glibc).
{% endhint %}

Installer maintenant [**Rust**](https://www.rust-lang.org/). Il vous sera utile pour complier le code source de `dog` :

```bash
curl --proto =https --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Lorsque le terminal vous le proposer, sélectionner `1` pour procéder à l'installation dans le dossier par défaut. Après avoir redémarrer votre terminal, taper la commande suivante :

```bash
source $HOME/.cargo/env
```

Naviguer dans la [release page](https://github.com/ogham/dog/releases/) de `dog`, identifier la version la plus récente, et copier l'URL du ficher `.tar.gz`. Télécharger le fichier en remplacant par l'URL que vous venez de copier

```bash
curl -LO https://github.com/ogham/dog/archive/refs/tags/v0.1.0.tar.gz
```

Décompresser les fichers du l'archive `.tar.gz` file, et entrez dans le répertoire extrait. \
Remplacez le nom de fichier ci-dessous par celui du fichier que vous avez téléchargé. \
De même, remplacez le nom du répertoire par celui du fichier extrait :

```bash
tar -xvzf v0.1.0.tar.gz  # Extract the .tar.gz file
cd dog-0.1.0             # Open directory
```

Avant de lancer le build, lancer cette commande pour mettre à jour les dépendances de Cargo

```bash
cargo update # Update dependencies
```

Lancer le build avec Cargo pour générer le fichier binaire de `dog`:

```bash
cargo build --release  # Build project
```

Copier le fichier binaire dans le dossier `bin` de l'utilisateur :

```bash
sudo cp target/release/dog /usr/local/bin  # Copy the resulting binary into your current user’s PATH
```

Vérifier votre installation en identifiant la version de `dog` installer

```bash
dog --version # checking the installed version of dog
```

{% hint style="info" %}
Source : [https://www.linode.com/docs/guides/use-dog-linux-dns-client/](https://www.linode.com/docs/guides/use-dog-linux-dns-client/)
{% endhint %}

## Cyberduck CLI

<figure><img src="../../../.gitbook/assets/cyberduck-logo.jpg" alt=""><figcaption></figcaption></figure>



### **Description**

Un outil de transfert de fichiers qui s'exécute dans votre shell sous Linux & OS X ou votre invite de ligne de commande Windows. Modifiez des fichiers sur des serveurs distants, téléchargez, chargez et copiez entre des serveurs avec FTP, SFTP ou WebDAV, ainsi que la prise en charge des déploiements de stockage dans le cloud Amazon S3 et OpenStack Swift.

### Installation

```bash
echo -e "[duck-stable]\nname=duck-stable\nbaseurl=https://repo.cyberduck.io/stable/\$basearch/\nenabled=1\ngpgcheck=0" | sudo tee /etc/yum.repos.d/duck-stable.repo
sudo yum install duck
```

{% hint style="info" %}
Source & Site web : [https://duck.sh/](https://duck.sh/)
{% endhint %}

## **MTR (**_**My Traceroute**_**)**

### **Description**

Un outil de diagnostic de réseau en ligne de commande qui fournit les fonctions des commandes **Ping** et **Traceroute**.

### Installation

```bash
sudo dnf install mtr
```

{% hint style="success" %}
Source : [https://github.com/traviscross/mtr](https://github.com/traviscross/mtr)
{% endhint %}

{% hint style="info" %}
Site web : [https://www.bitwizard.nl/mtr](https://www.bitwizard.nl/mtr/)
{% endhint %}

## curl

<figure><img src="../../../.gitbook/assets/Curl-logo.svg.png" alt=""><figcaption></figcaption></figure>

### Description

cURL (_client URL request library_) est une [interface en ligne de commande](https://fr.wikipedia.org/wiki/Interface\_en\_ligne\_de\_commande), destinée à récupérer le contenu d'une ressource accessible sur internet. Il peut être utilisé en tant que client REST. cURL implémente l'interface utilisateur et repose sur la bibliothèque logicielle `libcurl`

### Installation

```bash
sudo dnf install curl
```

{% hint style="info" %}
Source : [https://github.com/curl/curl](https://github.com/curl/curl)
{% endhint %}

{% hint style="success" %}
Site web : [https://curl.se/](https://curl.se/)
{% endhint %}

