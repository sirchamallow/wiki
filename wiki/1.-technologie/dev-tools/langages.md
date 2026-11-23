---
description: Setup pour langages de programmation sur Fedora
icon: python
---

# Langages

## Python

{% embed url="https://wiki.python.org/python/getting-started/BeginnersGuide/Download.html" %}

```bash
sudo dnf install python3		  # Installer Python 3 sur Fedora
sudo dnf install -y python2		# Installer Python 2 sur Fedora

# If you have both versions installed,
# and you have an app that expects a specific version,
# use this command to set the correct one in the system path:

sudo alternatives --set python /usr/bin/python3 # To set Python3 as the default
sudo alternatives --set python /usr/bin/python3 # To set Python2 as the default
```

***

## PHP

{% embed url="https://www.php.net/downloads.php?os=linux&osvariant=linux-fedora&version=default" %}

```bash
sudo dnf install php-cli			                # PHP Installation
sudo dnf install phpunit composer             # PHPUnit for unit tests or Composer to manage dependencies of PHP projects
sudo dnf install php-mysqli			              # PHP modules
sudo php --server localhost:8080 --docroot  .	# PHP Development Server
```

***

## Rust

{% embed url="https://rust-lang.org/fr/tools/install/" %}

### Rust

{% embed url="https://developer.fedoraproject.org/techa/languages/rust/rust-installation.html" %}

{% hint style="info" %}
This will install the compiler (`rustc`), standard library, gdb support, documentation generator (`rustdoc`) and the package manager (`cargo`).
{% endhint %}

```bash
sudo dnf install rust cargo # Installer Rust sur Fedora
```

### rustup

{% embed url="https://rustup.rs/" %}

rustup est un installateur pour le langage de programmation Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh # Installer Rustup sur Fedora
```

### rustlings

{% embed url="https://rustlings.rust-lang.org/setup/#installing-rustlings" %}

Le projet **rustlings** contient de petits exercices pour vous habituer à lire et à écrire du code Rust. Cela inclut la lecture et la réponse aux messages du compilateur

```bash
# Pré-requis : Assurez-vous d'avoir gcc installé (un éditeur de liens ).
sudo dnf install gcc # Installer GCC

cargo install rustlings # téléchargera et compilera Rustlings
rustlings init            # initialiser le rustlings/répertoire 

```

***

## Ruby

{% embed url="https://www.ruby-lang.org/en/documentation/installation/" %}

Ruby peut s'installer en une commande via le gestionnaire de paquets :&#x20;

```bash
sudo yum install ruby # Installer la dernière version de ruby
```

Mais la plupart des développeurs préfèrent le **compiler** avec `rbenv`. Cela permet de choisir la version exacte et de changer de version par projet. En contrepartie, il faut installer au préalable les outils et bibliothèques nécessaires à la compilation.

Voici un setup type pour une machine **Fedora** avec **rbenv, Ruby** et le framework **Rails + PostgreSQL**

### rbenv

{% embed url="https://rbenv.org/" %}

Maintenant, nous sommes êtes prêt à installer _**ruby**_ et à définir la version par défaut.

```bash
# Installer rbenv
curl -fsSL https://rbenv.org/install.sh | bash # Installer rbenv
rbenv --version                                # Vérifier la version de rbenv

# Ajouter l'initialisation de rbenv à votre terminal
echo 'eval "$(rbenv init - bash)"' >> ~/.bashrc # bash
source ~/.bashrc                                # bash
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc   # ZSH
source ~/.zshrc                                 # ZSH

# Installer Ruby avec rbenv
rbenv install -l (or rbenv install --list) # Liste les version de ruby stable disponible
rbenv install 4.x.x                        # Install une version spécifique de ruby
rbenv global 4.x.x                         # Definir la version que vous aller utiliser par défaut
exec $SHELL                                # Redémarrer votre terminal
ruby --version                             # Vérifier la version de Ruby
```

### Bundler

{% embed url="https://guides.rubygems.org/command-reference/bundle-install/" %}

Installer Bundler (**la seule gem à installer globalement**). Bundler gère les dépendances Ruby d'un projet à partir du `Gemfile`.&#x20;Il installe les versions nécessaires et utilise `Gemfile.lock` pour garantir des versions cohérentes.

```bash
gem install bundler # Installer Bundler
```

### Ruby on Rails

{% embed url="https://rubyonrails.org/" %}

Rails est le framework du langage Ruby

{% hint style="info" %}
**Pré-requis** : Installez les dépendances de compilation (`git`, `curl`, `gcc`, `libyaml-devel`, etc.) nécéssaire à Rails
{% endhint %}

```bash
sudo dnf install -y gcc gcc-c++ make patch redhat-rpm-config ruby-devel \
  libyaml-devel openssl-devel zlib-devel libffi-devel readline-devel \
  libxml2-devel libxslt-devel sqlite-devel postgresql-devel mysql-devel 
```

**Détails des dépendances**

**Outils de compilation et environnement Ruby**

* `gcc` et `gcc-c++` : compilateurs C et C++ de GNU pour compiler le code natif intégré dans de nombreuses gems populaires (comme le [serveur web puma](https://puma.io/)).&#x20;
* `make` : Orchestre la compilation à partir des fichiers Makefile générés automatiquement lors de l'installation des gems.
* `patch` : Permet d'appliquer des correctifs automatiques au code source pendant la compilation de Ruby ou de ses extensions.&#x20;
* `redhat-rpm-config` : macros et drapeaux de compilation spécifiques à Fedora. Sans ce paquet, la compilation d'extensions natives échoue souvent sur des erreurs de configuration de sécurité du compilateur.&#x20;
* `ruby-devel` : Fournit les fichiers d'en-tête (ruby.h) du Ruby fourni par Fedora, permettant aux compilateurs C/C++ d'interagir avec l'interpréteur système.

**Bibliothèques système fondamentales**

* `libyaml-devel` : Nécessaire à la gem `psych` pour lire et analyser les fichiers `YAML`, omniprésents dans Rails (database.yml, credentials.yml.enc, etc.).&#x20;
* `openssl-devel` : Indispensable à l'extension openSSL de Ruby pour gérer le chiffrement, les connexions HTTPS/TLS et le téléchargement sécurisé des gems.&#x20;
* `zlib-devel` : Gère la compression et la décompression de données (extraction des archives `.gem` et compression HTTP gzip).
* `libffi-devel` : Permet à Ruby d'appeler directement des fonctions issues de bibliothèques C externes via la gem ffi.
* `readline-devel` : Gère l'historique et l'édition de lignes dans le terminal, rendant la console interactive (rails console ou irb) utilisable avec les flèches directionnelles et l'autocomplétion.

**Parsing HTML/XML et bases de données**

* `libxml2-devel` et `libxslt-devel` : Bibliothèques C requises pour compiler la gem nokogiri depuis les sources, utilisée par Rails pour analyser et transformer le HTML/XML.&#x20;
* `sqlite-devel` : Requis pour compiler la gem `sqlite3`, la base de données configurée par défaut lors de la création d'un nouveau projet Rails.
* `postgresql-devel` (alias `libpq-devel`) : Fournit la bibliothèque client nécessaire à la gem `pg` si vous utilisez PostgreSQL.

**Installer le Framework Rails**

```bash
gem install rails                  # Installer le framework Rails
rails --version                    # Verifier la version de Rails
```

***

### gems

Les paquets Ruby sont appelés des **gems**. Elles sont gérer par **RubyGems** qui est le **gestionnaire de paquets de Ruby**. On peut le comparer à `dnf` pour Fedora, `pip` pour Python ou `npm` pour Node.js.

La commande `gem` est fournie par **RubyGems**, lui-même inclus avec les installations modernes de Ruby.

{% hint style="danger" %}
N'installez **JAMAIS** une gemme avec `sudo gem install`! Même si vous tombez sur une réponse de Stackoverflow (ou le terminal) vous indiquant de le faire.
{% endhint %}

```bash
# Installer d'autres gem (à faire pour chaque nouveau projet)
gem install colored                # Colored             https://github.com/defunkt/colored
gem install http                   # http                https://github.com/httprb/http
gem install rake                   # Rake                https://github.com/ruby/rake
gem install rspec                  # rspec               https://github.com/rspec/rspec-metagem
gem install rubocop-performance    # Rubocop-Performance https://github.com/rubocop/rubocop-performance
```

{% hint style="success" %}
Si le message `xx gems installed`, s'affiche tout est bon 👍
{% endhint %}

{% hint style="info" %}
Si vous préférez faire l'installation gem par gem c'est possible 😎👍
{% endhint %}

***

## Flutter

{% embed url="https://docs.flutter.dev/platform-integration/linux/setup" %}

```bash
sudo snap install flutter --classic	# Install Flutter using SnapStore
flutter sdk-path			# Display your Flutter SDK path
```

***

## Node.JS

{% embed url="https://nodejs.org/fr" %}

```bash
sudo dnf install nodejs # Installer NodeJS & npm
node --version          # Vérifier la version de nodejs
command -v nvm          # Vérifier la version de npm

# Yarn, gestionnaire de paquets pour installer des bibliothèques JavaScript.
sudo dnf install yarnpkg # Installer Yarn
yarn --version           # Vérifier la version de Yarn
```

### nvm

{% embed url="https://github.com/nvm-sh/nvm#installing-and-updating" %}

nvm est le manager de version de NodeJS. Il fonctionne sur n'importe quel shell compatible POSIX (sh, dash, ksh, zsh, bash), en particulier sur les plateformes suivantes : UNIX, macOS, et windows WSL.

***

## JAVA

### Gradle

{% embed url="https://gradle.org/install/" %}

{% hint style="info" %}
**Pré-requis** : nécéssite le gestionnaire de paquet SDKMAN!
{% endhint %}

```bash
sdk install gradle 7.6 # Installer Gradle
```

### SDKMAN!

{% embed url="https://sdkman.io/install" %}

Installation via le gestionnaire de paquet SDKMAN!

```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk version  # Installer SDK
```
