---
title: "Gemeinsame Elemente der Microsoft-Cloudkonnektivität"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Zusammenfassung: Informationen zu gemeinsamen Elementen der Netzwerkinfrastruktur und zu Vorbereitungen des Netzwerks.'
ms.openlocfilehash: b630daad3292976245c8cb5d3f493c32ad5be8a6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="99bc0-103">Gemeinsame Elemente der Microsoft-Cloudkonnektivität</span><span class="sxs-lookup"><span data-stu-id="99bc0-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="99bc0-104">**Zusammenfassung:** Informationen zu gemeinsamen Elementen der Netzwerkinfrastruktur und zu Vorbereitungen des Netzwerks.</span><span class="sxs-lookup"><span data-stu-id="99bc0-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="99bc0-105">Die Integration Ihres Netzwerk in die Microsoft-Cloud bietet optimalen Zugriff auf eine Vielzahl von Diensten.</span><span class="sxs-lookup"><span data-stu-id="99bc0-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="99bc0-106">Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud-Dienste</span><span class="sxs-lookup"><span data-stu-id="99bc0-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="99bc0-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="99bc0-107"><a name="steps"> </a></span></span>

<span data-ttu-id="99bc0-108">Für Ihr lokales Netzwerk:</span><span class="sxs-lookup"><span data-stu-id="99bc0-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="99bc0-109">Analysieren Sie Ihre Clientcomputer, und optimieren Sie die Netzwerkhardware, Softwaretreiber, Protokolleinstellungen und Internetbrowser.</span><span class="sxs-lookup"><span data-stu-id="99bc0-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="99bc0-110">Analysieren Sie Ihr lokales Netzwerk im Hinblick auf Wartezeiten und optimales Routing an das Internet-Edgegerät.</span><span class="sxs-lookup"><span data-stu-id="99bc0-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="99bc0-111">Analysieren Sie die Kapazität und Leistung Ihres Internet-Edgegeräts, und optimieren Sie es im Hinblick auf höheren Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="99bc0-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="99bc0-112">Für Ihre Internetverbindung.</span><span class="sxs-lookup"><span data-stu-id="99bc0-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="99bc0-113">Analysieren Sie die Wartezeit zwischen dem Internet-Edgegerät (z. B. die externe Firewall) und den regionalen Standorten des Microsoft Cloud-Diensts, mit dem Sie eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="99bc0-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="99bc0-p101">Analysieren Sie die Kapazität und die Nutzung Ihrer aktuellen Internetverbindung, und fügen Sie Kapazität hinzu, falls erforderlich. Fügen Sie alternativ eine ExpressRoute-Verbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="99bc0-116">Optionen für Microsoft-Cloudkonnektivität</span><span class="sxs-lookup"><span data-stu-id="99bc0-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="99bc0-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="99bc0-117"><a name="steps"> </a></span></span>

<span data-ttu-id="99bc0-118">Verwenden Sie Ihre vorhandene Internetpipe oder eine ExpressRoute-Verbindung mit Office 365, Azure und Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="99bc0-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="99bc0-119">**Abbildung 1: Optionen für Microsoft-Cloudkonnektivität**</span><span class="sxs-lookup"><span data-stu-id="99bc0-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Abbildung 1:  Optionen für Microsoft-Cloudkonnektivität](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="99bc0-p102">In Abbildung 1 wird gezeigt, wie ein lokales Netzwerk mithilfe der vorhandenen Internetpipe oder ExpressRoute mit Microsoft-Cloudangeboten verbunden werden kann. Die Internetpipe stellt ein Umkreisnetzwerk dar und kann die folgenden Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="99bc0-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="99bc0-p103">**Interne Firewall:** Eine Grenze zwischen Ihrem vertrauenswürdigen Netzwerk und einem nicht vertrauenswürdigen Netzwerk. Führt eine Filterung des Datenverkehrs (basierend auf Regeln) und eine Überwachung aus.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="99bc0-125">**Externe Arbeitslast:** Websites oder andere Arbeitslasten, die externen Benutzern im Internet zur Verfügung gestellt werden.</span><span class="sxs-lookup"><span data-stu-id="99bc0-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="99bc0-p104">**Proxyserver:** Dienstanforderungen für Webinhalte im Auftrag von Intranetbenutzern. Ein Reverse-Proxy lässt unerwünschte eingehende Anfragen zu.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="99bc0-p105">**Externe Firewall:** Lässt ausgehenden Datenverkehr und angegebenen eingehenden Datenverkehr zu. Kann eine Adressübersetzung durchführen.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="99bc0-130">**WAN-Verbindung zum Internetdienstanbieter:** Eine anbieterbasierte Verbindung zu einem ISP, der mit dem Internet für Konnektivität und Routing auf der gleichen Ebene steht.</span><span class="sxs-lookup"><span data-stu-id="99bc0-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="99bc0-131">In allen Microsoft-Cloud-Diensten gemeinsame Netzwerkbereiche</span><span class="sxs-lookup"><span data-stu-id="99bc0-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="99bc0-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="99bc0-132"><a name="steps"> </a></span></span>

<span data-ttu-id="99bc0-133">Sie müssen diese Netzwerkbereiche berücksichtigen, wenn Sie einen der Clouddienste von Microsoft einführen.</span><span class="sxs-lookup"><span data-stu-id="99bc0-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="99bc0-134">**Intranetleistung:** Die Leistung von internetbasierten Ressourcen wird beeinträchtigt, wenn das Intranet, einschließlich Clientcomputern, nicht optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="99bc0-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="99bc0-135">**Edgegeräte:** Geräte am Rand Ihres Netzwerks sind Ausgangspunkte und können NATs (Network Adress Translators), Proxyserver (einschließlich Reverse-Proxys, Firewalls, Angriffserkennungssysteme oder eine Kombination daraus umfassen.</span><span class="sxs-lookup"><span data-stu-id="99bc0-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="99bc0-p106">**Internetverbindung:** Die WAN-Verbindung zu Ihrem Internetdienstanbieter und das Internet sollten über ausreichend Kapazität für Höchstlasten verfügen. Sie können auch eine ExpressRoute-Verbindung verwenden.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="99bc0-p107">**Internet-DNS:** A-, AAAA-, CNAME-, MX-, PTR- und andere Datensätze, um die Microsoft-Cloud oder die in der Cloud gehosteten Dienste zu suchen. Beispielsweise benötigen Sie möglicherweise einen CNAME-Eintrag für Ihre in Azure PaaS gehostete App.</span><span class="sxs-lookup"><span data-stu-id="99bc0-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="99bc0-140">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="99bc0-140">Next step</span></span>

[<span data-ttu-id="99bc0-141">ExpressRoute für Microsoft-Cloudkonnektivität</span><span class="sxs-lookup"><span data-stu-id="99bc0-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="99bc0-142">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="99bc0-142">See also</span></span>

<span data-ttu-id="99bc0-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="99bc0-143"></span></span>

[<span data-ttu-id="99bc0-144">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="99bc0-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="99bc0-145">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="99bc0-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


