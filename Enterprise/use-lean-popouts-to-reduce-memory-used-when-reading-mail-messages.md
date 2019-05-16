---
title: Verwenden von Lean Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Web.
ms.openlocfilehash: 344047363bd58850fcd08a7f8f2fd46de757668c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070561"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="c9106-103">Verwenden von Lean Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="c9106-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="c9106-104">Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Web.</span><span class="sxs-lookup"><span data-stu-id="c9106-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="c9106-105">Dieser Artikel ist Teil des Projekts [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="c9106-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="c9106-106">Als globaler Office 365-Administrator können Sie Outlook im Web so konfigurieren, dass *Lean Popouts* , eine kleinere, weniger speicherintensive Version bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer, bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="c9106-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="c9106-107">Wenn Lean-Popouts für Outlook im Web konfiguriert sind, werden serverseitige gerenderte Komponenten geladen, die die Leistung optimieren.</span><span class="sxs-lookup"><span data-stu-id="c9106-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="c9106-108">Ab März 2018 sind Lean-Popouts derzeit nicht für Nachrichten verfügbar, die Nutzungsrechte Einschränkungen wie Information Rights Management (IRM) angeben.</span><span class="sxs-lookup"><span data-stu-id="c9106-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="c9106-109">Diese Features funktionieren weiterhin im Hauptfenster, sind jedoch nicht in Lean Popouts verfügbar:</span><span class="sxs-lookup"><span data-stu-id="c9106-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="c9106-110">Outlook-Add-Ins</span><span class="sxs-lookup"><span data-stu-id="c9106-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="c9106-111">Skype for Business-Anwesenheit</span><span class="sxs-lookup"><span data-stu-id="c9106-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="c9106-112">**So konfigurieren Sie Lean-Popouts für alle Benutzer in Ihrer Office 365-Organisation**</span><span class="sxs-lookup"><span data-stu-id="c9106-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="c9106-113">[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="c9106-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="c9106-114">Führen Sie das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) mit dem Parameter LeanPopoutEnabled wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="c9106-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="c9106-115">Um beispielsweise Lean-Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="c9106-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="c9106-116">So deaktivieren Sie Lean-Popouts für alle Benutzer in Ihrer Organisation:</span><span class="sxs-lookup"><span data-stu-id="c9106-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


