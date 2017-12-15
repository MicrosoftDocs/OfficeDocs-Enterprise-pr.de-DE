---
title: "Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Netzwerkintegration von Microsoft Office-Serverprodukten“."
ms.openlocfilehash: 2ced3ae648d07ae00c66b8ede8562df66826e4a9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="3ce03-103">Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten</span><span class="sxs-lookup"><span data-stu-id="3ce03-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="3ce03-104">**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Netzwerk Integration von Microsoft Office Server-Produkten.</span><span class="sxs-lookup"><span data-stu-id="3ce03-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="3ce03-p101">Dieses Poster enthält eine allgemeine Darstellung einer Netzwerk-Umgebung, die Lync Server 2013, SharePoint 2013 und Exchange Server 2013 enthält. Außerdem wird veranschaulicht, die folgenden-Elementen, die für diese Produkte sind: Remote- und internen Zugriff, Authentifizierung, Datenverkehr zwischen Clients und routing des Datenverkehrs über freigegebene Geräte.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="3ce03-107">Allgemeine Konzepte für Lync, Exchange, SharePoint Server und Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="3ce03-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="3ce03-108">Informationen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="3ce03-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="3ce03-109">Optimierter Netzwerkentwurf</span><span class="sxs-lookup"><span data-stu-id="3ce03-109">Streamlined network design</span></span>

<span data-ttu-id="3ce03-p102">Diese Topologie veranschaulicht die Bereitstellung einer lokalen Netzwerk von SharePoint 2013, Exchange Server 2013 und Lync Server 2013. Es wird auch die Verwendung von Microsoft Cloud-basierten Dienst, Exchange Online Protection, die aus dem Internet Spam und Malware Protection für eingehenden Datenverkehr von Simple Mail Transfer Protocol (SMTP) bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="3ce03-p103">Dieser Netzwerkentwurf wurde optimiert und enthält nur ein Minimum von Netzwerkfeatures. Der Entwurf berücksichtigt keine zusätzlichen Sicherheits- oder Infrastrukturfeatures, die in einigen Organisationen möglicherweise erforderlich sind.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="3ce03-114">Informationen zu diesem Diagramm: </span><span class="sxs-lookup"><span data-stu-id="3ce03-114">This diagram:</span></span> 
  
- <span data-ttu-id="3ce03-115">Es enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="3ce03-116">Es zeigt die Verwendung optionaler RAS-Server, z. B. eines Drittanbieter-VPN-Gateways oder DirectAccess-Servers, um Roaming- oder Remotemitarbeitern eine sichere Kommunikation zu ermöglichen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="3ce03-117">Es beschreibt ausführlich den SharePoint-, Exchange- und Lync-Datenverkehrsfluss vom Client zu den einzelnen Plattformserverebenen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="3ce03-118">Es gibt den Typ der Verbindung für Remote- oder internen Zugriff auf Basis von Client (z. B. Partner oder Mitarbeiter) und verwendeter Authentifizierungsmethode an. </span><span class="sxs-lookup"><span data-stu-id="3ce03-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="3ce03-119">Bricht die SharePoint, Exchange und Lync-Plattformen von erforderlichen Serverrollen, die der Front-End, Anwendung, Datenbank und anderen Ebenen identifiziert.</span><span class="sxs-lookup"><span data-stu-id="3ce03-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="3ce03-p104">Die hier für SharePoint, Lync und Exchange verwendete Architektur ist keine bevorzugte Methode zur Implementierung dieser Plattformen. Sie dient lediglich als Beispiel, da sich Topologien basierend auf den jeweiligen Netzwerkanforderungen und Sicherheitsaspekten unterscheiden. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="3ce03-122">Gatewayrouter</span><span class="sxs-lookup"><span data-stu-id="3ce03-122">Gateway router</span></span>

<span data-ttu-id="3ce03-p105">Bei dieser Topologie befindet sich der Gatewayrouter am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet. Alternativ können auch andere Komponenten vorhanden sein, die die Lücke zwischen dem Gatewayrouter und dem dargestellten Lastenausgleich schließen, z. B. mehrere Firewallebenen. Diese Topologie stellt nur eine von vielen Möglichkeiten zur Bereitstellung Ihres Netzwerks dar. In dieser Konfiguration ist das Gateway mit Zugriffssteuerungslisten (Access Control Lists, ACLs) konfiguriert, um ganz bestimmten eingehenden und ausgehenden IP-basierten Datenverkehr an den Routerschnittstellen zuzulassen. ACLs, erweiterte Überprüfung oder Netzwerkadressenübersetzung (Network Address Translation, NAT) können auch auf anderen Geräten im Netzwerk ausgeführt werden, z. B. Firewalls. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="3ce03-128">Lastenausgleich und Reverseproxygeräte</span><span class="sxs-lookup"><span data-stu-id="3ce03-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="3ce03-p106">Sie können Hardware- oder lastenausgleichslösungen zur Umleitung von Datenverkehr für Segmente, einschließlich SharePoint-Front-End-Servern und Exchange-Clientzugriffsserver (CASs) verwenden. In einigen Fällen ist es optimal ein Layer 7 hardwarebasierten Lastenausgleich für Persistenz Anforderungen verwenden, wie sie mithilfe der Informationen in der Anforderung, z. B. Cookies oder Kopfzeilen besser ausführen kann. Allerdings Faktoren, wie Kosten und verbesserte Auslastung und Arbeitslast aus einer solchen Lösung ist möglicherweise nicht für Ihre Bedürfnisse wünschenswert. Berücksichtigen Sie die folgenden Punkte für einen Lastenausgleich für SharePoint, Exchange und Lync:</span><span class="sxs-lookup"><span data-stu-id="3ce03-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="3ce03-p107">SharePoint - für SharePoint 2013, nicht müssen Sie Affinität für Ihre Front-End-Server zu aktivieren. In der Regel würde dies für Kurznotiz Sitzungen erstellen und Vermeiden von mehreren authentifizierungsanforderungen von Clients auf jedem Front-End-Webserver verwendet werden. Der neue verteilten Cachedienst in SharePoint 2013 speichert und verteilt die Anmeldung Token auf den Webservern der SharePoint-Farm.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="3ce03-p108">Exchange - In Exchange 2013 der CAS-Rolle soll Layer 4-Lastenausgleich, Anfragen auf der Transportschicht verteilen. Dies kann erheblich Load Balancer Auslastung und Arbeitslast reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="3ce03-p109">Lync - System DNS (Domain Name) des Lastenausgleichs für Session Initiation Protocol (SIP) Datenverkehr für Lync-Pools empfohlen. Hardwaregeräte zum Lastenausgleich (Hardwarelastenausgleich) ist für Datenverkehr von Lync Web (HTTPS) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="3ce03-140">Remotezugriffsoptionen</span><span class="sxs-lookup"><span data-stu-id="3ce03-140">Remote access options</span></span>

<span data-ttu-id="3ce03-p110">Es gibt mehrere Möglichkeiten, um Intranetressourcen für Partner im Internet zu veröffentlichen oder sicheren Remotezugriff für Remote- oder Roamingmitarbeiter bereitzustellen. Beispiele hierfür sind Reverseproxys, DirectAccess und Drittanbieter-VPN-Gateways. Die weiter unten in diesem Abschnitt erläuterten Remotezugriffslösungen sind Möglichkeiten für SharePoint, Lync und Exchange oder eine beliebige Kombination dieser Server in einer lokalen Bereitstellung. Einige Remoteoptionen können jedoch möglicherweise mit einer bestimmten Lösung nicht verwendet werden.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="3ce03-p111">Reverseproxy - Reverseproxy unterstützt Datenverkehr Verschlüsselung, wie Secure Sockets Layer (SSL), und mit, die Sie Intranet Applications und Webressourcen zu veröffentlichen können authentifizierten Benutzern und Partnern im Internet. Ein Beispiel ist Microsoft Forefront Unified Access Gateway (UAG). Viele Hardwaregeräte zum Lastenausgleich unterstützt auch Reverseproxy-Funktionen. Es gibt jedoch noch gültige Szenarien für die Verwendung einer eigenständigen Lösung basierend auf Ihren Anforderungen und Anforderungen, beispielsweise zur Optimierung der Leistung, Sicherheit Aufgliederung und Datenverkehr Isolation.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="3ce03-149">Reverseproxy – Vorteile und Überlegungen: </span><span class="sxs-lookup"><span data-stu-id="3ce03-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="3ce03-150">Ermöglicht Partnern oder Benutzern den authentifizierten und sicheren Zugriff auf Intranetressourcen (verwendet SSL (TCP 443) zwischen Client und Reverseproxyserver). </span><span class="sxs-lookup"><span data-stu-id="3ce03-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="3ce03-p112">Für Exchange bietet die Verwendung eines Reverseproxys wie z. B. Forefront UAG z. B. den Vorteil, dass vor dem Zugriff auf den Exchange-Clientzugriffsserver eine Vorauthentifizierung stattfindet. Remotezugriffsbenutzer, die veröffentlichte Anwendungen wie Outlook Web Access (OWA) verwenden, können sich mit der Standard-, NTLM- oder Kerberos-Methode authentifizieren, bevor sie das interne Netzwerk erreichen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="3ce03-153">Für Exchange und SharePoint können Lösungen wie Forefront UAG SSL-Verbindungen beenden und die Auslastung des Intranetressourcenservers verringern, während gleichzeitig eine zentrale Verwaltung von Zertifikaten möglich ist. </span><span class="sxs-lookup"><span data-stu-id="3ce03-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="3ce03-p113">Für Lync durchläuft Reverseproxy (TCP 443) für die Clientkommunikation Web (HTTPS)-Datenverkehr. Der Reverseproxy-Proxys der HTTPS Verbindung mit Lync Web Services, Exchange-Clientzugriffsserver und Office Web Apps. Lync Server 2013 unterstützt UAG nicht.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="3ce03-p114">DirectAccess - eine RAS-Technologie, die internetprotokollsicherheit (IPsec) für die Authentifizierung und zum Verschlüsseln von Datenverkehr zwischen dem DirectAccess-Client und Server verwendet. DirectAccess bietet gleichzeitigen Zugriff auf Internet und Intranet Ressourcen für servergespeicherte und Remotemitarbeiter, ohne eine Verbindung zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="3ce03-159">Überlegungen zu DirectAccess: </span><span class="sxs-lookup"><span data-stu-id="3ce03-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="3ce03-160">DirectAccess verwendet IPsec-geschützten Datenverkehr (Protokoll 50 und 51 sowie UDP 500) zwischen dem DirectAccess-Client und dem Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="3ce03-161">DirectAccess für Windows Server 2012 und Windows 8 erfordert keine Bereitstellung einer Public Key-Infrastruktur (PKI) für die Server- und Clientauthentifizierung. </span><span class="sxs-lookup"><span data-stu-id="3ce03-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="3ce03-162">Es wird empfohlen, vor der Verwendung von DirectAccess aufgrund von Audio- und Videodaten Wartezeitprobleme im Zusammenhang mit IPSec-Verschlüsselung und Entschlüsselung mit Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="3ce03-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="3ce03-p115">VPN-Gateway - Typische VPN-Gateways bieten eine RAS-Verbindung in der ein RAS-Clientcomputer logisch auf im Intranet über eine Verbindung getunnelte und vom Benutzer initiierte projiziert wird. Unified RAS-Dienst in Windows Server 2012 oder mehrere Drittanbieter-Lösungen können Sie die gesicherten Zugriff auf das Intranet für roaming oder remote Mitarbeiter bereitstellen können. VPN wird für Lync nicht empfohlen. Remote-Lync-Datenverkehr sollte verwenden Sie die Edge-Server und gleichzeitig kann split-tunneling.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="3ce03-167">Überlegungen zu DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="3ce03-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="3ce03-168">Sie müssen alle DNS-Einträge, die sowohl Internet- als auch Intranetbenutzer zulassen, so konfigurieren, dass sie DNS-Namen in die entsprechenden IP-Adressen auflösen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="3ce03-169">Für internetbasierte Partner und Roaming- oder Remotemitarbeiter bieten DNS-Einträge, die bei Internet-DNS-Servern registriert sind, nach Bedarf Auflösung in den Satz öffentlicher IP-Adressen für den Gatewayrouter, den Lync-Edgeserver, den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul sowie das DirectAccess- oder VPN-Gateway. </span><span class="sxs-lookup"><span data-stu-id="3ce03-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="3ce03-170">Für intranetbasierte Benutzer bieten DNS-Einträge, die bei Intranet-DNS-Servern registriert sind, die Auflösung in den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul für den Zugriff auf Exchange-, SharePoint- und Lync-Ressourcen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="3ce03-p116">DirectAccess-Clients verwenden Intranet-DNS-Server für Namen, die dem Intranet-DNS-Namespace entsprechen, und Internet-DNS-Server für die übrigen Namen. Um die Funktion von DirectAccess zu vereinfachen, erwägen Sie die Verwendung einer geteilten DNS-Implementierung mit unterschiedlichen DNS-Namespaces für intranet- und internetbasierte Namen. Verwenden Sie z. B. „contoso.com“ für den Internetnamespace und „corp.contoso.com“ für den Intranetnamespace. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="3ce03-p117">Exchange verwendet ein geteiltes DNS-Modell, bei dem sich die Auflösung von Host in IP für öffentlich weitergeleiteten Datenverkehr von der im Unternehmensnetzwerk unterscheidet. Sie benötigen zumindest DNS-Einträge für OWA, AutoErmittlung, ActiveSync-URLs für Clientdatenverkehr und einen MX-Eintrag für eingehende Nachrichten. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="3ce03-176">Wenn Sie Exchange Online Protection (EOP) verwenden, zeigt Ihr MX-Eintrag auf diesen Dienst anstatt auf die Exchange-Farm. </span><span class="sxs-lookup"><span data-stu-id="3ce03-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="3ce03-177">Für Exchange benötigen Sie einen TXT-Eintrag als Besitznachweis in Ihrem öffentlichen DNS und eine Verbundorganisations-ID zum Einrichten der Verbundfreigabe. </span><span class="sxs-lookup"><span data-stu-id="3ce03-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="3ce03-178">VPN-Remotezugriffsclients können so konfiguriert werden, dass sie nur Intranet-DNS-Server verwenden, wenn die VPN-Remotezugriffsverbindung aktiv ist. </span><span class="sxs-lookup"><span data-stu-id="3ce03-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="3ce03-179">Diagrammbeschreibung</span><span class="sxs-lookup"><span data-stu-id="3ce03-179">Diagram Description</span></span>

<span data-ttu-id="3ce03-p118">Dieses Diagramm enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht. Die Beschreibung dieses Diagramms ist in zwei Teile unterteilt: </span><span class="sxs-lookup"><span data-stu-id="3ce03-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="3ce03-182">Beschreibung der im Diagramm dargestellten Komponenten </span><span class="sxs-lookup"><span data-stu-id="3ce03-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="3ce03-183">Beschreibung des Datenverkehrsflusses durch die Komponenten zu den SharePoint-, Exchange-, Lync- und Office Web Apps-Serverebenen </span><span class="sxs-lookup"><span data-stu-id="3ce03-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="3ce03-184">Beschreibung der im Diagramm dargestellten Komponenten </span><span class="sxs-lookup"><span data-stu-id="3ce03-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="3ce03-185">Benutzertypen</span><span class="sxs-lookup"><span data-stu-id="3ce03-185">User types</span></span>

<span data-ttu-id="3ce03-186">Es gibt vier verschiedene Benutzertypen, drei außerhalb der Netzwerk- und Clouddienste und einen internen; dazu gehören: </span><span class="sxs-lookup"><span data-stu-id="3ce03-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="3ce03-187">Partnerunternehmen (Business-to-Business) – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="3ce03-188">Einzelne Partner (SharePoint und anonym (Lync)) – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="3ce03-189">Roaming- und Remotemitarbeiter – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="3ce03-190">Interne Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="3ce03-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="3ce03-191">Cloudbasierter E-Mail-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-191">Cloud-based email traffic</span></span>

<span data-ttu-id="3ce03-192">Es gibt eine cloudbasierte Komponente für SMTP-basierten E-Mail-Datenverkehr, entweder Internet-Mail-Hosts oder Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="3ce03-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="3ce03-193">Authentifizierung für externen Zugriff</span><span class="sxs-lookup"><span data-stu-id="3ce03-193">Authentication for external access</span></span>

<span data-ttu-id="3ce03-p119">Für jeden der Benutzertypen gibt es einen bestimmten Satz von Authentifizierungsverfahren für Lync, SharePoint und Exchange. Diese werden an späterer Stelle in diesem Thema genauer erläutert. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="3ce03-196">Gatewayrouter mit ACLs</span><span class="sxs-lookup"><span data-stu-id="3ce03-196">Gateway router with ACLs</span></span>

<span data-ttu-id="3ce03-197">Der Gatewayrouter befindet sich am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet. </span><span class="sxs-lookup"><span data-stu-id="3ce03-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="3ce03-198">RAS-Server für Lync und SharePoint</span><span class="sxs-lookup"><span data-stu-id="3ce03-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="3ce03-199">Diese Topologie umfasst einen Lync-Edgeserver und ein SharePoint-VPN-Gateway oder einen DirectAccess-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="3ce03-200">Lastenausgleich und Reverseproxygerät</span><span class="sxs-lookup"><span data-stu-id="3ce03-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="3ce03-p120">Sie können Hardware- oder Softwarelösungen für den Lastenausgleich verwenden, um Datenverkehr für Segmente umzuleiten, z. B. SharePoint-Front-End-Webserver und Exchange-Clientzugriffsserver (Client Access Server, CAS). Diese Topologie zeigt VIP-Komponenten für Lync, SharePoint und Exchange im Lastenausgleichsmodul. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="3ce03-203">Server</span><span class="sxs-lookup"><span data-stu-id="3ce03-203">Servers</span></span>

<span data-ttu-id="3ce03-p121">Es gibt vier Servern: Lync, SharePoint, Exchange und Office Web Apps Server. Jeder Server kann haben drei Ebenen: Front-End, Clientzugriff Tier, eine Anwendungsebene und eine Datenbank-Speicherung Schicht.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="3ce03-206">Front-End-Clientzugriffsebene</span><span class="sxs-lookup"><span data-stu-id="3ce03-206">Front-end, client-access tier</span></span>

<span data-ttu-id="3ce03-207">Diese Ebene verfügt über Komponenten auf allen vier Servern: </span><span class="sxs-lookup"><span data-stu-id="3ce03-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="3ce03-p122">Lync-Pool (Front-End). Das Diagramm zeigt zwei Lync-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="3ce03-p123">SharePoint-Front-End und verteilter Cache. Das Diagramm zeigt drei SharePoint-Datenbanken.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="3ce03-p124">Exchange CAS. Das Diagramm zeigt zwei Exchange-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="3ce03-p125">Office Web Apps Server. Das Diagramm zeigt zwei Office Web Apps-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="3ce03-216">Anwendungsebene</span><span class="sxs-lookup"><span data-stu-id="3ce03-216">Application tier</span></span>

<span data-ttu-id="3ce03-217">Diese Ebene verfügt nur über Komponenten auf dem SharePoint-Server: </span><span class="sxs-lookup"><span data-stu-id="3ce03-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="3ce03-p126">Suche (Abfrage, Index, Administration). Das Diagramm zeigt drei SharePoint-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="3ce03-p127">Batchverarbeitung. Das Diagramm zeigt drei SharePoint-Datenbanken.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="3ce03-222">Datenbank-/Speicherebene</span><span class="sxs-lookup"><span data-stu-id="3ce03-222">Database/storage tier</span></span>

<span data-ttu-id="3ce03-223">Diese Ebene verfügt über Komponenten auf dem Lync-, SharePoint- und Exchange-Server: </span><span class="sxs-lookup"><span data-stu-id="3ce03-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="3ce03-p128">Lync-Datenbank (Back-End). Das Diagramm zeigt drei Lync-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="3ce03-p129">SharePoint-Datenbank. Das Diagramm zeigt drei SharePoint-Datenbanken. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="3ce03-p130">Exchange-Postfachserver. Das Diagramm zeigt zwei Exchange-Postfachserver. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="3ce03-230">Weitere Informationen zu den Komponenten, die auf jedem SharePoint-Server-Rollen installiert finden Sie unter [Optimierte Topologien für SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="3ce03-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="3ce03-231">Beschreibung des Datenverkehrsflusses durch die Komponenten zu den verschiedenen Serverebenen</span><span class="sxs-lookup"><span data-stu-id="3ce03-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="3ce03-232">In diesem Abschnitt wird beschrieben, wie Benutzeranforderungen die Netzwerktopologie durchlaufen.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="3ce03-233">Authentifizierung und Routing für externen Zugriff</span><span class="sxs-lookup"><span data-stu-id="3ce03-233">Authentication and routing for external access</span></span>

<span data-ttu-id="3ce03-234">Es gibt drei verschiedene Clienttypen außerhalb der Netzwerk- und Clouddienste; dazu gehören: </span><span class="sxs-lookup"><span data-stu-id="3ce03-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="3ce03-235">Partnerunternehmen (Business-to-Business) – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="3ce03-236">Einzelne Partner (SharePoint und anonym (Lync)) – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="3ce03-237">Roaming- und Remotemitarbeiter – extern </span><span class="sxs-lookup"><span data-stu-id="3ce03-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="3ce03-238">Der Authentifizierungs- und Routingprozess für die verschiedenen externen Benutzertypen wird einzeln beschrieben. </span><span class="sxs-lookup"><span data-stu-id="3ce03-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="3ce03-239">Partnerunternehmen (Business-to-Business) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="3ce03-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="3ce03-p131">Lync: Verbundvertrauensstellung mit anderen Organisationen, Skype und Verbindungen mit öffentlichen Chatdiensten (PIC) mit AOL. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="3ce03-p132">SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="3ce03-p133">Exchange: Gegenseitige TLS-Authentifizierung (MTSL) für E-Mail-Datenverkehr, SAML-Authentifizierung für Verbundfreigabe. Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="3ce03-246">Der SMTP-Clientdatenverkehr durchläuft den Gatewayrouter und die Exchange-VIP (Lastenausgleich/Reverseproxyserver) zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="3ce03-247">Einzelne Partner (SharePoint) und anonym (Lync) (https://partnerweb.contoso.com und https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="3ce03-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="3ce03-p134">Lync: Anonyme Benutzer können nur solchen Lync-Besprechungen beitreten, die von Mitarbeitern organisiert wurden. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.  </span><span class="sxs-lookup"><span data-stu-id="3ce03-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="3ce03-p135">SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung oder formularbasierter Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="3ce03-252">Exchange: Nicht zutreffend. </span><span class="sxs-lookup"><span data-stu-id="3ce03-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="3ce03-253">Der Lync-Webdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="3ce03-254">Roaming- und Remotemitarbeiter</span><span class="sxs-lookup"><span data-stu-id="3ce03-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="3ce03-255">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="3ce03-256">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="3ce03-257">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="3ce03-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="3ce03-259">https://Mail.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="3ce03-259">https://mail.contoso.com*</span></span> 
    
6. <span data-ttu-id="3ce03-260">https://Dial.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="3ce03-260">https://dial.contoso.com*</span></span>
    
7. <span data-ttu-id="3ce03-261">https://Meet.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="3ce03-261">https://meet.contoso.com*</span></span>
    
* <span data-ttu-id="3ce03-262">Der Exchange-URL weist die folgenden virtuellen Verzeichnisse: AutoErmittlung Ecp, EWS, Microsoft-Server-ActiveSync, OAB Owa, PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce03-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="3ce03-p136">Lync: TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="3ce03-p137">SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft das VPN-Gateway oder den DirectAccess-Server zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="3ce03-p138">Exchange: Standardauthentifizierung über SSL (ActiveSync AutoErmittlung), formularbasierte Authentifizierung (OWA). Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="3ce03-269">Lync-Clientdatenverkehr durchläuft den Gatewayrouter zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="3ce03-270">Authentifizierung für internen Zugriff</span><span class="sxs-lookup"><span data-stu-id="3ce03-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="3ce03-271">Interne Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="3ce03-271">Internal employees</span></span>

> <span data-ttu-id="3ce03-272">https://Intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="3ce03-273">https://Teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="3ce03-274">https://My.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="3ce03-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="3ce03-276">https://Mail.contoso.com *</span><span class="sxs-lookup"><span data-stu-id="3ce03-276">https://mail.contoso.com*</span></span> 
    
> <span data-ttu-id="3ce03-277">https://Dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="3ce03-278">https://Meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="3ce03-279">https://Admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3ce03-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="3ce03-p139">Lync: Kerberos-, TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="3ce03-p140">SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr läuft zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="3ce03-p141">Exchange: AD DS, formularbasierte Authentifizierung. Der Exchange-Clientdatenverkehr läuft zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="3ce03-286">Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="3ce03-287">Cloudbasierter E-Mail-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-287">Cloud-based email traffic</span></span>

<span data-ttu-id="3ce03-288">Die Cloud-basierten Komponente für SMTP-basierte e-Mail-Verkehr umfasst Internet Mail gehostet oder Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="3ce03-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="3ce03-p142">Diese Komponenten leiten E-Mail-Datenverkehr mithilfe von SMTP durch das Netzwerk. Der Datenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="3ce03-291">Legende zum Netzwerkdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-291">Network traffic legend</span></span>

<span data-ttu-id="3ce03-292">Das Legendenfeld enthält eine grafische Darstellung der verschiedenen im Diagramm gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben: </span><span class="sxs-lookup"><span data-stu-id="3ce03-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="3ce03-293">Grüne Linie: Lync SIP Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="3ce03-294">Blaue Linie: Lync-Webdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="3ce03-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="3ce03-295">Violette Linie: SharePoint-Clientdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="3ce03-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="3ce03-296">Orangefarbene Linie: Exchange-Clientdatenverkehr </span><span class="sxs-lookup"><span data-stu-id="3ce03-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="3ce03-297">Graue Linie: Exchange-Postfachserver-Datenverkehr zwischen Exchange lokal und Exchange Online Protection. </span><span class="sxs-lookup"><span data-stu-id="3ce03-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="3ce03-298">Die verschiedenen Datenverkehrstypen und die von ihnen verwendeten Ports werden ebenfalls im Legendenfeld beschrieben. </span><span class="sxs-lookup"><span data-stu-id="3ce03-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="3ce03-299">Lync-SIP-Datenverkehr und Lync-Webdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="3ce03-300">Der Lync-Edgeserver verwendet die folgenden Ports für die Kommunikation mit externen Benutzern:  </span><span class="sxs-lookup"><span data-stu-id="3ce03-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="3ce03-301">Signale/Chatdatenverkehr (SIP/SIMPLE): TCP-Port 443 (für eingehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="3ce03-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="3ce03-302">Datenverkehr von Webkonferenzen (PSOM): TCP-Port 443 (für eingehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="3ce03-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="3ce03-303">A/V-Datenverkehr (SRTP): TCP 443, UDP 3478 und TCP 50000-59999 (optional) (für eingehenden und ausgehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="3ce03-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="3ce03-304">Der Lync-Edgeserver verwendet die folgenden Ports für die Verbundkommunikation:  </span><span class="sxs-lookup"><span data-stu-id="3ce03-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="3ce03-305">TCP-Ports 5061 (SIP), 5269 (XMPP), 443 und UDP 3478 (SRTP) (für eingehenden und ausgehenden Datenverkehr geöffnet) </span><span class="sxs-lookup"><span data-stu-id="3ce03-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="3ce03-306">SharePoint-Clientdatenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-306">SharePoint client traffic</span></span>

<span data-ttu-id="3ce03-p143">SharePoint kann den TCP-Port 443 (SSL) für die verschlüsselte Kommunikation zwischen dem Client und dem Lastenausgleichsmodul nutzen. Für den externen Zugriff aus dem Internet muss dieser Port für ein- und ausgehenden Datenverkehr auf dem Gatewayrouter (oder in der externen Firewall) geöffnet werden. </span><span class="sxs-lookup"><span data-stu-id="3ce03-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="3ce03-309">Exchange-Clientdatenverkehr und Exchange-Postfachserver-Datenverkehr</span><span class="sxs-lookup"><span data-stu-id="3ce03-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="3ce03-p144">Exchange verwendet TCP-Port 25 (SMTP) für die Server-zu-Server-Kommunikation. Die meisten Client-Verkehr (OWA, ActiveSync, AutoErmittlung, Outlook Anywhere) erfolgt über Port 443 (HTTPS). Falls Sie POP oder IMAP-Clients, werden diese Clients unterstützen außerdem Ports 110 (POP3), 995 (verschlüsselte POP3), 143 (IMAP4), 993 (verschlüsselte IMAP4) und 587 (SMTP) verwendet.</span><span class="sxs-lookup"><span data-stu-id="3ce03-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="3ce03-313">Weitere Informationen zum Lync-Netzwerkdatenverkehr?</span><span class="sxs-lookup"><span data-stu-id="3ce03-313">More on Lync network traffic?</span></span>

<span data-ttu-id="3ce03-p145">Erfahren Sie, wie Lync Server Ihrer Organisation Sofortnachrichten, Webkonferenzen, Anwendungsfreigabe und Sprachkommunikation bereitstellen können. Weitere Informationen finden Sie unter [Microsoft Lync Server 2013 Protokollarbeitsauslastungen](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="3ce03-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="3ce03-316">Das Poster enthält auch einen QR-Code zum Zugreifen auf diese Informationen. </span><span class="sxs-lookup"><span data-stu-id="3ce03-316">The poster also includes a QR code to access this information.</span></span> 
  

