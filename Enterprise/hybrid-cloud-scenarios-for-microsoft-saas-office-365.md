---
title: "Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Zusammenfassung: Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365)."
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="ce1c3-103">Hybrid Cloud-Szenarien für Microsoft SaaS (Office 365)</span><span class="sxs-lookup"><span data-stu-id="ce1c3-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="ce1c3-104">**Zusammenfassung:** Grundlegendes zur Hybrid-Architektur und Szenarien für Microsofts SaaS-basierte cloud-angeboten (Office 365).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="ce1c3-105">Kombinieren Sie lokale Bereitstellungen von Exchange, SharePoint oder Skype for Business mit ihren Gegenstücken in Office 365 als Bestandteile einer Cloudmigrations- oder langfristigen Integrationsstrategie.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="ce1c3-106">Architektur für Microsoft SaaS-Hybridszenarien</span><span class="sxs-lookup"><span data-stu-id="ce1c3-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="ce1c3-107">Abbildung 1 zeigt die Architektur der SaaS-basierten Hybridszenarien von Microsoft für Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="ce1c3-108">**Abbildung 1: Microsoft SaaS-basierte hybridszenarien für Office 365**</span><span class="sxs-lookup"><span data-stu-id="ce1c3-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Microsoft SaaS-basierte Hybridszenarien für Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="ce1c3-110">Für jede Schicht der Architektur:</span><span class="sxs-lookup"><span data-stu-id="ce1c3-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="ce1c3-111">Apps und Szenarien</span><span class="sxs-lookup"><span data-stu-id="ce1c3-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="ce1c3-112">Es gibt eine Vielzahl von SaaS-basierten Hybridszenarien, in denen es sich um Office-Serverprodukte und deren Office 365-Gegenstücke dreht:</span><span class="sxs-lookup"><span data-stu-id="ce1c3-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="ce1c3-113">Exchange-Server in Kombination mit Exchange Online (Exchange Server-Hybridbereitstellung)</span><span class="sxs-lookup"><span data-stu-id="ce1c3-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="ce1c3-114">Skype for Business Server in Kombination mit Skype for Business Online und den neuen Cloud-PBX- und Cloud Connector Edition-Szenarien</span><span class="sxs-lookup"><span data-stu-id="ce1c3-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="ce1c3-115">SharePoint Server 2016 oder SharePoint Server 2013 in Kombination mit SharePoint Online (mehrere Szenarien)</span><span class="sxs-lookup"><span data-stu-id="ce1c3-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="ce1c3-116">Es gibt auch Exchange Online mit lokaler Skype for Business Server-Bereitstellung, ein produktübergreifendes Hybridszenario.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="ce1c3-117">Identität</span><span class="sxs-lookup"><span data-stu-id="ce1c3-117">Identity</span></span>
    
    <span data-ttu-id="ce1c3-p101">Kann Verzeichnissynchronisierung mit lokaler Windows Server AD-Umgebung enthalten. Alternativ können Sie Azure AD für einen Verbund mit einem Drittanbieter-Identitätsdrittanbieter konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="ce1c3-120">Netzwerk</span><span class="sxs-lookup"><span data-stu-id="ce1c3-120">Network</span></span>
    
    <span data-ttu-id="ce1c3-121">Besteht aus Ihrem vorhandenen Internetzugang oder einer ExpressRoute-Verbindung mit Microsoft-Peering für Office 365 oder Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="ce1c3-122">Lokal</span><span class="sxs-lookup"><span data-stu-id="ce1c3-122">On-premises</span></span>
    
    <span data-ttu-id="ce1c3-p102">Kann aus vorhandenen Servern für Exchange, SharePoint und Skype for Business bestehen, die auf ihre neuesten Versionen aktualisiert sein sollten. Sie können diese dann für Hybridszenarien mit ihren Office 365-Gegenstücken kombinieren.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="ce1c3-125">Richten Sie Ihre eigene [Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="ce1c3-126">Skype for Business 2015 Hybrid</span><span class="sxs-lookup"><span data-stu-id="ce1c3-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="ce1c3-p103">Skype für Business 2015 hybride können Sie eine vorhandene lokale Bereitstellung mit Skype für Business Online zu kombinieren. Einige Benutzer werden lokal und einige Benutzer online verwaltet werden, aber die Benutzer freigeben Session Initiation Protocol (SIP) derselben Domäne, z. B. "contoso.com". Diese hybridkonfiguration können Sie lokal Migration zu Office 365 im Laufe der Zeit im Terminplan. Skype für Business 2015 kann auch mit Exchange Online integriert werden.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="ce1c3-130">**Abbildung 2: Skype Business 2015 hybridkonfiguration**</span><span class="sxs-lookup"><span data-stu-id="ce1c3-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Die Skype for Business 2015-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="ce1c3-132">Abbildung 2 zeigt die Skype hybridkonfiguration Business 2015, bestehend aus einer lokalen Skype für Business 2015 Front-End-Pool und Edge Server zum Kommunizieren mit Skype für Business Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="ce1c3-133">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ce1c3-133">For more information, see:</span></span>
  
- [<span data-ttu-id="ce1c3-134">Planen von hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online</span><span class="sxs-lookup"><span data-stu-id="ce1c3-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="ce1c3-135">Unterstützte hybridkonfigurationen für Skype für Business Server 2015</span><span class="sxs-lookup"><span data-stu-id="ce1c3-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="ce1c3-136">Skype für hybride Business</span><span class="sxs-lookup"><span data-stu-id="ce1c3-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="ce1c3-137">Cloud-PBX mit Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="ce1c3-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="ce1c3-138">Cloud-PBX mit Skype for Business Server ermöglicht es Ihnen, eine vorhandene lokale Skype for Business Server-Bereitstellung in eine Topologie mit lokaler PSTN-Konnektivität (Public Switched Telephone Network) zu überführen. </span><span class="sxs-lookup"><span data-stu-id="ce1c3-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="ce1c3-139">**Abbildung 3: Cloud Nebenstellenanlage mit Skype für Business Server**</span><span class="sxs-lookup"><span data-stu-id="ce1c3-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud-PBX mit Skype for Business Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="ce1c3-141">Abbildung 3 zeigt die Cloud-Nebenstellenanlage mit Skype für Business Server-Konfiguration, bestehend aus einem lokalen, vorhandene PBX oder Telekommunikation Gateway, einen Skype für Business Server und dem PSTN der Microsoft-Cloud-Nebenstellenanlage in Office 365, einschließlich Skype für Unternehmen verbunden Online.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="ce1c3-142">Benutzer im Unternehmen, die in der Cloud gehostet werden, können private PBX-Dienste (Private Branch Exchange, Nebenstellenanlage) aus der Microsoft-Cloud empfangen, wozu Signalisierung und Voicemail gehören, aber Festnetzanbindung (Freizeichen) wird über Enterprise-VoIP aus Ihrer lokalen Skype for Business Server-Bereitstellung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="ce1c3-p104">Dies ist ein gutes Beispiel für eine Hybridkonfiguration, die Ihnen eine schrittweise Migration zu einem cloudbasierten Dienst ermöglicht. Sie können die Sprachfunktionen der Benutzer beibehalten, wenn Sie diese zu Skype for Business Online verschieben. Sie können Ihre Benutzer in Ihrem eigenen Tempo verschieben. Die Sprachfunktionen werden unabhängig davon, wo die Benutzer gehostet sind, beibhelaten. </span><span class="sxs-lookup"><span data-stu-id="ce1c3-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="ce1c3-146">Weitere Informationen finden Sie unter [Planen der hybridkonnektivität zwischen Skype für Business Server und Skype für Business Online oder Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="ce1c3-147">Wenn Sie noch keine Lync Server- oder Skype for Business Server-Bereitstellung haben, können Sie Skype for Business Cloud Connector Edition verwenden. Dies ist eine Gruppe von konfektionierten virtuellen Computern, in denen lokale Festnetzanbindung (PSTN-Konnektivität) mit Cloud-PBX implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="ce1c3-148">Weitere Informationen finden Sie unter [Planen von Skype für Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="ce1c3-149">SharePoint-Hybridlösung</span><span class="sxs-lookup"><span data-stu-id="ce1c3-149">SharePoint Hybrid</span></span>

<span data-ttu-id="ce1c3-150">In einer SharePoint-Hybridlösung wird SharePoint Online in Office 365 mit Ihrer lokalen SharePoint-Farm kombiniert, um das Beste aus beiden zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="ce1c3-151">**Abbildung 4: Die SharePoint-hybridkonfiguration**</span><span class="sxs-lookup"><span data-stu-id="ce1c3-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![Die SharePoint-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="ce1c3-153">Abbildung 4 zeigt die SharePoint-hybridkonfiguration, bestehend aus einer lokalen SharePoint-Farm zum Kommunizieren mit SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="ce1c3-154">SharePoint-Hybridszenarien:</span><span class="sxs-lookup"><span data-stu-id="ce1c3-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="ce1c3-155">Hybrid-OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="ce1c3-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="ce1c3-156">Hybrid-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="ce1c3-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="ce1c3-157">Hybride Extranet B2B</span><span class="sxs-lookup"><span data-stu-id="ce1c3-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="ce1c3-158">Hybridsuche</span><span class="sxs-lookup"><span data-stu-id="ce1c3-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="ce1c3-159">Hybrid-Profile</span><span class="sxs-lookup"><span data-stu-id="ce1c3-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="ce1c3-160">Hybride Personenauswahl</span><span class="sxs-lookup"><span data-stu-id="ce1c3-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="ce1c3-161">Es ist einfach, Hybridszenarien mit den Assistenten zu aktivieren, mit denen die Hybridkonfiguration automatisiert wird und die aus dem SharePoint Online Admin Center in Office 365 verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="ce1c3-162">Startprogramm für Extensible Hybrid-app</span><span class="sxs-lookup"><span data-stu-id="ce1c3-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="ce1c3-163">Ermöglicht es Benutzern, Office 365-Video- und Delve-Apps und -Oberflächen auf den Seiten ihrer lokalen SharePoint-Farm anzuzeigen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="ce1c3-164">Diese SharePoint-Hybridszenarien sind mit Ausnahme von „Das erweiterbare Hybrid-Startprogramm für Apps“ alle sowohl für SharePoint 2016- als auch für SharePoint 2013-Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="ce1c3-165">Weitere Informationen finden Sie unter [SharePoint-Hybridlösung](http://hybrid.office.com/sharepoint/).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="ce1c3-166">Exchange Server 2016 Hybrid</span><span class="sxs-lookup"><span data-stu-id="ce1c3-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="ce1c3-167">Mit Exchange Server 2016 Hybrid können Sie von den Vorteilen von Exchange Online in Office 365 für Onlinebenutzer profitieren, während lokale Benutzer weiterhin die vorhandene Exchange Server-Infrastruktur nutzen. </span><span class="sxs-lookup"><span data-stu-id="ce1c3-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="ce1c3-168">**Abbildung 5: Die hybridkonfiguration Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="ce1c3-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Die Exchange 2016-Hybridkonfiguration](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="ce1c3-170">Abbildung 5 zeigt die Exchange-2016 hybridkonfiguration bestehend aus lokalen Exchange-Postfachserver mit Exchange Online Protection und Postfächer in Office 365 kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="ce1c3-171">Einige Benutzer haben einen lokalen E-Mail-Server, und einige Benutzer verwenden Exchange Online, aber für alle Benutzer wird derselbe E-Mail-Adressraum genutzt. </span><span class="sxs-lookup"><span data-stu-id="ce1c3-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="ce1c3-172">Diese Hybridkonfiguration ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ce1c3-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="ce1c3-173">Nutzt Ihre vorhandene Exchange Server-Infrastruktur, während Sie zu Exchange Online über einen Zeitraum, nach Ihrem Zeitplan Migration.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="ce1c3-174">Sie können Remotestandorte unterstützen, ohne in eine Zweigstelleninfrastruktur zu investieren.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="ce1c3-175">Sie können aus dem Internet eingehende E-Mails über Exchange Online Protection in Office 365 weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="ce1c3-176">Es können die Anforderungen von multinationalen Unternehmen erfüllt werden, die Filialen haben, für die lokales Speichern von Daten erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="ce1c3-177">Sie können diese Hybridkonfiguration auch mit anderen Microsoft Office 365-Anwendungen kombinieren, einschließlich Skype for Business Online und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ce1c3-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="ce1c3-178">Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) und [Exchange Hybrid](http://hybrid.office.com/exchange/).</span><span class="sxs-lookup"><span data-stu-id="ce1c3-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ce1c3-179">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="ce1c3-179">See Also</span></span>

[<span data-ttu-id="ce1c3-180">Microsoft Hybrid Cloud für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="ce1c3-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="ce1c3-181">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="ce1c3-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ce1c3-182">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="ce1c3-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



