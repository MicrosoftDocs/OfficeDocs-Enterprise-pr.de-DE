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
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.'
ms.openlocfilehash: 04df780732913eaaf80d9bca64db5174089ed80b
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573909"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="91721-103">Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="91721-104">**Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Verwalten von SharePoint Online-Websitegruppen.</span><span class="sxs-lookup"><span data-stu-id="91721-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="91721-105">Obwohl Sie das Microsoft 365 Admin Center verwenden können, können Sie auch Office 365 PowerShell verwenden, um Ihre SharePoint Online-Websitegruppen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="91721-105">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="91721-106">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="91721-106">Before you begin</span></span>

<span data-ttu-id="91721-107">Bei den Verfahren in diesem Artikel müssen Sie eine Verbindung mit SharePoint Online herstellen.</span><span class="sxs-lookup"><span data-stu-id="91721-107">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="91721-108">Weitere Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="91721-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="91721-109">Anzeigen von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="91721-110">Das SharePoint Online Admin Center verfügt über einige benutzerfreundliche Methoden zum Verwalten von Websitegruppen.</span><span class="sxs-lookup"><span data-stu-id="91721-110">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="91721-111">Angenommen, Sie möchten die Gruppen und die Gruppenmitglieder für die `https://litwareinc.sharepoint.com/sites/finance` Website ansehen.</span><span class="sxs-lookup"><span data-stu-id="91721-111">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="91721-112">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="91721-112">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="91721-113">klicken sie im Microsoft 365 admin center auf **ressourcen** > **websites**, und klicken sie dann auf die URL der website.</span><span class="sxs-lookup"><span data-stu-id="91721-113">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="91721-114">Klicken Sie im Dialogfeld -Websitesammlung auf **Zu dieser Website wechseln**.</span><span class="sxs-lookup"><span data-stu-id="91721-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="91721-115">Klicken Sie auf dieser Seite auf das Symbol **Einstellungen** (oben rechts auf der Seite) und dann auf **Websiteeinstellungen**:</span><span class="sxs-lookup"><span data-stu-id="91721-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="91721-116">![SharePoint Online-Websiteeinstellungen](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="91721-116">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="91721-117">Klicken Sie auf der Seite Websiteeinstellungen**Benutzer und Berechtigungen** auf **Websiteberechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="91721-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="91721-118">Wiederholen Sie dieses Verfahren für die nächste gewünschte Website.</span><span class="sxs-lookup"><span data-stu-id="91721-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="91721-119">Verwenden Sie zum Abrufen einer Liste mit Gruppen mithilfe von Office 365 PowerShell den folgenden Befehlssatz:</span><span class="sxs-lookup"><span data-stu-id="91721-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="91721-120">Es gibt zwei Möglichkeiten zum Ausführen dieses Befehlssatzes in der SharePoint Online-Verwaltungsshell-Eingabeaufforderung:</span><span class="sxs-lookup"><span data-stu-id="91721-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="91721-121">Kopieren Sie die Befehle in Notepad (oder einen anderen Text-Editor), ändern Sie den Wert der **$SiteUrl** -Variablen, wählen Sie die Befehle aus, und fügen Sie Sie in die SharePoint Online-Verwaltungsshell-Eingabeaufforderung ein.</span><span class="sxs-lookup"><span data-stu-id="91721-121">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="91721-122">Wenn Sie dies tun, wird PowerShell an einer **>>** Ansage angehalten.</span><span class="sxs-lookup"><span data-stu-id="91721-122">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="91721-123">Drücken Sie die EINGABETASTE, um den **Foreach**-Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="91721-123">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="91721-124">Kopieren Sie die Befehle in Editor (oder einen anderen Text-Editor), ändern Sie den Wert der **$siteURL**Variable, und speichern Sie dann diese Textdatei mit einem Namen und der Erweiterung „.ps1“ in einem geeigneten Ordner.</span><span class="sxs-lookup"><span data-stu-id="91721-124">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="91721-125">Führen Sie als nächstes das Skript über die Eingabeaufforderung der SharePoint Online-Verwaltungsshell aus, indem Sie den Pfad und den Dateinamen angeben.</span><span class="sxs-lookup"><span data-stu-id="91721-125">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="91721-126">Nachfolgend sehen Sie einen Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="91721-126">Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="91721-127">In beiden Fällen wird Folgendes angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91721-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online-Websitegruppen](media/SPO-site-groups.png)

<span data-ttu-id="91721-129">Hierbei handelt es sich um alle Gruppen, die für die Website `https://litwareinc.sharepoint.com/sites/finance`erstellt wurden, und alle Benutzer, die diesen Gruppen zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="91721-129">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="91721-130">Die Gruppennamen werden in gelb dargestellt, damit Sie die Gruppennamen von den Mitgliedern leicht unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="91721-130">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="91721-131">Ein weiteres Beispiel ist ein Befehlssatz, in dem die Gruppen und alle Gruppenmitgliedschaften für alle SharePoint Online-Websites aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="91721-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="91721-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="91721-132">See also</span></span>

[<span data-ttu-id="91721-133">Herstellen einer Verbindung mit SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="91721-134">Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="91721-135">Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="91721-136">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="91721-137">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91721-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

