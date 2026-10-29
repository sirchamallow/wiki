---
icon: database
---

# Base de données

## Redis

{% embed url="https://redis.com/fr/" %}

```bash
sudo dnf install redis     		# Install redis cli and server
sudo systemctl start redis	 	# Initialize redis server
sudo systemctl enable redis 	# To start redis on boot, run
```

### Interface graphique

{% embed url="https://redis.com/fr/redis-enterprise/redisinsight/" %}

{% embed url="https://github.com/joeferner/redis-commander" %}

{% embed url="https://github.com/patrikx3/redis-ui" %}

***

## PostgreSQL

{% embed url="https://www.postgresql.org/download/linux/redhat/" %}

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

### Raccourcis utiles

```bash
# Cheatsheet
\q    # Quitter la base de donnée
\duf+ # Liste des utilisateurs & leurs droits
\?    # Voir toutes les commandes posgres
\l    # Liste de toutes les base de données
\dt   # Voir toutes les tables de la db
\h    # Voir toutes les commandes SQL
SELECT version(); # Identifier la version de postgres installer
```

### PG-CLI

{% embed url="https://www.pgcli.com/" %}

Pgcli est une interface en ligne de commande pour Postgres dotée d'une fonction d'auto-complétion et de mise en évidence de la syntaxe (highlighting)

```bash
sudo yum install python-pip # Pré-requis : installer Python et PIP
sudo pip install pgcli      # Installer PGCLI
```

***

## MySQL

{% embed url="https://www.mysql.com/fr/" %}

```bash
sudo dnf install community-mysql-server # Installer MySQL sur Fedora (Linux)
mysql --version                         # Vérifier la version de MySQL

# Commandes
sudo systemctl start mysqld    # Démarrre le service
sudo systemctl enable mysqld   # Active le service
sudo systemctl restart mysqld  # Redémarrer le service
sudo mysql_secure_installation # Configurer MySQL avant la première utilisation
sudo mysql -u root -p          # Utiliser MySQL
```

***

## SQLite

{% embed url="https://www.sqlite.org/" %}

```bash
sudo dnf install sqlite # Installer SQlite sur Fedora (Linux)
sqlite3 --version       # Vérifier la version de SQLite 
```

***

## MongoDB

{% embed url="https://www.mongodb.com/fr-fr" %}

```bash
sudo dnf -y install mongodb-org # Installer MongoDB sur Fedora (Linux)
mongo --version # Vérifier la version de MongoDB
sudo systemctl start mongod.service  # Démarrre le service
sudo systemctl enable mongod.service # Active le service
sudo systemctl status mongod.service  # Vérifier l'état du service
```

***

## S3cmd

{% embed url="https://s3tools.org/s3cmd" %}

**S3cmd** est un outil de ligne de commande gratuit et un client pour télécharger, récupérer et gérer des données dans Amazon S3 et d'autres fournisseurs de services de stockage cloud qui utilisent le **protocole S3**, tels que Clever Cloud ou Google Cloud Storage. L'outil est un projet open source écrit en Python disponible sous licence publique GNU v2 (GPLv2).

```bash
sudo dnf install s3cmd               # Installation s3cmd
s3cmd --configure                    # Configuration
s3cmd ls                             # List All S3 Bucket
s3cmd mb s3://username               # Creating New Bucket
s3cmd put file.txt s3://username     # Uploading file in Bucket
s3cmd put -r backup s3://username    # Uploading Directory in Bucket 
s3cmd ls s3://username               # List Data of S3 Bucket
s3cmd get s3://username              # Download Files from Bucket
s3cmd del s3://tecadmin/file.txt     # Delete file from s3 bucket
s3cmd del s3://tecadmin/backup       # Delete directory from s3 bucket
s3cmd rb s3://username               # Rmove S3 Bucket
```

***

## Portabase

{% embed url="https://portabase.io" %}

Portabase, un **outil de sauvegarde et de restauration de base de données** pour PostgreSQL, MySQL, MsSQL, MariaDB, Firebird SQL, SQLite, MongoDB, Redis et Docker. La plateforme permet d'automatiser la sauvegarde et la restauration de bases de données depuis une interface centralisée.

***

## StackRender

{% embed url="https://stackrender.io/" %}

Un outil gratuit et open-source pour rendre l'évolution des schémas visuelle et simplifier les migrations SQL. Il prend actuellement en charge PostgreSQL, MySQL, MariaDB, SQLite, Oracle et Microsoft SQL Server.

***

## VisualLeaf

{% embed url="https://visualeaf.com/" %}

Un client open-source de gestion et d'exploration de données multiplateforme (disponible sur Windows, macOS et Linux). Conçu comme un espace de travail visuel unifié (_Visual Workspace_), cet outil permet de manipuler, de requêter et de visualiser simultanément des bases de données relationnelles (**SQL**) et non relationnelles (**NoSQL/Document**), éliminant ainsi le besoin de multiplier les logiciels spécialisés.
