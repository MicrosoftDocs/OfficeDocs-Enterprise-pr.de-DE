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
description: 'Zusammenfassung: Grundlegendes zur Hybrid Architektur und Szenarien für die SaaS-basierten Cloud-Angebote von Microsoft (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741391"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="7dd36-103">Hybrid Cloud-Szenarien für Microsoft-SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7dd36-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="7dd36-104">**Zusammenfassung:** Grundlegendes zur Hybrid Architektur und den Szenarien für die SaaS-basierten Cloud-Angebote von Microsoft (Office 365).</span><span class="sxs-lookup"><span data-stu-id="7dd36-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="7dd36-105">Kombinieren Sie lokale Bereitstellungen von Exchange, SharePoint oder Skype for Business mit ihren Gegenstücken in Office 365 als Bestandteile einer Cloudmigrations- oder langfristigen Integrationsstrategie.</span><span class="sxs-lookup"><span data-stu-id="7dd36-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="7dd36-106">Architektur für Microsoft SaaS-Hybridszenarien</span><span class="sxs-lookup"><span data-stu-id="7dd36-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="7dd36-107">Abbildung 1 zeigt die Architektur der SaaS-basierten Hybridszenarien von Microsoft für Office 365.</span><span class="sxs-lookup"><span data-stu-id="7dd36-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
**<span data-ttu-id="7dd36-108">Abbildung 1: Microsoft SaaS-basierte Hybridszenarien für Office 365</span><span class="sxs-lookup"><span data-stu-id="7dd36-108">Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365</span></span>**

![Microsoft SaaS-basierte Hybrid Szenarien für Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="7dd36-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="7dd36-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="7dd36-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="7dd36-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="7dd36-112">Es gibt eine Vielzahl von SaaS-basierten Hybridszenarien, in denen es sich um Office-Serverprodukte und deren Office 365-Gegenstücke dreht:</span><span class="sxs-lookup"><span data-stu-id="7dd36-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="7dd36-113">Exchange-Server in Kombination mit Exchange Online (Exchange Server-Hybridbereitstellung)</span><span class="sxs-lookup"><span data-stu-id="7dd36-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="7dd36-114">Skype for Business Server in Kombination mit Skype for Business Online und den neuen Cloud-PBX- und Cloud Connector Edition-Szenarien</span><span class="sxs-lookup"><span data-stu-id="7dd36-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="7dd36-115">SharePoint Server 2019, SharePoint Server 2016 oder SharePoint Server 2013 in Kombination mit SharePoint Online (mehrere Szenarien)</span><span class="sxs-lookup"><span data-stu-id="7dd36-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="7dd36-116">Es gibt auch Exchange Online mit lokaler Skype for Business Server-Bereitstellung, ein produktübergreifendes Hybridszenario.</span><span class="sxs-lookup"><span data-stu-id="7dd36-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="7dd36-117">Identität</span><span class="sxs-lookup"><span data-stu-id="7dd36-117">Identity</span></span>
    
    <span data-ttu-id="7dd36-118">Kann die Verzeichnissynchronisierung mit Ihren lokalen Active Directory-Domänendiensten (AD DS) einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="7dd36-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="7dd36-119">Alternativ können Sie Azure AD für einen Verbund mit einem Drittanbieter-Identitätsdrittanbieter konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="7dd36-120">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="7dd36-120">Network</span></span>
    
    <span data-ttu-id="7dd36-121">Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit Microsoft-Peering für Office 365 oder Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="7dd36-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="7dd36-122">Lokal</span><span class="sxs-lookup"><span data-stu-id="7dd36-122">On-premises</span></span>
    
    <span data-ttu-id="7dd36-p102">Kann aus vorhandenen Servern für Exchange, SharePoint und Skype for Business bestehen, die auf ihre neuesten Versionen aktualisiert sein sollten. Sie können diese dann für Hybridszenarien mit ihren Office 365-Gegenstücken kombinieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="7dd36-125">Richten Sie Ihre eigene Office 365 dev/Test-Umgebung ein, siehe [office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="7dd36-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="7dd36-126">Skype for Business Hybrid</span><span class="sxs-lookup"><span data-stu-id="7dd36-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="7dd36-127">Mit Skype for Business Hybrid können Sie eine vorhandene lokale Bereitstellung mit Skype for Business Online kombinieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="7dd36-128">Einige Benutzer arbeiten lokal, und einige Benutzer arbeiten online, sie nutzen jedoch dieselbe SIP-Domäne (Session Initiation-Protokoll), z. B. „contoso.com“).</span><span class="sxs-lookup"><span data-stu-id="7dd36-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="7dd36-129">Sie können diese Hybridkonfiguration verwenden, um nach Ihrer eigenen Zeitplanung von der lokalen Bereitstellung zu Office 365 zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="7dd36-130">Skype for Business kann auch in [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)integriert werden.</span><span class="sxs-lookup"><span data-stu-id="7dd36-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
**<span data-ttu-id="7dd36-131">Abbildung 2: die Skype for Business-Hybrid Konfiguration</span><span class="sxs-lookup"><span data-stu-id="7dd36-131">Figure 2: The Skype for Business hybrid configuration</span></span>**

![Die Skype for Business-Hybrid Konfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="7dd36-133">Abbildung 2 zeigt die Skype for Business-Hybrid Konfiguration, bestehend aus einem lokalen Skype for Business-Front-End-Pool und einem Edgeserver, der mit Skype for Business Online in Office 365 kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="7dd36-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="7dd36-134">Weitere Informationen finden Sie unter [Planen der Hybrid Konnektivität zwischen Skype for Business Server und Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="7dd36-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="7dd36-135">Cloud-PBX mit Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="7dd36-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="7dd36-136">Cloud PBX mit Skype for Business Server ermöglicht den Übergang einer vorhandenen Skype for Business Server-Bereitstellung in eine Topologie mit einer lokalen PSTN-Anbindung (Public Switched telePhone Network).</span><span class="sxs-lookup"><span data-stu-id="7dd36-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
**<span data-ttu-id="7dd36-137">Abbildung 3: Cloud-PBX mit Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="7dd36-137">Figure 3: Cloud PBX with Skype for Business Server</span></span>**

![Cloud-PBX mit Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="7dd36-139">Abbildung 3 zeigt die Cloud-nebenstellenANLAGE mit Skype for Business Server-Konfiguration, bestehend aus einer lokalen vorhandenen nebenstellenANLAGE oder einem Telco-Gateway, einem Skype for Business-Server und dem PSTN, das mit der Microsoft Cloud-nebenstellenANLAGE in Office 365 verbunden ist und Skype for Business umfasst. Online.</span><span class="sxs-lookup"><span data-stu-id="7dd36-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="7dd36-140">Benutzer im Unternehmen, die in der Cloud gehostet werden, können private PBX-Dienste (Private Branch Exchange, Nebenstellenanlage) aus der Microsoft-Cloud empfangen, wozu Signalisierung und Voicemail gehören, aber Festnetzanbindung (Freizeichen) wird über Enterprise-VoIP aus Ihrer lokalen Skype for Business Server-Bereitstellung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7dd36-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="7dd36-141">Dies ist ein hervorragendes Beispiel für eine Hybrid Konfiguration, mit der Sie schrittweise zu einem cloudbasierten Dienst migrieren können.</span><span class="sxs-lookup"><span data-stu-id="7dd36-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="7dd36-142">Sie können die VoIP-Funktionen Ihrer Benutzer behalten, wenn Sie beginnen, Sie in Skype for Business Online zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="7dd36-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="7dd36-143">Sie können Ihre Benutzer in Ihrem eigenen Tempo bewegen, da Sie wissen, dass Ihre VoIP-Funktionen unabhängig von ihrem Speicherort fortgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="7dd36-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="7dd36-144">Weitere Informationen finden Sie unter [Planen der Hybrid Konnektivität zwischen Skype for Business Server und Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="7dd36-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="7dd36-145">Wenn Sie noch keine Lync Server- oder Skype for Business Server-Bereitstellung haben, können Sie Skype for Business Cloud Connector Edition verwenden. Dies ist eine Gruppe von konfektionierten virtuellen Computern, in denen lokale Festnetzanbindung (PSTN-Konnektivität) mit Cloud-PBX implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="7dd36-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="7dd36-146">Weitere Informationen finden Sie unter [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="7dd36-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="7dd36-147">SharePoint-Hybridlösung</span><span class="sxs-lookup"><span data-stu-id="7dd36-147">SharePoint Hybrid</span></span>

<span data-ttu-id="7dd36-148">In einer SharePoint-Hybridlösung wird SharePoint Online in Office 365 mit Ihrer lokalen SharePoint-Farm kombiniert, um das Beste aus beiden zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="7dd36-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
**<span data-ttu-id="7dd36-149">Abbildung 4: Die SharePoint-Hybridkonfiguration</span><span class="sxs-lookup"><span data-stu-id="7dd36-149">Figure 4: The SharePoint hybrid configuration</span></span>**

![Die SharePoint-Hybrid Konfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="7dd36-151">Abbildung 4 zeigt die SharePoint-Hybrid Konfiguration, bestehend aus einer lokalen SharePoint-Farm, die mit SharePoint Online in Office 365 kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="7dd36-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="7dd36-152">SharePoint-Hybridszenarien:</span><span class="sxs-lookup"><span data-stu-id="7dd36-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="7dd36-153">OneDrive for Business-Hybridbereitstellung</span><span class="sxs-lookup"><span data-stu-id="7dd36-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="7dd36-154">Hybrid Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="7dd36-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="7dd36-155">Hybridsuche</span><span class="sxs-lookup"><span data-stu-id="7dd36-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="7dd36-156">Hybridprofile</span><span class="sxs-lookup"><span data-stu-id="7dd36-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="7dd36-157">Hybrid Auswahl</span><span class="sxs-lookup"><span data-stu-id="7dd36-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="7dd36-158">Es ist einfach, Hybridszenarien mit den Assistenten zu aktivieren, mit denen die Hybridkonfiguration automatisiert wird und die aus dem SharePoint Online Admin Center in Office 365 verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="7dd36-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="7dd36-159">Das erweiterbare Hybrid-App-Startfeld</span><span class="sxs-lookup"><span data-stu-id="7dd36-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="7dd36-160">Ermöglicht es Benutzern, Office 365-Video- und Delve-Apps und -Oberflächen auf den Seiten ihrer lokalen SharePoint-Farm anzuzeigen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dd36-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="7dd36-161">Diese SharePoint-Hybridszenarien sind mit Ausnahme von „Das erweiterbare Hybrid-Startprogramm für Apps“ alle sowohl für SharePoint 2016- als auch für SharePoint 2013-Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7dd36-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="7dd36-162">Exchange Server 2016 Hybrid</span><span class="sxs-lookup"><span data-stu-id="7dd36-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="7dd36-163">Mit Exchange Server 2016 Hybrid können Sie von den Vorteilen von Exchange Online in Office 365 für Onlinebenutzer profitieren, während lokale Benutzer weiterhin die vorhandene Exchange Server-Infrastruktur nutzen. </span><span class="sxs-lookup"><span data-stu-id="7dd36-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
**<span data-ttu-id="7dd36-164">Abbildung 5: Die Exchange 2016-Hybridkonfiguration</span><span class="sxs-lookup"><span data-stu-id="7dd36-164">Figure 5: The Exchange 2016 hybrid configuration</span></span>**

![Die Exchange 2016-Hybrid Konfiguration](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="7dd36-166">Abbildung 5 zeigt die Exchange 2016-Hybrid Konfiguration, die aus lokalen Exchange-Postfachservern besteht, die mit Exchange Online Protection und Postfächern in Office 365 kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="7dd36-167">Einige Benutzer haben einen lokalen E-Mail-Server, und einige Benutzer verwenden Exchange Online, aber für alle Benutzer wird derselbe E-Mail-Adressraum genutzt. </span><span class="sxs-lookup"><span data-stu-id="7dd36-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="7dd36-168">Diese Hybridkonfiguration ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7dd36-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="7dd36-169">Sie können Ihre vorhandene Exchange Server-Infrastruktur nutzen, während Sie nach und nach gemäß Ihrem Zeitplan zu Exchange Online migrieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="7dd36-170">Sie können Remotestandorte unterstützen, ohne in eine Zweigstelleninfrastruktur zu investieren.</span><span class="sxs-lookup"><span data-stu-id="7dd36-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="7dd36-171">Sie können aus dem Internet eingehende E-Mails über Exchange Online Protection in Office 365 weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="7dd36-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="7dd36-172">Es können die Anforderungen von multinationalen Unternehmen erfüllt werden, die Filialen haben, für die lokales Speichern von Daten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="7dd36-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="7dd36-173">Sie können diese Hybridkonfiguration auch mit anderen Microsoft Office 365-Anwendungen kombinieren, einschließlich Skype for Business Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7dd36-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="7dd36-174">Weitere Informationen finden Sie unter [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="7dd36-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7dd36-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7dd36-175">See Also</span></span>

[<span data-ttu-id="7dd36-176">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="7dd36-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="7dd36-177">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="7dd36-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

