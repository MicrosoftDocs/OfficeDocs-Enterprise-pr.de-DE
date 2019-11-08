---
title: Verfügbares Diagramm - Microsoft Lync 2013-Plattformoptionen
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens „Microsoft Lync 2013-Plattformoptionen, das unter Technische Diagramme verfügbar ist.
ms.openlocfilehash: a62fb6d1e1ee7fbddb79b0aec4ddafea4b07b4fe
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030599"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="2f1fe-103">Verfügbares Diagramm – Microsoft Lync 2013-Plattformoptionen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="2f1fe-104">**Zusammenfassung:** Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens „Microsoft Lync 2013-Plattformoptionen", das unter [Technische Diagramme](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="2f1fe-105">Dieses Poster beschreibt, was Unternehmensentscheidungsträger (Business Decision Makers, BDMs) und -architekten über Lync Online- (Office 365) und Lync Server-Bereitstellungen wissen müssen. Es umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="2f1fe-106">Einen Vergleich von vier verschiedenen Bereitstellungsoptionen: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server und vom Anbieter gehostetes Lync Server.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="2f1fe-107">Zwei Beispielszenarien für die Bereitstellung von Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="2f1fe-108">Vergleich von vier verschiedenen Bereitstellungen für die Lync 2013-Plattform</span><span class="sxs-lookup"><span data-stu-id="2f1fe-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="2f1fe-109">Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="2f1fe-110">Übersicht der verschiedenen Bereitstellungsfeatures</span><span class="sxs-lookup"><span data-stu-id="2f1fe-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="2f1fe-111">Vorteile des Implementierens der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="2f1fe-112">Lizenzierungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-112">Licensing requirements</span></span>
    
- <span data-ttu-id="2f1fe-113">Erforderliche Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="2f1fe-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="2f1fe-114">Verantwortlichkeiten der IT-Experten für das Implementieren der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="2f1fe-115">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2f1fe-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="2f1fe-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="2f1fe-117">Effizienzsteigerung und Kostenoptimierung mit Office 365-Plänen für mehrere Mandanten.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="2f1fe-118">Das begleitende Diagramm zeigt Lync Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen AD DS-Umgebung (Active Directory-Domänendienste) und dem Azure Active Directory-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="2f1fe-119">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="2f1fe-120">Software as a Service (SaaS).</span><span class="sxs-lookup"><span data-stu-id="2f1fe-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="2f1fe-121">Die umfangreiche Funktionspalette ist stets auf dem neuesten Stand.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="2f1fe-122">Umfasst einen Azure Active Directory-Mandanten für Onlinekonten, der mit anderen Anwendungen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="2f1fe-123">Die Verzeichnissynchronisierung schließt die Synchronisierung von Kontonamen und Kennwörtern zwischen der lokalen AD DS-Umgebung (Active Directory-Domänendienste) und dem Azure Active Directory-Mandanten ein.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="2f1fe-124">Falls einmaliges Anmelden (SSO) eine Anforderung ist, müssen Active Directory-Verbunddienste (AD FS) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="2f1fe-125">Clientkommunikation über das Internet ist verschlüsselt und authentifiziert.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="2f1fe-126">Herkömmliche Telefonausrüstung, Telefonfestnetzanbindung (Public Switched Telephone Network, PSTN) und Konnektivität ist über Drittanbieter verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="2f1fe-127">Lync Online/Server Hybrid (geteilte Domäne)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="2f1fe-128">Sie können die Vorteile von Office 365 mit einer lokalen Bereitstellung von Lync 2013 verbinden.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="2f1fe-p101">Das zugehörige Diagramm zeigt Office 365 mit Lync Online, wobei einige Benutzer lokal und einige Benutzer online arbeiten. Ein lokal bereitgestellter Edge-Server wird ebenfalls dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="2f1fe-131">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="2f1fe-132">Einige Benutzer arbeiten lokal und einige arbeiten online, sie nutzen jedoch die gleiche SIP-Domäne (z. B. contoso.com).</span><span class="sxs-lookup"><span data-stu-id="2f1fe-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="2f1fe-133">Nutzen der Vorteile der vorhandenen Lync Server 2013-Infrastruktur, einschließlich der Verbindungen mit PSTN.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="2f1fe-134">Einfaches Hinzufügen von neuen Lync Online-Benutzern, die keinen PSTN-Zugriff benötigen.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="2f1fe-135">Langsame Migration vom lokalen Lync zu Lync Online, ganz nach Ihrem Zeitplan.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="2f1fe-136">Integration in andere Office 365-Anwendungen, einschließlich Exchange Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="2f1fe-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-137">Lync Server</span></span>

<span data-ttu-id="2f1fe-p102">Bei dieser Bereitstellung sind Sie für alles zuständig. Das begleitende Diagramm zeigt eine Lync Server-Infrastruktur mit einer lokalen Active Directory-Domänendienste (AD DS)-Umgebung, in der Benutzer lokal arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="2f1fe-140">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="2f1fe-141">Planung und Festlegung des Umfangs der Kapazität.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="2f1fe-142">Serverbeschaffung und -einrichtung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="2f1fe-143">Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-143">Deployment.</span></span>
    
- <span data-ttu-id="2f1fe-144">Horizontale Skalierung, Patching und Betrieb</span><span class="sxs-lookup"><span data-stu-id="2f1fe-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="2f1fe-145">Sichern von Daten</span><span class="sxs-lookup"><span data-stu-id="2f1fe-145">Backing up data.</span></span>
    
- <span data-ttu-id="2f1fe-146">Verwalten von Failover und Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="2f1fe-147">Verbinden der Lync Server 2013-Infrastruktur mit PSTN</span><span class="sxs-lookup"><span data-stu-id="2f1fe-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="2f1fe-148">Integration mit vorhandener Telefonausrüstung, z. B. Private Branch Exchanges (PBXs)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="2f1fe-149">Vom Anbieter gehostetes Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="2f1fe-p103">Bei dieser Bereitstellung ist der Anbieter ist für alles zuständig. Das zugehörige Diagramm stellt das Netzwerk eines Anbieters dar, einschließlich der Server und Geräte mit einer Verbindung zur lokalen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="2f1fe-152">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="2f1fe-153">Planung und Festlegung des Umfangs der Kapazität.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="2f1fe-154">Serverbeschaffung und -einrichtung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="2f1fe-155">Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-155">Deployment.</span></span>
    
- <span data-ttu-id="2f1fe-156">Horizontale Skalierung, Patching und Betrieb</span><span class="sxs-lookup"><span data-stu-id="2f1fe-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="2f1fe-157">Sichern von Daten</span><span class="sxs-lookup"><span data-stu-id="2f1fe-157">Backing up data.</span></span>
    
- <span data-ttu-id="2f1fe-158">Verwalten von Failover und Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="2f1fe-159">Integration mit vorhandener Telefonausrüstung, z. B. Private Branch Exchanges (PBXs)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="2f1fe-160">Darüber hinaus kann der Anbieter:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="2f1fe-161">Server und Geräte im Netzwerk mit einer Verbindung zur lokalen Bereitstellung (durchgehende Linie) installieren,</span><span class="sxs-lookup"><span data-stu-id="2f1fe-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="2f1fe-162">Server auf Ihrer lokalen Bereitstellung (die gepunktete Linie) installieren.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="2f1fe-163">Vorteile des Implementierens der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="2f1fe-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="2f1fe-165">Keine betrieblichen Gemeinkosten für lokale Server oder Serversoftware</span><span class="sxs-lookup"><span data-stu-id="2f1fe-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="2f1fe-166">Kommunikationsfunktionen von Lync Server 2013 in einem cloudbasierten Dienst.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="2f1fe-167">Zugriff auf teilweise umfangreiche Funktionen im Zusammenhang mit Anwesenheit, Chats, Audio- und Videoanrufen, Onlinebesprechungen und Webkonferenzen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="2f1fe-168">Geografisch verteilte Organisationen oder Organisationen mit hauptsächlich mobilen Mitarbeitern</span><span class="sxs-lookup"><span data-stu-id="2f1fe-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="2f1fe-169">Lync Online/Server Hybrid (geteilte Domäne)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="2f1fe-170">Verwenden von Lync Online für Remotebenutzer und die Integration mit Geschäftspartnern</span><span class="sxs-lookup"><span data-stu-id="2f1fe-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="2f1fe-171">Durchführen einer Migration von Lync (lokal) zu Lync Online</span><span class="sxs-lookup"><span data-stu-id="2f1fe-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="2f1fe-172">Unterstützen von Remotestandorten ohne Verwendung eines Zweigstellengeräts</span><span class="sxs-lookup"><span data-stu-id="2f1fe-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="2f1fe-173">Einfaches Hinzufügen von Lync-Unterstützung für neue Geschäftskäufe</span><span class="sxs-lookup"><span data-stu-id="2f1fe-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="2f1fe-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-174">Lync Server</span></span>

- <span data-ttu-id="2f1fe-175">Private Cloudlösungen.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="2f1fe-176">Hoch angepasste Lösungen.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="2f1fe-177">Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Lync Online unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="2f1fe-178">Datenschutzeinschränkungen, die eine Synchronisierung von AD DS-Konten mit Office 365 verhindern</span><span class="sxs-lookup"><span data-stu-id="2f1fe-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="2f1fe-179">Organisationen, die sich Kontrolle über die gesamte Plattform und Lösung wünschen.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="2f1fe-180">Ersetzung der PBX-Anlage mit Lync Enterprise Voice</span><span class="sxs-lookup"><span data-stu-id="2f1fe-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="2f1fe-181">Vom Anbieter gehostetes Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="2f1fe-182">Organisationen, die Lync Server-Funktionen benötigen, die Bereitstellung und Wartung aber outsourcen möchten</span><span class="sxs-lookup"><span data-stu-id="2f1fe-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="2f1fe-183">Anbieter-basierten Lösungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="2f1fe-184">Hoch angepasste Lösungen.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="2f1fe-185">Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Lync Online unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="2f1fe-186">Ersetzung der PBX-Anlage mit Lync Enterprise Voice</span><span class="sxs-lookup"><span data-stu-id="2f1fe-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="2f1fe-187">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="2f1fe-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="2f1fe-189">Abonnementmodell</span><span class="sxs-lookup"><span data-stu-id="2f1fe-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="2f1fe-190">Lync Online/Server Hybrid (geteilte Domäne)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="2f1fe-p104">Office 365 - Abonnementmodell Keine weiteren Lizenzen nötig.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="2f1fe-193">Lokal – Alle lokalen Lizenzen sind gültig.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="2f1fe-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-194">Lync Server</span></span>

- <span data-ttu-id="2f1fe-195">Serverbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="2f1fe-195">Server Operating System</span></span>
    
- <span data-ttu-id="2f1fe-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-196">SQL Server</span></span>
    
- <span data-ttu-id="2f1fe-197">Lync Server 2013-Lizenz</span><span class="sxs-lookup"><span data-stu-id="2f1fe-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="2f1fe-198">Lync 2013-Clientzugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="2f1fe-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="2f1fe-199">Vom Anbieter gehostetes Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="2f1fe-200">Die Kosten basieren auf dem Vertrag mit dem Anbieter Ihrer Lync-Lösung.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="2f1fe-201">Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="2f1fe-201">Architecture tasks</span></span>

<span data-ttu-id="2f1fe-202">In diesem Abschnitt werden die Architekturaufgaben für die einzelnen Bereitstellungsoptionen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="2f1fe-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="2f1fe-204">Planen und Entwerfen der Verzeichnissynchronisierung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="2f1fe-205">Sicherstellen von Netzwerkkapazität und -verfügbarkeit durch Firewalls, Proxyserver, Gateways und über WAN-Verbindungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="2f1fe-206">Beziehen von SSL-Zertifikaten anderer Anbieter zum Ermöglichen einer unternehmensweiten Sicherheit für Office 365-Dienstangebote.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="2f1fe-207">Bestimmen Sie, ob Sie mit Office 365 eine Verbindung über IPv6 (Internet Protocol version 6) herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="2f1fe-208">Lync Online/Server Hybrid (geteilte Domäne)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="2f1fe-209">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="2f1fe-210">Bestimmen, wie viel Feature-Integration Sie mit lokalen und Onlineversionen von Exchange Server und SharePoint nutzen möchten.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="2f1fe-211">Bei Bedarf bestimmen, welches Proxyservergerät für Anforderungen von Office 365 verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="2f1fe-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-212">Lync Server</span></span>

<span data-ttu-id="2f1fe-213">Entwurf der Lync-Umgebung in einer vorhandenen lokalen Umgebung:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="2f1fe-214">Lync-Topologie für Haupt- und Zweigstellen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="2f1fe-215">Server-Hardware, einschließlich Virtualisierung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="2f1fe-216">Integration in Active Directory-Domänendienste (AD DS) und DNS</span><span class="sxs-lookup"><span data-stu-id="2f1fe-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="2f1fe-217">Lastenausgleich für Lync-Serverpools</span><span class="sxs-lookup"><span data-stu-id="2f1fe-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="2f1fe-218">Failover und Notfallwiederherstellung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="2f1fe-219">Vom Anbieter gehostetes Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="2f1fe-220">Bestimmen Sie für eine cloudbasierte Installation die Verbindung zum Netzwerk des Dienstanbieters.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="2f1fe-221">Bestimmen Sie für eine lokale Installation die Platzierung der Lync-Server des Anbieters in Ihrem Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="2f1fe-222">Bestimmen Sie für beide Typen die Integration in AD DS und mit Ihrer PBX-Ausrüstung.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="2f1fe-223">Verantwortlichkeiten von IT-Experten</span><span class="sxs-lookup"><span data-stu-id="2f1fe-223">IT Pro responsibilities</span></span>

<span data-ttu-id="2f1fe-224">In diesem Abschnitt werden die Verantwortlichkeiten der IT-Experten für die einzelnen Bereitstellungsoptionen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="2f1fe-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="2f1fe-226">Bereitstellen und Verwalten von Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="2f1fe-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="2f1fe-227">Implementieren des Verzeichnissynchronisierungsplans.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="2f1fe-228">Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="2f1fe-229">Konfigurieren des Proxys oder der Firewall für die IP-Adressen- und URL-Anforderungen von Office 365</span><span class="sxs-lookup"><span data-stu-id="2f1fe-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="2f1fe-230">Verwalten der Benutzerkonten und der Lync Online-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="2f1fe-231">Lync Online/Server Hybrid (geteilte Domäne)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="2f1fe-232">Zusätzlich zu Aufgaben für sowohl die Office 365- als auch lokale Umgebungen:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="2f1fe-233">Konfigurieren Sie, sofern erforderlich, das Proxyservergerät.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="2f1fe-234">Konfigurieren Sie die Integration von Features in lokalen und Onlineversionen von Exchange Server und SharePoint.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="2f1fe-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-235">Lync Server</span></span>

<span data-ttu-id="2f1fe-236">Bereitstellen und Verwalten von Lync Server in einer lokalen Umgebung:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="2f1fe-237">Bereitstellen der Server.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-237">Provision the servers.</span></span>
    
- <span data-ttu-id="2f1fe-238">Bereitstellen der Lync-Topologie.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="2f1fe-239">Aktualisieren der Lync-Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="2f1fe-240">Bedarfsabhängiges Hinzufügen oder Entfernen von Topologieservern anhand auf der Auslastung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="2f1fe-241">Implementieren der Failover- und Notfallwiederherstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="2f1fe-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="2f1fe-242">Vom Anbieter gehostetes Lync Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="2f1fe-243">Arbeiten Sie mit dem Anbieter an folgenden Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="2f1fe-244">Integration von Lync Server in Ihrem Netzwerk</span><span class="sxs-lookup"><span data-stu-id="2f1fe-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="2f1fe-245">Integration von Lync Server mit anderen Microsoft-Produkten und benutzerdefinierten Lösungen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="2f1fe-246">Überwachung der Einhaltung der Anbietervereinbarung zum Servicelevel (SLA)</span><span class="sxs-lookup"><span data-stu-id="2f1fe-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="2f1fe-247">Zwei Beispielszenarien für die Bereitstellung von Lync 2013</span><span class="sxs-lookup"><span data-stu-id="2f1fe-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="2f1fe-248">Komponenten der Verzeichnissynchronisierung in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2f1fe-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="2f1fe-249">Die Bereitstellung der Office 365-Verzeichnissynchronisierungskomponenten in Azure erfolgt schneller, da virtuelle Computer bedarfsabhängig bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="2f1fe-250">Das begleitende Diagramm zeigt Lync Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Umgebung und dem Azure Active Directory-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="2f1fe-p105">**Nur Verzeichnissynchronisierungsserver**. Anstatt in Ihrer lokalen Umgebung einen 64-Bit-Verzeichnissynchronisierungsserver bereitzustellen, richten Sie in Azure einen virtuellen Computer ein.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="2f1fe-p106">**Verzeichnissynchronisierung und AD FS**. Dank dieser Option können Sie Office 365-Verbundidentitäten unterstützten, ohne Ihrer lokalen Infrastruktur weitere Hardware hinzufügen zu müssen. Bietet außerdem Ausfallsicherheit, wenn die lokale Active Directory-Umgebung nicht verfügbar ist. Die Funktionen dieser Option umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="2f1fe-257">Verzeichnisintegrationskomponenten werden auf virtuellen Azure-Computern ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="2f1fe-258">AD FS wird im Internet über AD FS-Proxys auf virtuellen Azure-Computern veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="2f1fe-259">Datenverkehr für die Clientauthentifizierung durch Benutzer, die von einem beliebigen Standort aus eine Verbindung herstellen, wird von AD FS-Servern- und Proxys verarbeitet, die auf virtuellen Azure-Computern bereitgestellt sind.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="2f1fe-260">Lync-Integration mit Exchange und SharePoint in Office 365</span><span class="sxs-lookup"><span data-stu-id="2f1fe-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="2f1fe-261">Lync Server mit Exchange Online und SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2f1fe-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="2f1fe-262">Im zugehörigen Diagramm wird Office 365 mit Exchange Online und SharePoint Online mit einer Verbindung zu einer lokalen Lync Server 2013-Farm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="2f1fe-263">Die Vorteile dieser Bereitstellung umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="2f1fe-264">Nutzen des vollständigen Funktionssets von Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="2f1fe-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="2f1fe-265">Nutzen der vorhandenen lokalen Telefonausrüstung, z. B. PBXs.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="2f1fe-266">Verwenden von Exchange Online für E-Mails, Entlastung der lokalen E-Mail-Server und des lokalen Speichers</span><span class="sxs-lookup"><span data-stu-id="2f1fe-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="2f1fe-267">Verwenden von SharePoint Online für die Zusammenarbeit, geringerer Wartungsaufwand der lokalen SharePoint-Server</span><span class="sxs-lookup"><span data-stu-id="2f1fe-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="2f1fe-268">Verwenden von in Lync, Exchange und SharePoint integrierten Features wie Unified Messaging (UM) in Office 365</span><span class="sxs-lookup"><span data-stu-id="2f1fe-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="2f1fe-269">Exchange Server mit Lync Online</span><span class="sxs-lookup"><span data-stu-id="2f1fe-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="2f1fe-270">Im zugehörigen Diagramm wird Office 365 mit Lync Online mit einer Verbindung zu einer lokalen Exchange Server-Farm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2f1fe-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="2f1fe-271">Die Vorteile dieser Bereitstellung umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2f1fe-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="2f1fe-272">Nutzen der vorhandenen Exchange-Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="2f1fe-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="2f1fe-273">Verwenden von Lync Online für Anwesenheitsinformationen, Chats und Konferenzfunktionen</span><span class="sxs-lookup"><span data-stu-id="2f1fe-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

