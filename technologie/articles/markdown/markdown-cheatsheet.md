---
description: Pour formater votre texte vous pouvez utiliser la syntaxe markdown
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# 📋 Markdown cheatsheet

Plus d'informations sur le Markdown

## Styles de texte

Vous pouvez utiliser `_` ou `*` autour d'un mot pour le mettre en italique. Mettez-en deux pour le mettre en gras.

* `_italique_` s'affiche ainsi : _italique_
* `**gras**` s'affiche ainsi : **gras**
* `**_gras-italique_**` s'affiche ainsi : _**gras-italique**_
* `~~barré~~` s'affiche ainsi : ~~barré~~
* ++`barré`++ s'affiche ainsi : surbrillance

***

## Blocs de code

Créez un bloc de code en indentant chaque ligne avec quatre espaces, ou en mettant trois accents graves sur la ligne au dessus et en dessous de votre code. Exemple :

` ```bloc de code``` `

s'affiche ainsi :

```
bloc de code
```

***

## Liens

Créez un lien intégré en mettant le texte désiré entre crochets et le lien associé entre parenthèses.

`Top [Le wiki de sirchamallow](`[`https://sirchamallow.gitbook.io/wiki/`](https://sirchamallow.gitbook.io/wiki/)`) !`

s'affichera :

Top [le wiki de sirchamallow](https://sirchamallow.gitbook.io/wiki/)

***

## Images

Utilisez une image en ligne en copiant son adresse (finissant par `.jpg`, `.png`, `.gif` etc…) avec un texte alternatif entre crochets (qui sera affiché si l'image n'apparaît pas) et le lien entre parenthèses. Vous pouvez aussi ajouter un texte qui apparaîtra au survol de la souris grâce aux `"`.

```
![le logo de Framasoft](https://framasoft.org/nav/img/logo.png)
```

On peut ajouter un texte au survol :

```
![Le logo de Framasoft](https://framasoft.org/nav/img/logo.png "Un bien beau logo !")
```

En survolant l'image avec votre souris le texte apparaîtra :)

***

## Citation

Les citations se font avec le signe `>` :

```
> Oh la belle prise !
```

> Oh la belle prise !

***

## Listes

Vous pouvez créer des listes avec les caractères `*` et `-` pour des listes non ordonnées ou avec des nombres pour des listes ordonnées.

### Liste non ordonnée

```
* une élément
* un autre
 * un sous élément
 * un autre sous élément
* un dernier élément
```

* une élément
* un autre
  * un sous élément
  * un autre sous élément
* un dernier élément

### Liste ordonnée

```
1. élément un
2. élément deux
```

1. élément un
2. élément deux

### Liste de tâches

```markdown
- [x] #42
- [ ] https://sir.chamallow.com
- [ ] Lire l'expérience
```

* [x] \#739&#x20;
* [ ] [https://sir.chamallow.com-liste-de-taches/](https://sir.chamallow.com-liste-de-taches/)
* [ ] Lire l'expérience

***

## Notes de bas de page <a href="#footnotes" id="footnotes"></a>

Vous pouvez ajouter des notes de bas de page à votre contenu à l’aide de cette syntaxe entre crochets :

```
Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].

[^1]: My reference.
[^2]: To add line breaks within a footnote, prefix new lines with 2 spaces.
  This is a second line.
```

La note de bas de page s’affiche comme suit :

![](https://docs.github.com/assets/cb-27019/images/help/writing/footnote-rendered.png)

**Remarque** : La position d’une note de bas de page dans votre Markdown n’influence pas l’endroit où la note de bas de page sera affichée. Vous pouvez écrire une note de bas de page juste après votre référence à la note de bas de page ; elle sera quand même affichée en bas du markdown.

Les notes de bas de page ne sont pas prises en charge dans les wikis.

Source : [Docs GitHub](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#footnotes)

***

## Titres

Pour faire un titre, vous devez mettre un `#` devant la ligne. Pour faire un titre plus petit, ajoutez un `#` (jusque 6) :

```
H1 title (huge)
Markdown code: # Huge title

H2 title (large)
Markdown code: ## Large title

H3 title (medium)
Markdown code: ### Medium title

H4 title (regular)
Markdown code: #### Regular title

H5 title (small)
Markdown code: ##### Small title

H6 title (tiny)
Markdown code: ###### Tiny title
```

Vous pouvez également souligner le texte en utilisant `===` ou `---` pour créer des titres.

```
Un grand titre
=============
```

***

## Ligne Horizontale

Markdown code: `---`

***

## Tableaux

Pour créer un tableau vous devez placer une ligne de tirets (`-`) sous la ligne d'entête et séparer les colonnes avec des `|`. Vous pouvez aussi préciser l'alignement en utilisant des `:`. :

```
| Aligné au centre | Centré | Aligné au centre |
| :-: | :-: | :-: |
| Aligné | ce texte | Aligné |
| Aligné au | est | Aligné au |
| Aligné au centre | centré | Aligné au centre |

| Aligné à gauche | Gauche | Aligné à gauche |
| :- | :- | :- |
| Aligné | ce texte | Aligné |
| Aligné à | est | Aligné à |
| Aligné à gauche | à gauche | Aligné à gauche |

| Aligné à droite | Droite | Aligné à droite |
| -: | -: | -: |
| Aligné | ce texte | Aligné |
| Aligné à | est | Aligné à |
| Aligné à droite | à droite | Aligné à droite |
```

| Aligné au centre | Ce texte est | Aligné au centre |
| ---------------- | ------------ | ---------------- |
|          Aligné  | ce texte     |          Aligné  |
|       Aligné au  |    est       |       Aligné au  |
| Aligné au centre | centré       | Aligné au centre |

| Aligné à gauche | Ce texte est | Aligné à droite |
| --------------- | ------------ | --------------- |
| Aligné          | ce texte     | Aligné          |
| Aligné à        | est          | Aligné à        |
| Aligné à gauche | à gauche     | Aligné à droite |

<table><thead><tr><th width="249.33333333333331">Aligné à droite</th><th>Ce texte est</th><th>Aligné à droite</th></tr></thead><tbody><tr><td>                Aligné</td><td>        ce texte</td><td>                 Aligné</td></tr><tr><td>             Aligné à</td><td>                est</td><td>              Aligné à</td></tr><tr><td> Aligné à droite</td><td>        à droite</td><td>   Aligné à droite</td></tr></tbody></table>

***

## Alertes

**Insert a tip box**\
Markdown code: `| This is a tip.`

{% hint style="success" %}
This is a tip.
{% endhint %}

**Insert an information box**\
Markdown code: `|| This is an information.`

{% hint style="info" %}
This is an information.
{% endhint %}

**Insert a warning box**\
Markdown code: `||| This is a warning.`

{% hint style="danger" %}
This is a warning.
{% endhint %}
