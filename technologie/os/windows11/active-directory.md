---
icon: list-tree
---

# Active Directory

## Active Directory <a href="#manipulation" id="manipulation"></a>

Gestion de l'Active Directory avec le Powershell

### Raccourci recherche

Pour créer un **raccourci de recherche pour Active Directory** :

* Cliquez avec le bouton droit sur un espace vide de votre bureau et sélectionnez "Nouveau", puis "Raccourci".
* Dans le champ d'emplacement, entrez le chemin suivant :

```powershell
%SystemRoot%\system32\rundll32.exe dsquery,OpenQueryWindow
```

* Cliquez sur **"Suivant"** pour continuer.
* Donnez un nom à votre raccourci, par exemple **"Recherche AD"**, puis cliquez sur **"Terminer"**.

### Informations sur les ordinateurs

<pre class="language-powershell" data-full-width="true"><code class="lang-powershell">Get-ADComputer -Filter *                                 # Obtenez la liste des ordinateurs du domaine AD
Get-ADComputer -Filter * -Properties *                   # Obtenez les propriétés des ordinateurs
Get-ADComputer -Filter * -Properties * | Select Name     # Obtenez le nom des ordinateurs

# Comptez le nombre d’ordinateurs regroupés par la version du système d’exploitation
Get-ADComputer -Filter * -Properties * | group -Property operatingSystem | Select Name,Count

# Obtenez le dernier logon des ordinateurs
Get-ADComputer -Filter * -Properties * | Select Name, LastLogonDate

# Obtenez la liste des ordinateurs inactifs pour un nombre spécifique de jours.
$Days = 10
$Time = (Get-Date).Adddays(-($Days))
Get-ADComputer -Filter {LastLogonTimeStamp -lt $Time} -Properties * | Select Name, LastLogonDate

<strong># Obtenez tous les ordinateurs avec un texte spécifique dans le nom
</strong>Get-ADComputer -Filter { Name -like "*srv*"}
</code></pre>

### Création et activation d'un utilisateur <a href="#creation-et-activation-dun-utilisateur" id="creation-et-activation-dun-utilisateur"></a>

Pour créer un utilisateur, la commande à utiliser est `New-ADUser`. Il faut cependant un certain nombre d'informations, tel que le login, le mot de passe etc.&#x20;

Voici la _Syntaxe de création d'un utilisateur :_

{% code fullWidth="true" %}
```powershell
New-ADUser -Name "NOM Prénom" -SamAccountName <Login> -UserPrincipalName "login@domaine" -AccountPassword (ConvertTo-SecureString -AsPlainText <mdp> -Force) -PasswordNeverExpires $true -CannotChangePassword $true
```
{% endcode %}

* `-Name` : Indique le nom du compte, généralement le nom/prénom de la personne;
* `-SamAccountName` : Indique le Login de la personne, ce qu'elle va utiliser pour se connecter;
* `-UserPrincipalName` : Indique le nom complet de l'utilisateur dans l'AD (format login@domaine);
* `-AccountPassword` : Renseigne le mot de passe. l'option `ConvertTo-SecureString` permet de convertir le mot de passe en clair dans un format chiffré, illisible par l'humain.
* `-PasswordNeverExpires` : Indique si l'on veut que les personnes changent leurs mot de passe à intervalle régulier.

{% hint style="info" %}
Pour se faire la main avec Active Directory, mieux vaut activer cette option. \
En production, il vaut mieux **désactiver** cette option.
{% endhint %}

* `-CannotChangePassword` : Indique si l'on autorise le changement du mot de passe directement par les utilisateurs.

> Cette option dépend de la politique interne de l'entreprise, et dépendera probablement du service auquel cette personne sera affectée.

{% hint style="success" %}
Cette option dépendra de la politique interne de l'entreprise ainsi que probablement du service auquel cette personne sera affectée.
{% endhint %}

On active ensuite ce compte :

```powershell
Enable-ADAccount <login>
```

{% hint style="info" %}
Nous pouvons également ajouter l'option `-Enable $true` dans la commande précédente pour activer le compte
{% endhint %}

### Obtenir la liste des utilisateurs Active Directory <a href="#creation-et-activation-dun-utilisateur" id="creation-et-activation-dun-utilisateur"></a>

`Get-ADUser -Filter *` . Permets de lister les utilisateurs Active Directory

{% hint style="warning" %}
Cette commande va renvoyer TOUTES les informations de l'utilisateur, ce qui n'est peut-être pas nécessaire.&#x20;
{% endhint %}

Nous pouvons donc sélectionner les champs que l'on veut récupérer. \
&#xNAN;_&#x45;xemple de commande :_

```powershell
Get-ADUser -Filter * | select Name, samAccountName, UserPrincipalName
```

Cette commande va récupérer les champs **nom**, **login** et **nom complet de l'utilisateur** sur l'AD.

Nous pouvons également exporter les champs sélectionnés dans un fichier CSV en ajoutant la commande `| Export-Csv <nom_sortie.csv -Encoding UTF8`.

{% hint style="danger" %}
Attention : le | est important, puis que nous ajoutons cette commande à la suite de la précédent
{% endhint %}

### Comptes d’utilisateurs récents

Trouvez les comptes d’utilisateurs créés sur Active Directory au cours des 30 derniers jours.

{% code fullWidth="true" %}
```powershell
$Days = 30 # Modifier la valeur pour changer le nombre de jours
$Time = (Get-Date).Adddays(-($Days))
Get-ADUser -Filter * -Property whenCreated | Where {$_.whenCreated -gt $Time} | ft Name, WhenCreated
```
{% endcode %}

### Utilisateurs qui n’ont pas changé de mot de passe

Trouvez les utilisateurs dans Active Directory avec un mot de passe de plus de 30 jours.

{% code fullWidth="true" %}
```powershell
$Days = 30 # Modifier la valeur pour changer le nombre de jour
$Time = [DateTime]::Today.AddDays(-$Days)
Get-ADUser -Filter '(PasswordLastSet -lt $Time)' -Properties PasswordLastSet | ft Name,PasswordLastSet
```
{% endcode %}

### Ordinateurs inactifs

Trouvez les utilisateurs qui ne se sont pas connectés au Répertoire actif au cours des 30 derniers jours.

{% code fullWidth="true" %}
```powershell
$Days = 30
$Time = (Get-Date).Adddays(-($Days))
Get-ADUser -Filter {LastLogonTimeStamp -lt $Time} -Properties * | Select Name, LastLogonDat
```
{% endcode %}
