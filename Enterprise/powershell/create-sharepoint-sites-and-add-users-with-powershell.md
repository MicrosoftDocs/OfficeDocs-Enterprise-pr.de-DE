---
title: Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell
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
description: 'Zusammenfassung: Verwenden von Office 365 PowerShell, erstellen Sie neue SharePoint Online-Websites, und fügen Sie Benutzer und Gruppen auf diese Websites.'
ms.openlocfilehash: 0a0438917f6e7010b56703ce0bf73e89e1db0533
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden von Office 365 PowerShell neue SharePoint Online-Websites erstellen, und fügen Sie Benutzer und Gruppen auf diese Websites.

Wenn Sie Office 365 PowerShell zum Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern verwenden, können Sie schnell und wiederholt Aufgaben ausführen viel schneller als Sie in der Office-356-Verwaltungskonsole können. Sie können auch Aufgaben ausführen, die nicht möglich, in der Verwaltungskonsole Office 356 auszuführen sind. 

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Die Verfahren in diesem Thema müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>Schritt 1: Erstellen neuer Websitesammlungen mithilfe von Office 365 PowerShell

Erstellen Sie mehrere Websites mithilfe von Office 365 PowerShell und einer CSV-Datei, die Sie mithilfe des gelieferten Beispielcodes und Notepad erstellen. Hierzu ersetzen Sie die in Klammern stehende Platzhalter-Information durch Ihre eigenen Website- und Mandant-spezifischen Informationen. Auf diese Weise können Sie eine einzelne Datei erstellen und einen einzigen Office 365 PowerShell-Befehl ausführen, der diese Datei verwendet. Die durchgeführten Maßnahmen sind sowohl wiederholbar als auch tragbar und es werden viele, wenn nicht alle Fehler vermieden, die durch die Eingabe der Befehle in die SharePoint Online-Verwaltungsshell entstehen können. Dieses Verfahren lässt sich in zwei Teile aufteilen. Sie erstellen zuerst eine .csv-Datei, danach referenzieren Sie diese CSV-Datei mithilfe von Office 365 PowerShell, das mithilfe deren Inhalte die Websites erstellt.

Das Office 365 PowerShell-Cmdlet importiert die CSV-Datei und leitet sie so, dass sie in die Schleife in den runden Klammern passt, die die erste Zeile der Datei als Spaltenkopf liest. Das Office 365 PowerShell-Cmdlet arbeitet sich dann durch die restlichen Datensätze, erstellt eine neue Websitesammlung für jeden Datensatz und weist Eigenschaften der Websitesammlung gemäß den Spaltenköpfen zu.

###<a name="create-a-csv-file"></a>Erstellen einer CSV-Datei

1. Öffnen Sie den Editor und fügen Sie den folgenden Textblock ein:</br>
```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```</br>Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</br>(You can press Ctrl+H when you use Notepad to bulk replace faster.)</br>
2. Save the file on your desktop as **SiteCollections.csv**.

 > [!TIP]
> Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.

### Run the Windows PowerShell command

1. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {neue-SPOSite-Besitzer $_. Besitzer - StorageQuota $_. StorageQuota-Url $_. URL - NoWait - ResourceQuota $_. ResourceQuota-Vorlage $_. Vorlage - TimeZoneID $_. TimeZoneID-Titel $_. Name}
```
</br>Where *MyAlias* equals your user alias.</br>
2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</br>
3. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Get-SPOSite-detaillierte | Format-Table - AutoSize-Eigenschaft
```</br>
4. Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**.

That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.

## Step 2: Add users and groups

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.

### Create .csv and .ps1 files

1. Open Notepad, and paste the following text block into it:</br>
```
Website, Gruppe, PermissionLevels https://tenant.sharepoint.com/sites/contosotest, "Contoso" Project Leads Vollzugriff https://tenant.sharepoint.com/sites/contosotest, Contoso-Auditoren nur anzeigen https://tenant.sharepoint.com/sites/contosotest, Contoso-Designern Design https://tenant.sharepoint.com/sites/TeamSite01, XT1000 Teamleiter, Vollzugriff https://tenant.sharepoint.com/sites/TeamSite01, XT1000 Berater bearbeiten https://tenant.sharepoint.com/sites/Blog01, Contoso-Blog Design-Designern https://tenant.sharepoint.com/sites/Blog01, Contoso-Blog-Editoren bearbeiten https://tenant.sharepoint.com/sites/Project01, Project Alpha genehmigende Personen, Vollzugriff
```
</br>Where *tenant* equals your tenant name.</br>
2. Save the file to your desktop as **GroupsAndPermissions.csv**.</br>
3. Open a new instance of Notepad, and paste the following text block into it:</br>
```
Gruppe LoginName, Site "Contoso" Project Leads username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso Auditoren, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso Designern, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest XT1000 Teamleiter, UserName@Tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 XT1000 Berater, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 Contoso-Blog-Designern, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Contoso-Blog-Editoren, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Projekt Alpha genehmigende Personen, username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
</br>Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</br>
4. Save the file to your desktop as **Users.csv**.</br>
5. Open a new instance of Notepad, and paste the following text block into it:</br>
```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {neue-SPOSiteGroup-$_gruppieren. Gruppieren - PermissionLevels $_. PermissionLevels-Site $_. Import-Csv-C:\users\MyAlias\desktop\Users.csv Site} | wobei {Add-SPOUser-Gruppe $_. Gruppieren Sie – LoginName $_ LoginName-Site $_. Site}
```
</br>Where MyAlias equals the user name of the user that is currently logged on.</br>
6. Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.

You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.

### Run UsersAndGroups.ps1 script

1. Return to the SharePoint Online Management Shell.</br>
2. At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</br>
```
Set-ExecutionPolicy umgehen
```</br>
3. At the confirmation prompt, press **Y**.</br>
4. At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</br>
```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
</br>Where *MyAlias* equals your user name.</br>
5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Manage SharePoint Online site groups Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

