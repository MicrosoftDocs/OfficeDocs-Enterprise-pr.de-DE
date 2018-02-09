---
title: "Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Internetsites für SharePoint 2013 in Microsoft Azure“."
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="19820-103">Zugängliches Diagramm – Internetwebsites in Microsoft Azure für SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="19820-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="19820-104">**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Internet-Websites in Microsoft Azure für SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="19820-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="19820-p101">In diesem Poster wird beschrieben und veranschaulicht, wie öffentlich zugängliche Websites im Internet von der Elastizität in der Cloud und Azure AD für Kundenkonten profitieren. Es gibt sechs verschiedene Szenarien, die beschreiben, wie Internetsites von Azure profitieren: </span><span class="sxs-lookup"><span data-stu-id="19820-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="19820-107">Entwurf und Dimensionierung der Farmtopologie </span><span class="sxs-lookup"><span data-stu-id="19820-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="19820-108">Feinabstimmung für Azure </span><span class="sxs-lookup"><span data-stu-id="19820-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="19820-109">Auswahl des Active Directory-Modells </span><span class="sxs-lookup"><span data-stu-id="19820-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="19820-110">Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung </span><span class="sxs-lookup"><span data-stu-id="19820-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="19820-111">Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung </span><span class="sxs-lookup"><span data-stu-id="19820-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="19820-112">Entwurf der Azure-Umgebung </span><span class="sxs-lookup"><span data-stu-id="19820-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="19820-113">Entwurf und Dimensionierung der Farmtopologie</span><span class="sxs-lookup"><span data-stu-id="19820-113">Design and size the farm topology</span></span>

<span data-ttu-id="19820-114">Verwenden Sie die Topologie, Kapazität und Leistung Anleitung zum Entwerfen der Farmtopologie für SharePoint 2013 auf TechNet.</span><span class="sxs-lookup"><span data-stu-id="19820-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="19820-115">Stellen Sie sicher, dass die von Ihnen entworfene Farm die Kapazitäts- und Leistungsziele erfüllt. </span><span class="sxs-lookup"><span data-stu-id="19820-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="19820-116">Beispiel: Mittelgroße Internetsitefarm (ca. 85 Seitenaufrufe pro Sekunde)</span><span class="sxs-lookup"><span data-stu-id="19820-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="19820-117">Diese Farm stellt eine fehlertolerante SharePoint 2013-Farm Suchtopologie, die für eine Korpus optimiert wird, die 3,400,000 Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="19820-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="19820-118">Die beispielfarm verarbeitet Dokumente von 100 bis 200 pro Sekunde, abhängig von der Sprache, und in diesem Layout 85 Seitenansichten pro Sekunde und 100 Abfragen pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="19820-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="19820-119">Das zugehörige Diagramm zeigt eine mittelgroße Internetsitefarm mit drei Arten von Servern: </span><span class="sxs-lookup"><span data-stu-id="19820-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="19820-120">Webserver</span><span class="sxs-lookup"><span data-stu-id="19820-120">Web servers</span></span> 
    
- <span data-ttu-id="19820-121">Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="19820-121">Application servers</span></span> 
    
- <span data-ttu-id="19820-122">Datenbankserver</span><span class="sxs-lookup"><span data-stu-id="19820-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="19820-123">Webserver</span><span class="sxs-lookup"><span data-stu-id="19820-123">Web servers</span></span>

<span data-ttu-id="19820-p102">Im Abschnitt „Web-Server“ gibt es drei Webserver: Host A, Host B und Host C. Jeder Webserver enthält einen verteilten Cache, Benutzerprofile, verwaltete Metadaten und Abfrageverarbeitungsfunktionen. Sie enthalten auch ein Indexpartitionsreplikat, das auf jedem der Server vorhanden ist.  </span><span class="sxs-lookup"><span data-stu-id="19820-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="19820-126">Zum horizontalen Skalieren können Sie einen zusätzlichen Webserver mit den gleichen Funktionen hinzufügen. Dadurch werden weitere 28 Seitenansichten pro Sekunde ermöglicht. </span><span class="sxs-lookup"><span data-stu-id="19820-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="19820-127">Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="19820-127">Application servers</span></span>

<span data-ttu-id="19820-p103">Im Abschnitt „Anwendungsserver“ gibt es drei Anwendungsserver: Host D, Host E und Host F. Host D enthält Komponenten zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung. Host E enthält Komponenten zur Durchforstung, Verwaltung und Inhaltsverarbeitung. Host F enthält Komponenten zur Durchforstung und Inhaltsverarbeitung. </span><span class="sxs-lookup"><span data-stu-id="19820-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="19820-131">Zum horizontalen Skalieren können Sie einen Anwendungsserver mit einer Durchforstungs- und Inhaltsverarbeitungskomponente hinzufügen. Dadurch wird die Verarbeitung von 40 weiteren Dokumenten pro Sekunde ermöglicht. </span><span class="sxs-lookup"><span data-stu-id="19820-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="19820-132">Datenbankserver</span><span class="sxs-lookup"><span data-stu-id="19820-132">Database servers</span></span>

<span data-ttu-id="19820-133">Im Abschnitt „Datenbankserver“ gibt es zwei Server: Host G und Host H. Aus Gründen der Fehlertoleranz laufen die Server auf verbundenen Hosts. </span><span class="sxs-lookup"><span data-stu-id="19820-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="19820-p104">Host G enthält alle SharePoint-Datenbanken. Dazu gehören unter anderem die Suchverwaltungsdatenbank, Linkdatenbank, zwei Durchforstungsdatenbanken und eine Analysedatenbank. Host H enthält alle SharePoint-Datenbanken. Dazu gehören redundante Kopien aller Datenbanken mit SQL-Clustering, Spiegelung oder SQL Server 2012 AlwaysOn. </span><span class="sxs-lookup"><span data-stu-id="19820-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="19820-136">Feinabstimmung für Azure</span><span class="sxs-lookup"><span data-stu-id="19820-136">Fine-tune for Azure</span></span>

<span data-ttu-id="19820-p105">Die SharePoint-Farm muss möglicherweise für Verfügbarkeitssätze auf der Azure-Plattform optimiert werden. Um eine hohe Verfügbarkeit aller Komponenten sicherzustellen, vergewissern Sie sich, dass alle Serverrollen identisch konfiguriert sind.   </span><span class="sxs-lookup"><span data-stu-id="19820-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="19820-139">In der Beispieltopologie im Diagramm liegt folgende Situation vor: </span><span class="sxs-lookup"><span data-stu-id="19820-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="19820-140">Die Webserver und Datenbankserver sind identisch konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="19820-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="19820-p106">Die drei Anwendungsserver sind nicht identisch konfiguriert. Diese Serverrollen benötigen eine Optimierung für Verfügbarkeitssätze in Azure.  </span><span class="sxs-lookup"><span data-stu-id="19820-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="19820-143">Vor</span><span class="sxs-lookup"><span data-stu-id="19820-143">Before</span></span>

<span data-ttu-id="19820-p107">Im oberen Bereich des Diagramms sehen Sie die SharePoint-Farm vor der Optimierung für Verfügbarkeitssätze in Azure. Im Diagramm sind die drei Host-Anwendungsserver nicht identisch konfiguriert. Die Anzahl der Komponenten wird durch die Leistungs- und Kapazitätsziele für die Farm bestimmt. Die drei Server sind folgendermaßen konfiguriert: </span><span class="sxs-lookup"><span data-stu-id="19820-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="19820-148">Für den Anwendungsserver Host D wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="19820-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="19820-149">Für den Anwendungsserver Host E wurden Rollen zur Durchforstung, Verwaltung und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="19820-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="19820-150">Für den Anwendungsserver Host F wurden Rollen zur Durchforstung und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="19820-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="19820-151">Nach</span><span class="sxs-lookup"><span data-stu-id="19820-151">After</span></span>

<span data-ttu-id="19820-p108">In diesem Teil des Diagramms gezeigt, dass die SharePoint-Farm nach für Verfügbarkeit gezielt in Azure festgelegt. Diese Architektur für Azure angepasst werden kann, werden wir die vier Komponenten auf allen drei Servern repliziert. Dadurch wird die Anzahl der Komponenten über das für Leistung und Kapazität erhöht. Der Nachteil ist, dass dieses Design sorgt für hohe Verfügbarkeit aller vier Komponenten in der Azure-Plattform, wenn diese drei virtuellen Maschinen, die eine Menge Verfügbarkeit zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="19820-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="19820-156">Für alle drei Server wurden Rollen zur Durchforstung, Verwaltung, Analyse und Inhaltsverarbeitung konfiguriert. </span><span class="sxs-lookup"><span data-stu-id="19820-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="19820-157">Auswahl des Active Directory-Modells</span><span class="sxs-lookup"><span data-stu-id="19820-157">Choose the Active Directory model</span></span>

<span data-ttu-id="19820-p109">Alle SharePoint-Lösungen erfordern Windows Active Directory-Domänendienste (AD DS). Derzeit sind zwei Optionen für SharePoint-Lösungen in Azure verfügbar.  </span><span class="sxs-lookup"><span data-stu-id="19820-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="19820-p110">Option 1: Dedizierten Domäne – Sie können eine dedizierte und isolierte Domäne in Azure zur Unterstützung von einer SharePoint-Farm bereitstellen. Dies ist eine gute Wahl für Öffentliche Internetwebsites beschrieben.</span><span class="sxs-lookup"><span data-stu-id="19820-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="19820-p111">Option 2: Erweitern der lokalen Domäne über eine Standort-zu-Standort-VPN-Verbindung. Beim Erweitern der lokalen Domäne über eine Standort-zu-Standort-VPN-Verbindung der Benutzerzugriff auf der SharePoint-Farm als wäre es gehosteten lokalen. Sie können Ihre vorhandenen Active Directory und DNS-Implementierungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="19820-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="19820-165">Entwurf für die Identitätsverwaltung, Zonen und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="19820-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="19820-166">Entwurf für Konten und Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="19820-166">Design for accounts and authentication</span></span>

<span data-ttu-id="19820-167">Bestimmen Sie, welche Konten verwaltet werden und welche Art der Authentifizierung verwendet werden soll. </span><span class="sxs-lookup"><span data-stu-id="19820-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="19820-168">Konten für Website-Entwickler und -Autoren</span><span class="sxs-lookup"><span data-stu-id="19820-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="19820-169">Fügen Sie der Domäne in Azure Konten hinzu. </span><span class="sxs-lookup"><span data-stu-id="19820-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="19820-170">Verwenden Sie lokal die Active Directory-Verbunddienste (AD FS), um die internen Konten mit der Domäne in Azure zu verbinden. </span><span class="sxs-lookup"><span data-stu-id="19820-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="19820-171">Wenn der Entwurf eine Standort-zu-Standort-VPN-Verbindung enthält, verwenden Sie die internen Konten. </span><span class="sxs-lookup"><span data-stu-id="19820-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="19820-172">Konten für Kunden</span><span class="sxs-lookup"><span data-stu-id="19820-172">Accounts for customers</span></span>

- <span data-ttu-id="19820-173">Verwenden Sie Azure Active Directory. </span><span class="sxs-lookup"><span data-stu-id="19820-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="19820-174">Verwenden Sie einen anderen SAML-basierten Anbieter. </span><span class="sxs-lookup"><span data-stu-id="19820-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="19820-175">Entwurf für Zonen</span><span class="sxs-lookup"><span data-stu-id="19820-175">Design for zones</span></span>

<span data-ttu-id="19820-176">In SharePoint 2013 wird die Identitätsverwaltung bei der Konfiguration der Zonen und Authentifizierung berücksichtigt. </span><span class="sxs-lookup"><span data-stu-id="19820-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="19820-177">Dieser Entwurf bietet eine klare Trennung zwischen Kundenkonten und allen anderen Konten. </span><span class="sxs-lookup"><span data-stu-id="19820-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="19820-178">Verwenden Sie diesen Entwurf, wenn Sie Kundenkonten komplett anders als die internen Konten für Autoren und Website-Entwickler behandeln möchten. </span><span class="sxs-lookup"><span data-stu-id="19820-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="19820-179">Mithilfe dieses Designs können Sie Zonenrichtlinien verwenden, um Aktionen des Kunden innerhalb einer Webanwendung zu beschränken. </span><span class="sxs-lookup"><span data-stu-id="19820-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="19820-180">Dieser Entwurf führt zu verschiedenen URLs für Kundenkonten und interne Konten. </span><span class="sxs-lookup"><span data-stu-id="19820-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="19820-181">In diesem Beispiel:</span><span class="sxs-lookup"><span data-stu-id="19820-181">In this example:</span></span> 
  
- <span data-ttu-id="19820-182">Konfigurieren Sie die Standardzone für interne Konten. </span><span class="sxs-lookup"><span data-stu-id="19820-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="19820-p112">Konfigurieren Sie die Extranetzone für den authentifizierten Kundenzugriff. Verwenden Sie Azure Active Directory (AD) für Kundenkonten, oder verwenden Sie einen anderen SAML-basierten Anbieter. </span><span class="sxs-lookup"><span data-stu-id="19820-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="19820-185">Konfigurieren Sie die Internetzone für den anonymen Zugriff.  </span><span class="sxs-lookup"><span data-stu-id="19820-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="19820-186">Verwenden Sie keine zwei-Zonen-Design in der alle authentifizierten Benutzer konfiguriert sind, um die Standardzone zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="19820-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="19820-187">Das zugehörige Diagramm zeigt einen Drei-Zonen-Entwurf mit Trennung von internen und Kundenkonten.  </span><span class="sxs-lookup"><span data-stu-id="19820-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="19820-p113">Kunden und Besucher Zugriff auf den Azure AD-Mandanten in SharePoint 2013-Farm über Webanwendungen in einer der beiden Zonen. Die zwei Zonen umfassen:</span><span class="sxs-lookup"><span data-stu-id="19820-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="19820-190">Zone: Internet für anonyme Benutzer </span><span class="sxs-lookup"><span data-stu-id="19820-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="19820-191">Zone: Extranet für authentifizierte Benutzer </span><span class="sxs-lookup"><span data-stu-id="19820-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="19820-p114">Benutzer mit internen Konten greifen über AD DS auf den Azure Active Directory-Mandanten zu und in der lokalen Umgebung durch den VPN-Tunnel zu Azure AD auf AD FS. Die Standardzone bietet Windows-Authentifizierung (NTLM). </span><span class="sxs-lookup"><span data-stu-id="19820-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="19820-194">Entwurf für das Herstellen einer Verbindung mit Azure AD</span><span class="sxs-lookup"><span data-stu-id="19820-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="19820-p115">Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste. Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS. Die in Azure AD enthaltenen Identitätsdienste lassen sich problemlos in Ihre lokalen AD DS-Bereitstellungen integrieren und unterstützen andere Identitätsanbieter umfassend. </span><span class="sxs-lookup"><span data-stu-id="19820-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="19820-198">Das zugehörige Diagramm zeigt das folgende Szenario: </span><span class="sxs-lookup"><span data-stu-id="19820-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="19820-199">Bei der Integration von SharePoint 2013 mit Azure Active Directory dient ein Azure Access Control Service (ACS) zwei Zwecken:</span><span class="sxs-lookup"><span data-stu-id="19820-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="19820-p116"> Azure AD verwendet SAML 2.0 und SharePoint funktioniert nur mit SAML 1.1. ACS versteht beide Formate und fungiert als Vermittler zum Transformieren der Tokenformate zwischen SharePoint und Azure AD.   </span><span class="sxs-lookup"><span data-stu-id="19820-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="19820-202">ACS ersetzt die Notwendigkeit des Identitätsanbieter-Sicherheitstokendiensts (IP-STS) für dieses SAML-Szenario. </span><span class="sxs-lookup"><span data-stu-id="19820-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="19820-203">Weitere Informationen finden Sie in der TechNet-Bibliothek unter „Konfigurieren von Azure AD mit SharePoint 2013“. </span><span class="sxs-lookup"><span data-stu-id="19820-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="19820-204">Entwurf von Websites und URLs für die websiteübergreifende Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="19820-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="19820-205">Für die Veröffentlichung wird ein Entwurf mit einer Webanwendung empfohlen. </span><span class="sxs-lookup"><span data-stu-id="19820-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="19820-206">Websites zur Dokumenterstellung und zur Veröffentlichung sind in derselben Webanwendung. </span><span class="sxs-lookup"><span data-stu-id="19820-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="19820-207">Zur Veröffentlichung von Objekten wird die websiteübergreifende Veröffentlichung verwendet. </span><span class="sxs-lookup"><span data-stu-id="19820-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="19820-208">Verwenden Sie pfadbasierte und hostbenannte Websitesammlungen. </span><span class="sxs-lookup"><span data-stu-id="19820-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="19820-p117">Eine Stammwebsitesammlung ist erforderlich. Erstellen Sie diese Website als pfadbasierte Website. </span><span class="sxs-lookup"><span data-stu-id="19820-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="19820-211">Erstellen Sie alle anderen Websitesammlungen als hostbenannte Websitesammlungen. </span><span class="sxs-lookup"><span data-stu-id="19820-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="19820-212">Webanwendung und Stammwebsite-URLs </span><span class="sxs-lookup"><span data-stu-id="19820-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="19820-p118">Verwenden Sie einen internen Namen für die URL der Webanwendung. SharePoint verwendet den Namen des lokalen Computers als Standardnamen, sofern kein anderer Name angegeben wird. Sie können einen Domänennamen verwenden, der für die interne Netzwerkumgebung reserviert ist.  </span><span class="sxs-lookup"><span data-stu-id="19820-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="19820-p119">SharePoint weist bei der Erstellung der Webanwendung eine nicht standardmäßige Portnummer zu. Verwenden Sie diese Portnummer statt Port 80 oder Port 443. Oder verwenden Sie eine andere nicht standardmäßige Portnummer. </span><span class="sxs-lookup"><span data-stu-id="19820-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="19820-219">Verwenden Sie denselben Namen und dieselbe Portnummer für die Stammwebsitesammlung, bei der es sich um eine pfadbasierte Websitesammlung handelt. </span><span class="sxs-lookup"><span data-stu-id="19820-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="19820-p120">Das zugehörige Diagramm zeigt Anwendungspooldienste, z. B. Suchen in Websitesammlungen mithilfe von Webanwendungen. Die gezeigt Websitesammlung enthält: </span><span class="sxs-lookup"><span data-stu-id="19820-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="19820-222">Pfadbasierte Websitesammlung, die unter http://internal:8000 (Stammwebsite) zu finden ist. </span><span class="sxs-lookup"><span data-stu-id="19820-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="19820-223">Durchforstung: Hostbenannte Websitesammlungen, die unter einer Adresse wie z. B. https://authoring.contoso.com:8000 zu finden ist. </span><span class="sxs-lookup"><span data-stu-id="19820-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="19820-224">Abfragen: 2 separate hostbenannte Websitesammlungen, die unter Adresse wie etwa den folgenden zu finden sind: </span><span class="sxs-lookup"><span data-stu-id="19820-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="19820-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19820-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="19820-226">https://Secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19820-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="19820-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="19820-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="19820-228">http://Assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19820-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="19820-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19820-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="19820-230">http://Assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="19820-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="19820-231">Entwurf der Azure-Umgebung</span><span class="sxs-lookup"><span data-stu-id="19820-231">Design the Azure environment</span></span>

<span data-ttu-id="19820-232">Diese Beispielarchitektur umfasst folgende Elemente: </span><span class="sxs-lookup"><span data-stu-id="19820-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="19820-233">Eine Standort-zu-Standort-VPN-Verbindung ist optional und weitet die lokale Windows AD DS- und DNS-Umgebung auf das virtuelle Netzwerk in Azure aus. </span><span class="sxs-lookup"><span data-stu-id="19820-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="19820-234">Verwenden Sie zur Unterstützung der SharePoint-Farm optional eine dedizierte Domäne in Azure. </span><span class="sxs-lookup"><span data-stu-id="19820-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="19820-235">Server werden entsprechend der Rolle auf Azure-Clouddienste verteilt. </span><span class="sxs-lookup"><span data-stu-id="19820-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="19820-236">Verfügbarkeitssätze garantieren eine hohe Verfügbarkeit identisch konfigurierten Serverrollen.  </span><span class="sxs-lookup"><span data-stu-id="19820-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="19820-237">Weitere Informationen finden Sie im folgenden TechNet-Artikel: Azure-Architekturen für SharePoint-Lösungen. </span><span class="sxs-lookup"><span data-stu-id="19820-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="19820-238">Das zugehörige Diagramm zeigt ein Beispiel einer lokalen Umgebung, die mit einem virtuellen Azure-Netzwerk verbunden wird.   </span><span class="sxs-lookup"><span data-stu-id="19820-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="19820-239">Die lokalen Umgebung (ein optionales Element der Azure-Umgebung) umfasst die folgenden Komponenten: </span><span class="sxs-lookup"><span data-stu-id="19820-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="19820-240">Windows Server 2012 RRAS </span><span class="sxs-lookup"><span data-stu-id="19820-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="19820-241">AD DS</span><span class="sxs-lookup"><span data-stu-id="19820-241">AD DS</span></span> 
    
- <span data-ttu-id="19820-242">Ein VPN-Gateway von Windows Server und AD DS zum aktiven VPN-Gateway-Subnetz </span><span class="sxs-lookup"><span data-stu-id="19820-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="19820-243">Die virtuelle Azure-Netzwerkumgebung umfasst die folgenden Komponenten: </span><span class="sxs-lookup"><span data-stu-id="19820-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="19820-244">Das aktive VPN-Gateway-Subnetz (überlappend mit der lokalen Umgebung, falls zutreffend) </span><span class="sxs-lookup"><span data-stu-id="19820-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="19820-245">Clouddienst, der AD DS- und DNS-Verfügbarkeitssätze umfasst (zwei Server) </span><span class="sxs-lookup"><span data-stu-id="19820-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="19820-246">Clouddienst, der die Verfügbarkeitssätze der Front-End-Server (drei SharePoint Server) und die Verfügbarkeitssätze des App-Servers enthält (drei SharePoint Server) </span><span class="sxs-lookup"><span data-stu-id="19820-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="19820-247">Clouddienst, der die beiden Verfügbarkeitssätze für die Datenbanken enthält. </span><span class="sxs-lookup"><span data-stu-id="19820-247">Cloud service that contains two database availability sets</span></span> 
    

