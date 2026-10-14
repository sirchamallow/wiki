---
description: PTP – Precision Time Protocol
icon: clock-ten
---

# PTP

### Présentation

Le **PTP** (_Precision Time Protocol_) est un protocole de synchronisation d'horloge défini par la norme **IEEE 1588**. Il permet de synchroniser les équipements d'un réseau avec une précision **inférieure à la microseconde**, voire de l'ordre de la nanoseconde avec du matériel compatible.

Il est conçu pour les environnements où le **NTP** (précision de l'ordre de la milliseconde) ne suffit pas.

### Versions

| Version | Norme          | Remarque                                          |
| ------- | -------------- | ------------------------------------------------- |
| PTPv1   | IEEE 1588-2002 | Obsolète                                          |
| PTPv2   | IEEE 1588-2008 | Version la plus déployée, non compatible v1       |
| PTPv2.1 | IEEE 1588-2019 | Rétrocompatible v2, ajouts sécurité et redondance |

### Principe de fonctionnement

* Une **horloge maître** (Grandmaster) sert de référence, souvent synchronisée sur un GPS/GNSS.
* Les **esclaves** (clients) se calent sur le maître.
* L'algorithme **BMCA** (_Best Master Clock Algorithm_) élit automatiquement la meilleure horloge du réseau.
* Les échanges de messages horodatés permettent de calculer **le décalage** et **le délai de transit** :

```
 Maître                      Esclave
   |------- Sync (t1) -------->|  (t2)
   |------- Follow_Up (t1) --->|
   |<----- Delay_Req (t3) -----|
   |------ Delay_Resp (t4) --->|

 Délai    = ((t2 - t1) + (t4 - t3)) / 2
 Décalage = (t2 - t1) - Délai
```

### Types d'horloges

| Type              | Rôle                                                      |
| ----------------- | --------------------------------------------------------- |
| Grandmaster Clock | Source de temps de référence                              |
| Ordinary Clock    | Équipement final (maître ou esclave)                      |
| Boundary Clock    | Switch qui se synchronise en amont et redistribue en aval |
| Transparent Clock | Switch qui corrige le temps de traversée dans les paquets |

### Horodatage matériel vs logiciel

* **Matériel** : horodatage réalisé par la carte réseau (PHY/MAC) → précision nanoseconde.
* **Logiciel** : horodatage par le système d'exploitation → précision de quelques microsecondes.

Vérifier le support d'une carte sous Linux :

```bash
ethtool -T eth0
```

### Ports réseau

<table><thead><tr><th width="77">Port</th><th width="100">Protocole</th><th>Usage</th></tr></thead><tbody><tr><td>319</td><td>UDP</td><td>Messages d'événement (Sync, Delay_Req)</td></tr><tr><td>320</td><td>UDP</td><td>Messages généraux (Follow_Up, Announce)</td></tr></tbody></table>

\{% hint style="info" %\} PTP peut aussi fonctionner directement sur Ethernet (EtherType `0x88F7`). \{% endhint %\}

### PTP vs NTP

<table><thead><tr><th width="143">Critère</th><th width="191">NTP</th><th>PTP</th></tr></thead><tbody><tr><td>Précision</td><td>Milliseconde</td><td><strong>Sub-microseconde</strong></td></tr><tr><td>Matériel dédié</td><td>Non</td><td><strong>Recommandé</strong></td></tr><tr><td>Portée</td><td>Internet / WAN</td><td><strong>LAN principalement</strong></td></tr><tr><td>Complexité</td><td>Faible</td><td><strong>Plus élevée</strong></td></tr><tr><td>Usage typique</td><td>Serveurs, postes, AD</td><td><strong>Industrie, télécoms, finance, broadcast</strong></td></tr></tbody></table>

### Mise en œuvre sous Linux

Paquet : `linuxptp`

```bash
# Installation
sudo apt install linuxptp      # Debian/Ubuntu
sudo dnf install linuxptp      # Fedora/RHEL

# Lancer ptp4l en esclave sur eth0 (horodatage matériel)
sudo ptp4l -i eth0 -m -s

# Synchroniser l'horloge système sur l'horloge de la carte
sudo phc2sys -s eth0 -w -m
```

### Sous Windows

Windows 10 (1809+) / Windows Server 2019+ intègrent un client PTP via le service **W32Time** (désactivé par défaut, configuration par registre).

### À retenir

{% hint style="info" %}
* PTP = synchronisation **ultra-précise** sur réseau local.
* Nécessite des **switchs et cartes compatibles** pour atteindre sa précision maximale.
* Pour un usage bureautique classique, **NTP reste suffisant**.
{% endhint %}
