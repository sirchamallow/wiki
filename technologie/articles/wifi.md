---
icon: wifi
description: Quelques astuces sur le Wi-Fi
---

# WiFi

## Retrouvez le mot de passe Wi-Fi

Quel que soit votre OS, lancer le terminal, invite de commande ou PowerShell.&#x20;

Taper ensuite la ligne de commande ci-dessous, correspondante à votre OS.&#x20;

Remplacer NOM\_DU\_VOTRE\_WIFI, par le nom de votre réseau Wi-Fi

### Linux

```bash
sudo cat /etc/NetworkManager/system-connections/NOM_DU_VOTRE_WIFI | grep psk=
```

### Windows

```powershell
netsh wlan show profile NOM_DU_VOTRE_WI-FI key=clear
```

### macOS

```bash
security find-generic-password -wa NOM_DU_VOTRE_WIFI
```

