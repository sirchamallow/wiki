# 🥞 Base de données

## Redis

<figure><img src="../../../.gitbook/assets/langfr-2560px-Redis_Logo.png" alt="" width="375"><figcaption></figcaption></figure>

```bash
sudo dnf install redis     		# Install redis cli and server
sudo systemctl start redis	 	# Initialize redis server
sudo systemctl enable redis 	        # To start redis on boot, run
```

Source : [https://developer.fedoraproject.org/tech/database/redis/about.html](https://developer.fedoraproject.org/tech/database/redis/about.html)

## PostgreSQL

<figure><img src="../../../.gitbook/assets/postgresql.png" alt="" width="375"><figcaption></figcaption></figure>

#### Installation

```bash
# Install the repository RPM:
sudo dnf install -y https://download.postgresql.org/pub/repos/yum/reporpms/F-36-x86_64/pgdg-fedora-repo-latest.noarch.rpm

# Install PostgreSQL:
sudo dnf install -y postgresql15-server

# Optionally initialize the database and enable automatic start:
sudo /usr/pgsql-15/bin/postgresql-15-setup initdb
sudo systemctl enable postgresql-15
sudo systemctl start postgresql-15
```

Source : [https://www.postgresql.org/download/linux/redhat/](https://www.postgresql.org/download/linux/redhat/)

#### Quelques raccourcis utiles (cheatsheet)

```bash
\q    # Quitter la base de donnée
\duf+ # Liste des utilisateurs & leurs droits
\?    # Voir toutes les commandes posgres
\l    # Liste de toutes les base de données
\dt   # Voir toutes les tables de la db
\h    # Voir toutes les commandes SQL
SELECT version(); # Identifier la version de postgres installer
```

#### Désinstallation

Vous pouvez utilisez la commande DNF suivante pour désinstaller PostgreSQL depuis une distribution Fedora

```bash
sudo dnf remove postgresql
```

Vous pouvez utiliser un opérateur (\*) afin de supprimer tous les paquets dont le nom commence par postgres en utilisant la commande suivante :

```bash
sudo dnf remove postgres\*
```

Source : [https://kb.objectrocket.com/postgresql/how-to-completely-uninstall-postgresql-757](https://kb.objectrocket.com/postgresql/how-to-completely-uninstall-postgresql-757)

### PG-CLI

```bash
sudo yum install python-pip
sudo pip install pgcli
```

Source : [https://www.pgcli.com/install](https://www.pgcli.com/install)&#x20;

## MySQL

<figure><img src="../../../.gitbook/assets/mysql.png" alt="" width="375"><figcaption></figcaption></figure>

**Installation**

Mettez à jour votre Fedora pour vous assurer que tous les paquets existants sont à jour

```bash
sudo dnf upgrade --refresh -y
```

Installer MySQL

```bash
sudo dnf install community-mysql-server
```

Vérifier la version de MySQL

```bash
mysql --version
```

{% hint style="success" %}
Si le message affiche `v8.0` ou autres version, vous pouvez continuer
{% endhint %}

Commandes

```bash
sudo systemctl enable mysqld   # Active le service
sudo systemctl start mysqld    # Démarrre le service
sudo systemctl restart mysqld  # Redémarrer le service
```

Configurer MySQL avant la première utilisation

```bash
sudo mysql_secure_installation
```

Utiliser MySQL

```bash
sudo mysql -u root -p
```

**Désinstallation**

```bash
sudo dnf remove community-mysql-server
```

Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-mysql-mariadb/](https://docs.fedoraproject.org/en-US/quick-docs/installing-mysql-mariadb/)

## SQLite

<figure><img src="../../../.gitbook/assets/sqlite.png" alt="" width="250"><figcaption></figcaption></figure>

Mettez à jour votre Fedora pour vous assurer que tous les paquets existants sont à jour

```bash
sudo dnf upgrade --refresh -y
```

Ensuite procéder à l'installation

```bash
sudo dnf install sqlite
```

Vérifier la version de SQL Lite installer

```bash
sqlite3 --version
```

{% hint style="success" %}
Si le message affiche `v3.36.0` ou autre version, vous pouvez continuer
{% endhint %}

Source : [https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/](https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/)

## S3cmd

S3cmd est un outil de ligne de commande gratuit et un client pour télécharger, récupérer et gérer des données dans Amazon S3 et d'autres fournisseurs de services de stockage cloud qui utilisent le protocole S3, tels que Clever Cloud ou Google Cloud Storage. L'outil est un projet open source écrit en Python disponible sous licence publique GNU v2 (GPLv2).

#### Installation de S3cmd à partir de PyPA (Python Package Authority)

S3cmd peut être installé à partir de PyPA en utilisant PIP (l'outil recommandé pour PyPA).

{% hint style="info" %}
Vérifions d'abord si PIP est déjà installer sur votre machine
{% endhint %}

```bash
sudo yum install python-pip
```

Installation via PIP

```bash
sudo pip install s3cmd
```

