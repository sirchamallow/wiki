---
icon: face-smile
description: Quelques astuces pour MacOS
---

# Astuces

## Afficher le chemin d’accès d’un fichier sur Mac (fil d’ariane)

Pour afficher le chemin d’accès fichier d’un fichier sur Mac en bas du Finder, ouvrez le Finder et positionnez-vous sur le fichier de votre choix. \
\
Pressez ensuite les touches du clavier **`⌘ (cmd) + ⌥ (alt) + P`**

## Afficher les fichiers et dossiers cachés

Pour rendre visibles les fichiers dissimulés sur votre Mac,  ouvrez le Finder.

Pressez ensuite les touches du clavier **`⌘ (cmd) + ⇧ (maj) + .`** pour révéler les fichiers et dossiers masqués. Les éléments cachés apparaissent alors en semi-transparence. Vous pouvez y accéder normalement :)\
\
Pour les masquer à nouveau, réutilisez la combinaison **`⌘ + ⇧ + .`** dans le dossier concerné.

### Afficher le chemin d’accès d’un fichier sur Mac

Si vous désirez copier-coller le chemin d’accès d’un fichier sur Mac, il faut vous rendre sur le fichier, **faire un clic droit** puis maintenir appuyer la touch&#x65;**`⌥ (alt)`.** \
\
Vous verrez comme dans notre exemple apparaître « copier « nom\_du\_fichier.mp3 » en tant que nom de chemin ».

## Comment forcer la fermeture d’une app sur votre Mac

Si une app cesse de répondre et que vous ne pouvez pas la quitter normalement, suivez ces étapes pour forcer sa fermeture.

{% embed url="https://support.apple.com/fr-fr/102586" %}

## Installer Windows sur un Mac non récent avec Boot Camp

{% embed url="https://support.apple.com/fr-fr/guide/bootcamp-assistant" %}

## Prendre des captures d’écran

{% embed url="https://support.apple.com/fr-fr/guide/mac-help/mh26782/mac" %}

## Convertir les fichiers HEIC en JPEG

Comment faire pour convertir en JPEG des photos au forme HEIC ?\
En utilisant un outil de traitement d’image : **`ImageMagick`**.

#### Windows

1. [Télécharger ](https://imagemagick.org/script/download.php)et Installer ImageMagick.
2. Ouvrir une ligne de commande (`cmd.exe`).
3. Aller dans le répertoire qui contient les fichiers HEIC.
4. Exécuter la commande suivante :

```powershell
magick mogrify -format jpg *.heic
```

Chaque conversion d’image prendra quelques secondes :)