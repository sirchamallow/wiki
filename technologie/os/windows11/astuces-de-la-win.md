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

## Télémétrie pilotes carte graphique Nvidia

Penser à désactiver la télémétrie activée par défaut de la suite _GeForce Experience_, un logiciel de **Nvidia** accompagnant bien souvent les drivers de la carte graphique. Ils remontent automatiquement des informations sur votre système au fabricant.\
\
Avec le refrain classique "nous nous servons de cette télémétrie pour améliorer ses pilotes et l'expérience de ses utilisateurs". Mais comme tout est chiffré, il n'y aucun moyen de savoir ce qui est envoyé réellement. Il n'est possible de désactiver cette option depuis l'interface des pilotes.\
\
Il vous sera nécessaire soit de vous plonger dans les tâches planifiées, le registre et les services de Windows en suivant par exemple [ce guide de PC-Astuces](https://www.pcastuces.com/pratique/astuces/4871.htm), ou un installant [ce package depuis Chocolatey](https://chocolatey.org/packages/disable-nvidia-telemetry).

## **Désactiver les services inutiles**

Pour des solutions officielles concernant l'optimisation de Windows, afin de Désactiver les services inutile&#x73;**,** il y a... le site de Microsoft (:

{% embed url="https://learn.microsoft.com/fr-fr/windows/iot/iot-enterprise/optimize-your-device/services" %}

### Lancer des applications automatiquement au démarrage

1. Sélectionnez le bouton **Démarrer** et faites défiler jusqu’à trouver l’application que vous souhaitez exécuter au démarrage.
2. Cliquez sur l’application, sélectionnez **Plus**, puis sélectionnez **Ouvrir l’emplacement du fichier**. L’emplacement où est enregistré le raccourci vers l’application s’ouvre. S’il n’y a pas d’option pour **Ouvrir l’emplacement du fichier**, cela signifie que l’application ne peut pas s’exécuter au démarrage.
3. Avec l’emplacement du fichier ouvert, appuyez sur la **touche de logo Windows** + **R** (fenêtre exécutez), tapez **shell:startup**, puis sélectionnez **OK**. Le dossier **Démarrage** s’ouvre.
4. Copiez et collez le raccourci de l’application à partir de l’emplacement du fichier dans le dossier **Démarrage**.

{% hint style="info" %}
Source : [https://support.microsoft.com/fr-fr/windows/configurer-des-applications-de-d%C3%A9marrage-dans-windows-115a420a-0bff-4a6f-90e0-1934c844e473](https://support.microsoft.com/fr-fr/windows/configurer-des-applications-de-d%C3%A9marrage-dans-windows-115a420a-0bff-4a6f-90e0-1934c844e473)
{% endhint %}
