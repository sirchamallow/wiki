---
icon: circle-nodes
---

# Identifier ses DNS

Pour savoir quel serveur DNS vous utilisez, nous pouvons le faire en ligne de commande, vous pouvez suivre ces étapes :

### Windows

1. **Ouvrez l'Invite de commandes** :
   * Appuyez sur `Win + R`, tapez `cmd`, puis appuyez sur `Entrée`.
2.  **Tapez la commande suivante** :

    ```
    ipconfig /all
    ```

    * Appuyez sur `Entrée`.
3. **Recherchez la section "Serveurs DNS"** dans les résultats affichés. Vous y trouverez les adresses des serveurs DNS utilisés par vos adaptateurs réseau.

### macOS

1. **Ouvrez le Terminal** :
   * Vous pouvez le trouver dans `Applications > Utilitaires > Terminal`.
2.  **Tapez la commande suivante** :

    ```
    scutil --dns | grep 'nameserver\[[0-9]*\]'
    ```

    * Appuyez sur `Entrée`.
3. **Les adresses des serveurs DNS** seront listées dans les résultats.

### Linux

1. **Ouvrez le Terminal**.
2.  **Tapez la commande suivante** :

    ```
    nmcli dev show | grep 'IP4.DNS'
    ```

    * Appuyez sur `Entrée`.
3. **Les adresses des serveurs DNS** seront affichées dans les résultats.
