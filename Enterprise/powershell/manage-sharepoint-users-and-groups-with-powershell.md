---
title: Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzern,-Gruppen und-Websites.'
ms.openlocfilehash: 194486f539593215b8f8a17c04e3d4f499077c65
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068821"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Benutzern,-Gruppen und-Websites.

Wenn Sie ein SharePoint Online-Administrator sind, der mit umfangreichen Listen von Benutzerkonten oder Gruppen arbeitet und eine einfachere Lösung wünscht, können Sie Office 365 PowerShell verwenden. 

## <a name="before-you-begin"></a>Bevor Sie beginnen

Bei den Verfahren in diesem Thema müssen Sie eine Verbindung mit SharePoint Online herstellen. Weitere Informationen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>Abrufen einer Liste von Websites, Gruppen und Benutzern

Bevor wir mit der Verwaltung von Benutzern und Gruppen beginnen, müssen Sie Listen Ihrer Websites, Gruppen und Benutzer abrufen. Sie können diese Informationen dann verwenden, um das Beispiel in diesem Artikel zu bearbeiten.

### <a name="get-a-list-of-sites"></a>Abrufen einer Liste von Websites

Rufen Sie mit diesem Befehl eine Liste der Websites in Ihrem Mandanten ab:

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>Abrufen einer Liste von Gruppen

Rufen Sie mit diesem Befehl eine Liste der Gruppen in Ihrem Mandanten ab:

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>Abrufen einer Liste von Benutzern

Rufen Sie mit diesem Befehl eine Liste der Benutzer in Ihrem Mandanten ab:

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Hinzufügen eines Benutzers zur Gruppe der Websitesammlungsadministratoren

Verwenden Sie den Befehl **Set-ehepartnerr** , um einen Benutzer zur Liste der Websitesammlungsadministratoren in einer Websitesammlung hinzuzufügen. So sieht die Syntax aus:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

Ersetzen Sie zum Verwenden dieser Befehle alle Elemente innerhalb der Anführungszeichen, einschließlich < und >, mit den richtigen Namen.

Dieser Befehlssatz fügt beispielsweise Opal Castillo (Benutzername opalc) die Liste der Websitesammlungsadministratoren in der ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzu:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

Sie können diese Befehle Kopieren und in Editor einfügen, die Variablenwerte für $Tenant, $Site und $User auf tatsächliche Werte aus Ihrer Umgebung ändern und diese dann in Ihr SharePoint Online-Verwaltungsshell-Fenster einfügen, um Sie auszuführen.

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>Hinzufügen eines Benutzers zu anderen Gruppen von Websitesammlungsadministratoren

In dieser Aufgabe verwenden wir den Befehl **Add-Ehegatten** , um einen Benutzer zu einer SharePoint-Gruppe in einer Websitesammlung hinzuzufügen.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

Lassen Sie uns beispielsweise die Gruppe "Revisoren" (Benutzername "glenr") zur ContosoTest-Websitesammlung in der Contoso1-Mandantschaft hinzufügen:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Erstellen einer Website Sammlungs Gruppe

Verwenden Sie den Befehl **Set-SPOSiteGroup** , um eine neue SharePoint-Gruppe zu erstellen und der ContosoTest-Websitesammlung hinzuzufügen.

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
Gruppeneigenschaften wie Berechtigungsstufen können später mithilfe des Cmdlets **Set-SPOSiteGroup** aktualisiert werden.

Beispielsweise können wir die Gruppe "Überwachung" mit Berechtigungen "nur anzeigen" für die Contoso-Test Websitesammlung in der Contoso1-Mandantschaft hinzufügen:

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Entfernen von Benutzern aus einer Gruppe

Manchmal müssen Sie einen Benutzer von einer Website oder sogar allen Websites entfernen. Vielleicht verschiebt sich der Mitarbeiter von einem Geschäftsbereich zu einem anderen oder verlässt das Unternehmen. Sie können dies für einen Mitarbeiter problemlos auf der Benutzeroberfläche tun, dies ist jedoch nicht einfach, wenn Sie eine vollständige Abteilung von einer Website zu einer anderen verschieben müssen.

Wenn Sie jedoch die SharePoint Online-Verwaltungsshell und die CSV-Dateien verwenden, ist dies schnell und einfach. In dieser Aufgabe verwenden Sie Windows PowerShell, um einen Benutzer aus einer Website Sammlungs Sicherheitsgruppe zu entfernen. Anschließend verwenden Sie eine CSV-Datei und entfernen viele Benutzer aus unterschiedlichen Websites. 

Wir verwenden den Befehl **Remove-ehepartnerr** , um einen einzelnen Office 365-Benutzer aus einer Website Sammlungs Gruppe zu entfernen, damit die Befehlssyntax angezeigt wird. Die Syntax sieht folgendermaßen aus:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
Lassen Sie uns beispielsweise Bobby Overby aus der Gruppe der Website Sammlungs Prüfer in der Contoso-Test Websitesammlung in der Contoso1-Mandantschaft entfernen:

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Angenommen, wir wollten Bobby aus allen Gruppen entfernen, in denen er sich gerade befindet. So gehen Sie wie folgt vor:

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> Dies ist nur ein Beispiel. Führen Sie diesen Befehl nur aus, wenn Sie wirklich einen Benutzer aus jeder Gruppe entfernen müssen, beispielsweise wenn der Benutzer das Unternehmen verlässt.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatisieren der Verwaltung umfangreicher Listen von Benutzern und Gruppen

Wenn Sie SharePoint-Websites eine hohe Anzahl von Konten hinzufügen und Ihnen Berechtigungen erteilen möchten, können Sie das Microsoft 365 Admin Center, einzelne PowerShell-Befehle oder eine PowerShell-CSV-Datei verwenden. Die CSV-Datei ist die schnellste Möglichkeit, um diese Aufgabe zu automatisieren.

Der grundlegende Prozess besteht darin, eine CSV-Datei mit Kopfzeilen (Spalten) zu erstellen, die den Parametern entsprechen, die das Windows PowerShell-Skript benötigt. Sie können eine solche Liste ganz einfach in Excel erstellen und dann als CSV-Datei exportieren. Anschließend verwenden Sie ein Windows PowerShell-Skript zum Durchlaufen von Datensätzen (Zeilen) in der CSV-Datei, indem Sie die Benutzergruppen und den Websites hinzufügen. 

Erstellen wir beispielsweise eine CSV-Datei, um eine Gruppe von Websitesammlungen, Gruppen und Berechtigungen zu definieren. Als Nächstes erstellen wir eine CSV-Datei, um die Gruppen mit Benutzern aufzufüllen. Schließlich erstellen und führen wir ein einfaches Windows PowerShell-Skript aus, das die Gruppen erstellt und auffüllt.

Die erste CSV-Datei fügt einer oder mehreren Websitesammlungen eine oder mehrere Gruppen hinzu und weist diese Struktur auf:

### <a name="header"></a>Header

```
Site,Group,PermissionLevels
```

### <a name="item"></a>Element

```
https://tenant.sharepoint.com/sites/site,group,level
```

Hier ist eine Beispieldatei:

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

### <a name="header"></a>Header

```
Group,LoginName,Site
```

### <a name="item"></a>Element

```
group,login,https://tenant.sharepoint.com/sites/site
```

Hier ist eine Beispieldatei:

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

Für den nächsten Schritt müssen Sie die beiden CSV-Dateien auf Ihrem Laufwerk gespeichert haben. Hier sind Beispielbefehle, die sowohl CSV-Dateien als auch Berechtigungen und Gruppenmitgliedschaften hinzufügen:

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Das Skript importiert den Inhalt der CSV-Datei und verwendet die Werte in den Spalten, um die Parameter der Befehle **New-SPOSiteGroup** und **Add-ehegatter** aufzufüllen. In unserem Beispiel speichern wir diese in theO365Admin Ordner auf Laufwerk C, aber Sie können es speichern, wo immer Sie möchten.

Nun entfernen wir eine Gruppe von Personen für mehrere Gruppen an unterschiedlichen Standorten mit derselben CSV-Datei. Nachfolgend sehen Sie einen Beispielbefehl:

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generieren von Benutzer berichten

Möglicherweise möchten Sie einen einfachen Bericht für einige Websites abrufen und die Benutzer für diese Websites, ihre Berechtigungsstufe und andere Eigenschaften anzeigen. So sieht die Syntax aus:

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Dadurch werden die Daten für diese drei Websites erfasst und in eine Textdatei auf Ihrem lokalen Laufwerk geschrieben. Beachten Sie, dass mit dem Parameter-Append neue Inhalte zu einer vorhandenen Datei hinzugefügt werden.

Lassen Sie uns beispielsweise einen Bericht über die ContosoTest-, TeamSite01-und Project01-Websites für den Contoso1-Mandanten ausführen:

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Beachten Sie, dass nur die **$Site** -Variable geändert werden musste. Die **$Tenant** -Variable behält ihren Wert über alle drei Läufe des Befehls bei.

Was geschieht jedoch, wenn Sie dies für jede Website tun möchten? Sie können dies tun, ohne alle diese Websites eingeben zu müssen, indem Sie den folgenden Befehl verwenden:

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Dieser Bericht ist relativ einfach, und Sie können weiteren Code hinzufügen, um spezifischere Berichte oder Berichte mit detaillierteren Informationen zu erstellen. Dies sollte Ihnen jedoch eine Vorstellung davon vermitteln, wie Sie die SharePoint Online-Verwaltungsshell zum Verwalten von Benutzern in der SharePoint Online-Umgebung verwenden können.
   
## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Verwalten von SharePoint Online mit Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

