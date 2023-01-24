---
description: TUXEDO Computers
---

# 💻 TUXEDO Computers

### Introduction

TUXEDO Computers est fabricant d'ordinateurs originaire d'Allemagne qui produit des configs entièrement custom et avec du matériel parfaitement optimisé pour l'exécution de Linux.

### Tuxedo Keyboard

Kernel module pour le rétroéclairage du clavier

{% hint style="warning" %}
Pré-requis : Assurez-vous que**`kernel-devel`**soit installé pour la version du noyau en cours d'exécution
{% endhint %}

```bash
sudo dnf in kernel-devel
```

```bash
dnf copr enable kallepm/tuxedo-keyboard	  # Activate repo Copr ("Community projects")
dnf install tuxedo-keyboard		  # Install Tuxedo Keyboard
```

Source : [https://copr.fedorainfracloud.org/coprs/kallepm/tuxedo-keyboard/](https://copr.fedorainfracloud.org/coprs/kallepm/tuxedo-keyboard/) & [https://github.com/tuxedocomputers/tuxedo-keyboard](https://github.com/tuxedocomputers/tuxedo-keyboard)

### Tuxedo Control Center

Un outil pour vous aider à contrôler les paramètres de performance, d'énergie, de ventilation et de confort sur les ordinateurs portables TUXEDO.

{% hint style="warning" %}
Pré-requis : **Tuxedo Keyboard** doit être installer avant
{% endhint %}

```bash
dnf copr enable kallepm/tuxedo-control-center  # Activate repo Copr ("Community projects")
dnf install tuxedo-control-center              # Install Tuxedo Control Center
```

Source : [https://copr.fedorainfracloud.org/coprs/kallepm/tuxedo-control-center/](https://copr.fedorainfracloud.org/coprs/kallepm/tuxedo-control-center/) & [https://github.com/tuxedocomputers/tuxedo-control-center](https://github.com/tuxedocomputers/tuxedo-control-center)



