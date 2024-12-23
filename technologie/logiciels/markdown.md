---
icon: markdown
---

# Markdown

## Prise de notes

{% embed url="https://standardnotes.com" %}

{% embed url="https://stackedit.io" %}

## Wiki

{% embed url="https://gitbook.com" %}

{% embed url="https://hackmd.io" %}

***

## Conversion

### URL > Markdown

Markdownifier, un outil pour converntur une url ou une page en Markdown

{% embed url="https://heckyesmarkdown.com/" %}

### Excel > Markdown

{% embed url="https://tableconvert.com/" %}

### JSON Array > Markdown

{% embed url="https://tableconvert.com/json-to-markdown" %}

### HTML Table > Markdown

[https://tableconvert.com/html-to-markdown](https://tableconvert.com/html-to-markdown)

### Générateur de tableau

{% embed url="https://www.tablesgenerator.com/markdown_tables" %}

### Microsoft MarkItDown Converter

Un outil Python pour convertir des fichiers et des documents bureautiques en Markdown.

{% embed url="https://msftmd.replit.app/" %}

{% hint style="info" %}
Source : [https://github.com/microsoft/markitdown](https://github.com/microsoft/markitdown)
{% endhint %}

***

## Extensions

### Chrome

{% embed url="https://github.com/benweet/stackedit" %}

***

### VScode

Voici comment installer des extensions très utiles pour VS Code

{% hint style="info" %}
Copier / Coller les lignes de commandes suivantes dans votre **terminal** pour installer les extensions
{% endhint %}

{% code fullWidth="false" %}
```
code --install-extension foam.foam-vscode                    # Foam
code --install-extension shd101wyy.markdown-preview-enhanced # Markdown Preview Enhanced
code --install-extension DavidAnson.vscode-markdownlint      # markdownlint
code --install-extension bierner.markdown-emoji              # Markdown Emoji
```
{% endcode %}

## Hébergement

Vous pouvez héberger votre **blog Jekyll sur GitHub sans passer par une installation locale** en utilisant un thème Jekyll déjà hébergé sur GitHub. \
\
Voici un guide détaillé :

### Étape 1 : Choisir un thème Jekyll

1. Allez sur **Jekyll Themes** ou un autre site proposant des thèmes Jekyll.
2. Parcourez les thèmes disponibles et choisissez celui qui vous plaît. \
   Voici quelques exemples : [Chirpy Jekyll Theme](https://github.com/cotes2020/jekyll-theme-chirpy), [Orbit](https://github.com/sharu725/online-cv), [Linkhub](https://github.com/digitalmalayali/linkhub-jekyll-theme)
3. Cliquez sur le bouton "Fork" en haut à droite de la page du thème pour copier le dépôt du thème dans votre propre compte GitHub.

### Étape 2 : Renommer le dépôt

1. Allez sur votre compte **GitHub** et trouvez le dépôt que vous venez de forker.
2. Cliquez sur le bouton "Settings" (Paramètres) du dépôt.
3. Dans la section "Repository name" (Nom du dépôt), renommez le dépôt en `username.github.io` (remplacez `username` par votre nom d'utilisateur GitHub).
4. Cliquez sur "Rename" pour confirmer le changement.

### Étape 3 : Configurer GitHub Pages

1. Toujours dans les paramètres de votre dépôt, allez dans l'onglet "Pages" situé dans la barre latérale gauche.
2. Sous "Source", sélectionnez la branche `main` (ou `gh-pages` selon le thème) et le dossier `/` pour la source de votre site.
3. Cliquez sur "Save" pour appliquer les modifications.

### Étape 4 : Personnaliser votre blog

1. Retournez à la page principale de votre dépôt.
2. Utilisez l'éditeur de fichiers de GitHub pour modifier les fichiers de configuration et de contenu :
   * **\_config.yml** : Ce fichier contient les paramètres de votre site. Modifiez-le pour personnaliser le titre, la description, les liens sociaux, etc.
   * **\_posts** : Ce dossier contient les articles de votre blog. Vous pouvez ajouter de nouveaux fichiers Markdown (`.md`) pour créer de nouveaux articles, ou modifier les articles existants.
3. Pour ajouter un nouvel article, cliquez sur "Add file" > "Create new file", nommez le fichier selon le format `YYYY-MM-DD-nom-de-l-article.md`, et ajoutez le contenu de votre article en utilisant la syntaxe Markdown.

### Étape 5 : Vérifier votre site

1. Une fois vos modifications enregistrées, **GitHub Pages** générera automatiquement votre site.
2. Votre blog sera disponible à l'adresse `https://username.github.io` (remplacez `username` par votre nom d'utilisateur GitHub).
3. Visitez cette URL pour voir votre blog en ligne.

Et voilà ! Vous avez maintenant un blog Jekyll hébergé sur GitHub Pages sans avoir besoin d'installer Jekyll localement :)
