---
title: Entwerfen von Netzwerken für Microsoft-PaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Zusammenfassung: Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft Azure PaaS optimieren.'
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872236"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="cb794-103">Entwerfen von Netzwerken für Microsoft-PaaS</span><span class="sxs-lookup"><span data-stu-id="cb794-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="cb794-104">**Zusammenfassung:** Grundlegende Informationen darüber, wie Sie Ihr Netzwerk für Zugriff auf Microsoft Azure PaaS optimieren.</span><span class="sxs-lookup"><span data-stu-id="cb794-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="cb794-105">Für die Optimierung Ihrer Netzwerke für Azure PaaS-Apps ist eine ausreichende Internetbandbreite und möglicherweise die Verteilung des Netzwerkdatenverkehrs auf mehrere Websites oder Apps erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cb794-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="cb794-106">Planen von Schritten zum Hosten der PaaS-Anwendungen der Organisation in Azure</span><span class="sxs-lookup"><span data-stu-id="cb794-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="cb794-107">Durchlaufen Sie die **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft Cloud Services** in [Gemeinsame Elemente der Microsoft-Cloudkonnektivität](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="cb794-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="cb794-108">Optimieren Sie die Internetbandbreite mithilfe der Schritte 2 bis 4 der **Schritte zum Vorbereiten Ihres Netzwerks für Microsoft SaaS-Dienste** in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="cb794-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="cb794-109">Ermitteln Sie, ob Sie eine ExpressRoute-Verbindung mit Azure benötigen.</span><span class="sxs-lookup"><span data-stu-id="cb794-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="cb794-110">Für webbasierte Arbeitslasten müssen Sie ermitteln, ob Sie das Azure-Anwendungsgateway benötigen.</span><span class="sxs-lookup"><span data-stu-id="cb794-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="cb794-111">Um den Datenverkehr an unterschiedliche Endpunkte in unterschiedlichen Rechenzentren zu verteilen, ermitteln Sie, ob Sie Azure Traffic Manager benötigen.</span><span class="sxs-lookup"><span data-stu-id="cb794-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="cb794-112">Internetbandbreite für PaaS-Anwendungen in der Organisation</span><span class="sxs-lookup"><span data-stu-id="cb794-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="cb794-p101">Für Organisationsanwendungen, die in Azure PaaS gehostet sind, ist eine Internetbandbreite für Intranetbenutzer erforderlich. Es gibt zwei Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="cb794-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="cb794-p102">**Option 1:** Verwenden Sie Ihrer vorhandene Pipe, die für Internetverkehr optimiert ist und über die entsprechende Kapazität für Spitzenlasten verfügt. Weitere Informationen zu Überlegungen im Zusammenhang mit Internet-Edge, Clientnutzung und IT-Abläufen finden Sie unter[Entwerfen von Netzwerken für Microsoft-SaaS](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="cb794-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="cb794-117">**Option 2:** Verwenden Sie hohe Bandbreite oder eine niedrige Wartezeit eine ExpressRoute-Verbindung mit Azure.</span><span class="sxs-lookup"><span data-stu-id="cb794-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="cb794-118">**Abbildung 1: Verbindungsoptionen zum Verbinden der Azure PaaS-Dienste**</span><span class="sxs-lookup"><span data-stu-id="cb794-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Abbildung 1: Verbindungsoptionen für Azure PaaS-Dienste](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="cb794-120">In Abbildung 1 ist ein lokales Netzwerk dargestellt, das über eine Internetpipe oder ExpressRoute eine Verbindung zu Azure PaaS-Diensten herstellt.</span><span class="sxs-lookup"><span data-stu-id="cb794-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="cb794-121">Azure-Anwendungsgateway</span><span class="sxs-lookup"><span data-stu-id="cb794-121">Azure Application Gateway</span></span>

<span data-ttu-id="cb794-122">Dienste für Routing auf Anwendungsebene und Lastenausgleich, mit denen Sie ein skalierbares und hoch verfügbares Web-Front-End in Azure für Web-Apps, Clouddienste und virtuelle Computer erstellen können.</span><span class="sxs-lookup"><span data-stu-id="cb794-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="cb794-123">**Abbildung 2: Azure-Anwendungsgateway**</span><span class="sxs-lookup"><span data-stu-id="cb794-123">**Figure 2: Azure Application Gateway**</span></span>

![Abbildung 2: Azure-Anwendungsgatewaydienst](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="cb794-125">In Abbildung 2 ist das Azure-Anwendungsgateway dargestellt und wie Benutzeranforderungen aus dem Internet an Azure-Web-Apps, Clouddienste oder virtuelle Computer umgeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="cb794-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="cb794-126">Das Anwendungsgateway unterstützt derzeit Ebene 7 Anwendungsübermittlung für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="cb794-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="cb794-127">HTTP-Lastenausgleich</span><span class="sxs-lookup"><span data-stu-id="cb794-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="cb794-128">Cookiebasierte Sitzungsaffinität</span><span class="sxs-lookup"><span data-stu-id="cb794-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="cb794-129">SSL-Verschiebungen</span><span class="sxs-lookup"><span data-stu-id="cb794-129">SSL offload</span></span>
    
<span data-ttu-id="cb794-130">Weitere Informationen finden Sie unter [Anwendungsgateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="cb794-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="cb794-131">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="cb794-131">Azure Traffic Manager</span></span>

<span data-ttu-id="cb794-132">Die Verteilung des Datenverkehrs an verschiedene Endpunkte, darunter Clouddienste oder Azure-Web-Apps, die sich in unterschiedlichen Rechenzentren oder an externen Endpunkten befinden.</span><span class="sxs-lookup"><span data-stu-id="cb794-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="cb794-133">Der Traffic Manager verwendet die folgenden Routingmethoden:</span><span class="sxs-lookup"><span data-stu-id="cb794-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="cb794-134">**Failover:** Die Endpunkte befinden sich im gleichen oder in unterschiedlichen Azure-Rechenzentren, und Sie möchten einen primären Endpunkt für den gesamten Datenverkehr verwenden, stellen jedoch Sicherungen bereit, für den Fall, dass der primäre oder der Sicherungsendpunkt nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="cb794-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="cb794-135">**Roundrobin:** Sie möchten die Last über eine Reihe von Endpunkten im selben Rechenzentrum oder über unterschiedliche Rechenzentren hinweg verteilen.</span><span class="sxs-lookup"><span data-stu-id="cb794-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="cb794-136">**Leistung:** Sie haben die Endpunkte an unterschiedlichen geografischen Standorten, und Sie möchten, dass anfordernde Clients den „nächsten" Endpunkt im Hinblick auf niedrigste Wartezeit verwenden.</span><span class="sxs-lookup"><span data-stu-id="cb794-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="cb794-137">Nachfolgend finden Sie ein Beispiel für drei geografisch verteilte Web-Apps.</span><span class="sxs-lookup"><span data-stu-id="cb794-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="cb794-138">**Abbildung 3: Azure Traffic Manager**</span><span class="sxs-lookup"><span data-stu-id="cb794-138">**Figure 3: Azure Traffic Manager**</span></span>

![Abbildung 3: Azure Traffic Manager](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="cb794-p103">In Abbildung 3 ist der grundlegende Prozess dargestellt, den Traffic Manager zum Umleiten von Anforderungen an drei unterschiedliche Azure-Web-Apps in den USA, in Europa und in Asien verwendet. Im Beispiel:</span><span class="sxs-lookup"><span data-stu-id="cb794-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="cb794-142">Eine Benutzer-DNS-Abfrage für eine Website-URL wird an Azure Traffic Manager geleitet, der den Namen einer regionalen Web-Apps basierend auf der Leistungsroutingmethode zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="cb794-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="cb794-143">Der Benutzer initiiert den Datenverkehr mit der regionalen Web-App in Europa.</span><span class="sxs-lookup"><span data-stu-id="cb794-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="cb794-144">Weitere Informationen finden Sie unter [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="cb794-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="cb794-145">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="cb794-145">Next step</span></span>

[<span data-ttu-id="cb794-146">Entwerfen von Netzwerken für Microsoft Azure-IaaS</span><span class="sxs-lookup"><span data-stu-id="cb794-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="cb794-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cb794-147">See also</span></span>

[<span data-ttu-id="cb794-148">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="cb794-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="cb794-149">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="cb794-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

