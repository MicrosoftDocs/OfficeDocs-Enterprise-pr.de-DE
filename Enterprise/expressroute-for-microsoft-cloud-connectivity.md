---
title: ExpressRoute für Microsoft-Cloudkonnektivität
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/02/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Zusammenfassung: Verstehen Sie, wie Sie mit ExpressRoute schnellere und zuverlässigere Verbindungen zu Microsoft-Clouddiensten und -Plattformen erzielen können.'
ms.openlocfilehash: b0f47278a94b2926cd540ce759ced9b2418aa598
ms.sourcegitcommit: 6e3bfe55a173a733d6696790b88efa39853ebdb9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "27470167"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="de8b6-103">ExpressRoute für Microsoft-Cloudkonnektivität</span><span class="sxs-lookup"><span data-stu-id="de8b6-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="de8b6-104">**Zusammenfassung:** Verstehen Sie, wie Sie mit ExpressRoute schnellere und zuverlässigere Verbindungen zu Microsoft-Clouddiensten und -Plattformen erzielen können.</span><span class="sxs-lookup"><span data-stu-id="de8b6-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="de8b6-105">ExpressRoute bietet eine private, dedizierte Netzwerkverbindung mit hohem Durchsatz mit der Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="de8b6-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="de8b6-106">ExpressRoute in die Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="de8b6-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="de8b6-107">Nachfolgend finden Sie den Netzwerkpfad zur Microsoft-Cloud ohne ExpressRoute-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="de8b6-108">**Abbildung 1: Der Netzwerkpfad ohne ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="de8b6-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Abbildung 1: Der Netzwerkpfad ohne ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="de8b6-p101">Abbildung 1 zeigt den typischen Pfad zwischen einem lokalen Netzwerk und der Microsoft Cloud. Das lokale Netzwerk-Edge stellt über einen WAN-Link zu einem Internetdienstanbieter eine Verbindung zum Internet her. Der Datenverkehr bewegt dann sich über das Internet an den Rand der Microsoft Cloud. Cloud-Angebote innerhalb der Microsoft Cloud umfassen Office 365, Microsoft Azure, Microsoft Intune und Dynamics 365. Benutzer einer Organisation können sich im lokalen Netzwerk oder im Internet befinden.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="de8b6-115">Ohne eine ExpressRoute-Verbindung ist der einzige Teil des Datenverkehrpfads in die Microsoft Cloud, den Sie steuern können (und der eine Beziehung zu dem Dienstanbieter hat), der Link zwischen dem lokalen Netzwerk-Edge und dem Internetdienstanbieter.</span><span class="sxs-lookup"><span data-stu-id="de8b6-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="de8b6-116">Der Pfad zwischen Ihrem Internetdienstanbieter und dem Rand der Microsoft Cloud ist ein umfassendes Übermittlungssystem im Internet, das Ausfällen, Überlastungen und einer Überwachung durch böswillige Benutzer unterliegt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="de8b6-117">Benutzer im Internet, z. B. Roaming- oder Remotebenutzer, senden ihren Datenverkehr über das Internet an die Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="de8b6-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="de8b6-118">Nachfolgend finden Sie die Netzwerkpfade zur Microsoft Cloud mit ExpressRoute-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="de8b6-119">**Abbildung 2: Die Netzwerkpfade ohne ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="de8b6-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Abbildung 2: Die Netzwerkpfade ohne ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="de8b6-p102">Abbildung 2 zeigt zwei Netzwerkpfade. Der Datenverkehr zu Microsoft Intune bewegt sich über denselben Pfad wie normaler Internetverkehr. Datenverkehr zu Office 365, Microsoft Azure und Dynamics 365 bewegt sich über die ExpressRoute-Verbindung, ein dedizierter Pfad zwischen dem Rand des lokalen Netzwerks und dem Rand der Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="de8b6-p103">Eine Verbindung ExpressRoute Sie jetzt-Steuerelements über eine Beziehung mit Ihrem Dienstanbieter haben, über den gesamten Datenverkehr Pfad von der Kante des Microsoft cloud Edge. Diese Verbindung kann vorhersehbare Leistung und einen [99,95 % Betriebszeit SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)anbieten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="de8b6-p104">Sie können sich nun auf vorhersehbaren Durchsatz und planbare Wartezeit basierend auf der Verbindung Ihres Dienstanbieters für Office 365-, Azure- und Dynamics 365-Dienste verlassen. ExpressRoute-Verbindungen mit Microsoft Intune werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="de8b6-128">Datenverkehr, der über die ExpressRoute-Verbindung gesendet wird, unterliegt nicht mehr Internetausfällen, Überlastungen und Überwachungen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="de8b6-p105">Benutzer im Internet, z. B. Roaming- oder Remotebenutzer, senden ihren Datenverkehr nach wie vor über das Internet an die Microsoft Cloud. Eine Ausnahme stellt der Datenverkehr zu einer Branchenanwendung im Intranet dar, die in Azure IaaS gehostet wird, der über die ExpressRoute-Verbindung über eine Remotezugriffverbindung an das lokale Netzwerk gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="de8b6-131">Selbst bei einer ExpressRoute-Verbindung wird ein Teil des Datenverkehrs nach wie vor über das Internet gesendet, z. B. DNS-Abfragen, Überprüfungen der Zertifikatssperrliste und CDN-Anfragen (Content Delivery Netzwerk, Netzwerk für die Inhaltsübermittlung).</span><span class="sxs-lookup"><span data-stu-id="de8b6-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="de8b6-132">Weitere Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="de8b6-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="de8b6-133">ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="de8b6-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="de8b6-134">ExpressRoute für Azure</span><span class="sxs-lookup"><span data-stu-id="de8b6-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="de8b6-135">Vorteile von ExpressRoute für Azure</span><span class="sxs-lookup"><span data-stu-id="de8b6-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="de8b6-136">Nachfolgend finden Sie einige der Vorteile der Verwendung von ExpressRoute für Azure-basierte Clouddienste:</span><span class="sxs-lookup"><span data-stu-id="de8b6-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="de8b6-p106">**Vorhersagbare Leistung:** Mit einem dedizierten Pfad am Rand der Microsoft Cloud unterliegt Ihre Leistung nicht Ausfällen von Internetdienstanbietern und Überlastungen. Sie können Ihre Anbieter im Hinblick auf eine Durchsatz- und Wartezeit-SLA für die Microsoft Cloud zur Verantwortung ziehen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="de8b6-p107">**Datenschutz für Ihren Datenverkehr:** Verkehr, der über die dedizierte ExpressRoute-Verbindung gesendet wird, unterliegt nicht der Internetüberwachung oder Paketerfassung und Analyse durch böswillige Benutzer. Diese Verbindung ist so sicher wie die Verwendung von MPLS-basierten WAN-Links.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="de8b6-141">**Verbindungen mit hohem Durchsatz:** Dank einer umfassenden Unterstützung von ExpressRoute-Verbindungen durch Exchange-Anbieter und Netzwerkdienstanbieter können Sie einen Link mit bis zu 10 Gbit/s zur Microsoft Cloud erreichen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="de8b6-142">**Niedrigere Kosten für einige Konfigurationen:** Obwohl ExpressRoute-Verbindungen zusätzliche Kosten bedeuten, kann eine einzige ExpressRoute-Verbindung in einigen Fällen weniger kosten als eine Steigerung Ihrer Internetkapazität an mehreren Standorten Ihrer Organisation, um einen angemessenen Durchsatz zu Microsoft-Clouddiensten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="de8b6-p108">Eine ExpressRoute-Verbindung ist nicht in jeder Konfiguration eine Garantie für höhere Leistung. Es ist möglich, dass über eine ExpressRoute-Verbindung mit niedriger Bandbreite eine niedrigere Leistung erzielt wird als mit einer Internetverbindung mit hoher Bandbreite, die sich nicht weit von einem regionalen Microsoft-Rechenzentrum befindet.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="de8b6-145">Die neuesten Empfehlungen zur Verwendung von ExpressRoute mit Office 365 finden Sie unter [ExpressRoute für Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="de8b6-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="de8b6-146">ExpressRoute-Verbindungsmodelle</span><span class="sxs-lookup"><span data-stu-id="de8b6-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="de8b6-147">Tabelle 1 zeigt die drei primären Verbindungsmodelle für ExpressRoute-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="de8b6-148">**Co-Location bei einem Cloud Exchange**</span><span class="sxs-lookup"><span data-stu-id="de8b6-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="de8b6-149">**Punkt-zu-Punkt-Ethernet**</span><span class="sxs-lookup"><span data-stu-id="de8b6-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="de8b6-150">**n:n-Verbindung (IP VPN)**</span><span class="sxs-lookup"><span data-stu-id="de8b6-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute-Konnektivitätsmodell: Zusammengestellt bei einem Cloud-Austausch](media/Network-Poster/ER-Conn1.png)|![ExpressRoute-Konnektivitätsmodell: Punkt-zu-Punkt-Ethernet](media/Network-Poster/ER-Conn2.png)|![ExpressRoute-Konnektivitätsmodell: N:n-Verbindung (IP-VPN)](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="de8b6-154">Wenn Sie sich in einer Einrichtung mit einem Cloud Exchange befinden, können Sie virtuelle Querverbindungen zur Microsoft Cloud über den Ethernet Exchange des Co-Location-Anbieters bestellen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="de8b6-155">Sie können Ihre lokalen Rechenzentren über einen Punkt-zu-Punkt-Ethernet-Link mit der Microsoft Cloud verbinden.</span><span class="sxs-lookup"><span data-stu-id="de8b6-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="de8b6-156">Wenn Sie bereits einen IP VPN (MLPS)-Anbieter verwenden, um die Websites Ihrer Organisation zu verbinden, fungiert eine ExpressRoute-Verbindung zur Microsoft Cloud wie ein weiterer Standort in Ihrem privaten WAN.</span><span class="sxs-lookup"><span data-stu-id="de8b6-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="de8b6-157">**Tabelle 1: ExpressRoute-Verbindungsmodelle**</span><span class="sxs-lookup"><span data-stu-id="de8b6-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="de8b6-158">ExpressRoute-Peeringbeziehungen zu Microsoft-Clouddiensten</span><span class="sxs-lookup"><span data-stu-id="de8b6-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="de8b6-p109">Eine einzelne ExpressRoute Verbindung unterstützt bis zu zwei verschiedenen Border Gateway Protocol (BGP) Peers Beziehungen mit verschiedenen Teilen eines Microsoft-Cloud. BPG wird Peers Beziehungen verwendet, um eine Vertrauensstellung und exchange-Routinginformationen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p109">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="de8b6-161">**Abbildung 3: Die zwei verschiedenen BGP Beziehungen in einer einzigen ExpressRoute-Verbindung**</span><span class="sxs-lookup"><span data-stu-id="de8b6-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![Abbildung 3: Die zwei verschiedenen BGP Beziehungen in einer einzigen ExpressRoute-Verbindung](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="de8b6-p110">Abbildung 3 zeigt eine ExpressRoute Verbindung von einem lokalen Netzwerk. Die ExpressRoute Verbindung verfügt über zwei logische Peers Beziehungen. Eine Microsoft Peers Beziehung wechselt zu Microsoft SaaS-Dienste, einschließlich Office 365, Dynamcs 365 und Azure PaaS-Dienste. Eine private Beziehung Peers geht Azure IaaS und ein virtuelles Netzwerk-Gateway, die virtuellen Computern gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has two logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="de8b6-167">Die Microsoft-BGP-Peeringbeziehung:</span><span class="sxs-lookup"><span data-stu-id="de8b6-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="de8b6-168">Wird von einem Router in Ihrer DMZ in die öffentlichen Adressen von Office 365, Dynamics 365 und Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="de8b6-169">Unterstützt die bidirektional initiierte Kommunikation.</span><span class="sxs-lookup"><span data-stu-id="de8b6-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="de8b6-170">Die private BGP-Peeringbeziehung:</span><span class="sxs-lookup"><span data-stu-id="de8b6-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="de8b6-171">Besteht zwischen einem Router am Rand des Unternehmensnetzwerks und den privaten IP-Adressen, die Ihren Azure VNets zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="de8b6-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="de8b6-172">Unterstützt die bidirektional initiierte Kommunikation.</span><span class="sxs-lookup"><span data-stu-id="de8b6-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="de8b6-173">Ist eine Erweiterung Ihres Organisationsnetzwerks in die Microsoft Cloud, die über eine intern konsistente Adresse und Routing verfügt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="de8b6-174">Die öffentliche Peers BGP-Beziehung, die in früheren Versionen von in diesem Artikel beschriebenen ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="de8b6-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="de8b6-175">Beispiel der Anwendungsbereitstellung und für den Fluss des Datenverkehrs mit ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="de8b6-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="de8b6-p111">Wie sich Datenverkehr über ExpressRoute-Verbindungen hinweg und innerhalb der Microsoft Cloud bewegt ist eine Funktion der Routen an den Hops des Pfads zwischen der Quelle und dem Ziel sowie des Anwendungsverhaltens. Nachfolgend finden Sie ein Beispiel für eine Anwendung, die auf einem virtuellen Azure-Computer ausgeführt wird, der auf eine lokale SharePoint-Farm über eine Standort-zu-Standort-VPN-Verbindung zugreift.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p111">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="de8b6-178">**Abbildung 4: Eine Anwendung auf einem virtuellen Azure-Computer, der auf eine lokale SharePoint-Farm zugreift**</span><span class="sxs-lookup"><span data-stu-id="de8b6-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Abbildung 4: Eine Anwendung auf einem virtuellen Azure-Computer, der auf eine lokale SharePoint-Farm zugreift](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="de8b6-180">Abbildung 4 zeigt eine lokale SharePoint-Farm, eine Standort-zu-Standort-VPN-Verbindung zwischen dem lokalen Netzwerk und einem virtuellen Netzwerk in Azure IaaS, einen Anwendungsserver, der als ein virtueller Azure IaaS-Computer ausgeführt wird, und den Datenverkehr zwischen dem Anwendungsserver und der SharePoint-Farm.</span><span class="sxs-lookup"><span data-stu-id="de8b6-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="de8b6-181">Die Anwendung sucht die IP-Adresse der SharePoint-Farm mithilfe der lokalen DNS, und der gesamte Datenverkehr läuft über die Standort-zu-Standort-VPN-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="de8b6-182">Diese Organisation hat ihre lokale SharePoint-Farm zu SharePoint Online in Office 365 migriert und eine ExpressRoute-Verbindung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="de8b6-183">**Abbildung 5: Verschieben der lokalen SharePoint-Farm zu SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="de8b6-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Abbildung 5: Verschieben der lokalen SharePoint-Farm zu SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="de8b6-p112">Abbildung 5 zeigt das Hinzufügen einer ExpressRoute-Verbindung mit Peeringbeziehungen zu Microsoft SaaS und Office 365 und zu Azure IaaS, das den Anwendungsserver in einem virtuellen Netzwerk enthält. Die lokale SharePoint-Farm wurde nach Office 365 migriert.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p112">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="de8b6-187">Mit der Microsoft-Peeringbeziehung und der privaten Peeringbeziehung:</span><span class="sxs-lookup"><span data-stu-id="de8b6-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="de8b6-188">Vom virtuellen Azure-Netzwerkgateway stehen lokale Standorte über die ExpressRoute-Verbindung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="de8b6-189">Aus dem Office 365-Abonnement stehen öffentliche IP-Adressen von Edgegeräten, z. B. Proxyserver, über die ExpressRoute-Verbindung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="de8b6-190">vom Rand des lokalen Netzwerks stehen die privaten IP-Adressen von Azure VNet und die öffentlichen IP-Adressen von Office 365 über die ExpressRoute-Verbindung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="de8b6-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="de8b6-191">Wenn die Anwendung auf die URLs von SharePoint Online zugreift, wird der Datenverkehr über die ExpressRoute-Verbindung an einen Proxyserver am Rand weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="de8b6-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="de8b6-p113">Wenn der Proxyserver die IP-Adresse von SharePoint Online gefunden hat, wird der Datenverkehr wieder über die ExpressRoute-Verbindung zurückgeleitet. Antwortdatenverkehr wird über den umgekehrten Pfad übermittelt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p113">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="de8b6-194">**Abbildung 6: Datenfluss, wenn die SharePoint-Farm zu SharePoint Online in Office 365 migriert wurde**</span><span class="sxs-lookup"><span data-stu-id="de8b6-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Abbildung 6: Datenfluss, wenn die SharePoint-Farm zu SharePoint Online in Office 365 migriert wurde](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="de8b6-196">Abbildung 6 zeigt, wie der Datenverkehr zwischen dem Anwendungsserver und SharePoint Online in Office 365 über die private Peeringbeziehung vom Anwendungsserver an den Rand des lokalen Netzwerks und dann vom Rand über die Microsoft-Peeringbeziehung zu Office 365 fließt.</span><span class="sxs-lookup"><span data-stu-id="de8b6-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="de8b6-197">Das Ergebnis ist das so genannte „Hair Pinning“, eine Konsequenz des Routing- und Anwendungsverhaltens.</span><span class="sxs-lookup"><span data-stu-id="de8b6-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="de8b6-198">ExpressRoute und Microsoft Cloud-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="de8b6-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="de8b6-199">ExpressRoute-Verbindungen sind in zwei unterschiedlichen Versionen verfügbar: ExpressRoute und ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="de8b6-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="de8b6-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="de8b6-200">ExpressRoute</span></span>

<span data-ttu-id="de8b6-201">Die Art und Weise, wie sich Datenverkehr zwischen Ihrem Organisationsnetzwerk und einem Microsoft-Rechenzentrum bewegt, ist eine Kombination von Folgendem:</span><span class="sxs-lookup"><span data-stu-id="de8b6-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="de8b6-202">Ihren Standorten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-202">Your locations.</span></span>
    
- <span data-ttu-id="de8b6-203">Den Microsoft Cloud-Peeringstandorten (die physischen Standorte, die mit dem Microsoft-Edge verbunden werden sollen).</span><span class="sxs-lookup"><span data-stu-id="de8b6-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="de8b6-204">Den Standorten der Microsoft-Rechenzentren.</span><span class="sxs-lookup"><span data-stu-id="de8b6-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="de8b6-205">Die Standorte der Microsoft-Rechenzentren und der Cloud-Peeringbeziehungen sind alle mit dem Microsoft Cloud-Netzwerk verbunden.</span><span class="sxs-lookup"><span data-stu-id="de8b6-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="de8b6-p114">Wenn Sie eine ExpressRoute-Verbindung mit einem Microsoft Cloud-Peeringstandort erstellen, werden Sie mit dem Microsoft Cloud-Netzwerk und allen Microsoft-Rechenzentrumstandorten auf demselben Kontinent verbunden. Der Datenverkehr zwischen dem Cloud-Peeringstandort und dem Microsoft-Zielrechenzentrum erfolgt über das Microsoft Cloud-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p114">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="de8b6-208">Dies kann zu einer nicht optimalen Übermittlung an lokale Microsoft-Rechenzentren für das n:n-Verbindungsmodell führen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="de8b6-209">**Abbildung 7: Beispiel für ein geografisch verteilten Unternehmen, das eine einzelne ExpressRoute-Verbindung verwendet**</span><span class="sxs-lookup"><span data-stu-id="de8b6-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Abbildung 7: Beispiel für ein geografisch verteilten Unternehmen, das eine einzelne ExpressRoute-Verbindung verwendet](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="de8b6-p115">Abbildung 7 zeigt eine Organisation mit zwei Standorten, Standort 1 im Nordwesten der USA, und Standort 2 im Nordosten. Diese sind durch einen n: n-WAN-Anbieter verbunden. Diese Organisation verfügt auch über eine ExpressRoute-Verbindung zu einem Microsoft-Peeringstandort an der Westküste. Datenverkehr von Standort 2 im Nordosten, der an ein Rechenzentrum an der Ostküste gerichtet ist, muss den gesamten Weg über das WAN der Organisation an die Westküste, an den Microsoft-Peeringstandort und dann zurück über das gesamte Land über das Microsoft Cloud-Netzwerk an das Rechenzentrum an der Ostküste zurücklegen.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p115">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="de8b6-215">Verwenden Sie für eine optimale Übermittlung mehrere ExpressRoute-Verbindungen mit regionalen Microsoft Cloud-Peeringstandorten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="de8b6-216">**Abbildung 8: Die Verwendung mehrerer ExpressRoute-Verbindungen für optimale Übermittlung an regionale Rechenzentren**</span><span class="sxs-lookup"><span data-stu-id="de8b6-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Abbildung 8: Die Verwendung mehrerer ExpressRoute-Verbindungen für optimale Übermittlung an regionale Rechenzentren](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="de8b6-p116">Abbildung 8 zeigt dieselbe Organisation mit zwei ExpressRoute-Verbindungen, eine für jeden Standort, mit regional lokalen Microsoft-Peeringstandorten. In dieser Konfiguration geht Datenverkehr von Standort 2 im Nordosten, der an ein Rechenzentrum an der Ostküste gerichtet ist, direkt zu einem Peeringstandort an der Ostküste, zum Microsoft Cloud-Netzwerk und dann zu dem Rechenzentrum an der Ostküste.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p116">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="de8b6-220">Vorteile mehrerer ExpressRoute-Verbindungen:</span><span class="sxs-lookup"><span data-stu-id="de8b6-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="de8b6-221">Eine bessere Leistung für regional lokale Microsoft-Rechenzentrumsstandorte.</span><span class="sxs-lookup"><span data-stu-id="de8b6-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="de8b6-222">Höhere Verfügbarkeit in der Microsoft Cloud, wenn eine lokale ExpressRoute-Verbindung nicht mehr verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="de8b6-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="de8b6-p117">Dies eignet sich für Organisationen, die sich auf dem gleichen Kontinent befinden. Datenverkehr an Microsoft-Rechenzentren außerhalb des Kontinents, auf dem sich die Organisation befindet, läuft jedoch über das Internet.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p117">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="de8b6-225">Für interkontinentalen Datenverkehr über das Microsoft Cloud-Netzwerk müssen Sie die ExpressRoute Premium-Verbindungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="de8b6-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="de8b6-226">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="de8b6-226">ExpressRoute Premium</span></span>

<span data-ttu-id="de8b6-227">Für Organisationen, die global über Kontinente verteilt sind, können Sie ExpressRoute Premium verwenden.</span><span class="sxs-lookup"><span data-stu-id="de8b6-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="de8b6-p118">Mit ExpressRoute Premium können Sie alle Microsoft-Rechenzentren auf allen Kontinenten von einem beliebigen Microsoft-Peeringstandort auf einem beliebigen Kontinent erreichen. Der Datenverkehr zwischen Kontinenten erfolgt über das Microsoft Cloud-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p118">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="de8b6-230">Vorteile mehrerer ExpressRoute Premium-Verbindungen:</span><span class="sxs-lookup"><span data-stu-id="de8b6-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="de8b6-231">Eine bessere Leistung für kontinental lokale Microsoft-Rechenzentrumsstandorte.</span><span class="sxs-lookup"><span data-stu-id="de8b6-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="de8b6-232">Höhere Verfügbarkeit in der globalen Microsoft Cloud, wenn eine lokale ExpressRoute-Verbindung nicht mehr verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="de8b6-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="de8b6-233">ExpressRoute Premium ist für Office 365-basierten ExpressRoute Verbindungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de8b6-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="de8b6-234">**Abbildung 9: Das weltweite Microsoft Cloud-Netzwerk**</span><span class="sxs-lookup"><span data-stu-id="de8b6-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Abbildung 9: Das weltweite Microsoft Cloud-Netzwerk](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="de8b6-p119">Abbildung 9 zeigt ein logisches Diagramm des weltweiten Microsoft Cloud-Netzwerks mit Netzwerken, die sich über die Kontinente und Regionen der Welt und deren Zwischenverbindungen erstrecken. Da sich auf jedem Kontinent ein Teil des Microsoft Cloud-Netzwerks befindet, erstellt ein globales Unternehmen ExpressRoute Premium-Verbindungen von seinen regionalen Zweigstellen zu lokalen Microsoft-Peeringstandorten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p119">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="de8b6-238">Bei einer regionalen Niederlassung bewegt sich entsprechender Office 365-Datenverkehr folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="de8b6-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="de8b6-239">Datenverkehr an kontinentale Office 365-Rechenzentren bewegt sich über das Microsoft Cloud-Netzwerk innerhalb des Kontinents.</span><span class="sxs-lookup"><span data-stu-id="de8b6-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="de8b6-240">Datenverkehr an Office 365-Rechenzentren auf einem anderen Kontinent bewegt sich über das interkontinentale Microsoft Cloud-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="de8b6-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="de8b6-241">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="de8b6-241">For more information, see:</span></span>
  
- [<span data-ttu-id="de8b6-242">Schulung zu Azure ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="de8b6-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="de8b6-243">Netzwerkplanung und Leistungsoptimierung für Office 365</span><span class="sxs-lookup"><span data-stu-id="de8b6-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="de8b6-244">Office 365-Leistungsverwaltung</span><span class="sxs-lookup"><span data-stu-id="de8b6-244">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="de8b6-245">ExpressRoute-Optionen</span><span class="sxs-lookup"><span data-stu-id="de8b6-245">ExpressRoute options</span></span>

<span data-ttu-id="de8b6-246">Sie können auch die folgenden Optionen in Ihre ExpressRoute-Bereitstellung integrieren:</span><span class="sxs-lookup"><span data-stu-id="de8b6-246">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="de8b6-247">**Sicherheit an Ihrem Edge:** Um erweiterte Sicherheit für den Datenverkehr bereitzustellen, der über die ExpressRoute-Verbindung gesendet und empfangen wird, z. B. die Überprüfung von Datenverkehr oder Angriffserkennung/Schadsoftwareerkennung, platzieren Sie Ihre Sicherheitsgeräte im Datenverkehrpfad innerhalb Ihres Umkreisnetzwerks oder an der Grenze Ihres Intranets.</span><span class="sxs-lookup"><span data-stu-id="de8b6-247">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="de8b6-p120">**Internet-Datenverkehr für virtuelle Computer:** Um zu verhindern, dass virtuellen Azure-Computern Initiierung von Datenverkehr direkt mit dem Internet stattfindet, kündigen Sie die Standardroute an Microsoft an. Mit dem Internet-Datenverkehr wird über die Verbindung ExpressRoute und über Ihre lokale-Proxy-Server weitergeleitet. Datenverkehr von Azure VMs Azure PaaS-Dienste oder Office 365 wird über die ExpressRoute Verbindung zurück weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p120">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="de8b6-p121">**WAN-Optimierungen:** Sie können WAN-Optimierungen auf beiden Seiten einer privaten Peeringverbindung für ein standortübergreifendes virtuelles Azure-Netzwerk (VNet) bereitstellen. Verwenden Sie innerhalb des Azure VNet ein Netzwerkgerät für die WAN-Optimierung aus dem Azure Marketplace sowie benutzerdefiniertes Routing, um den Verkehr über das Gerät zu leiten.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p121">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="de8b6-p122">**Dienstqualität:** Verwenden Sie DSCP-Werte (Differentiated Services Code Point) in der IPv4-Kopfzeile des Datenverkehrs, um diesen für Sprach-, Video-/interaktive oder eine umfassende Übermittlung zu markieren. Dies ist besonders wichtig für die Microsoft-Peeringbeziehung und Skype for Business Online-Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="de8b6-p122">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="de8b6-255">Weitere Informationen finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="de8b6-255">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="de8b6-256">ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="de8b6-256">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="de8b6-257">Schulung zu Azure ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="de8b6-257">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="de8b6-258">ExpressRoute für Azure</span><span class="sxs-lookup"><span data-stu-id="de8b6-258">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="de8b6-259">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="de8b6-259">Next step</span></span>

[<span data-ttu-id="de8b6-260">Entwerfen von Netzwerken für Microsoft-SaaS</span><span class="sxs-lookup"><span data-stu-id="de8b6-260">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="de8b6-261">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="de8b6-261">See also</span></span>

[<span data-ttu-id="de8b6-262">Microsoft-Cloudnetzwerke für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="de8b6-262">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="de8b6-263">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="de8b6-263">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

