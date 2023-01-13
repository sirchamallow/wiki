# 🥞 Base de données

### Redis

<figure><img src="../../../.gitbook/assets/langfr-2560px-Redis_Logo.png" alt=""><figcaption></figcaption></figure>

```bash
sudo dnf install redis     		# Install redis cli and server
sudo systemctl start redis	 	# Initialize redis server
sudo systemctl enable redis 	        # To start redis on boot, run
```

Source : [https://developer.fedoraproject.org/tech/database/redis/about.html](https://developer.fedoraproject.org/tech/database/redis/about.html)

### PostgreSQL

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

Source : [https://www.pgcli.com/install](https://www.pgcli.com/install)

### SQLite

Mettez à jour votre Fedora pour vous assurer que tous les paquets existants sont à jour

```bash
sudo dnf upgrade --refresh -y
```

Ensuite procéder à l'installation

```bash
sudo dnf install sqlite
```

Vérifier la version de SQL Lite 3

```bash
sqlite3 --version
```

{% hint style="success" %}
Si le message affiche `v3.36.0` ou autre version, vous pouvez continuer
{% endhint %}

Source : [https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/](https://www.linuxcapable.com/how-to-install-sqlite-3-on-fedora-35/)
