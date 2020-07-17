---
title: Internetwebsites in Microsoft Azure mit SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 'Zusammenfassung: Internetwebsites, die SharePoint Server 2013 nutzen, profitieren, wenn sie in Azure-Infrastrukturdiensten gehostet werden. Dieser Artikel bietet Ressourcen für den Entwurf und die Implementierung dieser Lösung.'
ms.openlocfilehash: fa01df6903a9cbc2ec6163514f27a6bd2fd603aa
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998117"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="95f52-104">Internetwebsites in Microsoft Azure mit SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="95f52-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="95f52-105">Internet Websites, die SharePoint Server 2013 nutzen, indem Sie in Azure-Infrastrukturdiensten gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="95f52-105">Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services.</span></span> <span data-ttu-id="95f52-106">Dieser Artikel bietet Ressourcen für den Entwurf und die Implementierung dieser Lösung.</span><span class="sxs-lookup"><span data-stu-id="95f52-106">This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="95f52-107">Verwenden von Windows Azure-Infrastrukturdiensten für Internetwebsites</span><span class="sxs-lookup"><span data-stu-id="95f52-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="95f52-p103">Microsoft Azure bietet eine überzeugende Möglichkeit für das Hosting von Internetwebsites, die auf SharePoint Server 2013 basieren. Es ergeben sich folgende Vorteile:</span><span class="sxs-lookup"><span data-stu-id="95f52-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="95f52-110">Konzentration auf die Entwicklung einer überzeugenden Website anstatt auf den Aufbau von Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="95f52-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="95f52-111">Flexibilität bei der Skalierung der Lösung entsprechend der Nachfrage</span><span class="sxs-lookup"><span data-stu-id="95f52-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="95f52-112">Gebühren ausschließlich für die Ressourcen, die Sie benötigen und verwenden</span><span class="sxs-lookup"><span data-stu-id="95f52-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="95f52-113">Nutzung von Azure Active Directory für Kundenkonten</span><span class="sxs-lookup"><span data-stu-id="95f52-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="95f52-114">Hinzufügen von Features, die derzeit in Microsoft 365 nicht verfügbar sind, beispielsweise Deep Reporting und Analyse.</span><span class="sxs-lookup"><span data-stu-id="95f52-114">Add features that are not currently available in Microsoft 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="95f52-115">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="95f52-115">Resources</span></span>

<span data-ttu-id="95f52-116">Die folgenden technischen Abbildungen und Artikel bieten Informationen zum Entwerfen und Implementieren von Internetwebsites in Azure mit SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="95f52-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="95f52-117">**Ressource**</span><span class="sxs-lookup"><span data-stu-id="95f52-117">**Resource**</span></span>|<span data-ttu-id="95f52-118">**Weitere Informationen**</span><span class="sxs-lookup"><span data-stu-id="95f52-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="95f52-119">**SharePoint Server 2013-Internetwebsites in Azure**</span><span class="sxs-lookup"><span data-stu-id="95f52-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="95f52-120">[![Bild der Internetwebsites in Azure mit SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="95f52-120">[![Image of Internet sites in Azure using SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="95f52-121">[PDF-Datei](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="95f52-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="95f52-122">Dieses Architekturmodell zeigt wichtige Entwurfsaktivitäten und empfohlene Architekturentscheidungen für Internetwebsites in Azure.</span><span class="sxs-lookup"><span data-stu-id="95f52-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="95f52-123">**Entwurfsbeispiel: Internetwebsites in Azure für SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="95f52-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="95f52-124">[![Bild des Entwurfsbeispiels: Internetwebsites in Microsoft Azure für SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="95f52-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="95f52-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="95f52-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="95f52-126">Verwenden Sie dieses Entwurfsbeispiel als Ausgangspunkt für Ihre eigene Architektur.</span><span class="sxs-lookup"><span data-stu-id="95f52-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="95f52-127">**[Microsoft Azure-Architekturen für SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="95f52-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="95f52-128">In diesem Artikel wird beschrieben, wie Sie Azure-Architekturen zum Hosten von SharePoint-Lösungen entwerfen.</span><span class="sxs-lookup"><span data-stu-id="95f52-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="95f52-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="95f52-129">See Also</span></span>

[<span data-ttu-id="95f52-130">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="95f52-130">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)



