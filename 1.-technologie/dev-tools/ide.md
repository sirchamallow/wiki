---
icon: square-code
---

# IDE

## Visual Studio Code

Un IDE de Microsoft

{% embed url="https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions" %}

#### Installation

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
dnf check-update
sudo dnf install code
```

***

## Notepadqq

Une alternative linux à Notepadd++

{% embed url="https://snapcraft.io/notepadqq" %}

#### Installation

```bash
sudo dnf install snapd	                # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap    # Enable classic snap support, enter the following to create a symbolic link
sudo snap install notepadqq             # Install Notepadqq
```

***

