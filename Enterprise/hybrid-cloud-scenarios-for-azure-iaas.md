---
title: Hybrid Cloud-Szenarien für Azure IaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Zusammenfassung: Grundlegendes zu den Hybrid-Architektur und Szenarien für Microsoft Infrastruktur als Dienst (IaaS)-Cloud-angeboten in Azure basiert.'
ms.openlocfilehash: bb6611f51cc346273438e879d957597fe3299c58
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123242"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="63661-103">Hybrid Cloud-Szenarien für Azure-IaaS</span><span class="sxs-lookup"><span data-stu-id="63661-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="63661-104">**Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für die Microsoft-Infrastruktur als Dienst (IaaS)-Cloud-angeboten in Azure basiert.</span><span class="sxs-lookup"><span data-stu-id="63661-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="63661-105">Erweitern Sie Ihre lokale Computing- und Identitätsinfrastruktur in die Cloud, indem Sie IT-Arbeitslasten hosten, die in standortübergreifenden virtuellen Azure-Netzwerken (VNets) ausgeführt werden. </span><span class="sxs-lookup"><span data-stu-id="63661-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="63661-106">Architektur für Azure IaaS-Hybridszenario</span><span class="sxs-lookup"><span data-stu-id="63661-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="63661-107">Abbildung 1 zeigt die Architektur der IaaS-basierten Hybridszenarien von Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="63661-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="63661-108">**Abbildung 1: Microsoft IaaS-basierte Hybridszenarien in Azure**</span><span class="sxs-lookup"><span data-stu-id="63661-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft IaaS-basierte Hybridszenarien in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="63661-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="63661-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="63661-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="63661-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="63661-112">Eine IT-Arbeitslast ist üblicherweise eine mehrstufige hochverfügbare Anwendung, die aus virtuellen Azure-Computern besteht.</span><span class="sxs-lookup"><span data-stu-id="63661-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="63661-113">Identität</span><span class="sxs-lookup"><span data-stu-id="63661-113">Identity</span></span>
    
    <span data-ttu-id="63661-114">Fügen Sie, um lokale Authentifizierung zu ermöglichen, Identitätsserver, etwa Windows Server Active Directory-Domänencontroller, zur Gruppe der Server hinzu, die in Azure VNets (virtuelle Netzwerke) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="63661-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="63661-115">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="63661-115">Network</span></span>
    
    <span data-ttu-id="63661-116">Verwenden Sie entweder eine VPN-Verbindung zwischen Standorten über das Internet oder eine ExpressRoute-Verbindung mit privatem Peering zu Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="63661-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="63661-117">Lokal</span><span class="sxs-lookup"><span data-stu-id="63661-117">On-premises</span></span>
    
    <span data-ttu-id="63661-p101">Enthält Identitätsserver, die mit in Azure ausgeführten Identitätsservern synchronisiert werden. Kann auch Ressourcen enthalten, auf die in Azure ausgeführte virtuelle Computer zugreifen können, z. B. Speicher und Systemverwaltungsinfrastruktur.</span><span class="sxs-lookup"><span data-stu-id="63661-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="63661-120">DirSync-Server für Office 365</span><span class="sxs-lookup"><span data-stu-id="63661-120">DirSync server for Office 365</span></span>

<span data-ttu-id="63661-121">Ein Beispiel für die Ausweitung Ihrer Computing- und Identitätsinfrastruktur auf die Cloud ist die Ausführung Ihres Verzeichnissynchronisierungsservers (DirSync-Server) in einem Azure-VNet wie in Abbildung 2 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="63661-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="63661-122">**Abbildung 2: DirSync-Server für Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="63661-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![DirSync-Server für Office 365 in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="63661-p102">In Abbildung 2 hostet einer lokalen Netzwerk eine Windows Azure AD-Infrastruktur mit einer Proxyserver und Router den Rand. Der Router eine Verbindung mit einer Azure Gateway am Rand eines Azure VNet mit einer Standort-zu-Standort-VPN- oder ExpressRoute-Verbindung. Innerhalb der VNet führt ein Dirsync-Server Azure Active Directory verbinden.</span><span class="sxs-lookup"><span data-stu-id="63661-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="63661-127">Ein DirSync-Server für Office 365 synchronisiert die Liste der Konten in Windows Server AD mit dem Azure AD-Mandanten eines Office 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="63661-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="63661-p103">DirSync-Server sind Windows-basierte Server, auf denen Azure AD Connect ausgeführt wird. Wenn Sie Ihren DirSync-Server in einem virtuellen Netzwerk (VNet) in Azure IaaS bereitstellen, ermöglicht das eine beschleunigte Ressourcenbereitstellung und eine Reduzierung der Anzahl lokaler Server in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="63661-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="63661-130">Der DirSync-Server fragt regelmäßig Änderungen von Windows Server AD ab und synchronisiert diese Änderungen mit dem Office 365-Abonnement</span><span class="sxs-lookup"><span data-stu-id="63661-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="63661-131">Weitere Informationen finden Sie unter [Bereitstellen von Office 365 Directory-Synchronisierung in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="63661-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="63661-132">Branchenanwendung</span><span class="sxs-lookup"><span data-stu-id="63661-132">Line of business (LOB) application</span></span>

<span data-ttu-id="63661-133">Abbildung 3 zeigt die Konfiguration einer serverbasierten Branchenanwendung, die in Azure IaaS ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="63661-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="63661-134">**Abbildung 3: Branchenanwendung in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="63661-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Serverbasierte Branchenanwendung in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="63661-p104">In Abbildung 3 sehen Sie ein lokales Netzwerk, das eine Identitätsinfrastruktur und Benutzer hostet. Das Netzwerk ist über ein Standort-zu-Standort-VPN oder eine ExpressRoute-Verbindung mit einem Azure IaaS-Gateway verbunden. Azure IaaS hostet ein virtuelles Netzwerk mit den Servern der Branchenanwendung.</span><span class="sxs-lookup"><span data-stu-id="63661-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="63661-139">Sie können Branchenanwendungen erstellen, die auf virtuellen Azure-Computern ausgeführt werden, die sich in Subnetzen eines virtuellen Azure-Netzwerks in einem Azure-Rechenzentrum (auch als Standort bezeichnet) befinden. 


</span><span class="sxs-lookup"><span data-stu-id="63661-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="63661-140">Da Sie im Grundsatz Ihre lokale Infrastruktur auf Azure erweitern, müssen Sie Ihren virtuellen Netzwerken (VNets) einen eindeutigen privaten Adressraum zuweisen und Ihre lokalen Routingtabellen aktualisieren, damit Erreichbarkeit jedes VNets sichergestellt ist.</span><span class="sxs-lookup"><span data-stu-id="63661-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="63661-141">Sobald es Verbindungen mit diesen virtuellen Computern gibt, können diese über Remotedesktopverbindungen oder mit Ihrer Systemverwaltungssoftware genau so verwaltet werden wie Ihre lokalen Server.</span><span class="sxs-lookup"><span data-stu-id="63661-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="63661-142">Durch Konfigurieren von öffentlich verfügbar gemachten Ports können auch mobile oder Remotebenutzer über das Internet auf diese virtuellen Computer zugreifen.</span><span class="sxs-lookup"><span data-stu-id="63661-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="63661-143">Informationen zur Konfiguration einer Machbarkeitsstudie finden Sie unter [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="63661-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="63661-144">Attribute von Branchenanwendungen, die auf virtuellen Azure-Computern gehostet werden, sind folgende:</span><span class="sxs-lookup"><span data-stu-id="63661-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="63661-145">Mehrere Stufen</span><span class="sxs-lookup"><span data-stu-id="63661-145">Multiple tiers</span></span>
    
    <span data-ttu-id="63661-p105">Für normale Branchenanwendungen wird ein mehrstufiger Ansatz verwendet. Gruppen von Servern erledigen Identitäts-, Datenbank-, Anwendungs- und Logikverarbeitung und stellen Front-End-Webserver für Mitarbeiter- oder Kundenzugriff bereit. </span><span class="sxs-lookup"><span data-stu-id="63661-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="63661-148">Hohe Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="63661-148">High availability</span></span>
    
    <span data-ttu-id="63661-p106">Übliche Branchenanwendungen bieten Hochverfügbarkeit, indem auf jeder Stufe mehrere Server verwendet werden. Azure IaaS bietet eine SLA von 99,9 % zu Betriebszeit für Server in Azure-Verfügbarkeitssets. </span><span class="sxs-lookup"><span data-stu-id="63661-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="63661-151">Lastverteilung</span><span class="sxs-lookup"><span data-stu-id="63661-151">Load distribution</span></span>
    
    <span data-ttu-id="63661-p107">Um die Last des Netzwerkdatenverkehrs auf mehrere Server auf einer Schicht zu verteilen, können Sie einen internetbezogenen oder einen internen Azure-Lastenausgleich (Load Balancer) verwenden. Alternativ können Sie ein dediziertes Lastenausgleichsgerät verwenden, das aus dem Azure Marketplace verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="63661-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="63661-154">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="63661-154">Security</span></span>
    
    <span data-ttu-id="63661-p108">Um Server vor unerwünschtem eingehenden Datenverkehr aus dem Internet zu schützen, können Sie Azure-Netzwerksicherheitsgruppen verwenden. Sie können zulässigen oder zurückgewiesenen Datenverkehr für ein Subnetz oder die Netzwerkschnittstelle eines einzelnen virtuellen Computers definieren.</span><span class="sxs-lookup"><span data-stu-id="63661-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="63661-157">SharePoint Server 2016-Farm in Azure</span><span class="sxs-lookup"><span data-stu-id="63661-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="63661-158">Ein Beispiel für eine hoch verfügbare Multi-Tier-Branchenanwendung in Azure ist eine SharePoint Server 2016-Farm wie in Abbildung 4 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="63661-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="63661-159">**Abbildung 4: Hoch verfügbare SharePoint Server 2016-Farm in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="63661-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Hoch verfügbare SharePoint Server 2016-Farm in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="63661-p109">In Abbildung 4 hostet ein lokales Netzwerk eine Identitätsinfrastruktur und Benutzer. Das Netzwerk ist über ein Standort-zu-Standort-VPN oder eine ExpressRoute-Verbindung mit einem Azure IaaS-Gateway verbunden. Das Azure-VNet enthält die Server der SharePoint Server 2016-Farm. Dabei sind die Front-End-Server, die Anwendungsserver, der SQL Server-Cluster und die Domänencontroller jeweils auf unterschiedlichen Stufen (Tiers) platziert.</span><span class="sxs-lookup"><span data-stu-id="63661-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="63661-164">In einer solchen Konfiguration haben die Branchenanwendungen in Azure die folgenden Attribute: </span><span class="sxs-lookup"><span data-stu-id="63661-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="63661-165">Stufen</span><span class="sxs-lookup"><span data-stu-id="63661-165">Tiers</span></span>
    
    <span data-ttu-id="63661-166">Die verschiedenen Stufen stehen für die verschiedenen Server mit ihren jeweils eigenen Rollen innerhalb der Farm. Jede Stufe hat ein eigenes Subnetz.
</span><span class="sxs-lookup"><span data-stu-id="63661-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="63661-167">Hohe Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="63661-167">High-availability</span></span>
    
    <span data-ttu-id="63661-168">Hohe Verfügbarkeit wird erreicht, indem Sie auf jeder Stufe mindestens zwei Server implementieren und alle Server einer Stufe in derselben Verfügbarkeitsgruppe platzieren.</span><span class="sxs-lookup"><span data-stu-id="63661-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="63661-169">Lastverteilung</span><span class="sxs-lookup"><span data-stu-id="63661-169">Load distribution</span></span>
    
    <span data-ttu-id="63661-170">Die internen Load Balancer in Azure verteilen den eingehenden Clientwebverkehr an die Front-End-Server (WEB1 und WEB2) und die Listener-IP-Adresse des SQL Server-Clusters (SQL1, SQL2 und MN1).</span><span class="sxs-lookup"><span data-stu-id="63661-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="63661-171">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="63661-171">Security</span></span>
    
    <span data-ttu-id="63661-172">Mithilfe von Netzwerksicherheitsgruppen können Sie für jedes Subnetz festlegen, welcher eingehende und ausgehende Datenverkehr erlaubt ist.</span><span class="sxs-lookup"><span data-stu-id="63661-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="63661-173">Gehen Sie für eine erfolgreiche Implementierung wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="63661-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="63661-174">Evaluieren und experimentieren</span><span class="sxs-lookup"><span data-stu-id="63661-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="63661-175">Finden Sie unter [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) zu verstehen, die Vorteile der Ausführung von SharePoint Server 2016 in Azure.</span><span class="sxs-lookup"><span data-stu-id="63661-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="63661-176">Finden Sie unter [Intranet SharePoint Server 2016 in Azure Test-/Umgebung](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) zum Erstellen einer simulierten Test-/-Umgebung</span><span class="sxs-lookup"><span data-stu-id="63661-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="63661-177">Entwerfen</span><span class="sxs-lookup"><span data-stu-id="63661-177">Design</span></span>
    
    <span data-ttu-id="63661-178">Finden Sie unter [Entwerfen einer SharePoint Server 2016 Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) , um einen Vorgang zum Bestimmen des Satz von Azure IaaS-Netzwerke, Compute und Storage-Elemente zum Hosten Ihrer Farm und ihrer Einstellungen für die schrittweise.</span><span class="sxs-lookup"><span data-stu-id="63661-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="63661-179">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="63661-179">Deploy</span></span>
    
    <span data-ttu-id="63661-180">Finden Sie unter [Bereitstellen von SharePoint Server 2016 mit SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) schrittweise durchlaufen die End-to-End-Konfiguration der Farm, die hohe Verfügbarkeit in fünf Phasen.</span><span class="sxs-lookup"><span data-stu-id="63661-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="63661-181">Identitätsverbund für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="63661-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="63661-182">Ein weiteres Beispiel für eine mehrstufige, hochverfügbar LOB-Anwendung in Azure ist Identitätsverbund für Office 365.</span><span class="sxs-lookup"><span data-stu-id="63661-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="63661-183">**Abbildung 5: Eine hohe Verfügbarkeit Identitätsverbund-Infrastruktur für Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="63661-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Ein hoher Verfügbarkeit von Office 365 federated Authentifizierungsinfrastruktur in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="63661-p110">In Abbildung 5 hostet einer lokalen Netzwerk eine Identitätsinfrastruktur und Benutzer. Es ist mit einem Azure IaaS-Gateway mit einer Standort-zu-Standort-VPN- oder ExpressRoute Verbindung verbunden. Der Azure-VNet enthält Web Proxy-Server, Active Directory-Verbunddienste (AD FS) Server und Windows Server Active Directory (AD)-Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="63661-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="63661-188">In einer solchen Konfiguration haben die Branchenanwendungen in Azure die folgenden Attribute: </span><span class="sxs-lookup"><span data-stu-id="63661-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="63661-189">**Ebenen:** Ebenen für Web-Proxyserver, AD FS-Server und Windows Server Active Directory-Domänencontroller sind vorhanden.</span><span class="sxs-lookup"><span data-stu-id="63661-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="63661-190">**Verteilung laden:** Ein externe Azure System zum Lastenausgleich verteilt die eingehenden Clientanforderungen für die Authentifizierung an der Webproxys und eine interne Azure System zum Lastenausgleich verteilt authentifizierungsanforderungen an die AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="63661-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="63661-191">Gehen Sie für eine erfolgreiche Implementierung wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="63661-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="63661-192">Evaluieren und experimentieren</span><span class="sxs-lookup"><span data-stu-id="63661-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="63661-193">Finden Sie unter [Federated Identität für die Office 365-Umgebung](federated-identity-for-your-office-365-dev-test-environment.md) Test-/eine simulierten Test-/Umgebung für Verbundauthentifizierung mit Office 365 erstellen.</span><span class="sxs-lookup"><span data-stu-id="63661-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="63661-194">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="63661-194">Deploy</span></span>
    
    <span data-ttu-id="63661-195">Finden Sie unter [Deploy hohe Verfügbarkeit Verbundauthentifizierung für Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) schrittweise durchlaufen die End-to-End-Konfiguration die hohe Verfügbarkeit AD FS-Infrastruktur in fünf Phasen.</span><span class="sxs-lookup"><span data-stu-id="63661-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="63661-196">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="63661-196">See Also</span></span>

[<span data-ttu-id="63661-197">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="63661-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="63661-198">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="63661-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


