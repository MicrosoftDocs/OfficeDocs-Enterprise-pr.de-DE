---
title: Office 365 Network Connectivity Prinzipien
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Bevor Sie beginnen, Ihr Netzwerk für die Office 365-Netzwerkkonnektivität planen, ist es wichtig zu verstehen, die Konnektivität Grundsätze für sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung. In diesem Artikel helfen Ihnen das Verständnis der neuesten Anleitung zur Optimierung von Office 365-Netzwerkkonnektivität sicher.
ms.openlocfilehash: be41162833a7442ac65af1e973a00923841fca6b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540885"
---
# <a name="office-365-network-connectivity-principles"></a>Office 365 Network Connectivity Prinzipien

Bevor Sie beginnen, Ihr Netzwerk für die Office 365-Netzwerkkonnektivität planen, ist es wichtig zu verstehen, die Konnektivität Grundsätze für sichere Verwaltung von Office 365-Datenverkehr und erste die bestmögliche Leistung. In diesem Artikel helfen Ihnen das Verständnis der neuesten Anleitung zur Optimierung von Office 365-Netzwerkkonnektivität sicher.
  
Herkömmliche Unternehmensnetzwerken dienen in erster Linie, um Benutzern Zugriff auf Anwendungen und Daten in Unternehmen betrieben Rechenzentren mit starken Umkreisnetzwerk Sicherheit gehostet bereitzustellen. Das herkömmliche Modell setzt voraus, dass Benutzer Anwendungen und Daten von innerhalb der Umkreis Unternehmensnetzwerk über WAN-Verbindungen von Zweigniederlassungen oder Remote über VPN-Verbindungen zugreifen. 
  
Annahme von Anwendungen wie Office 365 SaaS verschiebt eine Kombination von Diensten und Daten außerhalb des Netzwerks. Wartezeit von Paketinspektion, Netzwerk Hairpins, unbeabsichtigten Verbindungen mit geografisch getrennte Endpunkte und anderen Faktoren eingeführt unterliegt Datenverkehrs zwischen Benutzern und SaaS Applications, ohne die Optimierung. Sie können die beste Office 365-Leistung und Zuverlässigkeit verstehen und Implementieren von Richtlinien für wichtige Optimierung sicherstellen.
  
In diesem Artikel erhalten Sie Informationen zur:
  
- [Office 365-Architektur](office-365-network-connectivity-principles.md#BKMK_Architecture) , wie er gilt für Kunden-Konnektivität in die cloud
- Aktualisierten [Office 365-Diensten Prinzipien](office-365-network-connectivity-principles.md#BKMK_Principles) und Strategien zum Optimieren der Netzwerkdatenverkehr und durch die Endbenutzer
- Die [Office 365-Endpunkten-Webdienst](office-365-network-connectivity-principles.md#BKMK_WebSvc), wodurch Netzwerkadministratoren nutzen eine strukturierte Liste der Endpunkte für die Verwendung in der Netzwerk-Optimierung
- Hinweise zur [neuen Office 365 Endpunkt Kategorien](office-365-network-connectivity-principles.md#BKMK_Categories) und Optimierung
- [Vergleich zwischen Umkreisnetzwerk Netzwerksicherheit mit Endgeräte-Sicherheit](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Inkrementelle](office-365-network-connectivity-principles.md#BKMK_IncOpt) Optimierungsoptionen für Office 365-Datenverkehr

## <a name="office-365-architecture"></a>Office 365-Architektur
<a name="BKMK_Architecture"> </a>

Office 365 ist eine verteilte Software-as-a-Service (SaaS) Cloud, die Produktivität und optimierte Zusammenarbeit Szenarien über eine Reihe von Micro-Dienste und Anwendungen, wie Exchange Online, SharePoint Online Skype für Online Business Microsoft bereitstellt Teams, Exchange Online Protection, Office Online und viele andere. Während bestimmte Anwendungen von Office 365 angewendet auf Kundennetzwerk und die Verbindungen mit der Cloud ihre einzigartigen Merkmale haben, weisen sie alle auf einige wichtige Prinzipale, die Ziele und die Architektur Muster. Diese Prinzipale und Architektur Mustern für die Konnektivität sind typisch für viele andere SaaS Wolken und zur selben Zeit wird deutlich anders aus der normalen Bereitstellungsmodelle der Plattform als Dienst und Infrastruktur als Dienst Wolken, wie beispielsweise Microsoft Azure.
  
Eines der wichtigsten architektonische Features von Office 365 (das ist häufig entgangene oder vom Netzwerkplaner falsch interpretiert) ist, dass es ein weltweiten verteilter Dienst im Kontext von wie Benutzer das Herstellen einer Verbindung ist. Die Position des Ziels Office 365-Mandanten ist wichtig zu verstehen, die Position des, wo die Kundendaten in der Cloud gespeichert ist, aber nicht die Arbeit mit Office 365 umfassen eine direkte Verbindung zum Datenträger, das Daten enthält. Die Benutzeroberfläche mit Office 365 (einschließlich Leistung, Zuverlässigkeit und andere wichtige Qualität Merkmale) umfasst Konnektivität über eine extrem verteilten Service Frontklappen, die auf Hunderten von Microsoft-Standorten weltweit erhöht wird. In den meisten Fällen wird die beste benutzerumgebung durch das Kundennetzwerk zur Weiterleitung von Anforderungen für den nächsten Einstiegspunkt für den Office 365 Benutzer zulassen, statt eine Verbindung mit Office 365 über eine Austritt in einem zentralen Speicherort oder einer Region erreicht.
  
Office 365-Benutzer sind für die meisten Kunden auf vielen Standorten verteilt. Um die besten Ergebnisse zu erzielen, sollten die in diesem Dokument beschriebenen Prinzipien auf Gesichtspunkt der Skalierung (nicht vertikales Skalieren), zum Optimieren der Konnektivität für die nächste Point of Presence, in der globalen Microsoft-Netzwerk, nicht für die geografische Konzentration betrachtet werden Speicherort der Office 365-Mandanten. Im Wesentlichen Dies bedeutet, dass, obwohl Office 365-Mandantendaten an einem bestimmten geografischen Standort gespeichert ist, wird Office 365-Erfahrung für diese Mandanten verteilten bleibt und kann sehr schließen in vorhanden sein (Netzwerk) in der Nähe jeder Endbenutzer Speicherort mit der Mandanten .
  
## <a name="office-365-connectivity-principles"></a>Office 365-Diensten Prinzipien
<a name="BKMK_Principles"> </a>

Microsoft empfiehlt die folgenden Grundsätze um eine optimale Office 365-Diensten und Leistung zu erzielen. Verwenden Sie diese Office 365-Diensten Grundsätze zum Verwalten des Datenverkehrs und die beste Leistung zu erhalten, wenn eine Verbindung zu Office 365.
  
Das primäre Ziel des Entwurfs sollte Wartezeit zu minimieren, durch die Reduzierung der Roundtripzeit (Zeit) aus dem Netzwerk, in das Microsoft Global Network Microsofts öffentliche Netzwerkbackbone, die alle Microsoft Rechenzentren mit geringer Latenz sind und cloud-Anwendung Einstiegspunkte auf der ganzen Welt verteilt. Erfahren Sie mehr über das Microsoft Global Network unter [wie Microsoft erstellt das schnelle und verlässliche globale Netzwerk](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
### <a name="identify-and-differentiate-office-365-traffic"></a>Identifizieren und Abgrenzen von Office 365-Datenverkehr
<a name="BKMK_P1"> </a>

![Identifizieren von Office 365-Datenverkehr](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identifizieren von Office 365 Netzwerkdatenverkehr ist der erste Schritt in wird dieser Datenverkehr vom generischen Internet gerichtete Netzwerkverkehr zu unterscheiden. Office 365-Diensten kann durch die Implementierung einer Kombination Ansätze wie Netzwerk Route Optimierung, Firewall-Regeln, Proxyeinstellungen des Browsers und der Prüfung Netzwerkgeräte für bestimmte Endpunkte umgangen optimiert werden.
  
Vorherige Office 365 Optimierung Leitfaden unterteilt Office 365-Endpunkten in zwei Kategorien, **erforderlich** und **Optional**. Wie Endpunkte zur Unterstützung der neuen Office 365-Dienste und Features hinzugefügt wurden, haben wir Office 365-Endpunkten in drei Kategorien reorganisiert: **Optimieren**, **Zulassen** und **Standard**. Richtlinien für jede Kategorie gilt für alle Endpunkte in der Kategorie, wodurch Optimierungen einfacher zu verstehen und zu implementieren. 
  
Weitere Informationen zu Office 365 Endpunkt Kategorien und Methoden zur Optimierung von finden Sie im Abschnitt [Kategorien für neue Office 365-Endpunkt](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft veröffentlicht alle Office 365-Endpunkten als Webdienst jetzt sowie Anleitungen zur optimalen diese Daten verwenden. Weitere Informationen zum Abrufen von und Arbeiten mit Office 365-Endpunkten finden Sie im Artikel [Office 365-URLs und IP-Adressbereiche](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
### <a name="egress-network-connections-locally"></a>Netzwerkverbindungen lokal Ausgang
<a name="BKMK_P2"> </a>

![Netzwerkverbindungen lokal Ausgang](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokalen DNS und Internet Ausgang ist besonders wichtig für reduziert die Verbindungslatenz und sicherstellen, dass benutzerverbindungen am nächsten Punkt des Eintrags zu Office 365-Diensten vorgenommen werden. In einer komplexen Netzwerktopologie ist es wichtig zu lokalen DNS und lokalen Internet Ausgang zusammen implementieren. Weitere Informationen dazu, wie Office 365 Clientverbindungen am nächsten Punkt des Eintrags weiterleitet finden Sie im Artikel [Clientkonnektivität](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Vor der Einführung von Clouddiensten wie etwa Office 365 wurde die Endbenutzer Internetkonnektivität ein Design Faktor bei der Netzwerkarchitektur relativ einfach. Wenn Internetdienste und Websites auf der ganzen Welt verteilt sind, ist Wartezeit zwischen corporate Ausgang Punkt und bestimmten Zielendpunkt weitgehend Funktion der geografische entfernungen.
  
Eine herkömmliche Netzwerkarchitektur alle ausgehende internetverbindungen Durchlaufen des Firmennetzwerks befinden und egress von einem zentralen Ort. Wie im weiteren Verlauf des Microsoft-Cloud-angeboten haben verfügt über eine verteilte Architektur der Internetzugriff Netzwerk für die Unterstützung von Clouddiensten latenzempfindliche kritisch werden. Globale Microsoft Network soll Wartezeit Erfordernissen mit der verteilten Service vorne Tür-Infrastruktur eine dynamische Fabric globale Einstiegspunkte gerecht zu werden, mit dem eingehende Verbindungen von Cloud-Dienst auf den nächsten Einstiegspunkt weitergeleitet. Dies soll kürzen "letzte Meile" für Microsoft-Cloud-Kunden durch effektiv verkürzen die Route zwischen dem Kunden und der Cloud.
  
Enterprise-WANs dienen häufig um Sonderinformationen Netzwerkdatenverkehr an einem zentralen Unternehmen Hauptsitz für die Untersuchung vor Ausgang für das Internet in der Regel über mindestens einen Proxy-Server. Das folgende Diagramm zeigt eine solche Netzwerktopologie.
  
![Bei diesem Modell herkömmlichen enterprise](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Da Office 365 im globalen Microsoft-Netzwerk ausgeführt, einschließlich Front-End-Server auf der ganzen Welt wird, wird häufig ein Front-End-Server in der Nähe der Standort des Benutzers. Durch lokalen Internet Ausgang bereitstellen und Konfigurieren der internen DNS-Server zum Bereitstellen der lokalen namensauflösung für Office 365-Endpunkten kann mit Office 365-Front-End-Webservern für den Benutzer möglichst schließen Netzwerkdatenverkehr für Office 365 verbinden. Die folgende Abbildung zeigt ein Beispiel einer Netzwerktopologie, die Benutzern von zentrale, Zweigstelle und Remotestandorten eine Verbindung herstellen, befolgen Sie die kürzeste für den nächsten Einstiegspunkt in Office 365 ermöglicht.
  
![Modell mit regionalen Ausgang Punkt WAN-Netzwerk](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Verkürzen des Netzwerkpfads zu Office 365 Einstiegspunkte auf diese Weise können Leistung verbessern, Konnektivität und der Endbenutzer Erfahrung in Office 365 und können auch Hilfe zur Reduzierung der Auswirkung von zukünftigen Änderungen an der Netzwerkarchitektur auf die Leistung von Office 365 und Zuverlässigkeit.
  
Darüber hinaus können DNS-Anforderungen Wartezeit verursachen, wenn der zuständigen DNS-Server ausgelastet oder entfernte ist. Sie können Name Resolution Wartezeit minimieren, indem provisioning lokale DNS-Servern in Zweigstellen und sicherzustellen, dass sie DNS-Einträge Cache entsprechend konfiguriert sind.
  
Während der regionalen Ausgang gut für Office 365 arbeiten kann, wäre das optimale Connectivity-Modell Netzwerk Ausgang am Standort des Benutzers, unabhängig davon, ob dies auf dem Unternehmensnetzwerk oder Remotestandorten wie Home, Hotels, Cafés ist immer bereitstellen und Flughäfen. Dieses Modell lokalen direkte Ausgang wird in der folgenden Abbildung dargestellt.
  
![Lokale Ausgang Netzwerkarchitektur](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Unternehmen, die Office 365 eingeführt haben können nutzen Sie das Microsoft Global Network verteilten Service vorderer Klappe Architektur durch sicherstellen, dass benutzerverbindungen mit Office 365 die kürzeste mögliche zu den nächsten Eintrag Microsoft Global Network dauern Punkt. Die lokale Ausgang Netzwerkarchitektur wird durch Zulassen der Office 365-Datenverkehr über die nächste Ausgang, unabhängig vom Benutzerstandort weitergeleitet werden sollen.
  
Die lokale Ausgang Architektur bietet die folgenden Vorteile über das herkömmliche Modell:
  
- Bietet eine optimale Leistung von Office 365 durch Optimieren der Route Länge. Endbenutzer-Verbindungen werden von der Infrastruktur verteilten Service vorderer Klappe dynamisch für den nächsten Einstiegspunkt in Office 365 weitergeleitet.
- Reduziert die Belastung Unternehmensnetzwerk-Infrastruktur durch Zulassen der lokalen Ausgang.
- Sichert Verbindungen an beiden Enden Endpunkt Clientsicherheit und Cloud-Sicherheitsfeatures werden genutzt.

### <a name="avoid-network-hairpins"></a>Vermeiden Sie Netzwerk hairpins
<a name="BKMK_P3"> </a>

![Vermeiden Sie hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Als allgemeine Daumenregel wird die kürzeste, direkte Route zwischen Benutzer- und engsten Office 365-Endpunkt die beste Leistung bieten. Ein Netzwerk Hairpin passiert, wenn WAN oder VPN-Datenverkehr für ein bestimmtes Ziel zuerst an eine andere intermediate Standort (wie Sicherheit Stapel, Cloud-Access-Broker von Cloud-basierten Web-Gateway), gerichtet ist gebunden Einführung in die Wartezeit und potenzielle Umleitung an eine Endpunkt geografisch entfernt. Netzwerk Hairpins können auch durch Ineffizienzen routing/peering oder suboptimaler (remote) DNS-Lookups verursacht werden.
  
Um sicherzustellen, dass Office 365-Diensten für Netzwerk Hairpins auch in der lokalen Ausgang Groß-/Kleinschreibung nicht gilt, überprüfen Sie, ob schließen Sie der Internetdienstanbieter, die zum Bereitstellen von Internet-Ausgang für den Speicherort eine direkte Peers Beziehung mit dem globalen Microsoft-Netzwerk in hat verwendet wird Nähe zu diesem Speicherort. Sie können auch Ausgang routing zum Senden von vertrauenswürdigen Office 365-Datenverkehr direkt konfigurieren möchten, im Gegensatz zu Proxyvorgänge oder über einen Drittanbieter-Cloud oder eine Cloud-basierten Netzwerk Sicherheitsanbieter tunneling, den für das Internet bestimmte Datenverkehr verarbeitet. Lokalen DNS-namensauflösung von Office 365-Endpunkten wird sichergestellt, dass neben den direkten routing die engsten Einstiegspunkte für Office 365 für benutzerverbindungen verwendet werden.
  
Bei Verwendung von Cloud-basierten Netzwerk oder Sicherheitsdienste für Ihre Office 365-Datenverkehr stellen Sie sicher, dass der Hairpinning Effekt ausgewertet wird und ihre Auswirkung auf die Leistung von Office 365 wird davon ausgegangen. Dies kann erfolgen durch Untersuchen der Anzahl und Standort der Service Provider Speicherorte, die über die der Datenverkehr im Verhältnis zum Anzahl Ihrer Zweigstellen und Microsoft Global Network Peers Punkte, Qualität Peers Beziehung des Netzwerk weitergeleitet wird der Dienstanbieter mit Ihrem Internetdienstanbieter Microsoft und der Leistung durch Backhauling in der Infrastruktur des Anbieters.
  
Aufgrund der großen Anzahl von verteilten Standorten mit Office 365-Einstiegspunkte und ihre Endbenutzer in der Nähe kann routing Office 365-Datenverkehr an eine beliebige Netzwerk- oder Drittanbieter negative auf Office 365-Verbindungen auswirken ist das anbieternetzwerk nicht für eine optimale Office 365 peering konfiguriert.
  
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Proxies umgehen, Datenverkehr Prüfung Geräte und doppelte sicherheitstechnologien
<a name="BKMK_P4"> </a>

![Proxies umgehen, Datenverkehr Prüfung Geräte und doppelte sicherheitstechnologien](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Unternehmenskunden, die ihre Netzwerksicherheit und Überwachungsrichtlinien Risiko Verringerung der Methoden speziell für Office 365 gebunden Datenverkehr und Sicherheitsfeatures von Office 365 verwenden, um ihre Abhängigkeit aufdringlich, Leistung beeinträchtigen und teurer Netzwerksicherheit zu reduzieren Technologien für Office 365-Netzwerkverkehr.
  
Die meisten Unternehmensnetzwerken Erzwingen der Netzwerksicherheit für Datenverkehr im Internet mithilfe von Technologien wie Proxys, SSL-Überprüfung, Paketinspektion und Data Loss Prevention-Systeme. Diese Technologien können bieten wichtige Risikominderung für generische Internet Anforderungen jedoch erheblich reduzieren Leistung, Skalierbarkeit und die Qualität des Endbenutzers auf Office 365-Endpunkten angewendet.
  
#### <a name="office-365-endpoints-web-service"></a>Office 365-Endpunkten-Webdienst
<a name="BKMK_WebSvc"> </a>

Office 365-Administratoren können ein Skript verwenden oder REST-Aufruf an eine strukturierte Liste der Endpunkte aus der Office 365-Endpunkten nutzen-Webdienst, und aktualisieren Sie die Konfiguration des Umkreisnetzwerks Firewalls und andere Netzwerkgeräte. Dadurch wird sichergestellt, dass-Datenverkehr für Office 365 identifiziert, entsprechend behandelt und anders aus Netzwerkdatenverkehr für generische und häufig unbekannten Websites im Internet gebunden verwaltete. Weitere Informationen zur Verwendung der Office 365-Endpunkten-Webdienst, finden Sie im Artikel [Office 365-URLs und IP-Adressbereiche](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Skripts PAC (Proxy Automatische Konfiguration)
<a name="BKMK_WebSvc"> </a>

Office 365-Administratoren können PAC (automatische Proxykonfiguration) Skripts erstellen, die auf Clientcomputern über WPAD oder GPO zugestellt werden können. Umgehen der Proxys für Office 365-Anforderungen von WAN oder VPN-Benutzern, da Office 365-Datenverkehr an die direkte internetverbindungen verwenden, sondern Durchlaufen des Firmennetzwerks befinden, können PAC Skripts verwendet werden.
  
#### <a name="office-365-security-features"></a>Office 365-Sicherheitsfeatures
<a name="BKMK_WebSvc"> </a>

Microsoft ist transparent zu Datacenter-Sicherheit, Sicherheit und Risikominderung auf Office 365-Servern und die Netzwerkendpunkte, die sie darstellen. Office 365 integrierte Sicherheitsfunktionen stehen zum Reduzieren der Netzwerk Sicherheitsrisiko dar, wie Data Loss Prevention, Virenschutz, Multi-Factor Authentication, Kunden Sperre im Feld, erweiterte Schutz, Office 365 Bedrohungsanalyse, Office 365 Secure Faktor, Exchange Online Protection und DDOS Netzwerksicherheit.
  
Weitere Informationen zu Microsoft-Rechenzentrum und globalen Netzwerk Sicherheit finden Sie im [Microsoft Trust Center](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Neue Office 365-Endpunkt-Kategorien
<a name="BKMK_Categories"> </a>

Office 365-Endpunkte stellen einen unterschiedlichen Satz von Netzwerkadressen und Subnetzen dar. Endpunkte möglicherweise URLs, IP-Adressen oder IP-Bereiche und einige Endpunkte mit bestimmten TCP/UDP-Ports aufgeführt sind. URLs können entweder einen vollqualifizierten Domänennamen wie *account.office.net* sein oder eine URL mit Platzhalter like * \*. office365.com*.
  
> [!NOTE]
> Die Speicherorte der Office 365-Endpunkten innerhalb des Netzwerks werden nicht direkt auf den Speicherort der Office 365-Mandantendaten beziehen. Aus diesem Grund Kunden sollte bei Office 365 als Dienst verteilten und globale Aussehen und dürfen nicht versuchen, blockieren Netzwerkverbindungen mit Office 365-Endpunkten geografische Kriterien erfüllen.
  
In unserem vorherigen Anleitung für die Verwaltung von Office 365-Datenverkehr wurden in zwei Kategorien unterteilt werden, **erforderlich** und **Optional**Endpunkte organisiert. Endpunkte in jeder Kategorie erforderlichen unterschiedliche Optimierungen je nach der Wichtigkeit des Diensts, und viele Kunden konfrontiert Probleme in der Anwendung der gleichen Netzwerk Optimierungen auf die vollständige Liste der Office 365-URLs und IP-Adressen zu rechtfertigen. 
  
Im neuen Modell Endpunkten in drei Kategorien **Optimieren**, **erforderlich** und **Default**, Bereitstellen eines Priorität-basierte pivots an, wo Sie den Fokus Netzwerk-Optimierung bietet die besten leistungsverbesserungen getrennt werden und Rendite. Die Endpunkte werden in den oben genannten Kategorien basierend auf die Vertraulichkeit der effektiven Benutzerinteraktion zu Netzwerk Qualität, Volume und Leistung Umschlag Szenarien und einfache Implementierung konsolidiert. Empfohlene Optimierungen können die gleiche Weise an alle Endpunkte in einer bestimmten Kategorie angewendet werden.
  
- **Optimieren** Endpunkte für die Verbindung mit jedem Office 365-Dienst sind erforderlich, und stellen über 75 % der Office 365-Bandbreite, Verbindungen und Menge der Daten dar. Diese Endpunkte darstellen Office 365-Bereitstellungsszenarios, die die am häufigsten Beachtung von Netzwerk-Leistung, Wartezeit und Verfügbarkeit sind. Alle Endpunkte, die in Microsoft-Rechenzentren gehostet werden. Wird erwartet, dass die Änderungsrate an die Endpunkte in dieser Kategorie wesentlich niedriger als für die Endpunkte in der anderen zwei Kategorien sein. Diese Kategorie umfasst eine (der Reihenfolge der ~ 10) sehr kleine Gruppe von URLs und einem definierten Satz von IP-Subnetze Core Office 365-Arbeitslasten wie Exchange Online, SharePoint Online, Skype für Business Online und Microsoft-Teams dedizierte Schlüssel.

    Eine verkürzte Liste von gut definiert wichtige Endpunkten soll Ihnen helfen, Planen und Implementieren von hohem Wert Netzwerk Optimierungen für diese Ziele schneller und einfacher.

    Beispiele für *Optimieren* Endpunkte *https://outlook.office365.com* , *https://\<Mandanten\>. sharepoint.com* und *https://\<Mandanten\>-my.sharepoint.com* .

    Methoden zur Optimierung von umfassen:

  - Umgeht oder weißen *Optimieren* Endpunkte für Netzwerkgeräte und Dienste, die Datenverkehr abfangen, SSL Entschlüsselung, umfassende Paketinspektion und Content-Filterung ausführen.
  - Umgehen der lokalen Proxy Geräte und Cloud-basierten Proxydienste, die zum Durchsuchen von generischen Internet häufig verwendet.
  - Priorisieren der Auswertung dieser Endpunkte als voll vertrauenswürdig durch die Netzwerk-Infrastruktur und Umkreis-Systeme.
  - Reduzierung oder Vermeidung von WAN-Backhauling priorisieren und direkte verteilten Internet-basierte Ausgang für diese Endpunkte erreicht bald wie möglich Benutzer/Zweigstellen erleichtern.
  - Vereinfachen Sie direkte Verbindung mit dieser Cloud-Endpunkte für VPN-Benutzer durch die Implementierung von Split-tunneling.
  - Stellen Sie sicher, dass der Ausgang Routingpfad für diese Endpunkte IP-Adressen von DNS-namensauflösung zurückgegeben werden soll.
  - Diese Endpunkte für SD-WAN-Integration für die direkte Schäden, minimale Wartezeit in der nächsten Internet Peers Punkt der globalen Microsoft Network Weiterleitung zu priorisieren.

- **Zulassen** Endpunkte für die Verbindung mit bestimmten Office 365-Dienste und Features sind erforderlich, aber werden nicht als beachtet Leistung des Netzwerks und Wartezeit, die in der Kategorie *Optimieren* . Der allgemeine Netzwerk Speicherbedarf dieser Endpunkte aus Sicht der Bandbreite und Count ist ebenfalls erheblich kleiner. Diese Endpunkte zu Office 365 dediziert sind und in Microsoft-Rechenzentren gehostet werden. Eine Breite Palette von Office 365-Micro-Dienste und deren Abhängigkeiten (der Reihenfolge der ~ 100 URLs) darstellen, und wird erwartet, dass Sie mit einer höheren Geschwindigkeit als die in der Kategorie *Optimieren* ändern. Nicht alle Endpunkte in dieser Kategorie sind definierten dedizierte IP-Subnetze zugeordnet.

    Optimierungen für *Zulassen* Endpunkte Netzwerk können die Benutzeroberfläche von Office 365 erhöhen, doch diese Optimierungen Weitere spezifisch, um Änderungen an ihrem Netzwerk zu minimieren beschränken von möglicherweise einige Kunden entscheiden.

    Beispiele für *Zulassen* Endpunkte *https://\*. protection.outlook.com* und *https://accounts.accesscontrol.windows.net*.

    Methoden zur Optimierung von umfassen:

  - Umgeht oder weißen *Zulassen* Endpunkte für Netzwerkgeräte und Dienste, die Datenverkehr abfangen, SSL Entschlüsselung, umfassende Paketinspektion und Content-Filterung ausführen.
  - Priorisieren der Auswertung dieser Endpunkte als voll vertrauenswürdig durch die Netzwerk-Infrastruktur und Umkreis-Systeme.
  - Reduzierung oder Vermeidung von WAN-Backhauling priorisieren und direkte verteilten Internet-basierte Ausgang für diese Endpunkte erreicht bald wie möglich Benutzer/Zweigstellen erleichtern.
  - Stellen Sie sicher, dass der Ausgang Routingpfad für diese Endpunkte IP-Adressen von DNS-namensauflösung zurückgegeben werden soll.
  - Diese Endpunkte für SD-WAN-Integration für die direkte Schäden, minimale Wartezeit in der nächsten Internet Peers Punkt der globalen Microsoft Network Weiterleitung zu priorisieren.

- **Standardmäßige** Endpunkte stehen für Office 365-Dienste und Abhängigkeiten, die Optimierung ist nicht erforderlich, und von Kunden Networks als normale Internet Datenverkehr gebunden behandelt werden können. Beachten Sie, dass einige Endpunkte in dieser Kategorie nicht in Microsoft-Rechenzentren gehostet werden können. Beispiele für *https://odc.officeapps.live.com* und *https://appexsin.stb.s-msn.com*.

Weitere Informationen zu Office 365-Netzwerk an Optimierungstechniken finden Sie im Artikel [Verwalten von Office 365-Endpunkten](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Vergleich zwischen Umkreisnetzwerk Netzwerksicherheit mit Endgeräte-Sicherheit
<a name="BKMK_SecurityComparison"> </a>

Das Ziel der traditionellen Netzwerksicherheit ist das Unternehmensnetzwerk Umkreisnetzwerk vor Eindringlingen und bösartige Angriffe verstärken. Wie Organisationen Office 365 einführen, werden einige Netzwerkdienste und Daten teilweise oder vollständig in die Cloud migriert. Wie eine grundlegende Änderung Netzwerkarchitektur der Fall ist, ist dieser Prozess eine erneute Auswertung der Netzwerksicherheit, die neue Faktoren berücksichtigt erforderlich:
  
- Clouddiensten angenommen werden, Netzwerkdienste und Daten zwischen lokalen Rechenzentren und der Cloud verteilt sind, und Sicherheit des Umkreisnetzwerks ist nicht mehr auf einem eigenen ausreichend.
- Remotebenutzer auf Unternehmensressourcen sowohl in lokalen Rechenzentren und in der Cloud aus nicht gesteuerte Orte wie privat-, Hotels und Cafés.
- Spezielle Sicherheitsfeatures können Clouddiensten zunehmend integriert werden und potenziell ergänzen oder ersetzen vorhandene Security-Systeme.

Microsoft bietet eine Vielzahl von Office 365 Sicherheitsfeatures und enthält einen verbindlichen Leitfaden für den Einsatz von bewährten Sicherheitsmethoden, mit denen Sie Daten und das Netzwerk Sicherheit für Office 365 sicherstellen können. Die folgenden: empfohlene bewährte Methoden
  
- **Mehrstufige Authentifizierung für die Verwendung (mehrstufiger Authentifizierung das)** Mehrstufiger Authentifizierung das hinzugefügt einer Strategie für die sichere Kennwörter durch Benutzer auffordern, bestätigen einen Telefonanruf, Textnachricht oder eine app-Benachrichtigung über ein Telefon smart nach ordnungsgemäß Sie ihr Kennwort eingeben eine zusätzliche Schutzebene.

- **Verwenden Sie Office 365-Cloud App-Sicherheit** Einrichten von Richtlinien zur abweichenden Aktivitäten verfolgen und handeln. Benachrichtigungen mit Office 365-Cloud-App-Sicherheit einrichten, sodass Administratoren ungewöhnliche oder riskant Benutzeraktivität, wie große Datenmengen herunterladen überprüfen können mehrere Fehler Anmeldeversuche oder Verbindungen aus einem unbekannten oder gefährlicher IP-Adressen.

- **Konfigurieren von Data Loss Prevention (DLP)** DLP können Sie vertrauliche Daten zu identifizieren und Richtlinien erstellen, die verhindern, dass Ihre Benutzer versehentlich oder absichtlich Datenfreigabe. DLP eignet sich für Office 365, einschließlich Exchange Online, SharePoint Online und OneDrive, damit die Benutzer kompatible bleiben können, ohne ihren Workflow zu unterbrechen.

- **Kunden-Lockbox verwenden** Ein Office 365-Administrator können Kunden Lockbox Sie steuern, wie ein Microsoft-Supportmitarbeiter während einer Sitzung auf Ihre Daten zugreift. In Fällen, in denen der Engineer Zugriff auf Ihre Daten erfordert zu behandeln und ein Problem beheben, können Kunden Lockbox Sie genehmigen oder Ablehnen der Access-Anforderung.

- **Verwenden Sie sichere Bewertung der Office 365** Sichere Score ist ein Analytics Sicherheitstool, die empfiehlt, was Sie tun können, um Risiko zu reduzieren. Sichere Faktor befasst sich mit Ihren Office 365-Einstellungen und Aktivitäten und miteinander verglichen, an einer Grundlinie von Microsoft hergestellt. Erhalten Sie eine Bewertung basierend auf wie ausgerichtete Sie mit bewährten Methoden für die Sicherheit sind.

Ein ganzheitlichen Ansatz für erweiterte Sicherheit sollte Berücksichtigung der folgenden enthalten:
  
- Umschalttaste Hervorhebung von Sicherheit in Richtung Endpunkt Sicherheit durch Anwenden von Cloud-basierten und Sicherheitsfeatures von Office-Client.
  - Reduzieren des Sicherheitsbereichs in das Rechenzentrum
  - Aktivieren Sie die entsprechende Vertrauensstellung für Benutzer Geräte im Büro oder an Remotestandorten
  - Sichern den Speicherort und den Speicherort im Fokus
  - Verwaltete Benutzer Computern haben höhere Vertrauensstellung mit Endgeräte-Sicherheit
- Verwalten der Informationssicherheit für alle ganzheitlich Konzentration nicht ausschließlich auf das Umkreisnetzwerk
  - Definieren Sie WAN und Erstellen von Perimeter Network Security zulassen von vertrauenswürdigen Datenverkehr Sicherheitsvorkehrungen zu umgehen und nicht verwaltete Geräten zu Gast Wi-Fi-Netzwerken trennen.
  - Reduziert die sicherheitsanforderungen des Unternehmens Rands WAN-Netzwerk
  - Einige Umkreis-Sicherheit Netzwerkgeräte wie Firewalls ist weiterhin erforderlich, aber laden gesunken
  - Stellt sicher lokalen Ausgang für Office 365-Datenverkehr
- Verbesserungen können inkrementell wie im Abschnitt [inkrementelle Optimierung](office-365-network-connectivity-principles.md#BKMK_IncOpt) beschrieben behandelt werden. Einige Optimierungstechniken bieten möglicherweise eine bessere Kosten-/Nutzen Verhältnisse je nach Ihrer Netzwerkarchitektur und sollten Sie die Optimierungen, die für Ihre Organisation sinnvollsten.

Weitere Informationen zu Office 365-Sicherheit und Compliance finden Sie unter [Übersicht über Sicherheit und Einhaltung von Vorschriften in Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Inkrementelle Optimierung
<a name="BKMK_IncOpt"> </a>

Wir haben das ideale Network Connectivity-Modell für SaaS weiter oben in diesem Artikel dargestellt, aber für viele große Organisationen mit in der Vergangenheit komplexen Netzwerkarchitekturen, es wird nicht praktikabel direkt alle diese Änderungen vornehmen. In diesem Abschnitt erläutern wir eine Anzahl von inkrementellen Änderungen, die dazu beitragen kann, die um Office 365-Leistung und Zuverlässigkeit zu verbessern.
  
Die Methoden, mit denen Sie Office 365-Datenverkehr optimieren variiert je nach Topologie des Netzwerks und die Netzwerkgeräte implementiert wurden. Große Unternehmen mit zahlreichen Standorten und komplexe Netzwerk Sicherheitsmaßnahmen müssen eine Strategie entwickeln, die enthält die meisten oder alle der [Office 365-Diensten Prinzipien](office-365-network-connectivity-principles.md#BKMK_Principles) Sie im Abschnitt aufgeführt werden, während nur kleinere Organisationen möglicherweise Grundsätze ein oder zwei berücksichtigen müssen.
  
Sie können als inkrementelle Prozess, Optimierung beinahe jede Methode nacheinander anwenden. Die folgende Tabelle enthält wichtige Methoden zur Optimierung von in der Reihenfolge der ihr Einfluss auf die Wartezeit und Zuverlässigkeit für die größte Zahl von Benutzern.
  
|**Optimierungsmethode**|**Beschreibung**|**Auswirkung**|
|:-----|:-----|:-----|
|Lokalen DNS-Auflösung und Internet Ausgang  <br/> |Bereitstellen von lokalen DNS-Servern an jedem Standort aus, und überprüfen Sie Ausgang, Office 365-Verbindungen mit dem Internet möglichst auf den Standort des Benutzers.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässige Verbindung für den nächsten Einstiegspunkt in Office 365  <br/> |
|Hinzufügen von regionalen Ausgang Punkt  <br/> |Wenn Ihres Unternehmensnetzwerks mehrere Standorte, wird jedoch nur eine Austritt verfügt, fügen Sie regionale Ausgang Punkt zum Aktivieren von Benutzern, die engsten Einstiegspunkt in Office 365 herzustellen.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässige Verbindung für den nächsten Einstiegspunkt in Office 365  <br/> |
|Proxies umgehen und Prüfung Geräte  <br/> |Konfigurieren von Browsern mit PAC-Dateien, die Office 365-direkt an Ausgang Punkt Anfragen.  <br/> Konfigurieren von Edge-Routern und Firewalls zulassen von Office 365-Datenverkehr ohne Prüfung.  <br/> | Minimieren der Wartezeit  <br/>  Reduzieren Sie die Belastung Netzwerkgeräte  <br/> |
|Direkte Verbindung für VPN-Benutzer aktivieren  <br/> |Aktivieren Sie für VPN-Benutzer Office 365-Verbindungen die Verbindung direkt über das Netzwerk des Benutzers und nicht über die VPN-Tunnels durch die Implementierung von Split-tunneling.  <br/> | Minimieren der Wartezeit  <br/>  Verbessern der zuverlässige Verbindung für den nächsten Einstiegspunkt in Office 365  <br/> |
|Migrieren von herkömmlichen WAN zu SD-WAN  <br/> |SD-WANs (Software definiert Wide Area Networks) WAN-Verwaltung zu vereinfachen und Verbessern der Leistung durch herkömmliche WAN-Router durch virtuelle Appliances, ähnelt die Virtualisierung von Compute-Ressourcen unter Verwendung von virtuellen Computern (VMs) ersetzt.  <br/> | Verbessern der Leistung und verwaltbarkeit von WAN-Datenverkehr  <br/>  Reduzieren Sie die Belastung Netzwerkgeräte  <br/> |
