---
title: Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Netzwerkintegration von Microsoft Office-Serverprodukten“.
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843866"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="06d9d-103">Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten</span><span class="sxs-lookup"><span data-stu-id="06d9d-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="06d9d-104">**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms namens "Network Integration of Microsoft Office Server Products".</span><span class="sxs-lookup"><span data-stu-id="06d9d-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="06d9d-105">Dieses Poster bietet eine allgemeine Darstellung einer Netzwerkumgebung, die lync Server 2013, SharePoint 2013 und Exchange Server 2013 umfasst.</span><span class="sxs-lookup"><span data-stu-id="06d9d-105">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013.</span></span> <span data-ttu-id="06d9d-106">Es zeigt außerdem die folgenden Netzwerkelemente, die für diese Produkte üblich sind: Remote- und interner Zugriff, Authentifizierung, Clientdatenverkehr und Routen von Datenverkehr über gemeinsam genutzte Geräte.</span><span class="sxs-lookup"><span data-stu-id="06d9d-106">It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="06d9d-107">Allgemeine Konzepte für Lync, Exchange, SharePoint Server und Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="06d9d-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="06d9d-108">Informationen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="06d9d-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="06d9d-109">Optimierter Netzwerkentwurf</span><span class="sxs-lookup"><span data-stu-id="06d9d-109">Streamlined network design</span></span>

<span data-ttu-id="06d9d-110">Diese Topologie veranschaulicht eine lokale Netzwerkbereitstellung von SharePoint 2013, Exchange Server 2013 und lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="06d9d-110">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013.</span></span> <span data-ttu-id="06d9d-111">Sie zeigt außerdem die Verwendung des cloudbasierten Microsoft-Diensts Exchange Online Protection, der Schutz vor Spam und Schadsoftware für eingehenden SMTP-Datenverkehr (Simple Mail Transfer Protocol) aus dem Internet bietet.</span><span class="sxs-lookup"><span data-stu-id="06d9d-111">It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="06d9d-p103">Dieser Netzwerkentwurf wurde optimiert und enthält nur ein Minimum von Netzwerkfeatures. Der Entwurf berücksichtigt keine zusätzlichen Sicherheits- oder Infrastrukturfeatures, die in einigen Organisationen möglicherweise erforderlich sind.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="06d9d-114">Informationen zu diesem Diagramm: </span><span class="sxs-lookup"><span data-stu-id="06d9d-114">This diagram:</span></span> 
  
- <span data-ttu-id="06d9d-115">Es enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="06d9d-116">Es zeigt die Verwendung optionaler RAS-Server, z. B. eines Drittanbieter-VPN-Gateways oder DirectAccess-Servers, um Roaming- oder Remotemitarbeitern eine sichere Kommunikation zu ermöglichen. </span><span class="sxs-lookup"><span data-stu-id="06d9d-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="06d9d-117">Es beschreibt ausführlich den SharePoint-, Exchange- und Lync-Datenverkehrsfluss vom Client zu den einzelnen Plattformserverebenen. </span><span class="sxs-lookup"><span data-stu-id="06d9d-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="06d9d-118">Es gibt den Typ der Verbindung für Remote- oder internen Zugriff auf Basis von Client (z. B. Partner oder Mitarbeiter) und verwendeter Authentifizierungsmethode an.</span><span class="sxs-lookup"><span data-stu-id="06d9d-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="06d9d-119">Es unterteilt die SharePoint-, Exchange- und Lync-Plattformen nach erforderlichen Serverrollen und identifiziert dabei die Front-End-, Anwendungs-, Datenbank- und andere Schichten.</span><span class="sxs-lookup"><span data-stu-id="06d9d-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="06d9d-p104">Die hier für SharePoint, Lync und Exchange verwendete Architektur ist keine bevorzugte Methode zur Implementierung dieser Plattformen. Sie dient lediglich als Beispiel, da sich Topologien basierend auf den jeweiligen Netzwerkanforderungen und Sicherheitsaspekten unterscheiden. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="06d9d-122">Gatewayrouter</span><span class="sxs-lookup"><span data-stu-id="06d9d-122">Gateway router</span></span>

<span data-ttu-id="06d9d-p105">Bei dieser Topologie befindet sich der Gatewayrouter am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet. Alternativ können auch andere Komponenten vorhanden sein, die die Lücke zwischen dem Gatewayrouter und dem dargestellten Lastenausgleich schließen, z. B. mehrere Firewallebenen. Diese Topologie stellt nur eine von vielen Möglichkeiten zur Bereitstellung Ihres Netzwerks dar. In dieser Konfiguration ist das Gateway mit Zugriffssteuerungslisten (Access Control Lists, ACLs) konfiguriert, um ganz bestimmten eingehenden und ausgehenden IP-basierten Datenverkehr an den Routerschnittstellen zuzulassen. ACLs, erweiterte Überprüfung oder Netzwerkadressenübersetzung (Network Address Translation, NAT) können auch auf anderen Geräten im Netzwerk ausgeführt werden, z. B. Firewalls. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="06d9d-128">Lastenausgleich und Reverseproxygeräte</span><span class="sxs-lookup"><span data-stu-id="06d9d-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="06d9d-129">Sie können Hardware- oder Softwarelösungen für den Lastenausgleich verwenden, um Datenverkehr für Segmente umzuleiten, z. B. SharePoint-Front-End-Webserver und Exchange-Clientzugriffsserver (Client Access Server, CAS).</span><span class="sxs-lookup"><span data-stu-id="06d9d-129">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs).</span></span> <span data-ttu-id="06d9d-130">In einigen Fällen ist es optimal, einen Layer 7-hardwarebasierten Lastenausgleich für Persistenz-Anforderungen zu verwenden, da er mithilfe von Informationen in der Anforderung wie Cookies oder Kopfzeilen besser durchführen kann.</span><span class="sxs-lookup"><span data-stu-id="06d9d-130">In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers.</span></span> <span data-ttu-id="06d9d-131">Allerdings sind Faktoren wie Kosten und erhöhte Nutzung und Arbeitsauslastung, die durch eine derartige Lösung entstehen, für Ihre spezifischen Anforderungen möglicherweise nicht wünschenswert.</span><span class="sxs-lookup"><span data-stu-id="06d9d-131">However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs.</span></span> <span data-ttu-id="06d9d-132">Beachten Sie bei einem übergreifenden Lastenausgleich für SharePoint, Exchange und Lync die folgenden Punkte:</span><span class="sxs-lookup"><span data-stu-id="06d9d-132">Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="06d9d-133">SharePoint – für SharePoint 2013 müssen Sie die Affinität für die Front-End-Webserver nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="06d9d-133">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers.</span></span> <span data-ttu-id="06d9d-134">Normalerweise wird Affinität verwendet, um flüchtige Sitzungen zu erstellen und mehrere Authentifizierungsanforderungen von Clients an jeden Front-End-Webserver zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="06d9d-134">Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server.</span></span> <span data-ttu-id="06d9d-135">Der neue verteilte Cache Dienst in SharePoint 2013 speichert und verteilt Anmeldetoken auf den Webservern der SharePoint-Farm.</span><span class="sxs-lookup"><span data-stu-id="06d9d-135">The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="06d9d-136">Exchange-in Exchange 2013 ist die CAS-Rolle für die Verwendung von Layer 4-Lastenausgleich ausgelegt und verteilt Anforderungen auf der Transportschicht.</span><span class="sxs-lookup"><span data-stu-id="06d9d-136">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer.</span></span> <span data-ttu-id="06d9d-137">Dies kann die durch den Lastenausgleich entstehende Nutzung und Arbeitsauslastung erheblich reduzieren.</span><span class="sxs-lookup"><span data-stu-id="06d9d-137">This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="06d9d-138">Der lync-Domain Name System (DNS)-Lastenausgleich wird für SIP-Datenverkehr (Session Initiation Protocol) für lync-Pools empfohlen.</span><span class="sxs-lookup"><span data-stu-id="06d9d-138">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools.</span></span> <span data-ttu-id="06d9d-139">Ein Hardwaregerät zum Lastenausgleich (HLB) ist für den Lync-Webdatenverkehr (HTTPS) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="06d9d-139">Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="06d9d-140">Remotezugriffsoptionen</span><span class="sxs-lookup"><span data-stu-id="06d9d-140">Remote access options</span></span>

<span data-ttu-id="06d9d-p110">Es gibt mehrere Möglichkeiten, um Intranetressourcen für Partner im Internet zu veröffentlichen oder sicheren Remotezugriff für Remote- oder Roamingmitarbeiter bereitzustellen. Beispiele hierfür sind Reverseproxys, DirectAccess und Drittanbieter-VPN-Gateways. Die weiter unten in diesem Abschnitt erläuterten Remotezugriffslösungen sind Möglichkeiten für SharePoint, Lync und Exchange oder eine beliebige Kombination dieser Server in einer lokalen Bereitstellung. Einige Remoteoptionen können jedoch möglicherweise mit einer bestimmten Lösung nicht verwendet werden.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="06d9d-145">Reverse Proxy – ein Reverseproxy unterstützt die Datenverkehrs Verschlüsselung, beispielsweise Secure Sockets Layer (SSL), und damit können Sie Intranet-Anwendungen und Webressourcen für authentifizierte Benutzer und Partner im Internet veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="06d9d-145">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet.</span></span> <span data-ttu-id="06d9d-146">Ein Beispiel ist Microsoft Forefront Unified Access Gateway (UAG).</span><span class="sxs-lookup"><span data-stu-id="06d9d-146">An example is Microsoft Forefront Unified Access Gateway (UAG).</span></span> <span data-ttu-id="06d9d-147">Viele Hardwaregeräte zum Lastenausgleich unterstützen auch Reverseproxyfunktionalität.</span><span class="sxs-lookup"><span data-stu-id="06d9d-147">Many hardware load balancers also support reverse proxy functionality.</span></span> <span data-ttu-id="06d9d-148">Es gibt trotzdem Szenarien, in denen eine eigenständige, an Ihre Anforderungen angepasste Lösung empfehlenswert ist, z. B. Datenverkehrsisolation, Sicherheitskompartimentierung und Leistungsoptimierung.</span><span class="sxs-lookup"><span data-stu-id="06d9d-148">However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="06d9d-149">Reverseproxy – Vorteile und Überlegungen: </span><span class="sxs-lookup"><span data-stu-id="06d9d-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="06d9d-150">Ermöglicht Partnern oder Benutzern den authentifizierten und sicheren Zugriff auf Intranetressourcen (verwendet SSL (TCP 443) zwischen Client und Reverseproxyserver). </span><span class="sxs-lookup"><span data-stu-id="06d9d-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="06d9d-p112">Für Exchange bietet die Verwendung eines Reverseproxys wie z. B. Forefront UAG z. B. den Vorteil, dass vor dem Zugriff auf den Exchange-Clientzugriffsserver eine Vorauthentifizierung stattfindet. Remotezugriffsbenutzer, die veröffentlichte Anwendungen wie Outlook Web Access (OWA) verwenden, können sich mit der Standard-, NTLM- oder Kerberos-Methode authentifizieren, bevor sie das interne Netzwerk erreichen. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="06d9d-153">Für Exchange und SharePoint können Lösungen wie Forefront UAG SSL-Verbindungen beenden und die Auslastung des Intranetressourcenservers verringern, während gleichzeitig eine zentrale Verwaltung von Zertifikaten möglich ist. </span><span class="sxs-lookup"><span data-stu-id="06d9d-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="06d9d-154">Für Lync durchläuft Webdatenverkehr (HTTPS) zur Kommunikation mit Clients den Reverseproxy (TCP 443).</span><span class="sxs-lookup"><span data-stu-id="06d9d-154">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication.</span></span> <span data-ttu-id="06d9d-155">Der Reverseproxy dient als Proxy für die HTTPS-Verbindung zu Lync-Webdiensten, Exchange CAS und Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="06d9d-155">The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps.</span></span> <span data-ttu-id="06d9d-156">UAG wird von lync Server 2013 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="06d9d-156">Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="06d9d-157">DirectAccess – eine RAS-Technologie, die IPSec (Internet Protocol Security) zur Authentifizierung und zum Verschlüsseln des Datenverkehrs zwischen dem DirectAccess-Client und-Server verwendet.</span><span class="sxs-lookup"><span data-stu-id="06d9d-157">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server.</span></span> <span data-ttu-id="06d9d-158">DirectAccess bietet Roaming- und Remotebenutzern gleichzeitigen Zugriff auf Ressourcen im Internet und Intranet, ohne dass eine Verbindung initiiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="06d9d-158">DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="06d9d-159">Überlegungen zu DirectAccess: </span><span class="sxs-lookup"><span data-stu-id="06d9d-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="06d9d-160">DirectAccess verwendet IPsec-geschützten Datenverkehr (Protokoll 50 und 51 sowie UDP 500) zwischen dem DirectAccess-Client und dem Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="06d9d-161">DirectAccess für Windows Server 2012 und Windows 8 erfordert keine Bereitstellung einer Public Key-Infrastruktur (PKI) für die Server- und Clientauthentifizierung. </span><span class="sxs-lookup"><span data-stu-id="06d9d-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="06d9d-162">Es wird empfohlen, DirectAccess mit lync Server 2013 aufgrund von Problemen mit der Audio-und Video Wartezeit im Zusammenhang mit der IPSec-Verschlüsselung und-Entschlüsselung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="06d9d-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="06d9d-163">VPN-Gateway-typische VPN-Gateways stellen eine RAS-Verbindung bereit, bei der ein RAS-Clientcomputer über eine getunnelte und vom Benutzer initiierte Verbindung logisch auf das Intranet projiziert wird.</span><span class="sxs-lookup"><span data-stu-id="06d9d-163">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection.</span></span> <span data-ttu-id="06d9d-164">Sie können Windows Server 2012 Unified Remote Access oder verschiedene Lösungen von Drittanbietern verwenden, um Roaming- oder Remotemitarbeitern sicheren Zugriff auf das Intranet zu bieten.</span><span class="sxs-lookup"><span data-stu-id="06d9d-164">You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees.</span></span> <span data-ttu-id="06d9d-165">VPN wird für Lync nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="06d9d-165">VPN is not recommended for Lync.</span></span> <span data-ttu-id="06d9d-166">Für Lync-Remotedatenverkehr sollten Edgeserver und getrenntes Tunneln verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="06d9d-166">Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="06d9d-167">Überlegungen zu DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="06d9d-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="06d9d-168">Sie müssen alle DNS-Einträge, die sowohl Internet- als auch Intranetbenutzer zulassen, so konfigurieren, dass sie DNS-Namen in die entsprechenden IP-Adressen auflösen. </span><span class="sxs-lookup"><span data-stu-id="06d9d-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="06d9d-169">Für internetbasierte Partner und Roaming- oder Remotemitarbeiter bieten DNS-Einträge, die bei Internet-DNS-Servern registriert sind, nach Bedarf Auflösung in den Satz öffentlicher IP-Adressen für den Gatewayrouter, den Lync-Edgeserver, den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul sowie das DirectAccess- oder VPN-Gateway. </span><span class="sxs-lookup"><span data-stu-id="06d9d-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="06d9d-170">Für intranetbasierte Benutzer bieten DNS-Einträge, die bei Intranet-DNS-Servern registriert sind, die Auflösung in den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul für den Zugriff auf Exchange-, SharePoint- und Lync-Ressourcen. </span><span class="sxs-lookup"><span data-stu-id="06d9d-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="06d9d-p116">DirectAccess-Clients verwenden Intranet-DNS-Server für Namen, die dem Intranet-DNS-Namespace entsprechen, und Internet-DNS-Server für die übrigen Namen. Um die Funktion von DirectAccess zu vereinfachen, erwägen Sie die Verwendung einer geteilten DNS-Implementierung mit unterschiedlichen DNS-Namespaces für intranet- und internetbasierte Namen. Verwenden Sie z. B. „contoso.com“ für den Internetnamespace und „corp.contoso.com“ für den Intranetnamespace. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="06d9d-p117">Exchange verwendet ein geteiltes DNS-Modell, bei dem sich die Auflösung von Host in IP für öffentlich weitergeleiteten Datenverkehr von der im Unternehmensnetzwerk unterscheidet. Sie benötigen zumindest DNS-Einträge für OWA, AutoErmittlung, ActiveSync-URLs für Clientdatenverkehr und einen MX-Eintrag für eingehende Nachrichten. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="06d9d-176">Wenn Sie Exchange Online Protection (EOP) verwenden, zeigt Ihr MX-Eintrag auf diesen Dienst anstatt auf die Exchange-Farm. </span><span class="sxs-lookup"><span data-stu-id="06d9d-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="06d9d-177">Für Exchange benötigen Sie einen TXT-Eintrag als Besitznachweis in Ihrem öffentlichen DNS und eine Verbundorganisations-ID zum Einrichten der Verbundfreigabe. </span><span class="sxs-lookup"><span data-stu-id="06d9d-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="06d9d-178">VPN-Remotezugriffsclients können so konfiguriert werden, dass sie nur Intranet-DNS-Server verwenden, wenn die VPN-Remotezugriffsverbindung aktiv ist. </span><span class="sxs-lookup"><span data-stu-id="06d9d-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="06d9d-179">Diagrammbeschreibung</span><span class="sxs-lookup"><span data-stu-id="06d9d-179">Diagram Description</span></span>

<span data-ttu-id="06d9d-p118">Dieses Diagramm enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht. Die Beschreibung dieses Diagramms ist in zwei Teile unterteilt: </span><span class="sxs-lookup"><span data-stu-id="06d9d-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="06d9d-182">Beschreibung der im Diagramm dargestellten Komponenten </span><span class="sxs-lookup"><span data-stu-id="06d9d-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="06d9d-183">Beschreibung des Datenverkehrsflusses durch die Komponenten zu den SharePoint-, Exchange-, Lync- und Office Web Apps-Serverebenen </span><span class="sxs-lookup"><span data-stu-id="06d9d-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="06d9d-184">Beschreibung der im Diagramm dargestellten Komponenten</span><span class="sxs-lookup"><span data-stu-id="06d9d-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="06d9d-185">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="06d9d-185">User types</span></span>

<span data-ttu-id="06d9d-186">Es gibt vier verschiedene Benutzertypen, drei außerhalb der Netzwerk- und Clouddienste und einen internen; dazu gehören: </span><span class="sxs-lookup"><span data-stu-id="06d9d-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="06d9d-187">Partnerunternehmen (Business-to-Business) – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="06d9d-188">Einzelne Partner (SharePoint und anonym (Lync)) – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="06d9d-189">Roaming- und Remotemitarbeiter – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="06d9d-190">Interne Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="06d9d-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="06d9d-191">Cloudbasierter E-Mail-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-191">Cloud-based email traffic</span></span>

<span data-ttu-id="06d9d-192">Es gibt eine cloudbasierte Komponente für SMTP-basierten E-Mail-Datenverkehr, entweder Internet-Mail-Hosts oder Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="06d9d-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="06d9d-193">Authentifizierung für externen Zugriff</span><span class="sxs-lookup"><span data-stu-id="06d9d-193">Authentication for external access</span></span>

<span data-ttu-id="06d9d-p119">Für jeden der Benutzertypen gibt es einen bestimmten Satz von Authentifizierungsverfahren für Lync, SharePoint und Exchange. Diese werden an späterer Stelle in diesem Thema genauer erläutert. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="06d9d-196">Gatewayrouter mit ACLs</span><span class="sxs-lookup"><span data-stu-id="06d9d-196">Gateway router with ACLs</span></span>

<span data-ttu-id="06d9d-197">Der Gatewayrouter befindet sich am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet. </span><span class="sxs-lookup"><span data-stu-id="06d9d-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="06d9d-198">RAS-Server für Lync und SharePoint</span><span class="sxs-lookup"><span data-stu-id="06d9d-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="06d9d-199">Diese Topologie umfasst einen Lync-Edgeserver und ein SharePoint-VPN-Gateway oder einen DirectAccess-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="06d9d-200">Lastenausgleich und Reverseproxygerät</span><span class="sxs-lookup"><span data-stu-id="06d9d-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="06d9d-p120">Sie können Hardware- oder Softwarelösungen für den Lastenausgleich verwenden, um Datenverkehr für Segmente umzuleiten, z. B. SharePoint-Front-End-Webserver und Exchange-Clientzugriffsserver (Client Access Server, CAS). Diese Topologie zeigt VIP-Komponenten für Lync, SharePoint und Exchange im Lastenausgleichsmodul. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="06d9d-203">Server</span><span class="sxs-lookup"><span data-stu-id="06d9d-203">Servers</span></span>

<span data-ttu-id="06d9d-204">Es gibt vier Server: lync-, SharePoint-, Exchange-und Office-webapps-Server.</span><span class="sxs-lookup"><span data-stu-id="06d9d-204">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server.</span></span> <span data-ttu-id="06d9d-205">Jeder Server kann drei Ebenen haben: eine Front-End-Clientzugriffsebene, eine Anwendungsebene und eine Datenbank-/Speicherebene.</span><span class="sxs-lookup"><span data-stu-id="06d9d-205">Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="06d9d-206">Front-End-Clientzugriffsebene</span><span class="sxs-lookup"><span data-stu-id="06d9d-206">Front-end, client-access tier</span></span>

<span data-ttu-id="06d9d-207">Diese Ebene verfügt über Komponenten auf allen vier Servern: </span><span class="sxs-lookup"><span data-stu-id="06d9d-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="06d9d-p122">Lync-Pool (Front-End). Das Diagramm zeigt zwei Lync-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="06d9d-p123">SharePoint-Front-End und verteilter Cache. Das Diagramm zeigt drei SharePoint-Datenbanken.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="06d9d-p124">Exchange CAS. Das Diagramm zeigt zwei Exchange-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="06d9d-p125">Office Web Apps Server. Das Diagramm zeigt zwei Office Web Apps-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="06d9d-216">Anwendungsebene</span><span class="sxs-lookup"><span data-stu-id="06d9d-216">Application tier</span></span>

<span data-ttu-id="06d9d-217">Diese Ebene verfügt nur über Komponenten auf dem SharePoint-Server: </span><span class="sxs-lookup"><span data-stu-id="06d9d-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="06d9d-p126">Suche (Abfrage, Index, Administration). Das Diagramm zeigt drei SharePoint-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="06d9d-p127">Batchverarbeitung. Das Diagramm zeigt drei SharePoint-Datenbanken.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="06d9d-222">Datenbank-/Speicherebene</span><span class="sxs-lookup"><span data-stu-id="06d9d-222">Database/storage tier</span></span>

<span data-ttu-id="06d9d-223">Diese Ebene verfügt über Komponenten auf dem Lync-, SharePoint- und Exchange-Server: </span><span class="sxs-lookup"><span data-stu-id="06d9d-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="06d9d-p128">Lync-Datenbank (Back-End). Das Diagramm zeigt drei Lync-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="06d9d-p129">SharePoint-Datenbank. Das Diagramm zeigt drei SharePoint-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="06d9d-p130">Exchange-Postfachserver. Das Diagramm zeigt zwei Exchange-Postfachserver. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="06d9d-230">Weitere Informationen zu den auf den einzelnen SharePoint-Serverrollen installierten Komponenten finden Sie unter [optimierte Topologien für SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="06d9d-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="06d9d-231">Beschreibung des Datenverkehrsflusses durch die Komponenten zu den verschiedenen Serverebenen</span><span class="sxs-lookup"><span data-stu-id="06d9d-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="06d9d-232">In diesem Abschnitt wird beschrieben, wie Benutzeranforderungen die Netzwerktopologie durchlaufen.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="06d9d-233">Authentifizierung und Routing für externen Zugriff</span><span class="sxs-lookup"><span data-stu-id="06d9d-233">Authentication and routing for external access</span></span>

<span data-ttu-id="06d9d-234">Es gibt drei verschiedene Clienttypen außerhalb der Netzwerk- und Clouddienste; dazu gehören: </span><span class="sxs-lookup"><span data-stu-id="06d9d-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="06d9d-235">Partnerunternehmen (Business-to-Business) – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="06d9d-236">Einzelne Partner (SharePoint und anonym (Lync)) – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="06d9d-237">Roaming- und Remotemitarbeiter – extern </span><span class="sxs-lookup"><span data-stu-id="06d9d-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="06d9d-238">Der Authentifizierungs- und Routingprozess für die verschiedenen externen Benutzertypen wird einzeln beschrieben. </span><span class="sxs-lookup"><span data-stu-id="06d9d-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="06d9d-239">Partner Unternehmen (Business-to-Business) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="06d9d-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="06d9d-p131">Lync: Verbundvertrauensstellung mit anderen Organisationen, Skype und Verbindungen mit öffentlichen Chatdiensten (PIC) mit AOL. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="06d9d-p132">SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="06d9d-p133">Exchange: Gegenseitige TLS-Authentifizierung (MTSL) für E-Mail-Datenverkehr, SAML-Authentifizierung für Verbundfreigabe. Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="06d9d-246">Der SMTP-Clientdatenverkehr durchläuft den Gatewayrouter und die Exchange-VIP (Lastenausgleich/Reverseproxyserver) zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="06d9d-247">Einzelne Partner (SharePoint) und Anonymous (lync)https://partnerweb.contoso.com (undhttps://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="06d9d-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="06d9d-p134">Lync: Anonyme Benutzer können nur solchen Lync-Besprechungen beitreten, die von Mitarbeitern organisiert wurden. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.  </span><span class="sxs-lookup"><span data-stu-id="06d9d-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="06d9d-p135">SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung oder formularbasierter Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="06d9d-252">Exchange: Nicht zutreffend. </span><span class="sxs-lookup"><span data-stu-id="06d9d-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="06d9d-253">Der Lync-Webdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="06d9d-254">Roaming- und Remotemitarbeiter</span><span class="sxs-lookup"><span data-stu-id="06d9d-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="06d9d-255">Die Exchange-URL verfügt über die folgenden virtuellen Verzeichnisse: AutoErmittlung, ECP, EWS, Microsoft-Server-ActiveSync, OAB, OWA, PowerShell</span><span class="sxs-lookup"><span data-stu-id="06d9d-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="06d9d-p136">Lync: TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="06d9d-p137">SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft das VPN-Gateway oder den DirectAccess-Server zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="06d9d-p138">Exchange: Standardauthentifizierung über SSL (ActiveSync AutoErmittlung), formularbasierte Authentifizierung (OWA). Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="06d9d-262">Lync-Clientdatenverkehr durchläuft den Gatewayrouter zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="06d9d-263">Authentifizierung für internen Zugriff</span><span class="sxs-lookup"><span data-stu-id="06d9d-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="06d9d-264">Interne Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="06d9d-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="06d9d-p139">Lync: Kerberos-, TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="06d9d-p140">SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr läuft zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="06d9d-p141">Exchange: AD DS, formularbasierte Authentifizierung. Der Exchange-Clientdatenverkehr läuft zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="06d9d-271">Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="06d9d-272">Cloudbasierter E-Mail-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-272">Cloud-based email traffic</span></span>

<span data-ttu-id="06d9d-273">Die cloudbasierte Komponente für SMTP-basierten E-Mail-Datenverkehr besteht entweder aus Internet-Mail-Hosts oder aus Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="06d9d-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="06d9d-p142">Diese Komponenten leiten E-Mail-Datenverkehr mithilfe von SMTP durch das Netzwerk. Der Datenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="06d9d-276">Legende zum Netzwerkdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-276">Network traffic legend</span></span>

<span data-ttu-id="06d9d-277">Das Legendenfeld enthält eine grafische Darstellung der verschiedenen im Diagramm gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben: </span><span class="sxs-lookup"><span data-stu-id="06d9d-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="06d9d-278">Grüne Reihe: lync-SIP-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="06d9d-279">Blaue Linie: Lync-Webdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="06d9d-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="06d9d-280">Violette Linie: SharePoint-Clientdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="06d9d-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="06d9d-281">Orangefarbene Linie: Exchange-Clientdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="06d9d-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="06d9d-282">Graue Linie: Exchange-Postfachserver-Datenverkehr zwischen Exchange lokal und Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="06d9d-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="06d9d-283">Die verschiedenen Datenverkehrstypen und die von ihnen verwendeten Ports werden ebenfalls im Legendenfeld beschrieben. </span><span class="sxs-lookup"><span data-stu-id="06d9d-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="06d9d-284">Lync-SIP-Datenverkehr und Lync-Webdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="06d9d-285">Der Lync-Edgeserver verwendet die folgenden Ports für die Kommunikation mit externen Benutzern:  </span><span class="sxs-lookup"><span data-stu-id="06d9d-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="06d9d-286">Signale/Chatdatenverkehr (SIP/SIMPLE): TCP-Port 443 (für eingehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="06d9d-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="06d9d-287">Datenverkehr von Webkonferenzen (PSOM): TCP-Port 443 (für eingehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="06d9d-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="06d9d-288">A/V-Datenverkehr (SRTP): TCP 443, UDP 3478 und TCP 50000-59999 (optional) (für eingehenden und ausgehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="06d9d-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="06d9d-289">Der Lync-Edgeserver verwendet die folgenden Ports für die Verbundkommunikation:  </span><span class="sxs-lookup"><span data-stu-id="06d9d-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="06d9d-290">TCP-Ports 5061 (SIP), 5269 (XMPP), 443 und UDP 3478 (SRTP) (für eingehenden und ausgehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="06d9d-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="06d9d-291">SharePoint-Clientdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-291">SharePoint client traffic</span></span>

<span data-ttu-id="06d9d-p143">SharePoint kann den TCP-Port 443 (SSL) für die verschlüsselte Kommunikation zwischen dem Client und dem Lastenausgleichsmodul nutzen. Für den externen Zugriff aus dem Internet muss dieser Port für ein- und ausgehenden Datenverkehr auf dem Gatewayrouter (oder in der externen Firewall) geöffnet werden. </span><span class="sxs-lookup"><span data-stu-id="06d9d-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="06d9d-294">Exchange-Clientdatenverkehr und Exchange-Postfachserver-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="06d9d-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="06d9d-295">Exchange verwendet TCP-Port 25 (SMTP) für die Kommunikation zwischen Servern.</span><span class="sxs-lookup"><span data-stu-id="06d9d-295">Exchange uses TCP port 25 (SMTP) for server-to-server communications.</span></span> <span data-ttu-id="06d9d-296">Der Großteil des Clientdatenverkehrs (OWA, ActiveSync, AutoErmittlung, Outlook Anywhere) erfolgt über Port 443 (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="06d9d-296">Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS).</span></span> <span data-ttu-id="06d9d-297">Wenn Sie über POP- oder IMAP-Clients verfügen, werden auch die Ports 110 (POP3), 995 (verschlüsseltes POP3), 143 (IMAP4), 993 (verschlüsseltes IMAP4) und 587 (SMTP) zur Unterstützung dieser Clients verwendet.</span><span class="sxs-lookup"><span data-stu-id="06d9d-297">If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="06d9d-298">Weitere Informationen zum Lync-Netzwerkdatenverkehr?</span><span class="sxs-lookup"><span data-stu-id="06d9d-298">More on Lync network traffic?</span></span>

<span data-ttu-id="06d9d-299">Erfahren Sie, wie Lync Server Ihrer Organisation bei der Bereitstellung von Chat, Webkonferenzen, Anwendungsfreigabe und Sprachkommunikation helfen kann.</span><span class="sxs-lookup"><span data-stu-id="06d9d-299">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication.</span></span> <span data-ttu-id="06d9d-300">Weitere Informationen finden Sie unter [Microsoft lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="06d9d-300">For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="06d9d-301">Das Poster enthält auch einen QR-Code zum Zugreifen auf diese Informationen.</span><span class="sxs-lookup"><span data-stu-id="06d9d-301">The poster also includes a QR code to access this information.</span></span> 
  

