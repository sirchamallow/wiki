---
icon: hammer-brush
---

# Dépannage

## Dépannage

### Android Flash Tool

[Android Flash Tool](https://flash.android.com/) vous permet de flasher une version Android sur votre appareil à des fins de développement et de test. Pour commencer, vous avez besoin d'une machine de développement et d'un appareil Android.

{% hint style="info" %}
Source : [https://source.android.com/docs/setup/build/flash#device-requirements](https://source.android.com/docs/setup/build/flash#device-requirements)
{% endhint %}

{% embed url="https://flash.android.com/" %}

### &#x20;**Xiaomi ADB/FastBoot Tools**

Dans ce tutoriel rapide, vous pouvez apprendre à désinstaller les applications d'usine sur vos téléphones Xiaomi Mi/Note/Redmi fonctionnant sous Android sans modifications d'accès root ! \
Vous pouvez supprimer des applications telles que **MSA** ( **M** IUI **System** A **ds** ), PartnerBookmarks, PartnerNetflixActivation, Mi Browser, Mi Video, Mi Pay, Mi Share, Facebook, etc.

**Tutoriel**

1. Activer **le mode développeur** sur l'appareil Android
2. Activer **le débogage USB** sur l'appareil Android
3. [**Installer les pilotes Android ADB**](https://developer.android.com/studio/run/win-usb) officiels de Google
4. Installer **le kit de développement JAVA** ( [**JDK par Oracle**](https://www.oracle.com/java/technologies/javase-downloads.html) ou [**OpenJDK**](https://adoptopenjdk.net/) )
5. Téléchargez et exécutez [**le fichier .jar de Xiaomi ADB/FastBoot Tools**](https://github.com/Szaki/XiaomiADBFastbootTools) (cliquez avec le bouton droit et sélectionnez pour l'ouvrir avec JDK installé ci-dessus, certains programmes d'archivage comme WinRAR ou 7-zip peuvent s'associer aux fichiers **\*.jar !)**
6. **Mise à jour : vous devez confirmer l'empreinte RSA** de votre ordinateur en appuyant sur le message OK qui apparaîtra sur l'écran de votre téléphone une fois que XiaomiADBFastBootTool se connectera à votre appareil en mode ADB !
7. Supprimer les applications/packages indésirables
8. **⚠️ Désactivez le débogage USB sur votre appareil Android lorsque vous avez terminé (pour des raisons de sécurité !)**

{% hint style="warning" %}
Toutes les applications ne peuvent pas être supprimées (désinstallées ou désactivées) de cette façon, comme par exemple pour l'application Mi Gallery, car cela bloquerait votre appareil. Mais la plupart des autres applications c'est possible :smile:
{% endhint %}

{% hint style="success" %}
Source : [https://tehnoblog.org/xiaomi-android-phone-how-to-uninstall-and-remove-factory-apps-bloatware-no-root/](https://tehnoblog.org/xiaomi-android-phone-how-to-uninstall-and-remove-factory-apps-bloatware-no-root/)
{% endhint %}
