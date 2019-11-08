---
title: Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Internetsites für SharePoint 2013 in Microsoft Azure“.
ms.openlocfilehash: cf978dfb95b1f201c342889fc3dda428bb618241
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38028059"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="6c3ae-103">Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="6c3ae-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="6c3ae-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Internet Websites in Microsoft Azure für SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="6c3ae-p101">In diesem Poster wird beschrieben und veranschaulicht, wie öffentlich zugängliche Websites im Internet von der Elastizität in der Cloud und Azure AD für Kundenkonten profitieren. Es gibt sechs verschiedene Szenarien, die beschreiben, wie Internetsites von Azure profitieren: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="6c3ae-107">Entwurf und Dimensionierung der Farmtopologie </span><span class="sxs-lookup"><span data-stu-id="6c3ae-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="6c3ae-108">Feinabstimmung für Azure </span><span class="sxs-lookup"><span data-stu-id="6c3ae-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="6c3ae-109">Auswahl des Active Directory-Modells </span><span class="sxs-lookup"><span data-stu-id="6c3ae-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="6c3ae-110">Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung </span><span class="sxs-lookup"><span data-stu-id="6c3ae-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="6c3ae-111">Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung </span><span class="sxs-lookup"><span data-stu-id="6c3ae-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="6c3ae-112">Entwurf der Azure-Umgebung </span><span class="sxs-lookup"><span data-stu-id="6c3ae-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="6c3ae-113">Entwurf und Dimensionierung der Farmtopologie</span><span class="sxs-lookup"><span data-stu-id="6c3ae-113">Design and size the farm topology</span></span>

<span data-ttu-id="6c3ae-114">Verwenden Sie die Topologie-, Kapazitäts-und Leistungs Anleitungen für SharePoint 2013 auf TechNet, um die Farmtopologie zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="6c3ae-115">Stellen Sie sicher, dass die von Ihnen entworfene Farm die Kapazitäts- und Leistungsziele erfüllt. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="6c3ae-116">Beispiel: Mittelgroße Internetsitefarm (ca. 85 Seitenaufrufe pro Sekunde)</span><span class="sxs-lookup"><span data-stu-id="6c3ae-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="6c3ae-117">Diese Farm stellt eine fehlertolerante SharePoint 2013 Such Farmtopologie bereit, die für einen Korpus optimiert ist, der 3,4 Millionen Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="6c3ae-118">In der Beispiel Farm werden 100-200 Dokumente pro Sekunde, abhängig von der Sprache, verarbeitet, und es werden 85 Seitenaufrufe pro Sekunde und 100 Abfragen pro Sekunde untergebracht.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="6c3ae-119">Das zugehörige Diagramm zeigt eine mittelgroße Internetsitefarm mit drei Arten von Servern: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="6c3ae-120">Webserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-120">Web servers</span></span> 
    
- <span data-ttu-id="6c3ae-121">Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-121">Application servers</span></span> 
    
- <span data-ttu-id="6c3ae-122">Datenbankserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="6c3ae-123">Webserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-123">Web servers</span></span>

<span data-ttu-id="6c3ae-p102">Im Abschnitt „Web-Server“ gibt es drei Webserver: Host A, Host B und Host C. Jeder Webserver enthält einen verteilten Cache, Benutzerprofile, verwaltete Metadaten und Abfrageverarbeitungsfunktionen. Sie enthalten auch ein Indexpartitionsreplikat, das auf jedem der Server vorhanden ist.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="6c3ae-126">Zum horizontalen Skalieren können Sie einen zusätzlichen Webserver mit den gleichen Funktionen hinzufügen. Dadurch werden weitere 28 Seitenansichten pro Sekunde ermöglicht. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="6c3ae-127">Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-127">Application servers</span></span>

<span data-ttu-id="6c3ae-p103">Im Abschnitt „Anwendungsserver“ gibt es drei Anwendungsserver: Host D, Host E und Host F. Host D enthält Komponenten zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung. Host E enthält Komponenten zur Durchforstung, Verwaltung und Inhaltsverarbeitung. Host F enthält Komponenten zur Durchforstung und Inhaltsverarbeitung. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="6c3ae-131">Zum horizontalen Skalieren können Sie einen Anwendungsserver mit einer Durchforstungs- und Inhaltsverarbeitungskomponente hinzufügen. Dadurch wird die Verarbeitung von 40 weiteren Dokumenten pro Sekunde ermöglicht. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="6c3ae-132">Datenbankserver</span><span class="sxs-lookup"><span data-stu-id="6c3ae-132">Database servers</span></span>

<span data-ttu-id="6c3ae-133">Im Abschnitt „Datenbankserver“ gibt es zwei Server: Host G und Host H. Aus Gründen der Fehlertoleranz laufen die Server auf verbundenen Hosts. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="6c3ae-p104">Host G enthält alle SharePoint-Datenbanken. Dazu gehören unter anderem die Suchverwaltungsdatenbank, Linkdatenbank, zwei Durchforstungsdatenbanken und eine Analysedatenbank. Host H enthält alle SharePoint-Datenbanken. Dazu gehören redundante Kopien aller Datenbanken mit SQL-Clustering, Spiegelung oder SQL Server 2012 AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="6c3ae-136">Feinabstimmung für Azure</span><span class="sxs-lookup"><span data-stu-id="6c3ae-136">Fine-tune for Azure</span></span>

<span data-ttu-id="6c3ae-p105">Die SharePoint-Farm muss möglicherweise für Verfügbarkeitssätze auf der Azure-Plattform optimiert werden. Um eine hohe Verfügbarkeit aller Komponenten sicherzustellen, vergewissern Sie sich, dass alle Serverrollen identisch konfiguriert sind.   </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="6c3ae-139">In der Beispieltopologie im Diagramm liegt folgende Situation vor: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="6c3ae-140">Die Webserver und Datenbankserver sind identisch konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="6c3ae-p106">Die drei Anwendungsserver sind nicht identisch konfiguriert. Diese Serverrollen benötigen eine Optimierung für Verfügbarkeitssätze in Azure.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="6c3ae-143">Vor</span><span class="sxs-lookup"><span data-stu-id="6c3ae-143">Before</span></span>

<span data-ttu-id="6c3ae-p107">Im oberen Bereich des Diagramms sehen Sie die SharePoint-Farm vor der Optimierung für Verfügbarkeitssätze in Azure. Im Diagramm sind die drei Host-Anwendungsserver nicht identisch konfiguriert. Die Anzahl der Komponenten wird durch die Leistungs- und Kapazitätsziele für die Farm bestimmt. Die drei Server sind folgendermaßen konfiguriert: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="6c3ae-148">Für den Anwendungsserver Host D wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="6c3ae-149">Für den Anwendungsserver Host E wurden Rollen zur Durchforstung, Verwaltung und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="6c3ae-150">Für den Anwendungsserver Host F wurden Rollen zur Durchforstung und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="6c3ae-151">Nach</span><span class="sxs-lookup"><span data-stu-id="6c3ae-151">After</span></span>

<span data-ttu-id="6c3ae-152">In diesem Teil des Diagramms sehen Sie die SharePoint-Farm nach der Optimierung für Verfügbarkeitssätze in Azure.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="6c3ae-153">Für die Anpassung dieser Architektur an Azure werden die vier Komponenten auf alle drei Server repliziert.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="6c3ae-154">Dies erhöht die Anzahl der Komponenten über die Leistungs-und Kapazitätsvorgaben hinaus.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="6c3ae-155">Der Vorteil besteht darin, dass dieser Entwurf für Hochverfügbarkeit aller vier Komponenten auf der Azure-Plattform sorgt, wenn diese drei virtuellen Computer einem Verfügbarkeitssatz zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="6c3ae-156">Für alle drei Server wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="6c3ae-157">Auswahl des Active Directory-Modells</span><span class="sxs-lookup"><span data-stu-id="6c3ae-157">Choose the Active Directory model</span></span>

<span data-ttu-id="6c3ae-p109">Alle SharePoint-Lösungen erfordern Windows Active Directory-Domänendienste (AD DS). Derzeit sind zwei Optionen für SharePoint-Lösungen in Azure verfügbar.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="6c3ae-160">Option 1: dedizierte Domäne – Sie können eine dedizierte und isolierte Domäne für Azure bereitstellen, um eine SharePoint-Farm zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="6c3ae-161">Dies ist eine gute Wahl für öffentlich zugängliche Internetwebsites.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="6c3ae-162">Option 2: Erweitern Sie die lokale Domäne über eine Standort-zu-Standort-VPN-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="6c3ae-163">Wenn Sie die lokale Domäne über eine Standort-zu-Standort-VPN-Verbindung erweitern, greifen Benutzer auf die SharePoint-Farm zu, als ob Sie lokal gehostet würde.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="6c3ae-164">Sie können die vorhandenen Active Directory-und DNS-Implementierungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="6c3ae-165">Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6c3ae-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="6c3ae-166">Entwurf für Konten und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="6c3ae-166">Design for accounts and authentication</span></span>

<span data-ttu-id="6c3ae-167">Bestimmen Sie, welche Konten verwaltet werden und welche Art der Authentifizierung verwendet werden soll. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="6c3ae-168">Konten für Website-Entwickler und -Autoren</span><span class="sxs-lookup"><span data-stu-id="6c3ae-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="6c3ae-169">Fügen Sie der Domäne in Azure Konten hinzu. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="6c3ae-170">Verwenden Sie lokal die Active Directory-Verbunddienste (AD FS), um die internen Konten mit der Domäne in Azure zu verbinden. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="6c3ae-171">Wenn der Entwurf eine Standort-zu-Standort-VPN-Verbindung enthält, verwenden Sie die internen Konten. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="6c3ae-172">Konten für Kunden</span><span class="sxs-lookup"><span data-stu-id="6c3ae-172">Accounts for customers</span></span>

- <span data-ttu-id="6c3ae-173">Verwenden Sie Azure Active Directory. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="6c3ae-174">Verwenden Sie einen anderen SAML-basierten Anbieter. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="6c3ae-175">Entwurf für Zonen</span><span class="sxs-lookup"><span data-stu-id="6c3ae-175">Design for zones</span></span>

<span data-ttu-id="6c3ae-176">In SharePoint 2013 wird die Identitätsverwaltung bei der Konfiguration der Zonen und Authentifizierung berücksichtigt. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="6c3ae-177">Dieser Entwurf bietet eine klare Trennung zwischen Kundenkonten und allen anderen Konten. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="6c3ae-178">Verwenden Sie diesen Entwurf, wenn Sie Kundenkonten komplett anders als die internen Konten für Autoren und Website-Entwickler behandeln möchten. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="6c3ae-179">Mithilfe dieses Designs können Sie Zonenrichtlinien verwenden, um Aktionen des Kunden innerhalb einer Webanwendung zu beschränken. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="6c3ae-180">Dieser Entwurf führt zu verschiedenen URLs für Kundenkonten und interne Konten. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="6c3ae-181">In diesem Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6c3ae-181">In this example:</span></span> 
  
- <span data-ttu-id="6c3ae-182">Konfigurieren Sie die Standardzone für interne Konten. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="6c3ae-p112">Konfigurieren Sie die Extranetzone für den authentifizierten Kundenzugriff. Verwenden Sie Azure Active Directory (AD) für Kundenkonten, oder verwenden Sie einen anderen SAML-basierten Anbieter. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="6c3ae-185">Konfigurieren Sie die Internetzone für den anonymen Zugriff.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="6c3ae-186">Verwenden Sie kein zwei Zonen Design, in dem alle authentifizierten Benutzer für die Verwendung der Standardzone konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="6c3ae-187">Das zugehörige Diagramm zeigt einen Drei-Zonen-Entwurf mit Trennung von internen und Kundenkonten.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="6c3ae-188">Besucher und Kunden greifen über Webanwendungen in einer von zwei Zonen auf den Azure AD Mandanten in der SharePoint 2013-Farm zu.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="6c3ae-189">Die beiden Zonen sind:</span><span class="sxs-lookup"><span data-stu-id="6c3ae-189">The two zones include:</span></span> 
  
- <span data-ttu-id="6c3ae-190">Zone: Internet für anonyme Benutzer </span><span class="sxs-lookup"><span data-stu-id="6c3ae-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="6c3ae-191">Zone: Extranet für authentifizierte Benutzer </span><span class="sxs-lookup"><span data-stu-id="6c3ae-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="6c3ae-p114">Benutzer mit internen Konten greifen über AD DS auf den Azure Active Directory-Mandanten zu und in der lokalen Umgebung durch den VPN-Tunnel zu Azure AD auf AD FS. Die Standardzone bietet Windows-Authentifizierung (NTLM). </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="6c3ae-194">Entwurf für das Herstellen einer Verbindung mit Azure AD</span><span class="sxs-lookup"><span data-stu-id="6c3ae-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="6c3ae-p115">Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste. Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS. Die in Azure AD enthaltenen Identitätsdienste lassen sich problemlos in Ihre lokalen AD DS-Bereitstellungen integrieren und unterstützen andere Identitätsanbieter umfassend. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="6c3ae-198">Das zugehörige Diagramm zeigt das folgende Szenario: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="6c3ae-199">Bei der Integration von SharePoint 2013 mit Azure Active Directory dient ein Azure-zugriffssteuerungsdienst (ACS) zwei Zwecken:</span><span class="sxs-lookup"><span data-stu-id="6c3ae-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="6c3ae-p116"> Azure AD verwendet SAML 2.0 und SharePoint funktioniert nur mit SAML 1.1. ACS versteht beide Formate und fungiert als Vermittler zum Transformieren der Tokenformate zwischen SharePoint und Azure AD.   </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="6c3ae-202">ACS ersetzt die Notwendigkeit des Identitätsanbieter-Sicherheitstokendiensts (IP-STS) für dieses SAML-Szenario. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="6c3ae-203">Weitere Informationen finden Sie in der TechNet-Bibliothek unter „Konfigurieren von Azure AD mit SharePoint 2013“. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="6c3ae-204">Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="6c3ae-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="6c3ae-205">Für die Veröffentlichung wird ein Entwurf mit einer Webanwendung empfohlen. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="6c3ae-206">Websites zur Dokumenterstellung und zur Veröffentlichung sind in derselben Webanwendung. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="6c3ae-207">Zur Veröffentlichung von Objekten wird die websiteübergreifende Veröffentlichung verwendet. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="6c3ae-208">Verwenden Sie pfadbasierte und hostbenannte Websitesammlungen. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="6c3ae-p117">Eine Stammwebsitesammlung ist erforderlich. Erstellen Sie diese Website als pfadbasierte Website. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="6c3ae-211">Erstellen Sie alle anderen Websitesammlungen als hostbenannte Websitesammlungen. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="6c3ae-212">Webanwendung und Stammwebsite-URLs </span><span class="sxs-lookup"><span data-stu-id="6c3ae-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="6c3ae-p118">Verwenden Sie einen internen Namen für die URL der Webanwendung. SharePoint verwendet den Namen des lokalen Computers als Standardnamen, sofern kein anderer Name angegeben wird. Sie können einen Domänennamen verwenden, der für die interne Netzwerkumgebung reserviert ist.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="6c3ae-p119">SharePoint weist bei der Erstellung der Webanwendung eine nicht standardmäßige Portnummer zu. Verwenden Sie diese Portnummer statt Port 80 oder Port 443. Oder verwenden Sie eine andere nicht standardmäßige Portnummer. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="6c3ae-219">Verwenden Sie denselben Namen und dieselbe Portnummer für die Stammwebsitesammlung, bei der es sich um eine pfadbasierte Websitesammlung handelt. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="6c3ae-p120">Das zugehörige Diagramm zeigt Anwendungspooldienste, z. B. Suchen in Websitesammlungen mithilfe von Webanwendungen. Die gezeigt Websitesammlung enthält: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="6c3ae-222">Pfadbasierte Websitesammlung, die sich https://internal:8000 unter (Stammwebsite) befindet.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-222">Path-based site collection located at https://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="6c3ae-223">Durchforstung: Websitesammlungen mit Hostnamen, die sich an https://authoring.contoso.com:8000einer Adresse wie.</span><span class="sxs-lookup"><span data-stu-id="6c3ae-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="6c3ae-224">Abfragen: 2 separate hostbenannte Websitesammlungen, die unter Adresse wie etwa den folgenden zu finden sind: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="6c3ae-225">Entwurf der Azure-Umgebung</span><span class="sxs-lookup"><span data-stu-id="6c3ae-225">Design the Azure environment</span></span>

<span data-ttu-id="6c3ae-226">Diese Beispielarchitektur umfasst folgende Elemente: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="6c3ae-227">Eine Standort-zu-Standort-VPN-Verbindung ist optional und weitet die lokale Windows AD DS- und DNS-Umgebung auf das virtuelle Netzwerk in Azure aus. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="6c3ae-228">Verwenden Sie zur Unterstützung der SharePoint-Farm optional eine dedizierte Domäne in Azure. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="6c3ae-229">Server werden entsprechend der Rolle auf Azure-Clouddienste verteilt. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="6c3ae-230">Verfügbarkeitssätze garantieren eine hohe Verfügbarkeit identisch konfigurierten Serverrollen.  </span><span class="sxs-lookup"><span data-stu-id="6c3ae-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="6c3ae-231">Weitere Informationen finden Sie im folgenden TechNet-Artikel: Azure-Architekturen für SharePoint-Lösungen. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="6c3ae-232">Das zugehörige Diagramm zeigt ein Beispiel einer lokalen Umgebung, die mit einem virtuellen Azure-Netzwerk verbunden wird.   </span><span class="sxs-lookup"><span data-stu-id="6c3ae-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="6c3ae-233">Die lokalen Umgebung (ein optionales Element der Azure-Umgebung) umfasst die folgenden Komponenten: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="6c3ae-234">Windows Server 2012 RRAS </span><span class="sxs-lookup"><span data-stu-id="6c3ae-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="6c3ae-235">AD DS</span><span class="sxs-lookup"><span data-stu-id="6c3ae-235">AD DS</span></span> 
    
- <span data-ttu-id="6c3ae-236">Ein VPN-Gateway von Windows Server und AD DS zum aktiven VPN-Gateway-Subnetz </span><span class="sxs-lookup"><span data-stu-id="6c3ae-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="6c3ae-237">Die virtuelle Azure-Netzwerkumgebung umfasst die folgenden Komponenten: </span><span class="sxs-lookup"><span data-stu-id="6c3ae-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="6c3ae-238">Das aktive VPN-Gateway-Subnetz (überlappend mit der lokalen Umgebung, falls zutreffend) </span><span class="sxs-lookup"><span data-stu-id="6c3ae-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="6c3ae-239">Clouddienst, der AD DS- und DNS-Verfügbarkeitssätze umfasst (zwei Server) </span><span class="sxs-lookup"><span data-stu-id="6c3ae-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="6c3ae-240">Clouddienst, der die Verfügbarkeitssätze der Front-End-Server (drei SharePoint Server) und die Verfügbarkeitssätze des App-Servers enthält (drei SharePoint Server) </span><span class="sxs-lookup"><span data-stu-id="6c3ae-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="6c3ae-241">Clouddienst, der die beiden Verfügbarkeitssätze für die Datenbanken enthält. </span><span class="sxs-lookup"><span data-stu-id="6c3ae-241">Cloud service that contains two database availability sets</span></span> 
    

