---
title: Netzwerkplanung mit ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Express Route für Office 365 bietet Layer 3-Konnektivität zwischen dem Netzwerk und den Rechenzentren von Microsoft. Die Schaltungen verwenden BGP-Routenankündigungen (Border Gateway Protocol) der Front-End-Server von Office 365. Aus der Perspektive Ihrer lokalen Geräte, wenn Sie den richtigen TCP/IP-Pfad zu Office 365 auswählen müssen, wird Azure Express Route als Alternative zum Internet angesehen.
ms.openlocfilehash: 459850a29e87650f1aecfc6a6977cd6e5b77ae07
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069701"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Netzwerkplanung mit ExpressRoute für Office 365

Express Route für Office 365 bietet Layer 3-Konnektivität zwischen dem Netzwerk und den Rechenzentren von Microsoft. Die Schaltungen verwenden BGP-Routenankündigungen (Border Gateway Protocol) der Front-End-Server von Office 365. Aus der Perspektive Ihrer lokalen Geräte, wenn Sie den richtigen TCP/IP-Pfad zu Office 365 auswählen müssen, wird Azure Express Route als Alternative zum Internet angesehen.
  
Azure Express Route fügt einen direkten Pfad zu einer bestimmten Gruppe unterstützter Features und Dienste hinzu, die von Office 365-Servern in Microsoft-Rechenzentren angeboten werden. Azure Express Route ersetzt nicht die Internetkonnektivität in Microsoft-Rechenzentren oder grundlegende Internetdienste wie Domänennamensauflösung. Azure Express Route und Ihre Internet Schaltkreise sollten gesichert und redundant sein.
  
In der folgenden Tabelle werden einige Unterschiede zwischen den Internet-und Azure Express Route-Verbindungen im Kontext von Office 365 hervorgehoben.

|**Unterschiede bei der Netzwerkplanung**|**Internet Netzwerkverbindung**|**Express Route-Netzwerkverbindung**|
|:-----|:-----|:-----|
| Zugriff auf erforderliche Internetdienste, einschließlich;  <br/>  DNS-Namensauflösung  <br/>  Zertifikatsperrüberprüfung  <br/>  Netzwerke für die Inhaltsübermittlung  <br/> |Ja  <br/> |Anforderungen an Microsoft owned DNS-und/oder CDN-Infrastrukturen können das Express Route-Netzwerk verwenden.  <br/> |
| Zugriff auf Office 365-Dienste, einschließlich;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office Online  <br/>  Office 365-Portal und-Authentifizierung  <br/> |Ja, alle Anwendungen und Features  <br/> |Ja, [bestimmte Anwendungen und Features](https://aka.ms/o365endpoints) <br/> |
|Lokale Sicherheit im Umkreis.  <br/> |Ja  <br/> |Ja  <br/> |
|Planung der Hochverfügbarkeit.  <br/> |Failover zu einer alternativen Internetnetzwerkverbindung  <br/> |Failover zu einer alternativen Express Route-Verbindung  <br/> |
|Direkte Verbindung mit einem vorhersagbaren Netzwerkprofil.  <br/> |Nein  <br/> |Ja  <br/> |
|IPv6-Konnektivität.  <br/> |Ja  <br/> |Ja  <br/> |

Erweitern Sie die Titel unten, um weitere Informationen zur Netzwerkplanung zu finden. Außerdem haben wir eine 10-teilige [Azure Express Route für Office 365-Schulungs](https://channel9.msdn.com/series/aer) Reihe aufgenommen, die tiefer taucht.

## <a name="existing-azure-expressroute-customers"></a>Vorhandene Azure Express Route-Kunden

Wenn Sie eine vorhandene Azure Express Route-Schaltung verwenden und Office 365-Verbindungen über diese Schaltung hinzufügen möchten, sollten Sie sich die Anzahl von Stromkreisen, Ausgangs Standorten und Größe der Schaltkreise ansehen, um sicherzustellen, dass Sie die Anforderungen Ihrer Office 365-Nutzung erfüllen. Die meisten Kunden benötigen zusätzliche Bandbreite, und viele erfordern zusätzliche Schaltungen.
  
Um den Zugriff auf Office 365 über Ihre vorhandenen Azure Express Route-Schaltungen zu ermöglichen, [Konfigurieren Sie die Routenfilter](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) , um sicherzustellen, dass auf die Office 365-Dienste zugegriffen werden kann.
  
Das Azure Express Route-Abonnement ist kundenzentriert, was bedeutet, dass Abonnements an Kunden gebunden sind. Als Kunde können Sie mehrere Azure Express Route-Schaltungen haben und über diese Schaltungen auf viele Microsoft Cloud-Ressourcen zugreifen. Sie können beispielsweise auswählen, dass Sie auf einen Azure Hosted Virtual Machine, einen Office 365-Testmandanten und einen Office 365-Produktions Mandanten über ein paar redundanter Azure Express Route-Schaltungen zugreifen möchten.
  
In dieser Tabelle werden die beiden Arten von Peering-Beziehungen erläutert, die Sie für Ihre Schaltungen implementieren können.

|**Peering-Beziehung**|**Azure privat**|**Microsoft**|
|:-----|:-----|:-----|
|**Dienste** <br/> |IaaS: virtuelle Azure-Computer  <br/> |PaaS: Azure Public Services  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Verbindungs Initiierung * * * * <br/> |Von Kunden zu Microsoft  <br/> Microsoft-zu-Kunde  <br/> |Von Kunden zu Microsoft  <br/> Microsoft-zu-Kunde  <br/> |
|**QoS-Unterstützung** <br/> |Keine QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS unterstützt derzeit nur Skype for Business.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Bandbreitenplanung für Azure Express Route

Jeder Office 365-Kunde verfügt über eindeutige Bandbreitenanforderungen je nach Anzahl der Personen an den einzelnen Standorten, wie aktiv er mit jeder Office 365-Anwendung ist, und anderen Faktoren wie der Verwendung von lokalen oder hybriden Geräten und Konfigurationen der Netzwerksicherheit.
  
Eine zu geringe Bandbreite führt zu Staus, erneuten Datenübertragungen und unvorhersehbaren Verzögerungen. Eine zu große Bandbreite führt zu unnötigen Kosten. In einem vorhandenen Netzwerk wird die Bandbreite oft im Hinblick auf die verfügbare Kapazität auf dem Circuit als Prozentsatz bezeichnet. Eine Kapazität von 10% wird wahrscheinlich zu Staus führen und eine Kapazität von 80% bedeutet im allgemeinen unnötige Kosten. Die Standardzuweisungen für die Kopffreiheit sind 20% bis 50%.
  
Um die richtige Bandbreite zu ermitteln, besteht der beste Mechanismus darin, Ihre vorhandene Netzwerkauslastung zu testen. Dies ist die einzige Möglichkeit, um die Verwendung und die Notwendigkeit zu wahren, da jede Netzwerkkonfiguration und-Anwendung in gewisser Weise eindeutig ist. Bei der Messung möchten Sie genau auf die gesamte Bandbreite, Latenz und TCP-Überlastung achten, um Ihre Netzwerkanforderungen zu verstehen.
  
Wenn Sie über eine geschätzte Baseline verfügen, die alle Netzwerkanwendungen umfasst, führen Sie Pilot Office 365 mit einer kleinen Gruppe aus, die die verschiedenen Profile der Personen in Ihrer Organisation umfasst, um die tatsächliche Nutzung zu ermitteln, und verwenden Sie die beiden Messungen, um die Anzahl der die Bandbreite, die Sie für jeden Office-Standort benötigen. Wenn bei den Tests Latenz-oder TCP-Überlastungsprobleme auftreten, müssen Sie den Ausstieg möglicherweise näher an die Personen mit Office 365 verschieben oder eine intensive NETZWERKÜBERPRÜFUNG wie die SSL-Entschlüsselung/-Überprüfung entfernen.
  
Alle unsere Empfehlungen für die Art der Netzwerkverarbeitung, die empfohlen wird, gelten sowohl für Express Route-als auch für Internet-Schaltungen. Das gleiche gilt für die restlichen Anweisungen auf unserer [Website zur Leistungsoptimierung](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Anwenden von Sicherheitskontrollen auf Azure Express Route für Office 365-Szenarien

Das Sichern der Azure Express Route-Konnektivität beginnt mit den gleichen Prinzipien wie die Sicherung der Internet Konnektivität. Viele Kunden wählen die Bereitstellung von Netzwerk-und Umkreis Steuerungen entlang des Express Route-Pfads, der Ihr lokales Netzwerk mit Office 365 und anderen Microsoft-Clouds verbindet. Diese Steuerelemente können Firewalls, Anwendungsproxys, Verhinderung von Datenverlust, Intrusionserkennung, Intrusion Prevention-Systeme usw. enthalten. In vielen Fällen wenden Kunden unterschiedliche Steuerstufen auf Datenverkehr an, der von einem lokalen Microsoft-System initiiert wird, im Vergleich zu Datenverkehr, der von Microsoft zum lokalen Kundennetzwerk gestartet wird, im Vergleich zu Datenverkehr, der von einem lokalen Standort zu einem allgemeinen Internet Ziel.
  
Hier einige Beispiele für die Integration der Sicherheit in das [Express Route-Verbindungsmodell](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) , das Sie bereitstellen möchten.

|**Express Route-Integrations Option**|**Umkreis Modell für Netzwerksicherheit**|
|:-----|:-----|
|Co-Location bei einem Cloud Exchange  <br/> |Installieren Sie neue oder nutzen Sie vorhandene Security/Perimeter-Infrastruktur in der Co-Location-Einrichtung, in der die Express Route-Verbindung hergestellt wird.  <br/> Nutzen Sie die Co-Location-Fazilität ausschließlich für Routing/Verbindungs Zwecke und für die Rücktransport Verbindung von der Co-Location-Einrichtung zur lokalen Security/Perimeter-Infrastruktur.  <br/> |
|Punkt-zu-Punkt-Ethernet  <br/> |Beenden Sie die Punkt-zu-Punkt-Express Route-Verbindung im vorhandenen lokalen Speicherort der Sicherheit/Umkreis Infrastruktur.  <br/> Installieren Sie eine neue Sicherheits-/Umkreis Infrastruktur für den Express Route-Pfad, und beenden Sie die Punkt-zu-Punkt-Verbindung dort.  <br/> |
|Any-to-any-IPVPN  <br/> |Nutzen Sie eine vorhandene lokale Sicherheit/Umkreis Infrastruktur an allen Standorten, die in den für Express Route für Office 365-Konnektivität verwendeten IPVPN.  <br/> Haarnadel das für Express Route für Office 365 verwendete IPVPN zu bestimmten lokalen Standorten, die als Sicherheit/Umkreis dienen.  <br/> |

Einige Dienstanbieter bieten außerdem verwaltete Sicherheit/Perimeter-Funktionalität als Teil ihrer Integrationslösungen mit Azure Express Route.
  
Bei der Topologie-Platzierung der Netzwerk-/Sicherheitsperimeter-Optionen, die für Express Route für Office 365-Verbindungen verwendet werden, sind folgende weitere Überlegungen zu beachten:
  
- Die tiefen-und typsicherheits-Steuerelemente können sich auf die Leistung und Skalierbarkeit der Office 365-Benutzeroberfläche auswirken.

- Ausgehende (lokale-\>Microsoft) und eingehende (Microsoft-\>lokale) [falls aktiviert]-Abläufe können unterschiedliche Anforderungen erfüllen. Diese sind wahrscheinlich unterschiedlich als ausgehend zu allgemeinen Internet Destinationen.

- Die Office 365-Anforderungen für Ports/Protokolle und erforderliche IP-Subnetze sind identisch, unabhängig davon, ob Datenverkehr über Express Route für Office 365 oder über das Internet weitergeleitet wird.

- Die topologische Platzierung des Kunden Netzwerks/der Sicherheitskontrollen bestimmt das ultimative End-to-End-Netzwerk zwischen dem Benutzer und dem Office 365-Dienst und kann erhebliche Auswirkungen auf die Netzwerkwartezeit und die Überlastung haben.

- Kunden werden aufgefordert, Ihre Sicherheits-/Umkreis Topologie für die Verwendung mit Express Route für Office 365 gemäß den bewährten Methoden für Redundanz, hohe Verfügbarkeit und Notfallwiederherstellung zu entwerfen.

Nachfolgend finden Sie ein Beispiel für die Woodgrove Bank, die die verschiedenen Azure Express Route-Konnektivitäts-Optionen mit den oben besprochenen Umkreis Sicherheitsmodellen vergleicht.
  
### <a name="example-1-securing-azure-expressroute"></a>Beispiel 1: Sichern von Azure Express Route
  
Die Woodgrove Bank erwägt die Implementierung von Azure Express Route und nach der Planung der optimalen Architektur für das [Routing mit Express Route für Office 365](routing-with-expressroute.md) und nachdem Sie die obigen Leitlinien zum Verständnis der Bandbreitenanforderungen verwendet haben, bestimmen Sie die beste Methode zum Sichern des Umfangs.
  
Für Woodgrove, eine multinationale Organisation mit Standorten auf mehreren Kontinenten, muss sich die Sicherheit über alle Umkreis Bereiche erstrecken. Die Option für optimale Konnektivität für Woodgrove ist eine Multi-Point-Verbindung mit mehreren Peering-Standorten rund um den Globus, um die Anforderungen Ihrer Mitarbeiter auf jedem Kontinent zu erfüllen. Jeder Kontinent umfasst redundante Azure-Express Route-Schaltungen innerhalb des Kontinents, und die Sicherheit muss alle diese Bereiche umfassen.
  
Die vorhandene Infrastruktur von Woodgrove ist zuverlässig und kann die zusätzliche Arbeit bewältigen, sodass die Woodgrove Bank in der Lage ist, die Infrastruktur für Ihre Azure-Express Route und die Internet Perimeter-Sicherheit zu nutzen. Wenn dies nicht der Fall wäre, könnte Woodgrove sich entscheiden, zusätzliche Geräte zu erwerben, um die vorhandenen Geräte zu ergänzen oder einen anderen Verbindungstyp zu behandeln.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Hohe Verfügbarkeit und Failover mit Azure Express Route
<a name="BKMK_high-availability"> </a>

Es wird empfohlen, mindestens zwei aktive Stromkreise von jedem Ausstieg mit Express Route an Ihren Express Route-Anbieter zu über stellen. Dies ist die häufigste Stelle, an der Fehler für Kunden angezeigt werden, und Sie können Sie problemlos vermeiden, indem Sie ein paar aktiver/aktiver Express Route-Schaltungen aktivieren. Außerdem empfehlen wir mindestens zwei aktive/aktive Internet-Schaltungen, da viele Office 365-Dienste nur über das Internet verfügbar sind.
  
Innerhalb des Ausgangspunkts Ihres Netzwerks gibt es viele andere Geräte und Stromkreise, die eine entscheidende Rolle bei der Wahrnehmung von Verfügbarkeit spielen. Diese Teile ihrer Verbindungsszenarien werden nicht durch Express Route oder Office 365-SLAs abgedeckt, Sie spielen jedoch eine entscheidende Rolle bei der End-to-End-Dienstverfügbarkeit, wie Sie von Personen in Ihrer Organisation wahrgenommen werden.
  
Konzentrieren Sie sich auf die Personen, die Office 365 verwenden, und wenn ein Fehlschlagen einer Komponente die Benutzerfreundlichkeit des Diensts beeinträchtigen würde, suchen Sie nach Möglichkeiten, den Gesamtprozentsatz der betroffenen Personen einzuschränken. Wenn ein Failovermodus operativ Komplex ist, sollten Sie die Erfahrung der Völker für eine Wiederherstellung in Betracht ziehen und nach Betriebs einfachen und automatisierten Failover-Modi suchen.
  
Außerhalb Ihres Netzwerks verfügen Office 365, Express Route und Ihr Express Route-Anbieter über unterschiedliche Verfügbarkeitsstufen.
  
### <a name="service-availability"></a>Service Availability
  
- Office 365-Dienste werden durch definierte Vereinbarungen zum [Service Level](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)abgedeckt, die verfüg barkeits-und Verfügbarkeits Metriken für einzelne Dienste enthalten. Ein Grund dafür, dass Office 365 so hohe Dienst Verfügbarkeitsstufen aufrecht erhalten kann, ist die Möglichkeit für einzelne Komponenten, mit dem globalen Microsoft-Netzwerk nahtlos zwischen den vielen Microsoft-Rechenzentren zu Failover. Dieses Failover erstreckt sich vom Datencenter und Netzwerk auf mehrere Internet-Ausstiegspunkte und ermöglicht ein nahtloses Failover aus der Perspektive der Benutzer, die den Dienst verwenden.

- Express Route [bietet eine SLA zur Verfügbarkeit von 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) für einzelne dedizierte Stromkreise zwischen dem Microsoft-netzwerkedgeserver und dem Express Route-Anbieter oder der Partner Infrastruktur. Diese Servicestufen werden auf der Express Route-Leitungsebene angewendet, die aus [zwei unabhängigen Verbindungen](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) zwischen den redundanten Microsoft-Geräten und den Netzwerkanbieter-Geräten an jedem Peering-Standort besteht.

### <a name="provider-availability"></a>Anbieter Verfügbarkeit
  
- Die Service Level-Arrangements von Microsoft halten bei Ihrem Express Route-Anbieter oder-Partner an. Dies ist auch der erste Ort, an dem Sie Entscheidungen treffen können, die sich auf Ihre Verfügbarkeitsstufe auswirken. Sie sollten die Architektur, die Verfügbarkeit und die Ausfallsicherheit von Ihrem Express Route-Anbieter zwischen Ihrem Umkreisnetzwerk und der Anbieterverbindung an jedem Microsoft-Peering-Standort genau bewerten. Achten Sie sowohl auf die logischen als auch auf die physikalischen Aspekte der Redundanz, die Peering-Ausrüstung, die bereitgestellten WAN-Schaltungen und alle zusätzlichen Dienste wie NAT-Dienste oder verwaltete Firewalls.

### <a name="designing-your-availability-plan"></a>Entwerfen des Verfügbarkeits Plans
  
Es wird dringend empfohlen, hohe Verfügbarkeit und Ausfallsicherheit in ihren End-to-End-Konnektivitäts Szenarien für Office 365 zu planen und zu entwerfen. Ein Entwurf sollte;
  
- keine einzelnen Fehlerquellen, einschließlich Internet-und Express Route-Schaltungen.

- minimieren Sie die Anzahl der betroffenen Personen und die Dauer dieser Auswirkungen für die meisten erwarteten Ausfälle.

- Optimierung für einfachen, wiederholbaren und automatischen Wiederherstellungsvorgang aus den meisten erwarteten Ausfalls Modi.

- Unterstützung der vollständigen Anforderungen des Netzwerkdatenverkehrs und der Funktionalität über redundante Pfade ohne erhebliche Beeinträchtigung.

Ihre Verbindungsszenarien sollten eine Netzwerktopologie aufweisen, die für mehrere unabhängige und aktive Netzwerkpfade zu Office 365 optimiert ist. Dadurch ergibt sich eine bessere End-to-End-Verfügbarkeit als eine Topologie, die nur für Redundanz auf der einzelnen Geräte-oder Geräteebene optimiert ist.
  
> [!TIP]
> Wenn Ihre Benutzer über mehrere Kontinente oder geographische Regionen verteilt sind und jeder dieser Standorte über redundante WAN-Leitungen mit einem einzigen lokalen Standort verbindet, auf dem sich eine einzelne Express Route-Schaltung befindet, werden Ihre Benutzer End-to-End-Dienstverfügbarkeit als ein Entwurf einer Netzwerktopologie, der unabhängige Express Route-Schaltungen umfasst, die die verschiedenen Regionen mit dem nächstgelegenen Peering-Standort verbinden.
  
Es wird empfohlen, mindestens zwei Express Route-Schaltungen für jeden Stromkreis zu über stellen, der mit einem anderen geografischen Peering-Standort verbunden ist. Sie sollten diese aktiv-aktiven paar von Stromkreisen für jede Region, in der Benutzer Express Route-Konnektivität für Office 365-Dienste verwenden. Dadurch kann jede Region während eines Notfalls verbunden bleiben, der sich auf einen Hauptstandort wie ein Rechenzentrum oder einen Peering-Standort auswirkt. Wenn Sie Sie als aktiv/aktiv konfigurieren, können Endbenutzer Datenverkehr über mehrere Netzwerkpfade verteilt werden. Dies reduziert den Umfang der betroffenen Personen während der Geräte-oder Netzwerk Ausrüstungs Ausfälle.
  
Es wird nicht empfohlen, eine einzelne Express Route-Schaltung mit dem Internet als Sicherung zu verwenden.
  
### <a name="example-2-failover-and-high-availability"></a>Beispiel 2: Failover und hohe Verfügbarkeit
  
Das Multi-geographische Design der Woodgrove Bank hat sich mit dem Routing, der Bandbreite und der Sicherheit befassen und muss jetzt eine hoch Verfügbarkeitsüberprüfung durchlaufen. Woodgrove denkt über die hohe Verfügbarkeit von drei Kategorien nach; Ausfallsicherheit, Zuverlässigkeit und Redundanz.
  
Ausfallsicherheit ermöglicht Woodgrove die schnelle Wiederherstellung von Fehlern. Zuverlässigkeit ermöglicht es Woodgrove, ein konsistentes Ergebnis innerhalb des Systems anzubieten. Redundanz ermöglicht es Woodgrove, zwischen einer oder mehreren gespiegelten Infrastruktur Instanzen zu wechseln.
  
Innerhalb jeder Edge-Konfiguration verfügt Woodgrove über redundante Firewalls, Proxys und IDs. Für Nordamerika verfügt Woodgrove über eine Edge-Konfiguration im Dallas-Datencenter und eine weitere Edge-Konfiguration im Virginia-Datencenter. Die redundante Ausrüstung an jedem Standort bietet Ausfallsicherheit für diesen Standort.
  
Die Netzwerkkonfiguration der Woodgrove Bank basiert auf einigen Grundprinzipien:
  
- Innerhalb jeder geografischen Region gibt es mehrere Azure Express Route-Schaltungen.

- Jeder Stromkreis innerhalb eines Bereichs kann den gesamten Netzwerkdatenverkehr innerhalb dieser Region unterstützen.

- Das Routing hat eindeutig einen oder anderen Pfad abhängig von Verfügbarkeit, Standort usw.

- Ein Failover zwischen Azure Express Route-Schaltungen erfolgt automatisch ohne zusätzliche Konfiguration oder Aktion, die von Woodgrove benötigt wird.

- Ein Failover zwischen Internet Schaltkreisen erfolgt automatisch ohne zusätzliche Konfiguration oder Aktion, die von Woodgrove benötigt wird.

In dieser Konfiguration mit Redundanz auf physischer und virtueller Ebene ist die Woodgrove Bank in der Lage, lokale Ausfallsicherheit, regionale Ausfallsicherheit und globale Ausfallsicherheit auf zuverlässige Weise bereitzustellen. Woodgrove hat diese Konfiguration gewählt, nachdem eine einzelne Azure Express Route-Schaltung pro Region ausgewertet wurde, und die Möglichkeit, ein Failover für das Internet durchführen zu können.
  
Wenn Woodgrove nicht über mehrere Azure Express Route-Schaltungen pro Region verfügen konnte, würde das Routing von Datenverkehr von Nordamerika zur Azure Express Route-Schaltung in Asien-Pazifik zu einer inakzeptablen Latenzzeit und zur erforderlichen DNS-Weiterleitungskonfiguration führen. Fügt die Komplexität hinzu.
  
Die Nutzung des Internets als Sicherungskonfiguration wird nicht empfohlen. Dies unterbricht das Zuverlässigkeits Prinzip von Woodgrove, was zu einer inkonsistenten Erfahrung mit der Verbindung führt. Darüber hinaus wäre eine manuelle Konfiguration erforderlich, um ein Failover in Anbetracht der konfigurierten BGP-Ankündigungen, der NAT-Konfiguration, der DNS-Konfiguration und der Proxykonfiguration durchführen zu können. Diese hinzugefügte Failover-Komplexität erhöht die Zeit für die Wiederherstellung und verringert die Diagnose und Problembehandlung der einzelnen Schritte.
  
Sie haben noch Fragen zur Planung und Implementierung von Traffic Management oder Azure Express Route? Lesen Sie den Rest unseres [Netzwerk-und Leistungs-Guidance](https://aka.ms/tune) oder die [Azure Express Route FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Arbeiten mit Azure Express Route-Anbietern
<a name="BKMK_high-availability"> </a>

Wählen Sie die Standorte Ihrer Schaltungen basierend auf Ihrer Bandbreite, Latenz, Sicherheit und hoher Verfügbarkeit. Sobald Sie wissen, welche Standorte Sie platzieren möchten, [Überarbeiten Sie die aktuelle Liste der Anbieter nach Regionen](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Arbeiten Sie mit Ihrem Anbieter oder Anbieter zusammen, um die besten Verbindungsoptionen, Point-to-Point, Multi-Point oder gehostet auszuwählen. Denken Sie daran, dass Sie die Verbindungsoptionen so kombinieren und anpassen können, dass die Bandbreite und andere redundante Komponenten Ihr Routing und das Design der Hochverfügbarkeit unterstützen.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen
<a name="BKMK_high-availability"> </a>

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Verwenden von BGP-Communities in Express Route für Office 365-Szenarien (Preview)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Express Route und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit Express Route](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche für Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
