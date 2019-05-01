---
title: Hybrid Cloud-Szenarien für Azure-IaaS
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
description: 'Zusammenfassung: Grundlegendes zur Hybrid Architektur und den Szenarien für die Infrastruktur von Microsoft als Service-(IaaS) Cloud-Angebot in Azure.'
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487636"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="e1c24-103">Hybrid Cloud-Szenarien für Azure-IaaS</span><span class="sxs-lookup"><span data-stu-id="e1c24-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="e1c24-104">**Zusammenfassung:** Verstehen der Hybrid Architektur und Szenarien für die Infrastruktur von Microsoft als Service (IaaS)-basierte Cloud-Angebote in Azure.</span><span class="sxs-lookup"><span data-stu-id="e1c24-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="e1c24-105">Erweitern Sie Ihre lokale Computing-und Identitätsinfrastruktur in die Cloud, indem Sie IT-Arbeitslasten hosten, die in standortübergreifenden Azure Virtual Networks (VNets) laufen.</span><span class="sxs-lookup"><span data-stu-id="e1c24-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="e1c24-106">Architektur des Azure IaaS-Hybrid Szenarios</span><span class="sxs-lookup"><span data-stu-id="e1c24-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="e1c24-107">Abbildung 1 zeigt die Architektur von Microsoft IaaS-basierten Hybrid Szenarien in Azure.</span><span class="sxs-lookup"><span data-stu-id="e1c24-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="e1c24-108">**Abbildung 1: Microsoft IaaS-basierte Hybrid Szenarien in Azure**</span><span class="sxs-lookup"><span data-stu-id="e1c24-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft IaaS-basierte Hybrid Szenarien in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="e1c24-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="e1c24-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="e1c24-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="e1c24-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="e1c24-112">Eine IT-Arbeitslast ist in der Regel eine mehrstufige, hoch verfügbare Anwendung, die aus virtuellen Azure-Computern (VMs) besteht.</span><span class="sxs-lookup"><span data-stu-id="e1c24-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="e1c24-113">Identität</span><span class="sxs-lookup"><span data-stu-id="e1c24-113">Identity</span></span>
    
    <span data-ttu-id="e1c24-114">Fügen Sie Identitäts Server, wie Active Directory-domänenDienste (AD DS), zu der Gruppe von Servern hinzu, die in Azure VNets für die lokale Authentifizierung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-114">Add identity servers, such as Active Directory Domain Services (AD DS) domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="e1c24-115">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="e1c24-115">Network</span></span>
    
    <span data-ttu-id="e1c24-116">Verwenden Sie eine Standort-zu-Standort-VPN-Verbindung über das Internet oder eine Express Route-Verbindung mit privatem Peering zu Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="e1c24-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="e1c24-117">Lokal</span><span class="sxs-lookup"><span data-stu-id="e1c24-117">On-premises</span></span>
    
    <span data-ttu-id="e1c24-118">Enthält Identitäts Server, die mit den Identitäts Servern in Azure synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-118">Contains identity servers that are synchronized with the identity servers running in Azure.</span></span> <span data-ttu-id="e1c24-119">Kann auch Ressourcen enthalten, auf die in Azure ausgeführten VMs zugegriffen werden kann, beispielsweise Speicher-und Systemverwaltungsinfrastruktur.</span><span class="sxs-lookup"><span data-stu-id="e1c24-119">Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="e1c24-120">Verzeichnissynchronisierungsserver für Office 365</span><span class="sxs-lookup"><span data-stu-id="e1c24-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="e1c24-121">Die Verwendung des Verzeichnissynchronisierungsservers von einem Azure-VNet, wie in Abbildung 2 dargestellt, ist ein Beispiel für die Erweiterung der Computing-und Identitätsinfrastruktur auf die Cloud.</span><span class="sxs-lookup"><span data-stu-id="e1c24-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="e1c24-122">**Abbildung 2: Verzeichnissynchronisierungsserver für Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="e1c24-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Verzeichnissynchronisierungsserver für Office 365 in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="e1c24-124">In Abbildung 2 hostet ein lokales Netzwerk eine AD DS-Infrastruktur mit einem Proxy Server und einem Router an seinem Edgeserver.</span><span class="sxs-lookup"><span data-stu-id="e1c24-124">In Figure 2, an on-premises network hosts a AD DS infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="e1c24-125">Der Router stellt eine Verbindung mit einem Azure-Gateway am Rand eines Azure-VNet mit einer Standort-zu-Standort-VPN-oder Express Route-Verbindung her.</span><span class="sxs-lookup"><span data-stu-id="e1c24-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="e1c24-126">Innerhalb des VNet führt ein Verzeichnissynchronisierungsserver Azure AD Connect aus.</span><span class="sxs-lookup"><span data-stu-id="e1c24-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="e1c24-127">Ein Verzeichnissynchronisierungsserver für Office 365 synchronisiert die Liste der Konten in AD DS mit dem Azure AD-Mandanten eines Office 365-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="e1c24-127">A directory synchronization server for Office 365 synchronizes the list of accounts in AD DS with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="e1c24-128">Ein Verzeichnissynchronisierungsserver ist ein Windows-basierter Server, auf dem Azure AD Connect ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e1c24-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="e1c24-129">Für eine schnellere Bereitstellung oder zur Verringerung der Anzahl von lokalen Servern in Ihrer Organisation stellen Sie den Verzeichnissynchronisierungsserver in einem virtuellen Netzwerk (VNet) in Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="e1c24-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="e1c24-130">Der Verzeichnissynchronisierungsserver fragt AD DS nach Änderungen ab und synchronisiert diese dann mit dem Office 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="e1c24-130">The directory synchronization server polls AD DS for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="e1c24-131">Weitere Informationen finden Sie unter [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e1c24-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="e1c24-132">Branchenanwendung</span><span class="sxs-lookup"><span data-stu-id="e1c24-132">Line of business (LOB) application</span></span>

<span data-ttu-id="e1c24-133">Abbildung 3 zeigt die Konfiguration einer Server basierten Branchenanwendung, die in Azure IaaS.</span><span class="sxs-lookup"><span data-stu-id="e1c24-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="e1c24-134">**Abbildung 3: Branchenanwendung in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="e1c24-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Server basierte Branchenanwendung in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="e1c24-136">In Abbildung 3 hostet ein lokales Netzwerk eine Identitätsinfrastruktur und Benutzer.</span><span class="sxs-lookup"><span data-stu-id="e1c24-136">In Figure 3, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="e1c24-137">Sie ist mit einem Azure IaaS-Gateway mit einer Standort-zu-Standort-VPN-oder Express Route-Verbindung verbunden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-137">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="e1c24-138">Azure IaaS hostet ein virtuelles Netzwerk, das die Server der Branchenanwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="e1c24-138">Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="e1c24-139">Sie können LOB-Anwendungen erstellen, die auf Azure-VMs, die sich in Subnetzen einer Azure-VNet in einem Azure-Datencenter (auch als Standort bezeichnet) befinden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="e1c24-140">Da Sie Ihre lokale Infrastruktur im Wesentlichen auf Azure ausdehnen, müssen Sie Ihrem VNets eindeutige private Adressräume zuweisen und ihre lokalen Routingtabellen aktualisieren, um die Erreichbarkeit der einzelnen VNet sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="e1c24-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="e1c24-141">Sobald die Verbindung hergestellt ist, können diese VMs mit Remotedesktopverbindungen oder mit ihrer Systemverwaltungssoftware, genau wie Ihre lokalen Server, verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="e1c24-142">Durch das Konfigurieren öffentlich zugänglicher Ports können diese VMs auch über das Internet von mobilen oder Remotebenutzern aus aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="e1c24-143">Eine Machbarkeitsstudie finden Sie unter [simuliertes standortübergreifendes virtuelles Netzwerk in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e1c24-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="e1c24-144">Attribute von Branchenanwendungen, die auf Azure-VMs gehostet werden, sind folgende:</span><span class="sxs-lookup"><span data-stu-id="e1c24-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="e1c24-145">Mehrere Ebenen</span><span class="sxs-lookup"><span data-stu-id="e1c24-145">Multiple tiers</span></span>
    
    <span data-ttu-id="e1c24-146">Typische Branchenanwendungen verwenden einen mehrstufigen Ansatz.</span><span class="sxs-lookup"><span data-stu-id="e1c24-146">Typical LOB applications use a tiered approach.</span></span> <span data-ttu-id="e1c24-147">Servergruppen bieten Identitäts-, Daten Bank Verarbeitungs-, Anwendungs-und Logik Verarbeitung sowie Front-End-Webserver für Mitarbeiter-oder Kunden Zugriff.</span><span class="sxs-lookup"><span data-stu-id="e1c24-147">Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="e1c24-148">Hohe Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="e1c24-148">High availability</span></span>
    
    <span data-ttu-id="e1c24-149">Typische Branchenanwendungen bieten eine hohe Verfügbarkeit durch die Verwendung von mehreren Servern in jeder Ebene.</span><span class="sxs-lookup"><span data-stu-id="e1c24-149">Typical LOB applications provide high availability by using multiple servers in each tier.</span></span> <span data-ttu-id="e1c24-150">Azure IaaS bietet eine Betriebszeit von 99,9% für Server in Azure-Verfügbarkeits Sätzen.</span><span class="sxs-lookup"><span data-stu-id="e1c24-150">Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="e1c24-151">Lastenverteilung</span><span class="sxs-lookup"><span data-stu-id="e1c24-151">Load distribution</span></span>
    
    <span data-ttu-id="e1c24-152">Um die Last des Netzwerkdatenverkehrs auf mehrere Server in einer Ebene zu verteilen, können Sie einen mit dem Internet verbundenen oder internen Azure-Lastenausgleich verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-152">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer.</span></span> <span data-ttu-id="e1c24-153">Sie können auch eine dedizierte Lastenausgleichs Einheit verwenden, die auf dem Azure Marketplace verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e1c24-153">Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="e1c24-154">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="e1c24-154">Security</span></span>
    
    <span data-ttu-id="e1c24-155">Um Server vor nicht angeforderten eingehenden Datenverkehr aus dem Internet zu schützen, können Sie Azure Network Security Groups verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-155">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups.</span></span> <span data-ttu-id="e1c24-156">Sie können den zulässigen oder verweigerten Datenverkehr für ein Subnetz oder die Netzwerkschnittstelle eines einzelnen virtuellen Computers definieren.</span><span class="sxs-lookup"><span data-stu-id="e1c24-156">You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="e1c24-157">SharePoint Server 2016-Farm in Azure</span><span class="sxs-lookup"><span data-stu-id="e1c24-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="e1c24-158">Ein Beispiel für eine hoch verfügbare mehrstufige Branchenanwendung in Azure ist eine SharePoint Server 2016-Farm, wie in Abbildung 4 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e1c24-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="e1c24-159">**Abbildung 4: eine hoch verfügbare SharePoint Server 2016-Farm in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="e1c24-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Eine SharePoint Server 2016-Farm mit hoher Verfügbarkeit in Azure IaaS](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="e1c24-161">In Abbildung 4 hostet ein lokales Netzwerk eine Identitätsinfrastruktur und Benutzer.</span><span class="sxs-lookup"><span data-stu-id="e1c24-161">In Figure 4, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="e1c24-162">Sie ist mit einem Azure IaaS-Gateway mit einer Standort-zu-Standort-VPN-oder Express Route-Verbindung verbunden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-162">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="e1c24-163">Die Azure-VNet enthält die Server der SharePoint Server 2016-Farm, die separate Ebenen für die Front-End-Server, die Anwendungsserver, den SQL Server-Cluster und die Domänencontroller umfasst.</span><span class="sxs-lookup"><span data-stu-id="e1c24-163">The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="e1c24-164">Diese Konfiguration weist die folgenden Attribute von Branchenanwendungen in Azure auf:</span><span class="sxs-lookup"><span data-stu-id="e1c24-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="e1c24-165">Ebenen</span><span class="sxs-lookup"><span data-stu-id="e1c24-165">Tiers</span></span>
    
    <span data-ttu-id="e1c24-166">Server, auf denen unterschiedliche Rollen in der Farm ausgeführt werden, erstellen die Ebenen, und jede Ebene verfügt über ein eigenes Subnetz.</span><span class="sxs-lookup"><span data-stu-id="e1c24-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="e1c24-167">Hohe Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="e1c24-167">High-availability</span></span>
    
    <span data-ttu-id="e1c24-168">Durch die Verwendung mehrerer Server in jeder Ebene und das Platzieren aller Server einer Ebene in demselben Verfügbarkeits Satz erreicht.</span><span class="sxs-lookup"><span data-stu-id="e1c24-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="e1c24-169">Lastenverteilung</span><span class="sxs-lookup"><span data-stu-id="e1c24-169">Load distribution</span></span>
    
    <span data-ttu-id="e1c24-170">Interne Azure-Lastenausgleichsmodule verteilen den eingehenden Client-Webdatenverkehr an die Front-End-Server (WEB1 und WEB2) und an die Listener-IP-Adresse des SQL Server-Clusters (SQL1, SQL2 und MN1).</span><span class="sxs-lookup"><span data-stu-id="e1c24-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="e1c24-171">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="e1c24-171">Security</span></span>
    
    <span data-ttu-id="e1c24-172">Mit Netzwerk Sicherheitsgruppen für jedes Subnetz können Sie den zulässigen eingehenden und ausgehenden Datenverkehr konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e1c24-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="e1c24-173">Folgen Sie diesem Pfad für die erfolgreiche Einführung:</span><span class="sxs-lookup"><span data-stu-id="e1c24-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="e1c24-174">AusWerten und testen</span><span class="sxs-lookup"><span data-stu-id="e1c24-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="e1c24-175">Informationen zu den Vorteilen der Verwendung von SharePoint Server 2016 in Azure finden Sie unter [SharePoint server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) .</span><span class="sxs-lookup"><span data-stu-id="e1c24-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="e1c24-176">Weitere Informationen finden Sie unter [Intranet SharePoint Server 2016 in Azure dev/Test Environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to Build a simulationed dev/Test Environment</span><span class="sxs-lookup"><span data-stu-id="e1c24-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="e1c24-177">Entwerfen</span><span class="sxs-lookup"><span data-stu-id="e1c24-177">Design</span></span>
    
    <span data-ttu-id="e1c24-178">Weitere Informationen finden Sie unter [Entwerfen einer SharePoint Server 2016-Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) , um einen Prozess zur Ermittlung der Gruppe von Azure IaaS-Netzwerk-, COMPUTE-und Speicherelementen zum Hosten Ihrer Farm und ihrer Einstellungen zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e1c24-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="e1c24-179">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="e1c24-179">Deploy</span></span>
    
    <span data-ttu-id="e1c24-180">Weitere Informationen finden Sie unter [deployIng SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) , um die End-to-End-Konfiguration der hoch Verfügbarkeits Farm in fünf Phasen schrittweise durchlaufen zu können.</span><span class="sxs-lookup"><span data-stu-id="e1c24-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="e1c24-181">Verbundidentität für Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="e1c24-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="e1c24-182">Ein weiteres Beispiel für eine mehrstufige Branchenanwendung mit hoher Verfügbarkeit in Azure ist die Verbundidentität für Office 365.</span><span class="sxs-lookup"><span data-stu-id="e1c24-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="e1c24-183">**Abbildung 5: eine hoch verfügbare Verbund Identitätsinfrastruktur für Office 365 in Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="e1c24-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Eine hoch verfügbare Office 365-Verbund Authentifizierungsinfrastruktur in Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="e1c24-185">In Abbildung 5 hostet ein lokales Netzwerk eine Identitätsinfrastruktur und Benutzer.</span><span class="sxs-lookup"><span data-stu-id="e1c24-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="e1c24-186">Sie ist mit einem Azure IaaS-Gateway mit einer Standort-zu-Standort-VPN-oder Express Route-Verbindung verbunden.</span><span class="sxs-lookup"><span data-stu-id="e1c24-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="e1c24-187">Das Azure-VNet enthält WebProxy Server, Active Directory-Verbunddienste-Server und Active Directory-domänenDienste (AD DS)-Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="e1c24-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="e1c24-188">Diese Konfiguration weist die folgenden Attribute von Branchenanwendungen in Azure auf:</span><span class="sxs-lookup"><span data-stu-id="e1c24-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="e1c24-189">**Ebenen:** Es gibt Ebenen für Webproxyserver, AD FS-Server und AD DS-Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="e1c24-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and AD DS domain controllers.</span></span>
    
- <span data-ttu-id="e1c24-190">**Lastenverteilung:** Ein externes Azure-Lastenausgleichsmodul verteilt die eingehenden Clientauthentifizierungsanforderungen an die Webproxys, und ein internes Azure-Lastenausgleichsmodul verteilt Authentifizierungsanforderungen an die AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="e1c24-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="e1c24-191">Folgen Sie diesem Pfad für die erfolgreiche Einführung:</span><span class="sxs-lookup"><span data-stu-id="e1c24-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="e1c24-192">AusWerten und testen</span><span class="sxs-lookup"><span data-stu-id="e1c24-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="e1c24-193">Informationen zum Erstellen einer simulierten Entwicklungs-und Testumgebung für die Verbundauthentifizierung mit Office 365 finden Sie unter [Federated Identity for your office 365 dev/Test Environment](federated-identity-for-your-office-365-dev-test-environment.md) .</span><span class="sxs-lookup"><span data-stu-id="e1c24-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="e1c24-194">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="e1c24-194">Deploy</span></span>
    
    <span data-ttu-id="e1c24-195">Weitere Informationen finden Sie unter [Deploy High Availability Federated Authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) , um die End-to-End-Konfiguration der AD FS-Infrastruktur mit hoher Verfügbarkeit in fünf Phasen schrittweise zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="e1c24-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="e1c24-196">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e1c24-196">See Also</span></span>

[<span data-ttu-id="e1c24-197">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="e1c24-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="e1c24-198">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="e1c24-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


