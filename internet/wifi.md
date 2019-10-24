# WiFi

## Retrouvez le mot de passe WiFi

1. Quelque soit votre OS, lancer le terminal, invite de commande ou Powershell. 
2. Taper ensuite la ligne de commande ci-dessous, correspondante à votre OS. 
3. Remplacer NOM\_DU\_VOTRE\_WIFI, par le nom de votre réseau WiFi

### Sous Linux

```text
sudo cat /etc/NetworkManager/system-connections/NOM_DU_VOTRE_WIFI | grep psk=
```

### Sous Windows

```text
netsh wlan show profile NOM_DU_VOTRE_WIFI key=clear
```

### Sous macOS

```text
security find-generic-password -wa NOM_DU_VOTRE_WIFI
```



