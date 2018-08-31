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
ms.openlocfilehash: a9fddf33b2f29e7b4e8ed6b86c2433c7ca19a9fc
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915350"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.
  
Obwohl Sie das Office 365 Administrationscenter verwenden können, können Sie auch Office 365 PowerShell zum Verwalten von Ihrer SharePoint Online-Website verwenden.

## <a name="before-you-begin"></a>Bevor Sie beginnen

Die Verfahren in diesem Artikel müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Ansicht SharePoint Online mit Office 365 PowerShell

Die SharePoint Online-Verwaltungskonsole enthält einige leicht zu bedienende-Methoden zum Verwalten von Websitegruppen. Nehmen wir beispielsweise an, die Sie an die Gruppen und Mitglieder der Gruppe suchen möchten die `https://litwareinc.sharepoint.com/sites/finance` Website. Nachfolgend finden Sie müssen Aufgaben:

1. Klicken Sie im Office 365 Admin Center auf **Ressourcen** > **Websites**, und klicken Sie dann auf die URL der Website.
2. Klicken Sie im Dialogfeld -Websitesammlung auf **Zu dieser Website wechseln**.
3. Klicken Sie auf dieser Seite auf das Symbol **Einstellungen** (oben rechts auf der Seite) und dann auf **Websiteeinstellungen**:</br>
![SharePoint Online-websiteeinstellungen](media/spo-site-settings.png)</br>
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

- Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , wählen Sie die Befehle aus, und fügen Sie sie in der Befehlszeile SharePoint Online-Verwaltungsshell. Wenn Sie dies tun, PowerShell stoppt bei einer **>>** Aufforderung. Drücken Sie die EINGABETASTE, um den **Foreach** -Befehl ausführen.</br>
- Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , und speichern Sie diese Datei mit dem Namen und die Erweiterung. ps1 in einem geeigneten Ordner. Führen Sie im nächsten Schritt das Skript über die Befehlszeile SharePoint Online-Verwaltungsshell durch Angeben des Namens Pfad und den Dateinamen. Hier ist ein Beispielbefehl:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

In beiden Fällen wird Folgendes angezeigt.

![SharePoint Online-Websitegruppen](media/SPO-site-groups.png)

Dies sind alle Gruppen, die für die Website erstellt wurden `https://litwareinc.sharepoint.com/sites/finance`sowie alle Benutzer, die diesen Gruppen zugewiesen. Gruppennamen sind separate Gruppennamen in ihrer Elemente Gelb, die Sie unterstützen.

Als weiteres Beispiel ist hier ein Befehl, der die Gruppen und alle Gruppenmitgliedschaften für alle Ihre SharePoint Online-Websites aufgeführt sind.

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

