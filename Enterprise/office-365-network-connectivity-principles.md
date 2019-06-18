---
title: Prinzipien von Office 365-Netzwerkverbindungen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Bevor Sie mit der Planung Ihres Netzwerks für Office 365 Netzwerkkonnektivität beginnen, müssen Sie sich mit den Grundlagen der Konnektivität vertraut machen, um Office 365 Datenverkehr sicher zu verwalten und die bestmögliche Leistung zu erzielen. Dieser Artikel hilft Ihnen, die neuesten Anleitungen für die sichere Optimierung Office 365 Netzwerkkonnektivität zu verstehen.
ms.openlocfilehash: e8bb819fee5aa53fe3ea23f7b3b691be131ddf1f
ms.sourcegitcommit: 99bf8739dfe1842c71154ed9548ebdd013c7e59e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2019
ms.locfileid: "35017295"
---
# <a name="office-365-network-connectivity-principles"></a>Prinzipien von Office 365-Netzwerkverbindungen

Bevor Sie mit der Planung Ihres Netzwerks für Office 365 Netzwerkkonnektivität beginnen, müssen Sie sich mit den Grundlagen der Konnektivität vertraut machen, um Office 365 Datenverkehr sicher zu verwalten und die bestmögliche Leistung zu erzielen. Dieser Artikel hilft Ihnen, die neuesten Anleitungen für die sichere Optimierung Office 365 Netzwerkkonnektivität zu verstehen.
  
Herkömmliche Unternehmensnetzwerke sind in erster Linie darauf ausgelegt, Benutzern den Zugriff auf Anwendungen und Daten zu ermöglichen, die in firmeneigenen Rechenzentren mit hoher Perimeter-Sicherheit gehostet werden. Bei dem herkömmlichen Modell wird davon ausgegangen, dass Benutzer auf Anwendungen und Daten aus dem Umkreis des Unternehmensnetzwerks, über WAN-Verbindungen von Zweigstellen oder Remote über VPN-Verbindungen zugreifen.
  
Durch die Einführung von SaaS-Anwendungen wie Office 365 wird eine Kombination von Diensten und Daten außerhalb des Netzwerkperimeters verschoben. Ohne Optimierung unterliegt der Datenverkehr zwischen Benutzern und SaaS-Anwendungen der Wartezeit, die durch die Paketüberprüfung, Netzwerk-Haarnadeln, versehentliche Verbindungen mit geografisch entfernten Endpunkten und anderen Faktoren verursacht wurde. Sie können die beste Office 365 Leistung und Zuverlässigkeit sicherstellen, indem Sie wichtige Optimierungsrichtlinien verstehen und implementieren.
  
In diesem Artikel erfahren Sie mehr über die folgenden Themen:
  
- [Office 365 Architektur](office-365-network-connectivity-principles.md#BKMK_Architecture) für die Kundenanbindung an die Cloud
- Aktualisierte [Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) -Konnektivitäts-Prinzipien und Strategien zur Optimierung des Netzwerkdatenverkehrs und der Benutzeroberfläche
- Der [Office 365 Endpunkte-Webdienst](office-365-network-connectivity-principles.md#BKMK_WebSvc), mit dem Netzwerkadministratoren eine strukturierte Liste von Endpunkten für die Verwendung in der Netzwerkoptimierung nutzen können
- [Neue Office 365-Endpunkt Kategorien](office-365-network-connectivity-principles.md#BKMK_Categories) und Optimierungs Anleitungen
- [Vergleichen der Netzwerkumkreis Sicherheit mit der Endpunktsicherheit](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Optionen für die [inkrementelle Optimierung](office-365-network-connectivity-principles.md#BKMK_IncOpt) für Office 365 Datenverkehr
- Das [Office 365-Netzwerk](https://aka.ms/netonboard)-Onboarding-Tool, ein neues Tool zum Testen der grundlegenden Konnektivität mit Office 365

## <a name="office-365-architecture"></a>Office 365 Architektur
<a name="BKMK_Architecture"> </a>

Office 365 ist eine verteilte Software-as-a-Service-Cloud (SaaS), die Produktivitäts-und Zusammenarbeitsszenarien mithilfe einer Vielzahl von Mikro Diensten und Anwendungen bereitstellt, wie Exchange Online, SharePoint Online, Skype for Business Online, Microsoft Teams, Exchange Online Schutz, Office Online und viele andere. Während bestimmte Office 365 Anwendungen möglicherweise Ihre einzigartigen Features für das Kundennetzwerk und die Konnektivität zur Cloud aufweisen, teilen Sie einige wichtige Prinzipale, Ziele und Architekturmuster. Diese Prinzipale und Architekturmuster für die Konnektivität sind für viele andere Saas-Clouds typisch und unterscheiden sich gleichzeitig von den typischen Bereitstellungsmodellen von Platt Form-as-a-Service-und Infrastruktur-as-a-Service-Clouds wie Microsoft Azure.
  
Eines der bedeutendsten architektonischen Features von Office 365 (die von Netzwerk Planern häufig übersehen oder falsch interpretiert werden) besteht darin, dass es sich um einen wahrhaft globalen verteilten Dienst im Kontext der Verbindung von Benutzern handelt. Der Speicherort des Ziels Office 365 Mandanten ist wichtig, um die Lokalität zu verstehen, in der Kundendaten in der Cloud gespeichert sind, aber die Benutzererfahrung mit Office 365 beinhaltet keine direkte Verbindung mit Datenträgern, die die Daten enthalten. Die Benutzererfahrung mit Office 365 (einschließlich Leistung, Zuverlässigkeit und anderen wichtigen Qualitätsmerkmalen) umfasst die Konnektivität über eine hoch verteilte Service-Fronttüren, die über Hunderte von Microsoft-Standorten weltweit skaliert werden. In den meisten Fällen wird die beste Benutzererfahrung erzielt, indem das Kundennetzwerk Benutzeranforderungen an den nächstgelegenen Einstiegspunkt für Office 365 Dienst weiterleiten kann, statt eine Verbindung mit Office 365 über einen Ausgangspunkt an einem zentralen Standort oder einer Region herzustellen.
  
Für die meisten Kunden werden Office 365 Benutzer über viele Standorte verteilt. Um die besten Ergebnisse zu erzielen, sollten die in diesem Dokument dargelegten Prinzipien in der Ansicht horizontal skalieren (nicht horizontal) betrachtet werden, wobei der Schwerpunkt auf der Optimierung der Konnektivität mit dem nächstgelegenen Punkt der Anwesenheit im globalen Netzwerk von Microsoft liegt, und nicht auf dem geographischen Speicherort des Office 365 Mandanten. Im Wesentlichen bedeutet dies, dass, obwohl Office 365 Mandantendaten an einem bestimmten geografischen Standort gespeichert werden können, Office 365 Erfahrung für diesen Mandanten verbreitet bleibt und in sehr enger (Netzwerk-) Nähe zu jedem Endbenutzer Standort vorhanden sein kann, der vom Mandanten verwendet wird. .
  
## <a name="office-365-connectivity-principles"></a>Office 365-Konnektivitäts-Prinzipien
<a name="BKMK_Principles"> </a>

Microsoft empfiehlt die folgenden Grundsätze, um optimale Office 365 Konnektivität und Leistung zu erzielen. Verwenden Sie die folgenden Office 365-Konnektivitäts-Prinzipien, um den Datenverkehr zu verwalten und beim Herstellen einer Verbindung mit Office 365 eine optimale Leistung zu erzielen.
  
Das primäre Ziel im Netzwerkentwurf sollte es sein, die Wartezeit zu minimieren, indem Sie die Roundtripzeit (Round-Trip Time, RTT) aus Ihrem Netzwerk in das globale Microsoft-Netzwerk, das öffentliche Netzwerkbackbone von Microsoft, verkürzen, das alle Microsoft-Rechenzentren mit niedriger Latenz verbindet. und Cloud-Anwendungs Einstiegspunkte, die auf der ganzen Welt verteilt sind. Weitere Informationen zum globalen Netzwerk von Microsoft finden Sie unter [How Microsoft baut sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>Identifizieren und differenzieren von Office 365 Datenverkehr

![Identifizieren von Office 365 Datenverkehr](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Das identifizieren Office 365 Netzwerkdatenverkehrs ist der erste Schritt in der Lage, diesen Datenverkehr von dem allgemeinen Internet gebundenen Netzwerkdatenverkehr zu unterscheiden. Office 365 Konnektivität kann durch Implementierung einer Kombination von Ansätzen wie Netzwerkrouten Optimierung, Firewallregeln, Browser Proxyeinstellungen und Umgehung von Netzwerk Inspektionsgeräten für bestimmte Endpunkte optimiert werden.
  
Frühere Office 365 Optimierungs Anleitungen unterteilen Office 365 Endpunkte in zwei Kategorien, **erforderlich** und **optional**. Da Endpunkte zur Unterstützung neuer Office 365-Dienste und-Features hinzugefügt wurden, haben wir Office 365 Endpunkte in drei Kategorien umstrukturiert: **optimize**, **Allow** und **default**. Richtlinien für jede Kategorie gelten für alle Endpunkte in der Kategorie, wodurch die Optimierung einfacher zu verstehen und zu implementieren ist.
  
Weitere Informationen zum Office 365 von Endpunkt Kategorien und Optimierungsmethoden finden Sie im Abschnitt [neue Office 365-Endpunkt Kategorien](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft veröffentlicht jetzt alle Office 365 Endpunkte als Webdienst und bietet Anleitungen zur optimalen Verwendung dieser Daten. Weitere Informationen zum Abrufen und arbeiten mit Office 365 Endpunkten finden Sie im Artikel [Office 365 URLs und IP-Adressbereiche](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Lokaler Ausgang von Netzwerkverbindungen

![Lokaler Ausgang von Netzwerkverbindungen](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokale DNS-und Internet Ausstiege sind von entscheidender Bedeutung, um die Verbindungswartezeit zu verringern und sicherzustellen, dass Benutzer Verbindungen zum nächsten Einstiegspunkt für Office 365 Dienste hergestellt werden. In einer komplexen Netzwerktopologie ist es wichtig, dass sowohl lokales DNS als auch lokales Internet-Ausstieg zusammen implementiert wird. Weitere Informationen dazu, wie Office 365 Clientverbindungen an den nächstgelegenen Einstiegs Ort weiterleitet, finden Sie im Artikel [Client Connectivity](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Vor dem Aufkommen von Cloud-Diensten wie Office 365 war die Internet Anbindung von Endbenutzern als Entwurfs Faktor in der Netzwerkarchitektur relativ einfach. Wenn Internet Dienste und Websites auf der ganzen Welt verteilt werden, ist die Wartezeit zwischen Unternehmens Ausgangspunkten und einem bestimmten Zielendpunkt größtenteils eine Funktion des geografischen Abstands.
  
In einer herkömmlichen Netzwerkarchitektur durchlaufen alle ausgehenden Internet Verbindungen das Unternehmensnetzwerk und gehen von einem zentralen Standort aus. Da die Cloud-Angebote von Microsoft ausgereift sind, ist eine verteilte, mit dem Internet verbundene Netzwerkarchitektur für die Unterstützung von Latenz sensitiven Cloud-Diensten entscheidend geworden. Das globale Microsoft-Netzwerk wurde entwickelt, um Latenz Anforderungen mit der verteilten Dienst-Front-Door-Infrastruktur zu erfüllen, einer dynamischen Struktur globaler Einstiegspunkte, die eingehende Cloud-Dienstverbindungen an den nächstgelegenen Einstiegspunkt weiterleitet. Dadurch soll die Länge der "letzten Meile" für Microsoft Cloud-Kunden reduziert werden, indem die Route zwischen dem Kunden und der Cloud effektiv verkürzt wird.
  
Enterprise-WANs werden häufig für die Backhaul von Netzwerkdatenverkehr an eine zentrale Unternehmenszentrale zur Inspektion vor dem Ausstieg ins Internet entwickelt, in der Regel über einen oder mehrere Proxy Server. Das folgende Diagramm veranschaulicht eine solche Netzwerktopologie.
  
![Herkömmliches Unternehmensnetzwerk Modell](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Da Office 365 im globalen Microsoft-Netzwerk ausgeführt wird, das Front-End-Server auf der ganzen Welt umfasst, gibt es häufig einen Front-End-Server in der Nähe des Standorts des Benutzers. Durch die Bereitstellung des lokalen Internet Ausgangs und das Konfigurieren interner DNS-Server für die Bereitstellung der lokalen Namensauflösung für Office 365 Endpunkte kann der für Office 365 vorgesehene Netzwerkdatenverkehr eine Verbindung mit Office 365-Front-End-Servern so nahe wie möglich an den Benutzer herstellen. Das folgende Diagramm zeigt ein Beispiel für eine Netzwerktopologie, die es Benutzern ermöglicht, eine Verbindung von der Hauptniederlassung, Zweigstelle und Remotestandorten aus herzustellen, um die kürzeste Route zum nächsten Office 365 Einstiegspfad zu erhalten.
  
![WAN-Netzwerkmodell mit regionalen Ausgangspunkten](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Das verkürzen des Netzwerkpfads zu Office 365 Einstiegspunkten auf diese Weise kann die Verbindungsleistung und die Endbenutzererfahrung in Office 365 verbessern und auch dazu beitragen, die Auswirkungen künftiger Änderungen an der Netzwerkarchitektur auf Office 365 Leistung zu reduzieren und Zuverlässigkeit.
  
Außerdem können DNS-Anforderungen eine Wartezeit einführen, wenn der antwortenden DNS-Server entfernt oder ausgelastet ist. Sie können die Wartezeit bei der Namensauflösung minimieren, indem Sie lokale DNS-Server an Zweigstellen bereitstellen und sicherstellen, dass Sie für die ordnungsgemäße Cache-DNS-Einträge konfiguriert sind.
  
Während regionale Ausgangspunkte für Office 365 gut geeignet sind, besteht das optimale Verbindungsmodell darin, dass immer ein Netzwerk Austritt am Standort des Benutzers bereitgestellt wird, unabhängig davon, ob sich dies im Unternehmensnetzwerk oder an Remotestandorten wie Home, Hotels, Coffee Shops und Flughäfen. Dieses lokale direkt Ausstieg-Modell wird im Diagramm unten dargestellt.
  
![Lokale Ausstieg-Netzwerkarchitektur](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Unternehmen, die Office 365 angenommen haben, können die Front-Door-Architektur des Microsoft Global-Netzwerks nutzen, indem Sie sicherstellen, dass Benutzer Verbindungen mit Office 365 möglichst kürzeste Route zum nächsten Microsoft Global Network-Eintrag erhalten. Punkt. Die lokale Ausgangs Netzwerkarchitektur ermöglicht dies, indem Office 365 Datenverkehr unabhängig vom Standort des Benutzers über den nächsten Ausgang geroutet wird.
  
Die lokale Ausgangsarchitektur verfügt über die folgenden Vorteile gegenüber dem herkömmlichen Modell:
  
- Bietet optimale Office 365 Leistung durch Optimierung der Routenlänge. Endbenutzer Verbindungen werden dynamisch an den nächsten Office 365 Einstiegspunkt der verteilten Dienst-Front-Door-Infrastruktur weitergeleitet.
- Reduziert die Auslastung der Unternehmensnetzwerk Infrastruktur, indem lokale Ausgänge zugelassen werden.
- Sichert Verbindungen an beiden Enden durch Nutzung von Client-Endpunktsicherheit und Cloud-Sicherheitsfunktionen.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Vermeiden von Spitzkehren für Netzwerke

![Haarnadeln vermeiden](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Als allgemeine Faustregel bietet die kürzeste, direkteste Route zwischen dem Benutzer und dem nächsten Office 365 Endpunkt die beste Leistung. Eine Netzwerk-Haarnadel tritt auf, wenn der WAN-oder VPN-Datenverkehr, der für ein bestimmtes Ziel gebunden ist, zuerst an einen anderen Zwischenspeicher (beispielsweise Sicherheits Stapel, Cloud-Zugriffs Broker, Cloud-basiertes WebGateway) weitergeleitet wird und die Wartezeit und mögliche Umleitung zu einer geografisch entfernter Endpunkt. Netzwerk-Haarnadeln können auch durch Ineffizienzen bei Routing/Peering-Vorgängen oder suboptimal (Remote)-DNS-Lookups verursacht werden.
  
Um sicherzustellen, dass Office 365 Konnektivität auch im lokalen Ausgangsfall keine Haarnadeln unterliegt, überprüfen Sie, ob der ISP, der zum Bereitstellen des Internet Ausstiegs für den Benutzerstandort verwendet wird, über eine direkte Peering-Beziehung mit dem Microsoft Global Network in close verfügt. Nähe zu diesem Standort. Möglicherweise möchten Sie auch das Ausgangsrouting so konfigurieren, dass vertrauenswürdige Office 365 Datenverkehr direkt gesendet werden, im Gegensatz zu Proxyvorgängen oder Tunneling über einen Drittanbieter-Cloud-oder cloudbasierten Netzwerk Sicherheitsanbieter, der Ihren Internet gebundenen Datenverkehr verarbeitet. Durch die lokale DNS-Namensauflösung Office 365 Endpunkte wird sichergestellt, dass neben dem direkten Routing die nächsten Office 365 Einstiegspunkte für Benutzer Verbindungen verwendet werden.
  
Wenn Sie Cloud-basierte Netzwerk-oder Sicherheitsdienste für den Office 365 Datenverkehr verwenden, stellen Sie sicher, dass der hairpinning-Effekt ausgewertet wird und seine Auswirkungen auf die Office 365 Leistung verstanden werden. Dies kann durch Untersuchung der Anzahl und der Speicherorte von Dienstanbieter Standorten erfolgen, über die der Datenverkehr im Verhältnis zur Nummer ihrer Zweigstellen und zum Microsoft Global Network Peering Points weitergeleitet wird, die Qualität der Netzwerk Peering-Beziehung von der Dienstanbieter mit Ihrem ISP und Microsoft sowie die Leistungseinbußen beim Transport in der Dienstanbieter Infrastruktur.
  
Aufgrund der großen Anzahl verteilter Standorte mit Office 365 Einstiegspunkten und ihrer Nähe zu Endbenutzern kann das Routing Office 365 Datenverkehrs an ein beliebiges Drittanbieternetzwerk oder einen Sicherheitsanbieter negative Auswirkungen auf Office 365 Verbindungen haben, wenn das Anbieter Netzwerk nicht für optimales Office 365 Peering konfiguriert.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Bewerten von Umgehungs Proxys, Datenverkehrs Inspektionsgeräten und doppelten Sicherheitstechnologien

![Umgehen von Proxys, Datenverkehrs Inspektionsgeräten und doppelten Sicherheitstechnologien](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Unternehmenskunden sollten ihre Methoden zur Netzwerksicherheit und zur Risikominderung speziell für Office 365 gebundenen Datenverkehr überprüfen und Office 365 Sicherheitsfeatures verwenden, um die Abhängigkeit von intrusivem, Leistungseinbußen und teurer Netzwerksicherheit zu verringern. Technologien für Office 365 Netzwerkdatenverkehr.
  
Die meisten Unternehmensnetzwerke erzwingen die Netzwerksicherheit für den Internet Datenverkehr mithilfe von Technologien wie Proxys, SSL-Inspektion, Paketüberprüfung und Verhinderung von Datenverlust Systemen. Diese Technologien bieten eine wichtige Risikominderung für generische Internet Anforderungen, können jedoch die Leistung, die Skalierbarkeit und die Qualität der Endbenutzererfahrung drastisch reduzieren, wenn Sie auf Office 365 Endpunkte angewendet werden.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 Endpunkte-Webdienst

Office 365 Administratoren können einen Skript-oder Rest-Aufruf verwenden, um eine strukturierte Liste von Endpunkten aus dem Office 365-Endpunkt-Webdienst zu nutzen und die Konfigurationen von Umkreisfirewalls und anderen Netzwerkgeräten zu aktualisieren. Dadurch wird sichergestellt, dass der für Office 365 gebundene Datenverkehr identifiziert, angemessen behandelt und anders gehandhabt wird als der Netzwerkdatenverkehr für generische und häufig unbekannte Internet Websites. Weitere Informationen zur Verwendung des Office 365 Endpunkte-Webdiensts finden Sie im Artikel [Office 365 von URLs und IP-Adressbereichen](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (Proxy Automatic Configuration)-Skripts
<a name="BKMK_WebSvc"> </a>

Office 365 Administratoren können PAC (Proxy Automatic Configuration)-Skripts erstellen, die über WPAD oder GPO an Benutzer Computer übermittelt werden können. PAC-Skripts können verwendet werden, um Proxys für Office 365 Anforderungen von WAN-oder VPN-Benutzern zu umgehen, sodass Office 365 Datenverkehr direkte Internet Verbindungen verwenden kann, anstatt das Unternehmensnetzwerk zu durchlaufen.
  
#### <a name="office-365-security-features"></a>Office 365 Sicherheitsfeatures
<a name="BKMK_WebSvc"> </a>

Microsoft ist für die Sicherheit von Rechenzentren, die Betriebssicherheit und die Risikominimierung rund um Office 365 Server und die von diesen repräsentierten Netzwerkendpunkte transparent. Office 365 integrierte Sicherheitsfunktionen sind verfügbar, um das Netzwerk Sicherheitsrisiko zu reduzieren, beispielsweise Verhinderung von Datenverlust, Virenschutz, mehrstufige Authentifizierung, Kunden Sperr Feld, Advanced Threat Protection, Office 365 Threat Intelligence, Office 365 Secure Score, Exchange Online Protection und Network DDoS Security.
  
Weitere Informationen zum Microsoft-Rechenzentrum und zur globalen Netzwerksicherheit finden Sie im [Microsoft Trust Center](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Neue Office 365-Endpunkt Kategorien
<a name="BKMK_Categories"> </a>

Office 365 Endpunkte stellen eine unterschiedliche Gruppe von Netzwerkadressen und Subnetzen dar. Endpunkte können URLs, IP-Adressen oder IP-Bereiche sein, und einige Endpunkte werden mit bestimmten TCP/UDP-Ports aufgelistet. URLs können entweder ein FQDN wie *Account.Office.net* oder eine Platzhalter-URL wie * \*. office365.com*sein.
  
> [!NOTE]
> Die Speicherorte von Office 365 Endpunkten im Netzwerk beziehen sich nicht direkt auf den Speicherort der Office 365 Mandantendaten. Aus diesem Grund sollten Kunden Office 365 als einen verteilten und globalen Dienst betrachten und nicht versuchen, Netzwerkverbindungen zu Office 365 Endpunkten basierend auf geografischen Kriterien zu blockieren.
  
In unserem vorherigen Leitfaden für die Verwaltung Office 365 Datenverkehrs wurden Endpunkte in zwei Kategorien unterteilt, **erforderlich** und **optional**. Endpunkte innerhalb jeder Kategorie erforderten unterschiedliche Optimierungen, je nach der Wichtigkeit des Diensts, und viele Kunden stellten sich vor Herausforderungen, um die Anwendung derselben Netzwerkoptimierungen auf die vollständige Liste der Office 365-URLs und IP-Adressen zu rechtfertigen.
  
Im neuen Modell werden Endpunkte in drei Kategorien unterteilt: **optimize**, **Allow** und **default**, wobei ein prioritätsbasierter Drehpunkt bereitgestellt wird, in dem die Bemühungen zur Netzwerkoptimierung konzentriert werden, um die besten Leistungsverbesserungen zu erzielen und die Rückgabe auf Investitionen. Die Endpunkte werden in den oben aufgeführten Kategorien basierend auf der Sensibilität der effektiven Benutzeroberfläche für Netzwerkqualität, Volumen und Leistung von Szenarien und der einfachen Implementierung konsolidiert. Empfohlene Optimierungen können auf die gleiche Weise auf alle Endpunkte in einer bestimmten Kategorie angewendet werden.
  
- Endpunkte **optimieren** sind für die Konnektivität mit jedem Office 365 Dienst erforderlich und stellen über 75% der Office 365 Bandbreite, der Verbindungen und des Datenvolumens dar. Diese Endpunkte stellen Office 365 Szenarien dar, die am sensibelsten für Netzwerkleistung, Wartezeit und Verfügbarkeit sind. Alle Endpunkte werden in Microsoft-Datencentern gehostet. Die Änderungsrate der Endpunkte in dieser Kategorie wird voraussichtlich deutlich niedriger sein als bei den Endpunkten in den beiden anderen Kategorien. Diese Kategorie enthält eine sehr kleine (in der Reihenfolge von ~ 10) Gruppe von wichtigen URLs und eine definierte Gruppe von IP-Subnetzen, die auf Kern Office 365 Arbeitslasten wie Exchange Online, SharePoint Online, Skype for Business Online und Microsoft Teams ausgerichtet sind.

    Eine verkürzte Liste mit gut definierten kritischen Endpunkten sollte Ihnen helfen, hochwertige Netzwerkoptimierungen für diese Ziele schneller und einfacher zu planen und zu implementieren.

    Beispiele für die *Optimierung* von *https://outlook.office365.com* Endpunkten sind *https://\<Mandanten\>. SharePoint.com* und *https://\<Mandanten\>-My.SharePoint.com* .

    Zu den Optimierungsmethoden gehören:

  - Umgehen oder Whitelist *optimieren* Sie Endpunkte für Netzwerkgeräte und-Dienste, die Datenverkehrsüberwachung, SSL-Entschlüsselung, umfassende Paketüberprüfung und Inhaltsfilterung durchführen.
  - Umgehen Sie lokale Proxy Geräte und Cloud-basierte Proxydienste, die häufig für generisches Internet browsen verwendet werden.
  - Priorisieren Sie die Bewertung dieser Endpunkte als voll vertrauenswürdig in Ihrer Netzwerkinfrastruktur und ihren Umkreis Systemen.
  - Priorisieren Sie die Reduzierung oder Eliminierung von WAN-Rück Transporten, und vereinfachen Sie die direkt verteilte Internet basierte Ausgangsposition für diese Endpunkte so nah wie möglich an Benutzern/Zweigstellen.
  - Vereinfachen Sie die direkte Konnektivität zu diesen Cloud-Endpunkten für VPN-Benutzer durch Implementierung des Split-Tunnelings.
  - Stellen Sie sicher, dass von der DNS-Namensauflösung zurückgegebene IP-Adressen dem Routing Ausgangspfad für diese Endpunkte entsprechen.
  - Priorisieren Sie diese Endpunkte für die SD-WAN-Integration für das direkte, minimale Latenz Routing in den nächstgelegenen Internet-peeringpunkt des globalen Microsoft-Netzwerks.

- Endpunkte **zulassen** sind für die Konnektivität mit bestimmten Office 365 Diensten und-Features erforderlich, sind jedoch nicht so anfällig für Netzwerkleistung und Latenz wie in der Kategorie *optimieren* . Die gesamte Netzwerkpräsenz dieser Endpunkte aus der Sicht der Bandbreite und der Anzahl der Verbindungen ist ebenfalls bedeutend kleiner. Diese Endpunkte sind für Office 365 dediziert und werden in Microsoft-Rechenzentren gehostet. Sie stellen eine breite Palette von Office 365-Mikro Diensten und deren Abhängigkeiten (in der Reihenfolge von ~ 100-URLs) dar und werden mit einer höheren Rate als in der Kategorie *optimieren* erwartet. Nicht alle Endpunkte in dieser Kategorie sind definierten dedizierten IP-Subnetzen zugeordnet.

    Netzwerkoptimierungen für *Allow* -Endpunkte können die Office 365 Benutzererfahrung verbessern, aber einige Kunden entscheiden sich möglicherweise, diese Optimierungen enger einzuschränken, um Änderungen am Netzwerk gering zu halten.

    Beispiele für *Allow* -Endpunkte sind *https://\*. Protection.Outlook.com* und *https://accounts.accesscontrol.windows.net*.

    Zu den Optimierungsmethoden gehören:

  - Bypass-oder Whitelist *erlaubt* Endpunkte für Netzwerkgeräte und-Dienste, die Datenverkehrsüberwachung, SSL-Entschlüsselung, ausführliche Paketüberprüfung und Inhaltsfilterung ausführen.
  - Priorisieren Sie die Bewertung dieser Endpunkte als voll vertrauenswürdig in Ihrer Netzwerkinfrastruktur und ihren Umkreis Systemen.
  - Priorisieren Sie die Reduzierung oder Eliminierung von WAN-Rück Transporten, und vereinfachen Sie die direkt verteilte Internet basierte Ausgangsposition für diese Endpunkte so nah wie möglich an Benutzern/Zweigstellen.
  - Stellen Sie sicher, dass von der DNS-Namensauflösung zurückgegebene IP-Adressen dem Routing Ausgangspfad für diese Endpunkte entsprechen.
  - Priorisieren Sie diese Endpunkte für die SD-WAN-Integration für das direkte, minimale Latenz Routing in den nächstgelegenen Internet-peeringpunkt des globalen Microsoft-Netzwerks.

- **Standard** Endpunkte stellen Office 365 Dienste und Abhängigkeiten dar, die keine Optimierung erfordern und können von Kundennetzwerken als normaler Internet gebundener Datenverkehr behandelt werden. Beachten Sie, dass einige Endpunkte in dieser Kategorie möglicherweise nicht in Microsoft-Rechenzentren gehostet werden. Beispiele: *https://odc.officeapps.live.com* include und *https://appexsin.stb.s-msn.com*.

Weitere Informationen zu Office 365 Methoden zur Netzwerkoptimierung finden Sie im Artikel [Managing Office 365](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview)Endpoints.
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Vergleichen der Netzwerkumkreis Sicherheit mit der Endpunktsicherheit
<a name="BKMK_SecurityComparison"> </a>

Das Ziel der traditionellen Netzwerksicherheit besteht darin, den Umkreis des Unternehmensnetzwerks vor Eindringversuchen und böswilligen Ausnutzungen zu verhärten. Wenn Organisationen Office 365 einführen, werden einige Netzwerkdienste und-Daten teilweise oder vollständig in die Cloud migriert. Wie jede grundlegende Änderung an der Netzwerkarchitektur erfordert dieser Prozess eine Neubewertung der Netzwerksicherheit, bei der die folgenden Faktoren berücksichtigt werden:
  
- Wenn Cloud-Dienste angenommen werden, werden Netzwerkdienste und-Daten zwischen lokalen Rechenzentren und der Cloud verteilt, und die Umkreis Sicherheit reicht nicht mehr aus.
- Remote Benutzer stellen eine Verbindung zu Unternehmensressourcen sowohl in lokalen Rechenzentren als auch in der Cloud von unkontrollierten Standorten wie Homes, Hotels und Coffee Shops her.
- Speziell erstellte Sicherheitsfeatures werden zunehmend in Cloud-Dienste integriert und können vorhandene Sicherheitssysteme möglicherweise ergänzen oder ersetzen.

Microsoft bietet eine breite Palette von Office 365 Sicherheitsfeatures und enthält Anleitungen für die Verwendung bewährter Sicherheitsmethoden, die Ihnen dabei helfen können, Daten und Netzwerksicherheit für Office 365 sicherzustellen. Empfohlene bewährte Methoden umfassen Folgendes:
  
- **Verwenden der mehrstufigen Authentifizierung (MFA)** MFA fügt einer strengen Kenn Wort Strategie eine zusätzliche Schutzebene hinzu, indem Benutzer nach der korrekten Eingabe Ihres Kennworts einen Telefonanruf, eine Textnachricht oder eine APP-Benachrichtigung auf dem Smartphone bestätigen müssen.

- **Verwenden der Microsoft Cloud-App-Sicherheit** Richten Sie Richtlinien ein, um anomale Aktivitäten nachzuverfolgen und darauf zu reagieren. Richten Sie Warnungen mit Microsoft Cloud App Security ein, damit Administratoren ungewöhnliche oder riskante Benutzeraktivitäten wie das Herunterladen großer Datenmengen, mehrere fehlgeschlagene Anmeldeversuche oder Verbindungen von unbekannten oder gefährlichen IP-Adressen überprüfen können.

- Konfigurieren der Verhinderung von **Datenverlust (DLP)** Mithilfe von DLP können Sie vertrauliche Daten identifizieren und Richtlinien erstellen, die verhindern, dass Benutzer versehentlich oder absichtlich die Daten freigeben. DLP funktioniert in Office 365 einschließlich Exchange Online, SharePoint Online und OneDrive, damit Ihre Benutzer kompatibel bleiben können, ohne den Workflow zu unterbrechen.

- **Kunden-Lockbox verwenden** Als Office 365 Administrator können Sie Customer Lockbox verwenden, um zu steuern, wie ein Microsoft-Supporttechniker während einer Hilfesitzung auf Ihre Daten zugreift. In Fällen, in denen der Techniker Zugriff auf Ihre Daten benötigt, um ein Problem zu beheben und zu beheben, können Sie mit der Customer Lockbox die Zugriffsanforderung genehmigen oder ablehnen.

- **Office 365 sicheres Ergebnis verwenden** Secure Score ist ein Tool zur Sicherheitsanalyse, mit dem Sie die Möglichkeiten zur weiteren Verringerung des Risikos empfehlen. Secure Score untersucht Ihre Office 365 Einstellungen und Aktivitäten und vergleicht diese mit einem von Microsoft festgelegten Basisplan. Sie erhalten eine Bewertung basierend darauf, wie Sie mit den besten Sicherheitsmethoden übereinstimmen.

Ein ganzheitlicher Ansatz zur Erhöhung der Sicherheit sollte Folgendes berücksichtigen:
  
- Verschieben Sie den Schwerpunkt von der Umkreis Sicherheit hin zur Endpunktsicherheit, indem Sie Cloud-basierte und Office-Client Sicherheitsfeatures anwenden.
  - Verkleinern des Sicherheits Perimeters auf das Rechenzentrum
  - Aktivieren einer äquivalenten Vertrauensstellung für Benutzer Geräte innerhalb des Büros oder an Remotestandorten
  - Fokus auf die Sicherung des Datenspeicherorts und des Benutzerspeicher Orts
  - Verwaltete Benutzer Computer haben eine höhere Vertrauensebene mit der Endpunktsicherheit
- Ganzheitliche Verwaltung aller Informationssicherheit, ohne sich ausschließlich auf den Umkreis zu konzentrieren
  - Definieren Sie WAN und die Sicherheit im Umkreisnetzwerk neu, indem Sie vertrauenswürdigen Datenverkehr erlauben, Sicherheitsgeräte zu umgehen und nicht verwaltete Geräte an Gast-Wi-Fi-Netzwerke zu trennen.
  - Reduzierung der Netzwerksicherheitsanforderungen des unternehmensweiten WAN-Edges
  - Einige Netzwerkperimeter-Sicherheitsgeräte wie Firewalls sind weiterhin erforderlich, aber die Last wird gesenkt.
  - Gewährleistet lokalen Ausstieg für Office 365 Datenverkehr
- Verbesserungen können inkrementell behoben werden, wie im Abschnitt [inkrementelle Optimierung](office-365-network-connectivity-principles.md#BKMK_IncOpt) beschrieben. Einige Optimierungstechniken bieten je nach Netzwerkarchitektur möglicherweise bessere Kosten-Nutzen-Relationen, und Sie sollten Optimierungen auswählen, die für Ihre Organisation am sinnvollsten sind.

Weitere Informationen zur Office 365 Sicherheit und Compliance finden Sie im Artikel [Overview of Security and Compliance in Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Inkrementelle Optimierung
<a name="BKMK_IncOpt"> </a>

Wir haben das ideale Netzwerk Verbindungsmodell für SaaS weiter oben in diesem Artikel dargestellt, aber für viele große Organisationen mit historisch komplexen Netzwerkarchitekturen ist es nicht praktikabel, alle diese Änderungen direkt vorzunehmen. In diesem Abschnitt wird eine Reihe von inkrementellen Änderungen erörtert, die dazu beitragen können, Office 365 Leistung und Zuverlässigkeit zu verbessern.
  
Die für die Optimierung Office 365 Datenverkehrs verwendeten Methoden hängen von Ihrer Netzwerktopologie und den von Ihnen implementierten Netzwerkgeräten ab. Große Unternehmen mit vielen Standorten und komplexen Netzwerk Sicherheitsverfahren müssen eine Strategie entwickeln, die die meisten oder alle im Abschnitt [Office 365 Connectivity Principles](office-365-network-connectivity-principles.md#BKMK_Principles) aufgeführten Grundsätze enthält, während kleinere Organisationen möglicherweise nur Sie müssen eine oder zwei Punkte in Frage stellen.
  
Sie können die Optimierung als inkrementellen Prozess angehen, indem Sie jede Methode nacheinander anwenden. In der folgenden Tabelle sind die wichtigsten Optimierungsmethoden in der Reihenfolge ihrer Auswirkungen auf die Wartezeit und Zuverlässigkeit für die größte Anzahl von Benutzern aufgeführt.
  
|**Optimization-Methode**|**Beschreibung**|**Auswirkung**|
|:-----|:-----|:-----|
|Lokale DNS-Auflösung und Internet Ausstieg  <br/> |Stellen Sie lokale DNS-Server an jedem Standort bereit, und stellen Sie sicher, dass Office 365 Verbindungen zum Internet so nah wie möglich an den Standort des Benutzers ausgehen.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Office 365 Einstiegspfad  <br/> |
|Hinzufügen regionaler Ausgangspunkte  <br/> |Wenn Ihr Unternehmensnetzwerk über mehrere Standorte, aber nur einen Ausgangspunkt verfügt, fügen Sie regionale Ausgangspunkte hinzu, um Benutzern das Herstellen einer Verbindung mit dem nächstgelegenen Office 365 Einstiegspunkt zu ermöglichen.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Office 365 Einstiegspfad  <br/> |
|Umgehen von Proxys und Inspektionsgeräten  <br/> |Konfigurieren Sie Browser mit PAC-Dateien, die Office 365 Anforderungen direkt an Ausgangspunkte senden.  <br/> Konfigurieren Sie Edge-Router und Firewalls, um Office 365 Datenverkehr ohne Inspektion zu ermöglichen.  <br/> | Minimieren der Wartezeit  <br/>  Verringern der Auslastung von Netzwerkgeräten  <br/> |
|Aktivieren der direkten Verbindung für VPN-Benutzer  <br/> |Aktivieren Sie für VPN-Benutzer Office 365 Verbindungen, um eine direkte Verbindung mit dem Netzwerk des Benutzers und nicht über den VPN-Tunnel herzustellen, indem Sie geteilte Tunneling implementieren.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässigen Konnektivität mit dem nächsten Office 365 Einstiegspfad  <br/> |
|Migrieren von einem herkömmlichen WAN zu einem SD-WAN  <br/> |SD-WANs (Software Defined Wide Area Networks) vereinfachen die WAN-Verwaltung und verbessern die Leistung, indem herkömmliche WAN-Router durch virtuelle Appliances ersetzt werden, ähnlich der Virtualisierung von Compute-Ressourcen mithilfe virtueller Computer (VMS).  <br/> | Verbessern der Leistung und Verwaltbarkeit des WAN-Datenverkehrs  <br/>  Verringern der Auslastung von Netzwerkgeräten  <br/> |

## <a name="related-topics"></a>Verwandte Themen

[Office 365 Netzwerkkonnektivität (Übersicht)](office-365-networking-overview.md)

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)

[URLs und IP-Adressbereiche für Office 365](urls-and-ip-address-ranges.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Bewerten Office 365 Netzwerkkonnektivität](assessing-network-connectivity.md)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)

[Bewerten Office 365 Netzwerkkonnektivität](assessing-network-connectivity.md)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)

[Office 365 Netzwerk-Onboarding-Tool](https://aka.ms/netonboard)

[So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog "Office 365 Networking"](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
