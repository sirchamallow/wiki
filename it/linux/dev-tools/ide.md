# ✨ IDE

## Visual Studio Code

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
dnf check-update
sudo dnf install code
```

{% hint style="info" %}
Source : [https://code.visualstudio.com/docs/setup/linux#\_rhel-fedora-and-centos-based-distributions](https://code.visualstudio.com/docs/setup/linux#\_rhel-fedora-and-centos-based-distributions)
{% endhint %}

## SublimeText

```bash
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
sudo dnf install sublime-text
```

{% hint style="info" %}
Source : [https://www.sublimetext.com/docs/linux\_repositories.html#dnf](https://www.sublimetext.com/docs/linux\_repositories.html#dnf)
{% endhint %}

## IDEA Ultimate

```bash
sudo dnf install snapd		                    # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap                # Enable classic snap support, enter the following to create a symbolic link
sudo snap install intellij-idea-ultimate --classic  # Install Jetbrains IDEA Ultimate
```

{% hint style="info" %}
Source : [https://snapcraft.io/install/intellij-idea-ultimate/fedora#install](https://snapcraft.io/install/intellij-idea-ultimate/fedora#install) & [https://www.jetbrains.com/idea/download/#section=linux](https://www.jetbrains.com/idea/download/#section=linux)
{% endhint %}

## Notepadqq

Une alternative linux à Notepadd++

#### Installation

```bash
sudo dnf install snapd	                # Enable Snapd
sudo ln -s /var/lib/snapd/snap /snap    # Enable classic snap support, enter the following to create a symbolic link
sudo snap install notepadqq             # Install Notepadqq
```

{% hint style="info" %}
Source : [https://snapcraft.io/notepadqq](https://snapcraft.io/notepadqq)
{% endhint %}
