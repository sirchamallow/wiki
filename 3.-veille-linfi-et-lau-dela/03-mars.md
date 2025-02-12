# 03 - Mars

➫ Chaque mois, vous retrouverez dans mes carnets de veille un large éventail de sujets, allant des dernières actualités aux tendances du moment, en passant par du contenu froid et des coups de cœur.

➫ [**Le wiki à été mis à jour**](https://sirchamallow.gitbook.io/wiki/), n’hésitez pas à le consulter :)

***

## \<Dev>

Être Développeur, c’est être rigoureux (•̀ᴗ•́)و ̑̑

* 🫣 Selon Jensen Huang (PDG de Nvidia), [l’IA surpassera les humains dans tous les domaines d’ici 5 ans](https://www.tomsguide.fr/lia-surpassera-les-humains-dans-tous-les-domaines-dici-5-ans-selon-le-pdg-de-nvidia/)
* **🛡️** Loco : [un framework Rust de type Ruby on Rails](https://www.programmez.com/actualites/loco-un-framework-rust-de-type-ruby-rails-36179)
* 🦀 [La Maison-Blanche exhorte les développeurs à abandonner C et C++ pour Rust](https://next.ink/brief_article/la-maison-blanche-exhorte-les-developpeurs-a-abandonner-c-et-c-pour-rust/)
*   🎱 [Les USA annoncent qu’un executive order à été signé pour le président pour interdire purement et simplement le transfert en masse de données personnelles sensibles des Américains vers un certain nombre d'états tiers](https://www.linkedin.com/posts/guillaume-champeau_fact-sheet-president-biden-issues-executive-activity-7168624241985196033-6PQv/). La mesure concerne les données biométriques, génomiques, de santé, de géolocalisation, financières ainsi que certaines données identifiantes.

    [Guillaume Champeau défriche l’impact pour les entreprises européennes sur Linkedin](https://www.linkedin.com/pulse/executive-order-interdisant-lacc%C3%A8s-%C3%A9tranger-%C3%A0-des-donn%C3%A9es-champeau-xh1de/?trackingId=RPPMGUkM9Y4PJeuuVpTbUg%3D%3D).
* **📟** Pour rappel, depuis le [RGPD](https://www.cnil.fr/fr/reglement-europeen-protection-donnees) et le principe de [security by default](https://www.wearenestor.com/blog/privacy-by-design-et-privacy-by-default), le fait d’utiliser SMTP / IMAP / FTP est obsolète depuis 2018. Ainsi pour éviter une [sanction de la CNIL](https://www.cnil.fr/fr/definition/sanction), on implémente directement SMTPS / IMAPS / SFTP ou FTPS. Pareil pour HTTP (si on a des données nominatives ou à protéger), on l’on privilégie (ou doit implémenter) HTTPS.
* **💻** [**security-misc**](https://github.com/Kicksecure/security-misc), une liste de l’équipe de [Kicksecure](https://www.kicksecure.com/) pour sécuriser Linux à tous les niveaux (noyau, bluetooth, réseau, protection des logins contre le brute-force, etc.)
* **📈** [**Pingora**](https://github.com/cloudflare/pingora), un proxy open-source développé par Cloudflare en Rust, conçu pour assurer une gestion plus efficace et fiable du trafic web
* **⏺️ Google Cloud** proposent plusieurs cours d’initiation gratuit à l’IA : [Introduction à l'IA générative](https://www.cloudskillsboost.google/course_templates/536), [Fondamentaux de l'IA générative](https://www.cloudskillsboost.google/course_templates/541), [Modèles de Langage à Grande Échelle (LLM)](https://www.cloudskillsboost.google/course_templates/539), [Architecture Encodeur-Décodeur](https://www.cloudskillsboost.google/course_templates/543), [Mécanisme d'Attention](https://www.cloudskillsboost.google/course_templates/537), [Reconnaissance d'image](https://www.cloudskillsboost.google/course_templates/542), [Introduction à Générative IA Studio](https://www.cloudskillsboost.google/course_templates/552)
* 🗞️ J’ai découvert récemment les PC portables [Tuxedo](https://www.tuxedocomputers.com/en/Linux-Hardware/Linux-Notebooks.tuxedo) chez mon précédent employeur. Ce mois-ci, j’ai découvert les [PC portables de ](https://frame.work/fr/fr)[**Framework.**](https://frame.work/fr/fr) La particularité est qu’il s’agit d’un ordinateur portable modulaire qui met l'accent sur la réparabilité, la capacité d'évolution et la personnalisation (ça me rapelle les vieux Thinkpad). Un peu comme [Fairphone](https://www.fairphone.com/fr/) pour les smartphones.
* 🧙‍♂️ Sébastien ([@sebi2706](https://twitter.com/sebi2706)) [nous présente ](https://www.youtube.com/watch?v=F-dodBIJ7is)[**Comnoco**](https://www.youtube.com/watch?v=F-dodBIJ7is), une [plateforme nocode pour construire vos backends](https://comnoco.com/)
* **💫** [**Grover**](https://github.com/Studiosity/grover), une gem Ruby/Rails permettant de transformer un fichier HTML en PDF, PNG ou JPEG
* 📧 A découvrir, la newsletter [**La veille des Ours**](https://www.linkedin.com/newsletters/la-veille-des-ours-7100088441966575616/) de l’entreprise Bearstech

***

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p><strong>Yvan Demumieux</strong> à réaliser <a href="https://www.linkedin.com/posts/yvan-demumieux_chatgpt-vs-ms-copilot-vs-claude-3-vs-gemini-activity-7172522179710926849-Iq-B/">un tableau comparatif complet en français des principaux Chatbots IA</a> (ChatGPT vs MS Copilot vs Claude 3 vs Gemini vs Mistral)</p></figcaption></figure>

***

### Logiciels ::

Nouveautés, découvertes… (☞ﾟヮﾟ)☞

* 🔴 **DocuSign** vient d'admettre qu'[il utilise les données de ses clients pour entraîner ses modèles d'IA](https://intelligence-artificielle.developpez.com/actu/354925/DocuSign-vient-d-admettre-qu-il-utilise-les-donnees-de-ses-clients-pour-entrainer-ses-modeles-d-IA-mais-offre-des-promesses-vagues-en-matiere-de-protection-de-la-vie-privee/)
* 🚂 [**GRAOU**](https://carto.graou.info/), la carte d'informations de ferroviaire français open-source de [Nicolas Wurtz](https://twitter.com/NicolasW_GRAOU) à subit [un gros lot de mise à jour](https://twitter.com/NicolasW_GRAOU/status/1766161994678177888) ! On peut cliquer sur les trains pour voir leurs arrêts, voir les signaux, les pancartes, les passages à niveau, etc.
* 🚗 [Le navigateur de la nouvelle Renault R5 E-Tech est… Vivaldi](https://www.clubic.com/actualite-520207-renault-r5-e-tech-pour-le-constructeur-francais-l-ecologie-passe-aussi-par-le-choix-d-un-navigateur-web.html) ! Un choix surprenant au premier abord, mais qui est aussi celui de Polestar, [Mercedes](https://www.clubic.com/vivaldi/actualite-477241-devinez-quel-navigateur-va-se-retrouver-dans-les-mercedes.html) et Audi.
* 🤖 [Microsoft met fin au ](https://next.ink/brief_article/microsoft-met-fin-au-sous-systeme-android-dans-windows-11/)[**sous-système Android dans Windows 11**](https://next.ink/brief_article/microsoft-met-fin-au-sous-systeme-android-dans-windows-11/)
* **🎮** [**Suyu**](https://suyu.dev/), le nouvel émulateur Switch open-source qui vient remplacer Yuzu (qui à déposer les armes face à Nintendo)
* **💻** [**Puter**](https://github.com/HeyPuter/puter), un OS dans votre navigateur
* **♻️** [**DAVx5**](https://www.davx5.com/), permets de synchroniser Google Contacts et Google Calendar sur Android sans passer par… Google :). En effet il synchronise via des protocoles ouverts (CalDav et CardDav)
* **📝** [**Ollama**](https://ollama.com/), un outil permettant de faire tourner en local différents modèles LLM.
* **🤔** [**Klap**](https://klap.app/), un outil qui vous délivre une vidéo au format vertical sur la base de n’importe quelle vidéo YouTube
* ⚰ [**Killed by Mozilla**](https://killedbymozilla.com/), un site qui liste les projets abandonnés par la fondation Mozilla
* 🔒 [Comment vérifier la sécurité du serveur de Linux avec ](https://itigic.com/how-to-check-linux-debian-server-security-with-debsecan/)[**Debsecan**](https://itigic.com/how-to-check-linux-debian-server-security-with-debsecan/)

***

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

***

### /Divers/

La rubrique gloubiboulga “ヽ(´▽｀)ノ”

* 🎧 [Une sélection de convertisseurs DAC portables pour garantir la qualité audio avec son smartphone](https://leclaireur.fnac.com/article/cp62441-ma-selection-de-convertisseurs-dac-portables-pour-garantir-la-qualite-audio-avec-son-smartphone/)
* 📰 [IFT: la filiale fibre d’Iliad-Free va lancer une offre dédiée aux opérateurs tiers et ouvre ses infrastructures](https://www.universfreebox.com/article/562674/fibre-la-filiale-fibre-diliad-free-va-lancer-une-offre-dediee-aux-operateurs-tiers-et-ouvre-ses-infrastructures)
* 🎥 Transformer son iPhone en caméra thermique ? C’est possible depuis plusieurs années déjà [avec de petits accessoires faciles à utiliser comme ](https://www.mac4ever.com/iphone/180329-test-de-la-camera-thermique-pour-iphone-topdon-isolation-points-chaud-animaux)[**celui de Topdon**](https://www.mac4ever.com/iphone/180329-test-de-la-camera-thermique-pour-iphone-topdon-isolation-points-chaud-animaux)
* 🥓 [Mieux comprendre l'économie grâce aux buffets à volonté](https://media.snowball.xyz/p/learn-a-corriger-buffet-a-volonte)
* ⌨ [Votre clavier peut vous trahir, l’écouter révélerait vos mots de passe](https://www.tomshardware.fr/votre-clavier-peut-vous-trahir-lecouter-revelerait-vos-mots-de-passe/)
* 🚩 [Le carré coloré du tube ne fournit pas d’indication sur la composition du dentifrice. Il facilite juste son repérage sur la chaîne de production](https://www.60millions-mag.com/2019/03/18/:~:text=Selon%20cette%20publication,%20le%20carr%C3%83%C2%A9,un%20%C3%82%C2%AB%20pur%20produit%20chimique%20%C3%82%C2%BB.)
* 👮‍♂️ La corruption de "basse intensité" : [comment des agents du service public cèdent aux sirènes de l'argent](https://www.francetvinfo.fr/replay-radio/le-choix-franceinfo/enquete-la-corruption-de-basse-intensite-comment-des-agents-du-service-public-cedent-aux-sirenes-de-l-argent_6146604.html)
* 🎵 [Mark Knopfler réunit plus de 60 musiciens pour single caritatif "Going Home"](https://www.francetvinfo.fr/culture/musique/rock/mark-knopfler-reunit-plus-de-60-musiciens-sur-un-seul-morceau_6425878.html), et que des stars
* 👶 Baisse de la fécondité : [D’ici à 2100, la plupart des pays verront leur population décliner](https://www.20minutes.fr/monde/4082440-20240321-baisse-fertilite-2100-plupart-pays-verront-population-decliner)
* ⚒ Très bon outil, [l’attache / fixation d'échelle pour galerie](https://eshop.wurth.fr/Categories-produits/Attache-echelle-RHSC-pour-galerie-d-utilitaires/31075601160201.cyid/3107.cgid/fr/FR/EUR/) de véhicule utilitaire
* 🎙 Deux albums et une chaîne YouTube à succès : à tout juste 22 ans, [**Feldup**](https://twitter.com/afpfr/status/1767506253545103470)[ est l'un des créateurs de contenu français les plus atypiques](https://twitter.com/afpfr/status/1767506253545103470), avec ses vidéos décortiquant les mystères d'internet.
* **🛡️** Les cybercriminels [volent des scans faciaux des utilisateurs d'iOS pour percer dans des comptes bancaires mobiles](https://www.theregister.com/2024/02/15/cybercriminals_stealing_face_id/)

***

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

***

### ← Replay →

Mes coups de cœur audio, vidéo, lectures du moment etc. ◖ᵔᴥᵔ◗ ♪ ♫

* 📺 [Ferrari](https://www.primevideo.com/-/fr/detail/0NHX4JGY462Z5A83KMBJA5LAS4/), [American Fiction](https://www.primevideo.com/detail/American-Fiction/0KEURR6UABMOJSC008Z54AUHYP) (Prime Video) | [Sly](https://www.netflix.com/fr/title/81450717) (Netflix) | [Shōgun](https://www.disneyplus.com/fr-fr/series/shogun/77sCbAqhMU5H) (Disney+)
* 📺 [**Last Week Tonight with John Oliver (HBO)**](https://www.youtube.com/@LastWeekTonight) : [Boeing](https://www.youtube.com/watch?v=Q8oCilY4szc) | [Elon Musk](https://www.youtube.com/watch?v=Eo3zORUGCbM) | [Chocolate](https://youtu.be/FwHMDjc7qJ8?si=x1q43oBdfZSKGsSi) | [McKinsey](https://youtu.be/AiOUojVd6xQ?si=xtH-NgOuoCbZp0Vo) | [Data Brokers](https://youtu.be/wqn3gR1WTcA?si=6y8O9-96qr1hNGUX). J’en profite pour signaler que l’intégralité des émissions est maintenant disponible légalement sur YouTube (plus de 300 épisodes depuis le début de l’émission, soit 10 années)
* 🎙 [**La Story**](https://www.lesechos.fr/podcasts/la-story) (Les Echos) : [échange avec Catherine Faye & Marine Sanclemente](https://shows.acast.com/07b210dd-7af5-5b41-b04d-e4eb2a19e708/episodes/65e8969f43c1bc0016f8e3a8?) (autrices du livre “[À la vie à la mort](https://www.editionspaulsen.com/demarches/674-a-la-vie-a-la-mort-sur-la-route-avec-thelma-et-louise.html)” aux éditions Paulsen) | [Montagne : le défi du manque de neige](https://shows.acast.com/la-story/episodes/montagne-le-defi-du-manque-de-neige) | [Fermob, le roi du jardin en couleur](https://shows.acast.com/la-story/episodes/fermob-le-roi-du-jardin-en-couleur)
* 🎙 [**La Réu d’écran Large**](https://www.ecranlarge.com/films/news/1482082-le-podcast-decran-large-tous-les-episodes-de-la-reu-decran-large) : Ryan Gosling ([1/2](https://shows.acast.com/644a8a32adac0f00105359d5/64f86ec8ab11cf001133a1b5) et [2/2](https://shows.acast.com/644a8a32adac0f00105359d5/6501c4d2b5dece00112fd1d1)), Jennifer Lawrence ([1/2](https://shows.acast.com/644a8a32adac0f00105359d5/65c62f3c2f12a6001678b7ff) et [2/2](https://shows.acast.com/644a8a32adac0f00105359d5/65cb6c49a180570018ecd91c)), Denis Villeneuve ([1/3](https://shows.acast.com/644a8a32adac0f00105359d5/65deff7dacbfff00161e2eda), [2/3](https://shows.acast.com/644a8a32adac0f00105359d5/65df5c99d34c360016e6446f) et [3/3](https://shows.acast.com/644a8a32adac0f00105359d5/65e5af805c669900174ff882))
* 📻 [**L’inconscient**](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient) (France Inter) : [À quoi sert de parler à un enfant ?](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient/l-inconscient-du-dimanche-12-mars-2023-2977664) | [Sommes-nous responsables de nos rêves ?](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient/l-inconscient-du-dimanche-24-septembre-2023-9578022) | [Qui choisit pour moi ? Comment l'inconscient influence nos décisions](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient/l-inconscient-du-dimanche-15-octobre-2023-8245598) | [L’Hypnose : miracle, arnaque ou thérapie](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient/l-inconscient-du-dimanche-24-mars-2024-1622867) ? | [Laïcité et spiritualité en psychanalyse](https://www.radiofrance.fr/franceinter/podcasts/l-inconscient/l-inconscient-du-dimanche-31-mars-2024-7915851)
* 📻 [**Le Temps du débat**](https://www.radiofrance.fr/franceculture/podcasts/le-temps-du-debat) (France Culture) : [Ukraine-Russie : quelle est l'importance réelle de la cyberguerre ?](https://www.radiofrance.fr/franceculture/podcasts/le-temps-du-debat/ukraine-russie-quelle-est-l-importance-reelle-de-la-cyberguerre-5086081) | [Médias : comment se construit le pluralisme ?](https://www.radiofrance.fr/franceculture/podcasts/le-temps-du-debat/medias-comment-se-construit-le-pluralisme-3807859)
* 🎙 [**Comprendre le monde**](https://www.youtube.com/channel/UC4VOE8jQPWUPp4PpNK8zhIg) (Pascal Boniface) : [A quoi sert la diplomatie ? Avec Hubert Védrine](https://www.youtube.com/watch?v=okkmNq3P8JI) | [Géopolotique des océans. Avec Julia Tasse](https://www.youtube.com/watch?v=5Y94iHmWsrg)
* 🎙 [**Defcast**](https://www.defense.gouv.fr/defcast-podcast-au-coeur-armees) : [Général Aymeric Bonnemaison, commandant de la cyberdéfense](https://www.podcastics.com/podcast/episode/general-aymeric-bonnemaison-commandant-de-la-cyberdefense-238563/) | [Adjudant-chef Sébastien, membre du groupe militaire de haute montagne](https://www.podcastics.com/podcast/episode/adjudant-chef-sebastien-membre-du-groupe-militaire-de-haute-montagne-235349/) | [Ingénieur général de l’armement Patrick Aufort, directeur de l’Agence de l’innovation de défense](https://www.podcastics.com/podcast/episode/ingenieur-general-de-larmement-patrick-aufort-directeur-de-lagence-de-linnovation-de-defense-261698/)
* 📖 [**La face cachée d'Internet**](https://www.editions-larousse.fr/livre/la-face-cachee-dinternet-poche-9782035960610) de [Rayna Stamboliyska](https://www.twitter.com/MaliciaRogue) aux éditions Larousse
