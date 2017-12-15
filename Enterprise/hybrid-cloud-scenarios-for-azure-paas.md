---
title: "Hybrid Cloud-Szenarien für Azure PaaS"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Zusammenfassung: Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure."
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="6fbc9-103">Hybrid Cloud-Szenarien für Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="6fbc9-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="6fbc9-104">**Zusammenfassung:** Grundlegende Informationen zur Hybrid-Architektur und -szenarien für PaaS-basierte Cloudangebote von Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="6fbc9-105">Kombinieren Sie lokale Daten oder Computingressourcen mit neuen oder konvertierten Anwendungen, die in Azure PaaS ausgeführt werden und Cloudleistung, -zuverlässigkeit und -skalierung nutzen sowie bessere Unterstützung für mobile Benutzer bieten können.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="6fbc9-106">Architektur für Azure PaaS-Hybridszenario</span><span class="sxs-lookup"><span data-stu-id="6fbc9-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="6fbc9-107">Abbildung 1 zeigt die Architektur der PaaS-basierten Hybridszenarien von Microsoft in Azure.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="6fbc9-108">**Abbildung 1: Microsoft PaaS-basierte Hybridszenarien in Azure**</span><span class="sxs-lookup"><span data-stu-id="6fbc9-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft PaaS-basierte Hybridszenarien in Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="6fbc9-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="6fbc9-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="6fbc9-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="6fbc9-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="6fbc9-112">Eine hybride PaaS-Anwendung wird in Azure ausgeführt und nutzt lokale Compute- oder Speicherressourcen.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="6fbc9-113">Identität</span><span class="sxs-lookup"><span data-stu-id="6fbc9-113">Identity</span></span>
    
    <span data-ttu-id="6fbc9-114">Besteht entweder aus einer Verzeichnissynchronisierung oder aus einem Partnerverbund mit einem Drittanbieter-Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="6fbc9-115">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="6fbc9-115">Network</span></span>
    
    <span data-ttu-id="6fbc9-p101">Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit öffentlichem Peering zu Azure PaaS. Sie müssen eine Möglichkeit für die Azure PaaS-Anwendung für den Zugriff auf die lokale Compute- oder Speicherressource hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="6fbc9-118">Lokal</span><span class="sxs-lookup"><span data-stu-id="6fbc9-118">On-premises</span></span>
    
    <span data-ttu-id="6fbc9-119">Besteht aus der Identitäts- und Sicherheitsinfrastruktur sowie vorhandenen branchenspezifischen Anwendungen oder Datenbankserver, auf die eine Azure PaaS-Anwendung sicher zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="6fbc9-120">Azure PaaS-Hybridanwendung</span><span class="sxs-lookup"><span data-stu-id="6fbc9-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="6fbc9-121">Abbildung 2 zeigt die Konfiguration einer Hybridanwendung, die in Azure ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="6fbc9-122">**Abbildung 2: Azure PaaS-basierte Hybridanwendung**</span><span class="sxs-lookup"><span data-stu-id="6fbc9-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Azure PaaS-basierte Hybridanwendung](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="6fbc9-p102">In Abbildung 2 werden Speicher oder Apps auf Servern und in einer DMZ mit einem Proxyserver in einem lokalen Netzwerk gehostet. Das Netzwerk ist über das Internet oder eine ExpressRoute-Verbindung mit PaaS Azure-Diensten verbunden.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="6fbc9-126">Eine Organisation kann seine Compute- oder Speicherressourcen wie folgt für die Azure PaaS-Hybridanwendung zugänglich machen:</span><span class="sxs-lookup"><span data-stu-id="6fbc9-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="6fbc9-127">Durch Hosten der Ressource auf Servern in der DMZ</span><span class="sxs-lookup"><span data-stu-id="6fbc9-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="6fbc9-128">Durch Hosten eines Reverseproxyservers in der DMZ, der authentifizierte, eingehende, HTTPS-basierte Anforderungen an die Ressource zulässt, die sich im lokalen System befindet</span><span class="sxs-lookup"><span data-stu-id="6fbc9-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="6fbc9-129">Die Azure-App kann Anmeldeinformationen verwenden von:</span><span class="sxs-lookup"><span data-stu-id="6fbc9-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="6fbc9-130">Azure AD, das mit Ihrem lokalen Identitätsanbieter, z. B. Windows Server Active Directory, synchronisiert werden kann</span><span class="sxs-lookup"><span data-stu-id="6fbc9-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="6fbc9-131">Einem Drittanbieter-Identitätsanbieter</span><span class="sxs-lookup"><span data-stu-id="6fbc9-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="6fbc9-132">Azure PaaS-Hybridanwendung als Beispiel</span><span class="sxs-lookup"><span data-stu-id="6fbc9-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="6fbc9-133">Abbildung 3 zeigt ein Beispiel für eine Hybridanwendung, die in Azure ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="6fbc9-134">**Abbildung 3: Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung**</span><span class="sxs-lookup"><span data-stu-id="6fbc9-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Ein Beispiel für eine Azure PaaS-basierte Hybridanwendung](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="6fbc9-p103">In Abbildung 3 wird eine Branchenanwendung in einem lokalen Netzwerk gehostet. Azure PaaS hostet eine benutzerdefinierte mobile App. Ein Smartphone im Internet greift auf die benutzerdefinierte mobile App in Azure zu, von wo wiederum Datenanforderungen an die lokale Branchenanwendung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="6fbc9-p104">Diese Azure PaaS-Beispielhybridanwendung ist eine benutzerdefinierte mobile App, die aktuelle Kontaktinformationen zu Mitarbeitern bereitstellt. Das End-to-End-Hybridszenario besteht aus:</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="6fbc9-141">Einer Smartphone-App, die überprüfte lokale Anmeldeinformationen erfordert, damit sie ausgeführt werden kann</span><span class="sxs-lookup"><span data-stu-id="6fbc9-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="6fbc9-142">Einer benutzerdefinierten mobilen App, die in Azure PaaS ausgeführt wird und Informationen zu bestimmten Mitarbeitern anhand von Abfragen anfordert, die von der Smartphone-App eines Benutzers stammen</span><span class="sxs-lookup"><span data-stu-id="6fbc9-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="6fbc9-143">Einem Reverseproxyserver in der DMZ, der die benutzerdefinierte mobile App überprüft und die Anforderung weiterleitet</span><span class="sxs-lookup"><span data-stu-id="6fbc9-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="6fbc9-144">Einer Branchenanwendungs-Serverfarm, die die Kontaktanforderung entsprechend den Berechtigungen verarbeitet, die das Konto des Benutzers hat</span><span class="sxs-lookup"><span data-stu-id="6fbc9-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="6fbc9-145">Da der lokale Identitätsanbieter mit Azure Active Directory synchronisiert wurde, können sowohl die benutzerdefinierte mobile App als auch die Branchen-App den Kontonamen des anfordernden Benutzers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="6fbc9-146">Stretch-Datenbank mit SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="6fbc9-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="6fbc9-147">Stretch-Datenbank ist ein Feature von SQL Server-2016, das es Ihnen ermöglicht, archivierte („kalte") Daten, z. B. abgeschlossene Geschäftsdaten in einer umfangreichen Tabelle, die Kundenbestellinformationen enthält, transparent und sicher in eine SQL Stretch-Datenbank in Azure zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="6fbc9-p105">Wird der Inhalt einer SQL Server-Instanz, einer Datenbank oder sogar einer einzelnen Tabelle in einer Stretch-Datenbank verwendet, ist er eine Kombination aus lokalen Daten auf dem Server mit SQL Server 2016 und Remotedaten in Azure. Daten, die zur Verwendung in einer Stretch-Datenbank auswählbar geworden sind, werden von SQL Server 2016 automatisch in Azure verschoben.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="6fbc9-150">In Abbildung 4 wird Stretch-Datenbank mit SQL Server 2016 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="6fbc9-151">**Abbildung 4: Stretch-Datenbank mit SQL Server 2016**</span><span class="sxs-lookup"><span data-stu-id="6fbc9-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![Stretch-Datenbank mit SQL Server 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="6fbc9-p106">In Abbildung 4 wird ein Server mit SQL Server 2016 mit einer kleinen lokalen Datenbank in einem lokalen Netzwerk gehostet. Azure PaaS hostet eine Instanz von Azure SQL Server Stretch-Datenbank mit dem gestreckten Teil der Datenbank. T-SQL-Abfragen von lokalen Benutzern, die an den lokalen SQL-Server gesendet werden, werden sicher an die Azure SQL Stretch-Datenbank weitergeleitet, welche die Ergebnisse für den anfordernden Benutzer zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="6fbc9-p107">Benutzerabfragen, die Verlaufsdaten enthalten, werden transparent an die Azure SQL Stretch-Datenbank weitergeleitet. Die Abfragen müssen nicht neu geschrieben werden, obwohl die Tabelle gestreckt ist.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="6fbc9-p108">Stretch-Datenbank stellt eine kostengünstige Möglichkeit für langfristige Speicherung und transparenten Zugriff auf Verlaufsdaten. Außerdem können hiermit Leistungs- und Verfügbarkeitsprobleme behoben werden, die auftreten, wenn die Tabellen sehr umfangreich sind.</span><span class="sxs-lookup"><span data-stu-id="6fbc9-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="6fbc9-160">Weitere Informationen finden Sie unter [Stretch-Datenbank](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="6fbc9-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6fbc9-161">See Also</span><span class="sxs-lookup"><span data-stu-id="6fbc9-161">See Also</span></span>

[<span data-ttu-id="6fbc9-162">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="6fbc9-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="6fbc9-163">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="6fbc9-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="6fbc9-164">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="6fbc9-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



