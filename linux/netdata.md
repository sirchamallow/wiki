# Netdata

{% hint style="info" %}
Ceci est un article du 31/03/2016 de **Korben**. L’article est sous license Creative Commons [**BY-NC-ND 4.0 International**](https://creativecommons.org/licenses/by-nc-nd/4.0/deed.fr). Vous pouvez également lire l’article sur [son blog](https://korben.info/outil-surveiller-temps-reel-performances-de-machine-linux.html). _**Bonne lecture !**_
{% endhint %}

Si vous gérez votre petit serveur dédié et que pour vous, le suivi des performances en temps réel de celui-ci est important, sachez qu’il existe un outil de monitoring nommé **Netdata** qui permet de surveiller à la seconde près des tas de paramètres tels que :

* L’utilisation des CPU
* L’utilisation de la mémoire \(RAM, swap…etc.\)
* Les I/O des disques
* Les interfaces réseau \(bande passante, paquets, erreurs, drops…etc.\)
* Les connexions au firewall iptables / netfilter
* Les processus \(en cours, bloqués, forks…etc.\)
* Les applications systèmes et leur consommation de CPU, mémoire, swap, disque…etc.\)
* L’utilisation d’Apache / Nginx
* L’utilisation de MySQL \(requêtes, locks, threads…Etc.\)
* La queue du serveur mail Postfix
* La bande passante utilisée par le proxy Squid et les requêtes reçues
* La température, le voltage, la vitesse des ventilos, l’humidité…etc. du matos
* Les appareils SNMP

Le plus cool là-dedans, c’est que Netdata est plutôt joli. Voici quelques écrans animés :

![](../.gitbook/assets/image%20%2814%29.png)

![](../.gitbook/assets/image%20%2818%29.png)

![](../.gitbook/assets/image%20%286%29.png)

![](../.gitbook/assets/image%20%2820%29.png)

## Pour l’installer sous Ubuntu / Debian, il suffit d’entrer la commande suivante pour installer les dépendances :

> apt-get install zlib1g-dev gcc make git autoconf autogen automake pkg-config

### Puis cloner le depot git :

> git clone https://github.com/firehol/netdata.git –depth=1

### Et lancer le script d’install :

> cd netdata ./netdata-installer.sh

### Enfin, il suffit de lancer netdata comme ceci :

> /usr/sbin/netdata

### Et il sera accessible depuis l’IP de votre serveur sur le port 19999

> http://127.0.0.1:19999/

enfin, pour la mise à jour régulière de netdata, il suffit de refaire un « git pull » à l’endroit où vous avez récupéré le dépôt git, puis de relancer le script d’install netdata-installer.sh.

C’est aussi simple que ça ! Et si vous voulez plus d’infos, [toute la doc se trouve ici.](https://github.com/firehol/netdata/)

[Source](http://www.tecmint.com/netdata-real-time-linux-performance-network-monitoring-tool/)

