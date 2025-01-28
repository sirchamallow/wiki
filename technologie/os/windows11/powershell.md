---
description: Une liste de commandes utiles
icon: rectangle-terminal
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

# Powershell

## PowerShell vs PowerShell ISE

**PowerShell ISE** offre **une interface graphiqu**e et des outils supplémentaires pour le développement de scripts, contrairement à la version standard de PowerShell qui utilise une **interface en ligne de commande**

## Connaître votre version

Pour identifier la version sur votre session PowerShell :

```powershell
$PSVersionTable # Afficher la version de PowerShell
```

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

