---
description: NTP, le serveur de temps
icon: hourglass-end
---

# NTP

Vous avez surement déjà lu récemment des articles sur les serveurs de temps (qui permets la synchronisation horaire), un aspect souvent délaissé par le département ou les services informatique en entreprise. Si les profils du milieu NetOps et DevOps ont compris l’intérêt d’avoir un bon **résolveur DNS** (un autre aspect important d’une infra), concernant le NTP (les serveurs de temps), la marge de progression est encore importante…

## C’est quoi NTP ?

![](https://i1.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/05/cquestcequecest.gif?ssl=1)

**NTP** ? Le « Network Time Protocol » (NTP) est l’un des plus anciens protocoles d’Internet **encore en service 🙂** . Il fut conçu pour offrir une précision inférieure à la seconde dans la synchronisation des horloges et remplace à ce titre le _Time protocol_ (TP, [RFC 868](https://tools.ietf.org/html/rfc868)), datant de mai 1983. Ce protocole est le fruit de travaux qui ont été réalisés en grande partie par l’Université du Delaware sous la houlette du professeur [David L. Mills](https://fr.wikipedia.org/wiki/David_L._Mills), professeur d’informatique à l’[Université du Delaware](https://fr.wikipedia.org/wiki/Universit%C3%A9_du_Delaware).

## **Schéma d’architecture des serveurs NTP**

![](https://i2.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/i2.wp.com/sir.chamallow.com/wp-content/uploads/2019/03/Architecture_NTP_fr.png?ssl=1)

Sur **Windows10** par exemple, Microsoft propose par défaut deux serveurs de temps de référence : [**time.windows.com**](http://time.windows.com/) ou [**time.nist.gov**](http://time.nist.gov/). Problème le premier répond trop souvent absent provoquant un échec de synchronisation avec toutes les problématiques que cela peut engendrer derrière…. Quand au second, il s’agit de celui du NIST (le « National Institute of Standards and Technology » du département du commerce des Etats-Unis). Ne serait-ce que pour des raisons de cybersécurité, je vous conseil de le remplacer par un autre.

Sur les appareils basé sur MacOS, Apple propose par défaut son serveur de temps maison : time.apple.com. Je n’ai pas réussit à trouver plus d’informations concernant leur fonctionnement.

## **Pourquoi changer son NTP 🤔 ?**

A cause de la recrue d’essence des cyberattaques, le NTP est devenue une cible privilégiée dans les [attaques DDoS par reflexion](https://www.bortzmeyer.org/attaques-reflexion.html) (comme le DNS ou le STMP). L’article récapitulatif présent [sur le blog de Stéphane Bortzmeyer](https://www.bortzmeyer.org/ntp-reflexion.html) résume bien la situation.

Et pour anticiper ce genre d’attaques je vous invite à la lecture de ce [guide de **l’ANSSI**](https://www.ssi.gouv.fr/entreprise/guide/comprendre-et-anticiper-les-attaques-ddos/) : « **Comprendre et anticiper les attaques DDoS**« .

Vous pouvez également consulter régulièrement la [page Insights du site DDoS Mon](https://ddosmon.net/insight/) qui vous donnent les dernières statistiques du domaine.

## **Changer son NTP** ⚙

Si le résolveur DNS 8.8.8.8 de Google vous est familier, sachez qu’il existe sont alter-ego pour les serveurs de temps. Il s’agit de [**time.google.com**](https://developers.google.com/time/). Il à l »avantage d’être public est fiable. Si Google n’est vous plait pas, vous en trouverez d’autres sur ceux indexés par le projet [**NTP Pool Project**](https://www.ntppool.org/fr/)\* (ceux concernant la zone géographique de la France sont sur [cette page](https://www.ntppool.org/zone/fr)). Il s’agit là du « serveur de temps » présent par défaut dans la plupart des distributions Linux ainsi que de nombreux appareils réseaux.

(\*) L’utilisation de **pool.ntp.org** est gratuite dans la plupart des cas (cependant si vous avez un très grand nombre de clients, il est possible que l’équipe du projet vous demandent une contribution.)

## **Liens annexes**

* [Liste de serveurs de temps NTP français (Strate 1 & 2)](https://services.renater.fr/ntp/serveurs_francais) (liste régulièrement mis à jour par Renater)
* Fiche Wikipédia France du [Protocole NTP (Network\_Time\_Protocol)](https://fr.wikipedia.org/wiki/Network_Time_Protocol)
* Page de la [Network Time Fondation](https://www.nwtime.org/)
* Configurer [Google Public NTP](https://developers.google.com/time/guides) sur votre machine
* Configurer un [client NTP sous Linux](https://www.it-connect.fr/configurer-un-client-ntp-sous-linux/)
* Configurer un [serveur NTP sous Windows Server](https://www.msnoob.com/configure-ntp-server-setting-on-windows-server.html)
* Configurer [OpentNtpd sur OpenBSD ou FreeBSD](https://calomel.org/ntpd.html)
* Site internet du [NTP Pool Project](https://www.ntppool.org/fr/) / [Communautée](https://community.ntppool.org/)
* Différence [NTP vs SNTP](https://fr.galsys.co.uk/news/sntp-vs-ntp/)
