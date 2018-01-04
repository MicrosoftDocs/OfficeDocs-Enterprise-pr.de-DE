---
title: "Verfügbares Diagramm - Microsoft Exchange 2013-Plattformoptionen"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namensMicrosoft Exchange 2013-Plattformoptionen, das unter Technische Diagramme verfügbar ist."
ms.openlocfilehash: d81fe9947feee64d1dd75278738262d10c802ecc
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="fefdb-103">Verfügbares Diagramm - Microsoft Exchange 2013-Plattformoptionen</span><span class="sxs-lookup"><span data-stu-id="fefdb-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="fefdb-104">**Zusammenfassung:** Dieser Artikel ist eine leicht zugängliche Textversion des Diagramms namens "Microsoft Exchange 2013-Plattformoptionen, das unter [Technische Diagramme](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="fefdb-104">This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="fefdb-105">Dieses Poster beschreibt, was Unternehmensentscheidungsträger (Business Decision Makers, BDMs) und -architekten über Exchange Online- und Exchange Server-Bereitstellungen wissen müssen. Es umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fefdb-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="fefdb-106">Vergleich von vier verfügbaren Plattformoptionen für Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server On-Premises und Provider-Hosted Exchange.</span><span class="sxs-lookup"><span data-stu-id="fefdb-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="fefdb-107">Beschreibungen von drei neuen oder aktualisierten Funktionen in Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="fefdb-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="fefdb-108">Vergleich von vier verschiedenen Bereitstellungen für die Exchange 2013-Plattform</span><span class="sxs-lookup"><span data-stu-id="fefdb-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="fefdb-109">Der Vergleich stellt Informationen zu den einzelnen Bereitstellungsoptionen in den folgenden Bereichen bereit:</span><span class="sxs-lookup"><span data-stu-id="fefdb-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="fefdb-110">Übersicht der verschiedenen Bereitstellungsfeatures</span><span class="sxs-lookup"><span data-stu-id="fefdb-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="fefdb-111">Vorteile des Implementierens der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="fefdb-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="fefdb-112">Lizenzierungsanforderungen</span><span class="sxs-lookup"><span data-stu-id="fefdb-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="fefdb-113">Erforderliche Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="fefdb-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="fefdb-114">Verantwortlichkeiten der IT-Experten für das Implementieren der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="fefdb-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="fefdb-115">Übersicht</span><span class="sxs-lookup"><span data-stu-id="fefdb-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="fefdb-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fefdb-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="fefdb-117">Sie gewinnen Effizienz und senken die Kosten mit Office 365.</span><span class="sxs-lookup"><span data-stu-id="fefdb-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="fefdb-p101">Das begleitende Diagramm zeigt Exchange Online mit einem Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Domänendienste (AD DS)-Umgebung und dem Azure Active Directory-Mandanten synchronisiert. Active Directory-Verbunddienste (AD FS) ist für einmaliges Anmelden (Single Sign-On) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="fefdb-120">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="fefdb-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fefdb-121">Der Betrieb von Servern und Serversoftware erfolgt durch Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fefdb-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="fefdb-122">Umfangreiche Funktionen von Exchange Server 2013 als cloudbasierter Dienst.</span><span class="sxs-lookup"><span data-stu-id="fefdb-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="fefdb-123">Immer aktuell mit den neuesten Features.</span><span class="sxs-lookup"><span data-stu-id="fefdb-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="fefdb-124">Exchange Online Protection (EOP) ist zum Schutz vor Spam/Malware enthalten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="fefdb-125">Integrierte hohe Verfügbarkeit mit 99,9 % Service Level Agreement (SLA).</span><span class="sxs-lookup"><span data-stu-id="fefdb-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="fefdb-p102">Verzeichnissynchronisierung einschließlich Kennwörter zwischen den lokalen Active Directory-Domänendienste (AD DS) und dem Azure Active Directory-Mandanten. Active Directory-Verbunddienste (AD FS) ist für einmalige Anmeldung (Single Sign-On) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="fefdb-128">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="fefdb-128">Exchange Hybrid</span></span>

<span data-ttu-id="fefdb-129">Sie können die Vorteile von Office 365 nutzen, während Sie Exchange Server lokal beibehalten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="fefdb-p103">Das begleitende Diagramm zeigt Office 365 mit Exchange Online. Einige Benutzer arbeiten lokal und einige arbeiten online. Außerdem zeigt es einen Azure Active Directory-Mandanten, der Kontonamen und Kennwörter zwischen der lokalen Active Directory-Domänendienste (AD DS)-Umgebung und dem Azure Active Directory-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="fefdb-132">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="fefdb-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fefdb-133">Einige Benutzer arbeiten lokal und einige arbeiten online. Außerdem nutzen die Benutzer gemeinsam den gleichen E-Mail-Adressbereich.</span><span class="sxs-lookup"><span data-stu-id="fefdb-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="fefdb-134">Nutzt Ihre vorhandene Exchange Server-Infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="fefdb-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="fefdb-135">Langsame Migration vom lokalen Exchange zu Exchange Online, ganz nach Ihrem Zeitplan.</span><span class="sxs-lookup"><span data-stu-id="fefdb-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="fefdb-136">Integration in andere Office 365-Anwendungen, einschließlich Lync Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="fefdb-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="fefdb-137">Exchange Server (lokal)</span><span class="sxs-lookup"><span data-stu-id="fefdb-137">Exchange Server on-premises</span></span>

<span data-ttu-id="fefdb-138">Sie können Ihre eigene Exchange Server 2013-Infrastruktur entwerfen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="fefdb-139">Das begleitende Diagramm zeigt eine Exchange Server-Infrastruktur mit einer lokalen Active Directory-Domänendienste (AD DS)-Umgebung, in der Benutzer lokal arbeiten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="fefdb-140">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="fefdb-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fefdb-141">Größtmögliche Kontrolle und Anpassung Ihrer Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fefdb-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="fefdb-142">Keine Abhängigkeit beim Beibehalten der Sitzungsaffinität auf der Lastenausgleichsebene.</span><span class="sxs-lookup"><span data-stu-id="fefdb-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="fefdb-143">Einfache hohe Verfügbarkeit und Websitezuverlässigkeit mit Datenbankverfügbarkeitsgruppen (Database Availability Groups, DAGs).</span><span class="sxs-lookup"><span data-stu-id="fefdb-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="fefdb-144">Verwaltete Verfügbarkeit, die es Ihnen ermöglicht, eine großartige Benutzererfahrung beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="fefdb-145">Nutzen der vorhandenen Hardware- und Speicherinfrastruktur.</span><span class="sxs-lookup"><span data-stu-id="fefdb-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="fefdb-146">Provider-Hosted Exchange</span><span class="sxs-lookup"><span data-stu-id="fefdb-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="fefdb-147">Sie können Ihre Exchange Server-Arbeitslast an einen Exchange Server-Lösungsanbieter outsourcen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="fefdb-148">Das begleitende Diagramm zeigt eine Exchange Server-Umgebung, die von einem Anbieter betrieben und verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="fefdb-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="fefdb-149">Beschreibung von Features und Funktionen:</span><span class="sxs-lookup"><span data-stu-id="fefdb-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="fefdb-150">Der Betrieb von Servern und Serversoftware erfolgt durch Ihren Anbieter.</span><span class="sxs-lookup"><span data-stu-id="fefdb-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="fefdb-151">Planung, Größenanpassung, Skalierung und Wartung der Exchange Server-Infrastruktur werden an Ihren Anbieter delegiert.</span><span class="sxs-lookup"><span data-stu-id="fefdb-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="fefdb-152">Dienstwartung erfolgt durch Ihren Anbieter.</span><span class="sxs-lookup"><span data-stu-id="fefdb-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="fefdb-153">Die Exchange-Funktionen sind auf die von Ihrem Anbieter bereitgestellte Softwareversion beschränkt.</span><span class="sxs-lookup"><span data-stu-id="fefdb-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="fefdb-154">Vorteile des Implementierens der einzelnen Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="fefdb-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="fefdb-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fefdb-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="fefdb-156">Diese Bereitstellungsoption eignet sich am besten für:</span><span class="sxs-lookup"><span data-stu-id="fefdb-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="fefdb-157">Organisationen, die Betriebskosten für lokale Exchange-Bereitstellungen senken möchten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="fefdb-158">Organisationen, die andere Office 365-Angebote nutzen möchten, zum Beispiel SharePoint Online und Lync Online.</span><span class="sxs-lookup"><span data-stu-id="fefdb-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="fefdb-159">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="fefdb-159">Exchange Hybrid</span></span>

<span data-ttu-id="fefdb-160">Diese Bereitstellungsoption eignet sich am besten für:</span><span class="sxs-lookup"><span data-stu-id="fefdb-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="fefdb-161">Durchführen einer Migration von Exchange (lokal) zu Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fefdb-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="fefdb-162">Unterstützen von Remotestandorten ohne Investitionen in eine Zweigstelleninfrastruktur.</span><span class="sxs-lookup"><span data-stu-id="fefdb-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="fefdb-163">Multinationale Unternehmen mit Filialen, die Daten am Standort benötigen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="fefdb-164">Exchange Server (lokal)</span><span class="sxs-lookup"><span data-stu-id="fefdb-164">Exchange Server on-premises</span></span>

<span data-ttu-id="fefdb-165">Diese Bereitstellungsoption eignet sich am besten für:</span><span class="sxs-lookup"><span data-stu-id="fefdb-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="fefdb-166">Hoch angepasste Lösungen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="fefdb-167">Ältere Lösungen mit Drittanbieterkomponenten, die auf Hardware und Software angewiesen sind, die nicht von Exchange Online unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="fefdb-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="fefdb-168">Organisationen, die behördlichen Regelungen unterliegen, die lokale Daten benötigen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="fefdb-169">Organisationen, die die Kontrolle über die gesamte Plattform und Lösung behalten möchten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="fefdb-170">Provider-Hosted Exchange</span><span class="sxs-lookup"><span data-stu-id="fefdb-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="fefdb-171">Diese Bereitstellungsoption eignet sich am besten für:</span><span class="sxs-lookup"><span data-stu-id="fefdb-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="fefdb-172">Organisationen, die Exchange Server-Funktionen benötigen, die Bereitstellung und Wartung aber outsourcen möchten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="fefdb-173">Organisationen, die persönliche Supportoptionen benötigen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="fefdb-174">Angepasste Lösungen und Integration in benutzerdefinierte, vom Anbieter bereitgestellte Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="fefdb-175">Ältere Lösungen mit Drittanbieterkomponenten, die von Hardware und Software abhängen, die nicht von Exchange Online unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="fefdb-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="fefdb-176">Lizenzanforderungen</span><span class="sxs-lookup"><span data-stu-id="fefdb-176">License requirements</span></span>

<span data-ttu-id="fefdb-177">In der folgenden Tabelle werden die Lizenzanforderungen für die einzelnen Bereitstellungsoptionen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="fefdb-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="fefdb-178">**Bereitstellungsoption**</span><span class="sxs-lookup"><span data-stu-id="fefdb-178">**Deployment option**</span></span>|<span data-ttu-id="fefdb-179">**Lizenzanforderungen**</span><span class="sxs-lookup"><span data-stu-id="fefdb-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fefdb-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fefdb-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="fefdb-181">Abonnementmodell</span><span class="sxs-lookup"><span data-stu-id="fefdb-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="fefdb-182">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="fefdb-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="fefdb-183">Office 365 - Abonnementmodell</span><span class="sxs-lookup"><span data-stu-id="fefdb-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="fefdb-184">Lokal - es gelten alle lokalen Lizenzen (überprüfen Sie Lizenzen für Exchanges Server (lokal))</span><span class="sxs-lookup"><span data-stu-id="fefdb-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="fefdb-185">Hybrid-Serverlizenz*</span><span class="sxs-lookup"><span data-stu-id="fefdb-185">Hybrid server license*</span></span> <br/> |
|<span data-ttu-id="fefdb-186">Exchange Server (lokal)</span><span class="sxs-lookup"><span data-stu-id="fefdb-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="fefdb-187">Serverbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="fefdb-187">Server Operating System</span></span> <br/>  <span data-ttu-id="fefdb-188">Exchange 2013-Serverlizenz</span><span class="sxs-lookup"><span data-stu-id="fefdb-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="fefdb-189">Exchange 2013-Clientzugriffslizenz</span><span class="sxs-lookup"><span data-stu-id="fefdb-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="fefdb-190">Provider-Hosted Exchange</span><span class="sxs-lookup"><span data-stu-id="fefdb-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="fefdb-191">Kosten basieren auf der Vereinbarung mit dem Anbieter</span><span class="sxs-lookup"><span data-stu-id="fefdb-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="fefdb-192">Architekturaufgaben</span><span class="sxs-lookup"><span data-stu-id="fefdb-192">Architecture tasks</span></span>

<span data-ttu-id="fefdb-193">In diesem Abschnitt werden die Architekturaufgaben für die einzelnen Bereitstellungsoptionen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="fefdb-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="fefdb-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fefdb-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="fefdb-195">Planen und Entwerfen der Verzeichnissynchronisierung.</span><span class="sxs-lookup"><span data-stu-id="fefdb-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="fefdb-196">Sicherstellen der Netzwerkkapazität und -konnektivität über Firewalls, Proxyserver, Gateways und WAN-Links hinweg.</span><span class="sxs-lookup"><span data-stu-id="fefdb-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="fefdb-197">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="fefdb-197">Exchange Hybrid</span></span>

<span data-ttu-id="fefdb-198">Zusätzlich zu den Architekturaufgaben für die Office 365- und die lokale Umgebung:</span><span class="sxs-lookup"><span data-stu-id="fefdb-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="fefdb-199">Entscheiden, ob die einmalige Anmeldung (Single-Sign On) bereitgestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fefdb-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="fefdb-200">Entscheiden, ob eingehende Internet-E-Mails durch eine lokale Organisation oder durch Exchange Online Protection weitergeleitet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="fefdb-201">Exchange Server (lokal)</span><span class="sxs-lookup"><span data-stu-id="fefdb-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="fefdb-202">Entwerfen der Exchange-Topologie.</span><span class="sxs-lookup"><span data-stu-id="fefdb-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="fefdb-203">Planen der Kapazität für Serverhardware.</span><span class="sxs-lookup"><span data-stu-id="fefdb-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="fefdb-204">Entwerfen der Mitteilungsweiterleitungstopologie.</span><span class="sxs-lookup"><span data-stu-id="fefdb-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="fefdb-205">Entwerfen des Lastenausgleichs für Clientzugriffsserver.</span><span class="sxs-lookup"><span data-stu-id="fefdb-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="fefdb-206">Planen der hohen Verfügbarkeit mithilfe von Datenbankverfügbarkeitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="fefdb-207">Provider-Hosted Exchange</span><span class="sxs-lookup"><span data-stu-id="fefdb-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="fefdb-208">Sicherstellen, dass die Netzwerkkapazität und -verfügbarkeit über Firewalls, Proxyserver, Gateways und WAN-Links hinweg für Ihren Anbieter zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="fefdb-209">Verantwortlichkeiten von IT-Experten</span><span class="sxs-lookup"><span data-stu-id="fefdb-209">IT Pro responsibilities</span></span>

<span data-ttu-id="fefdb-210">In diesem Abschnitt werden die Verantwortlichkeiten der IT-Experten für die einzelnen Bereitstellungsoptionen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="fefdb-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="fefdb-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="fefdb-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="fefdb-212">Implementieren des Verzeichnissynchronisierungsplans.</span><span class="sxs-lookup"><span data-stu-id="fefdb-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="fefdb-213">Planen und Implementieren interner und externer DNS-Datensätze sowie des entsprechenden Routings.</span><span class="sxs-lookup"><span data-stu-id="fefdb-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="fefdb-214">Konfigurieren des Proxyservers oder der Firewall für die Office 365-IP-Adress- und -URL-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="fefdb-215">Verwalten der Benutzerkonten und der Exchange Online-Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="fefdb-216">Exchange Hybrid</span><span class="sxs-lookup"><span data-stu-id="fefdb-216">Exchange Hybrid</span></span>

<span data-ttu-id="fefdb-217">Zusätzlich zu den Verantwortlichkeiten der IT-Experten für die Office 365- und die lokale Umgebung:</span><span class="sxs-lookup"><span data-stu-id="fefdb-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="fefdb-218">Konfigurieren von Active Directory-Verbunddienste (AD FS) für die einmalige Anmeldung (Single-Sign On) (falls gewünscht).</span><span class="sxs-lookup"><span data-stu-id="fefdb-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="fefdb-219">Konfigurieren von Exchange-Zertifikaten für die sichere Kommunikation zwischen Exchange 2013-Servern und Office 365.</span><span class="sxs-lookup"><span data-stu-id="fefdb-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="fefdb-220">Konfigurieren von DNS-Datensätzen für den gewünschten Pfad für eingehende Internet-E-Mails.</span><span class="sxs-lookup"><span data-stu-id="fefdb-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="fefdb-221">Exchange Server (lokal)</span><span class="sxs-lookup"><span data-stu-id="fefdb-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="fefdb-222">Konfigurieren der erforderlichen Zertifikate für Exchange-Dienste.</span><span class="sxs-lookup"><span data-stu-id="fefdb-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="fefdb-223">Bereitstellen der Server.</span><span class="sxs-lookup"><span data-stu-id="fefdb-223">Provision the servers.</span></span>
    
- <span data-ttu-id="fefdb-224">Implementieren der Exchange-Nachrichtenroutingtopologie.</span><span class="sxs-lookup"><span data-stu-id="fefdb-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="fefdb-225">Implementieren von Datenbankverfügbarkeitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="fefdb-226">Aktualisieren und Warten von Exchange-Servern.</span><span class="sxs-lookup"><span data-stu-id="fefdb-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="fefdb-227">Je nach Nutzung ggf. Hinzufügen oder Entfernen von Servern.</span><span class="sxs-lookup"><span data-stu-id="fefdb-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="fefdb-228">Provider-Hosted Exchange</span><span class="sxs-lookup"><span data-stu-id="fefdb-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="fefdb-229">Zu den Verantwortlichkeiten des Anbieter gehören folgende:</span><span class="sxs-lookup"><span data-stu-id="fefdb-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="fefdb-230">System- und Dienstwartung.</span><span class="sxs-lookup"><span data-stu-id="fefdb-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="fefdb-231">Feature-Rollouts.</span><span class="sxs-lookup"><span data-stu-id="fefdb-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="fefdb-232">Datenschutz und Notfallwiederherstellung.</span><span class="sxs-lookup"><span data-stu-id="fefdb-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="fefdb-233">Die Verantwortlichkeiten der IT-Mitarbeiter Ihrer Organisation umfassen das Erstellen und Verwalten von Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="fefdb-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="fefdb-234">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fefdb-234">More information</span></span>

<span data-ttu-id="fefdb-235">Weitere Informationen zu Exchange Online (Office 365) finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fefdb-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- <span data-ttu-id="fefdb-236">[Exchange Online-Dienstbeschreibung](((https://aka.ms/EXO)SD))</span><span class="sxs-lookup"><span data-stu-id="fefdb-236">[Exchange Online service description](((https://aka.ms/EXO)SD))</span></span>
    
- <span data-ttu-id="fefdb-237">[Exchange Online-Bibliothek auf TechNet](((https://aka.ms/EXO)TN))</span><span class="sxs-lookup"><span data-stu-id="fefdb-237">[Exchange Online library on TechNet](((https://aka.ms/EXO)TN))</span></span>
    
- <span data-ttu-id="fefdb-238">[Exchange Online-Portal]((https://aka.ms/EXO))</span><span class="sxs-lookup"><span data-stu-id="fefdb-238">[Exchange Online portal]((https://aka.ms/EXO))</span></span>
    
<span data-ttu-id="fefdb-239">Weitere Informationen zu Exchange Hybrid finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fefdb-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="fefdb-p104">[Exchange 2013-Hybridbereitstellungen]((https://aka.ms/ExchangeHybrid)). Beachten Sie, dass die Hybrid-Serverlizenz nur für die folgenden Szenarios erforderlich ist: Exchange 2010-Organisation mit Exchange 2013-Hybridserver und Exchange 2007-Organisation mit Exchange 2013- oder Exchange 2010-Hybridserver.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p104">[Exchange 2013 hybrid deployments]((https://aka.ms/ExchangeHybrid)). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- <span data-ttu-id="fefdb-242">[Office 365-Anmeldung]((https://aka.ms/HybridKey))</span><span class="sxs-lookup"><span data-stu-id="fefdb-242">[Office 365 Sign in]((https://aka.ms/HybridKey))</span></span>
    
<span data-ttu-id="fefdb-243">Weitere Informationen zu Exchange Server (lokal) finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fefdb-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- <span data-ttu-id="fefdb-244">[Exchange Server 2013-Bibliothek auf TechNet]((https://aka.ms/Ex2013TN))</span><span class="sxs-lookup"><span data-stu-id="fefdb-244">[Exchange Server 2013 library on TechNet]((https://aka.ms/Ex2013TN))</span></span>
    
- <span data-ttu-id="fefdb-245">[Exchange Server 2013-Portal]((https://aka.ms/Exchange2013))</span><span class="sxs-lookup"><span data-stu-id="fefdb-245">[Exchange Server 2013 portal]((https://aka.ms/Exchange2013))</span></span>
    
- <span data-ttu-id="fefdb-246">[Exchange Server 2013-Architektur]((https://aka.ms/Ex2013SP1ArchPoster))</span><span class="sxs-lookup"><span data-stu-id="fefdb-246">[Exchange Server 2013 architecture]((https://aka.ms/Ex2013SP1ArchPoster))</span></span>
    
<span data-ttu-id="fefdb-247">Weitere Informationen zu Provider-Hosted Exchange finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fefdb-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
<span data-ttu-id="fefdb-248">[Exchange Server 2013-Hosting und Lösungen mit mehreren Mandanten sowie Anleitungen]((https://aka.ms/Ex2013Hosting))</span><span class="sxs-lookup"><span data-stu-id="fefdb-248">[Exchange Server 2013 hosting and multi-tenancy solutions and guidance]((https://aka.ms/Ex2013Hosting))</span></span>
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="fefdb-249">Beschreibung von drei neuen oder aktualisierten Features in Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="fefdb-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="fefdb-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="fefdb-250">Exchange Online Protection</span></span>

<span data-ttu-id="fefdb-p105">Exchange Online Protection (EOP) bietet Schutz vor Spam und Malware für jede Bereitstellung durch Schutzebenenfunktionen, die über ein globales Netzwerk mit Rechenzentren bereitgestellt wird. Auf diese Weise können Sie die Verwaltung Ihrer Messagingumgebungen vereinfachen. EOP ist in Exchange Online-Abonnements enthalten, Sie können EOP aber auch für Hybrid- und lokale Bereitstellungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="fefdb-254">Die begleitenden Diagramme zeigen Bereitstellungen für Exchange Online, Exchange Hybrid und Exchange (lokal), die die EOP-Schicht im globalen Netzwerk umfassen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="fefdb-255">Exchange Server-Bereitstellungs-Assistent</span><span class="sxs-lookup"><span data-stu-id="fefdb-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="fefdb-p106">Der Exchange Server-Bereitstellungs-Assistent ist ein webbasiertes Tool, das Ihnen einige Fragen zur aktuellen Umgebung stellt und dann eine benutzerdefinierte, schrittweise Checkliste generiert, mit der Sie Exchange Server für verschiedene Szenariotypen bereitstellen können. Der Exchange Server-Bereitstellungs-Assistent erstellt eine benutzerdefinierte Bereitstellungscheckliste für Ihr Szenario, egal, ob Sie von einer vorherigen Version von Exchange zu Exchange 2013 oder Exchange Online migrieren oder eine Hybridinfrastruktur planen.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="fefdb-258">Der begleitende Screenshot zeigt eine Beispielcheckliste, die mithilfe des Exchange Server-Bereitstellungs-Assistenten erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="fefdb-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="fefdb-259">Integration in Lync und SharePoint</span><span class="sxs-lookup"><span data-stu-id="fefdb-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="fefdb-p107">Exchange Server 2013 umfasst viele Features, die in Lync Server 2013 und SharePoint Server 2013 integriert werden. Zusammen bieten diese Produkte eine umfangreiche Suite mit Features und verbessern die Zusammenarbeit in der gesamten Organisation.</span><span class="sxs-lookup"><span data-stu-id="fefdb-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="fefdb-262">Ein begleitendes Diagramm zeigt das Server-zu-Server-Authentifizierungsposter und enthält einen Link zum Poster.</span><span class="sxs-lookup"><span data-stu-id="fefdb-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="fefdb-263">Archivierung, Beibehaltung und eDiscovery</span><span class="sxs-lookup"><span data-stu-id="fefdb-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="fefdb-264">Website-Postfächer</span><span class="sxs-lookup"><span data-stu-id="fefdb-264">Site mailboxes</span></span>
    
- <span data-ttu-id="fefdb-265">Einheitlicher Kontaktspeicher</span><span class="sxs-lookup"><span data-stu-id="fefdb-265">Unified contact store</span></span>
    
- <span data-ttu-id="fefdb-266">Hochauflösende Benutzerfotos</span><span class="sxs-lookup"><span data-stu-id="fefdb-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="fefdb-267">Lync-Präsenz in Outlook und Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="fefdb-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="fefdb-268">Server-zu-Server-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="fefdb-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="fefdb-269">Voicemail</span><span class="sxs-lookup"><span data-stu-id="fefdb-269">Voicemail</span></span>
    
- <span data-ttu-id="fefdb-270">Besprechungsaufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="fefdb-270">Meeting recordings</span></span>
    
- <span data-ttu-id="fefdb-271">Exchange-Aufgabensynchronisierung</span><span class="sxs-lookup"><span data-stu-id="fefdb-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="fefdb-272">Ein begleitendes Diagramm zeigt das Exchange Server 2013 SP1-Architekturposter und enthält einen Link zum Poster.</span><span class="sxs-lookup"><span data-stu-id="fefdb-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

