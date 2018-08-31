---
title: Optimieren der Leistung von Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Sie zum Verbessern der Leistung von Exchange Online informieren.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541087"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="0067a-103">Optimieren der Leistung von Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0067a-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="0067a-p101">Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Sie zum Verbessern der Leistung von Exchange Online informieren. Dieser Artikel ist Teil des Projekts [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="0067a-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="0067a-106">Beachten Sie, um Verbessern der Leistung von Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0067a-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="0067a-107">Zur Verbesserung der Geschwindigkeit der Migration und zur Reduzierung der bandbreiteneinschränkungen Ihrer Organisation für Exchange Online, berücksichtigen Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="0067a-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="0067a-p102">**Verringern Sie die Größe von Postfächern.** Eine geringere Postfachgröße erhöht die Migrationsgeschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="0067a-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="0067a-p103">**Verwenden Sie die Funktionen zur Postfachverschiebung bei einer Exchange-Hybridbereitstellung.** Bei einer Exchange-Hybridbereitstellung erfordert Offline-E-Mail (in Form von OST-Dateien) kein erneutes Herunterladen, wenn zu Exchange Online migriert wird. Damit werden Ihre Bandbreitenanforderungen für Downloads erheblich reduziert.</span><span class="sxs-lookup"><span data-stu-id="0067a-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="0067a-p104">**Planen Sie das Verschieben von Postfächern für Zeiten mit geringem Datenverkehr aus dem Internet und geringer lokaler Exchange-Nutzung ein.** Bei der Planung von Verschiebungen werden Migrationsanforderungen an den Postfachreplikationsproxy gesendet, und die Anforderungen erfolgen möglicherweise nicht sofort.</span><span class="sxs-lookup"><span data-stu-id="0067a-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="0067a-p105">**Schlanke Popouts für Outlook im Web verwenden.** Schlanke Popouts bieten beträgt, weniger Arbeitsspeicher-Intensive Versionen von bestimmten e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer durch einige Komponenten auf dem Server rendern. Weitere Informationen finden Sie unter [schlanke Popouts verwenden, um Arbeitsspeicher zu reduzieren beim Lesen von e-Mail-Nachrichten verwendet](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="0067a-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="0067a-118">Weitere Informationen zur Leistung von Exchange-Migration finden Sie unter [Office 365-migrationsleistung und bewährte Methoden](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="0067a-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

