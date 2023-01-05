---
description: Firefox Send, une alternative à WeTransfer avec chiffrement de bout en bout
---

# 📤 Firefox Send

{% hint style="danger" %}
Update : le service est désormais arrter
{% endhint %}

La Fondation [Mozilla](https://www.frandroid.com/tag/mozilla-firefox) (à qui l’ont doit déjà la navigateur open-source Firefox) [a lancé son propre service de partage de fichiers](https://blog.mozilla.org/blog/2019/03/12/introducing-firefox-send-providing-free-file-transfers-while-keeping-your-personal-information-private/), qui était jusqu’à alors accessible uniquement sous la forme d’un mode expérimental du navigateur via le programme Test Pilot.

**Firefox Send** (c’est le nom du service) permet de transférer des fichiers avec un élément essentiel, le **chiffrement de bout en bout**. Pour ce qui est de l’envoi des fichiers, vous pouvez envoyer un fichier jusqu’à 2,5 Go avec votre compte Firefox (celui que vous utilisez pour synchroniser vos favoris, mots de passes, historique etc.), sinon le service ce limitera à 1Go.&#x20;

Pour information, contrairement aux services de stockage comme _Box_, _Dropbox_ ou _OneDrive_, Firefox Send ne s’intègre pas au système d’exploitation du périphérique, car vous devez taper l’url du site internet pour ensuite envoyer vos fichiers. Toutefois, une application mobile (en version bêta) sera également disponible sur Android prochainement.

### **Comment ça marche :**

{% embed url="https://youtu.be/eRHpEn2eHJA" %}

### **Open-Source 👍**

Le service est bien évidemment **open-source** 🙂 . Les sources sont disponible sur GitHub à cette adresse => [https://github.com/mozilla/send](https://github.com/mozilla/send). Pour ce qui est de la licence, il s’agit de la [Mozilla Public License version 2.0](https://github.com/mozilla/send/blob/master/LICENSE). On commence du coup à voir des projets annexes comme [ffsend](https://github.com/timvisee/ffsend), qui permets d’utiliser le service en ligne de commande ^\_\_^.

### **Des alternatives 🔁 ?**

Parmi les autres services similaires (le plus populaire étant [**WeTransfer**](https://www.wetransfer.com/)), vous trouverez également [**Framadrop**](https://framadrop.org/) (également [opensource](https://framagit.org/framasoft/framadrop/)), [**SwissTransfer**](https://www.swisstransfer.com/fr) (from Switerzland) ou encore [**SMASH**](https://www.fromsmash.com/) (from Lyon!). Ce dernier, à la différence des autres ne dispose pas de limite de taille pour l’envoi de vos fichiers.

### **Hébergement des données (☠️ ou 🧸?)**

Mozilla utilise **Google Cloud Platform** pour le stockage des fichiers. Ça en fera hurler plus d’un, mais c’est pas forcément mieux chez autres…. En effet _WeTranser_ ou _SMASH_ passe par **AWS** (Amazon Web Services). Seul _SwissTransfer_ (service gérer par Infomaniak) et _Framadrop_ (propulsé par l’association Framasoft), hébergent les données en Europe (la Suisse pour le premier, l’Allemagne pour le second)

### **Avis final 🤔 ?**

Agréable surprise sur le plan de l’ergonomie, de la sécurité (avec le chiffrement de bout en bout), Firefox Send s’avère être un bon outil (qui plus est open-source). En terme de vitesse d’upload, je n’ai pas senti de grosse différence vis à vis des autres plateformes. On regrettera toutefois la taille des fichiers assez faible ainsi que le stockage des données se retrouvent sur le cloud de Google (après rien de vous empêche de l’installer sur votre propre serveur \\\ °\_\_° // ). Sinon j’attends avec impatience la version sur Android !
