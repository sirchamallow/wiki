---
icon: circle-nodes
layout:
  width: default
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
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Identifier ses DNS

### U**n résolveur DNS c’est quoi ?**&#x20;

> Le Domain Name System (ou DNS, système de noms de domaine) est un service permettant de traduire un nom de domaine en informations de plusieurs types qui y sont associées, notamment en adresses IP de la machine portant ce nom – Wikipedia​.

Comment fonctionne un DNS : [https://howdns.works](https://howdns.works)

### **Services**

* Vérifier les DNS d’un site avec **IntoDNS** : [https://intodns.com](https://intodns.com/)​
* **DNSPerf**, pour comparer les performances des DNS : [https://www.dnsperf.com](https://www.dnsperf.com/)
* Analyser ses logs DNS : [https://github.com/dmachard/DNS-collector](https://github.com/dmachard/DNS-collector)

***

### Identifier ses DNS

Pour savoir quel serveur DNS vous utilisez, nous pouvons le faire en ligne de commande, vous pouvez suivre ces étapes :

#### Windows

1. **Ouvrez l'Invite de commandes** :
   * Appuyez sur `Win + R`, tapez `cmd`, puis appuyez sur `Entrée`.
2.  **Tapez la commande suivante** :

    ```
    ipconfig /all
    ```

    * Appuyez sur `Entrée`.
3. **Recherchez la section "Serveurs DNS"** dans les résultats affichés. Vous y trouverez les adresses des serveurs DNS utilisés par vos adaptateurs réseau.

***

#### MacOS

1. **Ouvrez le Terminal** :
   * Vous pouvez le trouver dans `Applications > Utilitaires > Terminal`.
2.  **Tapez la commande suivante** :

    ```
    scutil --dns | grep 'nameserver\[[0-9]*\]'
    ```

    * Appuyez sur `Entrée`.
3. **Les adresses des serveurs DNS** seront listées dans les résultats.

***

#### Linux

1. **Ouvrez le Terminal**.
2.  **Tapez la commande suivante** :

    ```
    nmcli dev show | grep 'IP4.DNS'
    ```

    * Appuyez sur `Entrée`.
3. **Les adresses des serveurs DNS** seront affichées dans les résultats.

