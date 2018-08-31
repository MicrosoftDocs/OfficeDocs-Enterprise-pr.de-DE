---
title: Verwenden Sie schlanke Popouts zur Reduzierung der Arbeitsspeicher, die beim Lesen von e-Mail-Nachrichten verwendet
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachricht Download in Outlook im Web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540797"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="65e3d-103">Verwenden Sie schlanke Popouts zur Reduzierung der Arbeitsspeicher, die beim Lesen von e-Mail-Nachrichten verwendet</span><span class="sxs-lookup"><span data-stu-id="65e3d-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="65e3d-p101">Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachricht Download in Outlook im Web. Dieser Artikel ist Teil des Projekts [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="65e3d-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="65e3d-p102">Als globaler Office 365-Administrator können Sie Outlook im Web zur Bereitstellung von *schlanke Popouts* , eine kleinere, weniger Arbeitsspeicher-Intensive Version von bestimmten e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer konfigurieren. Wenn schlanke Popouts für Outlook im Web konfiguriert werden, werden serverseitige Komponenten gerendert geladen, die Leistung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="65e3d-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="65e3d-108">Ab März 2018 sind schlanke Popouts derzeit nicht verfügbar für Nachrichten, die Verwendung Rechte Einschränkungen, wie etwa Information Rights Management (IRM) angeben.</span><span class="sxs-lookup"><span data-stu-id="65e3d-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="65e3d-109">Diese Features sind weiterhin im Hauptfenster von funktionsfähig sind jedoch nicht verfügbar in schlanke Popouts:</span><span class="sxs-lookup"><span data-stu-id="65e3d-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="65e3d-110">Outlook-Add-Ins</span><span class="sxs-lookup"><span data-stu-id="65e3d-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="65e3d-111">Skype für Business Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="65e3d-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="65e3d-112">**So konfigurieren Sie schlanke Popouts für alle Benutzer in Office 365-Organisation**</span><span class="sxs-lookup"><span data-stu-id="65e3d-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="65e3d-113">[Verbindung mit Exchange Online mit Remote-PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="65e3d-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="65e3d-114">Führen Sie das Cmdlet " [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) " mit dem Parameter LeanPopoutEnabled wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="65e3d-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="65e3d-115">Wenn Sie beispielsweise schlanke Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="65e3d-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="65e3d-116">Schlanke Popouts für alle Benutzer in Ihrer Organisation zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="65e3d-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


