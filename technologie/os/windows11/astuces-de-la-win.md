---
icon: lightbulb-exclamation-on
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
    visible: true
---

# Astuces de la Win

## Commandes de bases

Voici 15 commandes **CMD** de base essentielles à connaître pour l'utilisation du terminal (l'invite de commandes) sous Windows. Elles sont particulièrement utiles pour la gestion des fichiers, l'obtention d'informations système et le dépannage réseau.\
\
Je vous recommande [l'usage de PowerShell](https://learn.microsoft.com/fr-fr/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4) qui rendra l'expérience plus agréable.

1. **`DIR`** : Affiche la liste des fichiers et dossiers du répertoire courant
2. **`CD`** (ou `CHDIR`) : Permet de changer de répertoire ou d'afficher le répertoire courant
3. **`MKDIR`** (ou `MD`) : Crée un nouveau répertoire
4. **`RMDIR`** (ou `RD`) : Supprime un répertoire
5. **`COPY`** : Copie un ou plusieurs fichiers vers un autre emplacement
6. **`DEL`** : Supprime un ou plusieurs fichiers
7. **`REN`** (ou `RENAME`) : Renomme un fichier ou un répertoire
8. **`TYPE`** : Affiche le contenu d'un fichier texte
9. **`CLS`** : Efface l'écran de la console
10. **`IPCONFIG`** : Affiche les paramètres de configuration réseau
11. **`PING`** : Teste la connectivité réseau vers une adresse IP ou un nom de domaine
12. **`SYSTEMINFO`** : Affiche des informations détaillées sur la configuration du système
13. **`TASKLIST`** : Affiche la liste des processus en cours d'exécution
14. **`TASKKILL`** : Permet de terminer un processus en cours d'exécution
15. **`SHUTDOWN`** : Permet d'éteindre, redémarrer ou mettre en veille l'ordinateur

***

## Télémétrie pilotes carte graphique Nvidia

Penser à désactiver la télémétrie activée par défaut de la suite _GeForce Experience_, un logiciel de **Nvidia** accompagnant bien souvent les drivers de la carte graphique. Ils remontent automatiquement des informations sur votre système au fabricant.\
\
Avec le refrain classique "nous nous servons de cette télémétrie pour améliorer ses pilotes et l'expérience de ses utilisateurs". Mais comme tout est chiffré, il n'y aucun moyen de savoir ce qui est envoyé réellement. Il n'est possible de désactiver cette option depuis l'interface des pilotes.\
\
Il vous sera nécessaire soit de vous plonger dans les tâches planifiées, le registre et les services de Windows en suivant par exemple [ce guide de PC-Astuces](https://www.pcastuces.com/pratique/astuces/4871.htm), ou un installant [ce package depuis Chocolatey](https://chocolatey.org/packages/disable-nvidia-telemetry).

***

## **Désactiver les services inutiles**

Pour des solutions officielles concernant l'optimisation de Windows, afin de Désactiver les services inutile&#x73;**,** il y a... le site de Microsoft (:

{% embed url="https://learn.microsoft.com/fr-fr/windows/iot/iot-enterprise/optimize-your-device/services" %}

***

## Lancer des applications automatiquement au démarrage

1. Sélectionnez le bouton **Démarrer** et faites défiler jusqu’à trouver l’application que vous souhaitez exécuter au démarrage.
2. Cliquez sur l’application, sélectionnez **Plus**, puis sélectionnez **Ouvrir l’emplacement du fichier**. L’emplacement où est enregistré le raccourci vers l’application s’ouvre. S’il n’y a pas d’option pour **Ouvrir l’emplacement du fichier**, cela signifie que l’application ne peut pas s’exécuter au démarrage.
3. Avec l’emplacement du fichier ouvert, appuyez sur la **touche de logo Windows** + **R** (fenêtre exécutez), tapez **shell:startup**, puis sélectionnez **OK**. Le dossier **Démarrage** s’ouvre.
4. Copiez et collez le raccourci de l’application à partir de l’emplacement du fichier dans le dossier **Démarrage**.

{% hint style="info" %}
Source : [https://support.microsoft.com/fr-fr/windows/configurer-des-applications-de-d%C3%A9marrage-dans-windows-115a420a-0bff-4a6f-90e0-1934c844e473](https://support.microsoft.com/fr-fr/windows/configurer-des-applications-de-d%C3%A9marrage-dans-windows-115a420a-0bff-4a6f-90e0-1934c844e473)
{% endhint %}

***

## Faire quelques vérifications

### chkdsk

Vérifie le système de fichiers et les métadonnées du système de fichiers d’un volume à la recherche d’erreurs logiques et physiques.&#x20;

{% embed url="https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/chkdsk" %}

### sfc

La commande sfc /scannow analyse tous les fichiers système protégés et remplace les fichiers endommagés par une copie mise en cache. Les résultats de l'analyse seront affichés une fois ce processus terminé.

{% embed url="https://learn.microsoft.com/fr-fr/windows-server/administration/windows-commands/sfc" %}

{% embed url="https://support.microsoft.com/fr-fr/topic/utilisez-l-outil-v%C3%A9rificateur-des-fichiers-syst%C3%A8me-pour-r%C3%A9parer-les-fichiers-syst%C3%A8me-manquants-ou-endommag%C3%A9s-79aa86cb-ca52-166a-92a3-966e85d4094e" %}

***

## Réparer les fichiers de données Outlook (.pst et .ost) <a href="#page-header" id="page-header"></a>

{% embed url="https://support.microsoft.com/fr-fr/office/r%C3%A9parer-les-fichiers-de-donn%C3%A9es-outlook-pst-et-ost-25663bc3-11ec-4412-86c4-60458afc5253" %}

***

## Vérifier l'état de la batterie sur Windows

Ouvrez l'invite de commandes ou PowerShell en appuyant sur les touches `Win + X` et sélectionnez Invite de commandes en mode administrateur.&#x20;

Tapez la commande suivante et appuyez sur `Entrée` pour générez un rapport de batterie

```powershell
powercfg /batteryreport /output "C:\battery-report.html"
```

Et pour consulter le rapport, aller dans le dossier `C:\battery-report.html` et ouvrez ce fichier dans votre navigateur pour voir un rapport détaillé sur l'état de votre batterie (capacité de la batterie, l'historique d'utilisation...)

***

## Changer son adresse MAC Bluetooth <a href="#article-title" id="article-title"></a>

Windows ne permet pas tout le temps de le faire directement via les paramètres.

Avant de vous lancer dans ce genre de manipulations :&#x20;

{% hint style="danger" %}
L'adresse `00:00:00:00:00:00` (tous zéros) est interdite car elle peut rendre votre adaptateur inutilisable.
{% endhint %}

{% hint style="success" %}
Conservez l’adresse MAC d’origine si vous devez revenir en arrière. Pour restaurer la configuration initiale, il vous suffira de répéter l’opération en saisissant l’adresse d’origine.
{% endhint %}

Voici deux façon de faire la manipulation :

### **Gestionnaire de périphériques**

1. Appuyez sur `Win + X` et sélectionnez **Gestionnaire de périphériques**.
2. Trouvez votre adaptateur Bluetooth sous la section **Bluetooth**.
3. Faites un clic droit sur l'adaptateur Bluetooth et sélectionnez **Propriétés**.
4. Allez dans l'onglet **Avancé** ou **Avancé** (selon la version de Windows).
5. Recherchez une option appelée **Adresse réseau** ou **Network Address**.
6. Si cette option est disponible, vous pouvez entrer une nouvelle adresse MAC. Si elle n'est pas disponible, cette méthode ne fonctionnera pas pour votre adaptateur.

### Bluetooth MAC Address Changer

{% embed url="https://macaddresschanger.com" %}







