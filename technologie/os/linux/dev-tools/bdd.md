---
icon: database
---

# Base de données

## Redis

<figure><img src="../../../../.gitbook/assets/langfr-2560px-Redis_Logo.png" alt="" width="375"><figcaption></figcaption></figure>

```bash
sudo dnf install redis     		# Install redis cli and server
sudo systemctl start redis	 	# Initialize redis server
sudo systemctl enable redis 	        # To start redis on boot, run
```

{% hint style="info" %}
Source : [https://developer.fedoraproject.org/tech/database/redis/about.html](https://developer.fedoraproject.org/tech/database/redis/about.html)
{% endhint %}

#### Interface graphique pour Redis

* RedisInsight : [https://redis.com/fr/redis-enterprise/redisinsight/](https://redis.com/fr/redis-enterprise/redisinsight/)
* Redis-commander : [https://github.com/joeferner/redis-commander](https://github.com/joeferner/redis-commander)
* Redis-UI : [https://github.com/patrikx3/redis-ui](https://github.com/patrikx3/redis-ui)

***

## PostgreSQL

<figure><img src="../../../../.gitbook/assets/postgresql.png" alt="" width="375"><figcaption></figcaption></figure>

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

{% hint style="info" %}
Source : [https://www.postgresql.org/download/linux/redhat/](https://www.postgresql.org/download/linux/redhat/)
{% endhint %}

### Rccourcis utiles (cheatsheet)

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

{% hint style="info" %}
Source : [https://kb.objectrocket.com/postgresql/how-to-completely-uninstall-postgresql-757](https://kb.objectrocket.com/postgresql/how-to-completely-uninstall-postgresql-757)
{% endhint %}

### PG-CLI

```bash
sudo yum install python-pip
sudo pip install pgcli
```

{% hint style="info" %}
Source : [https://www.pgcli.com/install](https://www.pgcli.com/install)&#x20;
{% endhint %}

***

## MySQL

<figure><img src="../../../../.gitbook/assets/mysql.png" alt="" width="375"><figcaption></figcaption></figure>

### **Installation**

Mettez à jour votre Fedora pour vous assurer que tous les paquets existants sont à jour

```bash
sudo dnf upgrade --refresh -y
```

#### Installer MySQL

```bash
sudo dnf install community-mysql-server
```

### Vérifier la version

```bash
mysql --version
```

{% hint style="success" %}
Si le message affiche `v8.0` ou autres version, vous pouvez continuer
{% endhint %}

### Commandes

```bash
sudo systemctl start mysqld    # Démarrre le service
sudo systemctl enable mysqld   # Active le service
sudo systemctl restart mysqld  # Redémarrer le service
```

### Configurer MySQL avant la première utilisation

```bash
sudo mysql_secure_installation
```

### Utiliser MySQL

```bash
sudo mysql -u root -p
```

### **Désinstallation**

```bash
sudo dnf remove community-mysql-server
```

{% hint style="info" %}
Source : [https://docs.fedoraproject.org/en-US/quick-docs/installing-mysql-mariadb/](https://docs.fedoraproject.org/en-US/quick-docs/installing-mysql-mariadb/)
{% endhint %}

***

## SQLite

<figure><img src="../../../../.gitbook/assets/sqlite.png" alt="" width="250"><figcaption></figcaption></figure>

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

{% hint style="info" %}
Source : [https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/](https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/)
{% endhint %}

***

## MongoDB

<figure><img src="../../../../.gitbook/assets/MDB_BIG.png" alt="" width="375"><figcaption></figcaption></figure>

### **Installation**

```bash
sudo dnf -y install mongodb-org
```

### Vérifier la version

```bash
mongo --version
```

{% hint style="success" %}
Si le message affiche v4.4.4 ou autre version, vous pouvez continuer
{% endhint %}

### Commandes

<pre class="language-bash"><code class="lang-bash">sudo systemctl start mongod.service  # Démarrre le service
sudo systemctl enable mongod.service # Active le service
<strong>sudo systemctl status mongod.service  # Vérifier l'état du service
</strong></code></pre>

{% hint style="info" %}
Source : [https://computingforgeeks.com/installing-mongodb-on-centos-fedora/?expand\_article=1](https://computingforgeeks.com/installing-mongodb-on-centos-fedora/?expand_article=1)
{% endhint %}

***

## S3cmd

#### Description

**S3cmd** est un outil de ligne de commande gratuit et un client pour télécharger, récupérer et gérer des données dans Amazon S3 et d'autres fournisseurs de services de stockage cloud qui utilisent le **protocole S3**, tels que Clever Cloud ou Google Cloud Storage. L'outil est un projet open source écrit en Python disponible sous licence publique GNU v2 (GPLv2).

### Installation

```bash
sudo dnf install s3cmd 
```

### **Configuration**

```bash
s3cmd --configure 
```

### **Commandes**

```bash
s3cmd ls                                 # List All S3 Bucket
s3cmd mb s3://sirchamallow               # Creating New Bucket
s3cmd put file.txt s3://sirchamallow     # Uploading file in Bucket
s3cmd put -r backup s3://sirchamallow    # Uploading Directory in Bucket   # 
s3cmd ls s3://sirchamallow               # List Data of S3 Bucket
s3cmd get s3://sirchamallow              # Download Files from Bucket
s3cmd del s3://tecadmin/file.txt         # Delete file from s3 bucket
s3cmd del s3://tecadmin/backup           # Delete directory from s3 bucket
s3cmd rb s3://sirchamallowc              # Rmove S3 Bucket
```

{% hint style="info" %}
Source : [https://tecadmin.net/install-s3cmd-manage-amazon-s3-buckets/](https://tecadmin.net/install-s3cmd-manage-amazon-s3-buckets/)
{% endhint %}
