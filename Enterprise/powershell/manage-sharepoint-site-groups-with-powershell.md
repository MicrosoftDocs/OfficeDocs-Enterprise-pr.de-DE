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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="d2fe0-103">Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2fe0-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="d2fe0-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="d2fe0-105">Obwohl Sie das Office 365 Administrationscenter verwenden können, können Sie auch Office 365 PowerShell zum Verwalten von Ihrer SharePoint Online-Website verwenden.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d2fe0-106">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-106">Before you begin</span></span>

<span data-ttu-id="d2fe0-p101">Die Verfahren in diesem Artikel müssen Sie mit SharePoint Online herstellen. Anweisungen finden Sie unter [Connect to SharePoint Online-PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="d2fe0-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="d2fe0-109">Ansicht SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2fe0-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="d2fe0-p102">Die SharePoint Online-Verwaltungskonsole enthält einige leicht zu bedienende-Methoden zum Verwalten von Websitegruppen. Nehmen wir beispielsweise an, die Sie an die Gruppen und Mitglieder der Gruppe suchen möchten die https://litwareinc.sharepoint.com/sites/finance Website. Nachfolgend finden Sie müssen Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="d2fe0-113">Klicken Sie im Office 365 Admin Center auf **Ressourcen** > **Websites**, und klicken Sie dann auf die URL der Website.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="d2fe0-114">Klicken Sie im Dialogfeld Website-Auflistung auf **Gehe zu dieser Website**.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="d2fe0-115">Klicken Sie auf das Symbol **Einstellungen** (befindet sich in der oberen rechten Ecke der Seite), und klicken Sie dann auf **websiteeinstellungen**, auf der Websiteseite:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="d2fe0-116">![SharePoint Online-websiteeinstellungen](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="d2fe0-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="d2fe0-117">Klicken Sie auf der Seite Websiteeinstellungen unter **Benutzer und Berechtigungen**auf **Berechtigungen für Websites** .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="d2fe0-118">Wiederholen Sie dieses Verfahren für die nächste gewünschte Website.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="d2fe0-119">Verwenden Sie zum Abrufen einer Liste mit Gruppen mithilfe von Office 365 PowerShell den folgenden Befehlssatz:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="d2fe0-120">Es gibt zwei Methoden zum Ausführen dieses Befehls in der Befehlszeile SharePoint Online-Verwaltungsshell festgelegt:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>
- <span data-ttu-id="d2fe0-p103">Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , wählen Sie die Befehle aus, und fügen Sie sie in der Befehlszeile SharePoint Online-Verwaltungsshell. Wenn Sie dies tun, PowerShell stoppt bei einer >> Aufforderung. Drücken Sie die EINGABETASTE, um das Ausführen der für jeden Befehl.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a >> prompt. Press Enter to execute the for each command.</span></span></br>
- <span data-ttu-id="d2fe0-p104">Kopieren Sie die Befehle in Notepad (oder einem anderen Texteditor), ändern Sie den Wert der Variablen **$siteURL** , und speichern Sie diese Datei mit dem Namen und die Erweiterung. ps1 in einem geeigneten Ordner. Führen Sie im nächsten Schritt das Skript über die Befehlszeile SharePoint Online-Verwaltungsshell durch Angeben des Namens Pfad und den Dateinamen. Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example:</span></span></br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
<span data-ttu-id="d2fe0-127">$x = Get-SPOSite Foreach ($y in $x) {Write-Host $y.Url - ForegroundColor "Gelb" $z = Get-SPOSiteGroup-Website $y.Url Foreach ($ein in $z) {$b = Get-SPOSiteGroup-Site-$y.Url-Gruppe $a.Title Write-Host $b.Title - ForegroundColor "Cyan" $b | Select-Object - ExpandProperty Benutzer Write-Host}}</span><span class="sxs-lookup"><span data-stu-id="d2fe0-127">$x = Get-SPOSite foreach ($y in $x) { Write-Host $y.Url -ForegroundColor "Yellow" $z = Get-SPOSiteGroup -Site $y.Url foreach ($a in $z) { $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title Write-Host $b.Title -ForegroundColor "Cyan" $b | Select-Object -ExpandProperty Users Write-Host } }</span></span>
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

