---
title: Internetwebsites in Microsoft Azure mit SharePoint Server 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: 'Zusammenfassung: Internetwebsites, die SharePoint Server 2013 nutzen, profitieren, wenn sie in Azure-Infrastrukturdiensten gehostet werden. Dieser Artikel bietet Ressourcen für den Entwurf und die Implementierung dieser Lösung.'
ms.openlocfilehash: a2444cdf98e861530131d55ae80fc661f730ba57
ms.sourcegitcommit: 9f57825b10f20e3813732372541128ef187d52c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "20161788"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="4bd5f-104">Internetwebsites in Microsoft Azure mit SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="4bd5f-104">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="4bd5f-p102">**Zusammenfassung:** Internetwebsites, die SharePoint Server 2013 nutzen, profitieren, wenn sie in Azure-Infrastrukturdienste gehostet werden. Dieser Artikel bietet Ressourcen für den Entwurf und die Implementierung dieser Lösung.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-p102">**Summary:** Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services. This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="4bd5f-107">Verwenden von Windows Azure-Infrastrukturdiensten für Internetwebsites</span><span class="sxs-lookup"><span data-stu-id="4bd5f-107">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="4bd5f-p103">Microsoft Azure bietet eine überzeugende Möglichkeit für das Hosting von Internetwebsites, die auf SharePoint Server 2013 basieren. Es ergeben sich folgende Vorteile:</span><span class="sxs-lookup"><span data-stu-id="4bd5f-p103">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="4bd5f-110">Konzentration auf die Entwicklung einer überzeugenden Website anstatt auf den Aufbau von Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="4bd5f-110">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="4bd5f-111">Flexibilität bei der Skalierung der Lösung entsprechend der Nachfrage</span><span class="sxs-lookup"><span data-stu-id="4bd5f-111">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="4bd5f-112">Gebühren ausschließlich für die Ressourcen, die Sie benötigen und verwenden</span><span class="sxs-lookup"><span data-stu-id="4bd5f-112">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="4bd5f-113">Nutzung von Azure Active Directory für Kundenkonten</span><span class="sxs-lookup"><span data-stu-id="4bd5f-113">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="4bd5f-114">Hinzufügung von Features, die derzeit nicht in Office 365 verfügbar, z. B. umfassende Berichterstellung und Analyse</span><span class="sxs-lookup"><span data-stu-id="4bd5f-114">Add features that are not currently available in Office 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="4bd5f-115">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4bd5f-115">Resources</span></span>

<span data-ttu-id="4bd5f-116">Die folgenden technischen Abbildungen und Artikel bieten Informationen zum Entwerfen und Implementieren von Internetwebsites in Azure mit SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-116">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="4bd5f-117">**Resource**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-117">**Resource**</span></span>|<span data-ttu-id="4bd5f-118">**Weitere Informationen**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-118">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4bd5f-119">**SharePoint Server 2013-Internetwebsites in Azure**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-119">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="4bd5f-120">[![Bild der Internetwebsites in Azure mit SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="4bd5f-120">[![Image of Internet sites in Azure using SharePoint](images/MS_AZ_SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="4bd5f-121">[PDF-Datei](https://go.microsoft.com/fwlink/p/?LinkId=392552) \| [           ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="4bd5f-121">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="4bd5f-122">Dieses Architekturmodell zeigt wichtige Entwurfsaktivitäten und empfohlene Architekturentscheidungen für Internetwebsites in Azure.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-122">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="4bd5f-123">**Entwurfsbeispiel: Internetwebsites in Azure für SharePoint Server 2013**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-123">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="4bd5f-124">[![Abbildung des Entwurfsbeispiels: Internetwebsites in Microsoft Azure für SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="4bd5f-124">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="4bd5f-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="4bd5f-125">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="4bd5f-126">Verwenden Sie dieses Entwurfsbeispiel als Ausgangspunkt für Ihre eigene Architektur.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-126">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="4bd5f-127">**[Microsoft Azure-Architekturen für SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-127">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="4bd5f-128">In diesem Artikel wird beschrieben, wie Sie Azure-Architekturen zum Hosten von SharePoint-Lösungen entwerfen.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-128">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

   
<span data-ttu-id="4bd5f-129">**An der Diskussion teilnehmen**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-129">**Join the discussion**</span></span>

|<span data-ttu-id="4bd5f-130">**Kontakt**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-130">**Contact us**</span></span>|<span data-ttu-id="4bd5f-131">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-131">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4bd5f-132">**Welche Lösungen benötigen Sie?**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-132">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="4bd5f-p104">Wir entwickeln Inhalte für Lösungen auf Grundlage mehrerer Microsoft-Produkte und -Dienste. Lassen Sie uns wissen, was Sie von unseren serverübergreifenden Lösungen halten, oder fordern Sie spezifische Lösungen an, indem Sie eine E-Mail an [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) senden.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-p104">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="4bd5f-135">**An der Diskussion über Lösungen teilnehmen**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-135">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="4bd5f-p105">Wenn Sie sich für Cloud-basierte Lösungen interessieren, werden Sie Teil des Cloud Adoption Advisory Board (CAAB), um Zugriff auf eine größere, dynamische Community aus Microsoft-Inhaltsentwicklern, Branchenexperten und Kunden aus aller Welt zu haben. Um beizutreten, fügen Sie sich selbst als Mitglied des [CAAB (Cloud Adoption Advisory Board)-Bereichs](https://aka.ms/caab) der Microsoft Tech Community hinzu, und senden Sie uns eine E-Mail an [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Communityinhalte stehen allen Personen im [CAAB-Blog](https://blogs.technet.com/b/solutions_advisory_board/) zur Verfügung. CAAB-Mitglieder erhalten jedoch Einladungen zu privaten Webinaren, die neue Ressourcen und Lösungen für den Cloud-Einsatz beschreiben.</span><span class="sxs-lookup"><span data-stu-id="4bd5f-p105">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="4bd5f-140">**Die hier gezeigte Grafik abrufen**</span><span class="sxs-lookup"><span data-stu-id="4bd5f-140">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="4bd5f-p106">Wenn Sie eine bearbeitbare Kopie der Grafik wünschen, die Sie in disem Artikel sehen, senden wir Sie Ihnen gerne zu. Senden Sie eine E-Mail mit der Anforderung einschließlich der URL und dem Titel der Grafik an [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span><span class="sxs-lookup"><span data-stu-id="4bd5f-p106">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="4bd5f-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4bd5f-143">See Also</span></span>

[<span data-ttu-id="4bd5f-144">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="4bd5f-144">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)



