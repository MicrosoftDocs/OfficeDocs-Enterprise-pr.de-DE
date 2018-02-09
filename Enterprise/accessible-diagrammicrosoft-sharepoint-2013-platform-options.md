---
title: "Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Microsoft SharePoint 2013-Plattformoptionen“."
ms.openlocfilehash: 1f0d2bf4e74c7e1d28aaa27c6f88dac04f02b4a9
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="c696d-103">Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen</span><span class="sxs-lookup"><span data-stu-id="c696d-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="c696d-104">**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Microsoft SharePoint 2013-Plattformoptionen.</span><span class="sxs-lookup"><span data-stu-id="c696d-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="c696d-105">Was Entscheidungsträger (BDMs) und konstruiert zu Office 365, Microsoft Azure und lokale Bereitstellungen wissen müssen.</span><span class="sxs-lookup"><span data-stu-id="c696d-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="c696d-106">Dieses Poster hat zwei Abschnitte:</span><span class="sxs-lookup"><span data-stu-id="c696d-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="c696d-107">Einen Vergleich der vier verschiedenen Bereitstellungen für SharePoint 2013: SharePoint im Office 365, einer hybriden von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013, Azure und einer lokalen Bereitstellung von SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="c696d-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="c696d-108">Eine Beschreibung der drei typische Arbeitslasten in Azure verschieben.</span><span class="sxs-lookup"><span data-stu-id="c696d-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="c696d-109">Vergleich von vier verschiedenen Bereitstellungen für die SharePoint 2013-Plattform</span><span class="sxs-lookup"><span data-stu-id="c696d-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="c696d-110">Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit:</span><span class="sxs-lookup"><span data-stu-id="c696d-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="c696d-111">Übersicht der verschiedenen Bereitstellungsfeatures</span><span class="sxs-lookup"><span data-stu-id="c696d-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="c696d-112">Vorteile der einzelnen Arten der Bereitstellung </span><span class="sxs-lookup"><span data-stu-id="c696d-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="c696d-113">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="c696d-113">License requirements</span></span> 
    
- <span data-ttu-id="c696d-114">Für die Implementierung erforderliche Architekturaufgaben </span><span class="sxs-lookup"><span data-stu-id="c696d-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="c696d-115">Verantwortlichkeiten von IT-Experten für die Implementierung </span><span class="sxs-lookup"><span data-stu-id="c696d-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="c696d-116">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c696d-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="c696d-117">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="c696d-118">Mehr Effizienz und Optimierung für Kosten mit mandantenfähigen Office 365-Pläne.</span><span class="sxs-lookup"><span data-stu-id="c696d-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="c696d-119">Das zugehörige Diagramm zeigt SharePoint Online mit einer Azure Active Directory-Instanz, Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="c696d-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="c696d-120">Beschreibung der Features:</span><span class="sxs-lookup"><span data-stu-id="c696d-120">Description of features:</span></span> 
  
- <span data-ttu-id="c696d-121">Software as a Service (SaaS).</span><span class="sxs-lookup"><span data-stu-id="c696d-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="c696d-122">Die umfangreiche Funktionspalette ist stets auf dem neuesten Stand. </span><span class="sxs-lookup"><span data-stu-id="c696d-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="c696d-123">Enthält ein Azure Active Directory-Mandanten (kann mit einer anderen Anwendung verwendet werden).</span><span class="sxs-lookup"><span data-stu-id="c696d-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="c696d-124">Verzeichnisintegration umfasst Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="c696d-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="c696d-125">Falls einmaliges Anmelden (SSO) eine Anforderung ist, können Active Directory-Verbunddienste (Active Directory Federation Services, AD FS) implementiert werden.  </span><span class="sxs-lookup"><span data-stu-id="c696d-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="c696d-126">Clientkommunikation über das Internet über verschlüsselten und authentifizierten Zugriff (Port 443). </span><span class="sxs-lookup"><span data-stu-id="c696d-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="c696d-127">Die Datenmigration ist darauf beschränkt, was über das Internet hochgeladen werden kann. </span><span class="sxs-lookup"><span data-stu-id="c696d-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="c696d-128">Anpassungen: Apps für Office, SharePoint und SharePoint Designer 2013. </span><span class="sxs-lookup"><span data-stu-id="c696d-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="c696d-129">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-129">Hybrid with Office 365</span></span>

<span data-ttu-id="c696d-130">Kombiniert die Vorteile von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="c696d-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="c696d-131">Das zugehörige Diagramm zeigt die Office 365 mit SharePoint Online mit Business Connectivity Services (BCS) für die Verbindung zu einer lokalen SharePoint Server 2013-Farm.</span><span class="sxs-lookup"><span data-stu-id="c696d-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="c696d-132">Wählen Sie aus, welche der folgenden Features integriert werden sollen: </span><span class="sxs-lookup"><span data-stu-id="c696d-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="c696d-133">SharePoint-Suche</span><span class="sxs-lookup"><span data-stu-id="c696d-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="c696d-134">Benutzer können Suchergebnisse aus beiden Umgebungen anzeigen.  </span><span class="sxs-lookup"><span data-stu-id="c696d-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="c696d-135">Extranet-Benutzer können sich remote mit einem lokalen Active Directory-Konto anmelden und die gesamte Hybridfunktionalität nutzen. </span><span class="sxs-lookup"><span data-stu-id="c696d-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="c696d-136">BCS</span><span class="sxs-lookup"><span data-stu-id="c696d-136">BCS</span></span>
  
<span data-ttu-id="c696d-p101">Aus SharePoint Online: Benutzer können Lese- und Schreibvorgänge ausführen. Der BCS-Dienst stellt eine Verbindung mit einer lokalen SharePoint Server 2013-Farm her. Der für die lokale Farm konfigurierte BCS-Dienst vermittelt die Verbindung mit den lokalen OData-Dienstendpunkten.  </span><span class="sxs-lookup"><span data-stu-id="c696d-p101">From SharePoint Online: Users can perform both read and write operations. The BCS service connects to an on-premises SharePoint Server 2013 farm. The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="c696d-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="c696d-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="c696d-141">Aus SharePoint Online können Benutzer Lese- und Schreibvorgänge für ein lokales SAP-System ausführen. </span><span class="sxs-lookup"><span data-stu-id="c696d-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="c696d-142">Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-142">Azure</span></span>

<span data-ttu-id="c696d-143">Kommen Sie in den Genuss der Cloud, ohne die volle Kontrolle über die Plattform und Features zu verlieren.  </span><span class="sxs-lookup"><span data-stu-id="c696d-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="c696d-144">Das zugehörige Diagramm zeigt Azure, die zwei Clouddiensten, einer SharePoint 2013-Farm und Windows Server Active Directory mit DNS Herstellen einer Verbindung mit Benutzern über das Internet oder Herstellen einer Verbindung mit der lokalen Active Directory über VPN-Tunnels enthält.</span><span class="sxs-lookup"><span data-stu-id="c696d-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="c696d-145">Zu den Features zählen: </span><span class="sxs-lookup"><span data-stu-id="c696d-145">Features include:</span></span> 
  
-  <span data-ttu-id="c696d-146">Azure ist eine Plattform, die die zum Hosten einer SharePoint 2013-Farm erforderlichen Infrastruktur und app-Dienste bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="c696d-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="c696d-147">Infrastrukturdienste:</span><span class="sxs-lookup"><span data-stu-id="c696d-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="c696d-148">Beste systemeigene Cloudplattform für SQL Server und SharePoint. </span><span class="sxs-lookup"><span data-stu-id="c696d-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="c696d-149">EDV-Ressourcen stehen nahezu unverzüglich ohne Verpflichtung zur Verfügung. </span><span class="sxs-lookup"><span data-stu-id="c696d-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="c696d-150">Schwerpunkt auf Anwendungen, nicht auf Rechenzentren und Infrastruktur. </span><span class="sxs-lookup"><span data-stu-id="c696d-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="c696d-151">Kostengünstige Entwicklungs- und Testumgebungen. </span><span class="sxs-lookup"><span data-stu-id="c696d-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="c696d-152">Der Zugriff auf SharePoint-Lösungen kann über das Internet ermöglicht oder über einen VPN-Tunnel zwischen Standorten auf eine Unternehmensumgebung beschränkt werden. </span><span class="sxs-lookup"><span data-stu-id="c696d-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="c696d-153">Anpassungen sind nicht eingeschränkt. </span><span class="sxs-lookup"><span data-stu-id="c696d-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="c696d-154">Lokal</span><span class="sxs-lookup"><span data-stu-id="c696d-154">On premises</span></span>

<span data-ttu-id="c696d-155">Ihre Zuständigkeit gilt für alles.  </span><span class="sxs-lookup"><span data-stu-id="c696d-155">You own everything.</span></span> 
  
<span data-ttu-id="c696d-156">Das begleitende Diagramm zeigt eine lokale Umgebung mit Webservern, Anwendungsservern und Active Directory, das für die Suche mit allen Datenbanken und dedizierten Anwendungsservern kommuniziert. </span><span class="sxs-lookup"><span data-stu-id="c696d-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="c696d-157">Zu den Features zählen: </span><span class="sxs-lookup"><span data-stu-id="c696d-157">Features include:</span></span> 
  
- <span data-ttu-id="c696d-158">Planung und Festlegung des Umfangs der Kapazität</span><span class="sxs-lookup"><span data-stu-id="c696d-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="c696d-159">Serverbeschaffung und -einrichtung</span><span class="sxs-lookup"><span data-stu-id="c696d-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="c696d-160">Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="c696d-160">Deployment.</span></span> 
    
- <span data-ttu-id="c696d-161">Horizontale Skalierung, Patching und Betrieb</span><span class="sxs-lookup"><span data-stu-id="c696d-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="c696d-162">Sichern von Daten</span><span class="sxs-lookup"><span data-stu-id="c696d-162">Backing up data.</span></span> 
    
- <span data-ttu-id="c696d-163">Vorhalten einer Umgebung für die Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="c696d-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="c696d-164">Anpassungen sind nicht eingeschränkt. </span><span class="sxs-lookup"><span data-stu-id="c696d-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="c696d-p102">Vorteile der Bereitstellungsarten</span><span class="sxs-lookup"><span data-stu-id="c696d-p102">Deployment type is best for . . .</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="c696d-168">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="c696d-p103">Sichere externe Freigabe von Daten und Zusammenarbeit. (besonderes Feature!) </span><span class="sxs-lookup"><span data-stu-id="c696d-p103">Secure external sharing and collaboration. (Unique feature!)</span></span> 
    
- <span data-ttu-id="c696d-171">Intranet – Teamwebsites, Meine Websites und interne Zusammenarbeit. </span><span class="sxs-lookup"><span data-stu-id="c696d-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="c696d-172">Dokumentspeicherung und -versionsverwaltung in der Cloud. </span><span class="sxs-lookup"><span data-stu-id="c696d-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="c696d-173">Einfache öffentlich zugängliche Website. </span><span class="sxs-lookup"><span data-stu-id="c696d-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="c696d-174">Zusätzliche Features mit Office 365 dedizierte Abonnementpläne:</span><span class="sxs-lookup"><span data-stu-id="c696d-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="c696d-175">Microsoft-Rechenzentrumssysteme, die Ihrer Organisation fest zugeordnet sind und nicht mit anderen Organisationen gemeinsam genutzt werden.  </span><span class="sxs-lookup"><span data-stu-id="c696d-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="c696d-176">Jede Kundenumgebung befindet sich in einem physisch getrennten Netzwerk. </span><span class="sxs-lookup"><span data-stu-id="c696d-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="c696d-p104">Clientkommunikation über ein mit IPSec geschütztes VPN oder eine private Verbindung in der Zuständigkeit des Kunden. Zweistufige Authentifizierung ist optional. </span><span class="sxs-lookup"><span data-stu-id="c696d-p104">Client communication across an IPSec-secured VPN or customer-owned private connection. Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="c696d-179">Pläne mit ITAR-Unterstützung. </span><span class="sxs-lookup"><span data-stu-id="c696d-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="c696d-180">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="c696d-181">Verwenden von Office 365 für externe Freigabe und Zusammenarbeit anstelle der Einrichtung einer Extranetumgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="c696d-182">Verschieben Sie „Meine Websites“ (OneDrive for Business) in die Cloud, damit Benutzer remote einfacher auf ihre Dateien zugreifen können.  </span><span class="sxs-lookup"><span data-stu-id="c696d-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="c696d-183">Starten Sie neue Teamwebsites in Office 365.</span><span class="sxs-lookup"><span data-stu-id="c696d-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="c696d-184">Integrieren von Office 365-Website in lokalen BCS-SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="c696d-185">Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-185">Azure</span></span>

- <span data-ttu-id="c696d-p105">SharePoint für Internetwebsites – öffentliche facing Websites. Nutzen Sie die Vorteile von Azure Active Directory für Kundenkonten und Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="c696d-p105">SharePoint for Internet Sites — Public facing sites. Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="c696d-188">Entwicklungs-, Test- und Stagingumgebungen – Schnelle In- und Außerbetriebnahme ganzer Umgebungen. </span><span class="sxs-lookup"><span data-stu-id="c696d-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="c696d-189">Hybridanwendungen – Anwendungen können sich in Ihrem Rechenzentrum und der Cloud befinden. </span><span class="sxs-lookup"><span data-stu-id="c696d-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="c696d-p106">Umgebung für die Notfallwiederherstellung – Schnelle Wiederherstellung nach einem Notfall. Rein nutzungsabhängige Zahlung. </span><span class="sxs-lookup"><span data-stu-id="c696d-p106">Disaster recovery environment — Quickly recover from a disaster. Pay only for use.</span></span> 
    
- <span data-ttu-id="c696d-192">Farmen, für die eine umfassende Berichterstellung und Überwachung erforderlich sind. </span><span class="sxs-lookup"><span data-stu-id="c696d-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="c696d-193">Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="c696d-193">Web analytics.</span></span> 
    
- <span data-ttu-id="c696d-194">Verschlüsselung gespeicherter Daten (in den SQL-Datenbanken). </span><span class="sxs-lookup"><span data-stu-id="c696d-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="c696d-195">Verschlüsselung gespeicherter Daten (in den SQL-Datenbanken)</span><span class="sxs-lookup"><span data-stu-id="c696d-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="c696d-196">Auf Landesgrenzen beschränkte Farmen (wenn sich die Daten in einem bestimmten Rechtsraum befinden müssen). </span><span class="sxs-lookup"><span data-stu-id="c696d-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="c696d-197">Komplexe BI-Lösungen, die sich in der Nähe von BI-Daten befinden müssen. </span><span class="sxs-lookup"><span data-stu-id="c696d-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="c696d-198">Private Cloudlösungen. </span><span class="sxs-lookup"><span data-stu-id="c696d-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="c696d-199">Hoch angepasste Lösungen.</span><span class="sxs-lookup"><span data-stu-id="c696d-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="c696d-200">Legacy-Lösungen mit Drittanbieter-Komponenten, die abhängig von Hardware und Software, die nicht auf Azure Infrastructure Services unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="c696d-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="c696d-201">Private-Einschränkungen, die Synchronisierung von Active Directory-Benutzerkonten mit Azure Active Directory (eine Voraussetzung für Office 365) zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="c696d-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="c696d-202">Organisationen, die Kontrolle über die gesamte Plattform und Lösung bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="c696d-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="c696d-203">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="c696d-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="c696d-204">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="c696d-p107">Abonnementmodell. Keine weiteren Lizenzen nötig. </span><span class="sxs-lookup"><span data-stu-id="c696d-p107">Subscription model. No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="c696d-207">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="c696d-p108">Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig.</span><span class="sxs-lookup"><span data-stu-id="c696d-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="c696d-210">Lokal – Alle lokalen Lizenzen sind gültig.</span><span class="sxs-lookup"><span data-stu-id="c696d-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="c696d-211">Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-211">Azure</span></span>

-  <span data-ttu-id="c696d-212">Azure-Abonnement (umfasst das Serverbetriebssystem)</span><span class="sxs-lookup"><span data-stu-id="c696d-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="c696d-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c696d-213">SQL Server</span></span> 
    
- <span data-ttu-id="c696d-214">SharePoint 2013-Serverlizenz</span><span class="sxs-lookup"><span data-stu-id="c696d-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="c696d-215">SharePoint 2013-Clientzugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="c696d-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="c696d-216">Lokal</span><span class="sxs-lookup"><span data-stu-id="c696d-216">On premises</span></span>

- <span data-ttu-id="c696d-217">Serverbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="c696d-217">Server operating system</span></span> 
    
- <span data-ttu-id="c696d-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c696d-218">SQL Server</span></span> 
    
- <span data-ttu-id="c696d-219">SharePoint 2013-Serverlizenz</span><span class="sxs-lookup"><span data-stu-id="c696d-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="c696d-220">SharePoint 2013-Clientzugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="c696d-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="c696d-221">Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="c696d-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="c696d-222">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="c696d-p109">Verzeichnisintegration planen und entwerfen. Zwei Optionen. Mit beiden Optionen bereitgestellt werden kann, lokal oder in Azure: Kennwort Sync (erfordert eine 64-Bit-Server). SSO (AD FS und mehreren Servern erfordert).</span><span class="sxs-lookup"><span data-stu-id="c696d-p109">Plan and design directory integration. Two options. Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server). SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="c696d-227">Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="c696d-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="c696d-228">Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote.</span><span class="sxs-lookup"><span data-stu-id="c696d-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="c696d-229">Planen des Mandantennamens, Entwerfen von Architektur und Steuerung der Websitesammlung. </span><span class="sxs-lookup"><span data-stu-id="c696d-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="c696d-230">Planen von Anpassungen, Lösungen und Apps für SharePoint Online. </span><span class="sxs-lookup"><span data-stu-id="c696d-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="c696d-p110">Entscheiden Sie, ob Sie über das Internetprotokoll 6 (IPv6) mit Office 365 verbinden möchten. Dies wird nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="c696d-p110">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6). This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="c696d-233">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-233">Hybrid with Office 365</span></span>

<span data-ttu-id="c696d-234">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="c696d-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="c696d-p111">Bestimmen Sie, wie viele Features integriert werden sollen, und wählen Sie die Hybridtopologie. Siehe das Poster dieses Modells: Welche Hybridtopologie soll ich verwenden? </span><span class="sxs-lookup"><span data-stu-id="c696d-p111">Determine how much feature integration you want and choose the hybrid topology. See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="c696d-237">Bestimmen Sie, falls erforderlich, welches Proxyservergerät verwendet werden soll. </span><span class="sxs-lookup"><span data-stu-id="c696d-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="c696d-238">Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-238">Azure</span></span>

<span data-ttu-id="c696d-239">Entwerfen Sie die Netzwerkumgebung auf Azure:</span><span class="sxs-lookup"><span data-stu-id="c696d-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="c696d-240">Virtuelles Netzwerk in Azure, einschließlich Subnetze.</span><span class="sxs-lookup"><span data-stu-id="c696d-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="c696d-241">Domänenumgebung und Integration mit lokalen Servern. </span><span class="sxs-lookup"><span data-stu-id="c696d-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="c696d-242">IP-Adressen und DNS. </span><span class="sxs-lookup"><span data-stu-id="c696d-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="c696d-243">Affinitätsgruppen und Speicherkonten. </span><span class="sxs-lookup"><span data-stu-id="c696d-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="c696d-244">Entwerfen der SharePoint-Umgebung in Azure:</span><span class="sxs-lookup"><span data-stu-id="c696d-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="c696d-245">Topologie und logische Architektur der SharePoint-Farm. </span><span class="sxs-lookup"><span data-stu-id="c696d-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="c696d-246">Azure verfügbarkeitssätze und Domänen aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c696d-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="c696d-247">Festlegen der Größen virtueller Computer.  </span><span class="sxs-lookup"><span data-stu-id="c696d-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="c696d-248">Endpunkt mit Lastenausgleich. </span><span class="sxs-lookup"><span data-stu-id="c696d-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="c696d-249">Nach Wunsch externe Endpunkte für öffentlichen Zugriff.  </span><span class="sxs-lookup"><span data-stu-id="c696d-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="c696d-250">Notfallwiederherstellungsumgebung. </span><span class="sxs-lookup"><span data-stu-id="c696d-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="c696d-251">Lokal</span><span class="sxs-lookup"><span data-stu-id="c696d-251">On premises</span></span>

<span data-ttu-id="c696d-252">Entwerfen der SharePoint-Umgebung in einer vorhandenen lokalen Umgebung: </span><span class="sxs-lookup"><span data-stu-id="c696d-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="c696d-253">Topologie und logische Architektur der SharePoint-Farm. </span><span class="sxs-lookup"><span data-stu-id="c696d-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="c696d-254">Server-Hardware.</span><span class="sxs-lookup"><span data-stu-id="c696d-254">Server hardware.</span></span> 
    
- <span data-ttu-id="c696d-255">Virtuelle Umgebung, falls verwendet. </span><span class="sxs-lookup"><span data-stu-id="c696d-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="c696d-256">Lastenausgleich.</span><span class="sxs-lookup"><span data-stu-id="c696d-256">Load balancing.</span></span> 
    
- <span data-ttu-id="c696d-257">Integration in AD DS und DNS.  </span><span class="sxs-lookup"><span data-stu-id="c696d-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="c696d-258">Notfallwiederherstellungsumgebung. </span><span class="sxs-lookup"><span data-stu-id="c696d-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="c696d-259">Verantwortlichkeiten von IT-Experten</span><span class="sxs-lookup"><span data-stu-id="c696d-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="c696d-260">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="c696d-261">Stellen Sie sicher, dass Benutzerarbeitsstationen Office 365-clientvoraussetzungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="c696d-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="c696d-262">Implementieren des Verzeichnisintegrationsplans.</span><span class="sxs-lookup"><span data-stu-id="c696d-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="c696d-263">Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.</span><span class="sxs-lookup"><span data-stu-id="c696d-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="c696d-264">Konfigurieren der Proxy oder der Firewall für Office 365-IP-Adresse und URL-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="c696d-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="c696d-265">Erstellen und Zuweisen von Berechtigungen zu Websitesammlungen. </span><span class="sxs-lookup"><span data-stu-id="c696d-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="c696d-266">Implementieren von Anpassungen, Lösungen und Apps für SharePoint Online. </span><span class="sxs-lookup"><span data-stu-id="c696d-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="c696d-267">Überwachen der Netzwerkverfügbarkeit und Bestimmen möglicher Engpässe. </span><span class="sxs-lookup"><span data-stu-id="c696d-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="c696d-268">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-268">Hybrid with Office 365</span></span>

<span data-ttu-id="c696d-269">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="c696d-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="c696d-270">Konfigurieren Sie, sofern erforderlich, das Proxyservergerät.</span><span class="sxs-lookup"><span data-stu-id="c696d-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="c696d-271">Konfigurieren Sie die hybride Identitätsverwaltungsinfrastruktur: Einmaliges Anmelden und Server-zu-Server-Authentifizierung zwischen den beiden Umgebungen. </span><span class="sxs-lookup"><span data-stu-id="c696d-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="c696d-272">Konfigurieren Sie die Integration der gewählten Features: Suche, BCS, Duet Enterprise Online. </span><span class="sxs-lookup"><span data-stu-id="c696d-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="c696d-273">Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-273">Azure</span></span>

<span data-ttu-id="c696d-274">Bereitstellen und Verwalten von Azure und SharePoint-Umgebung:</span><span class="sxs-lookup"><span data-stu-id="c696d-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="c696d-275">Implementieren und Verwalten von Azure Netzwerkumgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="c696d-276">Bereitstellen der SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="c696d-277">Aktualisieren der SharePoint-Farmserver. </span><span class="sxs-lookup"><span data-stu-id="c696d-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="c696d-278">Bedarfsabhängiges Hinzufügen oder Herunterfahren virtueller Computer basierend auf der Farmauslastung. </span><span class="sxs-lookup"><span data-stu-id="c696d-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="c696d-279">Erhöhen oder Verringern der Größe virtueller Computer den Anforderungen entsprechend. </span><span class="sxs-lookup"><span data-stu-id="c696d-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="c696d-280">Sichern der SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="c696d-281">Implementieren der Umgebung und des Protokolls für die Notfallwiederherstellung. </span><span class="sxs-lookup"><span data-stu-id="c696d-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="c696d-282">Lokal</span><span class="sxs-lookup"><span data-stu-id="c696d-282">On premises</span></span>

<span data-ttu-id="c696d-283">Bereitstellen und Verwalten der lokalen SharePoint-Umgebung: </span><span class="sxs-lookup"><span data-stu-id="c696d-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="c696d-284">Bereitstellen von Servern.</span><span class="sxs-lookup"><span data-stu-id="c696d-284">Provision servers.</span></span> 
    
- <span data-ttu-id="c696d-285">Bereitstellen der SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="c696d-286">Aktualisieren der SharePoint-Farmserver. </span><span class="sxs-lookup"><span data-stu-id="c696d-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="c696d-287">Bedarfsabhängiges Hinzufügen oder Entfernen von Farmservern basierend auf der Farmauslastung. </span><span class="sxs-lookup"><span data-stu-id="c696d-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="c696d-288">Sichern der SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="c696d-289">Implementieren der Umgebung und des Protokolls für die Notfallwiederherstellung. </span><span class="sxs-lookup"><span data-stu-id="c696d-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="c696d-290">Drei typische Arbeitslasten in Azure verschieben</span><span class="sxs-lookup"><span data-stu-id="c696d-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="c696d-291">Office 365 plus Verzeichniskomponenten in Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="c696d-292">Bereitstellen von Office 365-verzeichnisintegrationskomponenten in Azure ist schneller, da es bei Bedarf virtuellen Computern bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="c696d-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="c696d-293">Nur Verzeichnissynchronisierungsserver</span><span class="sxs-lookup"><span data-stu-id="c696d-293">Directory synchronization server only</span></span>

<span data-ttu-id="c696d-294">Die 64-Bit-Directory-Synchronisierungsserver in Ihrer lokalen Umgebung bereitstellen möchten, stellen Sie einen virtuellen Computer in Azure stattdessen bereit.</span><span class="sxs-lookup"><span data-stu-id="c696d-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="c696d-295">Das zugehörige Diagramm zeigt SharePoint Online mit einer Azure Active Directory-Instanz, Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und den Mandanten Azure Active Directory synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="c696d-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="c696d-296">Verzeichnissynchronisierung plus AD FS</span><span class="sxs-lookup"><span data-stu-id="c696d-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="c696d-p112">Diese Option können Sie Office 365 federated Identitäten (SSO) ohne Hardware in Ihrer lokalen Infrastruktur zu unterstützen. Es bietet auch Flexibilität, wenn die lokale Active Directory-Umgebung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c696d-p112">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="c696d-299">Verzeichnisintegrationskomponenten befinden sich im Azure.</span><span class="sxs-lookup"><span data-stu-id="c696d-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="c696d-300">AD FS ist mit dem Internet über AD FS-Proxys in Azure veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="c696d-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="c696d-301">Clientauthentifizierungsdatenverkehr für Benutzer, die von einer beliebigen Position verbinden wird von AD FS-Servern und -Proxys, die auf Azure bereitgestellten behandelt.</span><span class="sxs-lookup"><span data-stu-id="c696d-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="c696d-302">Öffentliche Internetwebsite und Azure AD für benutzerdefinierte Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="c696d-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="c696d-p113">Nutzen Sie die Möglichkeit, problemlos Anforderung skaliert durch Ihre Website in Azure platzieren. Verwenden Sie zum Speichern von Kundenkonten Azure AD.</span><span class="sxs-lookup"><span data-stu-id="c696d-p113">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure. Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="c696d-305">Azure Vorteile für Internetsites</span><span class="sxs-lookup"><span data-stu-id="c696d-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="c696d-306">Zahlen Sie nur für die Ressourcen, die Sie benötigen, indem Sie die Anzahl der virtuellen Computer abhängig von der Farmauslastung skalieren. </span><span class="sxs-lookup"><span data-stu-id="c696d-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="c696d-307">Fügen Sie eine umfassende Berichterstellung und Web Analytics hinzu.</span><span class="sxs-lookup"><span data-stu-id="c696d-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="c696d-308">Konzentrieren Sie sich auf die Entwicklung einer überzeugenden Website und nicht auf die Einrichtung von Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="c696d-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="c696d-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="c696d-309">Azure AD</span></span>

<span data-ttu-id="c696d-p114">Azure AD bietet Funktionen Identity Management und Zugriff für Steuerelement für Cloud-Dienste. Merkmale ein Cloud-basierten-Speichers für Directory-Daten und eine Kerngruppe von Identitätsdienste, einschließlich Benutzereingriffe, Authentifizierungsdienste und AD FS. Der Identitätsdienste, die mit Azure AD enthalten sind einfache Integration mit Ihrer lokalen Active Directory-Bereitstellungen und Drittanbieter-Identitätsanbieter vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c696d-p114">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="c696d-p115">Das zugehörige Diagramm veranschaulicht die Konfiguration von Zonen und Authentifizierung, die für das Internet gerichtete Websites wichtig sind. Das Diagramm zeigt die Azure Active Directory-Instanz, einer SharePoint-Farm auf Azure mit zwei Zonen enthält:</span><span class="sxs-lookup"><span data-stu-id="c696d-p115">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites. The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="c696d-315">Eine Internetzone, die mit anonymen und authentifizierten Besuchern und Kunden außerhalb des Netzwerks interagiert </span><span class="sxs-lookup"><span data-stu-id="c696d-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="c696d-316">Eine Standardzone, die NTLM für die Durchforstung und Windows-Authentifizierung umfasst, die mit Ihrer lokalen Active Directory-Bereitstellung über einen VPN Tunnel interagiert.  </span><span class="sxs-lookup"><span data-stu-id="c696d-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="c696d-317">Lokale Farm plus Disaster Recovery in Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="c696d-p116">Wählen Sie eine Disaster Recovery-Option, die Ihren geschäftlichen Anforderungen entspricht. Azure bietet Einstiegs-Optionen für Unternehmen, die erste Schritte mit Disaster Recovery und erweiterte Optionen für Unternehmen mit hoher Resiliency Requirements.</span><span class="sxs-lookup"><span data-stu-id="c696d-p116">Choose a disaster recovery option that matches your business requirements. Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="c696d-320">Verzögert betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="c696d-320">Cold standby</span></span>

- <span data-ttu-id="c696d-p117">Die Farm ist vollständig erstellt, aber die virtuellen Computer beendet werden. (Sie Zahlen nur, wenn ihnen ausgeführt wird.)</span><span class="sxs-lookup"><span data-stu-id="c696d-p117">The farm is fully built, but the virtual machines are stopped. (You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="c696d-323">Zur Verwaltung der Umgebung zählen das Starten der virtuellen Computer in regelmäßigen Abständen, das Einspielen von Patches und Updates sowie das Überprüfen der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c696d-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="c696d-324">Starten Sie die vollständige Umgebung bei einem Notfall.</span><span class="sxs-lookup"><span data-stu-id="c696d-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="c696d-325">Bedingt betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="c696d-325">Warm standby</span></span>

- <span data-ttu-id="c696d-326">Dies umfasst eine kleine Farm, die bereitgestellt ist und ausgeführt wird.  </span><span class="sxs-lookup"><span data-stu-id="c696d-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="c696d-327">Die Farm kann bei einem Failover sofort die Benutzer unterstützen.  </span><span class="sxs-lookup"><span data-stu-id="c696d-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="c696d-328">Skalieren Sie die Farm rasch horizontal, um den gesamten Benutzerstamm zu unterstützen. </span><span class="sxs-lookup"><span data-stu-id="c696d-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="c696d-329">Unmittelbar betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="c696d-329">Hot standby</span></span>

<span data-ttu-id="c696d-330">Eine vollständig dimensionierte Farm ist bereitgestellt und wird im Standby-Modus ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c696d-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="c696d-p118">Das zugehörige Diagramm zeigt eine Interaktion mit der SharePoint-Notfallwiederherstellungsumgebung in Azure lokale Farm. Die lokalen Datenbanken mithilfe von SQL Server-Protokollversand über VPN-Tunnels die Wiederherstellung der SharePoint-Umgebung zugreifen, die zwei SQL-Datenbankserver enthält, die die SharePoint-Datenbanken, zwei Web-Front-End-Servern und zwei SharePoint enthalten Anwendungsserver.</span><span class="sxs-lookup"><span data-stu-id="c696d-p118">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure. The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

