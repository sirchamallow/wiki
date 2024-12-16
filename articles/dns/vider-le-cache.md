---
icon: trash-can
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Vider le cache

## **Windows** <a href="#h-vider-le-cache-dns-sous-microsoft-windows-xp-7-vista-8-8-1-ou-10" id="h-vider-le-cache-dns-sous-microsoft-windows-xp-7-vista-8-8-1-ou-10"></a>

Sous Windows, le processus de purge du cache DNS est le même pour la plupart des versions.&#x20;

{% hint style="info" %}
Vous devez utiliser l’option **Exécuter en tant qu’administrateur** lors de l’exécution de l’invite de commande pour accéder à toutes les autorisations de sécurité du système
{% endhint %}

1. Utilisez le raccourci **Windows + R** pour ouvrir la fenêtre **Exécuter.**
2. Tapez **cmd** pour ouvrir l’i**nvite de commande** de Windows.
3. Tapez la commande suivante et appuyez sur **Entrée :**

```powershell
ipconfig /flushdns
```

4\. Windows effacera automatiquement vos fichiers de cache DNS et réinitialisera le cache du résolveur DNS.&#x20;

## MacOS

Sur macOS, la méthode/commande pour vider le cache DNS varie en fonction de la version de votre système d’exploitation. Identifier en premier lieu votre version de macOS en cliquant sur l’icône **Apple -> À propos de ce Mac**.

{% hint style="info" %}
Renseignez votre mot de passe administrateur si besoin et cliquez à nouveau sur la touche **Entrée** pour vider votre cache DNS.
{% endhint %}

Voici les commandes pour chaque version :

**macOS 11 Big Sur ou 12 Monterey**

```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

**macOS 10.11 El Capitan, 10.12 Sierra, 10.13 High Sierra, 10.14 Mojave, ou 10.15 Catalina**

```bash
sudo killall -HUP mDNSResponder
```

**macOS 10.10 Yosemite**&#x20;

```bash
sudo discoveryutil udnsflushcaches
```

**macOS 10.7 Lion, 10.8 Mountain Lion, ou 10.9 Mavericks**

```bash
sudo killall -HUP mDNSResponder
```

**macOS 10.6 Snow Leopard**

```bash
sudo dscacheutil -flushcache
```

**macOS 10.5 Leopard**

```bash
sudo lookupd -flushcache
```

## Linux

Dans votre terminal, saisissez la commande en fonction du service que votre système Linux exécute.\
Voici la méthode pour `Name Service Cache Daemon` (nscd) et `systemd`.

### **nscd**

```
sudo /etc/init.d/nscd restart
```

### **systemd**

```
systemd-resolve --flush-caches
```

{% hint style="success" %}
Ensuite, entrez la commande suivante : **`systemd-resolve --statistics`** pour vérifier si la commande précédente a réussi à vider le cache DNS.
{% endhint %}
