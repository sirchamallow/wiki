---
description: Outils pour serveurs
icon: server
---

# OPS

## Netdata

Si vous gérez votre petit serveur dédié et que pour vous, le suivi des performances en temps réel de celui-ci est important, sachez qu’il existe un outil de monitoring nommé **Netdata** qui permet de surveiller à la seconde près des tas de paramètres. \
\
L'avantage, c’est que Netdata propose des dashboard plutôt jolies 🤩

#### Installation manuel

```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh) all # Download and install Netdata 
systemctl start netdata 				# Start the Netdata service
systemctl enable netdata 				# Now make service enable so that on boot up it start automatically
systemctl status netdata 				# Now check the status
firewall-cmd --permanent --add-port=19999/tcp 		# Allow Netdata default port to pass through firewall
firewall-cmd --reload 					# Reload the firewall
https//server-ip:19999					# Open browser and go to you server ip
```

{% embed url="https://www.linuxhelp.com/how-to-install-netdata-on-fedora-34" %}

#### Installation via kickstart.sh

```bash
curl https://my-netdata.io/kickstart.sh > /tmp/netdata-kickstart.sh && sh /tmp/netdata-kickstart.sh
```

{% embed url="https://learn.netdata.cloud/docs/agent/packaging/installer/methods/kickstart" %}

***

## Ansible

{% embed url="https://docs.ansible.com/ansible/2.9/installation_guide/intro_installation.html#installing-ansible-on-rhel-centos-or-fedora" %}

#### Installation

```bash
sudo dnf install ansible
```

***

## WireGuard

{% embed url="https://www.wireguard.com/install/#fedora-tools" %}

#### Installation

```bash
sudo dnf install wireguard-tools
```

### WireGuard Easy

Le moyen le plus simple d’installer et de gérer WireGuard sur n’importe quel hôte Linux :)

{% embed url="https://github.com/wg-easy/wg-easy" %}

***

## RabbitMQ

RabbitMQ utilise le protocole AMQP (Advanced Message Queuing Protocol) pour envoyer des messages en toute sécurité via des agents de messages. Un agent de messages se compose d'échanges et de files d'attente.

#### Installation

<pre class="language-bash"><code class="lang-bash"># Add YUM repository using bash script
curl -s https://packagecloud.io/install/repositories/rabbitmq/erlang/script.rpm.sh | sudo bash

# Update system YUM repositories
sudo yum clean all &#x26;&#x26; sudo yum makecache -y

# Install Erlang on Fedora
sudo yum install erlang

# Add RabbitMQ Yum repositor
curl -s https://packagecloud.io/install/repositories/rabbitmq/rabbitmq-server/script.rpm.sh | sudo bash

# The last step is the actual installation of RabbitMQ
sudo yum install rabbitmq-server

# Confirm version of RabbitMQ installed
rpm -qi rabbitmq-server

# Start RabbitMQ Service
sudo systemctl start rabbitmq-server
sudo systemctl enable rabbitmq-server
# Confirm service status
<strong>systemctl status  rabbitmq-server
</strong></code></pre>

{% embed url="https://computingforgeeks.com/installing-rabbitmq-on-centos-fedora/" %}

{% embed url="https://www.rabbitmq.com/install-rpm.html#install-erlang" %}

***

## Mozilla SSL Configuration Generator

<figure><img src="../../.gitbook/assets/Capture d’écran du 2024-01-10 17-31-03.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://ssl-config.mozilla.org" %}

**Mozilla SSL Configuration Generator** est un outil gratuit de la fondation Mozilla qui permet de générer des configurations SSL/TLS sécurisées pour des serveurs web.

Le site propose trois configurations différentes, en fonction des besoins du serveur :

* **Modern** : cette configuration est recommandée pour les serveurs qui ne nécessitent pas de compatibilité avec des clients très anciens. Elle utilise les protocoles `TLS 1.3` et `TLS 1.2`, ainsi que les algorithmes de chiffrement les plus sûrs.
* **Intermediate** : cette configuration est recommandée pour la plupart des serveurs web. Elle utilise les protocoles `TLS 1.3`, `TLS 1.2` et `TLS 1.1`, ainsi que les algorithmes de chiffrement les plus sûrs, à l'exception de certains qui ne sont pas compatibles avec tous les clients.
* **Old** : cette configuration est recommandée uniquement pour les serveurs web qui nécessitent une compatibilité avec des clients très anciens. Elle utilise les protocoles `TLS 1.2`, `TLS 1.1` et `TLS 1.0`, ainsi que certains algorithmes de chiffrement plus anciens qui ne sont pas recommandés pour une sécurité optimale.

Pour utiliser le site, il suffit de renseigner quelques informations sur le serveur, la version du logiciel, la version d'OpenSSL utilisée et les exigences en matière de compatibilité avec les clients. Le site générera alors un fichier de configuration SSL/TLS prêt à être utilisé :tada:
