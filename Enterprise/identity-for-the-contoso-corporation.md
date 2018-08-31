---
title: Identität für die Contoso Corporation
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
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: 'Zusammenfassung: Grundlegendes zu wie Contoso nutzt IDaaS und bietet geografisch verteilten und redundante Authentifizierung für Benutzer.'
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915440"
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="f5298-103">Identität für die Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="f5298-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="f5298-104">**Zusammenfassung:** Verstehen Sie, wie Contoso nutzt IDaaS und bietet geografisch verteilten und redundante Authentifizierung für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="f5298-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="f5298-p101">Microsoft bietet eine Identität als Dienst (IDaaS) über die Cloud-angeboten. Um eine Cloud-inklusive Infrastruktur einführen, muss Contoso IDaaS Lösung ihre lokalen STS-Anbieter nutzen und umfassen Verbundauthentifizierung mit ihren vorhandenen vertrauenswürdigen, Drittanbieter-Identitätsanbieter.</span><span class="sxs-lookup"><span data-stu-id="f5298-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="f5298-107">Windows Server Active Directory-Gesamtstruktur von Contoso</span><span class="sxs-lookup"><span data-stu-id="f5298-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="f5298-p102">Contoso verwendet eine einzelne Windows Server Active Directory (AD)-Gesamtstruktur für „contoso.com“ mit sieben Domänen, eine für jede Region der Welt. Die Zentrale, die Regionalstellen und die Zweigstellen enthalten Domänencontroller für die lokale Authentifizierung und Autorisierung.
</span><span class="sxs-lookup"><span data-stu-id="f5298-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="f5298-110">**Abbildung 1: Gesamtstruktur und Domänen von Contoso weltweit**</span><span class="sxs-lookup"><span data-stu-id="f5298-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Weltweite Windows Server Active Directory-Gesamtstruktur und Domänen](media/Contoso-Poster/Contoso-WW-ID.png)
  
<span data-ttu-id="f5298-112">Abbildung 1 zeigt die Contoso-Gesamtstruktur mit regionalen Domänen für die unterschiedlichen Regionen, die Regionalstellen enthalten.</span><span class="sxs-lookup"><span data-stu-id="f5298-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="f5298-113">Contoso möchte die Konten und Gruppen in der „contoso.com“-Gesamtstruktur zur Authentifizierung und Autorisierung seiner cloudbasierten Apps und Arbeitslasten verwenden.
</span><span class="sxs-lookup"><span data-stu-id="f5298-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="f5298-114">Contoso Verbundauthentifizierung Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="f5298-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="f5298-115">Contoso lässt Folgendes zu:
 


</span><span class="sxs-lookup"><span data-stu-id="f5298-115">Contoso allows:</span></span>
  
- <span data-ttu-id="f5298-116">Kunden können ihre Microsoft-, Facebook- oder Google Mail-Konten verwenden, um sich bei ihren öffentlichen Websites anzumelden.</span><span class="sxs-lookup"><span data-stu-id="f5298-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="f5298-117">Lieferanten und Partner können ihre LinkedIn-, Salesforce- oder Google Mail-Konten verwenden, um sich beim Partnerextranet anzumelden.</span><span class="sxs-lookup"><span data-stu-id="f5298-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="f5298-118">**Abbildung 2: Contosos Unterstützung für die Verbundauthentifizierung für Kunden und Partner**</span><span class="sxs-lookup"><span data-stu-id="f5298-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Contosos vorhandene Infrastruktur für die Unterstützung der Verbundauthentifizierung für Kunden und Partner](media/Contoso-Poster/Federated-ID.png)
  
<span data-ttu-id="f5298-p103">Abbildung 2 zeigt die Contoso-DMZ mit einer öffentlichen Website, einem Partnerextranet und einer Reihe von AD FS-Servern. Die DMZ ist mit dem Internet verbunden, das Kunden, Partner und Internetdienste enthält.</span><span class="sxs-lookup"><span data-stu-id="f5298-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="f5298-122">Active Directory Federation Services-Server (AD FS) in der DMZ authentifizieren Kundenanmeldeinformationen für Zugriff auf die öffentliche Website und Partneranmeldeinformationen für Zugriff auf das Partnerextranet.</span><span class="sxs-lookup"><span data-stu-id="f5298-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="f5298-p104">Wenn Contoso ihrer öffentlichen Website mit einem Azure Web App und Partnerextranet Dynamics 365 wechselt, soll weiterhin für den Kunden und Partnern diese Drittanbieter-Identitätsanbieter verwenden. Dies wird durch die Konfiguration des Verbunds zwischen Mandanten "Contoso" Azure AD und diese Drittanbieter-Identitätsanbieter erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="f5298-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="f5298-125">Directory-Synchronisierung für Contoso Windows Server Active Directory-Gesamtstruktur</span><span class="sxs-lookup"><span data-stu-id="f5298-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="f5298-p105">Contoso hat das Azure AD-Connect-Tool auf einem Server in seiner Paris Datacenter-Cluster bereitgestellt. Azure Active Directory verbinden synchronisiert Änderungen an der Windows Server Active Directory-Gesamtstruktur "contoso.com" mit dem Azure AD-Mandanten von Contoso Office 365, zur Abstimmung, Dynamics 365 und Azure-Abonnements gemeinsam genutzt werden. Weitere Informationen zu Abonnements Lizenzen von Benutzerkonten und Mandanten, finden Sie unter [Abonnements, Lizenzen und Benutzerkonten der Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span><span class="sxs-lookup"><span data-stu-id="f5298-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="f5298-129">**Abbildung 3: Infrastruktur für die Verzeichnissynchronisierung von Contoso**</span><span class="sxs-lookup"><span data-stu-id="f5298-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Infrastruktur für die Verzeichnissynchronisierung von Contoso](media/Contoso-Poster/DirSync.png)
  
<span data-ttu-id="f5298-131">Abbildung 3 zeigt Servercluster, auf dem Azure AD Connect ausgeführt wird, das die Windows Server AD-Gesamtstruktur von Contoso mit dem Azure AD-Mandanten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="f5298-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="f5298-p106">Contoso hat Verbundauthentifizierung, konfiguriert die einmaliges Anmelden für Contoso Worker bereitstellt. Ein Benutzer, der bereits die "contoso.com" Windows Server Active Directory-Gesamtstruktur angemeldet hat eine Microsoft SaaS oder PaaS Cloud-Ressource zugreift, werden nicht zur Eingabe eines Kennworts aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="f5298-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="f5298-134">Geografische Verteilung des Contoso-Authentifizierungsdatenverkehrs
</span><span class="sxs-lookup"><span data-stu-id="f5298-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="f5298-p107">Damit Contoso seine Mobil- und Remotemitarbeiter besser unterstützen kann, werden in Contosos Regionalstellen Gruppen von Authentifizierungsservern bereitgestellt. Bei dieser Infrastruktur wird die Last verteilt und werden Redundanz und höhere Leistung geboten, wenn Benutzeranmeldeinformationen für den Zugriff auf Microsoft-Cloudangebote authentifiziert werden, für die der gemeinsame Azure AD-Mandant verwendet wird.
</span><span class="sxs-lookup"><span data-stu-id="f5298-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="f5298-137">Damit die Last von Authentifizierungsanfragen verteilt wird, hat Contoso Traffic Manager mit einem Profil konfiguriert, in dem die Leistungsroutingmethode verwendet wird, wodurch authentifizierende Clients an die regional nächstgelegene Gruppe von Authentifizierungsservern verwiesen wird.
 </span><span class="sxs-lookup"><span data-stu-id="f5298-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="f5298-138">**Abbildung 4: Geografische Verteilung des Authentifizierungsdatenverkehrs für Regionalstellen
**</span><span class="sxs-lookup"><span data-stu-id="f5298-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![<span data-ttu-id="f5298-139">Geografische Verteilung des Contoso-Authentifizierungsdatenverkehrs für Regionalstellen
</span><span class="sxs-lookup"><span data-stu-id="f5298-139">Geographical distribution of Contoso authentication traffic for regional offices</span></span>](media/Contoso-Poster/Auth-GeoDist.png)
  
<span data-ttu-id="f5298-p108">Abbildung 4 zeigt die Ebenen von Clientcomputern, Azure Traffic Manager und Authentifizierungsservern in Regionalstellen. Jede regionale Niederlassung verwendet Webproxys und AD FS-Server, um Benutzeranmeldeinformationen mit Windows Server AD-Domänencontrollern zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="f5298-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="f5298-142">Beispiel zum Authentifizierungsprozess:
</span><span class="sxs-lookup"><span data-stu-id="f5298-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="f5298-143">Der Clientcomputer initiiert eine Kommunikation mit einer Webseite in der Office 365-Mandantschaft in Europa (z. B. „sharepoint.contoso.com“).


</span><span class="sxs-lookup"><span data-stu-id="f5298-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="f5298-p109">Office 365 sendet eine Anforderung zum Nachweis der Authentifizierung zurück. Die Anforderung enthält die URL, die für die Authentifizierung kontaktiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="f5298-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="f5298-146">Der Clientcomputer versucht, den DNS-Namen in der URL zu einer IP-Adresse aufzulösen.</span><span class="sxs-lookup"><span data-stu-id="f5298-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="f5298-147">Azure Traffic Manager empfängt die DNS-Abfrage und antwortet dem Clientcomputer mit der IP-Adresse eines Webanwendungs-Proxyservers in der Regionalstelle, die am nächsten zum Clientcomputer liegt.
</span><span class="sxs-lookup"><span data-stu-id="f5298-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="f5298-148"> Der Clientcomputer sendet eine Authentifizierungsanforderung an einen Webanwendungs-Proxyserver, der die Anforderung an einen AD FS-Server weiterleitet.



</span><span class="sxs-lookup"><span data-stu-id="f5298-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="f5298-149">Der AD FS-Server fordert die Anmeldeinformationen des Benutzers vom Clientcomputer an.</span><span class="sxs-lookup"><span data-stu-id="f5298-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="f5298-150">Der Clientcomputer sendet die Anmeldeinformationen des Benutzers, ohne dass der Benutzer zu einer Eingabe aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="f5298-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="f5298-151">Der AD FS-Server überprüft die Anmeldeinformationen mit einem Windows Server AD-Domänencontroller in der Regionalstelle und gibt ein Sicherheitstoken an den Clientcomputer zurück.</span><span class="sxs-lookup"><span data-stu-id="f5298-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="f5298-152">Der Clientcomputer sendet das Sicherheitstoken an Office 365.</span><span class="sxs-lookup"><span data-stu-id="f5298-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="f5298-153">Nach der erfolgreichen Überprüfung speichert Office 365 das Sicherheitstoken zwischen und sendet die Webseitenanforderung aus Schritt 1 an den Clientcomputer.
</span><span class="sxs-lookup"><span data-stu-id="f5298-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="f5298-154">Redundanz für die Authentifizierungsinfrastruktur der Zentrale in Azure IaaS
</span><span class="sxs-lookup"><span data-stu-id="f5298-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="f5298-155">Um Redundanz für die Remote- und Mobilmitarbeiter der Pariser Zentrale bereitzustellen, in der 15.000 Mitarbeiter beschäftigt sind, hat Contoso eine zweite Gruppe von Anwendungsproxys und AD FS-Servern in Azure IaaS bereitgestellt.
</span><span class="sxs-lookup"><span data-stu-id="f5298-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="f5298-156">**Abbildung 5: Redundanz für die Authentifizierungsinfrastruktur in Azure IaaS
**</span><span class="sxs-lookup"><span data-stu-id="f5298-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![Die redundante Authentifizierungsinfrastruktur in Azure Iaas für die Pariser Zentrale](media/Contoso-Poster/Paris-Auth-Redun.png)
  
<span data-ttu-id="f5298-158">Abbildung 5 zeigt Webproxys und AD FS-Server in der DMZ sowie jeweils eine zusätzliche Gruppe in einem standortübergreifenden virtuellen Azure-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="f5298-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="f5298-p110">Wenn die primären Authentifizierungsserver in der DMZ in der Zentrale nicht mehr verfügbar sind, wechseln IT-Mitarbeiter zu der redundanten Gruppe, die in Azure IaaS bereitgestellt ist. Nachfolgende Authentifizierunganforderungen aus dem Büro in Paris verwenden die Gruppe in Azure IaaS, bis das Verfügbarkeitsproblem behoben ist.</span><span class="sxs-lookup"><span data-stu-id="f5298-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="f5298-161">Damit das Hin- und Zurückschalten funktioniert, aktualisiert Contoso das Azure Traffic Manager-Profil so, dass für die Webanwendungsproxys unterschiedliche Gruppen von IP-Adressen verwendet werden:
</span><span class="sxs-lookup"><span data-stu-id="f5298-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="f5298-162">Wenn die DMZ-Authentifizierungsserver verfügbar sind, werden die IP-Adressen der Server in der DMZ verwendet.
</span><span class="sxs-lookup"><span data-stu-id="f5298-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="f5298-163">Wenn die DMZ-Authentifizierungsserver nicht verfügbar sind, werden die IP-Adressen der Server in Azure IaaS verwendet.
</span><span class="sxs-lookup"><span data-stu-id="f5298-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f5298-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f5298-164">See Also</span></span>

[<span data-ttu-id="f5298-165">Contoso in der Microsoft-Cloud</span><span class="sxs-lookup"><span data-stu-id="f5298-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="f5298-166">Ressourcen zur Cloud-IT-Architektur von Microsoft</span><span class="sxs-lookup"><span data-stu-id="f5298-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f5298-167">Microsoft-Cloud-Identität für Enterprise-Architekten</span><span class="sxs-lookup"><span data-stu-id="f5298-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="f5298-168">Identität- und Geräteschutz für Office 365</span><span class="sxs-lookup"><span data-stu-id="f5298-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="f5298-169">Enterprise-Cloud-Roadmap von Microsoft: Ressourcen für IT-Entscheidungsträger</span><span class="sxs-lookup"><span data-stu-id="f5298-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



