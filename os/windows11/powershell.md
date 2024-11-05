---
description: Une liste de commandes utiles
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

# ⌨️ Powershell

## Cheatsheet <a href="#information-systeme" id="information-systeme"></a>

### Informations systèmes

```powershell
Get-ComputerInfo                    # Afficher les informations systèmes (version de windows, édition, bios version, etc)
$PSVersionTable                     # Afficher la version de PowerShell
Get-WMIObject Win32_OperatingSystem # Afficher la version de Windows
$env:COMPUTERNAME                   # Afficher le nom de l'ordinateur
```

### Services et processus <a href="#services-et-processus" id="services-et-processus"></a>

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

### Réseau <a href="#reseau" id="reseau"></a>

```powershell
Get-NetIPConfiguration                # Afficher l'interface locale et les IPs assignés
Test-Connection name                  # Ping basique
Test-NetConnection name               # Ping avancée
Test-NetConnection name -TraceRoute   # Perform a trace route
Test-NetConnection name -Port port    # Perform a port check

# DNS
Set-DnsClientServerAddress -InterfaceAlias interface -ServerAddresses dns,dns2 # Changer les serveurs DNS
Resolve-DnsName name                  # Basique DNS lookup
Resolve-DnsName name -Type recordtype # DNS lookup pour un record spécifique (ie txt, srv, soa, etc)
Clear-DnsClientCache                  # Effacer le cache local DNS
```

### Contrôle à distance <a href="#controle-a-distance" id="controle-a-distance"></a>

```powershell
Enable-PSRemoting # Enable PowerShell remoting locally
Enter-PSSession computername -Credential username # Connect to a remote computer
Invoke-Command -ComputerName computername -ScriptBlock {commands to execute} -Credential username # Execute the script block contents on the remote computer
$SessionName = New-PSSession computername -Credential username # Store a persistent session in a variable which can be used with Enter-PSSession or Invoke-Command
```

### Gestion du système <a href="#gestion-du-systeme" id="gestion-du-systeme"></a>

```powershell
start-Computer      # Redémarrer la machine
Stop-Computer       # Eteindre la machine
Checkpoint-Computer # Créer un point de restauration a system restore point
Restore-Computer    # Restaurer l'ordinateur à un point de restauration
```

### Gestion des fichiers <a href="#gestion-des-fichiers" id="gestion-des-fichiers"></a>

#### Création <a href="#creation" id="creation"></a>

* Obtenir son répertoire actuel : `Get-Location` (ou l'alias `pwd` connu sous Linux)
* Lister le contenu d'un répertoire : `Get-ChildItem` (ou l'alias `ls` ou `dir`)
* Créer un nouveau répertoire ou fichier :

```powershell
New-Item -Name "Nom_Rep" -ItemType Directory                     # Créer une répertoire
New-Item -Name "nom_fichier.ext" -ItemType File.                 # Créer un fichier 
New-Item -Name "nom_fichier.ext" -ItemType File -Value "Contenu" # Créer un fichier avec du contenu
```

#### Manipulation <a href="#manipulation" id="manipulation"></a>
