---
description: Voici les méthodes pour effectuer le changement de DNS sur votre machine
icon: arrows-rotate-reverse
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Changer ses DNS

## Pourquoi faire ?

Pour accéder à des ressources dont un ou plusieurs fournisseur d'accès à internet bloque l'accès.

Comme par exemple : [Sci-Hub](https://fr.wikipedia.org/wiki/Sci-Hub), [LibGen](https://fr.wikipedia.org/wiki/Library_Genesis)...

***

## Comment faire ?

### **Windows**&#x20;

1. Ouvrez le **Centre Réseau et partage**.
2. Cliquez sur **Modifier les paramètres de la carte**.
3. Faites un **clic droit** sur votre connexion réseau (Ethernet ou Wi-Fi), puis sélectionnez **Propriétés**.
4. Double-cliquez sur **Protocole Internet version 4 (TCP/IPv4)** (ou **Version 6 (TCP/IPv6)** si nécessaire).
5. Cochez **Utiliser l'adresse de serveur DNS suivante**.
6. Renseignez les champs :
   * **Serveur DNS préféré**
   * **Serveur DNS auxiliaire**
7. Validez en cliquant sur **OK**, puis à nouveau sur **OK** pour enregistrer les modifications.

{% hint style="info" %}
Vous pouvez ensuite ouvrir un invite de commandes et exécuter `ipconfig /flushdns` pour vider le cache DNS et appliquer immédiatement les nouveaux paramètres.
{% endhint %}

***

### **Linux** (Fedora Gnome)&#x20;

1. Ouvrez les **Paramètres**.
2. Accédez à **Réseau**.
3. Cliquez sur l'icône **⚙️** située à côté de votre connexion active (Ethernet ou Wi-Fi).
4. Ouvrez l'onglet **IPv4** (ou **IPv6** selon votre besoin).
5. Désactivez l'option **Automatique** dans la section **DNS**.
6. Saisissez les adresses de vos serveurs DNS, séparées par une virgule.
7. Cliquez sur **Appliquer**.
8. Désactivez puis réactivez la connexion réseau, ou redémarrez-la pour prendre en compte les modifications.

{% hint style="info" %}
Pour vérifier que les nouveaux DNS sont bien utilisés, ouvrez un terminal et exécutez :
{% endhint %}

```bash
Shellresolvectl status          # Alternative 1
Shellnmcli dev show | grep DNS  # Alternative 2
```

***

### **Mac**&#x20;

1. Ouvrez les **Réglages Système** (ou **Préférences Système** sur les anciennes versions de macOS).
2. Cliquez sur **Réseau**.
3. Sélectionnez votre connexion active (**Wi‑Fi** ou **Ethernet**).
4. Cliquez sur **Détails...** (ou **Avancé...** selon la version de macOS).
5. Ouvrez l'onglet **DNS**.
6. Dans la section **Serveurs DNS**, cliquez sur le bouton **+** pour ajouter un ou plusieurs serveurs DNS.
7. Saisissez les adresses DNS souhaitées.
8. Cliquez sur **OK**, puis sur **Appliquer** pour enregistrer les modifications.

{% hint style="info" %}
Pour vérifier que les nouveaux DNS sont bien utilisés, ouvrez un **terminal** et exécutez :
{% endhint %}

```bash
Shellscutil --dns # Vérifier que les nouveaux DNS sont bien actif
```

***

### **Android**

{% hint style="success" %}
Vous pouvez aussi utiliser des application comme [**DNS66**](https://f-droid.org/packages/org.jak_linux.dns66/) (F-Droid), [**DNS Changer**](https://play.google.com/store/apps/details?id=com.frostnerd.dnschanger\&hl=fr) (Google Play), [**Blokada**](https://github.com/blokadaorg) (GitHub)
{% endhint %}

Sinon de manière classique :&#x20;

* Ouvrez les **Paramètres**.
* Accédez à **Réseau et Internet** (ou **Connexions** selon le constructeur).
* Appuyez sur **Wi‑Fi**.
* Touchez le nom du réseau Wi‑Fi connecté ou l'icône **⚙️** associée.
* Sélectionnez **Modifier le réseau** ou **Gérer les paramètres du réseau**.
* Ouvrez les **Options avancées**.
* Dans **Paramètres IP**, remplacez **DHCP** par **Statique**.
* Conservez les informations IP existantes et renseignez les champs :
  * **DNS 1**
  * **DNS 2**
* Enregistrez les modifications.

#### Alternative : DNS privé (Android 9 et versions ultérieures)

1. Ouvrez les **Paramètres**.
2. Accédez à **Réseau et Internet**.
3. Sélectionnez **DNS privé**.
4. Choisissez **Nom d'hôte du fournisseur DNS privé**.
5. Saisissez le nom d'hôte souhaité.

**Exemples :**

* Cloudflare : `one.one.one.one`
* Google : `dns.google`
* Quad9 : `dns.quad9.net`

{% hint style="info" %}
La méthode **DNS privé** est généralement préférable car elle utilise le chiffrement DNS (DoT) et s'applique à l'ensemble des connexions réseau du téléphone, pas uniquement au Wi‑Fi configuré.
{% endhint %}

***

### **Chromebook**&#x20;

Paramètres > Réseau puis sélectionnez votre connexion Wi-Fi. Désactivez la configuration automatique de l’adresse IP en cliquant sur Réseau, puis désactivez l’option Configurer l’adresse IP automatiquement en cliquant sur l’interrupteur. Modifiez les Serveurs de nom. Au lieu d’utiliser l’option par défaut, cliquer sur Serveurs de nom personnalisés et saisir une adresse de serveur primaire et secondaire.
