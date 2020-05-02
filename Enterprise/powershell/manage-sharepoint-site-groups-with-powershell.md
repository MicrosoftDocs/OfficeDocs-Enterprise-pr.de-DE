---
title: Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um SharePoint Online Websitegruppen zu verwalten.'
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004198"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="d1627-103">Verwalten von SharePoint Online-Websitegruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="d1627-104">Obwohl Sie das Microsoft 365 Admin Center verwenden können, können Sie auch Office 365 PowerShell verwenden, um Ihre SharePoint Online Websitegruppen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="d1627-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d1627-105">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="d1627-105">Before you begin</span></span>

<span data-ttu-id="d1627-106">Für die Verfahren in diesem Artikel müssen Sie eine Verbindung mit SharePoint Online herstellen.</span><span class="sxs-lookup"><span data-stu-id="d1627-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="d1627-107">Weitere Anweisungen finden Sie unter [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="d1627-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="d1627-108">Anzeigen von SharePoint Online mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="d1627-109">Das SharePoint Online Admin Center verfügt über einige einfach zu verwendende Methoden zum Verwalten von Websitegruppen.</span><span class="sxs-lookup"><span data-stu-id="d1627-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="d1627-110">Nehmen wir beispielsweise an, Sie möchten die Gruppen und die Gruppenmitglieder für die `https://litwareinc.sharepoint.com/sites/finance` Website betrachten.</span><span class="sxs-lookup"><span data-stu-id="d1627-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="d1627-111">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="d1627-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="d1627-112">Klicken Sie im SharePoint Admin Center auf **aktive Websites**, und klicken Sie dann auf die URL der Website.</span><span class="sxs-lookup"><span data-stu-id="d1627-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="d1627-113">Klicken Sie auf der Seite Website auf das Symbol **Einstellungen** (befindet sich in der rechten oberen Ecke der Seite), und klicken Sie dann auf **Websiteberechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="d1627-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="d1627-114">Wiederholen Sie dieses Verfahren für die nächste gewünschte Website.</span><span class="sxs-lookup"><span data-stu-id="d1627-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="d1627-115">Wenn Sie eine Liste der Gruppen mit Office 365 PowerShell abrufen möchten, können Sie die folgenden Befehle verwenden:</span><span class="sxs-lookup"><span data-stu-id="d1627-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="d1627-116">Es gibt zwei Möglichkeiten zum Ausführen dieses Befehlssatzes in der Eingabeaufforderung der SharePoint Online Verwaltungsshell:</span><span class="sxs-lookup"><span data-stu-id="d1627-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="d1627-117">Kopieren Sie die Befehle in Notepad (oder einen anderen Text-Editor), ändern Sie den Wert der **$SiteUrl** -Variablen, wählen Sie die Befehle aus, und fügen Sie Sie dann in die Eingabeaufforderung der SharePoint Online Verwaltungsshell ein.</span><span class="sxs-lookup"><span data-stu-id="d1627-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="d1627-118">Wenn Sie dies tun, wird PowerShell an einer **>>** Eingabeaufforderung angehalten.</span><span class="sxs-lookup"><span data-stu-id="d1627-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="d1627-119">Drücken Sie die EINGABETASTE `foreach` , um den Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d1627-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="d1627-120">Kopieren Sie die Befehle in Editor (oder einen anderen Text-Editor), ändern Sie den Wert der **$siteURL**Variable, und speichern Sie dann diese Textdatei mit einem Namen und der Erweiterung „.ps1“ in einem geeigneten Ordner.</span><span class="sxs-lookup"><span data-stu-id="d1627-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="d1627-121">Führen Sie als nächstes das Skript über die Eingabeaufforderung der SharePoint Online Management Shell aus, indem Sie den Pfad und den Dateinamen angeben.</span><span class="sxs-lookup"><span data-stu-id="d1627-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="d1627-122">Nachfolgend sehen Sie einen Beispielbefehl:</span><span class="sxs-lookup"><span data-stu-id="d1627-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="d1627-123">In beiden Fällen wird Folgendes angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1627-123">In both cases, you should see something similar to this:</span></span>

![SharePoint Online Websitegruppen](media/SPO-site-groups.png)

<span data-ttu-id="d1627-125">Dies sind alle Gruppen, die für die Website `https://litwareinc.sharepoint.com/sites/finance`erstellt wurden, sowie alle Benutzer, die diesen Gruppen zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="d1627-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="d1627-126">Die Gruppennamen werden in gelb dargestellt, damit Sie die Gruppennamen von den Mitgliedern leicht unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="d1627-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="d1627-127">Ein weiteres Beispiel ist ein Befehlssatz, der die Gruppen und alle Gruppenmitgliedschaften für alle Ihre SharePoint Online Websites auflistet.</span><span class="sxs-lookup"><span data-stu-id="d1627-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
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
    
## <a name="see-also"></a><span data-ttu-id="d1627-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d1627-128">See also</span></span>

[<span data-ttu-id="d1627-129">Herstellen einer Verbindung mit SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="d1627-130">Erstellen von SharePoint Online-Websites und Hinzufügen von Benutzern mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="d1627-131">Verwalten von SharePoint Online-Benutzern und -Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="d1627-132">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d1627-133">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1627-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

