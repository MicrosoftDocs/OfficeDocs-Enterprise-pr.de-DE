---
title: Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um SharePoint Online Websitegruppen zu verwalten.'
ms.openlocfilehash: 2deaeb2a39b094b828f75a18d4a2c2f06ca79e47
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031740"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell, um SharePoint Online Websitegruppen zu verwalten.
  
Obwohl Sie das Microsoft 365 Admin Center verwenden können, können Sie auch Office 365 PowerShell verwenden, um Ihre SharePoint Online Websitegruppen zu verwalten.

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Für die Verfahren in diesem Artikel müssen Sie eine Verbindung mit SharePoint Online herstellen. Weitere Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Anzeigen von SharePoint Online mit Office 365 PowerShell

Das SharePoint Online Admin Center verfügt über einige einfach zu verwendende Methoden zum Verwalten von Websitegruppen. Nehmen wir beispielsweise an, Sie möchten die Gruppen und die Gruppenmitglieder für die `https://litwareinc.sharepoint.com/sites/finance` Website betrachten. Gehen Sie dazu wie folgt vor:

1. Klicken Sie im Microsoft 365 Admin Center auf **Ressourcen** > **Websites**, und klicken Sie dann auf die URL der Website.
2. Klicken Sie im Dialogfeld -Websitesammlung auf **Zu dieser Website wechseln**.
3. Klicken Sie auf dieser Seite auf das Symbol **Einstellungen** (oben rechts auf der Seite) und dann auf **Websiteeinstellungen**:<br/>
![SharePoint Online von Websiteeinstellungen](media/spo-site-settings.png)<br/>
4. Klicken Sie auf der Seite Websiteeinstellungen**Benutzer und Berechtigungen** auf **Websiteberechtigungen**.

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

Es gibt zwei Möglichkeiten zum Ausführen dieses Befehlssatzes in der Eingabeaufforderung der SharePoint Online Verwaltungsshell:

- Kopieren Sie die Befehle in Notepad (oder einen anderen Text-Editor), ändern Sie den Wert der **$SiteUrl** -Variablen, wählen Sie die Befehle aus, und fügen Sie Sie dann in die Eingabeaufforderung der SharePoint Online Verwaltungsshell ein. Wenn Sie dies tun, wird PowerShell an einer **>>** Eingabeaufforderung angehalten. Drücken Sie die EINGABETASTE, um den **Foreach**-Befehl auszuführen.<br/>
- Kopieren Sie die Befehle in Editor (oder einen anderen Text-Editor), ändern Sie den Wert der **$siteURL**Variable, und speichern Sie dann diese Textdatei mit einem Namen und der Erweiterung „.ps1“ in einem geeigneten Ordner. Führen Sie als nächstes das Skript über die Eingabeaufforderung der SharePoint Online Management Shell aus, indem Sie den Pfad und den Dateinamen angeben. Nachfolgend sehen Sie einen Beispielbefehl:

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

In beiden Fällen wird Folgendes angezeigt.

![SharePoint Online Websitegruppen](media/SPO-site-groups.png)

Dies sind alle Gruppen, die für die Website `https://litwareinc.sharepoint.com/sites/finance`erstellt wurden, sowie alle Benutzer, die diesen Gruppen zugewiesen sind. Die Gruppennamen werden in gelb dargestellt, damit Sie die Gruppennamen von den Mitgliedern leicht unterscheiden können.

Ein weiteres Beispiel ist ein Befehlssatz, der die Gruppen und alle Gruppenmitgliedschaften für alle Ihre SharePoint Online Websites auflistet.

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

