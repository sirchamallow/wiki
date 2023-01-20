---
description: .m3u rules !
---

# 💡 Créer une playlist de webradios

L'idée pour démarrer est de repérer les radios qu'on aime bien, et s'en constituer soi-même une liste qu'on pourra écouter avec le lecteur audio de notre choix.

Il est en fait assez simple d'externaliser des listes de radio dans des fichiers playlists portant l'extension .m3u . Cela permet ensuite de les écouter avec tout lecteur capable de lire un flux en streaming, c'est à dire la plupart (VLC, foobar2000…).

## Trouver les radios <a href="#trouver_les_radios" id="trouver_les_radios"></a>

{% hint style="info" %}
Chaque webradio émet un flux, dont nous chercherons à connaître l'adresse.
{% endhint %}

Qu'il s'agisse de radios ou webradios, certains sites recensent les adresses des flux. Il en existe des millers. Je ne vais en retenir un qui existe depuis très longtemps : [**Radio-Browser**](https://www.radio-browser.info/), et qui corrige très rapidement quand il y a une erreur de flux dans la liste.

### Liste par pays <a href="#quelles_radios" id="quelles_radios"></a>

```html
https://www.radio-browser.info/countries
```

### Liste par langues <a href="#quelles_radios" id="quelles_radios"></a>

```html
https://www.radio-browser.info/languages
```

### Liste par styles <a href="#quelles_radios" id="quelles_radios"></a>

```html
https://www.radio-browser.info/tags
```

Une fois identifer les radios qui vous intéressent, mettez de côté chaque flux (URL) en effectuant un copier-coller dans un bloc-notes.

Voici un exemple de liste :&#x20;

```
http://direct.franceinfo.fr/live/franceinfo-midfi.mp3     # France Info
http://icecast.radiofrance.fr/franceculture-hifi.aac      # France Culture
http://icecast.radiofrance.fr/fip-hifi.aac                # FIP
https://radios.rtbf.be/classic21-128.mp3                  # Classic 21
http://stream.srg-ssr.ch/m/couleur3/mp3_128               # Couleur 3
http://radiomeuh.ice.infomaniak.ch/radiomeuh-128.mp3      # RadioMeuh
http://cdn.nrjaudio.fm/adwz1/fr/30607/mp3_128.mp3         # Nostalgie Funk
https://icecast.radiofrance.fr/fippop-hifi.aac            # FIP Pop
http://stream.srg-ssr.ch/m/rsp/mp3_128                    # Radio Swiss Pop
http://icecast.radiofrance.fr/fipjazz-hifi.aac            # FIP Jazz
http://tsfjazz.ice.infomaniak.ch/tsfjazz-high             # TSF Jazz
http://stream.srg-ssr.ch/m/rsj/mp3_128                    # Radio Swiss Jazz
```

## Créer la playlist .m3u <a href="#creer_la_playlist_m3u" id="creer_la_playlist_m3u"></a>

Pour faire une playlist, il faut respecter un formattage.\
\
Pour cela il suffit de faire précéder chaque adresse de flux par une ligne:

<pre><code><strong>#EXTINF:0,Nom De La Radio
</strong></code></pre>

Ce qui donnera:

```
#EXTINF:0,1. France Info
http://direct.franceinfo.fr/live/franceinfo-midfi.mp3
#EXTINF:0,2. France Culture
http://icecast.radiofrance.fr/franceculture-hifi.aac
#EXTINF:0,3. FIP
http://icecast.radiofrance.fr/fip-hifi.aac
#EXTINF:0,4. Classic 21
https://radios.rtbf.be/classic21-128.mp3
#EXTINF:0,5. Couleur 3
http://stream.srg-ssr.ch/m/couleur3/mp3_128
#EXTINF:0,6. RadioMeuh
http://radiomeuh.ice.infomaniak.ch/radiomeuh-128.mp3
#EXTINF:0,7. Nostalgie Funk
http://cdn.nrjaudio.fm/adwz1/fr/30607/mp3_128.mp3
#EXTINF:0,8. FIP Pop
https://icecast.radiofrance.fr/fippop-hifi.aac
#EXTINF:0,9. Radio Swiss Pop
http://stream.srg-ssr.ch/m/rsp/mp3_128
#EXTINF:0,10. FIP Jazz
http://icecast.radiofrance.fr/fipjazz-hifi.aac
#EXTINF:0,11. TSF Jazz
http://tsfjazz.ice.infomaniak.ch/tsfjazz-high
#EXTINF:0,12. Radio Swiss Jazz
http://stream.srg-ssr.ch/m/rsj/mp3_128
```

En tête du document, on ajoutera la mention :

```
#EXTM3U
```

Ce qui donne :

```
#EXTM3U
#EXTINF:0,1. France Info
http://direct.franceinfo.fr/live/franceinfo-midfi.mp3
#EXTINF:0,2. France Culture
http://icecast.radiofrance.fr/franceculture-hifi.aac
#EXTINF:0,3. FIP
http://icecast.radiofrance.fr/fip-hifi.aac
#EXTINF:0,4. Classic 21
https://radios.rtbf.be/classic21-128.mp3
#EXTINF:0,5. Couleur 3
http://stream.srg-ssr.ch/m/couleur3/mp3_128
#EXTINF:0,6. RadioMeuh
http://radiomeuh.ice.infomaniak.ch/radiomeuh-128.mp3
#EXTINF:0,7. Nostalgie Funk
http://cdn.nrjaudio.fm/adwz1/fr/30607/mp3_128.mp3
#EXTINF:0,8. FIP Pop
https://icecast.radiofrance.fr/fippop-hifi.aac
#EXTINF:0,9. Radio Swiss Pop
http://stream.srg-ssr.ch/m/rsp/mp3_128
#EXTINF:0,10. FIP Jazz
http://icecast.radiofrance.fr/fipjazz-hifi.aac
#EXTINF:0,11. TSF Jazz
http://tsfjazz.ice.infomaniak.ch/tsfjazz-high
#EXTINF:0,12. Radio Swiss Jazz
http://stream.srg-ssr.ch/m/rsj/mp3_128
```

{% hint style="success" %}
Et c'est terminé, il suffit d'enregistrer votre fichier en lui faisant prendre pour extension: **.m3u** :)
{% endhint %}
