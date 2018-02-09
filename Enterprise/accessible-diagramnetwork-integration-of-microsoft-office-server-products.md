---
title: "Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Netzwerkintegration von Microsoft Office-Serverprodukten“."
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Zugängliches Diagramm – Netzwerkintegration von Microsoft Office-Serverprodukten

**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen Netzwerk Integration von Microsoft Office Server-Produkten.
  
Dieses Poster enthält eine allgemeine Darstellung einer Netzwerk-Umgebung, die Lync Server 2013, SharePoint 2013 und Exchange Server 2013 enthält. Außerdem wird veranschaulicht, die folgenden-Elementen, die für diese Produkte sind: Remote- und internen Zugriff, Authentifizierung, Datenverkehr zwischen Clients und routing des Datenverkehrs über freigegebene Geräte. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Allgemeine Konzepte für Lync, Exchange, SharePoint Server und Office Web Apps

### <a name="about-the-design"></a>Informationen zum Entwurf

#### <a name="streamlined-network-design"></a>Optimierter Netzwerkentwurf

Diese Topologie veranschaulicht die Bereitstellung einer lokalen Netzwerk von SharePoint 2013, Exchange Server 2013 und Lync Server 2013. Es wird auch die Verwendung von Microsoft Cloud-basierten Dienst, Exchange Online Protection, die aus dem Internet Spam und Malware Protection für eingehenden Datenverkehr von Simple Mail Transfer Protocol (SMTP) bereitstellt. 
  
Dieser Netzwerkentwurf wurde optimiert und enthält nur ein Minimum von Netzwerkfeatures. Der Entwurf berücksichtigt keine zusätzlichen Sicherheits- oder Infrastrukturfeatures, die in einigen Organisationen möglicherweise erforderlich sind.   
  
Informationen zu diesem Diagramm:  
  
- Es enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht.   
    
- Es zeigt die Verwendung optionaler RAS-Server, z. B. eines Drittanbieter-VPN-Gateways oder DirectAccess-Servers, um Roaming- oder Remotemitarbeitern eine sichere Kommunikation zu ermöglichen.  
    
- Es beschreibt ausführlich den SharePoint-, Exchange- und Lync-Datenverkehrsfluss vom Client zu den einzelnen Plattformserverebenen.  
    
- Es gibt den Typ der Verbindung für Remote- oder internen Zugriff auf Basis von Client (z. B. Partner oder Mitarbeiter) und verwendeter Authentifizierungsmethode an.  
    
- Bricht die SharePoint, Exchange und Lync-Plattformen von erforderlichen Serverrollen, die der Front-End, Anwendung, Datenbank und anderen Ebenen identifiziert. 
    
Die hier für SharePoint, Lync und Exchange verwendete Architektur ist keine bevorzugte Methode zur Implementierung dieser Plattformen. Sie dient lediglich als Beispiel, da sich Topologien basierend auf den jeweiligen Netzwerkanforderungen und Sicherheitsaspekten unterscheiden.  
  
#### <a name="gateway-router"></a>Gatewayrouter

Bei dieser Topologie befindet sich der Gatewayrouter am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet. Alternativ können auch andere Komponenten vorhanden sein, die die Lücke zwischen dem Gatewayrouter und dem dargestellten Lastenausgleich schließen, z. B. mehrere Firewallebenen. Diese Topologie stellt nur eine von vielen Möglichkeiten zur Bereitstellung Ihres Netzwerks dar. In dieser Konfiguration ist das Gateway mit Zugriffssteuerungslisten (Access Control Lists, ACLs) konfiguriert, um ganz bestimmten eingehenden und ausgehenden IP-basierten Datenverkehr an den Routerschnittstellen zuzulassen. ACLs, erweiterte Überprüfung oder Netzwerkadressenübersetzung (Network Address Translation, NAT) können auch auf anderen Geräten im Netzwerk ausgeführt werden, z. B. Firewalls.  
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Lastenausgleich und Reverseproxygeräte

Sie können Hardware- oder lastenausgleichslösungen zur Umleitung von Datenverkehr für Segmente, einschließlich SharePoint-Front-End-Servern und Exchange-Clientzugriffsserver (CASs) verwenden. In einigen Fällen ist es optimal ein Layer 7 hardwarebasierten Lastenausgleich für Persistenz Anforderungen verwenden, wie sie mithilfe der Informationen in der Anforderung, z. B. Cookies oder Kopfzeilen besser ausführen kann. Allerdings Faktoren, wie Kosten und verbesserte Auslastung und Arbeitslast aus einer solchen Lösung ist möglicherweise nicht für Ihre Bedürfnisse wünschenswert. Berücksichtigen Sie die folgenden Punkte für einen Lastenausgleich für SharePoint, Exchange und Lync: 
  
- SharePoint - für SharePoint 2013, nicht müssen Sie Affinität für Ihre Front-End-Server zu aktivieren. In der Regel würde dies für Kurznotiz Sitzungen erstellen und Vermeiden von mehreren authentifizierungsanforderungen von Clients auf jedem Front-End-Webserver verwendet werden. Der neue verteilten Cachedienst in SharePoint 2013 speichert und verteilt die Anmeldung Token auf den Webservern der SharePoint-Farm. 
    
- Exchange - In Exchange 2013 der CAS-Rolle soll Layer 4-Lastenausgleich, Anfragen auf der Transportschicht verteilen. Dies kann erheblich Load Balancer Auslastung und Arbeitslast reduziert werden. 
    
- Lync - System DNS (Domain Name) des Lastenausgleichs für Session Initiation Protocol (SIP) Datenverkehr für Lync-Pools empfohlen. Hardwaregeräte zum Lastenausgleich (Hardwarelastenausgleich) ist für Datenverkehr von Lync Web (HTTPS) erforderlich. 
    
### <a name="remote-access-options"></a>Remotezugriffsoptionen

Es gibt mehrere Möglichkeiten, um Intranetressourcen für Partner im Internet zu veröffentlichen oder sicheren Remotezugriff für Remote- oder Roamingmitarbeiter bereitzustellen. Beispiele hierfür sind Reverseproxys, DirectAccess und Drittanbieter-VPN-Gateways. Die weiter unten in diesem Abschnitt erläuterten Remotezugriffslösungen sind Möglichkeiten für SharePoint, Lync und Exchange oder eine beliebige Kombination dieser Server in einer lokalen Bereitstellung. Einige Remoteoptionen können jedoch möglicherweise mit einer bestimmten Lösung nicht verwendet werden.   
  
Reverseproxy - Reverseproxy unterstützt Datenverkehr Verschlüsselung, wie Secure Sockets Layer (SSL), und mit, die Sie Intranet Applications und Webressourcen zu veröffentlichen können authentifizierten Benutzern und Partnern im Internet. Ein Beispiel ist Microsoft Forefront Unified Access Gateway (UAG). Viele Hardwaregeräte zum Lastenausgleich unterstützt auch Reverseproxy-Funktionen. Es gibt jedoch noch gültige Szenarien für die Verwendung einer eigenständigen Lösung basierend auf Ihren Anforderungen und Anforderungen, beispielsweise zur Optimierung der Leistung, Sicherheit Aufgliederung und Datenverkehr Isolation. 
  
Reverseproxy – Vorteile und Überlegungen:  
  
- Ermöglicht Partnern oder Benutzern den authentifizierten und sicheren Zugriff auf Intranetressourcen (verwendet SSL (TCP 443) zwischen Client und Reverseproxyserver).  
    
- Für Exchange bietet die Verwendung eines Reverseproxys wie z. B. Forefront UAG z. B. den Vorteil, dass vor dem Zugriff auf den Exchange-Clientzugriffsserver eine Vorauthentifizierung stattfindet. Remotezugriffsbenutzer, die veröffentlichte Anwendungen wie Outlook Web Access (OWA) verwenden, können sich mit der Standard-, NTLM- oder Kerberos-Methode authentifizieren, bevor sie das interne Netzwerk erreichen.  
    
- Für Exchange und SharePoint können Lösungen wie Forefront UAG SSL-Verbindungen beenden und die Auslastung des Intranetressourcenservers verringern, während gleichzeitig eine zentrale Verwaltung von Zertifikaten möglich ist.  
    
- Für Lync durchläuft Reverseproxy (TCP 443) für die Clientkommunikation Web (HTTPS)-Datenverkehr. Der Reverseproxy-Proxys der HTTPS Verbindung mit Lync Web Services, Exchange-Clientzugriffsserver und Office Web Apps. Lync Server 2013 unterstützt UAG nicht. 
    
DirectAccess - eine RAS-Technologie, die internetprotokollsicherheit (IPsec) für die Authentifizierung und zum Verschlüsseln von Datenverkehr zwischen dem DirectAccess-Client und Server verwendet. DirectAccess bietet gleichzeitigen Zugriff auf Internet und Intranet Ressourcen für servergespeicherte und Remotemitarbeiter, ohne eine Verbindung zu initiieren. 
  
Überlegungen zu DirectAccess:  
  
- DirectAccess verwendet IPsec-geschützten Datenverkehr (Protokoll 50 und 51 sowie UDP 500) zwischen dem DirectAccess-Client und dem Server.  
    
- DirectAccess für Windows Server 2012 und Windows 8 erfordert keine Bereitstellung einer Public Key-Infrastruktur (PKI) für die Server- und Clientauthentifizierung.  
    
- Es wird empfohlen, vor der Verwendung von DirectAccess aufgrund von Audio- und Videodaten Wartezeitprobleme im Zusammenhang mit IPSec-Verschlüsselung und Entschlüsselung mit Lync Server 2013. 
    
    VPN-Gateway - Typische VPN-Gateways bieten eine RAS-Verbindung in der ein RAS-Clientcomputer logisch auf im Intranet über eine Verbindung getunnelte und vom Benutzer initiierte projiziert wird. Unified RAS-Dienst in Windows Server 2012 oder mehrere Drittanbieter-Lösungen können Sie die gesicherten Zugriff auf das Intranet für roaming oder remote Mitarbeiter bereitstellen können. VPN wird für Lync nicht empfohlen. Remote-Lync-Datenverkehr sollte verwenden Sie die Edge-Server und gleichzeitig kann split-tunneling. 
    
### <a name="domain-name-system-dns-considerations"></a>Überlegungen zu DNS (Domain Name System)

Sie müssen alle DNS-Einträge, die sowohl Internet- als auch Intranetbenutzer zulassen, so konfigurieren, dass sie DNS-Namen in die entsprechenden IP-Adressen auflösen.  
  
- Für internetbasierte Partner und Roaming- oder Remotemitarbeiter bieten DNS-Einträge, die bei Internet-DNS-Servern registriert sind, nach Bedarf Auflösung in den Satz öffentlicher IP-Adressen für den Gatewayrouter, den Lync-Edgeserver, den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul sowie das DirectAccess- oder VPN-Gateway.  
    
- Für intranetbasierte Benutzer bieten DNS-Einträge, die bei Intranet-DNS-Servern registriert sind, die Auflösung in den Satz virtueller IP-Adressen (VIPs) auf dem Lastenausgleichsmodul für den Zugriff auf Exchange-, SharePoint- und Lync-Ressourcen.  
    
- DirectAccess-Clients verwenden Intranet-DNS-Server für Namen, die dem Intranet-DNS-Namespace entsprechen, und Internet-DNS-Server für die übrigen Namen. Um die Funktion von DirectAccess zu vereinfachen, erwägen Sie die Verwendung einer geteilten DNS-Implementierung mit unterschiedlichen DNS-Namespaces für intranet- und internetbasierte Namen. Verwenden Sie z. B. „contoso.com“ für den Internetnamespace und „corp.contoso.com“ für den Intranetnamespace.  
    
- Exchange verwendet ein geteiltes DNS-Modell, bei dem sich die Auflösung von Host in IP für öffentlich weitergeleiteten Datenverkehr von der im Unternehmensnetzwerk unterscheidet. Sie benötigen zumindest DNS-Einträge für OWA, AutoErmittlung, ActiveSync-URLs für Clientdatenverkehr und einen MX-Eintrag für eingehende Nachrichten.  
    
- Wenn Sie Exchange Online Protection (EOP) verwenden, zeigt Ihr MX-Eintrag auf diesen Dienst anstatt auf die Exchange-Farm.  
    
- Für Exchange benötigen Sie einen TXT-Eintrag als Besitznachweis in Ihrem öffentlichen DNS und eine Verbundorganisations-ID zum Einrichten der Verbundfreigabe.  
    
- VPN-Remotezugriffsclients können so konfiguriert werden, dass sie nur Intranet-DNS-Server verwenden, wenn die VPN-Remotezugriffsverbindung aktiv ist.  
    
### <a name="diagram-description"></a>Diagrammbeschreibung

Dieses Diagramm enthält eine Beispielnetzwerktopologie, die den eingehenden und ausgehenden Datenverkehr über einen Gatewayrouter und den Lastenausgleich von Clientsitzungsdatenverkehr (extern und intern) an die entsprechenden SharePoint-, Exchange- und Lync-Serverebenen veranschaulicht. Die Beschreibung dieses Diagramms ist in zwei Teile unterteilt:  
  
- Beschreibung der im Diagramm dargestellten Komponenten  
    
- Beschreibung des Datenverkehrsflusses durch die Komponenten zu den SharePoint-, Exchange-, Lync- und Office Web Apps-Serverebenen  
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Beschreibung der im Diagramm dargestellten Komponenten 

#### <a name="user-types"></a>Benutzertypen

Es gibt vier verschiedene Benutzertypen, drei außerhalb der Netzwerk- und Clouddienste und einen internen; dazu gehören:  
  
- Partnerunternehmen (Business-to-Business) – extern  
    
- Einzelne Partner (SharePoint und anonym (Lync)) – extern  
    
- Roaming- und Remotemitarbeiter – extern  
    
- Interne Mitarbeiter 
    
#### <a name="cloud-based-email-traffic"></a>Cloudbasierter E-Mail-Datenverkehr

Es gibt eine cloudbasierte Komponente für SMTP-basierten E-Mail-Datenverkehr, entweder Internet-Mail-Hosts oder Exchange Online Protection.  
  
#### <a name="authentication-for-external-access"></a>Authentifizierung für externen Zugriff

Für jeden der Benutzertypen gibt es einen bestimmten Satz von Authentifizierungsverfahren für Lync, SharePoint und Exchange. Diese werden an späterer Stelle in diesem Thema genauer erläutert.  
  
#### <a name="gateway-router-with-acls"></a>Gatewayrouter mit ACLs

Der Gatewayrouter befindet sich am Rand des Netzwerks und leitet den gesamten eingehenden und ausgehenden Datenverkehr in das bzw. aus dem Intranet.  
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>RAS-Server für Lync und SharePoint

Diese Topologie umfasst einen Lync-Edgeserver und ein SharePoint-VPN-Gateway oder einen DirectAccess-Server.  
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Lastenausgleich und Reverseproxygerät

Sie können Hardware- oder Softwarelösungen für den Lastenausgleich verwenden, um Datenverkehr für Segmente umzuleiten, z. B. SharePoint-Front-End-Webserver und Exchange-Clientzugriffsserver (Client Access Server, CAS). Diese Topologie zeigt VIP-Komponenten für Lync, SharePoint und Exchange im Lastenausgleichsmodul.  
  
#### <a name="servers"></a>Server

Es gibt vier Servern: Lync, SharePoint, Exchange und Office Web Apps Server. Jeder Server kann haben drei Ebenen: Front-End, Clientzugriff Tier, eine Anwendungsebene und eine Datenbank-Speicherung Schicht.
  
#### <a name="front-end-client-access-tier"></a>Front-End-Clientzugriffsebene

Diese Ebene verfügt über Komponenten auf allen vier Servern:  
  
- Lync-Pool (Front-End). Das Diagramm zeigt zwei Lync-Datenbanken.  
    
- SharePoint-Front-End und verteilter Cache. Das Diagramm zeigt drei SharePoint-Datenbanken.   
    
- Exchange CAS. Das Diagramm zeigt zwei Exchange-Datenbanken.  
    
- Office Web Apps Server. Das Diagramm zeigt zwei Office Web Apps-Datenbanken.  
    
#### <a name="application-tier"></a>Anwendungsebene

Diese Ebene verfügt nur über Komponenten auf dem SharePoint-Server:  
  
- Suche (Abfrage, Index, Administration). Das Diagramm zeigt drei SharePoint-Datenbanken.  
    
- Batchverarbeitung. Das Diagramm zeigt drei SharePoint-Datenbanken.   
    
#### <a name="databasestorage-tier"></a>Datenbank-/Speicherebene

Diese Ebene verfügt über Komponenten auf dem Lync-, SharePoint- und Exchange-Server:  
  
- Lync-Datenbank (Back-End). Das Diagramm zeigt drei Lync-Datenbanken.  
    
- SharePoint-Datenbank. Das Diagramm zeigt drei SharePoint-Datenbanken.  
    
- Exchange-Postfachserver. Das Diagramm zeigt zwei Exchange-Postfachserver.  
    
Weitere Informationen zu den Komponenten, die auf jedem SharePoint-Server-Rollen installiert finden Sie unter [Optimierte Topologien für SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Beschreibung des Datenverkehrsflusses durch die Komponenten zu den verschiedenen Serverebenen

In diesem Abschnitt wird beschrieben, wie Benutzeranforderungen die Netzwerktopologie durchlaufen.   
  
#### <a name="authentication-and-routing-for-external-access"></a>Authentifizierung und Routing für externen Zugriff

Es gibt drei verschiedene Clienttypen außerhalb der Netzwerk- und Clouddienste; dazu gehören:  
  
- Partnerunternehmen (Business-to-Business) – extern  
    
- Einzelne Partner (SharePoint und anonym (Lync)) – extern  
    
- Roaming- und Remotemitarbeiter – extern  
    
Der Authentifizierungs- und Routingprozess für die verschiedenen externen Benutzertypen wird einzeln beschrieben.  
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Partnerunternehmen (Business-to-Business) (https://partnerweb.contoso.com)

- Lync: Verbundvertrauensstellung mit anderen Organisationen, Skype und Verbindungen mit öffentlichen Chatdiensten (PIC) mit AOL. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.  
    
- SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server.  
    
- Exchange: Gegenseitige TLS-Authentifizierung (MTSL) für E-Mail-Datenverkehr, SAML-Authentifizierung für Verbundfreigabe. Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server.  
    
- Der SMTP-Clientdatenverkehr durchläuft den Gatewayrouter und die Exchange-VIP (Lastenausgleich/Reverseproxyserver) zum Exchange-Server.  
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Einzelne Partner (SharePoint) und anonym (Lync) (https://partnerweb.contoso.com und https://meet.contoso.com)

- Lync: Anonyme Benutzer können nur solchen Lync-Besprechungen beitreten, die von Mitarbeitern organisiert wurden. Der Lync-Verbunddatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.   
    
- SharePoint: Vertrauenswürdiger Partneridentitätsanbieter mit SAML-Authentifizierung oder formularbasierter Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft den Gatewayrouter zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server.  
    
- Exchange: Nicht zutreffend.  
    
- Der Lync-Webdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server.  
    
#### <a name="roaming-and-remote-employees"></a>Roaming- und Remotemitarbeiter

1. https://Intranet.contoso.com 
    
2. https://Teams.contoso.com 
    
3. https://My.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://Mail.contoso.com * 
    
6. https://Dial.contoso.com *
    
7. https://Meet.contoso.com *
    
* Der Exchange-URL weist die folgenden virtuellen Verzeichnisse: AutoErmittlung Ecp, EWS, Microsoft-Server-ActiveSync, OAB Owa, PowerShell 
  
- Lync: TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr durchläuft den Gatewayrouter zum Lync-Edgeserver, zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.  
    
- SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr durchläuft das VPN-Gateway oder den DirectAccess-Server zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server.  
    
- Exchange: Standardauthentifizierung über SSL (ActiveSync AutoErmittlung), formularbasierte Authentifizierung (OWA). Der Exchange-Clientdatenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server.  
    
- Lync-Clientdatenverkehr durchläuft den Gatewayrouter zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server.  
    
#### <a name="authentication-for-internal-access"></a>Authentifizierung für internen Zugriff

#### <a name="internal-employees"></a>Interne Mitarbeiter

> https://Intranet.contoso.com 
    
> https://Teams.contoso.com 
    
> https://My.contoso.com
    
> https://partnerweb.contoso.com
    
> https://Mail.contoso.com * 
    
> https://Dial.contoso.com 
    
> https://Meet.contoso.com
    
> https://Admin.contoso.com
    
- Lync: Kerberos-, TLS-DSK- oder NTLM-Authentifizierung. Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Lync-Server.  
    
- SharePoint: Active Directory-Domänendienste (AD DS), formularbasierte Authentifizierung oder SAML-Authentifizierung. Der SharePoint-Clientdatenverkehr läuft zur SharePoint-VIP (Lastenausgleich/Reverseproxyserver) und dann zum SharePoint-Server.  
    
- Exchange: AD DS, formularbasierte Authentifizierung. Der Exchange-Clientdatenverkehr läuft zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server.  
    
- Der Lync-Clientdatenverkehr läuft zur Lync-VIP (Lastenausgleich/Reverseproxyserver), zu einem Hardwaregerät zum Lastenausgleich (HLB), das für HTTPS-Datenverkehr erforderlich ist, und dann zum Lync-Server.  
    
#### <a name="cloud-based-email-traffic"></a>Cloudbasierter E-Mail-Datenverkehr

Die Cloud-basierten Komponente für SMTP-basierte e-Mail-Verkehr umfasst Internet Mail gehostet oder Exchange Online Protection.
  
Diese Komponenten leiten E-Mail-Datenverkehr mithilfe von SMTP durch das Netzwerk. Der Datenverkehr durchläuft den Gatewayrouter zur Exchange-VIP (Lastenausgleich/Reverseproxyserver) und dann zum Exchange-Server.  
  
### <a name="network-traffic-legend"></a>Legende zum Netzwerkdatenverkehr

Das Legendenfeld enthält eine grafische Darstellung der verschiedenen im Diagramm gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben:  
  
- Grüne Linie: Lync SIP Datenverkehr 
    
- Blaue Linie: Lync-Webdatenverkehr  
    
- Violette Linie: SharePoint-Clientdatenverkehr  
    
- Orangefarbene Linie: Exchange-Clientdatenverkehr  
    
- Graue Linie: Exchange-Postfachserver-Datenverkehr zwischen Exchange lokal und Exchange Online Protection.  
    
Die verschiedenen Datenverkehrstypen und die von ihnen verwendeten Ports werden ebenfalls im Legendenfeld beschrieben.  
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync-SIP-Datenverkehr und Lync-Webdatenverkehr

Der Lync-Edgeserver verwendet die folgenden Ports für die Kommunikation mit externen Benutzern:   
  
- Signale/Chatdatenverkehr (SIP/SIMPLE): TCP-Port 443 (für eingehenden Datenverkehr geöffnet)  
    
- Datenverkehr von Webkonferenzen (PSOM): TCP-Port 443 (für eingehenden Datenverkehr geöffnet)  
    
- A/V-Datenverkehr (SRTP): TCP 443, UDP 3478 und TCP 50000-59999 (optional) (für eingehenden und ausgehenden Datenverkehr geöffnet)  
    
Der Lync-Edgeserver verwendet die folgenden Ports für die Verbundkommunikation:   
  
- TCP-Ports 5061 (SIP), 5269 (XMPP), 443 und UDP 3478 (SRTP) (für eingehenden und ausgehenden Datenverkehr geöffnet)  
    
#### <a name="sharepoint-client-traffic"></a>SharePoint-Clientdatenverkehr

SharePoint kann den TCP-Port 443 (SSL) für die verschlüsselte Kommunikation zwischen dem Client und dem Lastenausgleichsmodul nutzen. Für den externen Zugriff aus dem Internet muss dieser Port für ein- und ausgehenden Datenverkehr auf dem Gatewayrouter (oder in der externen Firewall) geöffnet werden.  
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange-Clientdatenverkehr und Exchange-Postfachserver-Datenverkehr

Exchange verwendet TCP-Port 25 (SMTP) für die Server-zu-Server-Kommunikation. Die meisten Client-Verkehr (OWA, ActiveSync, AutoErmittlung, Outlook Anywhere) erfolgt über Port 443 (HTTPS). Falls Sie POP oder IMAP-Clients, werden diese Clients unterstützen außerdem Ports 110 (POP3), 995 (verschlüsselte POP3), 143 (IMAP4), 993 (verschlüsselte IMAP4) und 587 (SMTP) verwendet. 
  
#### <a name="more-on-lync-network-traffic"></a>Weitere Informationen zum Lync-Netzwerkdatenverkehr?

Erfahren Sie, wie Lync Server Ihrer Organisation Sofortnachrichten, Webkonferenzen, Anwendungsfreigabe und Sprachkommunikation bereitstellen können. Weitere Informationen finden Sie unter [Microsoft Lync Server 2013 Protokollarbeitsauslastungen](https://aka.ms/G5jzjo). 
  
Das Poster enthält auch einen QR-Code zum Zugreifen auf diese Informationen.  
  

