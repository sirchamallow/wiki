---
description: Red Hat Enterprise Linux (RHEL)
icon: redhat
---

# REHL multiverse

## Fedora Linux

### Présentation

Fedora Linux est un système d’exploitation libre et une distribution Linux communautaire développée par le projet Fedora et sponsorisée par l’entreprise Red Hat, qui lui fournit des développeurs ainsi que des moyens financiers et logistiques. ([Wikipedia](https://fr.wikipedia.org/wiki/Fedora_Linux))

## **Alternatives**

### **AlmaLinux** et **RockyLinux**

#### Présentation

Il existe d'autres distributions basées sur REHL, comme **AlmaLinux** ou **RockyLinux**&#x20;

AlmaLinux et RockyLinux se définissent comme des **systèmes d’exploitations d’entreprises** et s’adressent en premier lieu aux entreprises et aux organisations à la recherche d’une distribution Linux stable et mise à jour, à des fins commerciales.&#x20;

### Pourquoi les utiliser  ?

Car ils constituent une alternative gratuite à Red Hat Enterprise Linux (REHL), qui est payant.\
\
La solution est particulièrement pertinente pour les serveurs, qui ont besoin d’un système d’exploitation fiable.

### Différences avec RHEL

Voici les principales différences avec Red Hat Enterprise Linux (RHEL).

**AlmaLinux** se positionne comme une alternative gratuite et communautaire à RHEL, offrant une **compatibilité ABI**. La distribution peut désormais inclure des correctifs de bugs plus rapidement que RHEL qui suit son propre cycle de mises à jour. La distribution utilise également plusieurs sources pour son code, dont CentOS Stream.&#x20;

{% hint style="info" %}
Alma Linux est géré par une organisation à but non lucratif. Il bénéficie d'un financement annuel garanti de 1 million de dollars [de la part de sponsors](https://www.techtarget.com/searchdatacenter/tip/Rocky-Linux-vs-AlmaLinux-Which-is-better).
{% endhint %}

**Rocky Linux** de son côté cherche à maintenir une **compatibilité binaire 1:1** avec RHEL. C'est-à-dire qu'il vise une reproduction exacte du comportement d'un système de référence. Cela garantit que les applications fonctionneront de manière identique sur les deux systèmes. Et cela implique une correspondance parfaite des bibliothèques, des versions du noyau et des configurations système.

{% hint style="info" %}
Rocky Linux est une entreprise à but lucratif détenue par un seul individu
{% endhint %}

## Compatibilité ABI et binaire 1:1

Il s'agit de deux concepts liés, mais distincts dont voici les différences :

La **compatibilité ABI** (Application Binary Interface) concerne l'interface entre les applications compilées et le système d'exploitation. Elle permet aux applications compilées de fonctionner sans recompilation sur des systèmes avec la même ABI. Et de se concentrer sur la stabilité des appels système, des structures de données et des conventions d'appel.

{% hint style="info" %}
La compatibilité ABI permet généralement des **mises à jour et des correctifs plus rapides.**
{% endhint %}

La **compatibilité binaire 1:1** quant à elle vise une reproduction exacte du comportement d'un système de référence. En garantissant que les applications fonctionneront de manière identique sur les deux systèmes. Cela implique une correspondance parfaite des bibliothèques, des versions du noyau et des configurations système.

{% hint style="info" %}
La compatibilité binaire 1:1 offre une garantie plus forte de fonctionnement identique, mais peut limiter les améliorations indépendantes.
{% endhint %}
