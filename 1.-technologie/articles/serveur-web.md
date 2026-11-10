---
description: PAGE NON FINALISEE // DRAFT
---

# Serveur WEB

Dans ce comparatif, **Nginx** sert de référence, face à **Caddy**, **HAProxy**, **Apache httpd** et **Traefik**. Les cinq couvrent le reverse proxy, mais avec des philosophies très différentes : **Nginx** mise sur l’équilibre performance/polyvalence, **Caddy** sur la simplicité, **HAProxy** sur le proxy pur et le load balancing, **Apache** sur la modularité historique, et **Traefik** sur les environnements Docker/Kubernetes.

### Vue d’ensemble

Certains sont réellement des **serveurs web**, tandis que d’autres sont avant tout des **proxys**.

| Logiciel     | Serveur Web | Reverse proxy   | Load balancer |
| ------------ | ----------- | --------------- | ------------- |
| Nginx        | ✅           | ✅               | ✅             |
| Apache httpd | ✅           | ✅               | ✅             |
| Caddy        | ✅           | ✅               | ✅             |
| HAProxy      | ❌           | ✅               | ✅             |
| Traefik      | ❌\*         | ✅               | ✅             |
| Envoy        | ❌           | ✅               | ✅             |
| Varnish      | ❌           | ✅               | ❌             |
| Squid        | ❌           | ✅/Forward proxy | ❌             |

\*Traefik peut fournir quelques contenus/réponses, mais ce n'est pas un serveur web généraliste comme Nginx, Caddy ou Apache.

* **Nginx** est un serveur web, reverse proxy, cache HTTP, load balancer et proxy TCP/UDP. Il reste un choix très solide quand on veut un composant central polyvalent. ([nginx.org](https://nginx.org/en/))
* **Caddy** vise surtout l’efficacité opérationnelle : son gros avantage est l’**HTTPS automatique par défaut**, avec émission et renouvellement des certificats intégrés. ([caddyserver.com](https://caddyserver.com/docs/automatic-https))
* **HAProxy** est centré sur la **répartition de charge** et le **proxy haute performance**, avec modes **L4 (TCP)** et **L7 (HTTP)**. C’est souvent le meilleur choix quand le proxy est le cœur du système. ([haproxy.org](https://www.haproxy.org/download/1.3/doc/configuration.txt))
* **Apache httpd** reste très flexible grâce à ses modules. Avec `mod_proxy` et ses extensions, il peut faire reverse proxy et load balancing, mais sa configuration est généralement plus fragmentée que celle de Caddy ou Nginx. ([httpd.apache.org](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html))
* **Traefik** est pensé pour les environnements **dynamiques**. Il découvre automatiquement les services via des providers comme **Docker** ou **Kubernetes**, et génère son routage à partir de labels, annotations ou ressources dédiées. ([doc.traefik.io](https://doc.traefik.io/traefik/reference/install-configuration/providers/overview/))

### **Raccourci pratique**

* usage classique VPS / sites web → **Caddy**
* forte charge / proxy pur → **HAProxy**
* stack traditionnelle / compatibilité large → **Nginx; Apache**
* containers / cloud-native → **Traefik** ([caddyserver.com](https://caddyserver.com/docs/))

***

Ces trois rôles se ressemblent parce qu'ils manipulent tous des requêtes HTTP/HTTPS, mais **la question clé est : qui produit réellement la réponse ?**



## Serveur web, reverse proxy et load balancer : comprendre la différence

Ces trois rôles se ressemblent parce qu'ils manipulent tous des requêtes HTTP/HTTPS, mais **la question clé est : qui produit réellement la réponse ?**

### 1. Serveur web : « Je possède le contenu »

Prenons un serveur avec Nginx et les fichiers suivants :

```
/var/www/monsite/
├── index.html
├── style.css
└── logo.png
```

Lorsque ton navigateur demande :

```
GET https://www.monsite.fr/index.html
```

Nginx cherche directement `index.html` sur son disque et le renvoie au navigateur.

```
Navigateur
    │
    │ GET /index.html
    ▼
  Nginx
    │
    │ lit /var/www/monsite/index.html
    ▼
 Disque
    │
    ▼
 index.html
    │
    └──────────────► Navigateur
```

Ici, **Nginx est le serveur web** : c'est lui qui possède et fournit la ressource.

C'est particulièrement adapté aux contenus **statiques** :

* HTML
* CSS
* JavaScript
* images
* fichiers à télécharger

#### Exemple

Tu demandes :

```
https://www.exemple.fr/logo.png
```

Nginx peut simplement répondre :

```
HTTP/1.1 200 OK
Content-Type: image/png

[données de l'image]
```

Il n'a besoin d'aucun autre serveur.

***

### 2. Reverse proxy : « Je ne possède pas forcément le contenu, je sais à qui demander »

Supposons maintenant que tu installes **Grafana** sur un serveur.

Grafana écoute localement sur :

```
http://127.0.0.1:3000
```

Mais tu ne veux pas que les utilisateurs saisissent :

```
http://serveur:3000
```

Tu veux :

```
https://grafana.exemple.fr
```

Tu places alors Nginx devant :

```
Utilisateur
    │
    │ https://grafana.exemple.fr
    │ port 443
    ▼
  Nginx
    │
    │ http://127.0.0.1:3000
    ▼
 Grafana
```

Cette fois :

1. le navigateur contacte Nginx ;
2. Nginx reçoit la requête ;
3. Nginx voit qu'elle concerne `grafana.exemple.fr` ;
4. il transmet la requête à Grafana ;
5. Grafana génère la réponse ;
6. Grafana répond à Nginx ;
7. Nginx renvoie la réponse au navigateur.

Donc :

```
Navigateur → Nginx → Grafana
Navigateur ← Nginx ← Grafana
```

**Nginx est ici le reverse proxy.**

***

#### Pourquoi mettre un intermédiaire ?

À première vue, tu pourrais te dire :

> Pourquoi ne pas simplement exposer Grafana directement sur Internet ?

C'est possible, mais le reverse proxy apporte beaucoup de choses.

#### A. Une seule adresse HTTPS standard

Tes applications peuvent utiliser différents ports en interne :

```
Grafana       → :3000
Nextcloud     → :8080
Application   → :5000
API           → :9000
```

Alors que depuis Internet, tout arrive en HTTPS sur le port `443` :

```
grafana.exemple.fr   ─┐
nextcloud.exemple.fr ─┼──► Nginx :443
app.exemple.fr       ─┘
```

Nginx regarde le nom demandé et choisit la destination.

Par exemple :

```
grafana.exemple.fr
        ↓
Nginx
        ↓
127.0.0.1:3000
```

et :

```
nextcloud.exemple.fr
        ↓
Nginx
        ↓
192.168.10.20:8080
```

***

#### B. Centraliser HTTPS

C'est également très intéressant pour TLS.

On peut avoir :

```
Internet
   │
   │ HTTPS
   │ TLS
   ▼
Reverse Proxy
   │
   │ HTTP ou HTTPS
   ▼
Application
```

Le reverse proxy peut gérer :

* les certificats TLS ;
* leur renouvellement ;
* les versions TLS autorisées ;
* les cipher suites ;
* HSTS ;
* les redirections HTTP → HTTPS.

On parle souvent de **TLS termination**.

C'est notamment une des forces de **Caddy**, qui automatise fortement la gestion HTTPS.

***

#### C. Cacher l'infrastructure interne

L'utilisateur voit simplement :

```
https://grafana.exemple.fr
```

Il n'a pas besoin de connaître :

```
192.168.50.26:3000
```

La topologie interne peut donc évoluer sans modifier l'adresse utilisée par les utilisateurs.

***

### 3. Load balancer : « J'ai plusieurs serveurs possibles, lequel choisir ? »

Le load balancer introduit une nouvelle problématique.

Imaginons que ton application devienne très utilisée.

Un seul serveur ne suffit plus.

Tu en déploies trois :

```
WEB01
WEB02
WEB03
```

Ils fournissent tous la même application.

Tu places HAProxy devant :

```
                    ┌──► WEB01
                    │
Internet ──► HAProxy├──► WEB02
                    │
                    └──► WEB03
```

HAProxy reçoit par exemple :

```
GET /application
```

Puis décide :

> Cette requête partira sur WEB02.

La suivante pourra aller vers WEB03.

***

### 4. Comment choisit-il le serveur ?

Plusieurs algorithmes existent.

#### Round Robin

Le plus facile à comprendre :

```
requête 1 → WEB01
requête 2 → WEB02
requête 3 → WEB03
requête 4 → WEB01
requête 5 → WEB02
...
```

On tourne entre les serveurs.

#### Least Connections

Le load balancer regarde quel serveur a actuellement le moins de connexions.

Par exemple :

```
WEB01 → 120 connexions
WEB02 → 45 connexions
WEB03 → 90 connexions
```

Il pourra favoriser :

```
WEB02
```

Cela peut être intéressant lorsque certaines requêtes durent beaucoup plus longtemps que d'autres.

***

### 5. Le load balancer vérifie aussi si les serveurs fonctionnent

C'est là que cela devient très intéressant pour un sysadmin.

Supposons :

```
WEB01 → OK
WEB02 → OK
WEB03 → HS
```

HAProxy peut effectuer régulièrement des **health checks**.

Si WEB03 ne répond plus :

```
                    ┌──► WEB01 ✅
Internet ──► HAProxy├──► WEB02 ✅
                    └─X► WEB03 ❌
```

HAProxy cesse alors d'envoyer les nouvelles requêtes vers WEB03.

Quand le serveur redevient opérationnel, il peut être réintégré.

Le **load balancing ne sert donc pas uniquement aux performances**. Il participe également à la **haute disponibilité**.

***

### 6. Reverse proxy et load balancer sont donc très proches

C'est souvent ici que la confusion apparaît.

Un reverse proxy classique fait essentiellement :

```
Client
   ↓
Reverse Proxy
   ↓
Serveur A
```

Un load balancer fait :

```
Client
   ↓
Load Balancer
   ↓
   ├── Serveur A
   ├── Serveur B
   └── Serveur C
```

On peut considérer un load balancer HTTP comme **un reverse proxy capable de choisir entre plusieurs backends en fonction de règles ou d'algorithmes de répartition**.

C'est pourquoi Nginx peut faire **les deux**.

***

### 7. Et concrètement, Nginx, Caddy, HAProxy et Traefik ?

C'est là que les différences deviennent plus faciles à comprendre.

| Logiciel         | Sa spécialité                                          |
| ---------------- | ------------------------------------------------------ |
| **Apache httpd** | Servir des sites Web                                   |
| **Nginx**        | Serveur web + reverse proxy + load balancing           |
| **Caddy**        | Serveur web + reverse proxy avec HTTPS très automatisé |
| **HAProxy**      | Reverse proxy + load balancing                         |
| **Traefik**      | Reverse proxy + load balancing dynamique               |
| **Varnish**      | Reverse proxy + cache HTTP                             |
| **Squid**        | Surtout forward proxy + cache                          |

Cela explique pourquoi **Nginx et Caddy sont difficiles à mettre dans une seule case**. Ils peuvent changer complètement de rôle selon leur configuration.

***

### 8. Exemple réaliste complet

Imaginons une infrastructure avec :

* 2 serveurs Grafana ;
* 3 serveurs applicatifs ;
* plusieurs noms DNS ;
* une seule entrée HTTPS.

On pourrait avoir :

```
                       Internet
                           │
                       HTTPS :443
                           │
                           ▼
                    ┌─────────────┐
                    │   HAProxy   │
                    └──────┬──────┘
                           │
             ┌─────────────┴─────────────┐
             │                           │
     grafana.exemple.fr           app.exemple.fr
             │                           │
        ┌────┴────┐                ┌─────┼─────┐
        ▼         ▼                ▼     ▼     ▼
     Grafana1  Grafana2          APP1  APP2  APP3
```

HAProxy assure alors plusieurs fonctions :

#### Reverse proxy

Il sait que :

```
grafana.exemple.fr → serveurs Grafana
app.exemple.fr     → serveurs APP
```

#### Load balancer

Il sait que :

```
Grafana → Grafana1 ou Grafana2
APP     → APP1, APP2 ou APP3
```

#### TLS termination

Il peut gérer :

```
HTTPS → certificat → déchiffrement TLS
```

#### Health check

Il vérifie :

```
APP1 ✅
APP2 ✅
APP3 ❌
```

et n'envoie plus de trafic vers APP3.

***

### La notion fondamentale à retenir

Pose-toi simplement cette question :

**« Après avoir reçu la requête HTTP, que fait le logiciel ? »**

* Il **cherche le fichier et le renvoie lui-même** → **serveur web**
* Il **transmet la requête vers une application située derrière** → **reverse proxy**
* Il **choisit parmi plusieurs serveurs derrière** → **load balancer**

Et surtout, **un même logiciel peut cumuler plusieurs rôles**. Nginx peut très bien servir directement `/logo.png`, transmettre `/api/` vers une application et répartir `/app/` entre trois serveurs. C'est cette polyvalence qui explique une bonne partie de son succès.

