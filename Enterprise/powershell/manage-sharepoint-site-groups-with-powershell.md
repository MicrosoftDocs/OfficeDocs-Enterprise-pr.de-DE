---
title: Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell
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
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.'
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.
  
Obwohl Sie das Office 365 Administrationscenter verwenden können, können Sie auch Office 365 PowerShell zum Verwalten von Ihrer SharePoint Online-Website verwenden.

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Die Verfahren in diesem Artikel müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Ansicht SharePoint Online mit Office 365 PowerShell

Die SharePoint Online-Verwaltungskonsole enthält einige leicht zu bedienende-Methoden zum Verwalten von Websitegruppen. Nehmen wir beispielsweise an, die Sie an die Gruppen und Mitglieder der Gruppe suchen möchten die https://litwareinc.sharepoint.com/sites/finance Website. Nachfolgend finden Sie müssen Aufgaben:

1. Klicken Sie im Office 365 Admin Center auf **Ressourcen** > **Websites**, und klicken Sie dann auf die URL der Website.
2. Klicken Sie im Dialogfeld Website-Auflistung auf **Gehe zu dieser Website**.
3. Klicken Sie auf das Symbol **Einstellungen** (befindet sich in der oberen rechten Ecke der Seite), und klicken Sie dann auf **websiteeinstellungen**, auf der Websiteseite:</br>
![SharePoint Online-websiteeinstellungen](images/spo-site-settings.png)</br>
4. Klicken Sie auf der Seite Websiteeinstellungen unter **Benutzer und Berechtigungen**auf **Berechtigungen für Websites** .

Wiederholen Sie dieses Verfahren für die nächste gewünschte Website.

Verwenden Sie zum Abrufen einer Liste mit Gruppen mithilfe von Office 365 PowerShell den folgenden Befehlssatz:

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Es gibt zwei Methoden zum Ausführen dieses Befehls in der Befehlszeile SharePoint Online-Verwaltungsshell festgelegt:
- Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , wählen Sie die Befehle aus, und fügen Sie sie in der Befehlszeile SharePoint Online-Verwaltungsshell. Wenn Sie dies tun, PowerShell stoppt bei einer >> Aufforderung. Drücken Sie die EINGABETASTE, um das Ausführen der für jeden Befehl.</br>
- Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , und speichern Sie diese Datei mit dem Namen und die Erweiterung. ps1 in einem geeigneten Ordner. Führen Sie im nächsten Schritt das Skript über die Befehlszeile SharePoint Online-Verwaltungsshell durch Angeben des Namens Pfad und den Dateinamen. Es folgt ein Beispiel:</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = Get-SPOSite Foreach ($y in $x) {Write-Host $y.Url - ForegroundColor "Gelb" $z = Get-SPOSiteGroup-Website $y.Url Foreach ($ein in $z) {$b = Get-SPOSiteGroup-Site-$y.Url-Gruppe $a.Title Write-Host $b.Title - ForegroundColor "Cyan" $b | Select-Object - ExpandProperty Benutzer Write-Host}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

