---
title: Verringern des beim Lesen von e-Mail-Nachrichten verwendeten Arbeitsspeichers mithilfe von Lean Popouts
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Internet.
ms.openlocfilehash: a9070d9aefc8e4c223667848b4af5c06518de076
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616808"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="887ba-103">Verringern des beim Lesen von e-Mail-Nachrichten verwendeten Arbeitsspeichers mithilfe von Lean Popouts</span><span class="sxs-lookup"><span data-stu-id="887ba-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="887ba-104">Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Internet.</span><span class="sxs-lookup"><span data-stu-id="887ba-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="887ba-105">Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) -Projekt.</span><span class="sxs-lookup"><span data-stu-id="887ba-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="887ba-106">Als Office 365 globaler Administrator können Sie Outlook im Internet so konfigurieren, dass es *schlanke Popouts* , eine kleinere, weniger arbeitsspeicherintensive Version bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="887ba-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="887ba-107">Wenn Lean Popouts für Outlook im Internet konfiguriert sind, werden serverseitige gerenderte Komponenten geladen, die die Leistung optimieren.</span><span class="sxs-lookup"><span data-stu-id="887ba-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="887ba-108">Seit März 2018 stehen Lean-Popouts derzeit nicht für Nachrichten zur Verfügung, die Nutzungsrechte Einschränkungen angeben, beispielsweise IRM (Information Rights Management, Verwaltung von Informationsrechten).</span><span class="sxs-lookup"><span data-stu-id="887ba-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="887ba-109">Diese Features funktionieren weiterhin im Hauptfenster, stehen aber in Lean Popouts nicht zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="887ba-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="887ba-110">Outlook-Add-Ins</span><span class="sxs-lookup"><span data-stu-id="887ba-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="887ba-111">Skype for Business Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="887ba-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="887ba-112">**So konfigurieren Sie Lean Popouts für alle Benutzer in Ihrer Office 365 Organisation**</span><span class="sxs-lookup"><span data-stu-id="887ba-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="887ba-113">Stellen [Sie mithilfe von Remote-PowerShell eine Verbindung zu Exchange Online her](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="887ba-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="887ba-114">Führen Sie das Cmdlet " [OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) " mit dem Parameter "LeanPopoutEnabled" wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="887ba-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="887ba-115">Um beispielsweise Lean Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="887ba-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="887ba-116">So deaktivieren Sie Lean Popouts für alle Benutzer in Ihrer Organisation:</span><span class="sxs-lookup"><span data-stu-id="887ba-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


