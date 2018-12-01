---
title: Architektur von Microsoft Hybrid Cloud-Szenarien
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Zusammenfassung: Informationen über die Architektur von Microsoft-Hybridcloudangeboten.'
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123392"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="fb984-103">Architektur von Microsoft Hybrid Cloud-Szenarien</span><span class="sxs-lookup"><span data-stu-id="fb984-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="fb984-104">**Zusammenfassung:** Informationen über die Architektur von Microsoft-Hybridcloudangeboten.</span><span class="sxs-lookup"><span data-stu-id="fb984-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="fb984-105">Verwenden Sie eine architekturbezogene Herangehensweise, wenn Sie Hybridcloudszenarien mit Microsoft-Clouddiensten und -plattformen planen und implementieren.</span><span class="sxs-lookup"><span data-stu-id="fb984-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="fb984-106">**Abbildung 1: Microsoft-Hybridcloudstack**</span><span class="sxs-lookup"><span data-stu-id="fb984-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft Hybridcloudstack](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="fb984-108">Abbildung 1 zeigt den Microsoft-Hybridcloudstack und die Schicht, die lokal, Netzwerk, Identität, Apps, Szenarien und die Kategorie des Clouddiensts (Microsoft SaaS, Azure PaaS und Azure PaaS) enthält.</span><span class="sxs-lookup"><span data-stu-id="fb984-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="fb984-p101">Ebene der Apps und Szenarien hat die bestimmte Hybrid-Cloud-Szenarien, die detailliert sind in den Artikeln dieses Modells. Die Identität, Netzwerk und lokalen Ebenen können gemeinsam die Kategorien von Cloud-Dienst (SaaS, PaaS oder PaaS) sein.</span><span class="sxs-lookup"><span data-stu-id="fb984-p101">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="fb984-111">Lokal</span><span class="sxs-lookup"><span data-stu-id="fb984-111">On-premises</span></span>
    
    <span data-ttu-id="fb984-p102">Lokale Infrastruktur für Hybridszenarien kann Server für SharePoint, Exchange, Skype for Business und Branchenanwendungen enthalten. Des weiteren kann sie Datenspeicher (Datenbanken, Listen, Dateien) enthalten. Ohne ExpressRoute-Verbindungen muss der Zugriff auf die lokalen Datenspeicher über einen Reverseproxy oder durch Zugriff auf den Server oder die Daten in der DMZ oder dem Extranet gewährt werden.</span><span class="sxs-lookup"><span data-stu-id="fb984-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="fb984-115">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="fb984-115">Network</span></span>
    
    <span data-ttu-id="fb984-p103">Es gibt zwei Optionen für die Verbindung mit Microsoft-Cloud-Plattformen und Dienste: Ihre vorhandenen Internet Pipe und ExpressRoute. Verwenden Sie eine ExpressRoute-Verbindung, wenn vorhersehbare Leistung wichtig ist. Eine Verbindung als ExpressRoute können Sie direkt an Microsoft SaaS-Dienste (Office 365 und Dynamics 365), Azure PaaS-Dienste und Azure IaaS-Dienste eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="fb984-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="fb984-119">Identität</span><span class="sxs-lookup"><span data-stu-id="fb984-119">Identity</span></span>
    
    <span data-ttu-id="fb984-p104">Je nach Microsoft-Cloudplattform gibt es zwei Möglichkeiten für die Cloudidentitätsinfrastruktur. Integrieren Sie für SaaS und Azure PaaS Ihre lokale Identitätsinfrastruktur in Azure AD oder einen Verbund mit Ihrer lokalen Infrastruktur oder Drittanbieter-Identitätsanbietern. Für in Azure ausgeführte virtuelle Computer können Sie Ihre lokale Identitätsinfrastruktur, z. B. Windows Server AD, auf virtuelle Netzwerke (VNets) erweitern, in denen sich ihre virtuellen Computer befinden.</span><span class="sxs-lookup"><span data-stu-id="fb984-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="fb984-123">Hybridcloudszenarien für den dreiphasigen Prozess der Cloudeinführung</span><span class="sxs-lookup"><span data-stu-id="fb984-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="fb984-p105">Viele Unternehmen, so auch Microsoft, verwenden eine dreiphasige Herangehensweise zur Einführung der Cloud. Hybridcloudszenarien können in jeder Phase eine Rolle spielen.</span><span class="sxs-lookup"><span data-stu-id="fb984-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="fb984-126">Verschieben von Produktivitätsarbeitslasten in SaaS</span><span class="sxs-lookup"><span data-stu-id="fb984-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="fb984-127">Für Produktivitätsarbeitslasten, die aktuell lokal sind oder die lokal bleiben müssen, ermöglichen Hybridszenarien, sie mit ihren Cloudgegenstücken zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="fb984-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="fb984-128">Entwickeln von neuen und modernen Anwendungen in Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="fb984-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="fb984-129">Azure PaaS-Hybridanwendungen können lokale Server- oder Speicherressourcen sicher nutzen.</span><span class="sxs-lookup"><span data-stu-id="fb984-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="fb984-130">Verschieben von vorhandenen Anwendungen in Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="fb984-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="fb984-131">Für Aufnehmen-und-Verlagern- sowie Erstellen-in-der-Cloud-Szenarien bieten serverbasierte Anwendungen, die auf virtuellen Azure-Computern ausgeführt werden, einfache Bereitstellung und Skalierung.</span><span class="sxs-lookup"><span data-stu-id="fb984-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="fb984-132">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fb984-132">See Also</span></span>

[<span data-ttu-id="fb984-133">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="fb984-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="fb984-134">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="fb984-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

