---
description: Quelques astuces pour configurer votre terrminal
icon: rectangle-terminal
---

# Terminal

## Shell

#### Vérifier la version du shell

```bash
bash --version        # Check Bash version
zsh --version         # Check ZSH version
fish --version        # Check fish version
gnome-shell --version # Check GNOME version
```

### Changer le shell par défaut

{% hint style="info" %}
Pour changer de shell, un utilisateur doit exécuter la commande **chsh** et préciser où se trouve son nouveau shell.
{% endhint %}

```bash
sudo dnf install util-linux-user    # Install chsh
cat /etc/shells			                # liste tous les shells de votre système
chsh				                        # Changer le shell de l'utilisateur
/bin/zsh			                      # Exemple: changer leshell Bash pour ZSH
```

## Configurer son terminal

{% embed url="https://stefy237.github.io/Mysh/" %}

Mysh, un générateur de config terminal Linux. Vous récupérez un script, et tout est en place. Tout se passe dans lenavigateur. Un gain de temps considérable

***

## Zsh

Comment remplacer Bash par Zsh

**Zsh** (abréviation de **Z Shell**) est un programme shell riche en fonctionnalités pour les systèmes d'exploitation de type Unix (dont Linux est un dérivé) avec de nombreuses fonctionnalités.\
Il s'agit d'une version étendue du **Bourne Shell (sh).** L'intérêt de _Zsh_ par rapport à la plupart des autres commandes cd, l'extension de chemin récursif et la correction orthographique et la sélection interactive de fichiers et de répertoires.

Zsh se trouvat dans les référentiels Fedora et peut être installé avec la commande dnf suivante.

```bash
sudo dnf install zsh # Installer sur Linux (Fedora)
```

***

## Oh-My-ZSH (OMZ)

{% embed url="https://ohmyz.sh" %}

**Oh My Zsh** est un framework pour ZSH, il fournit de nombreux thèmes et plugins (support de PHP, Python, PostgreSQL ...). Ci-dessous, sont présents ceux que j'utilise.&#x20;

{% hint style="info" %}
A découvrir, une liste de plugins pour OMZ réalisé par Unixorn : \
[https://github.com/unixorn/awesome-zsh-plugins#oh-my-zsh](https://github.com/unixorn/awesome-zsh-plugins#oh-my-zsh)
{% endhint %}

Pour l'installer, lancer la commande suivante :&#x20;

```bash
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

Une fois "Oh My Zsh" d'installé, il suffit de redémarrer ZSH pour prendre en compte les changements. (CTRL + D puis "zsh")

{% embed url="https://www.it-connect.fr/passer-de-bash-a-zsh/" %}

#### Activer les mise à jour de Oh-My-ZSH

Il est possible de mettre à jour OMZ de deux façons, manuellement ou de façon automatique

```bash
omz update # Mise à jour manuel de omz
```

```shell
zstyle ':omz:update' mode auto	    # Activer mise à jour automatique
zstyle ':omz:update' mode disabled  # Désactiver mise à jour automatique
```

## Thèmes OMZ

Il existe plusieurs thèmes pour OMZ, voici comme installer deux d'entre eux (agnoster et powerlevel10K)

{% hint style="success" %}
La liste complète est thèmes est [disponible ici](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes).
{% endhint %}

### Agnoster

1 - Ouvrir le fichier `.zhrc`

```bash
open ~/.zshrc
```

2 - Changer le thème par défaut

Parcourez votre fichier afin de trouver cette ligne `ZSH_THEME` et ajouter `agnoster`

```bash
ZSH_THEME="agnoster"
```

3 - Mettre à jour le fichier de config ZSH

```bash
source ~/.zshrc
```

### Powerlevel10K

Avant de procéder à l'installation du thème **Powerlevel10K**, il est fortement reccomander d'installer la polices d'écriture **Meslo Nerd Font** pour une meilleur confort.

**Pré-requis : Meslo Nerd Font**

1. Télécharger Meslo Nerd Font (fichiers ttf)

* [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
* [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
* [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
* [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

2. Installer les fonts sur votre système

Double-cliquer sur chaque fichier, et cliquer "Install". Cela installera `MesloLGS NF` sur votre système.

3. Définir la police d'écriture dans votre Terminal ou IDE

* **Visual Studio Code**: Ouvrir _Fichiers → Préférences → Paramètres_ (PC) ou _Code → Préférences → Paramètres_ (Mac), et taper `terminal.integrated.fontFamily` dans la barre de recherche présente en haut de l'onglet _Préférences_ et basculer la valeur sur `MesloLGS NF`. Vous pouvez consulter [ce screenshot](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/389133fb8c9a2347929a23702ce3039aacc46c3d/visual-studio-code-font-settings.jpg) pour voir ce que cela doit donner.
* **GNOME Terminal** / **Tilix** (le terminal par défaut de Fedora): Ouvrir le _Terminal → Préférences_ et sélectionner un profil . Rechercher _Custom font_ sous _Text Appearance_ et sélectionner`MesloLGS NF Regular`

**Installation de Powerlevel10K**

1 - Cloner le répertoire suivant

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

2 - Ouvrir le fichier .zhrc

```bash
open ~/.zshrc
```

3 - Changer le thème par défaut

Parcourez votre fichier afin de trouver cette ligne ZSH\_THEME et ajouter `powerlevel10k`

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

4 - Mettre à jour le fichier de config ZSH

```bash
source ~/.zshrc
```

{% embed url="https://github.com/romkatv/powerlevel10k#oh-my-zsh" %}

### Plugins

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

{% embed url="https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md" %}

{% embed url="https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md" %}

***

## Warp

{% embed url="https://www.warp.dev" %}

Warp est un émulateur de terminal écrit en **Rust**.\
\
Il se distingue par des fonctionnalités telles que Warp Drive pour le partage de commandes entre équipes, Warp AI pour les suggestions et l'assistance des commandes, ainsi qu'un IDE moderne avec une sélection de texte et un positionnement du curseur.

La manière la plus simple d'installer Warp est de télécharger et d'installer [le paquet rpm](https://app.warp.dev/download?package=rpm).\
Après le téléchargement, vous pouvez installer le paquet avec :

```bash
sudo dnf install ./.rpm # Installer sur Linux (Fedora)
```

L'installation du paquetage .rpm configurera automatiquement le dépôt yum de Warp. Lors de la première mise à jour, dnf récupérera la clé de signature nécessaire pour vérifier l'intégrité des paquets téléchargés.

***

## TMUX

**tmux** est un multiplexeur de terminaux libre en mode texte. Il permet d'utiliser plusieurs terminaux virtuels dans une seule fenêtre de terminal ou une session sur un terminal distant. tmux peut être détaché d'une session et continuer de fonctionner en arrière-plan, on peut également s'y rattacher plus tard. [Wikipédia](https://fr.wikipedia.org/wiki/Tmux)

```bash
sudo dnf -y install tmux # Installer sur Linux (Fedora)
```

{% embed url="https://fedoramagazine.org/use-tmux-more-powerful-terminal/" %}

### Liste de raccourcis

`tmux ls` : voir la liste liste des tmux actifs

`tmux new -s mysession` : démarrer une nouvelle session avec un nom

`tmux a -t mysession` : se connecter à votre dernière session qui porte un nom

### Cheatsheet

{% embed url="https://tmuxcheatsheet.com/" %}

***

## Dog

{% embed url="https://github.com/ogham/dog" %}

dog est un client DNS en ligne de commande comme dig. Il utilise une syntax colorée qui comprend la syntaxe normale des arguments en ligne de commande. Le client supporte les protocoles DNS-over-TLS et DNS-over-HTTPS, et peut émettre du JSON.

Sur Fedora, vous pouvez installer dog via Snapcraft ou manuellement

#### Installation via Snap

```bash
sudo dnf install snapd		            # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap  # Enable classic snap support, enter the following to create a symbolic link
sudo snap install dog		              # Install dog
```

#### Installation manuelle

Installer `gcc`, `tar`, et les librairies SSL nécessaire : `libssl` or `openssl`.

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

***

## Doggo

{% embed url="https://github.com/mr-karan/doggo" %}

**doggo** est un client DNS moderne en ligne de commande (comme _dig_ ) écrit en Go. Il affiche les informations de manière claire et concise et prend en charge des protocoles tels que DoH, DoT, DoQ et DNSCrypt. Ce projet est entièrement inspiré de [dog](https://github.com/ogham/dog/) , un programme écrit en Rust. L'auteur y à ajouter quelques fonctionnalités et réécrit en `Go`. D'où le nom `dog`+ `go`=> **doggo** .

#### Installation facile (recommandée)

```bash
curl -fsSL https://raw.githubusercontent.com/mr-karan/doggo/main/install.sh | sh
```

#### Gestionnaires de paquets

* Homebrew (MacOS) : `brew install doggo`
* Winget (Windows) : `winget install doggo`

#### Démarrage rapide

Voici quelques exemples rapides pour vous familiariser :

```bash
doggo example.com # Simple DNS lookup
doggo MX github.com @9.9.9.9 # Query MX records using a specific nameserver
doggo example.com @https://cloudflare-dns.com/dns-query # Use DNS over HTTPS
doggo example.com --json | jq '.responses[0].answers[].address' # JSON output for scripting
doggo --reverse 8.8.8.8 --short # Reverse DNS lookup
doggo example.com --trace # Follow the delegation chain iteratively
doggo example.com --gp-from Germany,Japan --gp-limit 2 # Using Globalping
```

***

## Cyberduck CLI

{% embed url="https://duck.sh/" %}

Un outil de transfert de fichiers qui s'exécute dans votre shell sous Linux & OS X ou votre invite de ligne de commande Windows. Modifiez des fichiers sur des serveurs distants, téléchargez, chargez et copiez entre des serveurs avec FTP, SFTP ou WebDAV, ainsi que la prise en charge des déploiements de stockage dans le cloud Amazon S3 et OpenStack Swift.

```bash
echo -e "[duck-stable]\nname=duck-stable\nbaseurl=https://repo.cyberduck.io/stable/\$basearch/\nenabled=1\ngpgcheck=0" | sudo tee /etc/yum.repos.d/duck-stable.repo
sudo yum install duck
```

***

## **MTR (**_**My Traceroute**_**)**

{% embed url="https://www.bitwizard.nl/mtr/" %}

Un outil de diagnostic de réseau en ligne de commande qui fournit les fonctions des commandes **Ping** et **Traceroute**.

```bash
sudo dnf install mtr # Installer sur Linux (Fedora)
```

***

## VIM

{% embed url="https://www.vim.org/download.php" %}

{% embed url="https://fedoraproject.org/wiki/Vim" %}

VIM permets de lire et d'éditer des fichiers depuis votre terminal.\
Pas facile à prendre en main :D

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf install vim        # VIM CLI version
</strong><strong>sudo dnf install vim-X11    # VIM vith GUI features
</strong></code></pre>

### Liste de raccourcis

`:q!` or `ZQ` - quitter et abandonner les modifications non sauvegardée

{% hint style="info" %}
Vim Cheatsheet : [https://vim.rtorr.com/lang/fr\_fr](https://vim.rtorr.com/lang/fr_fr)
{% endhint %}

#### Faire une modification sur un fichier

1. Rechercher la valeur à modifier : `/<value>`
2. Faire une insertion : `i`
3. Changer la valeur
4. Quitter la saisie vim : `exit`
5. Sauvegarder et quitter vim : `:wq`

#### Mouvement du curseur

* `k` - déplacer le curseur vers le **haut** ⬆️
* `j` - déplacer le curseur vers le **bas** `⬇️`
* `h` - déplacer le curseur vers la **gauche** ⬅️
* `l` - déplacer le curseur vers la **droite** ➡️
* `H` - déplacement vers le **haut** de l'écran ⬆️
* `M` - déplacement vers le **milieu** de l'écran&#x20;
* `L` - déplacement vers le **bas** de l'écran `⬇️`
* `gg` - aller à la **première ligne** du document ⏫
* `G` - aller à la **dernière ligne** du document ⏬

***

## GNU nano

{% embed url="https://www.nano-editor.org/" %}

GNU nano permet de lire et d'éditer des fichiers depuis votre terminal mais de façon plus accessible que VIM.

```bash
sudo dnf install nano # Installer sur Linux (Fedora)
```

### Liste de raccourcis

Toutes les commandes sont préfixées avec soit `^` ou `M`.&#x20;

* Le symbole caret (`^`) représente la touche`Ctrl` de vote clavier.&#x20;
* La lettre `M`représente la touche `Alt` de votre clavier.

Par exemple, pour `^J`les commandes signifient que l'appui sur `Ctrl`et `J` en même temps.

#### Sélectionner du texte

Pour sélectionner du texte, le copier et le coller :

1. Se déplacer avec les flèches ↑ ↓ ← → pour se placer à l'endroit voulu,
2. Faire Alt+A pour marquer le début de la sélection,
3. Se déplacer avec les flèches ↑ ↓ ← → pour sélectionner la zone de texte à copier,
4. Copier cette sélection avec Alt+^,
5. Se déplacer à l'endroit voulu pour le collage,
6. Coller avec Ctrl+U.

#### Raccourcis utiles

* `CTRL` + `A` : Permet d’aller au début de la ligne
* `CTRL` + `E` : Permet d’aller à la fin de la ligne
* `CTRL` + `Y` : Permet de remonter de page en page
* `CTRL` + `V` : Permet de descendre de page en page
* `CTRL` + `_` : Permet de se rendre au n° de ligne indiqué
* `CTRL` + `C` : Permet de savoir à quel n° de ligne / colonne / caractère se trouve votre curseur
* `CTRL` + `W` : Permet de faire une recherche
* `CTRL` + `D` : Permet de supprimer un caractère
* `CTRL` + `K` : Permet de supprimer une ligne complète (comme la commande dd sous Vi)
* `CTRL` + `O` : Permet de sauvegarder votre fichier
* `CTRL` + `X` : Permet de quitter nano
* `CTRL` + `G` : Affiche l’aide

***

## Fresh

{% embed url="https://getfresh.dev/" %}

Un éditeur de texte en ligne de commande moderne et complet, **sans aucune configuration requise**. Raccourcis clavier familiers, prise en charge de la souris et fonctionnalités dignes d'un IDE : aucune période d'apprentissage nécessaire.

#### Installation

<pre class="language-bash"><code class="lang-bash"><strong>curl -sL $(curl -s https://api.github.com/repos/sinelaw/fresh/releases/latest | grep "browser_download_url.*\.$(uname -m)\.rpm" | cut -d '"' -f 4) -o fresh-editor.rpm &#x26;&#x26; sudo rpm -U fresh-editor.rpm
</strong></code></pre>

Ou téléchargez le fichier `.deb` manuellement depuis la [page de téléchargement des versions](https://github.com/sinelaw/fresh/releases).

***

## curl

{% embed url="https://curl.se/" %}

cURL (_client URL request library_) est une [interface en ligne de commande](https://fr.wikipedia.org/wiki/Interface_en_ligne_de_commande), destinée à récupérer le contenu d'une ressource accessible sur internet. Il peut être utilisé en tant que client REST. cURL implémente l'interface utilisateur et repose sur la bibliothèque logicielle `libcurl`

```bash
sudo dnf install curl # Installer curl
```

***

## Htop

{% embed url="https://htop.dev/downloads.html" %}

**htop** est un moniteur système pour les systèmes d’exploitation type Unix très similaire à **top**, qui fonctionne également en mode Terminal, mais qui dispose d'un environnement en mode texte plus convivial que ce dernier.

```bash
sudo dnf install htop  # Installer htop
```

***

## Btop++

{% embed url="https://github.com/aristocratos/btop?ref=itsfoss.com" %}

Une alternative plus graphique à `top` ou `htop`

{% hint style="success" %}
Des thèmes sont également disponible : [https://github.com/aristocratos/btop](https://github.com/aristocratos/btop?ref=itsfoss.com#themes)
{% endhint %}

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf install btop  # Installer btop++
</strong></code></pre>

***

## GPing

{% embed url="https://github.com/orf/gping" %}

Une alternative graphique et plus complète (multipe hosts par exemple) à la commande `ping`

Après l'installation, lancer `gping` \<domaine.tld>

```bash
sudo dnf copr enable atim/gping -y && sudo dnf install gping  # Installer GPing
```

***

## EZA

{% embed url="https://eza.rocks/" %}

`eza` est une alternative moderne du programme de listage de fichiers `ls`. \
Il utilise des couleurs pour distinguer les types de fichiers et les métadonnées. Il connaît les liens symboliques, les attributs étendus et Git ! Enfin, il est petit, rapide et ne comporte qu'un seul binaire :)

Après l'installation, lancer `eza` à la place de commande `ls`.

Pour connaitre la liste complète des raccourcis, taper `eza --help`

```bash
sudo dnf install eza  # Installer eza
```

### Liste de raccourcis

<pre class="language-bash"><code class="lang-bash"><strong># La Base
</strong><strong>eza -l             # Vue liste
</strong>eza -l -T          # Vue liste avec arborescence

# Eléments
eza -l --grid      # Vue liste en colonnes
eza -l --icons     # Vue liste avec icones
eza -l --hyperlink # Vue liste avec hyperlien
eza -l --header    # Vue liste avec le header
eza -l --blocksize # Vue liste avec la taille des fichiers
eza -l --time-style "+%d/%m/%Y" # Vue liste avec la taille des fichiers

# Combinaisons (exemples)
eza -l --icons --hyperlink --header --blocksize --time-style "+%d/%m/%Y"    # Vue liste
eza -T -l --icons --hyperlink --header --blocksize --time-style "+%d/%m/%Y" # Vue liste avec avec arborescence

# GIT
eza -l --icons --hyperlink --header --time-style "+%d/%m/%Y" --git
eza -l --icons --hyperlink --header --time-style "+%d/%m/%Y" --git --git-repos-quotes'
</code></pre>

***

## Arsenal

{% embed url="https://github.com/Orange-Cyberdefense/arsenal" %}

Un outil pour créez un inventaire de vos commandes Linux favorites

```bash
python3 -m pip install arsenal-cli  # Installation avec pip

# Installation manuelle
git clone https://github.com/Orange-Cyberdefense/arsenal.git
cd arsenal
python3 -m pip install -r requirements.txt
./run

./addalias.sh # Inside your .bashrc or .zshrc add the path to run to help you do that you could launch the addalias.sh script
arsenal # Lancer l'application               
```

***

## sshx

{% embed url="https://sshx.io/" %}

`sshx` est une solution pour partager votre terminal en expérience collaborative. Vous pourrez ainsi partager votre terminal aussi facilement qu’un document Google Docs, avec un simple lien.

```bash
curl -sSf https://sshx.io/get | sh  # Installer  sshx
```

***

## SmokePing

{% embed url="https://oss.oetiker.ch/smokeping/" %}

**SmokePing** est un logiciel de surveillance réseau qui mesure et affiche graphiquement les temps de latence (temps de réponse) entre une machine et plusieurs autres cibles sur un réseau. Conçu par _Tobi Oetiker_, l'outil est libre et écrit en Perl.

#### Installation

```bash
sudo dnf install smokeping httpd fping rrdtool perl perl-FCGI perl-CGI perl-Config-Grammar

# smokeping : le logiciel
# httpd : serveur web Apache
# fping : pour envoyer rapidement des séries de pings
# rrdtool : gestion des bases de données de séries temporelles
# perl : le langage de programmation utilisé par SmokePing
## Modules Perl nécésssaires pour l’exécution des scripts SmokePing :
## perl-FCGI (FastCGI support)
## perl-CGI (support CGI)
## perl-Config-Grammar (parsing de fichier de configuration)
```

#### Lancement

```bash
sudo systemctl enable --now httpd
sudo systemctl start httpd
# Activer et Démarrer le serveur web Apache pour afficher l’interface web

sudo systemctl enable --now smokeping
sudo systemctl start smokeping
# Activer et lance Smokeping

sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
# Si le pare-feu est activé, s'assurez que le port 80 (HTTP) est ouvert

xdg-open http://localhost/cgi-bin/smokeping.cgi
# Ouvre le lien dans ton navigateur et remplace localhost par l'IP de ta machine
```

#### Configuration

Les fichiers de configuration se trouvent dans `/etc/smokeping/config.d/` :

* **General** : paramètre de base (nom, email, url cgi, etc.)
* **Targets** : machines à surveiller

{% hint style="warning" %}
Après une modification, toujours relancer le service
{% endhint %}

```bash
sudo systemctl restart httpd
# Redémarre le serveur web Apache pour afficher l’interface web
sudo systemctl restart smokeping
# Redémarre Smokeping
```

**Conseils utiles**

* Pour sécuriser l’accès web, configure un **virtualhost Apache avec restriction IP** ou un mot de passe
* Ajoute/modifie les cibles dans `/etc/smokeping/config.d/Targets` pour surveiller d’autres machines ou serveurs.

Tu devrais voir les graphiques générés par SmokePing après quelques minutes d’activité :)

***

## HL

{% embed url="https://github.com/pamburus/hl" %}

Visualiseur et processeur de journaux haute performance qui transforme les journaux aux formats JSON et logfmt en un format lisible par l'humain. Conçu pour une efficacité optimale, il permet une analyse rapide des fichiers journaux volumineux avec une surcharge minimale.

Download and extract using `curl` and `tar` on Linux (x86\_64)

```bash
curl -sSfL https://github.com/pamburus/hl/releases/latest/download/hl-linux-x86_64-musl.tar.gz | tar xz
```

***

## Tabview

{% embed url="https://github.com/shshemi/tabiew" %}

Tabiew est une application TUI légère qui permet aux utilisateurs de visualiser et d'interroger des fichiers de données tabulaires, tels que CSV, Parquet, Arrow, etc.

***

## Yazi

{% embed url="https://yazi-rs.github.io/" %}

Un gestionnaire de fichiers dans le terminal

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf copr enable lihaohong/yazi  # Activer le dépot copr/yazi 
</strong>sudo dnf install yazi  # Installer Yazi
</code></pre>

***

## **dua** (-> _Disk Usage Analyzer_)

{% embed url="https://lib.rs/crates/dua-cli" %}

Un visualiseur d'espace disque moderne dans le terminal

Linux exige que la cible soit spécifiée explicitement pour obtenir la version MUSL.

```bash
curl -LSfs https://raw.githubusercontent.com/Byron/dua-cli/master/ci/install.sh | \
    sh -s -- --git Byron/dua-cli --target x86_64-unknown-linux-musl --crate dua 
```

***

## csvlens

{% embed url="https://github.com/YS-L/csvlens" %}

Ouvrir un ficher `.csv` depuis le terminal car pourquoi pas après tout

### Liste de raccourcis

Exécutez le programme `csvlens` en fournissant le nom du fichier CSV :

```
csvlens <filename>
```

#### Raccourcis clavier

<table data-header-hidden><thead><tr><th width="222">Clé</th><th>Action</th></tr></thead><tbody><tr><td><strong>Raccourci</strong></td><td><strong>Action</strong></td></tr><tr><td><code>hjkl</code> (ou <code>← ↓ ↑ →</code>)</td><td>Défilez d'une ligne ou d'une colonne dans la direction indiquée.</td></tr><tr><td><code>Ctrl + f</code> (ou <code>Page Down</code>)</td><td>Faites défiler une fenêtre vers le bas</td></tr><tr><td><code>Ctrl + b</code> (ou <code>Page Up</code>)</td><td>Faites défiler d'une fenêtre vers le haut</td></tr><tr><td><code>Ctrl + d</code> (ou <code>d</code>)</td><td>Faites défiler la moitié de la fenêtre vers le bas</td></tr><tr><td><code>Ctrl + u</code> (ou <code>u</code>)</td><td>Faites défiler la moitié de la fenêtre vers le haut</td></tr><tr><td><code>Ctrl + h</code></td><td>Défilez d'une fenêtre vers la gauche</td></tr><tr><td><code>Ctrl + l</code></td><td>Défilez d'une fenêtre vers la droite</td></tr><tr><td><code>Ctrl + ←</code></td><td>Défilez vers la gauche jusqu'à la première colonne</td></tr><tr><td><code>Ctrl + →</code></td><td>Défilez vers la droite jusqu'à la dernière colonne</td></tr><tr><td><code>Ctrl + e</code></td><td>Afficher les lignes marquées sur la sortie standard et quitter</td></tr><tr><td><code>G</code> (ou <code>End</code>)</td><td>Aller en bas</td></tr><tr><td><code>g</code> (ou <code>Home</code>)</td><td>Retour en haut</td></tr><tr><td><code>n</code> (en mode Recherche)</td><td>Passer au résultat suivant</td></tr><tr><td><code>N</code> (en mode Recherche)</td><td>Aller au résultat précédent</td></tr><tr><td><code>TAB</code></td><td>Basculer entre les modes de sélection de lignes, de colonnes ou de cellules</td></tr><tr><td><code>></code></td><td>Augmenter la largeur de la colonne sélectionnée</td></tr><tr><td><code>&#x3C;</code></td><td>Réduire la largeur de la colonne sélectionnée</td></tr><tr><td><code>Shift + ↓</code>(ou <code>J</code>)</td><td>Trier les lignes ou inverser le sens du tri selon la colonne sélectionnée</td></tr><tr><td><code>Ctrl + j</code></td><td>Identique à ce qui précède, mais triez par ordre naturel (par exemple « fichier2 » &#x3C; « fichier10»).</td></tr><tr><td><code>y</code></td><td>Copier la ligne ou la cellule sélectionnée dans le presse-papiers</td></tr><tr><td><code>q</code></td><td>Sortie</td></tr></tbody></table>

***

## Miller

Marre de jongler avec des tas d'outils pour travailler avec vos fichiers CSV et JSON ? Miller est un outil permettant de requêter, manipuler ou reformater vos fichiers CSV / JSON de façons préciser depuis votre terminal avec des commandes sort, cut et join et une compréhension approfondie des formats de données structurés

{% embed url="https://github.com/johnkerl/miller" %}

```bash
yum install miller # Installer miller
```

