# 📟 Terminal

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

<figure><img src="../../../.gitbook/assets/dog-screenshot.png" alt=""><figcaption></figcaption></figure>

### **Description**

dog est un client DNS en ligne de commande comme dig. Il utilise une syntax colorée qui comprend la syntaxe normale des arguments en ligne de commande. Le client supporte les protocoles DNS-over-TLS et DNS-over-HTTPS, et peut émettre du JSON.

### Installation

```bash
sudo dnf install snapd		      # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap  # Enable classic snap support, enter the following to create a symbolic link
sudo snap install dog		      # Install dog
```

{% hint style="info" %}
Source : [https://snapcraft.io/install/dog/fedora](https://snapcraft.io/install/dog/fedora)
{% endhint %}

{% hint style="success" %}
Site web : [https://github.com/ogham/dog](https://github.com/ogham/dog)&#x20;
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

