---
description: Quelques astuces sur le Wi-Fi
icon: wifi
---

# WiFi

## Retrouvez le mot de passe Wi-Fi

1. Quel que soit votre OS, lancer le terminal, invite de commande ou PowerShell.&#x20;
2. Taper ensuite la ligne de commande ci-dessous, correspondante à votre OS.&#x20;
3. Remplacer NOM\_DU\_VOTRE\_WIFI, par le nom de votre réseau Wi-Fi

### Sous Linux

```bash
sudo cat /etc/NetworkManager/system-connections/NOM_DU_VOTRE_WIFI | grep psk=
```

### Sous Windows

```powershell
netsh wlan show profile NOM_DU_VOTRE_WI-FI key=clear
```

### Sous macOS

```bash
security find-generic-password -wa NOM_DU_VOTRE_WIFI
```

