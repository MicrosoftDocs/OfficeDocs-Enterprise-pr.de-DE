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
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="5f8c2-103">Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="5f8c2-104">**Zusammenfassung:** Verwenden von Office 365 PowerShell neue SharePoint Online-Websites erstellen, und fügen Sie Benutzer und Gruppen auf diese Websites.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="5f8c2-p101">Wenn Sie Office 365 PowerShell zum Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern verwenden, können Sie schnell und wiederholt Aufgaben ausführen viel schneller als Sie in der Office-356-Verwaltungskonsole können. Sie können auch Aufgaben ausführen, die nicht möglich, in der Verwaltungskonsole Office 356 auszuführen sind.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="5f8c2-107">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-107">Before you begin</span></span>

<span data-ttu-id="5f8c2-p102">Die Verfahren in diesem Thema müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="5f8c2-110">Schritt 1: Erstellen neuer Websitesammlungen mithilfe von Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="5f8c2-p103">Erstellen Sie mehrere Websites mithilfe von Office 365 PowerShell und eine CSV-Datei, die Sie mit den bereitgestellten Beispielcode und im Editor erstellen. Für dieses Verfahren benötigen Sie die für Platzhalterinformationen in Klammern mit eigenen Website und Mandanten-spezifische Informationen ersetzen. Dieser Vorgang können Sie eine einzelne Datei zu erstellen, und führen Sie einen einzelnen Office 365 PowerShell-Befehl, der diese Datei verwendet. Dadurch wird die Aktionen wiederholbare und tragbaren und viele, wenn nicht alle Fehler, die lange Befehle in SharePoint Online-Verwaltungsshell eingeben stammen kann entfällt. Es gibt zwei Teile dieser Prozedur. Zuerst erstellen Sie eine CSV-Datei, und Sie werden von Office 365 PowerShell, der seinen Inhalt verwendet wird, um die Websites erstellen, CSV-Datei verweisen.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process lets you create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="5f8c2-p104">Das Office 365 PowerShell-Cmdlet importiert die CSV-Datei und leitet sie so, dass sie in die Schleife in den runden Klammern passt, die die erste Zeile der Datei als Spaltenkopf liest. Das Office 365 PowerShell-Cmdlet arbeitet sich dann durch die restlichen Datensätze, erstellt eine neue Websitesammlung für jeden Datensatz und weist Eigenschaften der Websitesammlung gemäß den Spaltenköpfen zu.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="5f8c2-119">Erstellen einer CSV-Datei</span><span class="sxs-lookup"><span data-stu-id="5f8c2-119">Create a .csv file</span></span>

1. <span data-ttu-id="5f8c2-120">Öffnen Sie den Editor und fügen Sie den folgenden Textblock ein:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="5f8c2-121">Wobei *Mandanten* ist der Name Ihres Mandanten und *Besitzer* ist der Benutzername des Benutzers bei Ihrem Mandanten, denen möchten Sie die Rolle des primären Websitesammlungsadministrators gewähren.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="5f8c2-122">(Sie können STRG + H drücken, wenn Sie zum Ersetzen schneller Massen-Editor verwenden.)</span><span class="sxs-lookup"><span data-stu-id="5f8c2-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="5f8c2-123">Speichern Sie die Datei auf Ihrem Desktop als **SiteCollections.csv**.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="5f8c2-p105">Bevor Sie diese oder andere CSV oder Windows PowerShell-Skriptdatei verwenden, ist es empfehlenswert, um sicherzustellen, dass keine zusätzlichen oder nicht druckbaren Zeichen vorhanden sind. Öffnen die Datei in Word, und klicken Sie im Menüband klicken Sie auf das Absatzsymbol nicht druckbare Zeichen angezeigt. Es sollten keine zusätzlichen nicht druckbaren Zeichen sein. Beispielsweise sollte keine Absatzmarken am Ende der Datei außer dem letzten vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="5f8c2-128">Ausführen des PowerShell-Befehls</span><span class="sxs-lookup"><span data-stu-id="5f8c2-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="5f8c2-129">Bei Aufforderung durch Windows PowerShell geben Sie das folgende Cmdlet ein, oder kopieren und fügen Sie es ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="5f8c2-130">Dabei entspricht *MyAlias* Ihrem Benutzeralias.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="5f8c2-p106">Warten Sie, bis die Windows PowerShell-Eingabeaufforderung wieder erscheint. Dies kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="5f8c2-133">Bei Aufforderung durch Windows PowerShell geben Sie das folgende Cmdlet ein, oder kopieren und fügen Sie es ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="5f8c2-p107">Beachten Sie die neue Websitesammlungen in der Liste. Sie sollten die folgenden Websitesammlungen finden Sie unter: **Contosotest**, **TeamSite01**, **Blog01**und **Project01**</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="5f8c2-p108">Fertig! Sie haben mehrere Websitesammlungen mit der erstellten CSV-Datei und ein einziges Windows PowerShell-Cmdlet erstellt. Sie können jetzt Benutzer erstellen und diesen Websites zuweisen.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="5f8c2-139">Schritt 2: Hinzufügen von Benutzern und Gruppen</span><span class="sxs-lookup"><span data-stu-id="5f8c2-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="5f8c2-p109">Sie werden nun Benutzer erstellen und sie zu einer Websitesammlungsgruppe hinzufügen. Sie werden danach mithilfe einer .csv-Datei große Mengen an neuen Gruppen und Benutzern hochladen.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="5f8c2-142">Für die folgenden Verfahren wird davon ausgegangen, dass Sie die Websitesammlungen contosotest, TeamSite01, Blog01 und Project01 erfolgreich erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="5f8c2-143">Erstellen von CSV und ps1-Dateien</span><span class="sxs-lookup"><span data-stu-id="5f8c2-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="5f8c2-144">Öffnen Sie den Editor und fügen Sie den folgenden Textblock ein:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="5f8c2-145">*Mandanten* , in Ihrem Mandantennamen entspricht.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="5f8c2-146">Speichern Sie die Datei auf Ihrem Desktop als **GroupsAndPermissions.csv**.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="5f8c2-147">Öffnen Sie eine neue Instanz von Notepad und fügen Sie den folgenden Textblock ein:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="5f8c2-148">*Mandanten* entspricht Ihrem Mandantennamen wobei *Username* entspricht dem Benutzernamen eines vorhandenen Benutzers.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="5f8c2-149">Speichern Sie die Datei auf Ihrem Desktop als **Users.csv**.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="5f8c2-150">Öffnen Sie eine neue Instanz von Notepad und fügen Sie den folgenden Textblock ein:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="5f8c2-151">MyAlias entspricht, in dem der Benutzername des Benutzers, der derzeit angemeldet ist.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="5f8c2-p110">Speichern Sie die Datei auf Ihrem Desktop als **usersandgroups. ps1**. Dies ist eine einfache Windows PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="5f8c2-154">Sie können jetzt das Skript UsersAndGroup.ps1 durchlaufen lassen, um Benutzer und Gruppen zu mehreren Websitesammlungen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="5f8c2-155">Ausführen von Skript UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="5f8c2-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="5f8c2-156">Gehen Sie zurück zu der SharePoint Online-Verwaltungsshell.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="5f8c2-157">Bei Aufforderung durch Windows PowerShell geben sie die folgende Zeile ein, oder kopieren und fügen Sie sie ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="5f8c2-158">Drücken Sie zur Bestätigung aufgefordert **Y**ein.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="5f8c2-159">Bei Aufforderung durch Windows PowerShell geben Sie Folgendes ein oder kopieren und fügen es ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="5f8c2-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="5f8c2-160">*MyAlias* entspricht, in dem Ihr Benutzername.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="5f8c2-p111">Warten Sie, bis die Eingabeaufforderung wieder erscheint, bevor Sie fortfahren. Zuerst werden Sie die Gruppen sehen, sobald diese erstellt sind. Sobald Benutzer hinzugefügt werden, sehen Sie wiederholt die Gruppenliste.</span><span class="sxs-lookup"><span data-stu-id="5f8c2-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f8c2-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5f8c2-164">See also</span></span>

[<span data-ttu-id="5f8c2-165">Herstellen einer Verbindung mit SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="5f8c2-166">Verwalten von SharePoint Online-Websitegruppen Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="5f8c2-167">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5f8c2-168">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f8c2-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

