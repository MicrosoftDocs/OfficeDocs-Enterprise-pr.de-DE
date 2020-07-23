---
title: Prinzipien von Microsoft 365-Netzwerkverbindungen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Bevor Sie mit der Planung Ihres Netzwerks für die Office 365-Netzwerkkonnektivität beginnen, ist es wichtig, dass Sie sich mit den Prinzipien von Verbindungen für die sichere Verwaltung von Office 365-Datenverkehr und optimaler Leistung vertraut machen. Dieser Artikel hilft Ihnen, die neuesten Hinweise für die sichere Optimierung der Office 365-Netzwerkkonnektivität zu verstehen.
ms.openlocfilehash: 83743bfcb7a2bd3ba137947b7eb65d159d039b25
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230291"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Prinzipien von Microsoft 365-Netzwerkverbindungen

*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*

Bevor Sie mit der Planung Ihres Netzwerks für die Microsoft 365-Netzwerkkonnektivität beginnen, müssen Sie sich mit den Grundlagen der Konnektivität vertraut machen, um den Microsoft 365-Datenverkehr sicher zu verwalten und die bestmögliche Leistung zu erzielen. In diesem Artikel erhalten Sie Informationen zu den neuesten Richtlinien für die sichere Optimierung der Netzwerkkonnektivität von Microsoft 365.
  
Herkömmliche Unternehmensnetzwerke sind in erster Linie für den Zugriff von Benutzern auf Anwendungen und Daten ausgelegt, die in unternehmenseigenen Rechenzentren mit hoher Perimetersicherheit gehostet werden. Das herkömmliche Modell setzt voraus, dass Benutzer auf Anwendungen und Daten innerhalb des Perimeters des Unternehmensnetzwerks über WAN-Links von Zweigniederlassungen aus oder remote über VPN-Verbindungen zugreifen.
  
Durch die Einführung von SaaS-Anwendungen wie Microsoft 365 wird eine Kombination von Diensten und Daten außerhalb des Netzwerkperimeters verschoben. Ohne Optimierung wird der Datenverkehr zwischen Benutzern und SaaS-Anwendungen durch Latenzen durch die Paketüberprüfung, Spitzkehren für Netzwerke, versehentliche Verbindungen zu geographisch entfernten Endpunkten und andere Faktoren beeinträchtigt. Sie können die beste Leistung und Zuverlässigkeit von Microsoft 365 sicherstellen, indem Sie wichtige Optimierungsrichtlinien verstehen und implementieren.
  
In diesem Artikel werden die folgenden Themen behandelt:
  
- [Microsoft 365-Architektur](office-365-network-connectivity-principles.md#BKMK_Architecture) für Kunden Konnektivität mit der Cloud
- Aktualisierte [Microsoft 365-Konnektivitäts Prinzipien](office-365-network-connectivity-principles.md#BKMK_Principles) und Strategien zur Optimierung des Netzwerkdatenverkehrs und der Benutzeroberfläche
- Der [Office 365-Webdienst für Endpunkte](office-365-network-connectivity-principles.md#BKMK_WebSvc), der es Netzwerkadministratoren ermöglicht, eine strukturierte Liste von Endpunkten für die Netzwerkoptimierung zu verwenden
- [Neue Office 365-Endpunktkategorien](office-365-network-connectivity-principles.md#BKMK_Categories) und Optimierungshinweise
- [Vergleichen der Sicherheit des Netzwerkperimeters mit der Endpunktsicherheit](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Inkrementelle Optimierungs](office-365-network-connectivity-principles.md#BKMK_IncOpt) Optionen für Microsoft 365-Datenverkehr
- Der [Microsoft 365 Connectivity Test](https://aka.ms/netonboard), ein neues Tool zum Testen der grundlegenden Konnektivität mit Microsoft 365

## <a name="microsoft-365-architecture"></a>Microsoft 365-Architektur
<a name="BKMK_Architecture"> </a>

Microsoft 365 ist eine verteilte Software-as-a-Service-Cloud (SaaS), die Produktivitäts-und Zusammenarbeitsszenarien mithilfe einer Vielzahl von Mikro Diensten und Anwendungen bereitstellt, wie Exchange Online, SharePoint Online, Skype for Business Online, Microsoft Teams, Exchange Online Schutz, Office in einem Browser und viele andere. Während bestimmte Microsoft 365-Anwendungen möglicherweise Ihre einzigartigen Features für das Kundennetzwerk und die Konnektivität zur Cloud aufweisen, teilen Sie einige wichtige Prinzipale, Ziele und Architekturmuster. Diese Grundsätze und Architekturmuster für die Konnektivität sind für viele andere Saas-Clouds typisch und unterscheiden sich gleichzeitig von den typischen Bereitstellungsmodellen von Platt Form-as-a-Service-und Infrastruktur-as-a-Service-Clouds wie Microsoft Azure.
  
Eines der bedeutendsten architektonischen Features von Microsoft 365 (das häufig von Netzwerkarchitekten vermisst oder falsch interpretiert wird) besteht darin, dass es sich um einen wahrhaft globalen verteilten Dienst im Kontext der Verbindung von Benutzern handelt. Der Speicherort des Ziel-Microsoft 365-Mandanten ist wichtig, um die Lokalität zu verstehen, in der Kundendaten in der Cloud gespeichert sind, aber die Benutzererfahrung mit Microsoft 365 erfordert keine direkte Verbindung mit Datenträgern, die die Daten enthalten. Die Benutzererfahrung mit Microsoft 365 (einschließlich Leistung, Zuverlässigkeit und anderen wichtigen Qualitätsmerkmalen) umfasst die Konnektivität über hoch verteilte Dienst-Fronttüren, die über Hunderte von Microsoft-Standorten weltweit skaliert werden. In den meisten Fällen wird die beste Benutzererfahrung erzielt, indem das Kundennetzwerk Benutzeranforderungen an den nächstgelegenen Microsoft 365-Dienst Einstiegspunkt weiterleiten kann, anstatt eine Verbindung mit Microsoft 365 über einen Ausgangspunkt an einem zentralen Standort oder einer Region herzustellen.
  
Für die meisten Kunden werden Microsoft 365-Benutzer über viele Standorte verteilt. Um die besten Ergebnisse zu erzielen, sollten die in diesem Dokument dargelegten Prinzipien in der Ansicht horizontal skalieren (nicht horizontal) untersucht werden, wobei der Schwerpunkt auf der Optimierung der Konnektivität mit dem nächstgelegenen Punkt der Anwesenheit im globalen Microsoft-Netzwerk liegt, und nicht auf dem geographischen Standort des Microsoft 365-Mandanten. Im Wesentlichen bedeutet dies, dass, obwohl Microsoft 365-Mandantendaten möglicherweise an einem bestimmten geografischen Standort gespeichert werden, die Microsoft 365-Erfahrung für diesen Mandanten verbreitet bleibt und in sehr enger (Netzwerk-) Nähe zu jedem Endbenutzer Standort vorhanden sein kann, der vom Mandanten verwendet wird.
  
## <a name="microsoft-365-connectivity-principles"></a>Microsoft 365-Konnektivitäts Prinzipien
<a name="BKMK_Principles"> </a>

Microsoft empfiehlt die folgenden Grundsätze, um eine optimale Konnektivität und Leistung von Microsoft 365 zu erreichen. Verwenden Sie diese Microsoft 365-Konnektivitäts Prinzipien, um Ihren Datenverkehr zu verwalten und die beste Leistung zu erzielen, wenn Sie eine Verbindung mit Microsoft 365 herstellen.
  
Das Hauptziel des Netzwerkdesigns sollte sein, die Latenz zu minimieren, indem die RTT (Round Trip Time) von Ihrem Netzwerk zum globalen Microsoft-Netzwerk minimiert wird, welches der öffentliche Netzwerkbackbone von Microsoft ist, der alle Microsoft-Rechenzentren mit geringer Latenz und weltweit verteilten Einstiegspunkten für Cloudanwendungen verbindet. Erfahren Sie mehr über das globale Microsoft-Netzwerk unter [So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identifizieren und differenzieren von Microsoft 365-Datenverkehr

![Identifizieren von Microsoft 365-Datenverkehr](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Das Identifizieren von Microsoft 365-Netzwerkdatenverkehr ist der erste Schritt in der Lage, diesen Datenverkehr von einem generischen, vom Internet gebundenen Netzwerkdatenverkehr zu unterscheiden. Die Microsoft 365-Konnektivität kann durch Implementierung einer Kombination von Ansätzen wie Netzwerkrouten Optimierung, Firewallregeln, Browser Proxyeinstellungen und Umgehung von Netzwerk Inspektionsgeräten für bestimmte Endpunkte optimiert werden.
  
Frühere Microsoft 365-Optimierungs Anleitungen haben Microsoft 365-Endpunkte in zwei Kategorien unterteilt, **erforderlich** und **optional**. Da Endpunkte zur Unterstützung neuer Microsoft 365-Dienste und-Features hinzugefügt wurden, haben wir Microsoft 365-Endpunkte in drei Kategorien umstrukturiert: **optimize**, **Allow**und **default**. Richtlinien für jede Kategorie gelten für alle Endpunkte in der Kategorie, wodurch Optimierungen einfacher zu verstehen und zu implementieren sind.
  
Weitere Informationen zu den Microsoft 365-Endpunkt Kategorien und Optimierungsmethoden finden Sie im Abschnitt [neue Office 365-Endpunkt Kategorien](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft veröffentlicht jetzt alle Microsoft 365-Endpunkte als Webdienst und bietet Anleitungen zur optimalen Verwendung dieser Daten. Weitere Informationen zum Abrufen und arbeiten mit Microsoft 365-Endpunkten finden Sie im Artikel [Office 365 von URLs und IP-Adressbereichen](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Lokaler Ausgang von Netzwerkverbindungen

![Lokaler Ausgang von Netzwerkverbindungen](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokale DNS-und Internet Ausstiege sind von entscheidender Bedeutung, um die Verbindungswartezeit zu verringern und sicherzustellen, dass Benutzer Verbindungen an den nächsten Einstiegspunkt für Microsoft 365-Dienste erfolgen. In einer komplexen Netzwerktopologie ist es wichtig, dass sowohl lokaler DNS- als auch lokaler Internetausgang zusammen implementiert werden. Weitere Informationen dazu, wie Microsoft 365 Clientverbindungen an den nächstgelegenen Einstiegs Ort weiterleitet, finden Sie im Artikel [Client Connectivity](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Vor dem Aufkommen von Cloud-Diensten wie Microsoft 365 war die Endbenutzer-Internet Konnektivität als Entwurfs Faktor in der Netzwerkarchitektur relativ einfach. Wenn Internetdienste und Websites rund um den Globus verteilt sind, wird die Latenz zwischen den Ausgangspunkten des Unternehmens und einem bestimmten Zielendpunkt weitestgehend durch die geografische Entfernung bestimmt.
  
Bei einer herkömmlichen Netzwerkarchitektur durchlaufen alle ausgehenden Internetverbindungen das Unternehmensnetzwerk und gehen von einem zentralen Standort aus. Angesichts ausgereifterer Cloudprodukte von Microsoft ist eine verteilte, mit dem Internet verbundene Netzwerkarchitektur für die Unterstützung latenzsensibler Clouddienste wichtig geworden. Das globale Microsoft-Netzwerk wurde so entwickelt, dass Latenzanforderungen mit der Infrastruktur verteilter Dienst-Front-Doors erfüllt werden. Dabei handelt es sich um eine dynamische Fabric globaler Einstiegspunkte, die eingehende Clouddienst-Verbindungen zum nächstgelegenen Einstiegspunkt weiterleitet. Damit soll die Länge der "letzten Meile" für Microsoft Cloud-Kunden reduziert werden, indem der Weg zwischen dem Kunden und der Cloud effektiv verkürzt wird.
  
Unternehmens-WANs sind häufig so ausgelegt, dass Netzwerkdatenverkehr per Backhauling zur Überprüfung an eine Unternehmenszentrale zurückgeleitet wird, bevor er (in der Regel über einen oder mehrere Proxyserver) ins Internet geroutet wird. Die folgende Abbildung zeigt eine solche Netzwerktopologie.
  
![Herkömmliches Unternehmensnetzwerkmodell](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Da Microsoft 365 im globalen Microsoft-Netzwerk ausgeführt wird, das Front-End-Server auf der ganzen Welt umfasst, gibt es häufig einen Front-End-Server in der Nähe des Standorts des Benutzers. Durch die Bereitstellung des lokalen Internet Ausstiegs und das Konfigurieren interner DNS-Server für die Bereitstellung der lokalen Namensauflösung für Microsoft 365-Endpunkte kann der für Microsoft 365 vorgesehene Netzwerkdatenverkehr eine Verbindung mit Microsoft 365-Front-End-Servern so nahe wie möglich an den Benutzer herstellen. Das folgende Diagramm zeigt ein Beispiel für eine Netzwerktopologie, die es Benutzern ermöglicht, eine Verbindung von der Hauptniederlassung, Zweigstelle und Remotestandorten aus herzustellen, um die kürzeste Route zum nächsten Einstiegs Standort von Microsoft 365 zu erhalten.
  
![WAN-Netzwerkmodell mit regionalen Ausgangspunkten](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Durch die Verkürzung des Netzwerkpfads zu Microsoft 365-Einstiegspunkten auf diese Weise können die Verbindungsleistung und die Endbenutzererfahrung in Microsoft 365 verbessert werden, und Sie können auch dazu beitragen, die Auswirkungen künftiger Änderungen an der Netzwerkarchitektur auf die Leistung und Zuverlässigkeit von Microsoft 365 zu verringern.
  
Außerdem können DNS-Anforderungen zu Wartezeiten führen, wenn sich der antwortende DNS-Server in weiter Entfernung befindet oder ausgelastet ist. Sie können die Wartezeit bei Namensauflösungen minimieren, indem Sie lokale DNS-Server an Zweigstellen bereitstellen und sicherstellen, dass Sie so konfiguriert sind, dass DNS-Einträge entsprechend zwischengespeichert werden.
  
Während regionale Ausgangspunkte für Microsoft 365 gut geeignet sind, besteht das optimale Verbindungsmodell darin, dass immer ein Netzwerk Austritt am Standort des Benutzers bereitgestellt wird, unabhängig davon, ob sich dies im Unternehmensnetzwerk oder an Remotestandorten wie Immobilien, Hotels, Cafés und Flughäfen befinden kann. Dieses Modell mit lokalem direkten Ausgang ist in der nachstehenden Abbildung dargestellt.
  
![Netzwerkarchitektur mit lokalem Ausgang](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Unternehmen, die Microsoft 365 angenommen haben, können die verteilte Dienst-Front-Door-Architektur von Microsoft Global Network nutzen, indem Sie sicherstellen, dass die Benutzer Verbindungen mit Microsoft 365 den kürzesten möglichen Weg zum nächsten Microsoft Global Network-Einstiegspunkt übernehmen. Die lokale Ausgangs Netzwerkarchitektur ermöglicht dies, indem Microsoft 365-Datenverkehr unabhängig vom Standort des Benutzers über den nächsten Ausgang geroutet werden kann.
  
Die Architektur mit lokalem Ausgang bietet gegenüber dem herkömmlichen Modell folgende Vorteile:
  
- Bietet eine optimale Leistung von Microsoft 365 durch Optimierung der Routenlänge. Endbenutzer Verbindungen werden dynamisch an den nächsten Einstiegspunkt von Microsoft 365 durch die verteilte Dienst-Front-Door-Infrastruktur weitergeleitet.
- Verringert die Auslastung der Unternehmensnetzwerkinfrastruktur durch einen lokalen Ausgang
- Gewährleistet die Sicherheit von Verbindungen auf beiden Seiten durch Nutzung von Client-Endpunktsicherheits- und Cloudsicherheitsfunktionen

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Vermeiden von Spitzkehren für Netzwerke

![Vermeiden von Spitzkehren](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Als allgemeine Faustregel bietet die kürzeste, direkteste Route zwischen dem Benutzer und dem nächsten Microsoft 365-Endpunkt die beste Leistung. Eine Netzwerk-Haarnadel tritt auf, wenn der WAN-oder VPN-Datenverkehr, der für ein bestimmtes Ziel gebunden ist, zuerst an einen anderen Zwischenspeicher (beispielsweise Sicherheits Stapel, Cloud-Zugriffs Broker, Cloud-basiertes WebGateway) weitergeleitet wird und die Wartezeit und mögliche Umleitung an einen geografisch entfernten Endpunkt eingeführt wird. Netzwerk-Spitzkehren können auch durch Ineffizienzen beim Routing/Peering oder durch nicht optimale (Remote-)DNS-Suchen verursacht werden.
  
Um sicherzustellen, dass die Microsoft 365-Konnektivität auch im lokalen Ausgangsfall keine Haarnadeln unterliegt, überprüfen Sie, ob der ISP, der zum Bereitstellen des Internets für den Benutzerstandort verwendet wird, über eine direkte Peering-Beziehung mit dem globalen Microsoft-Netzwerk in unmittelbarer Nähe zu diesem Standort verfügt. Möglicherweise möchten Sie auch das Ausgangsrouting so konfigurieren, dass ein vertrauenswürdiger Microsoft 365-Datenverkehr direkt gesendet wird, im Gegensatz zur Proxyfunktion oder zum Tunneln über einen Drittanbieter-Cloud-oder Cloud-basierten Netzwerk Sicherheitsanbieter, der Ihren Internet gebundenen Datenverkehr verarbeitet. Die lokale DNS-Namensauflösung von Microsoft 365-Endpunkten trägt dazu bei, dass neben dem direkten Routing die nächsten Einstiegspunkte von Microsoft 365 für Benutzer Verbindungen verwendet werden.
  
Wenn Sie Cloud-basierte Netzwerk-oder Sicherheitsdienste für Ihren Microsoft 365-Datenverkehr verwenden, müssen Sie sicherstellen, dass das Ergebnis der Haarnadel ausgewertet wird und ihre Auswirkungen auf die Leistung von Microsoft 365 verstanden werden. Dazu müssen Sie die Anzahl und die Standorte von Dienstanbietern, über die der Datenverkehr weitergeleitet wird, im Verhältnis zur Anzahl Ihrer Zweigniederlassungen und den Peering-Punkten des globalen Microsoft-Netzwerks, die Qualität der Netzwerk-Peering-Beziehung des Dienstanbieters mit Ihrem Internetdienstanbieter und Microsoft sowie die Auswirkungen von Backhauling in der Infrastruktur des Dienstanbieters auf die Leistung überprüfen.
  
Aufgrund der großen Anzahl verteilter Standorte mit Microsoft 365 Einstiegspunkten und ihrer Nähe zu Endbenutzern kann das Routing von Microsoft 365-Datenverkehr an ein beliebiges Drittanbieternetzwerk oder einen Sicherheitsanbieter negative Auswirkungen auf Microsoft 365-Verbindungen haben, wenn das Anbieter Netzwerk nicht für ein optimales Microsoft 365-Peering konfiguriert ist.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Bewerten von Umgehungs Proxys, Datenverkehrs Inspektionsgeräten und doppelten Sicherheitstechnologien

![Umgehen von Proxys, Datenverkehrs Inspektionsgeräten und doppelten Sicherheitstechnologien](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Unternehmenskunden sollten ihre Methoden zur Netzwerksicherheit und zur Risikominderung speziell für den Microsoft 365-gebundenen Datenverkehr überprüfen und Microsoft 365-Sicherheitsfeatures verwenden, um die Abhängigkeit von intrusivem, Leistungseinbußen und teuren Netzwerksicherheitstechnologien für den Microsoft 365-Netzwerkdatenverkehr zu verringern.
  
Die meisten Unternehmensnetzwerke erzwingen Netzwerksicherheit für Internetdatenverkehr mithilfe von Technologien wie Proxys, SSL-Prüfung, Paketüberprüfung und Systemen zur Verhinderung von Datenverlust. Diese Technologien bieten eine wichtige Risikominderung für generische Internet Anforderungen, können jedoch die Leistung, die Skalierbarkeit und die Qualität der Endbenutzererfahrung drastisch reduzieren, wenn Sie auf Microsoft 365-Endpunkte angewendet werden.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365-Endpunkte-Webdienst

Microsoft 365-Administratoren können einen Skript-oder Rest-Aufruf verwenden, um eine strukturierte Liste von Endpunkten aus dem Office 365 Endpunkte-Webdienst zu nutzen und die Konfigurationen von Umkreisfirewalls und anderen Netzwerkgeräten zu aktualisieren. Dadurch wird sichergestellt, dass der Datenverkehr für Microsoft 365 identifiziert, entsprechend behandelt und anders gehandhabt wird als der Netzwerkdatenverkehr, der für generische und häufig unbekannte Internet Websites gebunden ist. Weitere Informationen zum Verwenden des Office 365-Endpunkte-Webdienstes finden Sie im Artikel [Office 365-URLs und -IP-Adressbereiche](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC-Skripts (Proxy Automatic Configuration)
<a name="BKMK_WebSvc"> </a>

Microsoft 365-Administratoren können PAC (Proxy Automatic Configuration)-Skripts erstellen, die über WPAD oder GPO an Benutzer Computer übermittelt werden können. PAC-Skripts können verwendet werden, um Proxys für Microsoft 365-Anforderungen von WAN-oder VPN-Benutzern zu umgehen, sodass Microsoft 365-Datenverkehr direkte Internet Verbindungen verwenden kann, anstatt das Unternehmensnetzwerk zu durchlaufen.
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365-Sicherheitsfeatures
<a name="BKMK_WebSvc"> </a>

Microsoft ist für die Sicherheit von Rechenzentren, die Betriebssicherheit und die Risikominimierung rund um Microsoft 365-Server und die Netzwerkendpunkte, die Sie darstellen, transparent. Microsoft 365 integrierte Sicherheitsfunktionen sind verfügbar, um das Netzwerk Sicherheitsrisiko zu reduzieren, beispielsweise Verhinderung von Datenverlust, Virenschutz, mehrstufige Authentifizierung, Kunden Sperr Feld, Advanced Threat Protection, Microsoft 365 Threat Intelligence, Microsoft 365 Secure Score, Exchange Online Protection und Network DDoS Security.
  
Weitere Informationen zur Sicherheit der Rechenzentren und des globalen Netzwerks von Microsoft finden Sie im [Microsoft Trust Center](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Neue Office 365-Endpunktkategorien
<a name="BKMK_Categories"> </a>

Office 365-Endpunkte stellen einen vielfältigen Satz von Netzwerkadressen und Subnetzen dar. Endpunkte sind URLs, IP-Adressen oder IP-Bereiche und einige Endpunkte werden mit bestimmten TCP/UDP-Ports aufgelistet. URLs können entweder ein FQDN wie *Account.Office.net*oder eine Platzhalter-URL wie * \* . office365.com*sein.
  
> [!NOTE]
> Die Speicherorte von Office 365 Endpunkten im Netzwerk beziehen sich nicht direkt auf den Speicherort der Microsoft 365-Mandantendaten. Aus diesem Grund sollten Kunden Microsoft 365 als einen verteilten und globalen Dienst betrachten und nicht versuchen, Netzwerkverbindungen zu Office 365 Endpunkten basierend auf geografischen Kriterien zu blockieren.
  
In unserem vorherigen Leitfaden für die Verwaltung von Microsoft 365-Datenverkehr wurden Endpunkte in zwei Kategorien unterteilt: **erforderlich** und **optional**. Endpunkte innerhalb jeder Kategorie erforderten je nach Kritikalität des Dienstes unterschiedliche Optimierungen und viele Kunden hatten Schwierigkeiten, die Anwendung derselben Netzwerkoptimierungen auf die gesamte Liste der Office 365-URLs und -IP-Adressen zu rechtfertigen.
  
Im neuen Modell werden Endpunkte in drei Kategorien unterteilt: **optimize**, **Allow**und **default**, wobei ein prioritätsbasierter Drehpunkt bereitgestellt wird, in dem die Bemühungen zur Netzwerkoptimierung konzentriert werden, um die besten Leistungsverbesserungen und den Return on Investment zu erzielen. Die Endpunkte werden in den oben aufgeführten Kategorien basierend auf der Sensibilität der effektiven Benutzeroberfläche für Netzwerkqualität, Volumen und Leistungsumfang von Szenarien und der einfachen Implementierung konsolidiert. Auf die gleiche Weise können empfohlene Optimierungen auf alle Endpunkte in der jeweiligen Kategorie angewendet werden.
  
- Endpunkte **optimieren** sind für die Konnektivität mit jedem Office 365 Dienst erforderlich und stellen über 75% der Office 365 Bandbreite, der Verbindungen und des Datenvolumens dar. Diese Endpunkte stellen Office 365 Szenarien dar, die für die Netzwerkleistung, die Wartezeit und die Verfügbarkeit am sensibelsten sind. Alle Endpunkte werden in Microsoft-Rechenzentren gehostet. Die Anzahl der Änderungen an den Endpunkten in dieser Kategorie wird voraussichtlich erheblich geringer sein als bei den Endpunkten in den anderen beiden Kategorien. Diese Kategorie enthält eine kleine (in der Reihenfolge von ~ 10) Gruppe von wichtigen URLs und eine definierte Gruppe von IP-Subnetzen, die für Kern Office 365 Arbeitslasten wie Exchange Online, SharePoint Online, Skype for Business Online und Microsoft Teams dediziert sind.

    Eine verkürzte Liste mit gut definierten kritischen Endpunkten sollte Ihnen helfen, hochwertige Netzwerkoptimierungen für diese Ziele schneller und einfacher zu planen und zu implementieren.

    Beispiele für die *Optimierung* von Endpunkten sind *https://outlook.office365.com* *https:// \<tenant\> . SharePoint.com*und *https:// \<tenant\> -My.SharePoint.com*.

    Zu Optimierungsmethoden zählen folgende:

  - Umgehen Sie die *Optimierung* von Endpunkten für Netzwerkgeräte und-Dienste, die Datenverkehrsüberwachung, SSL-Entschlüsselung, umfassende Paketüberprüfung und Inhaltsfilterung durchführen.
  - Umgehung von lokalen Proxy-Geräten und cloudbasierten Proxy-Diensten, die häufig für allgemeines Browsen im Internet verwendet werden.
  - Priorisieren Sie die Auswertung dieser Endpunkte als vollständig vertrauenswürdig durch Ihre Netzwerkinfrastruktur und Perimetersysteme.
  - Priorisieren Sie die Reduzierung oder Eliminierung von WAN-Rück Transporten, und vereinfachen Sie den direkt verteilten Internet basierten Ausstieg für diese Endpunkte so nah wie möglich an Benutzern/Zweigstellen.
  - Unterstützen Sie die direkte Konnektivität zu diesen Cloud-Endpunkten für VPN-Benutzer durch Implementierung getrennter Tunnel.
  - Stellen Sie sicher, dass die durch die DNS-Namensauflösung zurückgegebenen IP-Adressen dem Routing-Ausgangspfad für diese Endpunkte entsprechen.
  - Priorisieren Sie diese Endpunkte für die SD-WAN-Integration für direktes Routing mit minimaler Latenz in den nächstgelegenen Internet-Peering-Punkt des globalen Microsoft-Netzwerks.

- Endpunkte **zulassen** sind für die Konnektivität mit bestimmten Office 365 Diensten und-Features erforderlich, sind jedoch nicht so anfällig für Netzwerkleistung und Latenz wie in der Kategorie *optimieren* . Die gesamte Netzwerkpräsenz dieser Endpunkte aus der Sicht der Bandbreite und der Anzahl der Verbindungen ist ebenfalls kleiner. Diese Endpunkte sind Office 365 zugeordnet und werden in Microsoft-Rechenzentren gehostet. Sie stellen eine breite Palette von Office 365-Mikrodiensten und deren Abhängigkeiten (von ~ 100-URLs) dar und es ist davon auszugehen, dass sie eine höhere Änderungsrate als diejenigen in der Kategorie *Optimieren* aufweisen. Nicht alle Endpunkte in dieser Kategorie sind definierten dedizierten IP-Subnetzen zugeordnet.

    Netzwerkoptimierungen für *Zulassen*-Endpunkte können das Office 365-Benutzererlebnis verbessern, aber einige Kunden entscheiden sich möglicherweise dazu, diese Optimierungen enger einzugrenzen, um Änderungen am Netzwerk möglichst gering zu halten.

    Beispiele für *Zulassen*-Endpunkte sind etwa *https://\*.protection.outlook.com* und *https://accounts.accesscontrol.windows.net*.

    Zu Optimierungsmethoden zählen folgende:

  - Bypass *Allow* endpoints on Network Devices and Services, die Datenverkehr abhören, SSL-Entschlüsselung, Deep Packet Inspection und Inhaltsfilterung durchführen.
  - Priorisieren Sie die Auswertung dieser Endpunkte als vollständig vertrauenswürdig durch Ihre Netzwerkinfrastruktur und Perimetersysteme.
  - Priorisieren Sie die Reduzierung oder Eliminierung von WAN-Rück Transporten, und vereinfachen Sie den direkt verteilten Internet basierten Ausstieg für diese Endpunkte so nah wie möglich an Benutzern/Zweigstellen.
  - Stellen Sie sicher, dass die durch die DNS-Namensauflösung zurückgegebenen IP-Adressen dem Routing-Ausgangspfad für diese Endpunkte entsprechen.
  - Priorisieren Sie diese Endpunkte für die SD-WAN-Integration für direktes Routing mit minimaler Latenz in den nächstgelegenen Internet-Peering-Punkt des globalen Microsoft-Netzwerks.

- **Standard**-Endpunkte stellen Office 365-Dienste und Abhängigkeiten dar, die keine Optimierung erfordern und von Kundennetzwerken als normaler Internetdatenverkehr behandelt werden können. Einige Endpunkte in dieser Kategorie werden möglicherweise nicht in Microsoft-Datencentern gehostet. Beispiele sind *https://odc.officeapps.live.com* und *https://appexsin.stb.s-msn.com*.

Weitere Informationen zu den Verfahren zur Office 365-Netzwerkoptimierung finden Sie im Artikel [Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Vergleichen der Sicherheit des Netzwerkperimeters mit der Endpunktsicherheit
<a name="BKMK_SecurityComparison"> </a>

Das Ziel der herkömmlichen Netzwerksicherheit ist die Absicherung des Unternehmensnetzwerkperimeters gegen Eindringversuche und böswillige Angriffe. Wenn Organisationen Microsoft 365 annehmen, werden einige Netzwerkdienste und-Daten teilweise oder vollständig in die Cloud migriert. Bei allen grundlegenden Änderungen an der Netzwerkarchitektur ist für diesen Prozess eine Neubewertung der Netzwerksicherheit erforderlich, bei der die folgenden Faktoren berücksichtigt werden:
  
- Wenn Clouddienste eingeführt werden, werden Netzwerkdienste und -daten zwischen lokalen Rechenzentren und der Cloud verteilt und der Perimeterschutz allein ist nicht mehr ausreichend.
- Remote Benutzer verbinden sich mit Unternehmensressourcen sowohl in lokalen Rechenzentren als auch in der Cloud von unkontrollierten Standorten wie Heimen, Hotels und Cafés aus.
- Speziell entwickelte Sicherheitsfeatures werden zunehmend in Clouddienste integriert und können vorhandene Sicherheitssysteme ergänzen oder ersetzen.

Microsoft bietet eine breite Palette von Microsoft 365-Sicherheitsfeatures und enthält normative Anleitungen für die Verwendung bewährter Sicherheitsmethoden, mit denen Sie die Daten-und Netzwerksicherheit für Microsoft 365 sicherstellen können. Empfohlene bewährte Methoden umfassen die folgenden:
  
- **Verwenden Sie mehrstufige Authentifizierung (MFA)** MFA fügt eine zusätzliche Schutzebene zu einer Strategie mit sicherem Kennwort hinzu, indem Benutzer nach der korrekten Eingabe des Kennworts einen Telefonanruf, eine Textnachricht oder eine App-Benachrichtigung auf ihrem Smartphone bestätigen müssen.

- **Verwenden der Microsoft Cloud-App-Sicherheit** Konfigurieren Sie Richtlinien, um anomale Aktivitäten nachzuverfolgen und darauf zu reagieren. Richten Sie Benachrichtigungen mit Microsoft Cloud App Security ein, damit Administratoren ungewöhnliche oder riskante Benutzeraktivitäten, z. B. das Herunterladen großer Datenmengen, mehrere gescheiterte Anmeldeversuche oder Verbindungen von unbekannten oder gefährlichen IP-Adressen aus, überprüfen können.

- **Konfigurieren Sie die Verhinderung von Datenverlust (DLP)** DLP ermöglicht es Ihnen, vertrauliche Daten zu erkennen und Richtlinien zu erstellen, durch die verhindert wird, dass Ihre Benutzer die Daten versehentlich oder absichtlich freigeben. DLP funktioniert in Microsoft 365, einschließlich Exchange Online, SharePoint Online und OneDrive, damit Ihre Benutzer kompatibel bleiben können, ohne den Workflow zu unterbrechen.

- **Kunden-Lockbox verwenden** Als Microsoft 365-Administrator können Sie die Kunden-Lockbox verwenden, um zu steuern, wie ein Microsoft-Supporttechniker während einer Hilfesitzung auf Ihre Daten zugreift. In Fällen, in denen der Techniker zur Erkennung und Behebung eines Problems Zugriff auf Ihre Daten benötigt, ermöglicht Ihnen Kunden Lockbox, die Zugriffsanfrage zu genehmigen oder abzulehnen.

- **Office 365 sicheres Ergebnis verwenden** Ein Tool zur Sicherheitsanalyse, mit dem Sie die Möglichkeiten zur weiteren Verringerung des Risikos empfehlen. Secure Score untersucht Ihre Microsoft 365-Einstellungen und-Aktivitäten und vergleicht diese mit einem von Microsoft festgelegten Basisplan. Anschließend erhalten Sie eine Bewertung basierend auf Ihrer Anwendung der bewährten Methoden für die Wahrung der Sicherheit.

Ein ganzheitlicher Ansatz zur Verbesserung der Sicherheit sollte folgende Aspekte berücksichtigen:
  
- Verlagern Sie den Schwerpunkt vom Perimeterschutz auf die Endpunktsicherheit, indem Sie cloudbasierte und Office-Client-basierte Sicherheitsfunktionen anwenden.
  - Verkleinern Sie den Sicherheitsperimeter auf das Rechenzentrum
  - Aktivieren Sie eine gleichwertige Vertrauensstellung für Benutzergeräte innerhalb des Büros oder an Remotestandorten
  - Legen Sie den Fokus auf die Absicherung des Datenspeicherorts und des Benutzerstandorts
  - Verwaltete Benutzercomputer haben eine höhere Vertrauensstellung
- Ganzheitliche Verwaltung aller Informationssicherheitsdaten, keine reine Fokussierung auf den Perimeter
  - Neudefinieren der WAN-und Building Perimeter-Netzwerksicherheit durchzulassen, dass vertrauenswürdiger Datenverkehr Sicherheitsgeräte umgeht und nicht verwaltete Geräte an Gast-Wi-Fi-Netzwerke trennt
  - Verringern der Netzwerksicherheitsanforderungen des unternehmensweiten WAN-Edges
  - Einige Geräte für den Netzwerkperimeterschutz wie Firewalls sind weiterhin erforderlich, aber die Auslastung wird reduziert.
  - Gewährleistet lokalen Ausstieg für Microsoft 365-Datenverkehr
- Verbesserungen können inkrementell umgesetzt werden, wie im Abschnitt [Inkrementelle Optimierung](office-365-network-connectivity-principles.md#BKMK_IncOpt) beschrieben. Einige Optimierungstechniken bieten je nach Netzwerkarchitektur möglicherweise ein besseres Preis-Leistungs-Verhältnis und Sie sollten die Optimierungen auswählen, die für Ihre Organisation am besten geeignet sind.

Weitere Informationen zur Sicherheit und Compliance von Microsoft 365 finden Sie im Artikel [Microsoft 365 Security](https://docs.microsoft.com/microsoft-365/security) und [Microsoft 365 Security](https://docs.microsoft.com/microsoft-365/compliance).
  
## <a name="incremental-optimization"></a>Inkrementelle Optimierung
<a name="BKMK_IncOpt"> </a>

Wir haben weiter oben in diesem Artikel das ideale Netzwerkverbindungsmodell für SaaS vorgestellt, aber vielen großen Organisationen mit historisch komplexen Netzwerkarchitekturen wird es nicht möglich sein, alle diese Änderungen direkt durchzuführen. In diesem Abschnitt wird eine Reihe von inkrementellen Änderungen erörtert, mit denen die Leistung und Zuverlässigkeit von Microsoft 365 verbessert werden kann.
  
Die Methoden, die Sie zum Optimieren des Datenverkehrs von Microsoft 365 verwenden werden, variieren in Abhängigkeit von Ihrer Netzwerktopologie und den von Ihnen implementierten Netzwerkgeräten. Große Unternehmen mit vielen Standorten und komplexen Netzwerk Sicherheitsverfahren müssen eine Strategie entwickeln, die die meisten oder alle im Abschnitt " [Microsoft 365 Connectivity Principles](office-365-network-connectivity-principles.md#BKMK_Principles) " aufgeführten Grundsätze enthält, während kleinere Organisationen nur eine oder zwei berücksichtigen sollten.
  
Sie können die Optimierung als inkrementellen Vorgang angehen und die jeweiligen Methoden nacheinander anwenden. In der folgenden Tabelle sind die wichtigsten Optimierungsmethoden danach aufgeführt, wie stark sie sich bei den meisten Benutzern auf Latenz und Zuverlässigkeit auswirken.
  
|**Optimierungsmethode**|**Beschreibung**|**Auswirkung**|
|:-----|:-----|:-----|
|Lokale DNS-Auflösung und Internetausgang  <br/> |Stellen Sie lokale DNS-Server an jedem Standort bereit, und stellen Sie sicher, dass Microsoft 365-Verbindungen so weit wie möglich am Standort des Benutzers in das Internet eingehen.  <br/> | Latenzen minimieren  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Microsoft 365-Einstiegspfad  <br/> |
|Regionale Ausgangspunkte hinzufügen  <br/> |Wenn Ihr Unternehmensnetzwerk über mehrere Standorte, aber nur einen Ausgangspunkt verfügt, fügen Sie regionale Ausgangspunkte hinzu, um Benutzern das Herstellen einer Verbindung mit dem nächsten Microsoft 365-Einstiegspunkt zu ermöglichen.  <br/> | Latenzen minimieren  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Microsoft 365-Einstiegspfad  <br/> |
|Proxys und Überprüfungsgeräte umgehen  <br/> |Konfigurieren Sie Browser mit PAC-Dateien, die Microsoft 365-Anforderungen direkt an Ausgangspunkte senden.  <br/> Konfigurieren Sie Edge-Router und Firewalls, um Microsoft 365-Datenverkehr ohne Inspektion zu ermöglichen.  <br/> | Latenzen minimieren  <br/>  Auslastung von Netzwerkgeräten reduzieren  <br/> |
|Direkte Verbindung für VPN-Benutzer aktivieren  <br/> |Für VPN-Benutzer können Sie Microsoft 365-Verbindungen so aktivieren, dass eine direkte Verbindung mit dem Netzwerk des Benutzers statt über den VPN-Tunnel hergestellt wird, indem Sie geteilte Tunneling implementieren.  <br/> | Latenzen minimieren  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Microsoft 365-Einstiegspfad  <br/> |
|Migrieren vom herkömmlichen WAN zu SD-WAN  <br/> |SD-WANs (Software Defined Wide Area Networks) vereinfachen die WAN-Verwaltung und verbessern die Leistung, da herkömmliche WAN-Router durch virtuelle Geräte ersetzt werden, ähnlich wie bei der Virtualisierung von Computerressourcen mit virtuellen Maschinen (VMs).  <br/> | Verbessern der Leistung und Verwaltbarkeit von WAN-Datenverkehr  <br/>  Auslastung von Netzwerkgeräten reduzieren  <br/> |

## <a name="related-topics"></a>Verwandte Themen

[Microsoft 365-Netzwerkkonnektivität (Übersicht)](office-365-networking-overview.md)

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)

[URLs und IP-Adressbereiche für Office 365](urls-and-ip-address-ranges.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Bewerten der Microsoft 365-Netzwerkkonnektivität](assessing-network-connectivity.md)

[Netzwerkplanung und Leistungsoptimierung für Microsoft 365](network-planning-and-performance.md)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)

[Microsoft 365-Konnektivitätstest](https://aka.ms/netonboard)

[So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365-Networking-Blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
