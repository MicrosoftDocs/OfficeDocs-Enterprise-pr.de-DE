---
title: Optimieren der Leistung von Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Ihnen mitteilen, wie Sie die Leistung von Exchange Online verbessern.
ms.openlocfilehash: d736568687da5ffe0ebed5a57a6afa6f93173c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070351"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="707b3-103">Optimieren der Leistung von Exchange Online</span><span class="sxs-lookup"><span data-stu-id="707b3-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="707b3-104">Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Ihnen mitteilen, wie Sie die Leistung von Exchange Online verbessern, insbesondere vor einer Migration.</span><span class="sxs-lookup"><span data-stu-id="707b3-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="707b3-105">Dieser Artikel ist Teil des Projekts [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="707b3-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="707b3-106">Zu berücksichtigende Aspekte für die Verbesserung der Leistung von Exchange Online</span><span class="sxs-lookup"><span data-stu-id="707b3-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="707b3-107">Berücksichtigen Sie Folgendes, um die Migrations Geschwindigkeit zu verbessern und die Bandbreiteneinschränkungen Ihrer Organisation für Exchange Online zu verringern:</span><span class="sxs-lookup"><span data-stu-id="707b3-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="707b3-108">**Verringern der Postfachgröße.**</span><span class="sxs-lookup"><span data-stu-id="707b3-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="707b3-109">Geringere Postfachgröße verbessert die Migrations Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="707b3-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="707b3-110">**Verwenden Sie die Post Fach Verschiebungsfunktionen in einer Exchange-hybridbereitstellung.**</span><span class="sxs-lookup"><span data-stu-id="707b3-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="707b3-111">Bei einer Exchange-hybridbereitstellung werden offline-e-Mails (in der Form von. Ost-Dateien) erfordert keinen erneuten Download bei der Migration zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="707b3-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="707b3-112">Dadurch werden die Anforderungen an die Download Bandbreite deutlich reduziert.</span><span class="sxs-lookup"><span data-stu-id="707b3-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="707b3-113">**Planen Sie die Postfachverschiebungen in Zeiten mit niedrigem Internet Datenverkehr und einer niedrigen lokalen Exchange-Verwendung.**</span><span class="sxs-lookup"><span data-stu-id="707b3-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="707b3-114">Bei der Planung von Verschiebungen werden Migrationsanforderungen an den Replikations Proxy übermittelt und werden möglicherweise nicht sofort ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="707b3-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="707b3-115">**Verwenden Sie Lean Popouts für Outlook im Web.**</span><span class="sxs-lookup"><span data-stu-id="707b3-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="707b3-116">Lean Popouts bieten kleinere, weniger speicherintensive Versionen bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer, indem Sie einige Komponenten auf dem Server rendern.</span><span class="sxs-lookup"><span data-stu-id="707b3-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="707b3-117">Weitere Informationen finden Sie unter [Verwenden von Lean-Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="707b3-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="707b3-118">Allgemeine Ratschläge</span><span class="sxs-lookup"><span data-stu-id="707b3-118">General advice</span></span>

- <span data-ttu-id="707b3-119">Stellen Sie sicher, dass die DNS-Suche für Outlook.Office.com in das MS-Datencenter an einem logischen Eingabespeicherort für Ihren Standort gelangt.</span><span class="sxs-lookup"><span data-stu-id="707b3-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="707b3-120">Recherchieren Sie das Zwischenspeichern von Postfächern, und wählen Sie die entsprechenden Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="707b3-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="707b3-121">zwischen Speicherungszeitraum, Zwischenspeicherung für freigegebene Postfächer usw.).</span><span class="sxs-lookup"><span data-stu-id="707b3-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="707b3-122">Halten Sie Ihre Outlook-Daten von der Übergabe von VPN-Verbindungen (an eine zentrale) ab, bevor Sie über das Internet übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="707b3-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="707b3-123">Stellen Sie sicher, dass die Postfachdaten den Einschränkungen für Ordner und Element, Beträge entsprechen.</span><span class="sxs-lookup"><span data-stu-id="707b3-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="707b3-124">Weitere Informationen zur Exchange-Migrationsleistung finden Sie unter [Office 365-Migrationsleistung und bewährte Methoden](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="707b3-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

