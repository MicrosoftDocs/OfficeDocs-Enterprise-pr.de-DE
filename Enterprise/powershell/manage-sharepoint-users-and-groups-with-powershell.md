---
title: Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzer, Gruppen und Websites.'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzer, Gruppen und Websites.

Wenn Sie eine SharePoint Online sind, funktioniert mit umfangreichen Listen von Benutzerkonten oder-Gruppen und einfacher Verwaltung möchte, können Sie Office 365 PowerShell verwenden. 

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Die Verfahren in diesem Thema müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Abrufen einer Liste von Websites, Gruppen und Benutzern

Bevor wir mit der Verwaltung von Benutzern und Gruppen beginnen, müssen Sie Listen Ihrer Websites, Gruppen und Benutzer abrufen. Sie können anhand dieser Informationen dann das Beispiel in diesem Artikel durcharbeiten.

### <a name="get-a-list-of-sites"></a>Abrufen einer Liste von Websites ab

Rufen Sie eine Liste der Websites in Ihrem Mandanten mit dem folgenden Befehl ab:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Abrufen einer Liste von Gruppen

Rufen Sie eine Liste der Gruppen in Ihrem Mandanten mit dem folgenden Befehl ab:

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a>Abrufen einer Liste von Benutzern

Rufen Sie eine Liste der Benutzer in Ihrem Mandanten mit dem folgenden Befehl ab:

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Hinzufügen eines Benutzers zur Gruppe der Websitesammlungsadministratoren

Verwenden Sie den **Set-SPOUser** -Befehl zum Hinzufügen eines Benutzers zur Liste der Websitesammlungs-Administratoren für eine Websitesammlung. Dies ist die Syntax wie sieht:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

In diesem Beispiel Variablen verwendet, um Werte zu speichern und Notizen im Skript hat (beispielsweise "<!--This is the Tenant Name…-->") können Sie sehen, was diese Werte werden soll.

Wird beispielsweise dieser Reihe von Befehlen Opal Castillo (User Name Opalc) die Liste der Websitesammlungs-Administratoren für die Websitesammlung ContosoTest des Mandanten contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Sie können diese Befehle tatsächlich ausschneiden und in Notepad einfügen, die Variablenwerte für $tenant, $site und $user in tatsächliche Werte aus Ihrer Umgebung ändern, und dies dann in Ihr Windows SharePoint Online-Verwaltungsshellfenster einfügen.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Hinzufügen eines Benutzers zu anderen Gruppen von Websitesammlungsadministratoren

Für diese Aufgabe wird den **Add-SPOUser** -Befehl verwendet, um einen Benutzer einer SharePoint-Gruppe für eine Websitesammlung hinzuzufügen. Dies ist die Syntax wie sieht:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Beispielsweise fügen Sie Glen voller (User Name Glenr) der Gruppe Auditoren für die Websitesammlung ContosoTest des Mandanten contoso1:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Erstellen einer Websitesammlungsgruppe

Sie verwenden den Befehl **Set-SPOSiteGroup** Erstellen einer neuen SharePoint-Gruppe und für die Websitesammlung ContosoTest hinzufügen. Dies ist die Syntax wie sieht:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> Sie müssen eine beliebige Zeichenfolge mit Leerzeichen in Anführungszeichen setzen. Gruppe Eigenschaften wie Berechtigungsstufen, können später mit dem **Set-SPOSiteGroup** -Cmdlet aktualisiert werden.

Beispielsweise wir die Gruppe Auditoren mit Leserechten Berechtigungen für die Websitesammlung Contoso Test des Mandanten contoso1 hinzuzufügen:

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Entfernen von Benutzern aus einer Gruppe

Manchmal müssen Sie einen Benutzer aus einer Seite oder sogar aus allen Websites entfernen. Vielleicht wechselt der Mitarbeiter in einen anderen Bereich oder verlässt das Unternehmen. Bei nur einem Mitarbeiter können Sie dazu problemlos die Benutzeroberfläche verwenden. Aber das Ganze ist nicht so leicht, wenn Sie einen ganzen Bereich von einer Website zu einer anderen umziehen müssen.

Verwenden Sie die SharePoint Online-Verwaltungsshell und CSV-Dateien, ist dies jedoch schnell und einfach. Windows PowerShell verwenden Sie für diese Aufgabe um aus einer Website Auflistung Sicherheitsgruppe einen Benutzer zu entfernen. Sie können eine CSV-Datei verwenden, und Entfernen von vielen Benutzern von verschiedenen Standorten. 

Wir können den Befehl **Remove-SPOUser** verwenden, um einen einzelnen Office 365-Benutzer aus einer Websitegruppe-Auflistung entfernen, damit wir die Befehlssyntax sehen können. Hier wird die Syntax wie sieht:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

Beispielsweise sollen Bobby Overby aus der Gruppe der Prüfer in der Contoso Test-Websitesammlung in der contoso1-Instanz entfernt:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Angenommen, wir möchten Bobby aus allen Gruppen entfernen, in denen er derzeit Mitglied ist. Wir würden dazu folgendermaßen vorgehen:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Hiermit wird nur gezeigt, wie Sie dies tun. Sie sollten diesen Befehl nur ausführen, wenn Sie einen Benutzer wirklich aus allen Gruppen entfernen müssen, z. B. wenn der Benutzer das Unternehmen verlässt.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatisieren der Verwaltung umfangreicher Listen mit Benutzern und Gruppen

Sie können eine große Anzahl von Konten zu SharePoint-Websites hinzufügen, und erteilen sie Berechtigungen, die Office 365 Administrationscenter, einzelne PowerShell-Befehle oder PowerShell verwenden eine CSV-Datei. Mit diesen Optionen wird die CSV-Datei die schnellste Möglichkeit, diese Aufgabe automatisieren.

Die grundlegende Vorgehensweise ist eine CSV-Datei erstellen, die Kopfzeilen (Spalten) verfügt, die die Parameter entsprechen, die das Windows PowerShell-Skript muss. Sie können auf einfache Weise eine solche Liste in Excel erstellen und anschließend als eine CSV-Datei zu exportieren. Klicken Sie dann, verwenden Sie ein Windows PowerShell-Skript durchlaufen Datensätze (Zeilen) in der CSV-Datei hinzufügen von Benutzern zu Gruppen auf Websites und Gruppen. 

Erstellen wir als Beispiel eine CSV-Datei, um eine Gruppe von Websitesammlungen, Gruppen und Berechtigungen zu definieren. Als Nächstes erstellen wir eine CSV-Datei, um die Gruppen mit Benutzern aufzufüllen. Anschließend erstellen wir ein einfaches Windows PowerShell-Skript, das die Gruppen erstellt und auffüllt, und führen es aus.

Die erste CSV-Datei fügt einer oder mehreren Websitesammlungen eine oder mehrere Gruppen hinzu und weist diese Struktur auf:

### <a name="header"></a>Kopfzeile:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Artikel:

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

Es folgt eine Beispieldatei:

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Die zweite CSV-Datei fügt einer oder mehreren Gruppen einen oder mehrere Benutzer hinzu und weist diese Struktur auf:

### <a name="header"></a>Kopfzeile:

```
Group,LoginName,Site
```

### <a name="item"></a>Artikel:

```
group,login,https://tenant.sharepoint.com/sites/site
```

Es folgt eine Beispieldatei:

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

Im nächsten Schritt müssen Sie die beiden CSV-Dateien auf Ihrem Laufwerk speichern. Hier sind die Befehle, die beide CSV-Dateien verwenden und Berechtigungen und Gruppenmitgliedschaft hinzufügen:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Das Skript den Inhalt der CSV-Datei importiert, und die Werte in den Spalten (in Fettschrift) verwendet, um die Parameter der Befehle **New-SPOSiteGroup** und **Add-SPOUser** auffüllen. In unserem Beispiel werden wir dies auf Laufwerk C gespeichert, jedoch können Sie es speichern, wo Sie möchten.

Als nächsten Schritt entfernen wir mehrere Personen, die sich in verschiedenen Gruppen in unterschiedlichen Websites befinden, mithilfe derselben CSV-Datei. Hier ist der Befehl:

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Erstellen von Benutzerberichten

Sie möchten vielleicht einen einfachen Bericht für einige Websites erstellen und die Benutzer für diese Websites, deren Berechtigungsebene und weitere Eigenschaften anzeigen. So sieht die Syntax aus:

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Dadurch wird Code die Daten für diese drei Standorte und in einer Textdatei auf dem lokalen Laufwerk zu schreiben. Beachten Sie, dass der Parameter – Append werden neue Inhalte zu einer vorhandenen Datei hinzufügen.

Angenommen, wir führen einen Bericht auf den Websites ContosoTest, TeamSite01 und Project01 für den Mandanten „Contoso 1“ aus.

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Beachten Sie, dass wir hatten, nur die **$site** -Variable zu ändern. Die Variable **$tenant** hält seinen Wert über alle drei Textläufe des Befehls.

Was wäre, wenn Sie den Bericht für jede Website erstellen wollen würden? Sie müssen dazu nicht alle diese Website eingeben, sondern können diesen Befehl verwenden:

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

In diesem Bericht ist relativ einfach, und Sie können weitere Code zum Erstellen von genauere Berichte oder Berichte, die enthalten ausführlichere Informationen hinzufügen. Aber diese Weise erhalten Sie eine Vorstellung vom Zweck der Verwendung von SharePoint Online-Verwaltungsshell zum Verwalten von Benutzern in der SharePoint Online-Umgebung.
   
## <a name="see-also"></a>Siehe auch

[Verbinden Sie mit SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Verwalten von SharePoint Online mit Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

