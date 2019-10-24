# Construire des logiciels, ensemble, avec Git 🔗

{% hint style="info" %}
**Préambule :** Cet article est la traduction français de « [Building software together with Git](https://eliotberriot.com/blog/2019/03/05/building-sotfware-together-with-git/)« , écrit en anglais par le développeur [Eliot BERRIOT](https://eliotberriot.com/) \(qui développe notamment [Funkwhale](http://www.funkwhale.audio/), un serveur de musique moderne auto-hébergé et [open-source](https://dev.funkwhale.audio/funkwhale/funkwhale) -licence [AGPLv3](https://dev.funkwhale.audio/funkwhale/funkwhale/blob/develop/LICENSE)-, inspiré par Grooveshark. Une version démo est disponible [ici](https://demo.funkwhale.audio/)\).
{% endhint %}

{% hint style="success" %}
La traduction française et relecture à été réalisée par [@Alice](https://bidule.menf.in/users/alice), [@Elanndelh](https://imaginair.es/@Elanndelh), [@Lapineige](https://mamot.fr/@Lapineige) et [@Gordon](https://cybre.space/@gordon). Le texte est mis à disposition **sous licence Creative Commons** [**CC-0**](https://creativecommons.org/publicdomain/zero/1.0/deed.fr). Vous êtes encouragé·es à la partager, la traduire, et la réutiliser. Si la lecture de cet article vous a intéressé, abonnez-vous au blog de l’auteur via son [flux RSS](https://eliotberriot.com/feed.xml), oui suivez-le [sur Mastodon](https://mastodon.eliotberriot.com/@eliotberriot) \(:
{% endhint %}

**En tant que développeuses ou développeurs, nous avons tendance à oublier que nous utilisons un jargon obscur qui nous fait ressembler à d’occultes sorcières ou sorciers.** Il peut y avoir une forme d’élitisme derrière cela, bien sûr, mais je pense que cela arrive aussi parce que le développement logiciel est vraiment un domaine bizarre, avec ses propres problématiques et solutions. De plus la terminologie obscure décrit souvent un concept vraiment spécifique et complexe qu’il serait difficile de décrire autrement.

Il n’y a pas beaucoup de ressources disponibles en ligne qui introduisent Git, GitHub, le concept de commits, branches, gestion de version, _forks_, _pull requests_ et autres termes liés au développement, qui apparaissent comme du jargon auprès d’une audience non-technique.

**Ce texte est une tentative d’améliorer la situation.** Je tiens à remercier vivement [@Ginny](ttps://kitty.town/@GinnyMcQueen/101688023906508502) pour l’idée originale, [@Hush](https://im-in.space/@y6nH) pour la relecture et les corrections, et [toutes les personnes qui ont aidé à la rédaction en partageant leurs retours](https://mastodon.eliotberriot.com/@eliotberriot/101688786698500081).

## 🤝 **Comment collaborons-nous sur du logiciel ?**

**Comme pour tout projet, un projet de développement logiciel rencontre plus de succès lorsque de multiples personnes travaillent sur plusieurs tâches en parallèle.** Dans une organisation typique, on s’attend à trouver comptables, gestionnaires, secrétaires, commerciales et commerciaux, et finalement, tout le monde travaille sur ses propres tâches en même temps, sans problèmes. On veut éviter le plus possible les situations où quelqu’un a besoin d’attendre une autre personne pour pouvoir avancer. On appelle ces situations des goulots d’étranglement. Un exemple de tel goulot serait d’avoir un seul téléphone dans une entreprise de 100 personnes : tout le monde devrait attendre son tour pour pouvoir passer un appel, ce qui serait une perte de temps.

Le développement logiciel fonctionne de manière semblable : des développeur·ses, graphistes, traducteur·ices — quasiment tout le monde — souhaitent travailler sans avoir à se préoccuper du travail des autres, en particulier lorsque le projet grossit et attire des dizaines, voire des centaines, de contributeur·ices. Pour gérer cela, les personnes impliquées dans le développement logiciel se reposent habituellement sur quelques outils et procédés que je vais décrire ci-dessous.

## 🤔 **Qu’est-ce qu’un logiciel ?**

**Ce qu’on appelle logiciel, dans sa forme la plus courante, n’est rien d’autre qu’un ensemble de fichiers texte, également appelée une base de code \(ou** _**codebase**_**, en anglais\).** Ces fichiers texte contiennent des instructions pouvant être exécutées par un ordinateur. Oui, le travail de développement consiste seulement à écrire des choses.

Bien sûr, en tant que développeuse ou développeur, **vous devez penser à** _**ce**_ **que vous écrivez. Comme un·e écrivain·e 😉** . Si vous avez déjà travaillé sur une thèse, ou sur toute forme de rédaction longue, vous avez rencontré de nombreux problèmes rencontrés lorsque des développeur·euses cherchent à travailler sur le même logiciel.

Lorsque vous êtes en pleine rédaction, vous aurez besoin assez souvent de :

* **Relecture** \(_**Reviewing**_ en anglais\) : vous voulez que quelqu’un d’autre lise votre travail, et éventuellement puisse y faire des corrections ou modifications
* **Collaboration** : vous voulez que quelqu’un puisse travailler sur une partie de la documentation, pendant que vous travaillez sur une autre
* **Gestion de versions** \(_**Versioning**_ en anglais\) : la possibilité d’accéder à une précédente version du document \(par exemple parce que vous avez supprimé quelque chose par accident\)

Vous pouvez mettre en place de la relecture et de la collaboration en envoyant par e-mail des copies de votre travail à d’autres personnes, puis en intégrant leurs retours dans votre propre copie, par de simples opérations de copier-coller. Pour la gestion de versions, les fonctionnalités « annuler/refaire » de votre éditeur de texte peuvent aider, de même que sauvegarder des copies entières de votre document sur un autre support de temps à autre.

Cependant, si vous avez déjà travaillé à plus d’une ou deux personnes sur le même document, vous savez que c’est particulièrement pénible à gérer, et est source de nombreuses erreurs. Avez-vous vraiment envoyé la dernière version à vos ami·es ? Avez-vous bien intégré tous leurs retours ? Comment faire pour revenir à la version d’hier de votre travail, alors que la dernière sauvegarde complète date de la semaine dernière ?

Le développement logiciel rencontre _exactement_ les mêmes problèmes. Mais en général, il y a encore plus de personnes impliquées.

## **Et un jour, linus torvalds créa git 😉**

![](https://i1.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/git_logo.png?ssl=1)

Git, et les plateformes associées, telles que [GitHub](https://github.com/), sont une tentative pour résoudre les problèmes mentionnés dans la section précédente. **Git permet à des personnes de contribuer à une même base de code d’une façon saine et efficace.** Néanmoins, pour pouvoir le faire, il est nécessaire de repenser la façon dont on devrait collaborer, et introduire de nouveaux concepts. Tout cela représente du jargon pour toute nouvelle personne, et c’est particulièrement difficile à assimiler, c’est pourquoi je vais tenter de démystifier tout ça.

![](https://i0.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/git-1.jpg?ssl=1)

## **Commits et gestion de version**

Au cœur de [Git](https://git-scm.com/) se trouve un mécanisme permettant de _gérer les versions_ d’une base de code. \(_le **versioning**_ ****en anglais\)

**Chaque version de la base de code est, pour faire simple, un instantané de la base de code, associé à sa date de création. C’est ce qui donne une gestion de version, parce qu’il est possible de remonter dans le temps, pour retrouver n’importe quel instantané.**

Ces instantanés sont appelés _**commits**_. Cependant, faire une copie intégrale du projet pour chaque commit nécessiterait un espace disque phénoménal. [Git](https://fr.wikipedia.org/wiki/GitHub) est plus malin que ça 😉, et il fait en sorte de ne stocker que les différences \(appelées _diffs_\) entre chaque commit

💡 Prenons un exemple simple :

1. Alice débute son projet logiciel, crée un fichier texte contenant 10 lignes, puis crée le premier commit.
2. 3 jours plus tard, elle modifie la ligne 7, et crée un second commit. Ce dernier contiendra le fait que la ligne 7 a été modifiée.
3. 5 jours plus tard, elle supprime la ligne 3, et crée un nouveau commit. Ce commit contiendra le fait qu’une ligne a été supprimée.nenenene

Tous ces commits créent un historique de tout ce qui s’est passé sur le projet \(on parle de _logs_\) :

* Jour 1 : Alice a ajouté 10 lignes
* Jour 4 : Alice a modifié la ligne 7
* Jour 9 : Alice a supprimé la ligne 3

Et si nous voulons revenir au jour 1, il est possible de demander à Git de défaire les changements du jour 9, puis du jour 4, dans cet ordre, ce qui nous ramènera la base de code telle qu’elle était au jour 1. Puis nous pouvons rejouer le commit suivant, celui du jour 4, pour atteindre la version suivante du projet, et enfin rejouer le commit du jour 9 pour obtenir notre dernière version.

Vous vous rappelez sans doute que j’ai mentionné trois fonctionnalités souhaitées : gestion de version, collaboration et relecture. **Les commits nous apportent la gestion de version**, mais également la possibilité d’auditer : qui a fait quoi, et quand. Ça apporte un bonus appréciable.

## **Branches et parallélisation**

[Git Branches](https://fr.atlassian.com/git/tutorials/using-branches/git-checkout) – \([CC BY 2.5 AU](https://creativecommons.org/licenses/by/2.5/au/)\)

![](https://i2.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/git_branches.png?ssl=1)

Le dixième jour, Alice décide de tenter une expérience avec quelque chose de nouveau 🆕, mais elle n’est pas certaine que ça fonctionne. Pour commencer à bidouiller son idée, elle crée ce que git appelle _une branche_. **Vous pouvez vous représenter les branches comme des routes, se séparant parfois en deux. Au bout du compte, deux routes peuvent se rejoindre, mais ce n’est pas obligatoire.**

Dans git, tous les commits se déroulent sur une branche, par défaut sur celle nommée `master`. Donc, si on se représente l’état actuel du projet avec ça en tête, voici à quoi ça pourrait ressembler :

```text
| branche master
|
* Commit du jour 1 : Alice a ajouté 10 lignes
|
* Commit du jour 4 : Alice a modifié la ligne 7
|
* Commit du jour 9 : Alice a supprimé la ligne 3

```

Donc, si Alice crée sa nouvelle branche, nommée `expérimentation`, à partir de la branche `master`, cela donne quelque chose comme :

```text
| branche master
|
* Commit du jour 1 : Alice a ajouté 10 lignes
|
* Commit du jour 4 : Alice a modifié la ligne 7
|
* Commit du jour 9 : Alice a supprimé la ligne 3
|
|\
| \
|  | branche expérimentale

```

La branche `master` existe toujours, sur la gauche, mais Alice est maintenant en train de travailler sur la branche `expérimentale`, sur la droite.

Elle est très productive, et crée quelques commits sur cette branche :

```text
| branche master
|
* Commit du jour 1 : Alice a ajouté 10 lignes
|
* Commit du jour 4 : Alice a modifié la ligne 7
|
* Commit du jour 9 : Alice a supprimé la ligne 3
|
|\
| \
|  | branche expérimentale
|  |
|  * Commit du jour 11 : Alice a ajouté 10 nouvelles lignes
|  |
|  * Commit du jour 13 : Alice a modifié les lignes 5 à 9
```

Puisqu’elle est satisfaite par ses changements, elle décide de _fusionner_ \(_merge_, en anglais\) la branche _expérimentale_ au sein de la branche _master_.

![](https://i1.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/git_merging.gif?ssl=1)

C’est la façon de git d’appliquer les changements d’une branche sur une autre. Vous vous rappelez de l’analogie des routes que j’ai faite ? C’est comme ça qu’une fusion peut être représentée :

```text
|    Route principale (branche master)
|
|\   La route se sépare en deux
| \
|  | Route secondaire (branche expérimentale)
|  |
|  |
|  |
|  |
| /
|/   Les deux routes se rejoignent
|
|    La route principale continue son cours
```

Lorsque la fusion est faite, la branche _expérimentale_ est supprimée, et ses commits sont maintenant présents sur la branche _master_ :

```text
| branche master
|
* Commit du jour 1 : Alice a ajouté 10 lignes
|
* Commit du jour 4 : Alice a modifié la ligne 7
|
* Commit du jour 9 : Alice a supprimé la line 3
|
* Commit du jour 11 : Alice a ajouté 10 nouvelles lignes (depuis la branche expérimentale)
|
* Commit du jour 13 : Alice a modifié les lignes 5 à 9 (depuis la branche expérimentale)
```

Si, pour une quelconque raison, Alice n’était pas satisfaite par son expérience, elle aurait pu la supprimer sans la fusionner, et la branche `master` n’aurait pas été affectée. **Les branches sont un concept puissant, mais également difficile à appréhender dans git**.

![](https://i0.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/i2.wp.com/sir.chamallow.com/wp-content/uploads/2019/03/Git_branch_meme.jpg?ssl=1)

Elles sont utiles pour expérimenter sans risques, mais permettent aussi la collaboration, ce que nous allons voir dans la section suivante.

## **Dépôts et collaboration**

Dans le scénario précédent, Alice était seule. Mais au 14ème jour, son ami Bob vient l’aider sur son nouveau projet 💪. Comment cela fonctionne avec git ?

Lorsqu’Alice a commencé à travailler sur le projet, elle utilisait sa propre copie locale, ce que nous appellerons un _dépôt_ \(_repository_, en anglais\). **Vous pouvez penser à un dépôt comme un espace de travail, appartenant à quelqu’un \(Alice, dans ce cas\).**

Vu que Bob veut pouvoir contribuer, il aura besoin de son propre dépôt. L’une des façons de faire ça est qu’Alice _pousse_, ou publie \(_**push**_, en anglais\) son dépôt sur une plateforme telle que GitHub ou [GitLab](https://about.gitlab.com/), de demander ensuite à Bob de s’y créer un compte et d’utiliser le bouton _**fork**_. Cette opération \(_fourchage_ en français, mais on utilise généralement le terme anglais\) consiste simplement à créer une copie du dépôt de quelqu’un d’autre.

Git et GitHub ont beau avoir des noms similaires, ce sont des choses très différentes, et leur différence devient visible dès lors que l’on commence à parler de collaboration. **Si je reviens à mon analogie du document texte, git est similaire à un éditeur de texte, comme Microsoft Word ou LibreOffice.** C’est un outil que vous installez sur votre ordinateur pour pouvoir travailler sur vos documents \(hors-ligne\). **D’un autre côté, GitHub et les plateformes similaires comme GitLab ou** [**Bitbucket**](https://bitbucket.org/) **sont plus proches de** [**Google Docs**](https://www.google.com/intl/fr-CA/docs/about/) : ce sont des services web qui hébergent votre travail, et le rendent visible et modifiable par d’autres. \(en ligne\)

Vous _n’avez pas besoin_ d’utiliser GitHub si vous utilisez git, mais les deux tendent à être utilisés ensemble car ils se complètent et ont des objectifs différents.

Lorsque Bob _forke_ le dépôt d’Alice, sur GitHub, il se retrouve avec une copie exacte de son dépôt. C’est l’équivalent git d’« envoyer votre thèse par e-mail à un·e ami·e ».

Donc, Bob dispose d’un dépôt fonctionnel, et commence à ajouter ses propres commits sur la branche `master` :

```text
| Espace de travail de Bob / branche Master
|
| (les précédents commits ont été omis)
|
* Commit du jour 11 : Alice a ajouté 10 nouvelles lignes (depuis la branche expérimentale)
|
* Commit du jour 13 : Alice a modifié les lignes 5 à 9 (depuis la branche expérimentale)
|
* Commit du jour 14 : Bob a modifié la ligne 8
|
* Commit du jour 15 : Bob a supprimé la ligne 12
|
```

Bob a ajouté deux commits lors des jours 14 et 15. Il aimerait que cela soit intégré dans le dépôt d’Alice. Une façon d’y arriver en utilisant une plateforme telle que GitHub ou GitLab est de créer une _demande d’intégration_ \(_**pull request**_, ou _**merge request**_ en anglais selon la plateforme\). Ces demandes de collaboration sont souvent abréviées **PRs**.

![](https://i0.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/brace-yourselves-pull-requests-are-coming.jpg?ssl=1)

Est-ce que vous vous souvenez quand Alice a fusionné sa branche `expérimentale` dans la branche `master` dans la section précédente ? Une demande d’intégration consiste simplement à demander à quelqu’un de fusionner une branche provenant de notre dépôt, au sein d’une branche sur son dépôt.

Donc, Bob crée une demande d’intégration \(_Pull Request_\) :

> Bonjour Alice !
>
> J’aimerais fusionner la branche `améliorations` de mon dépôt au sein de la branche `master` de ton dépôt.
>
> J’ai créé un commit qui corrige une faute de frappe, et un autre qui améliore les performances.
>
> N’hésite pas à me répondre si tu as des questions.
>
> Bob

Lorsqu’Alice reçoit cette Pull Request, elle peut relire les commits de Bob \(les modifications, ajouts etc.\), et décider s’ils lui conviennent ou pas. C’est ce que l’on appelle une _relecture de code_ \(_**code review**_ en anglais\). Lors de la relecture de code, Alice va lire les changements apportés par les commits de Bob, y suggérer des modifications, et lorsqu’elle sera satisfaite du résultera, acceptera la Pull Request.

Accepter cette demande fusionnera la branche `améliorations` de Bob dans la branche `master` du dépôt d’Alice.

```text
| Alice's workspace / master branch
|
| (previous commits ommited)
|
* Commit from day 11: Alice added 10 new lines (from experiment branch)
|
* Commit from day 13: Alice edited lines 5 to 9 (from experiment branch)
|
* Commit from day 14: Bob edited lines 8 (from bob/improvements branch)
|
* Commit from day 15: Bob deleted line 12 (from bob/improvements branch)
|
```

```text
| Espace de travail d’Alice / branche Master
|
| (les précédents commits ont été omis)
|
* Commit du jour 11 : Alice a ajouté 10 nouvelles lignes (depuis la branche expérimentale)
|
* Commit du jour 13 : Alice a modifié les lignes 5 à 9 (depuis la branche expérimentale)
|
* Commit du jour 14 : Bob a modifié la ligne 8 (depuis la branche bob/améliorations)
|
* Commit du jour 15 : Bob a supprimé la ligne 12 (depuis la branche bob/améliorations)
|
```

Bien sûr, elle aurait également pu refuser la Pull Request, auquel cas sa branche `master` n’aurait pas été modifiée. **Par ailleurs, la branche de Bob et sa Pull Request n’empêchent pas Alice de travailler sur ses propres branches pendant ce temps : elle peut continuer à ajouter des commits sur sa branche `master`, et ils seraient préservés avec la fusion de la branche de Bob dans la sienne.**

En utilisant les branches, dépôts et Pull Requests, Alice et Bob ont réussi à collaborer sur le même logiciel. C’est génial !

![](https://i0.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/much-success-many-congratulations.jpg?ssl=1)

## **Bonus : Conflits, tickets, et versions**

Si vous avez tout lu jusqu’ici, les choses devraient être un peu moins effrayantes pour vous. Cependant, il y a plusieurs autres choses à savoir au sujet du développement logiciel, et sur la façon dont on collabore tout en travaillant sur le logiciel.

### **Conflits**

**Dans la terminologie de git, un conflit est une situation où deux changements qui concernent les mêmes lignes du même fichier sont faits sur des branches différentes, et que vous essayez de fusionner ces branches.**

Examinons une situation typique de conflit :

* Bob crée un dépôt dérivé de celui d’Alice, comme décrit dans la section précédente sur le _fourchage_
* Bob remarque une coquille quelque part et ajoute un commit à la branche `master` de son dépôt pour corriger la coquille. Il oublie d’ouvrir une pull request immédiatement.
* En même temps, Alice remarque la même coquille et ajoute un commit à la branche `master` de son dépôt pour corriger la coquille.
* Quelques jours plus tard, Bob se souvient d’ouvrir une pull request pour fusionner sa branche `master` dans celle d’Alice
* Malheureusement, puisque la branche `master` d’Alice a un commit en lien avec la même ligne, git ne peut pas faire la fusion automatiquement et se plaindra vertement: « Alice et toi avez édité cette ligne en même temps, quel changement dois-je garder ? »

En résumé, comme dans la vraie vie, les conflits se produisent généralement quand des gens travaillent exactement sur la même chose en même temps. **Deux personnes qui offrent le même livre à une fête d’anniversaire sont l’équivalent, dans le monde physique, de ce que git appelle un conflit.**

![](https://i2.wp.com/auktfrkszm.cloudimg.io/cdn/n/q70/sir.chamallow.com/wp-content/uploads/2019/03/grumpy-git-1.jpg?ssl=1)

Quand ils se produisent, les conflits exigent une résolution humaine et manuelle. Quelqu’un doit lire et comprendre les deux changements en conflit puis généralement choisir celui qui a le plus de sens.

Les moyens simples d’éviter les conflits dans git comprennent :

* **La fusion fréquente de vos branches** : Plus vous attendez, plus il y a de chance que quelqu’un d’autre ait commité un changement qui pourrait interférer avec votre propre travail
* **La coordination avec les autres personnes qui contribuent** : partagez le travail en petites tâches indépendantes, et attribuez ces tâches à des personnes précises. Les tickets, comme il est mis en évidence ci-dessous, peuvent aider !

Les conflits ne sont pas toujours un signe d’un manque de coordination, et ils se produiront vraisemblablement de temps à autres dans n’importe quel projet. Cependant, minimiser les situations de conflits est nécessaire pour réussir à paralléliser efficacement votre travail.

### **Tickets \(« issues »\)**

Les tickets sont une partie importante du développement logiciel. Vous avez peut-être déjà entendu ces phrases: « Veuillez ouvrir un ticket » ou « Veuillez ouvrir un bug dans notre outil de suivi des tickets ». Mais qu’est-ce qu’un ticket ?

Les tickets, également appelés « rapports de bugs » ou « demande d’ajout de fonctionnalité » sont des messages postés sur l’outil de suivi de tickets d’un projet. Les développeur·ses, contributeur·ices et utilisateur·ices de logiciel ouvrent généralement des tickets pour :

* Garder une trace d’un nouveau bug dans le logiciel
* Suggérer une amélioration ou une nouvelle fonctionnalité
* Poser une question sur le comportement du logiciel

**Les tickets sont** _**extrêmement**_ **utiles, parce qu’ils constituent la mémoire d’un projet, et fournissent aussi un aperçu des développements futurs, des demandes populaires et des problèmes habituels que rencontre une communauté.**

Les autres personnes peuvent généralement ajouter des commentaires sur les tickets, discuter des solutions possibles et des écueils à éviter, fournir des solutions de contournement, etc. Quand un développement est nécessaire pour résoudre un ticket ou ajouter une fonctionnalité, un·e développeur·se créera généralement une branche, travaillera sur une solution, puis soumettra une pull request avec les changements. Une fois cette pull request acceptée, le ticket en lien est généralement fermé.

En résumé, voici le cycle de vie typique d’un ticket:

1. Bob rencontre un problème dans le logiciel
2. Bob ouvre un ticket qui décrit le bug
3. Maria, qui rencontre le même problème, ajoute un commentaire sur le ticket et décrit une solution possible
4. Alice décide de travailler sur le ticket
5. Elle s’attribue la responsabilité du ticket, crée une branche, commite les changements qui répondent au problème soulevé dans le ticket et ouvre une pull request avec cette branche
6. La pull request est mergée dans la branche `master`
7. Le ticket de Bob est fermé

Au quotidien, les personnes qui contribuent à un projet ont tendance à résoudre des tickets distincts, pour s’assurer qu’ils ou elles travaillent sur des problèmes différents et réussir à paralléliser le travail sans conflits.

Vous souvenez-vous du conflit qui s’est produit quand Alice et Bob ont tous deux essayé de corriger la même coquille dans le code source ? Si Bob avait ouvert un ticket dès qu’il avait remarqué la coquille, Alice l’aurait remarqué et ils auraient pu décider ensemble qui devrait proposer un correctif.

### **Version \(« releases »\)**

Les versions, également appelées « tags », sont la dernière pièce manquante du processus de développement type. La plupart des projets ont tendance à suivre des cycles similaires :

1. Les mainteneur·ses du projet ou les communautés choisissent un ensemble de tickets jugés prioritaires
2. Les contributeur·ices traitent ces tickets
3. Une fois les tickets sélectionnés traités, une version est publiée
4. Les utilisateur·ices mettent à jour vers la nouvelle version
5. Retour à l’étape 1.

**Une version est un état d’un logiciel qui est distribué au grand-public et sensé améliorer ou remplacer les versions précédentes.**

Généralement, les versions sont nommées en utilisant un motif précis, comme `version 1.2.3`, `version 1.2.4` et `version 1.3`.

## **Conclusion**

J’espère que ce texte vous a plu et que les explications vous ont donné une vue plus claire de ce qui se passe en développement logiciel.

Il faut quelques efforts pour tout démêler et montrer l’utilité de tout ceci d’une manière non-technique. Si vous pensez que j’ai échoué quelque part ou qu’il manque quelque chose, n’hésitez pas à me le faire savoir !

