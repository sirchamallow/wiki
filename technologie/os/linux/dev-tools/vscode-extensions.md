---
icon: code
description: Il existe de multiples extensions pour l'ide VSCode, en voici une sélection
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# VSCode

## Extensions

Voici comment installer des extensions très utiles pour VS Code

{% hint style="info" %}
Copier / Coller les lignes de commandes suivantes dans votre **terminal** pour installer les extensions
{% endhint %}

<pre class="language-bash"><code class="lang-bash">## Stylish
code --install-extension emmanuelbeziat.vscode-great-icons # VSCode Great Icons
code --install-extension github.github-vscode-theme        # GitHub Theme
code --install-extension Catppuccin.catppuccin-vsc         # Catppuccin Theme
code --install-extension Catppuccin.catppuccin-vsc-icons   # Catppuccin icons
code --install-extension mhutchie.git-graph                # Git Graph
code --install-extension oderwat.indent-rainbow            # indent-rainbow
code --install-extension soerenuhrbach.vscode-deepl        # Deepl Translate
code --install-extension adamvoss.vscode-languagetool      # LanguageTool
code --install-extension adamvoss.vscode-languagetool-en   # LanguageTool (en)
code --install-extension adamvoss.vscode-languagetool-fr   # LanguageTool (fr)

## Tools Microsoft VSCode
code --install-extension MS-vsliveshare.vsliveshare         # Visual Studio Live Share
code --install-extension ms-vscode.remote-repositories      # Remote Repositories
code --install-extension ms-vscode-remote.remote-wsl        # Windows Subsystem for Linux (WSL)
code --install-extension ms-vscode-remote.remote-ssh        # Remote - SSH
code --install-extension ms-vscode-remote.remote-ssh-edit   # Remote - SSH: Editing Configuration Files
code --install-extension ms-vscode-remote.vscode-remote-extensionpack # Remote Development
code --install MS-CEINTL.vscode-language-pack-fr            # French Language Pack for Visual Studio Code

## Tools
code --install-extension dbaeumer.vscode-eslint             # ESLint
code --install-extension Postman.postman-for-vscode         # Postman
code --install-extension Rubymaniac.vscode-paste-and-indent # Paste and Indent
code --install-extension usernamehw.errorlens               # Error Lens
code --install-extension jock.svg                           # SVG
code --install-extension IronGeek.vscode-env                # ENV
code --install-extension KnisterPeter.vscode-commitizen     # Commitizen
code --install-extension sidthesloth.html5-boilerplate      # HTML Boilerplate
<strong>code --install-extension ms-ossdata.vscode-postgresql       # PostgreSQL
</strong>code --install-extension redhat.ansible                     # Ansible

## Language Support
code --install-extension rebornix.ruby               # Ruby
code --install-extension rust-lang.rust              # Rust
code --install-extension dustypomerleau.rust-syntax  # Rust syntax
code --install-extension ms-python.python            # Python
code --install-extension golang.Go                   # Go
code --install-extension redhat.vscode-yaml          # YAML
code --install-extension redhat.vscode-xml           # XML
</code></pre>

## Polices

Voici les étapes à suivre pour changer la police de caractère sur Visual Studio Code

1. **Ouvrez les paramètres** :
   * Allez dans le menu en haut de l'écran et sélectionnez `Fichier` > `Préférences` > `Paramètres`.
   * Vous pouvez aussi utiliser le raccourci `Ctrl + ,`.
2. **Recherchez la police** :
   * Dans la barre de recherche des paramètres, tapez `font family`.
3. **Modifiez la police** :
   * Dans la section `Editor: Font Family`, entrez le nom de la police que vous souhaitez utiliser. Par exemple, pour utiliser `Fira Code`, vous pouvez entrer `Fira Code`.
4. **Enregistrez et redémarrez** :
   * Enregistrez vos modifications et redémarrez VS Code pour appliquer les changements.