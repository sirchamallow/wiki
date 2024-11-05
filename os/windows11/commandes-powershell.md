---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# ⌨️ Commandes Powershell

## Information système <a href="#information-systeme" id="information-systeme"></a>

Une liste de commandes utiles

```bash
# Afficher les informations systèmes (win ver, edition, bios version, etc)
Get-ComputerInfo

# Afficher la version de PowerShell
$PSVersionTable

# Afficher la version de Windows
Get-WMIObject Win32_OperatingSystem

# Afficher le nom de l'ordinateur
$env:COMPUTERNAME
```
