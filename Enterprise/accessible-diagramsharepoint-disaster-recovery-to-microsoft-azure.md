---
title: Zugängliches Diagramm – SharePoint-Notfallwiederherstellung in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „SharePoint-Notfallwiederherstellung in Microsoft Azure“.
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487721"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="90a1b-103">Zugängliches Diagramm – SharePoint-Notfallwiederherstellung in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="90a1b-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="90a1b-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms namens SharePoint Disaster Recovery to Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="90a1b-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="90a1b-105">Dieses Poster zeigt Beispiele von Architekturen zum Erstellen einer Wiederherstellungsumgebung in Azure. </span><span class="sxs-lookup"><span data-stu-id="90a1b-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="90a1b-106">Lokale Umgebung mit einer Azure-Wiederherstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="90a1b-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="90a1b-107">Das Diagramm zeigt ein Architekturbeispiel für die Produktionsumgebung einer lokalen Umgebung, die Azure für die Wiederherstellung verwendet. </span><span class="sxs-lookup"><span data-stu-id="90a1b-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="90a1b-108">Lokale Produktionsumgebung</span><span class="sxs-lookup"><span data-stu-id="90a1b-108">On-premises production environment</span></span>

<span data-ttu-id="90a1b-109">Das zugehörige Diagramm zeigt eine Liveproduktionsumgebung mit vier Serverebenen in einer Serverfarm. </span><span class="sxs-lookup"><span data-stu-id="90a1b-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="90a1b-110">Ebene 1</span><span class="sxs-lookup"><span data-stu-id="90a1b-110">Tier 1</span></span>

<span data-ttu-id="90a1b-p101">Diese Ebene enthält zwei Server für Front-End-Dienste und Abfrageverarbeitung. Eine Indexpartition stellt ein Replikat der beiden Server bereit. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="90a1b-113">Ebene 2</span><span class="sxs-lookup"><span data-stu-id="90a1b-113">Tier 2</span></span>

<span data-ttu-id="90a1b-114">Diese Ebene enthält zwei Servern für verteilten Cache. </span><span class="sxs-lookup"><span data-stu-id="90a1b-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="90a1b-115">Ebene 3</span><span class="sxs-lookup"><span data-stu-id="90a1b-115">Tier 3</span></span>

<span data-ttu-id="90a1b-p102">Diese Ebene enthält gibt drei Server. Jeder Server bietet die folgenden Dienste: </span><span class="sxs-lookup"><span data-stu-id="90a1b-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="90a1b-118">Back-End-Dienste </span><span class="sxs-lookup"><span data-stu-id="90a1b-118">Backend services</span></span> 
    
- <span data-ttu-id="90a1b-119">Administrator</span><span class="sxs-lookup"><span data-stu-id="90a1b-119">Admin</span></span> 
    
- <span data-ttu-id="90a1b-120">Workflow-Manager</span><span class="sxs-lookup"><span data-stu-id="90a1b-120">Workflow manager</span></span> 
    
- <span data-ttu-id="90a1b-121">Durchforstungsdatenbank</span><span class="sxs-lookup"><span data-stu-id="90a1b-121">Crawl</span></span> 
    
- <span data-ttu-id="90a1b-122">Inhaltsverarbeitung</span><span class="sxs-lookup"><span data-stu-id="90a1b-122">Content processing</span></span> 
    
- <span data-ttu-id="90a1b-123">Analyse</span><span class="sxs-lookup"><span data-stu-id="90a1b-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="90a1b-124">Ebene 4</span><span class="sxs-lookup"><span data-stu-id="90a1b-124">Tier 4</span></span>

<span data-ttu-id="90a1b-p103">Diese Ebene enthält zwei Server. Beide Server haben drei Verfügbarkeitsgruppen, wie nachfolgend erläutert: </span><span class="sxs-lookup"><span data-stu-id="90a1b-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="90a1b-127">Verfügbarkeitsgruppe 1 stellt Suchfunktionen bereit. </span><span class="sxs-lookup"><span data-stu-id="90a1b-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="90a1b-128">Verfügbarkeitsgruppe 2 stellt Inhalte, Konfiguration und Dienstanwendungen bereit. </span><span class="sxs-lookup"><span data-stu-id="90a1b-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="90a1b-129">Verfügbarkeitsgruppe 3 stellte Inhalte bereit. </span><span class="sxs-lookup"><span data-stu-id="90a1b-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="90a1b-p104">Diese Ebene enthält auch einen Dateifreigabeserver. Die Server der Ebene 4 kommunizieren per Protokollversand mit diesem Server. Dieser Server kommuniziert seinerseits durch DFS-Replikation (DFSR, Distributed File System Replication) mit einem Dateifreigabeserver in der betriebsbereiten Azure-Wiederherstellungsumgebung, wie im folgenden Abschnitt beschrieben. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="90a1b-133">Azure-Wiederherstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="90a1b-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="90a1b-134">Betriebsbereite Umgebung, in der virtuelle Computer ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="90a1b-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="90a1b-p105">Das zugehörige Diagramm zeigt die lokale Umgebung, die in der Azure-Wiederherstellungsumgebung genau repliziert wird. Der Dateifreigabeserver in dieser Umgebung ist durch DFSR mit der lokalen Umgebung verknüpft. DFSR überträgt Protokolle über den Dateifreigabeserver aus der Produktionsumgebung in die Wiederherstellungsumgebung. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="90a1b-138">Übersicht</span><span class="sxs-lookup"><span data-stu-id="90a1b-138">Overview</span></span>

<span data-ttu-id="90a1b-139">Die Notfallwiederherstellungsumgebung für eine lokale SharePoint 2013-Farm kann in Azure gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="90a1b-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="90a1b-140"> Azure-Infrastrukturdienste stellt ein sekundäres Datencenter zur Verfügung. </span><span class="sxs-lookup"><span data-stu-id="90a1b-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="90a1b-141">Zahlen Sie nur für die Ressourcen, die Sie tatsächlich nutzen. </span><span class="sxs-lookup"><span data-stu-id="90a1b-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="90a1b-142">Kleine Wiederherstellungsfarmen können nach einem Notfall horizontal hochskaliert werden, um Skalierungs- und Kapazitätsziele zu erreichen. </span><span class="sxs-lookup"><span data-stu-id="90a1b-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="90a1b-143">Die Wiederherstellungsfarm in Azure ist so konfiguriert, dass sie so identisch wie möglich mit der lokalen Produktionsfarm ist. </span><span class="sxs-lookup"><span data-stu-id="90a1b-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="90a1b-144">Gleiche Zuordnung von Serverrollen</span><span class="sxs-lookup"><span data-stu-id="90a1b-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="90a1b-145">Gleiche Konfiguration von Anpassungen </span><span class="sxs-lookup"><span data-stu-id="90a1b-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="90a1b-146">Gleiche Konfiguration von Suchfunktionen (diese können sich auf einer kleinere Version der Produktionsfarm befinden) </span><span class="sxs-lookup"><span data-stu-id="90a1b-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="90a1b-147">Protokollversand und DFSR werden verwendet, um Datenbanksicherungen und Transaktionsprotokolle in die Azure-Farm zu kopieren. </span><span class="sxs-lookup"><span data-stu-id="90a1b-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="90a1b-p106">DFSR überträgt Protokolle aus der Produktionsumgebung in die Wiederherstellungsumgebung. In einem WAN-Szenario ist DFSR effizienter als das direkte Versenden der Protokolle an den sekundären Server in Azure. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="90a1b-150">Protokolle werden auf den Azure-basierten SQL Server-Computern wiedergegeben. </span><span class="sxs-lookup"><span data-stu-id="90a1b-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="90a1b-151">Die per Protokollversand verschickten Datenbanken werden erst dann an die Farm angefügt, wenn eine Wiederherstellung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="90a1b-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="90a1b-152">Failoververfahren: </span><span class="sxs-lookup"><span data-stu-id="90a1b-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="90a1b-153">Beenden Sie den Protokollversand.</span><span class="sxs-lookup"><span data-stu-id="90a1b-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="90a1b-154">Lassen Sie keinen Datenverkehr zur primären Farm mehr zu.</span><span class="sxs-lookup"><span data-stu-id="90a1b-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="90a1b-155">Geben Sie die letzten Transaktionsprotokolle wieder.</span><span class="sxs-lookup"><span data-stu-id="90a1b-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="90a1b-156">Fügen Sie die Inhaltsdatenbanken an die Farm an.</span><span class="sxs-lookup"><span data-stu-id="90a1b-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="90a1b-157">Starten Sie eine vollständige Durchforstung.</span><span class="sxs-lookup"><span data-stu-id="90a1b-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="90a1b-158">Stellen Sie Dienstanwendungen aus der replizierten Services-Datenbanken wieder her.</span><span class="sxs-lookup"><span data-stu-id="90a1b-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="90a1b-159">Zu den Wiederherstellungszielen dieser Lösung gehören: </span><span class="sxs-lookup"><span data-stu-id="90a1b-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="90a1b-160">Websites und Inhalte</span><span class="sxs-lookup"><span data-stu-id="90a1b-160">Sites and content</span></span> 
    
- <span data-ttu-id="90a1b-161">Suche (erneut durchforstet, kein Suchverlauf) </span><span class="sxs-lookup"><span data-stu-id="90a1b-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="90a1b-162">Dienste</span><span class="sxs-lookup"><span data-stu-id="90a1b-162">Services</span></span>
    
<span data-ttu-id="90a1b-163">Zusätzliche Punkte, die von Microsoft Consulting Services oder einem Partner übernommen werden können: </span><span class="sxs-lookup"><span data-stu-id="90a1b-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="90a1b-164">Synchronisieren benutzerdefinierter Farmlösungen</span><span class="sxs-lookup"><span data-stu-id="90a1b-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="90a1b-165">Verbindungen mit lokalen Datenquellen (Business Data Connectivity (BDC) und Suchinhaltsquellen) </span><span class="sxs-lookup"><span data-stu-id="90a1b-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="90a1b-166">Wiederherstellungsszenarien für die Suchfunktion</span><span class="sxs-lookup"><span data-stu-id="90a1b-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="90a1b-167">Recovery Time Objectives (RTO, angestrebte Wiederherstellungsdauer) Recovery Point Objectives (RPO, angestrebter Wiederherstellungszeitpunkt)</span><span class="sxs-lookup"><span data-stu-id="90a1b-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="90a1b-168">Verzögert betriebsbereite Umgebung, in der virtuelle Computer ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="90a1b-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="90a1b-169">Verzögert betriebsbereite Umgebungen brauchen länger für den Start, sind jedoch kostengünstiger. </span><span class="sxs-lookup"><span data-stu-id="90a1b-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="90a1b-p107">Die Farm ist vollständig erstellt, aber die virtuellen Computer werden nach Erstellung der Farm angehalten. Sie zahlen nur Verarbeitungskosten, wenn die virtuellen Computer ausgeführt werden, es fallen jedoch Speicher- und Netzwerkübertragungskosten an. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="90a1b-172">Bei einem Notfall werden alle virtuellen Computer in der Farm gestartet und repariert. </span><span class="sxs-lookup"><span data-stu-id="90a1b-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="90a1b-173">Sicherungen und Transaktionsprotokolle werden auf die Farmdatenbanken angewendet. </span><span class="sxs-lookup"><span data-stu-id="90a1b-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="90a1b-174">In der folgenden Liste werden zusätzliche Verfahren für verzögert betriebsbereite Umgebungen beschrieben: </span><span class="sxs-lookup"><span data-stu-id="90a1b-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="90a1b-175">Schalten Sie virtuelle Computer regelmäßig ein, um die Umgebung zu reparieren, zu aktualisieren und zu überprüfen. </span><span class="sxs-lookup"><span data-stu-id="90a1b-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="90a1b-176">Führen Sie Verfahren zum Aktualisieren von DNS- und IP-Adressen aus. </span><span class="sxs-lookup"><span data-stu-id="90a1b-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="90a1b-177">Richten Sie SQL AlwaysOn nach einem Failover ein. </span><span class="sxs-lookup"><span data-stu-id="90a1b-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="90a1b-p108">Das zugehörige Diagramm zeigt eine replizierte Wiederherstellungsumgebung auf virtuellen Computern. Nach einem Failover zu einer verzögert betriebsbereiten Umgebung werden alle virtuellen Computer gestartet, und die Verfügbarkeitsgruppen werden mithilfe von Wiedergabeprotokollen konfiguriert, um die Datenbankserver verfügbar zu machen. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="90a1b-180">SharePoint-Wiederherstellungsumgebung in Azure</span><span class="sxs-lookup"><span data-stu-id="90a1b-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="90a1b-181">Entwerfen und erstellen Sie die Failoverumgebung in Azure. </span><span class="sxs-lookup"><span data-stu-id="90a1b-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="90a1b-182">Erstellen Sie ein virtuelles Netzwerk in Microsoft Azure. </span><span class="sxs-lookup"><span data-stu-id="90a1b-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="90a1b-p109">Verbinden Sie das lokale Netzwerk über eine Standort-zu-Standort-VPN-Verbindung mit dem virtuellen Netzwerk in Azure. Diese Verbindung verwendet ein dynamisches Gateway in Azure. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="90a1b-p110">Stellen Sie mindestens einen Domänencontroller für das virtuelle Azure-Netzwerk bereit, und konfigurieren Sie diesen für die Arbeit mit der lokalen Domäne. Diese Domänencontroller sind Katalogserver. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="90a1b-187">Passen Sie die SharePoint-Farm für Clouddienste und Verfügbarkeitsgruppen an.  </span><span class="sxs-lookup"><span data-stu-id="90a1b-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="90a1b-188">Stellen Sie die SharePoint-Farm sowie einen Dateiserver zum Hosten von Dateifreigaben bereit. </span><span class="sxs-lookup"><span data-stu-id="90a1b-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="90a1b-189">Richten Sie Protokollversand und DFSR zwischen der lokalen Umgebung und der Azure-basierten Wiederherstellungsumgebung ein. </span><span class="sxs-lookup"><span data-stu-id="90a1b-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="90a1b-190">Das zugehörige Diagramm zeigt die lokale Umgebung und das virtuelle Azure-Netzwerk mit den folgenden Features: </span><span class="sxs-lookup"><span data-stu-id="90a1b-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="90a1b-191">Lokale Umgebung</span><span class="sxs-lookup"><span data-stu-id="90a1b-191">On-premises environment</span></span>

- <span data-ttu-id="90a1b-192">Windows Server 2012 RRAS </span><span class="sxs-lookup"><span data-stu-id="90a1b-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="90a1b-193">Active Directory-Server</span><span class="sxs-lookup"><span data-stu-id="90a1b-193">Active Directory server</span></span> 
    
<span data-ttu-id="90a1b-194">Die Schnittstelle zwischen dem lokalen Netzwerk und dem virtuellen Azure-Netzwerk bildet ein VPN-Gateway (virtuelles privates Netzwerk). </span><span class="sxs-lookup"><span data-stu-id="90a1b-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="90a1b-195">Virtuelles Azure-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="90a1b-195">Azure virtual network</span></span>

<span data-ttu-id="90a1b-196">Das VPN-Gateway hat eine Schnittstelle mit einem aktiven VPN-Gatewaysubnetz. </span><span class="sxs-lookup"><span data-stu-id="90a1b-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="90a1b-197">Das virtuelle Azure-Netzwerk enthält drei Clouddienste: </span><span class="sxs-lookup"><span data-stu-id="90a1b-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="90a1b-198">Der erste Clouddienst verfügt über zwei Active Directory- und DNS-Server mit einer Verfügbarkeitsgruppe. </span><span class="sxs-lookup"><span data-stu-id="90a1b-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="90a1b-199">Der zweite clouddienst verfügt über drei Servergruppen: zwei verteilte Cacheserver mit einem Verfügbarkeits Satz.</span><span class="sxs-lookup"><span data-stu-id="90a1b-199">The second cloud service has three sets of servers: Two distributed cache servers with an availability set.</span></span> <span data-ttu-id="90a1b-200">Zwei Front-End-Server mit einem Verfügbarkeits Satz.</span><span class="sxs-lookup"><span data-stu-id="90a1b-200">Two front-end servers with an availability set.</span></span> <span data-ttu-id="90a1b-201">Drei Back-End-Server mit einem Verfügbarkeits Satz.</span><span class="sxs-lookup"><span data-stu-id="90a1b-201">Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="90a1b-p112">Der dritte Clouddienst verfügt über drei Datenbankserver mit einer Verfügbarkeitsgruppe. Einer dieser Datenbankserver ist eine Dateifreigabe für den Protokollversand und ein dritter Knoten einer Knotenmehrheit für SQL Server AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="90a1b-204">Erstellen der AD DS-Hybridumgebung</span><span class="sxs-lookup"><span data-stu-id="90a1b-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="90a1b-205">Die Konfiguration von AD DS für diese Lösung ist ein Hybridbereitstellungsszenario, in dem AD DS teilweise lokal und teilweise auf virtuellen Azure-Computern bereitgestellt wird. </span><span class="sxs-lookup"><span data-stu-id="90a1b-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="90a1b-206">Wichtig: Lesen Sie vor dem Bereitstellen von AD DS in Azure die Richtlinien für die Bereitstellung von Windows Server Activehttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)Directory auf virtuellen Microsoft Azure-Computern (.</span><span class="sxs-lookup"><span data-stu-id="90a1b-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="90a1b-207">Ausführliche Anweisungen zum Entwerfen und Bereitstellen von Active Directory-Umgebungen http://TechNet.microsoft.comfinden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="90a1b-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="90a1b-p113">Diese Referenzarchitektur enthält zwei virtuelle Computer, die als Domänencontroller konfiguriert sind. Jeder ist wie folgt konfiguriert: </span><span class="sxs-lookup"><span data-stu-id="90a1b-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="90a1b-210">Größe: klein </span><span class="sxs-lookup"><span data-stu-id="90a1b-210">Size — Small.</span></span> 
    
- <span data-ttu-id="90a1b-211">Betriebssystem: Windows Server 2012  </span><span class="sxs-lookup"><span data-stu-id="90a1b-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="90a1b-p114">Rolle: AD DS-Domänencontroller, der als globaler Katalogserver ausgewiesen ist. Diese Konfiguration reduziert den ausgehenden Datenverkehr über die VPN-Verbindung. In einer Umgebung mit mehreren Domänen mit einer hohen Änderungsrate konfigurieren Sie die Domänencontroller lokal so, dass sie nicht mit den globalen Katalogservern in Azure synchronisiert werden.  </span><span class="sxs-lookup"><span data-stu-id="90a1b-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="90a1b-p115">Datenträger: Platzieren Sie die AD DS-Datenbank, Protokolle und SYSVOL auf Azure-Datenträgern. Platzieren Sie sie nicht auf dem Datenträger mit dem Betriebssystem oder den temporären Datenträgern, die von Azure bereitgestellt werden. Dies ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="90a1b-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="90a1b-218">Rolle: Installieren und konfigurieren Sie Windows DNS auf den Domänencontrollern. </span><span class="sxs-lookup"><span data-stu-id="90a1b-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="90a1b-p116">IP-Adressen: Verwenden Sie dynamische IP-Adressen. Dazu müssen Sie ein virtuelles Azure-Netzwerk erstellen. </span><span class="sxs-lookup"><span data-stu-id="90a1b-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

