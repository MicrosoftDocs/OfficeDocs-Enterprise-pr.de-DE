---
title: Netzwerkfunktionen für die Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 'Zusammenfassung: Hier erfahren Sie die Contoso-Netzwerkinfrastruktur und wie es ExpressRoute für optimierte (RBAC) zu Microsoft Cloud-angeboten verwenden können.'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915220"
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="54f76-103">Netzwerkfunktionen für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="54f76-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="54f76-104">**Zusammenfassung:** Verstehen der Contoso-Netzwerkinfrastruktur und wie es ExpressRoute für optimierte (RBAC) zu Microsoft Cloud-angeboten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="54f76-104">**Summary:** Understand the Contoso networking infrastructure and how it can use ExpressRoute for optimized acccess to Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="54f76-p101">Wenn Sie eine Cloud-inklusive Infrastruktur einführen, realisiert Netzwerktechniker Contoso die Verschiebung in die Möglichkeit, die Netzwerkverkehr zu cloudbasierten Diensten Reisen. Anstatt nur optimieren Datenverkehr auf lokalen Servern und Rechenzentren, muss gleich Aufmerksamkeit für die Optimierung der Datenverkehr von der Kante Internet und über das Internet.</span><span class="sxs-lookup"><span data-stu-id="54f76-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="54f76-107">Contoso Netzwerkinfrastruktur</span><span class="sxs-lookup"><span data-stu-id="54f76-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="54f76-108">Contoso hat die folgende Netzwerkinfrastruktur, die in Abbildung 1 dargestellt ist.
</span><span class="sxs-lookup"><span data-stu-id="54f76-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="54f76-109">**Abbildung 1: WAN-Infrastruktur von Contoso**</span><span class="sxs-lookup"><span data-stu-id="54f76-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![WAN-Infrastruktur von Contoso, die Zentralen, Regionalstellen und Zweigstellen verknüpft](media/Contoso-Poster/Contoso-WW-Net.png)
  
<span data-ttu-id="54f76-111">Abbildung 1 zeigt die weltweiten Contoso-Niederlassungen sowie die WAN-Verbindungen der Regional- und Zweigstellen dazwischen.</span><span class="sxs-lookup"><span data-stu-id="54f76-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="54f76-112">Weitere Elemente des Netzwerks sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="54f76-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="54f76-113">Lokales Netzwerk</span><span class="sxs-lookup"><span data-stu-id="54f76-113">On-premises network</span></span>
    
    <span data-ttu-id="54f76-p102">WAN-Verbindungen verbinden die zentrale Paris mit regionalen Standorten und regionale Büros und Zweigstellen in einer sternförmigen Konfiguration. Innerhalb jeder Office liefern Router Datenverkehr an Hosts oder drahtlose Zugriffspunkte auf Subnetze, die private IP-Adressbereichs verwenden.</span><span class="sxs-lookup"><span data-stu-id="54f76-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="54f76-116">Internetverbindung</span><span class="sxs-lookup"><span data-stu-id="54f76-116">Internet connectivity</span></span>
    
    <span data-ttu-id="54f76-p103">Jede Niederlassung verfügt über eine eigene Internetkonnektivität über einen Proxyserver. Dies wird in der Regel als ein WAN implementiert Link zu einem lokalen ISP, die auch öffentliche IP-Adressen für den Proxyserver bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="54f76-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="54f76-119">Internetauftritt</span><span class="sxs-lookup"><span data-stu-id="54f76-119">Internet presence</span></span>
    
    <span data-ttu-id="54f76-p104">Contoso besitzt den öffentlichen Domänennamen "contoso.com". Die öffentliche Contoso-Website zum Bestellen von Produkten ist eine Gruppe von Servern in einer Internet verbundenen Datencenter in der Paris Campus. Contoso verwendet eine/24 bis / öffentliche IP-Adressbereich im Internet.</span><span class="sxs-lookup"><span data-stu-id="54f76-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="54f76-123">Contoso app-Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="54f76-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="54f76-124">Contoso hat seine Anwendungs- und Serverinfrastruktur für Folgendes konzipiert:



</span><span class="sxs-lookup"><span data-stu-id="54f76-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="54f76-125">**Abbildung 2: Contoso Infrastruktur für die interne Anwendung**</span><span class="sxs-lookup"><span data-stu-id="54f76-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Contosos Infrastruktur für die interne Anwendung](media/Contoso-Poster/App-Infra.png)
  
- <span data-ttu-id="54f76-127">Zweigstellen verwenden lokale Cacheserver, um Dokumente und interne Websites zu speichern, auf die häufig zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="54f76-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="54f76-p105">
Regionalstellen verwenden regionale Anwendungsserver für die Regional- und Zweigstellenbüros. Diese Server werden mit Servern in der Pariser Zentrale synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="54f76-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="54f76-130">Auf dem Pariser Campus befinden sich die Rechenzentren mit den zentralen-Anwendungsservern, die das gesamte Unternehmen bedienen.</span><span class="sxs-lookup"><span data-stu-id="54f76-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="54f76-p106">Für Benutzer in Zweigstellen- oder Regionalbüros können 60 % der von ihnen benötigten Ressourcen von den Zweigstellen- oder Regionalbüroservern bereitgestellt werden.
 Die weiteren 40 % der Ressourcenanforderungen werden über die WAN-Verbindung mit dem Pariser Campus abgedeckt.</span><span class="sxs-lookup"><span data-stu-id="54f76-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="54f76-133">Contoso Netzwerk-Analyse</span><span class="sxs-lookup"><span data-stu-id="54f76-133">Contoso's network analysis</span></span>

<span data-ttu-id="54f76-134">Hier sind die Ergebnisse der Contoso Analyse der Änderungen in ihrem Netzwerk soll, um die verschiedenen Arten von Microsoft Cloud-angeboten, benötigt:</span><span class="sxs-lookup"><span data-stu-id="54f76-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="54f76-135">**SaaS cloud-angeboten: Office 365 und zur Abstimmung Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="54f76-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="54f76-136">**Azure PaaS: Mobile Anwendungen**</span><span class="sxs-lookup"><span data-stu-id="54f76-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="54f76-137">**Azure IaaS: Serverbasierte Arbeitslasten**</span><span class="sxs-lookup"><span data-stu-id="54f76-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="54f76-138">Die erfolgreiche Akzeptanz von SaaS-Diensten durch Benutzer ist von einer hochverfügbaren und leistungsfähigen Konnektivität mit dem Internet oder direkt von Microsoft-Clouddiensten abhängig.
</span><span class="sxs-lookup"><span data-stu-id="54f76-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="54f76-139">Für mobile Benutzer werden deren aktuelle Internetzugänge als ausreichend angenommen.
</span><span class="sxs-lookup"><span data-stu-id="54f76-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="54f76-140">Für Benutzer im Intranet Contoso muss jede Niederlassung analysiert und für den Durchsatz, mit dem Internet und Zeitangaben in Europa-Rechenzentrum von Microsoft Office 365 und zur Abstimmung Dynamics 365-Mandanten hosten optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="54f76-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="54f76-p107">Damit Contoso seine Mobil- und Remotemitarbeiter besser unterstützen kann, werden Legacy-Apps und einige Dateifreigabewebsites überarbeitet und als Azure PaaS-Apps bereitgestellt. Für eine optimale Leistung plant Contoso die Bereitstellung der neuen Apps auf mehreren Azure-Rechenzentren weltweit. Azure Traffic Manager zum Senden von Client-App-Anforderungen (unabhängig davon, ob diese von einem mobilen Benutzer oder einem Computer in dem Büro stammen) an das nächste Azure-Rechenzentrum, das die App hostet.</span><span class="sxs-lookup"><span data-stu-id="54f76-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="54f76-144"> 

Die IT-Abteilung muss PaaS-Anwendungsleistung und -Datenverkehrsverteilung zu ihrer Lösung für die Überwachung der Netzwerkintegrität hinzufügen.
</span><span class="sxs-lookup"><span data-stu-id="54f76-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="54f76-145">Um einige ältere und Archivierungsserver aus den Rechenzentren auf dem Pariser Campus zu entfernen und Server für einen Quartalsabschluss nach Bedarf hinzuzufügen, plant Contoso die Verwendung von virtuellen Computern, die in Azure-Infrastrukturdiensten ausgeführt werden.  

</span><span class="sxs-lookup"><span data-stu-id="54f76-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="54f76-146">Die virtuellen Azure-Netzwerke, zu denen diese Server gehören, müssen für nicht überlappende Adressbereiche, Routing und integriertes DNS ausgelegt werden.

</span><span class="sxs-lookup"><span data-stu-id="54f76-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="54f76-147">Die IT-Abteilung muss diese neuen Server in ihr Netzwerkverwaltungs- und -überwachungssystem einbeziehen.
</span><span class="sxs-lookup"><span data-stu-id="54f76-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="54f76-148">Contoso Verwendung von ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="54f76-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="54f76-p108">ExpressRoute ist eine dedizierte WAN-Verbindung von Ihrem Standort an einen Microsoft Speicherort Peers, der Ihr Netzwerk mit dem Microsoft-Cloud-Netzwerk verbindet. ExpressRoute Verbindungen bieten vorhersehbare Leistung und einer Betriebszeit von 99,9 % Vereinbarung zum SERVICELEVEL. .</span><span class="sxs-lookup"><span data-stu-id="54f76-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="54f76-p109">Sie sind mit einer ExpressRoute-Verbindung mit dem Microsoft-Cloud-Netzwerk und allen Microsoft Datacenter Speicherorten in der gleichen Kontinent verbunden. Der Datenverkehr zwischen den Peers Cloud-Speicherort und dem Ziel-Microsoft-Rechenzentrum wird über das Microsoft Cloud-Netzwerk übertragen.</span><span class="sxs-lookup"><span data-stu-id="54f76-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="54f76-154">**Abbildung 3: Das weltweite Microsoft Cloud-Netzwerk**</span><span class="sxs-lookup"><span data-stu-id="54f76-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![Das weltweite Microsoft Cloud-Netzwerk](media/Contoso-Poster/MS-WW-Cloud.png)
  
<span data-ttu-id="54f76-156">Abbildung 3 zeigt das miteinander verbundene Microsoft Cloud-Netzwerk für die unterschiedlichen Regionen weltweit. </span><span class="sxs-lookup"><span data-stu-id="54f76-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="54f76-p110">Mit ExpressRoute Premium können Sie alle Microsoft-Rechenzentren auf allen Kontinenten von einem beliebigen Microsoft-Peeringstandort auf einem beliebigen Kontinent erreichen. Der Datenverkehr zwischen Kontinenten erfolgt über das Microsoft Cloud-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="54f76-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="54f76-159">Basierend auf der Analyse der aktuellen und zukünftigen Datenverkehr zu Microsoft Cloud-angeboten, hat Contoso eine Bewertung Netzwerk ausgeführt und implementiert eine n: n-ExpressRoute (MPLS-basiert) Verbindung für den Zugriff auf Azure Ressourcen, mit privaten und öffentlichen peering Beziehungen, aus der zentrale Paris zum Microsoft Peers Speicherort in Europa.</span><span class="sxs-lookup"><span data-stu-id="54f76-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="54f76-160">Diese Verbindung bedeutet für die IT-Abteilung von Contoso:</span><span class="sxs-lookup"><span data-stu-id="54f76-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="54f76-161">Gleichbleibende Leistung für die Verwaltung von verteilten Azure PaaS-Apps
</span><span class="sxs-lookup"><span data-stu-id="54f76-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="54f76-p111">Alle von Contoso Anwendungsentwickler und Hauptinfrastruktur IT Administratoren sind in der Paris Campus. Mit Azure PaaS-apps in verschiedenen Azure Rechenzentren auf der ganzen Welt verteilten benötigt Contoso konsistente Leistung aus dem Paris Campus zum Verwalten der apps und ihre Speicherressourcen, die von TB von Dokumenten bestehen.</span><span class="sxs-lookup"><span data-stu-id="54f76-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="54f76-164">Gleichbleibende Leistung für die Verwaltung von Servern in Azure IaaS
</span><span class="sxs-lookup"><span data-stu-id="54f76-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="54f76-p112">Die Administratoren von Contoso Rechenzentrum befinden sich in der Paris Campus und die Servern im Azure bereitgestellt werden sind eine Erweiterung des Datencenters Paris. Contoso benötigt konsistente Leistung auf diese neuen Server für den Zugriff auf ältere apps und Archivspeicher und für die Verarbeitung von Ende des Quartals.</span><span class="sxs-lookup"><span data-stu-id="54f76-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="54f76-167">Contoso Pfad zur cloud-Netzwerke Bereitschaft</span><span class="sxs-lookup"><span data-stu-id="54f76-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="54f76-168">Contoso verwendet die folgenden Schritte, um sein Netzwerk für die Microsoft-Cloud vorzubereiten:</span><span class="sxs-lookup"><span data-stu-id="54f76-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="54f76-169">Optimieren von Mitarbeitercomputern für Internetzugriff
</span><span class="sxs-lookup"><span data-stu-id="54f76-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="54f76-170">Einzelne Computer werden überprüft werden, um sicherzustellen, dass Folgendes in neuester Version installiert ist: TCP/IP-Stapel, Browser, NIC-Treiber sowie Sicherheits- und Betriebssystemupdates.
</span><span class="sxs-lookup"><span data-stu-id="54f76-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="54f76-171">Analysieren der Internetnutzung in jedem Büro und ggf. mehr Bandbreite</span><span class="sxs-lookup"><span data-stu-id="54f76-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="54f76-172">
Jedes Büro wird hinsichtlich seiner aktuellen Internetnutzung analysiert, und die Bandbreite der WAN-Verbindung wird erhöht, wenn die Auslastung bei 70 % oder darüber liegt.
</span><span class="sxs-lookup"><span data-stu-id="54f76-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="54f76-173">Analysieren der DMZ-Systeme in jedem Büro hinsichtlich optimaler Leistung
</span><span class="sxs-lookup"><span data-stu-id="54f76-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="54f76-p113">Firewalls, Angriffserkennungssysteme und andere Systeme im Internetpfad werden hinsichtlich optimaler Leistung analysiert.
 Proxyserver werden nach Bedarf aktualisiert (Update oder Upgrade).</span><span class="sxs-lookup"><span data-stu-id="54f76-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="54f76-176">Hinzufügen von ExpressRoute Premium für den Pariser Campus</span><span class="sxs-lookup"><span data-stu-id="54f76-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="54f76-177">Bietet einheitlichen Zugriff auf Azure-Ressourcen für die Verwaltung von Azure PaaS- und IaaS-Arbeitslasten.</span><span class="sxs-lookup"><span data-stu-id="54f76-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="54f76-178">Erstellen und Testen eines Azure Traffic Manager-Profils für Azure PaaS-Apps</span><span class="sxs-lookup"><span data-stu-id="54f76-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="54f76-179">Es wird ein Azure Traffic Manager-Profil getestet, in dem die Leistungsroutingmethode verwendet wird, um Kenntnisse zur Verteilung von Internetdatenverkehr an regionale Standorte zu erlangen.
</span><span class="sxs-lookup"><span data-stu-id="54f76-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="54f76-180">Reservieren von privatem Adressraum für virtuelle Azure-Netzwerke
</span><span class="sxs-lookup"><span data-stu-id="54f76-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="54f76-181">Reservieren Sie entsprechend der Anzahl von prognostizierten kurz- und langfristigen Servern in Azure IaaS privaten Adressraum für virtuelle Azure-Netzwerke und deren Subnetze.
</span><span class="sxs-lookup"><span data-stu-id="54f76-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="54f76-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="54f76-182">See Also</span></span>

[<span data-ttu-id="54f76-183">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="54f76-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="54f76-184">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="54f76-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="54f76-185">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="54f76-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



