---
title: Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Zusammenfassung: Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123412"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="e2d3b-103">Hybrid Cloud-Szenarien für Microsoft-SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="e2d3b-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="e2d3b-104">**Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="e2d3b-105">Kombinieren Sie lokale Bereitstellungen von Exchange, SharePoint oder Skype for Business mit ihren Gegenstücken in Office 365 als Bestandteile einer Cloudmigrations- oder langfristigen Integrationsstrategie.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="e2d3b-106">Architektur für Microsoft SaaS-Hybridszenarien</span><span class="sxs-lookup"><span data-stu-id="e2d3b-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="e2d3b-107">Abbildung 1 zeigt die Architektur der SaaS-basierten Hybridszenarien von Microsoft für Office 365.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="e2d3b-108">**Abbildung 1: Microsoft SaaS-basierte Hybridszenarien für Office 365**</span><span class="sxs-lookup"><span data-stu-id="e2d3b-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Microsoft SaaS-basierte Hybridszenarien für Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="e2d3b-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="e2d3b-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="e2d3b-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="e2d3b-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="e2d3b-112">Es gibt eine Vielzahl von SaaS-basierten Hybridszenarien, in denen es sich um Office-Serverprodukte und deren Office 365-Gegenstücke dreht:</span><span class="sxs-lookup"><span data-stu-id="e2d3b-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="e2d3b-113">Exchange-Server in Kombination mit Exchange Online (Exchange Server-Hybridbereitstellung)</span><span class="sxs-lookup"><span data-stu-id="e2d3b-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="e2d3b-114">Skype for Business Server in Kombination mit Skype for Business Online und den neuen Cloud-PBX- und Cloud Connector Edition-Szenarien</span><span class="sxs-lookup"><span data-stu-id="e2d3b-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="e2d3b-115">SharePoint Server 2019, 2016 für SharePoint Server oder SharePoint Server 2013 in Kombination mit SharePoint Online (mehrere Szenarien)</span><span class="sxs-lookup"><span data-stu-id="e2d3b-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="e2d3b-116">Es gibt auch Exchange Online mit lokaler Skype for Business Server-Bereitstellung, ein produktübergreifendes Hybridszenario.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="e2d3b-117">Identität</span><span class="sxs-lookup"><span data-stu-id="e2d3b-117">Identity</span></span>
    
    <span data-ttu-id="e2d3b-p101">Kann Verzeichnissynchronisierung mit lokaler Windows Server AD-Umgebung enthalten. Alternativ können Sie Azure AD für einen Verbund mit einem Drittanbieter-Identitätsdrittanbieter konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="e2d3b-120">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="e2d3b-120">Network</span></span>
    
    <span data-ttu-id="e2d3b-121">Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit Microsoft-Peering für Office 365 oder Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="e2d3b-122">Lokal</span><span class="sxs-lookup"><span data-stu-id="e2d3b-122">On-premises</span></span>
    
    <span data-ttu-id="e2d3b-p102">Kann aus vorhandenen Servern für Exchange, SharePoint und Skype for Business bestehen, die auf ihre neuesten Versionen aktualisiert sein sollten. Sie können diese dann für Hybridszenarien mit ihren Office 365-Gegenstücken kombinieren.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="e2d3b-125">Richten Sie Ihre eigene Office 365-Umgebung Test-/, finden Sie unter [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="e2d3b-126">Skype für hybride Business</span><span class="sxs-lookup"><span data-stu-id="e2d3b-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="e2d3b-p103">Skype für hybride Business können Sie eine vorhandene lokale Bereitstellung mit Skype für Business Online zu kombinieren. Einige Benutzer werden lokal und einige Benutzer online verwaltet werden, aber die Benutzer freigeben Session Initiation Protocol (SIP) derselben Domäne, z. B. "contoso.com". Diese hybridkonfiguration können Sie lokal Migration zu Office 365 im Laufe der Zeit im Terminplan. Skype für Unternehmen kann auch mit [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)integriert werden.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="e2d3b-131">**Abbildung 2: Skype Business hybridkonfiguration**</span><span class="sxs-lookup"><span data-stu-id="e2d3b-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Die Skype Business hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="e2d3b-133">Abbildung 2 zeigt die Skype Business hybridkonfiguration, bestehend aus einer lokalen Skype für Business Front-End-Pool und Edge Server zum Kommunizieren mit Skype für Business Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="e2d3b-134">Weitere Informationen finden Sie unter [Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="e2d3b-135">Cloud-PBX mit Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="e2d3b-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="e2d3b-136">Übergang von einer vorhandenen Skype für Business Server lokale Bereitstellung zu einer Topologie mit lokalen (Public Switched Telephone Network, PSTN) Konnektivität ermöglicht Cloud Nebenstellenanlage mit Skype für Business Server.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="e2d3b-137">**Abbildung 3: Cloud-PBX mit Skype for Business Server**</span><span class="sxs-lookup"><span data-stu-id="e2d3b-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud-PBX mit Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="e2d3b-139">Abbildung 3 zeigt die Cloud-Nebenstellenanlage mit Skype für Business Server-Konfiguration, bestehend aus einem lokalen, vorhandene PBX oder Telekommunikation Gateway, einen Skype für Business Server und dem PSTN der Microsoft-Cloud-Nebenstellenanlage in Office 365, einschließlich Skype für Unternehmen verbunden Online.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="e2d3b-140">Benutzer im Unternehmen, die in der Cloud gehostet werden, können private PBX-Dienste (Private Branch Exchange, Nebenstellenanlage) aus der Microsoft-Cloud empfangen, wozu Signalisierung und Voicemail gehören, aber Festnetzanbindung (Freizeichen) wird über Enterprise-VoIP aus Ihrer lokalen Skype for Business Server-Bereitstellung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="e2d3b-p104">Dies ist ein hervorragendes Beispiel eine hybridkonfiguration, die schrittweise Migration mit einem cloudbasierten Dienst ermöglicht. Sie können Ihrer Benutzer Sprachfunktionen beibehalten, wenn Sie beginnen, die sie in Skype für Business Online zu verschieben. Sie können die Benutzer an das Tempo, wissen, dass ihre VoIP-Funktionen Nein weiterhin Fachgebiet zur verschieben, wo sie verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="e2d3b-144">Weitere Informationen finden Sie unter [Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="e2d3b-145">Wenn Sie noch keine Lync Server- oder Skype for Business Server-Bereitstellung haben, können Sie Skype for Business Cloud Connector Edition verwenden. Dies ist eine Gruppe von konfektionierten virtuellen Computern, in denen lokale Festnetzanbindung (PSTN-Konnektivität) mit Cloud-PBX implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="e2d3b-146">Weitere Informationen finden Sie unter [Planen von Skype für Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="e2d3b-147">SharePoint-Hybridlösung</span><span class="sxs-lookup"><span data-stu-id="e2d3b-147">SharePoint Hybrid</span></span>

<span data-ttu-id="e2d3b-148">In einer SharePoint-Hybridlösung wird SharePoint Online in Office 365 mit Ihrer lokalen SharePoint-Farm kombiniert, um das Beste aus beiden zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="e2d3b-149">**Abbildung 4: Die SharePoint-Hybridkonfiguration**</span><span class="sxs-lookup"><span data-stu-id="e2d3b-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Die SharePoint-Hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="e2d3b-151">Abbildung 4 zeigt die SharePoint-hybridkonfiguration, bestehend aus einer lokalen SharePoint-Farm zum Kommunizieren mit SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="e2d3b-152">SharePoint-Hybridszenarien:</span><span class="sxs-lookup"><span data-stu-id="e2d3b-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="e2d3b-153">OneDrive for Business-Hybridbereitstellung</span><span class="sxs-lookup"><span data-stu-id="e2d3b-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="e2d3b-154">Hybride Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="e2d3b-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="e2d3b-155">Hybridsuche</span><span class="sxs-lookup"><span data-stu-id="e2d3b-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="e2d3b-156">Hybridprofile</span><span class="sxs-lookup"><span data-stu-id="e2d3b-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="e2d3b-157">Hybride Personenauswahl</span><span class="sxs-lookup"><span data-stu-id="e2d3b-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="e2d3b-158">Es ist einfach, Hybridszenarien mit den Assistenten zu aktivieren, mit denen die Hybridkonfiguration automatisiert wird und die aus dem SharePoint Online Admin Center in Office 365 verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="e2d3b-159">Das erweiterbare Hybrid-App-Startfeld</span><span class="sxs-lookup"><span data-stu-id="e2d3b-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="e2d3b-160">Ermöglicht es Benutzern, Office 365-Video- und Delve-Apps und -Oberflächen auf den Seiten ihrer lokalen SharePoint-Farm anzuzeigen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="e2d3b-161">Diese SharePoint-Hybridszenarien sind mit Ausnahme von „Das erweiterbare Hybrid-Startprogramm für Apps“ alle sowohl für SharePoint 2016- als auch für SharePoint 2013-Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="e2d3b-162">Exchange Server 2016 Hybrid</span><span class="sxs-lookup"><span data-stu-id="e2d3b-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="e2d3b-163">Mit Exchange Server 2016 Hybrid können Sie von den Vorteilen von Exchange Online in Office 365 für Onlinebenutzer profitieren, während lokale Benutzer weiterhin die vorhandene Exchange Server-Infrastruktur nutzen. </span><span class="sxs-lookup"><span data-stu-id="e2d3b-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="e2d3b-164">**Abbildung 5: Die Exchange 2016-Hybridkonfiguration**</span><span class="sxs-lookup"><span data-stu-id="e2d3b-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Die Exchange 2016-Hybridkonfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="e2d3b-166">Abbildung 5 zeigt die Exchange-2016 hybridkonfiguration bestehend aus lokalen Exchange-Postfachserver mit Exchange Online Protection und Postfächer in Office 365 kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="e2d3b-167">Einige Benutzer haben einen lokalen E-Mail-Server, und einige Benutzer verwenden Exchange Online, aber für alle Benutzer wird derselbe E-Mail-Adressraum genutzt. </span><span class="sxs-lookup"><span data-stu-id="e2d3b-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="e2d3b-168">Diese Hybridkonfiguration ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e2d3b-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="e2d3b-169">Sie können Ihre vorhandene Exchange Server-Infrastruktur nutzen, während Sie nach und nach gemäß Ihrem Zeitplan zu Exchange Online migrieren.


</span><span class="sxs-lookup"><span data-stu-id="e2d3b-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="e2d3b-170">Sie können Remotestandorte unterstützen, ohne in eine Zweigstelleninfrastruktur zu investieren.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="e2d3b-171">Sie können aus dem Internet eingehende E-Mails über Exchange Online Protection in Office 365 weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="e2d3b-172">Es können die Anforderungen von multinationalen Unternehmen erfüllt werden, die Filialen haben, für die lokales Speichern von Daten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="e2d3b-173">Sie können diese Hybridkonfiguration auch mit anderen Microsoft Office 365-Anwendungen kombinieren, einschließlich Skype for Business Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e2d3b-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="e2d3b-174">Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="e2d3b-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2d3b-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e2d3b-175">See Also</span></span>

[<span data-ttu-id="e2d3b-176">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="e2d3b-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="e2d3b-177">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="e2d3b-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

