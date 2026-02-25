---
description: Une liste de commandes utiles
icon: rectangle-terminal
---

# Powershell

## PowerShell vs PowerShell ISE

**PowerShell ISE** offre **une interface graphiqu**e et des outils supplémentaires pour le développement de scripts, contrairement à la version standard de PowerShell qui utilise une **interface en ligne de commande**

***

## Connaître votre version

Pour identifier la version sur votre session PowerShell :

```powershell
$PSVersionTable # Afficher la version de PowerShell
```

***

## Cheatsheet <a href="#information-systeme" id="information-systeme"></a>

### Informations systèmes

```powershell
Get-ComputerInfo                    # Afficher les informations systèmes (version de windows, édition, bios version, etc)
Get-WMIObject Win32_OperatingSystem # Afficher la version de Windows
$env:COMPUTERNAME                   # Afficher le nom de l'ordinateur
```

### Services et processus <a href="#services-et-processus" id="services-et-processus"></a>

{% code fullWidth="true" %}
```powershell
# Service
Get-Service            # Lister tous les services [Alias: gsv]
Get-Service name       # Avoir des détails sur un service spécifique [Alias: gsv]
Start-Service name     # Démarrer un service à l'arrêt [Alias: sasv]
Stop-Service name      # Arrêter un service en cours [Alias: spsv]
Restart-Service name   # Redémarrer un service en cours

# Process
Get-Process            # Lister tous les processes [Alias: ps]
Get-Process name       # Avoir des détails sur un process spécifique [Alias: ps]
Start-Process name     # Démarrer un process à l'arrêt [Alias: start, saps]
Stop-Process name      # Stop a process [Alias: kill, spps]
Wait-Process name      # Attendre qu'un process ce stop avant de continuer
Debug-Process name     # Attacher un debugger à un process
```
{% endcode %}

### Réseau <a href="#reseau" id="reseau"></a>

<pre class="language-powershell" data-full-width="true"><code class="lang-powershell">Get-NetIPConfiguration                 # Afficher l'interface locale et les IPs assignés
<strong>netsh wlan show profiles               # Afficher la liste des réseau sans fil enregistrés
</strong>Test-Connection name                   # Ping basique
Test-NetConnection name                # Ping avancée
Test-NetConnection name -TraceRoute    # Perform a trace route
Test-NetConnection name -Port port     # Perform a port check
Test-NetConnection google.com -Port 80 # Testez la connectivité du port TCP
Get-NetTCPConnection                   # Affiche la liste des connexions TCP
Get-NetUDPEndpoint                     # Affiche la liste des connexions UDP

# DNS
Set-DnsClientServerAddress -InterfaceAlias interface -ServerAddresses dns,dns2 # Changer les serveurs DNS
Resolve-DnsName name                  # Basique DNS lookup
Resolve-DnsName name -Type recordtype # DNS lookup pour un record spécifique (ie txt, srv, soa, etc)
Clear-DnsClientCache                  # Effacer le cache local DNS
</code></pre>

### Contrôle à distance <a href="#controle-a-distance" id="controle-a-distance"></a>

{% code fullWidth="true" %}
```powershell
Enable-PSRemoting                                 # Activer la possibilitée des sessions PowerShell distantes sur la machine locale 
Enter-PSSession computername -Credential username # Connexion à un ordinateur distant
```
{% endcode %}

### Gestion du système <a href="#gestion-du-systeme" id="gestion-du-systeme"></a>

{% code fullWidth="true" %}
```powershell
start-Computer      # Redémarrer la machine
Stop-Computer       # Eteindre la machine
Checkpoint-Computer # Créer un point de restauration a system restore point
Restore-Computer    # Restaurer l'ordinateur à un point de restauration
```
{% endcode %}

### Gestion des fichiers <a href="#gestion-des-fichiers" id="gestion-des-fichiers"></a>

#### Création <a href="#creation" id="creation"></a>

* Obtenir son répertoire actuel : `Get-Location` (ou l'alias `pwd` connu sous Linux)
* Lister le contenu d'un répertoire : `Get-ChildItem` (ou l'alias `ls` ou `dir`)
* Créer un nouveau répertoire ou fichier :

{% code fullWidth="true" %}
```powershell
New-Item -Name "Nom_Rep" -ItemType Directory                     # Créer une répertoire
New-Item -Name "nom_fichier.ext" -ItemType File.                 # Créer un fichier 
New-Item -Name "nom_fichier.ext" -ItemType File -Value "Contenu" # Créer un fichier avec du contenu
```
{% endcode %}

***

## 100 Aide-mémoire de commandes Windows

#### SYSTEM INFO & ENUMERATION (1–15)

1. **`whoami`** → Affiche l'utilisateur actuellement connecté.
2. **`hostname`** → Affiche le nom de l'ordinateur.
3. **`systeminfo`** → Informations complètes sur l'OS, les correctifs et le matériel.
4. **`ver`** → Version de Windows.
5. **`set`** → Affiche les variables d'environnement.
6. **`echo %username%`** → Affiche le nom d'utilisateur.
7. **`date /t`** → Affiche la date.
8. **`time /t`** → Affiche l'heure.
9. **`driverquery`** → Liste les pilotes installés.
10. **`tasklist`** → Processus en cours d'exécution.
11. **`tasklist /svc`** → Processus avec services associés.
12. **`wmic os get caption`** → Nom du système d'exploitation.
13. **`wmic cpu get name`** → Informations sur le processeur.
14. **`wmic bios get serialnumber`** → Numéro de série du BIOS.
15. **`wmic qfe`** → Correctifs installés.

#### USER & ACCOUNT ENUMERATION (16–25)

1. **`net user`** → Liste tous les utilisateurs.
2. **`net user <user>`** → Détails d'un utilisateur spécifique.
3. **`net localgroup`** → Liste les groupes.
4. **`net localgroup administrators`** → Utilisateurs administrateurs.
5. **`whoami /groups`** → Appartenance aux groupes de l'utilisateur.
6. **`whoami /priv`** → Privilèges de l'utilisateur.
7. **`query user`** → Utilisateurs connectés.
8. **`net accounts`** → Politique de mot de passe.
9. **`net user <user> /active:no`** → Désactive un utilisateur.
10. **`net user <user> *`** → Change le mot de passe.

#### NETWORK ENUMERATION (26–45)

1. **`ipconfig`** → Informations IP.
2. **`ipconfig /all`** → Configuration réseau complète.
3. **`ipconfig /displaydns`** → Cache DNS.
4. **`ipconfig /flushdns`** → Efface le cache DNS.
5. **`getmac`** → Adresse MAC.
6. **`arp -a`** → Table ARP.
7. **`route print`** → Table de routage.
8. **`netstat -an`** → Ports ouverts.
9. **`netstat -ano`** → Ports + PID.
10. **`netstat -b`** → Processus utilisant le port (admin).
11. **`ping <host>`** → Teste la connectivité.
12. **`tracert <host>`** → Trace la route.
13. **`pathping <host>`** → Ping + perte de route.
14. **`nslookup <domain>`** → Recherche DNS.
15. **`net view`** → Partages réseau.
16. **`net view \\target`** → Partages d'une cible spécifique.
17. **`nbtstat -n`** → Noms NetBIOS.
18. **`nbtstat -A <ip>`** → Informations NetBIOS distantes.
19. **`net use`** → Affiche les lecteurs mappés.
20. **`net use \\ip\share`** → Connecte un partage.

#### FILE & DIRECTORY OPERATIONS (46–60)

1. **`dir`** → Liste les fichiers.
2. **`dir /a`** → Affiche les fichiers cachés.
3. **`tree`** → Arborescence des répertoires.
4. **`cd`** → Change de répertoire.
5. **`mkdir`** → Crée un dossier.
6. **`rmdir`** → Supprime un dossier.
7. **`del`** → Supprime un fichier.
8. **`copy`** → Copie un fichier.
9. **`move`** → Déplace un fichier.
10. **`rename`** → Renomme un fichier.
11. **`type file.txt`** → Lit un fichier.
12. **`more file.txt`** → Lit page par page.
13. **`attrib`** → Attributs de fichier.
14. **`attrib +h file`** → Cache un fichier.
15. **`where file.exe`** → Trouve le chemin d'un fichier.

#### SEARCH & FORENSICS (61–70)

1. **`find "text" file.txt`** → Recherche une chaîne de caractères.
2. **`findstr "text" file.txt`** → Recherche avancée.
3. **`findstr /s /i password *.*`** → Recherche récursivement.
4. **`fc file1 file2`** → Compare des fichiers.
5. **`certutil -hashfile file sha256`** → Hash du fichier.
6. **`cipher /c file`** → Vérifie le chiffrement.
7. **`cipher /w:c`** → Efface l'espace supprimé.
8. **`compact`** → Vérifie la compression.
9. **`forfiles`** → Trouve des fichiers par date.
10. **`dir /s filename`** → Recherche un fichier.

#### PROCESS & SERVICE CONTROL (71–80)

1. **`tasklist`** → Liste les processus.
2. **`taskkill /PID 1234`** → Arrête un processus par PID.
3. **`taskkill /IM proc.exe /F`** → Force l'arrêt d'un processus.
4. **`sc query`** → Liste les services.
5. **`sc query state= all`** → Tous les services.
6. **`sc stop service`** → Arrête un service.
7. **`sc start service`** → Démarre un service.
8. **`net start`** → Services en cours d'exécution.
9. **`net stop service`** → Arrête un service.
10. **`wmic process list brief`** → Liste des processus.

#### SECURITY & PERMISSIONS (81–90)

1. **`icacls file`** → Affiche les permissions.
2. **`icacls file /grant user:F`** → Accorde l'accès complet.
3. **`takeown /f file`** → Prend la propriété.
4. **`auditpol /get /category:*`** → Politique d'audit.
5. **`secedit /export`** → Politique de sécurité.
6. **`gpresult /r`** → Résultat de la stratégie de groupe.
7. **`gpupdate /force`** → Met à jour les GPO.
8. **`logoff`** → Déconnecte l'utilisateur.
9. **`shutdown /s /t 0`** → Arrêt du système.
10. **`shutdown /r /t 0`** → Redémarrage.

#### DISK & SYSTEM UTILITIES (91–100)

1. **`chkdsk`** → Vérification du disque.
2. **`diskpart`** → Gestionnaire de disque.
3. **`sfc /scannow`** → Vérification des fichiers système.
4. **`dism /online /cleanup-image /restorehealth`** → Réparation de Windows.
5. **`mountvol`** → Points de montage de volumes.
6. **`fsutil fsinfo drives`** → Liste les lecteurs.
7. **`fsutil file createnew file 1000`** → Crée un fichier.
8. **`powercfg /a`** → Modes d'alimentation.
9. **`wevtutil qe System`** → Lit les journaux d'événements.
10. **`eventvwr`** → Ouvre l'observateur d'événements.
