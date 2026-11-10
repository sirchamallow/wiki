---
icon: gear
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

# Logiciels

## Warp.dev

{% embed url="https://www.warp.dev/" %}

Warp est un émulateur de terminal écrit en **Rust**. Il se distingue par des fonctionnalités telles que Warp Drive pour le partage de commandes entre équipes, Warp AI pour les suggestions et l'assistance des commandes, ainsi qu'un IDE moderne avec une sélection de texte et un positionnement du curseur.

***

## Firefox

{% embed url="https://www.mozilla.org/fr/firefox/mac/" %}

Navigateur web de la fondation Mozilla orientée vie privée

{% embed url="https://www.mozilla.org/fr/firefox/developer/" %}

Firefox Developer Edition Variante du navigateur web de la fondation Mozilla orientée vie privée

### Extensions & Thèmes

Découvrez divers extensions & thèmes sur ce wiki en cliquant sur le lien

{% content-ref url="../../logiciels/browsers/firefox-extensions/" %}
[firefox-extensions](../../logiciels/browsers/firefox-extensions/)
{% endcontent-ref %}

***

## WiFi Signal : Strength Analyzer

{% embed url="https://www.intuitibits.com/products/wifisignal/" %}

WiFi Signal lets you monitor your Wi-Fi network’s status and signal quality, notifying you about changes in your Wi-Fi connection

***

## Onyx

{% embed url="https://www.titanium-software.fr/fr/onyx.html" %}

Une trousse à outils indispensable qui dispose d’une centaine de fonctionnalités, telles que, le nettoyage du Mac, la reconstruction de services défectueux, la vérification de la structure du système de fichiers, l’exécution des scripts de maintenance, la configuration des paramètres cachés du Finder, du Dock, de Safari et de plusieurs applications Apple…

***

## Duet Display

{% embed url="https://www.duetdisplay.com/fr" %}

Duet transforme votre iPhone ou iPad dans l’écran supplémentaire le plus avancé pour votre Mac & PC.

***

## Magnet

{% embed url="https://magnet.crowdcafe.com/index.html" %}

Permets de redimensionner les fenêtres de manière appropriée.

***

## CleanMyMac

{% embed url="https://macpaw.com/fr/cleanmymac" %}

Supprimez des tonnes de fichiers inutiles ou malveillants, et accélérez et organisez votre Mac.

CleanMyMac X regroupe plus de 30 outils conçus pour vous aider à résoudre les problèmes courants sur Mac. Il vous permet de gérer votre espace de stockage et vos applications, et de surveiller la santé de votre ordinateur.

***

## WiFi Explorer : Scanner

{% embed url="https://www.intuitibits.com/products/wifiexplorer/" %}

Découvrez, surveillez et dépannez les réseaux sans fil.

Identifiez rapidement les conflits de canaux, les chevauchements de signaux ou les problèmes de configuration susceptibles d'affecter la connectivité et les performances de votre réseau sans fil

***

## TopNotch

{% embed url="https://topnotch.app/" %}

Masquer le Notch du MacBook Pro 14 / 16″ et MacBook Air (M2)

***

## Latest

{% embed url="https://max.codes/latest/" %}

Pour maintenir automatiquement ses apps à jour sur Mac, Vous pouvez confier la tâche à un utilitaire open-source pour macOS

***

## Menu Bar Spacing

Personnaliser l'espace des icônes présent dans votre barre de menu.

Très pratique si vous avez beaucoup d'extensions ou un MacBook avec un notch

{% embed url="https://github.com/sindresorhus/menu-bar-spacing-meta/releases" %}

{% embed url="https://sindresorhus.com/menu-bar-spacing" %}

***

## Velja

{% embed url="https://sindresorhus.com/velja" %}

Vous permets de choisir dans quel navigateur sera ouvert vos liens, et de changer ensuite

***

## Homebrew

{% embed url="https://brew.sh/fr/" %}

Un gestionnaire de paquets pour macOS gratuit et open-source écrit en Ruby.&#x20;

Installation en ligne de commande. Copiez et collez dans une fenêtre du Terminal.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

***

## MacPorts

{% embed url="https://www.macports.org/install.php" %}

Un autre gestionnaire de paquets pour macOS

***

## MicMac

{% embed url="https://www.micmac-app.fr/fr/index.html" %}

Un outil gratuit permettant la configuration rapide, le nettoyage et la maintenance quotidienne du système macOS. Il est développé par [**Denis Dubois**](https://x.com/dedubo), rédacteur pour le magazine [VVMac Hebdo](https://www.vvmac.com/), l'utilitaire s’inspire de l’application populaire [Onyx](https://www.justgeek.fr/onyx-un-utilitaire-de-nettoyage-complet-pour-votre-mac-83684/). \
\
La différence ? MicMac intègre des fonctionnalités supplémentaires qui le rendent encore plus efficace pour personnaliser et maintenir votre ordinateur en parfaite santé

***

## Kaomoji Drawer

{% embed url="https://dakotafelder.com/kaomoji-drawer/" %}

Une application qui permets l'accès aux émoticônes japonaises (kaomojis) directement depuis la barre de menu Mac

***

## Maccy

{% embed url="https://maccy.app/" %}

Maccy est un gestionnaire de presse-papiers destiné écrit en **Swift**.

***

## **MARTA File Manager**

{% embed url="https://marta.sh/download/" %}

**MARTA File Manager** est une application de gestion de fichiers écrite entièrement en Swift, elle se distingue par sa performance exceptionnelle et son respect de la vie privée.

***

## Nping

{% embed url="https://github.com/hanshuaikang/Nping" %}

**Nping,** un outil de ping développé en Rust. Il prend en charge le ping simultané pour plusieurs adresses, l'affichage de graphiques visuels, les mises à jour de données en temps réel et d'autres fonctionnalités.

#### Installation via HomeBrew

```bash
brew tap hanshuaikang/nping # Installer 
brew install nping          # Installer nping
nping --help                # Aide
```

#### Usage

```bash
# 🏎 Nping mean NB Ping, A Ping Tool in Rust with Real-Time Data and Visualizations
nping www.google.com www.apple.com www.microsoft.com -c 20 -i 2
nping --help

# Usage
nping [OPTIONS] <TARGET>...
Options:
  -c, --count <COUNT>        Number of pings to send [default: 65535]
  -i, --interval <INTERVAL>  Interval in seconds between pings [default: 0]
  -6, --force_ipv6           Force using IPv6
  -m, --multiple <MULTIPLE>  Specify the maximum number of target addresses, Only works on one target address [default: 0]
  -v, --view-type <VIEW_TYPE>  view mode graph or table [default: graph]
  -h, --help                 Print help
  -V, --version              Print version

# Arguments
<TARGET>...  target IP address or hostname to ping
```

***

## PastePal

{% embed url="https://indiegoodies.com/pastepal" %}

Un gestionnaire de presse-papier pour MacOS.

***

## MacOptimizers

{% embed url="https://macoptimizers.informatiqueconnect.fr/" %}

Une application native gratuite conçue pour analyser, nettoyer et optimiser un Mac. Développée en Swift

***

## Stats

{% embed url="https://mac-stats.com/" %}

Une application légère et gratuite pour la barre de menus qui vous offre une vue d'ensemble complète de l'état de votre système : processeur, carte graphique, mémoire vive, disque, réseau et bien plus encore

***

## MacDirStat

{% embed url="https://github.com/phalladar/MacDirStat" %}

Un outil de visualisation d'espace disque

***

## Mole

{% embed url="https://mole.fit/fr/" %}

Mole. Nettoyez les fichiers inutiles, gérez les apps, lancez la maintenance, analysez le disque et suivez l’état en direct dans une app Mac native.

***

## LitlleSnitch mini

{% embed url="https://www.obdev.at/products/littlesnitch-mini/index.html" %}

**Little Snitch Mini** est une application conçue pour offrir une approche plus accessible de la sécurité réseau. Contrairement au pare-feu traditionnel de macOS (qui gère principalement le trafic _entrant_), Little Snitch Mini surveille le trafic _sortant_. Il vous indique exactement quelles données vos applications envoient sur Internet, vers quels pays et vers quels serveurs. La version Mini adopte une **approche purement visuelle et non intrusive**. Elle s'intègre discrètement dans la barre des menus de votre Mac et s'appuie sur le framework d'extensions système moderne d'Apple

***

## Procexp-Mac&#x20;

{% embed url="https://github.com/microsoft/Procexp-Mac" %}

Sysinternals Process Explorer pour Mac est une implémentation native macOS de l'interface Process Explorer. Elle offre une arborescence des processus en temps réel, l'inspection des modules, des descripteurs et des threads dans le volet inférieur, des propriétés détaillées par processus, des graphiques de performance système, l'inspection de la signature de code et des équivalents macOS pour les flux de travail de Process Explorer.
