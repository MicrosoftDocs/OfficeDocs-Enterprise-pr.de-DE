---
title: Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
f1.keywords:
- NOCSH
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Microsoft SharePoint 2013 Plattformoptionen.
ms.openlocfilehash: 100645b8de8487497eca4a2581523818e18834b3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843876"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="41323-103">Zugängliches Diagramm – Microsoft SharePoint 2013-Plattformoptionen</span><span class="sxs-lookup"><span data-stu-id="41323-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="41323-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen Microsoft SharePoint 2013 Plattformoptionen.</span><span class="sxs-lookup"><span data-stu-id="41323-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="41323-105">Was Business decision makers (BDMs) und Architekten über Office 365, Microsoft Azure und lokale Bereitstellungen wissen müssen.</span><span class="sxs-lookup"><span data-stu-id="41323-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="41323-106">Dieses Poster besteht aus zwei Abschnitten:</span><span class="sxs-lookup"><span data-stu-id="41323-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="41323-107">Ein Vergleich von vier verschiedenen Bereitstellungen für SharePoint 2013: SharePoint in Office 365, eine Kombination aus Office 365 mit einer lokalen Bereitstellung von SharePoint 2013, Azure und einer lokalen Bereitstellung von SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="41323-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="41323-108">Eine Beschreibung von drei typischen Arbeitsauslastungen, die zu Azure migriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="41323-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="41323-109">Vergleich von vier verschiedenen Bereitstellungen für die SharePoint 2013 Plattform</span><span class="sxs-lookup"><span data-stu-id="41323-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="41323-110">Der Vergleich enthält Informationen zu den einzelnen Bereitstellungsoptionen im Zusammenhang mit den folgenden Bereichen:</span><span class="sxs-lookup"><span data-stu-id="41323-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="41323-111">Übersicht der verschiedenen Bereitstellungsfeatures</span><span class="sxs-lookup"><span data-stu-id="41323-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="41323-112">Vorteile der einzelnen Bereitstellungstypen</span><span class="sxs-lookup"><span data-stu-id="41323-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="41323-113">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="41323-113">License requirements</span></span> 
    
- <span data-ttu-id="41323-114">Für die Implementierung erforderliche Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="41323-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="41323-115">Verantwortlichkeiten für IT-Experten für die Implementierung</span><span class="sxs-lookup"><span data-stu-id="41323-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="41323-116">Übersicht</span><span class="sxs-lookup"><span data-stu-id="41323-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="41323-117">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="41323-118">Steigern Sie die Effizienz und optimieren Sie die Kosten mit Office 365 mehr Mandanten Plänen.</span><span class="sxs-lookup"><span data-stu-id="41323-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="41323-119">Das zugehörige Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="41323-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="41323-120">Beschreibung der Features:</span><span class="sxs-lookup"><span data-stu-id="41323-120">Description of features:</span></span> 
  
- <span data-ttu-id="41323-121">Software as a Service (SaaS).</span><span class="sxs-lookup"><span data-stu-id="41323-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="41323-122">Die umfangreiche Funktionsgruppe ist immer auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="41323-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="41323-123">Enthält einen Azure Active Directory-Mandanten (kann mit anderen Anwendungen verwendet werden).</span><span class="sxs-lookup"><span data-stu-id="41323-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="41323-124">Die Verzeichnisintegration umfasst das Synchronisieren von Kontonamen und Kennwörtern zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="41323-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="41323-125">Wenn einmaliges Anmelden (Single Sign-on, SSO) erforderlich ist, können Active Directory Verbunddienste (AD FS) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="41323-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="41323-126">Client Kommunikation über das Internet über einen verschlüsselten und authentifizierten Zugriff (Port 443).</span><span class="sxs-lookup"><span data-stu-id="41323-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="41323-127">Die Datenmigration ist auf das, was über das Internet hochgeladen werden kann, limitiert.</span><span class="sxs-lookup"><span data-stu-id="41323-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="41323-128">Anpassungen: Apps für Office, SharePoint und SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="41323-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="41323-129">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-129">Hybrid with Office 365</span></span>

<span data-ttu-id="41323-130">Kombinieren Sie die Vorteile von Office 365 mit einer lokalen Bereitstellung von SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="41323-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="41323-131">Das zugehörige Diagramm zeigt Office 365 mit SharePoint Online mit Business Connectivity Services (BCS) eine Verbindung mit einer lokalen SharePoint Server 2013 Farm herstellen.</span><span class="sxs-lookup"><span data-stu-id="41323-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="41323-132">Wählen Sie aus, welche der folgenden Features integriert werden sollen:</span><span class="sxs-lookup"><span data-stu-id="41323-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="41323-133">SharePoint-Suche</span><span class="sxs-lookup"><span data-stu-id="41323-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="41323-134">Benutzer können Suchergebnisse aus beiden Umgebungen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="41323-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="41323-135">Extranet-Benutzer können sich Remote mit einem lokalen Active Directory-Konto anmelden und alle verfügbaren hybridfunktionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="41323-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="41323-136">BCS</span><span class="sxs-lookup"><span data-stu-id="41323-136">BCS</span></span>
  
<span data-ttu-id="41323-137">Von SharePoint Online: Benutzer können Lese-und Schreibvorgänge ausführen.</span><span class="sxs-lookup"><span data-stu-id="41323-137">From SharePoint Online: Users can perform both read and write operations.</span></span> <span data-ttu-id="41323-138">Der BCS-Dienst stellt eine Verbindung mit einer lokalen SharePoint Server 2013 Farm her.</span><span class="sxs-lookup"><span data-stu-id="41323-138">The BCS service connects to an on-premises SharePoint Server 2013 farm.</span></span> <span data-ttu-id="41323-139">Der in der lokalen Farm konfigurierte BCS-Dienst vermittelt die Verbindung mit lokalen OData-Dienstendpunkten.</span><span class="sxs-lookup"><span data-stu-id="41323-139">The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="41323-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="41323-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="41323-141">In SharePoint Online können Benutzer Lese-und Schreibvorgänge für ein lokales SAP-System ausführen.</span><span class="sxs-lookup"><span data-stu-id="41323-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="41323-142">Azure</span><span class="sxs-lookup"><span data-stu-id="41323-142">Azure</span></span>

<span data-ttu-id="41323-143">Nutzen Sie die Cloud, und behalten Sie die vollständige Kontrolle über die Plattform und die Funktionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="41323-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="41323-144">Das begleitende Diagramm zeigt Azure, die zwei Cloud-Dienste, eine SharePoint 2013 Farm und Windows Server-Active Directory mit DNS-Verbindung mit Benutzern über das Internet oder eine Verbindung zu lokalen Active Directory über VPN-Tunnel enthält.</span><span class="sxs-lookup"><span data-stu-id="41323-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="41323-145">Zu den Features gehören:</span><span class="sxs-lookup"><span data-stu-id="41323-145">Features include:</span></span> 
  
-  <span data-ttu-id="41323-146">Azure ist eine Plattform, die die Infrastruktur und die APP-Dienste bereitstellt, die zum Hosten einer SharePoint 2013 Farm erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="41323-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="41323-147">Infrastrukturdienste.</span><span class="sxs-lookup"><span data-stu-id="41323-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="41323-148">Beste Native Cloud-Plattform für SQL Server und SharePoint.</span><span class="sxs-lookup"><span data-stu-id="41323-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="41323-149">Computing-Ressourcen stehen fast sofort ohne Verpflichtung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="41323-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="41323-150">Konzentrieren Sie sich auf Anwendungen anstelle von Rechenzentren und Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="41323-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="41323-151">Günstige Entwicklungs-und Testumgebungen.</span><span class="sxs-lookup"><span data-stu-id="41323-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="41323-152">Auf SharePoint-Lösungen kann über das Internet zugegriffen werden oder nur über eine Unternehmensumgebung über einen Standort-zu-Standort-VPN-Tunnel zugänglich sein.</span><span class="sxs-lookup"><span data-stu-id="41323-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="41323-153">Anpassungen sind nicht limitiert.</span><span class="sxs-lookup"><span data-stu-id="41323-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="41323-154">Lokal</span><span class="sxs-lookup"><span data-stu-id="41323-154">On premises</span></span>

<span data-ttu-id="41323-155">Sie besitzen alles.</span><span class="sxs-lookup"><span data-stu-id="41323-155">You own everything.</span></span> 
  
<span data-ttu-id="41323-156">Das begleitende Diagramm zeigt eine lokale Umgebung mit Webservern, Anwendungsservern und Active Directory, die mit allen Datenbanken und dedizierten Anwendungsservern für die Suche kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="41323-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="41323-157">Zu den Features gehören:</span><span class="sxs-lookup"><span data-stu-id="41323-157">Features include:</span></span> 
  
- <span data-ttu-id="41323-158">Planung und Festlegung des Umfangs der Kapazität.</span><span class="sxs-lookup"><span data-stu-id="41323-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="41323-159">Serverbeschaffung und -einrichtung</span><span class="sxs-lookup"><span data-stu-id="41323-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="41323-160">Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="41323-160">Deployment.</span></span> 
    
- <span data-ttu-id="41323-161">Horizontale Skalierung, Patching und Betrieb</span><span class="sxs-lookup"><span data-stu-id="41323-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="41323-162">Sichern von Daten</span><span class="sxs-lookup"><span data-stu-id="41323-162">Backing up data.</span></span> 
    
- <span data-ttu-id="41323-163">Verwalten einer Notfallwiederherstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="41323-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="41323-164">Anpassungen sind nicht limitiert.</span><span class="sxs-lookup"><span data-stu-id="41323-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="41323-165">Der Bereitstellungs eignet sich am besten für.</span><span class="sxs-lookup"><span data-stu-id="41323-165">Deployment type is best for .</span></span> <span data-ttu-id="41323-166">.</span><span class="sxs-lookup"><span data-stu-id="41323-166">.</span></span> <span data-ttu-id="41323-167">.</span><span class="sxs-lookup"><span data-stu-id="41323-167">.</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="41323-168">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="41323-169">Sichere externe Freigabe und Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="41323-169">Secure external sharing and collaboration.</span></span> <span data-ttu-id="41323-170">(Einzigartiges Feature!)</span><span class="sxs-lookup"><span data-stu-id="41323-170">(Unique feature!)</span></span> 
    
- <span data-ttu-id="41323-171">Intranet – Team Websites, meine Websites und interne Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="41323-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="41323-172">Dokumentieren Sie Speicherung und Versionsverwaltung in der Cloud.</span><span class="sxs-lookup"><span data-stu-id="41323-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="41323-173">Grundlegende Website mit öffentlichem Standard.</span><span class="sxs-lookup"><span data-stu-id="41323-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="41323-174">Zusätzliche Features mit Office 365 dedizierten Abonnement Plänen:</span><span class="sxs-lookup"><span data-stu-id="41323-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="41323-175">Microsoft-Rechenzentrumsgeräte, die für Ihre Organisation reserviert sind und nicht für eine andere Organisation freigegeben sind.</span><span class="sxs-lookup"><span data-stu-id="41323-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="41323-176">Jede Kundenumgebung befindet sich in einem physisch getrennten Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="41323-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="41323-177">Client Kommunikation über ein IPSec-gesichertes VPN oder eine private privat Verbindung im Kundenbesitz.</span><span class="sxs-lookup"><span data-stu-id="41323-177">Client communication across an IPSec-secured VPN or customer-owned private connection.</span></span> <span data-ttu-id="41323-178">Die zweistufige Authentifizierung ist optional.</span><span class="sxs-lookup"><span data-stu-id="41323-178">Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="41323-179">ITAR-Support Pläne.</span><span class="sxs-lookup"><span data-stu-id="41323-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="41323-180">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="41323-181">Verwenden Sie Office 365 für die externe Freigabe und Zusammenarbeit, anstatt eine Extranet-Umgebung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="41323-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="41323-182">Stellen Sie meine Websites (OneDrive für Unternehmen) in die Cloud ein, um Benutzern den Remotezugriff auf Ihre Dateien zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="41323-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="41323-183">Starten Sie neue Teamwebsites in Office 365.</span><span class="sxs-lookup"><span data-stu-id="41323-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="41323-184">Integrieren einer Office 365 Website in eine lokale BCS SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="41323-185">Azure</span><span class="sxs-lookup"><span data-stu-id="41323-185">Azure</span></span>

- <span data-ttu-id="41323-186">SharePoint für Internet Websites – öffentliche gegenüberliegende Websites.</span><span class="sxs-lookup"><span data-stu-id="41323-186">SharePoint for Internet Sites — Public facing sites.</span></span> <span data-ttu-id="41323-187">Nutzen Sie Azure AD für Kundenkonten und-Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="41323-187">Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="41323-188">Entwickler-, Test-und Staging-Umgebungen – schnelles Bereitstellen und Aufheben der Bereitstellung ganzer Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="41323-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="41323-189">Hybrid Anwendungen – Anwendungen, die sich auf Ihr Rechenzentrum und die Cloud erstrecken.</span><span class="sxs-lookup"><span data-stu-id="41323-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="41323-190">Notfallwiederherstellungsumgebung – schnelle Wiederherstellung nach einem Notfall.</span><span class="sxs-lookup"><span data-stu-id="41323-190">Disaster recovery environment — Quickly recover from a disaster.</span></span> <span data-ttu-id="41323-191">Zahlen Sie nur für die Verwendung.</span><span class="sxs-lookup"><span data-stu-id="41323-191">Pay only for use.</span></span> 
    
- <span data-ttu-id="41323-192">Farmen, die eine umfassende Berichterstellung oder Überwachung erfordern.</span><span class="sxs-lookup"><span data-stu-id="41323-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="41323-193">Webanalyse.</span><span class="sxs-lookup"><span data-stu-id="41323-193">Web analytics.</span></span> 
    
- <span data-ttu-id="41323-194">Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt).</span><span class="sxs-lookup"><span data-stu-id="41323-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="41323-195">Datenverschlüsselung im Ruhezustand (Daten werden in den SQL-Datenbanken verschlüsselt)</span><span class="sxs-lookup"><span data-stu-id="41323-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="41323-196">In-Country-Farmen (wenn sich Daten innerhalb eines Gerichtsstands befinden müssen).</span><span class="sxs-lookup"><span data-stu-id="41323-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="41323-197">Komplexe BI-Lösungen, die sich in der Nähe von BI-Daten befinden müssen.</span><span class="sxs-lookup"><span data-stu-id="41323-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="41323-198">Private Cloudlösungen.</span><span class="sxs-lookup"><span data-stu-id="41323-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="41323-199">Hoch angepasste Lösungen.</span><span class="sxs-lookup"><span data-stu-id="41323-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="41323-200">Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die in Azure-Infrastrukturdiensten nicht unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="41323-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="41323-201">Datenschutz Einschränkungen, die die Synchronisierung von Active Directory Konten mit Azure Active Directory verhindern (Voraussetzung für Office 365).</span><span class="sxs-lookup"><span data-stu-id="41323-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="41323-202">Organisationen, die die Steuerung der gesamten Plattform und Lösung bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="41323-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="41323-203">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="41323-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="41323-204">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="41323-205">Abonnementmodell</span><span class="sxs-lookup"><span data-stu-id="41323-205">Subscription model.</span></span> <span data-ttu-id="41323-206">Keine zusätzlichen Lizenzen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="41323-206">No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="41323-207">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="41323-p108">Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig.</span><span class="sxs-lookup"><span data-stu-id="41323-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="41323-210">Lokal – Alle lokalen Lizenzen sind gültig.</span><span class="sxs-lookup"><span data-stu-id="41323-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="41323-211">Azure</span><span class="sxs-lookup"><span data-stu-id="41323-211">Azure</span></span>

-  <span data-ttu-id="41323-212">Azure-Abonnement (enthält das Server Betriebssystem)</span><span class="sxs-lookup"><span data-stu-id="41323-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="41323-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="41323-213">SQL Server</span></span> 
    
- <span data-ttu-id="41323-214">SharePoint 2013 Server Lizenz</span><span class="sxs-lookup"><span data-stu-id="41323-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="41323-215">SharePoint 2013 Client Zugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="41323-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="41323-216">Lokal</span><span class="sxs-lookup"><span data-stu-id="41323-216">On premises</span></span>

- <span data-ttu-id="41323-217">Server-Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="41323-217">Server operating system</span></span> 
    
- <span data-ttu-id="41323-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="41323-218">SQL Server</span></span> 
    
- <span data-ttu-id="41323-219">SharePoint 2013 Server Lizenz</span><span class="sxs-lookup"><span data-stu-id="41323-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="41323-220">SharePoint 2013 Client Zugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="41323-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="41323-221">Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="41323-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="41323-222">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="41323-223">Planen und Entwerfen der Verzeichnisintegration.</span><span class="sxs-lookup"><span data-stu-id="41323-223">Plan and design directory integration.</span></span> <span data-ttu-id="41323-224">Zwei Optionen.</span><span class="sxs-lookup"><span data-stu-id="41323-224">Two options.</span></span> <span data-ttu-id="41323-225">Beide Optionen können lokal oder in Azure bereitgestellt werden: Kennwortsynchronisierung (erfordert 1 64-Bit-Server).</span><span class="sxs-lookup"><span data-stu-id="41323-225">Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server).</span></span> <span data-ttu-id="41323-226">SSO (erfordert AD FS und mehrere Server).</span><span class="sxs-lookup"><span data-stu-id="41323-226">SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="41323-227">Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="41323-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="41323-228">Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote.</span><span class="sxs-lookup"><span data-stu-id="41323-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="41323-229">Planen Sie den Mandantennamen, und entwerfen Sie die Architektur der Websitesammlung und die Steuerung.</span><span class="sxs-lookup"><span data-stu-id="41323-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="41323-230">Planen von Anpassungen, Lösungen und Apps für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="41323-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="41323-231">Entscheiden Sie, ob Sie über das Internet Protocol 6 (IPv6) eine Verbindung mit Office 365 herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="41323-231">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6).</span></span> <span data-ttu-id="41323-232">Dies ist jedoch nicht die Regel.</span><span class="sxs-lookup"><span data-stu-id="41323-232">This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="41323-233">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-233">Hybrid with Office 365</span></span>

<span data-ttu-id="41323-234">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="41323-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="41323-235">Bestimmen Sie, wie viel Funktionsintegration Sie wünschen, und wählen Sie die Hybrid Topologie aus.</span><span class="sxs-lookup"><span data-stu-id="41323-235">Determine how much feature integration you want and choose the hybrid topology.</span></span> <span data-ttu-id="41323-236">Siehe dieses Modell Poster: welche Hybrid Topologie sollte ich verwenden?</span><span class="sxs-lookup"><span data-stu-id="41323-236">See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="41323-237">Ermitteln Sie bei Bedarf, welches Proxy Server Gerät verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="41323-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="41323-238">Azure</span><span class="sxs-lookup"><span data-stu-id="41323-238">Azure</span></span>

<span data-ttu-id="41323-239">Entwerfen der Azure-Netzwerkumgebung:</span><span class="sxs-lookup"><span data-stu-id="41323-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="41323-240">Virtuelles Netzwerk in Azure, einschließlich Subnetze.</span><span class="sxs-lookup"><span data-stu-id="41323-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="41323-241">Domänenumgebung und Integration in lokale Server.</span><span class="sxs-lookup"><span data-stu-id="41323-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="41323-242">IP-Adressen und DNS.</span><span class="sxs-lookup"><span data-stu-id="41323-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="41323-243">Affinitätsgruppen und Speicherkonten.</span><span class="sxs-lookup"><span data-stu-id="41323-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="41323-244">Entwerfen der SharePoint-Umgebung in Azure:</span><span class="sxs-lookup"><span data-stu-id="41323-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="41323-245">SharePoint-Farmtopologie und logische Architektur.</span><span class="sxs-lookup"><span data-stu-id="41323-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="41323-246">Azure-Verfügbarkeits Sätze und Aktualisieren von Domänen.</span><span class="sxs-lookup"><span data-stu-id="41323-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="41323-247">Größen für virtuelle Computer.</span><span class="sxs-lookup"><span data-stu-id="41323-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="41323-248">Lastenausgleich-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="41323-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="41323-249">Externe Endpunkte für den öffentlichen Zugriff, falls dies vorzuziehen ist.</span><span class="sxs-lookup"><span data-stu-id="41323-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="41323-250">Notfallwiederherstellungsumgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="41323-251">Lokal</span><span class="sxs-lookup"><span data-stu-id="41323-251">On premises</span></span>

<span data-ttu-id="41323-252">Entwerfen der SharePoint-Umgebung in einer vorhandenen lokalen Umgebung:</span><span class="sxs-lookup"><span data-stu-id="41323-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="41323-253">SharePoint-Farmtopologie und logische Architektur.</span><span class="sxs-lookup"><span data-stu-id="41323-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="41323-254">Server Hardware.</span><span class="sxs-lookup"><span data-stu-id="41323-254">Server hardware.</span></span> 
    
- <span data-ttu-id="41323-255">Virtuelle Umgebung (sofern verwendet).</span><span class="sxs-lookup"><span data-stu-id="41323-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="41323-256">Lastenausgleich.</span><span class="sxs-lookup"><span data-stu-id="41323-256">Load balancing.</span></span> 
    
- <span data-ttu-id="41323-257">Integration in AD DS und DNS.</span><span class="sxs-lookup"><span data-stu-id="41323-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="41323-258">Notfallwiederherstellungsumgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="41323-259">Verantwortlichkeiten für IT-Experten</span><span class="sxs-lookup"><span data-stu-id="41323-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="41323-260">SharePoint 2013 in Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="41323-261">Stellen Sie sicher, dass Benutzerarbeitsstationen Office 365 Client Voraussetzungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="41323-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="41323-262">Implementieren Sie den Verzeichnis Integrationsplan.</span><span class="sxs-lookup"><span data-stu-id="41323-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="41323-263">Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.</span><span class="sxs-lookup"><span data-stu-id="41323-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="41323-264">Konfigurieren Sie den Proxy oder die Firewall für Office 365 IP-Adressen-und URL-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="41323-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="41323-265">Erstellen Sie Berechtigungen für Websitesammlungen, und weisen Sie diese zu.</span><span class="sxs-lookup"><span data-stu-id="41323-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="41323-266">Implementieren von Anpassungen, Lösungen und Apps für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="41323-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="41323-267">Überwachen der Netzwerkverfügbarkeit und Identifizieren möglicher Engpässe</span><span class="sxs-lookup"><span data-stu-id="41323-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="41323-268">Hybrid mit Office 365</span><span class="sxs-lookup"><span data-stu-id="41323-268">Hybrid with Office 365</span></span>

<span data-ttu-id="41323-269">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="41323-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="41323-270">Konfigurieren Sie, sofern erforderlich, das Proxyservergerät.</span><span class="sxs-lookup"><span data-stu-id="41323-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="41323-271">Konfigurieren der Hybriden Identitäts Verwaltungsinfrastruktur: SSO und Server-zu-Server-Authentifizierung zwischen den beiden Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="41323-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="41323-272">Konfigurieren Sie die Integration ausgewählter Features: Search, BCS, Duet Enterprise online.</span><span class="sxs-lookup"><span data-stu-id="41323-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="41323-273">Azure</span><span class="sxs-lookup"><span data-stu-id="41323-273">Azure</span></span>

<span data-ttu-id="41323-274">Bereitstellen und Verwalten der Azure-und SharePoint-Umgebung:</span><span class="sxs-lookup"><span data-stu-id="41323-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="41323-275">Implementieren und Verwalten der Azure-Netzwerkumgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="41323-276">Stellen Sie die SharePoint-Umgebung bereit.</span><span class="sxs-lookup"><span data-stu-id="41323-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="41323-277">Aktualisieren von SharePoint-Farmservern</span><span class="sxs-lookup"><span data-stu-id="41323-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="41323-278">Hinzufügen oder Herunterfahren virtueller Computer bei Bedarf basierend auf der Farm Nutzung.</span><span class="sxs-lookup"><span data-stu-id="41323-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="41323-279">Erweitern oder verringern der Größe virtueller Computer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="41323-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="41323-280">Sichern Sie die SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="41323-281">Implementieren der Notfallwiederherstellungsumgebung und des Protokolls.</span><span class="sxs-lookup"><span data-stu-id="41323-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="41323-282">Lokal</span><span class="sxs-lookup"><span data-stu-id="41323-282">On premises</span></span>

<span data-ttu-id="41323-283">Bereitstellen und Verwalten der SharePoint-Umgebung in lokalen Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="41323-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="41323-284">Bereitstellungsserver.</span><span class="sxs-lookup"><span data-stu-id="41323-284">Provision servers.</span></span> 
    
- <span data-ttu-id="41323-285">Stellen Sie die SharePoint-Umgebung bereit.</span><span class="sxs-lookup"><span data-stu-id="41323-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="41323-286">Aktualisieren von SharePoint-Farmservern</span><span class="sxs-lookup"><span data-stu-id="41323-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="41323-287">Hinzufügen oder Entfernen von Farmservern bei Bedarf basierend auf der Farm Nutzung.</span><span class="sxs-lookup"><span data-stu-id="41323-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="41323-288">Sichern Sie die SharePoint-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="41323-289">Implementieren der Notfallwiederherstellungsumgebung und des Protokolls.</span><span class="sxs-lookup"><span data-stu-id="41323-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="41323-290">Drei typische Arbeitsauslastungen für die Umstellung auf Azure</span><span class="sxs-lookup"><span data-stu-id="41323-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="41323-291">Office 365 plus Verzeichniskomponenten in Azure</span><span class="sxs-lookup"><span data-stu-id="41323-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="41323-292">Die Bereitstellung Office 365 Verzeichnis Integrationskomponenten in Azure ist schneller, da virtuelle Computer bei Bedarf bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="41323-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="41323-293">Nur Verzeichnissynchronisierungsserver</span><span class="sxs-lookup"><span data-stu-id="41323-293">Directory synchronization server only</span></span>

<span data-ttu-id="41323-294">Anstatt den 64-Bit-Verzeichnissynchronisierungsserver in Ihrer lokalen Umgebung bereitzustellen, müssen Sie stattdessen einen virtuellen Computer in Azure bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="41323-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="41323-295">Das zugehörige Diagramm zeigt SharePoint Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory Umgebung und dem Azure Active Directory-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="41323-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="41323-296">Verzeichnissynchronisierung Plus AD FS</span><span class="sxs-lookup"><span data-stu-id="41323-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="41323-297">Dank dieser Option können Sie Office 365-Verbundidentitäten unterstützten, ohne Ihrer lokalen Infrastruktur weitere Hardware hinzufügen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="41323-297">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="41323-298">Bietet außerdem Ausfallsicherheit, wenn die lokale Active Directory-Umgebung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="41323-298">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="41323-299">Verzeichnis Integrationskomponenten befinden sich in Azure.</span><span class="sxs-lookup"><span data-stu-id="41323-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="41323-300">AD FS wird im Internet über AD FS-Proxys in Azure veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="41323-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="41323-301">Der Client Authentifizierungsdatenverkehr wird für Benutzer, die von einem beliebigen Standort aus eine Verbindung herstellen, von AD FS-Servern und Proxys verarbeitet, die in Azure bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="41323-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="41323-302">Öffentliche Internet Website und Azure AD für die Kundenauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="41323-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="41323-303">Nutzen Sie die Möglichkeit, die Anforderungen einfach zu skalieren, indem Sie Ihre Internet Website in Azure platzieren.</span><span class="sxs-lookup"><span data-stu-id="41323-303">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure.</span></span> <span data-ttu-id="41323-304">Verwenden Sie Azure AD zum Speichern von Kundenkonten.</span><span class="sxs-lookup"><span data-stu-id="41323-304">Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="41323-305">Azure-Vorteile für Internet Websites</span><span class="sxs-lookup"><span data-stu-id="41323-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="41323-306">Zahlen Sie nur für die Ressourcen, die Sie benötigen, indem Sie die Anzahl der virtuellen Computer basierend auf der Farm Nutzung skalieren.</span><span class="sxs-lookup"><span data-stu-id="41323-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="41323-307">Fügen Sie Deep Reporting und Webanalyse hinzu.</span><span class="sxs-lookup"><span data-stu-id="41323-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="41323-308">Konzentrieren Sie sich auf die Entwicklung einer großartigen Website statt auf die Erstellung von Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="41323-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="41323-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="41323-309">Azure AD</span></span>

<span data-ttu-id="41323-310">Azure AD bietet Identitätsverwaltungs- und Zugriffssteuerungsfunktionen für Clouddienste.</span><span class="sxs-lookup"><span data-stu-id="41323-310">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="41323-311">Zu den Funktionen zählen ein cloudbasierter Speicher für Verzeichnisdaten und eine Kerngruppe von Identitätsdiensten, einschließlich Anmeldungsprozessen, Authentifizierungsdiensten und AD FS.</span><span class="sxs-lookup"><span data-stu-id="41323-311">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="41323-312">Die in Azure Ad enthaltenen Identitätsdienste können problemlos in Ihre lokalen Active Directory-Bereitstellungen integriert werden und Drittanbieter-Identitätsanbieter vollständig unterstützen.</span><span class="sxs-lookup"><span data-stu-id="41323-312">The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="41323-313">Das begleitende Diagramm zeigt die Konfiguration von Zonen und Authentifizierung, die für mit dem Internet verbundene Standorte wichtig ist.</span><span class="sxs-lookup"><span data-stu-id="41323-313">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites.</span></span> <span data-ttu-id="41323-314">Das Diagramm zeigt den Azure Active Directory-Mandanten, der eine SharePoint-Farm in Azure mit zwei Zonen enthält:</span><span class="sxs-lookup"><span data-stu-id="41323-314">The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="41323-315">Eine Internet Zone, die mit anonymen und authentifizierten Besuchern und Kunden außerhalb des Netzwerks interagiert</span><span class="sxs-lookup"><span data-stu-id="41323-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="41323-316">Eine Standardzone, die NTLM für die Durchforstung und Windows-Authentifizierung enthält, die mit Ihrer lokalen Active Directory-Bereitstellung über einen VPN-Tunnel interagiert.</span><span class="sxs-lookup"><span data-stu-id="41323-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="41323-317">Lokale Farm und Notfallwiederherstellung in Azure</span><span class="sxs-lookup"><span data-stu-id="41323-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="41323-318">Wählen Sie eine Notfall Wiederherstellungsoption, die Ihren geschäftlichen Anforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="41323-318">Choose a disaster recovery option that matches your business requirements.</span></span> <span data-ttu-id="41323-319">Azure bietet Einstiegs Optionen für Unternehmen, die erste Schritte mit der Notfallwiederherstellung und erweiterte Optionen für Unternehmen mit hohen Ausfall Sicherheitsanforderungen.</span><span class="sxs-lookup"><span data-stu-id="41323-319">Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="41323-320">Kalt-Standby</span><span class="sxs-lookup"><span data-stu-id="41323-320">Cold standby</span></span>

- <span data-ttu-id="41323-321">Die Farm ist vollständig erstellt, aber die virtuellen Computer sind nicht in Betrieb.</span><span class="sxs-lookup"><span data-stu-id="41323-321">The farm is fully built, but the virtual machines are stopped.</span></span> <span data-ttu-id="41323-322">(Sie zahlen nur, wenn Sie in Betrieb sind!)</span><span class="sxs-lookup"><span data-stu-id="41323-322">(You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="41323-323">Das aufrecht erhalten der Umgebung umfasst das Starten der virtuellen Computer von Zeit zu Zeit, das Patchen, aktualisieren und Überprüfen der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="41323-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="41323-324">Starten Sie die vollständige Umgebung bei einem Notfall.</span><span class="sxs-lookup"><span data-stu-id="41323-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="41323-325">Warm-Standby</span><span class="sxs-lookup"><span data-stu-id="41323-325">Warm standby</span></span>

- <span data-ttu-id="41323-326">Dies umfasst eine kleine Farm, die bereitgestellt wird und aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="41323-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="41323-327">Die Farm kann Benutzern unmittelbar im Fall eines Failovers zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="41323-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="41323-328">Schnelles Skalieren der Farm, um die gesamte Benutzerbasis zu bedienen</span><span class="sxs-lookup"><span data-stu-id="41323-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="41323-329">Hot Standby</span><span class="sxs-lookup"><span data-stu-id="41323-329">Hot standby</span></span>

<span data-ttu-id="41323-330">Eine vollständige Farm wird bereitgestellt und wird im Standbymodus gestartet.</span><span class="sxs-lookup"><span data-stu-id="41323-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="41323-331">Das begleitende Diagramm zeigt eine lokale Farm, die mit der SharePoint-Notfallwiederherstellungsumgebung in Azure interagiert.</span><span class="sxs-lookup"><span data-stu-id="41323-331">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure.</span></span> <span data-ttu-id="41323-332">Die lokalen Datenbanken verwenden SQL Server Protokollversand über den VPN-Tunnel für den Zugriff auf die SharePoint-Notfallwiederherstellungsumgebung, die zwei SQL-Datenbankserver enthält, die die SharePoint-Datenbanken, zwei Front-End-Server und zwei SharePoint enthalten Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="41323-332">The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

