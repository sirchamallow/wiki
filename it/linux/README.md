---
description: Linux
---

# 🐧 Fedora Workstation

## Présentation

Fedora Linux est un système d’exploitation libre et une distribution Linux communautaire développée par le projet Fedora et sponsorisée par l’entreprise Red Hat, qui lui fournit des développeurs ainsi que des moyens financiers et logistiques. ([Wikipedia](https://fr.wikipedia.org/wiki/Fedora\_Linux))

### Navigation

{% content-ref url="astuces.md" %}
[astuces.md](astuces.md)
{% endcontent-ref %}

{% content-ref url="dev-tools/" %}
[dev-tools](dev-tools/)
{% endcontent-ref %}

{% content-ref url="software/" %}
[software](software/)
{% endcontent-ref %}

{% content-ref url="gnome-extensions.md" %}
[gnome-extensions.md](gnome-extensions.md)
{% endcontent-ref %}

{% content-ref url="hardware/" %}
[hardware](hardware/)
{% endcontent-ref %}

## Commandes des bases

Voici une liste de commandes de bases pour **Linux** (celles-ci ne sont pas spécifique à Fedora)

### Renommer un fichier ou un répertoire

Voic un exemple pour renommer un fichier/répertoire du nom de "paris" en "lyon":

```bash
mv paris lyon
```

### Déplacer un fichier ou répertoire

Voici comment déplacer un fichier/répertoire du dossier courant vers le répertoire distant "/home/georges/Bureau" :

```bash
mv lyon /home/georges/Bureau
```

### Déplacer tout les fichiers/répertoires

On va déplacer tout les fichiers/répertoires du dossier courant vers le répertoire distant "/home/georges/Bureau/marseille":

```bash
mv * /home/georges/Bureau/marseille
```

### Supprime un répertoire non vide et son contenu

```bash
rm -r
```

## Mise à jour

Voici la procédure pour mettre à jour votre version de Fedora

N'oublier de faires vos backups avant ce genre d'opération.

```bash
sudo dnf upgrade --refresh
# Lancer la mise à jour, puis redémarrez votre ordinateur.
```

{% hint style="danger" %}
**Important :** Ne sautez pas cette étape. Les mises à jour du système sont nécessaires pour recevoir les clés de signature des versions supérieures, et elles corrigent souvent des problèmes liés au processus de mise à niveau.
{% endhint %}

```bash
sudo dnf install dnf-plugin-system-upgrade
# Installe le paquet dnf-plugin-system-upgrade (si celui-ci n'est pas déjà installé)

sudo dnf system-upgrade download --releasever=39
# Téléchargez les paquets mis à jour
# Votre machine va redémarrer automatiquement à la fin du processus

sudo dnf system-upgrade reboot
# Une fois le processus de mise à niveau terminé, 
# votre système redémarrera une seconde fois dans la version mise à jour de Fedora
```

{% hint style="info" %}
Source : [https://docs.fedoraproject.org/fr/quick-docs/upgrading-fedora-offline/](https://docs.fedoraproject.org/fr/quick-docs/upgrading-fedora-offline/)
{% endhint %}

## Options utiles

### **Clean**

<pre class="language-bash"><code class="lang-bash"><strong>sudo dnf clean dbcache    # Effacer le cache de DNF
</strong><strong>sudo dnf clean packages   # Effacer les paquets mis en cache lors du téléchargement
</strong>sudo dnf clean plugins    # Efface le cache de tous les plugins activés
sudo dnf clean metadata   # Supprime les métadonnées du dépôt. 
<strong>sudo dnf clean all        # Effacer TOUT les caches, les métadatas &#x26; les fichiers inutiles de DNF
</strong></code></pre>

### **Reinstall**

Si vous avez besoin de réinstaller un programme vous pouvez utiliser l'option _reinstall_

```bash
sudo dnf reinstall <nom-du-paquet>
```

### **List**

```bash
sudo dnf list obsoletes # Liste des paquets obsolètes (utile avant une 
mise à niveau de Fedora)
sudo dnf list recent    # Liste des derniers paquets ajoutés à vos dépôts
sudo dnf list extras    # Liste des paquets installés ne provenant pas des dépôts actifs ou installation manuelle
```

{% hint style="info" %}
Source : [https://doc.fedora-fr.org/wiki/DNF,\_le\_gestionnaire\_de\_paquets\_de\_Fedora#Conclusion](https://doc.fedora-fr.org/wiki/DNF,\_le\_gestionnaire\_de\_paquets\_de\_Fedora#Conclusion)
{% endhint %}
