---
description: Setup pour langages de programmation sur Fedora
---

# 📑 Langages

## Python

<figure><img src="../../../.gitbook/assets/Python-Logo.png" alt=""><figcaption></figcaption></figure>

```bash
sudo dnf install python3		# Installing Python 3
sudo dnf install -y python2		# Installing Python 2

# If you have both versions installed,
# and you have an app that expects a specific version,
# use this command to set the correct one in the system path:

sudo alternatives --set python /usr/bin/python3 # To set Python3 as the default
sudo alternatives --set python /usr/bin/python3 # To set Python2 as the default
```

Source : [https://citizix.com/how-to-install-python-2-and-python-3-on-fedora-35/](https://citizix.com/how-to-install-python-2-and-python-3-on-fedora-35/)

## PHP

<figure><img src="../../../.gitbook/assets/php-server-integration-wysiwyg-html-editor-froala-10.png" alt=""><figcaption></figcaption></figure>

```bash
sudo dnf install php-cli			# PHP Installation
sudo dnf install phpunit composer               # PHPUnit for unit tests or Composer to manage dependencies of PHP projects
sudo dnf install php-mysqli			# PHP modules
sudo php --server localhost:8080 --docroot  .	# PHP Development Server
```

Source : [https://developer.fedoraproject.org/tech/languages/php/php-installation.html](https://developer.fedoraproject.org/tech/languages/php/php-installation.html)

## Rust

<figure><img src="../../../.gitbook/assets/rust-logo.png" alt=""><figcaption></figcaption></figure>

#### Rust

```bash
sudo dnf install rust cargo
```

{% hint style="info" %}
This will install the compiler (`rustc`), standard library, gdb support, documentation generator (`rustdoc`) and the package manager (`cargo`).
{% endhint %}

Source : [https://developer.fedoraproject.org/techa/languages/rust/rust-installation.html](https://developer.fedoraproject.org/techa/languages/rust/rust-installation.html)

#### rustup

rustup est un installateur pour le langage de programmation Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Source : [https://rustup.rs/](https://rustup.rs/)

#### rustlings

Le projet **rustlings** contient de petits exercices pour vous habituer à lire et à écrire du code Rust. Cela inclut la lecture et la réponse aux messages du compilateur

```bash
# find out the latest version at https://github.com/rust-lang/rustlings/releases/latest (on edit 5.2.1)
git clone -b 5.2.1 --depth 1 https://github.com/rust-lang/rustlings
cd rustlings
cargo install --force --path .
```

Source : [https://github.com/rust-lang/rustlings#manually](https://github.com/rust-lang/rustlings#manually)

## Ruby

<figure><img src="../../../.gitbook/assets/Ruby-logo (1).png" alt=""><figcaption></figcaption></figure>

#### Dépendances

Avant d'installer Ruby, installons [`rbenv`](https://github.com/sstephenson/rbenv), un software qui installe et manage les environnements `ruby`. La première étape consiste à installer les dépendances pour Ruby.

```bash
sudo dnf install git-core zlib zlib-devel gcc-c++ patch readline readline-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison curl sqlite-devel
```

#### rbenv

Maintenant installons _**rbenv**_

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

```bash
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
exec $SHELL
```

#### Ruby

Maintenant, nous sommes êtes prêt à installer _**ruby**_ et à définir la version par défaut.

```bash
rbenv install 3.1.2    # Install ruby
rbenv global 3.1.2     # Define version to use by default
exec $SHELL            # Reset your terminal
ruby --version         # Check your Ruby version
```

{% hint style="success" %}
Si le message commence par `ruby 3.1.2p` , continuez 👍
{% endhint %}

#### gems

Installons maintenant quelques gems 🤗

```bash
gem install bundler colored faker http pry-byebug rake rest-client rspec rubocop-performance sqlite3
```

{% hint style="info" %}
Si vous préférez le faire gem par gem c'est possible 😎👍
{% endhint %}

```bash
gem install bundler                # Bundler             https://bundler.io/
gem install colored                # Colored             https://github.com/defunkt/colored
gem install faker                  # Faker               https://github.com/faker-ruby/faker
gem install http                   # http                https://github.com/httprb/http
gem install pry-byebug             # Pry-byebug          https://github.com/deivid-rodriguez/pry-byebug
gem install rake                   # Rake                https://github.com/ruby/rake
gem install rest-client            # Rest Client         https://github.com/rest-client/rest-client
gem install rspec                  # rspec               https://github.com/rspec/rspec-metagem
gem install rubocop-performance    # Rubocop-Performance https://github.com/rubocop/rubocop-performance
gem install sqlite3                # SQLite 3            https://github.com/sparklemotion/sqlite3-ruby
```

{% hint style="success" %}
Si le message `xx gems installed`, s'affiche tout est bon 👍
{% endhint %}

{% hint style="danger" %}
N'installez **JAMAIS** une gemme avec `sudo gem install`! Même si vous tombez sur une réponse de Stackoverflow (ou le terminal) vous indiquant de le faire.
{% endhint %}

#### Bundler

```bash
sudo dnf install rubygem-bundler
```

{% hint style="success" %}
La commande **`bundle`**devrait être ensuite disponible sur votre système.
{% endhint %}

## Ruby on Rails

<figure><img src="../../../.gitbook/assets/Ruby_On_Rails_Logo.svg.png" alt=""><figcaption></figcaption></figure>



#### Installation avec RubyGems.org

{% hint style="info" %}
**Pré-requis :** Pour installer Rails, vous devez d'abord avoir installer Ruby et les packages:\
`ruby-devel`, `gcc`, `zlib-devel` et ensuite installons rails en utilisant la gem
{% endhint %}

```bash
sudo dnf install rubygem-rails  	# Install Rubygem with RubyGems.org
sudo dnf group install 'Ruby on Rails'	# Install Rails framework
```

Source : [https://developer.fedoraproject.org/tech/languages/ruby/ror-installation.html](https://developer.fedoraproject.org/tech/languages/ruby/ror-installation.html)\
Alternative : [https://github.com/rails/rails#getting-started](https://github.com/rails/rails#getting-started)

## Flutter

<figure><img src="../../../.gitbook/assets/Google-flutter-logo.svg.png" alt=""><figcaption></figcaption></figure>

```bash
sudo snap install flutter --classic	# Install Flutter using SnapStore
flutter sdk-path			# Display your Flutter SDK path
```

Source : [https://docs.flutter.dev/get-started/install/linux](https://docs.flutter.dev/get-started/install/linux)

## Node.JS

<figure><img src="../../../.gitbook/assets/2560px-Node.js_logo.svg.png" alt=""><figcaption></figcaption></figure>

#### NodeJS

Démarrons l'installation avec cette commande :&#x20;

```bash
sudo dnf install nodejs
```

Lorsque l'installation est terminé, taper :&#x20;

```bash
node --version
```

{% hint style="success" %}
Si le message affiche `v16.15.1` ou autre version, vous pouvez continuer
{% endhint %}

#### nvm

nvm est manager de version de Node. Il fonctionne sur n'importe quel shell compatible POSIX (sh, dash, ksh, zsh, bash), en particulier sur les plateformes suivantes : UNIX, macOS, et windows WSL.

**Installons nvm** par le script d'installation

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
```

```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bashbas
```

L'exécution de l'une des commandes ci-dessus télécharge un script et l'exécute. Le script **clone le dépôt** nvm dans /.nvm, et tente d'ajouter les lignes sources de l'extrait ci-dessous **au bon fichier de profil** (/.bash\_profile, \~/.zshrc, \~/.profile, ou \~/.bashrc).

```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

**Vérifier l'installation**

```bash
command -v nvm
```

{% hint style="success" %}
En cas de réussite, `nvm` devrait afficher.
{% endhint %}

Source : [https://developer.fedoraproject.org/tech/languages/nodejs/nodejs.html](https://developer.fedoraproject.org/tech/languages/nodejs/nodejs.html) & [https://github.com/nvm-sh/nvm/blob/master/README.md#installing-and-updating](https://github.com/nvm-sh/nvm/blob/master/README.md#installing-and-updating)

#### yarn

<figure><img src="../../../.gitbook/assets/yarn_image.png" alt=""><figcaption></figcaption></figure>

Installons maintenant yarn, le gestionnaire de paquets pour installer des bibliothèques JavaScript.

```bash
sudo dnf install yarnpkg
```

Ensuite, exécutez la commande suivante :

```bash
yarn --version
```

{% hint style="success" %}
Si le message affiche `v1.22.17` ou autre version, vous pouvez continuer
{% endhint %}

#### npm

<figure><img src="../../../.gitbook/assets/Npm-logo.png" alt=""><figcaption></figcaption></figure>

#### **Installation de modules NPM**

Pour installer des modules supplémentaires à partir des dépôts Fedora :

```bash
sudo dnf install 'npm(module-name)'       # Method 1
sudo dnf install nodejs-<module-name>     # Method 2
```

Source : [https://developer.fedoraproject.org/tech/languages/nodejs/modules.html](https://developer.fedoraproject.org/tech/languages/nodejs/modules.html)

#### **Installation global modules**

Créez un répertoire pour les installations globales dans votre répertoire personnel

```bash
mkdir ~/.npm-global
```

Définissez le nouveau chemin du répertoire pour **npm**

```bash
npm config set prefix '~/.npm-global'.
```

Ouvrez/créez le fichier \~/.profile et ajoutez la ligne suivante

```bash
export PATH=~/.npm-global/bin:$PATH
```

Mettez à jour vos variables système avec cette commande

```bash
source ~/.profile
```

## JAVA

<figure><img src="../../../.gitbook/assets/Java.png" alt=""><figcaption></figcaption></figure>

#### Gradle

{% hint style="info" %}
**Pré-requis** : nécéssite le gestionnaire de paquet SDKMAN!
{% endhint %}

#### Installation de gradle

```bash
sdk install gradle 7.6
```

Source : [https://gradle.org/install/](https://gradle.org/install/)

#### SDKMAN!

Installation via le gestionnaire de paquet SDKMAN!

```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

Ensuite, exécutez la commande suivante :

```bash
sdk version
```

{% hint style="success" %}
Si le message affiche `v5.16.0` ou autre version, vous pouvez continuer
{% endhint %}

Source : [https://sdkman.io/install](https://sdkman.io/install)

#### WAR

work in progress section

## Scala

<figure><img src="../../../.gitbook/assets/ezgif.com-webp-to-jpg-2.jpg" alt=""><figcaption></figcaption></figure>

Installation de SCALA

{% hint style="info" %}
Pré-requis : nécéssite le gestionnaire de paquet SDKMAN!
{% endhint %}

```bash
sdk install scala
```

#### SBT

Install SBT

<pre class="language-bash"><code class="lang-bash">sudo rm -f /etc/yum.repos.d/bintray-rpm.repo    	      # Remove old Bintray repo file
<strong>curl -L https://www.scala-sbt.org/sbt-rpm.repo > sbt-rpm.repo
</strong>sudo mv sbt-rpm.repo /etc/yum.repos.d/
sudo dnf install sbt										 # Install SBT
</code></pre>

Source : [https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html](https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html)
