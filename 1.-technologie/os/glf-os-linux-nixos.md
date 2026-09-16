---
icon: linux
---

# GLF OS (Linux/NixOS)

### Site internet

{% embed url="https://glfos.org/" %}

### GLFOS vs NixOS

{% embed url="https://framagit.org/gaming-linux-fr/glf-os/glf-os/-/wikis/Draft/GLF-OS-vs-NixOS" %}

### Commandes GLF

Ces nouvelles commandes sont des alias vers des commandes NixOS plus verbeuse. Notez que ces alias fonctionnent uniquement si vous avez la fonctionnalité expérimental `flake` d'activé, ce qui est le cas par défaut avec GLF-OS.

<table><thead><tr><th width="121">Nom</th><th>Fonction</th></tr></thead><tbody><tr><td><code>glf-update</code></td><td><p>Forcer la mise à jour de son système. Nécessite un redémarrage.</p><p>Note</p><p>C'est la méthode conseillée pour toutes modifications de votre configuration</p></td></tr><tr><td><code>glf-switch</code></td><td><p>Applique le changement de configuration immédiatement.</p><p>Utile lors d'un changement dans <code>/etc/nixos/customConfig/default.nix</code></p><p>Warning</p><p>Pour certaines modifications le redémarrage est obligatoire. A utiliser si vous savez ce que vous faites.</p></td></tr><tr><td><code>glf-history</code></td><td>Afficher l'historique de la mise à jour</td></tr><tr><td><code>glf-systeminfo</code></td><td>Voir les informations du système.</td></tr><tr><td><code>GLFfetch</code></td><td>Obtenir le Fetch spécifique à GLF-OS</td></tr></tbody></table>

Source : [https://framagit.org/gaming-linux-fr/glf-os/glf-os/-/wikis/Overview/Commandes-GLF](https://framagit.org/gaming-linux-fr/glf-os/glf-os/-/wikis/Overview/Commandes-GLF)<br>
