---
title: Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell, erstellen Sie neue SharePoint Online-Websites, und fügen Sie Benutzer und Gruppen auf diese Websites.'
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897168"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden von Office 365 PowerShell neue SharePoint Online-Websites erstellen, und fügen Sie Benutzer und Gruppen auf diese Websites.

Wenn Sie Office 365 PowerShell zum Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern verwenden, können Sie schnell und wiederholt Aufgaben ausführen viel schneller als Sie in der Office-356-Verwaltungskonsole können. Sie können auch Aufgaben ausführen, die nicht möglich, in der Verwaltungskonsole Office 356 auszuführen sind. 

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Die Verfahren in diesem Thema müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Schritt 1: Erstellen neuer Websitesammlungen mithilfe von Office 365 PowerShell

Erstellen Sie mehrere Websites mithilfe von Office 365 PowerShell und eine CSV-Datei, die Sie mit den bereitgestellten Beispielcode und im Editor erstellen. Für dieses Verfahren benötigen Sie die für Platzhalterinformationen in Klammern mit eigenen Website und Mandanten-spezifische Informationen ersetzen. Dieser Vorgang können Sie eine einzelne Datei zu erstellen, und führen Sie einen einzelnen Office 365 PowerShell-Befehl, der diese Datei verwendet. Dadurch wird die Aktionen wiederholbare und tragbaren und viele, wenn nicht alle Fehler, die lange Befehle in SharePoint Online-Verwaltungsshell eingeben stammen kann entfällt. Es gibt zwei Teile dieser Prozedur. Zuerst erstellen Sie eine CSV-Datei, und Sie werden von Office 365 PowerShell, der seinen Inhalt verwendet wird, um die Websites erstellen, CSV-Datei verweisen.

Das Office 365 PowerShell-Cmdlet importiert die CSV-Datei und leitet sie so, dass sie in die Schleife in den runden Klammern passt, die die erste Zeile der Datei als Spaltenkopf liest. Das Office 365 PowerShell-Cmdlet arbeitet sich dann durch die restlichen Datensätze, erstellt eine neue Websitesammlung für jeden Datensatz und weist Eigenschaften der Websitesammlung gemäß den Spaltenköpfen zu.

### <a name="create-a-csv-file"></a>Erstellen einer CSV-Datei

1. Öffnen Sie den Editor und fügen Sie den folgenden Textblock ein:<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>Wobei *Mandanten* ist der Name Ihres Mandanten und *Besitzer* ist der Benutzername des Benutzers bei Ihrem Mandanten, denen möchten Sie die Rolle des primären Websitesammlungsadministrators gewähren.<br/>(Sie können STRG + H drücken, wenn Sie zum Ersetzen schneller Massen-Editor verwenden.)<br/>

2. Speichern Sie die Datei auf Ihrem Desktop als **SiteCollections.csv**.<br/>

> [!TIP]
> Bevor Sie diese oder andere CSV oder Windows PowerShell-Skriptdatei verwenden, ist es empfehlenswert, um sicherzustellen, dass keine zusätzlichen oder nicht druckbaren Zeichen vorhanden sind. Öffnen die Datei in Word, und klicken Sie im Menüband klicken Sie auf das Absatzsymbol nicht druckbare Zeichen angezeigt. Es sollten keine zusätzlichen nicht druckbaren Zeichen sein. Beispielsweise sollte keine Absatzmarken am Ende der Datei außer dem letzten vorhanden sein.

### <a name="run-the-windows-powershell-command"></a>Ausführen des PowerShell-Befehls

1. Bei Aufforderung durch Windows PowerShell geben Sie das folgende Cmdlet ein, oder kopieren und fügen Sie es ein, und drücken Sie die EINGABETASTE:<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>Dabei entspricht *MyAlias* Ihrem Benutzeralias.<br/>

2. Warten Sie, bis die Windows PowerShell-Eingabeaufforderung wieder erscheint. Dies kann einige Minuten dauern.<br/>

3. Bei Aufforderung durch Windows PowerShell geben Sie das folgende Cmdlet ein, oder kopieren und fügen Sie es ein, und drücken Sie die EINGABETASTE:<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. Beachten Sie die neue Websitesammlungen in der Liste. Sie sollten die folgenden Websitesammlungen finden Sie unter: **Contosotest**, **TeamSite01**, **Blog01**und **Project01**

Fertig! Sie haben mehrere Websitesammlungen mit der erstellten CSV-Datei und ein einziges Windows PowerShell-Cmdlet erstellt. Sie können jetzt Benutzer erstellen und diesen Websites zuweisen.

## <a name="step-2-add-users-and-groups"></a>Schritt 2: Hinzufügen von Benutzern und Gruppen

Sie werden nun Benutzer erstellen und sie zu einer Websitesammlungsgruppe hinzufügen. Sie werden danach mithilfe einer .csv-Datei große Mengen an neuen Gruppen und Benutzern hochladen.

Für die folgenden Verfahren wird davon ausgegangen, dass Sie die Websitesammlungen contosotest, TeamSite01, Blog01 und Project01 erfolgreich erstellt haben.

### <a name="create-csv-and-ps1-files"></a>Erstellen von CSV und ps1-Dateien

1. Öffnen Sie den Editor und fügen Sie den folgenden Textblock ein:<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>*Mandanten* , in Ihrem Mandantennamen entspricht.<br/>

2. Speichern Sie die Datei auf Ihrem Desktop als **GroupsAndPermissions.csv**.<br/>

3. Öffnen Sie eine neue Instanz von Notepad und fügen Sie den folgenden Textblock ein:<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>*Mandanten* entspricht Ihrem Mandantennamen wobei *Username* entspricht dem Benutzernamen eines vorhandenen Benutzers.<br/>

4. Speichern Sie die Datei auf Ihrem Desktop als **Users.csv**.<br/>

5. Öffnen Sie eine neue Instanz von Notepad und fügen Sie den folgenden Textblock ein:<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>MyAlias entspricht, in dem der Benutzername des Benutzers, der derzeit angemeldet ist.<br/>

6. Speichern Sie die Datei auf Ihrem Desktop als **usersandgroups. ps1**. Dies ist eine einfache Windows PowerShell-Skripts.

Sie können jetzt das Skript UsersAndGroup.ps1 durchlaufen lassen, um Benutzer und Gruppen zu mehreren Websitesammlungen hinzuzufügen.

### <a name="run-usersandgroupsps1-script"></a>Ausführen von Skript UsersAndGroups.ps1

1. Gehen Sie zurück zu der SharePoint Online-Verwaltungsshell.<br/>
2. Bei Aufforderung durch Windows PowerShell geben sie die folgende Zeile ein, oder kopieren und fügen Sie sie ein, und drücken Sie die EINGABETASTE:<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. Drücken Sie zur Bestätigung aufgefordert **Y**ein.<br/>

4. Bei Aufforderung durch Windows PowerShell geben Sie Folgendes ein oder kopieren und fügen es ein, und drücken Sie die EINGABETASTE:<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>*MyAlias* entspricht, in dem Ihr Benutzername.<br/>

5. Warten Sie, bis die Eingabeaufforderung wieder erscheint, bevor Sie fortfahren. Zuerst werden Sie die Gruppen sehen, sobald diese erstellt sind. Sobald Benutzer hinzugefügt werden, sehen Sie wiederholt die Gruppenliste.

## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Verwalten von SharePoint Online-Websitegruppen Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

