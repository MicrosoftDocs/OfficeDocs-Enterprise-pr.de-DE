---
title: Netzwerkplanung mit ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: ITPro
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
description: ExpressRoute für Office 365 bietet Layer 3-Konnektivität zwischen dem Netzwerk und Microsoft Rechenzentren. Stromkreise verwenden Border Gateway Protocol (BGP) Route Werbung der Office 365 Front-End-Server. Wenn sie den richtigen TCP/IP-Pfad zu Office 365, auswählen, wird aus der Sicht von Ihrer lokalen Geräten Azure ExpressRoute als Alternative zum Internet angezeigt.
ms.openlocfilehash: 7a2c9cb8ee562c0527416aa83184de90cd204476
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897228"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Netzwerkplanung mit ExpressRoute für Office 365

ExpressRoute für Office 365 bietet Layer 3-Konnektivität zwischen dem Netzwerk und Microsoft Rechenzentren. Stromkreise verwenden Border Gateway Protocol (BGP) Route Werbung der Office 365 Front-End-Server. Wenn sie den richtigen TCP/IP-Pfad zu Office 365, auswählen, wird aus der Sicht von Ihrer lokalen Geräten Azure ExpressRoute als Alternative zum Internet angezeigt.
  
Azure ExpressRoute Fügt einen direkten Pfad zu einem bestimmten Satz von unterstützten Features und Dienste, die von Office 365-Servern in der Microsoft Rechenzentren angeboten werden. Azure ExpressRoute ersetzen keine Verbindung mit Microsoft-Rechenzentren oder grundlegende Internetdienste wie Auflösung des Domänennamens. Azure ExpressRoute und den Internet Stromkreisen sollte gesicherte und redundant sein.
  
In der folgenden Tabelle werden einige Unterschiede zwischen dem Internet und Azure ExpressRoute Verbindungen im Kontext von Office 365 behandelt.

|**Unterschiede bei der netzwerkplanung**|**Internet-Netzwerkverbindung**|**ExpressRoute-Verbindung**|
|:-----|:-----|:-----|
| Zugriff auf erforderliche Internetdienste, einschließlich;  <br/>  DNS-namensauflösung  <br/>  Certificate Revocation Überprüfung  <br/>  Netzwerke für die Inhaltsübermittlung  <br/> |Ja  <br/> |Anforderungen an Microsoft gehören, dass DNS und/oder CDN-Infrastruktur des Netzwerks ExpressRoute verwenden kann.  <br/> |
| Zugriff auf Office 365-Dienste, einschließlich;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office Online  <br/>  Office 365-Portal und Authentifizierung  <br/> |Ja, alle Programme und Features  <br/> |Ja, [bestimmte Anwendungen und Features](https://aka.ms/o365endpoints) <br/> |
|Lokale Sicherheit bei Umkreisnetzwerk.  <br/> |Ja  <br/> |Ja  <br/> |
|Planen der hohen Verfügbarkeit.  <br/> |Failover auf eine alternative Netzwerk Internetverbindung  <br/> |Failover auf eine alternative ExpressRoute-Verbindung  <br/> |
|Direkte Verbindung mit einem Netzwerkprofil vorhersehbare.  <br/> |Nein  <br/> |Ja  <br/> |
|IPv6-Konnektivität.  <br/> |Ja  <br/> |Ja  <br/> |

Erweitern Sie die Titel unten für weitere planungsanleitung Netzwerk. Wir haben auch eine 10-Teil [Azure ExpressRoute für Office 365-Schulung](https://channel9.msdn.com/series/aer) Reihe aufgezeichnet, die tiefer Mitte zu ziehen.

## <a name="existing-azure-expressroute-customers"></a>Bestehende Kunden von Azure ExpressRoute

Wenn Sie eine vorhandene Azure ExpressRoute Netzfrequenz verwenden und die Office 365-Diensten über diese Verbindung hinzufügen möchten, sollten Sie sehen Sie sich die Anzahl der Circuits Ausgang Speicherorte und Größe der Stromkreise sicherzustellen, dass sie den Bedürfnissen der Nutzung von Office 365 werden. Die meisten Kunden erfordern zusätzliche Bandbreite und viele weitere Schaltkreise erfordern.
  
Zum Aktivieren des Zugriffs auf Office 365 über den vorhandenen Azure ExpressRoute Stromkreisen werden [Routefilter konfigurieren](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) , um sicherzustellen, dass die Office 365-Diensten zugegriffen.
  
Das ExpressRoute Azure-Abonnement ist Kunden centric, Bedeutung Abonnements an Kunden gebunden sind. Als Kunde können Sie mehrere Azure ExpressRoute Circuits und viele Microsoft Cloud auf Ressourcen zugreifen können über diese Schaltkreise. Sie können beispielsweise auswählen eine Azure Zugriff auf den virtuellen Computer, ein Office 365-Mandanten Test und ein Office 365-produktionsmandanten über ein Paar von redundante Azure ExpressRoute Stromkreise gehostet.
  
Die folgende Tabelle erläutert die zwei Typen von Peers Beziehungen gewählte können zur Implementierung über den Stromkreisen.

|**Peers Beziehung**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Dienste** <br/> |IaaS: Azure-virtuelle Computer  <br/> |PaaS: Azure öffentliche Dienste  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Verbindung Initiation *** <br/> |Kunden-Microsoft-  <br/> Microsoft-Kunden  <br/> |Kunden-Microsoft-  <br/> Microsoft-Kunden  <br/> |
|**QoS-support** <br/> |Keine QoS  <br/> |QoS-<sup>1</sup> <br/> |

<sup>1</sup> QoS unterstützt Skype für Business nur zu diesem Zeitpunkt.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planen von Azure ExpressRoute Bandbreite

Aller Office 365-Kunden hat eindeutige Bandbreite muss nach der Anzahl der Personen an jedem Standort, wie aktiv sie mit jeder Anwendung Office 365 und anderen Faktoren, wie die Verwendung von lokalen oder Hybrid-Geräte und Netzwerk Sicherheitskonfigurationen sind.
  
Nicht genügend Bandbreite wird eine Überlastung, hohem von Daten und unvorhersehbares Verzögerungen führen. Mit zu hohem Bandbreite führt unnötige Kosten. Klicken Sie auf einem vorhandenen Netzwerk ist Bandbreite häufig im Hinblick auf die Größe des Reserve verfügbar auf der Netzfrequenz als Prozentsatz bezeichnet. 10 % Reserve wird wahrscheinlich Ergebnis in eine Überlastung und unnötige Kosten bedeutet 80 % Reserven im Allgemeinen müssen. Typische Reserven Ziel Zuweisungen werden 20 % bis 50 %.
  
Damit die richtige Ebene der Bandbreite ermittelt wird, ist die beste Möglichkeit testen Sie Ihre vorhandenen Netzwerk Auslastung. Dies ist die einzige Möglichkeit zum Abrufen einer true Messung der Verwendung des und müssen als jeder Netzwerkkonfiguration und Anwendungen sind einige eindeutige Weise. Beim Messen Sie möchten die insgesamt Bandbreitenverbrauch, Wartezeit und TCP Überlastung zu verstehen, Ihr Netzwerk achten müssen.
  
Einmal eine geschätzte Baseline, die alle Network Applications, pilot Office 365 mit eine kleine Gruppe enthält, die die verschiedenen Profile von Personen in Ihrer Organisation zum Bestimmen der tatsächlichen Verbrauch umfasst haben und die zwei Maße verwenden, um den Umfang der schätzen Bandbreite, benötigen Sie für jede Niederlassung benötigen. Wenn Wartezeit oder TCP Überlastung Probleme in der Tests gefunden vorhanden sind, müssen Sie die Ausgang näher an die Personen, die mit Office 365 verschieben oder Entfernen von intensiven Überprüfung wie SSL-Entschlüsselung/Überprüfung Netzwerk.
  
Alle unsere empfohlenen auf welche Art von Netzwerk-Verarbeitung empfohlen wird auf ExpressRoute und Internet Circuits angewendet wird. Dies gilt auch für den Rest dieses Handbuchs auf unsere [Performance tuning-Website](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Anwenden von Sicherheitssteuerelemente auf Azure ExpressRoute für Office 365-Szenarien

Sichern von Azure ExpressRoute Connectivity beginnt mit demselben Prinzip wie Internetkonnektivität sichern. Viele Kunden entscheiden sich zum Bereitstellen von Netzwerk- und Umkreis-Steuerelemente auf dem Herstellen einer Verbindung mit ihrem lokalen Netzwerk zu Office 365 und anderen Microsoft-Wolken ExpressRoute Pfad. Diese Steuerelemente möglicherweise Firewalls, Proxys, Daten verhindern von Informationsverlusten, unbefugten, Intrusion Prevention-Systeme und usw. umfassen. In vielen Fällen gelten Kunden verschiedene Ebenen von Steuerelementen für Datenverkehr aus lokalen und sollte an Microsoft, im Vergleich zu Datenverkehr von Microsoft Customer lokalen Netzwerk, im Vergleich zu Datenverkehr vom lokalen unterschiedlich sein und sollte eine allgemeine initiiert und sollte initiiert initiiert Internet-Ziel.
  
Nachfolgend finden Sie einige Beispiele für die Integration von Sicherheit mit dem [ExpressRoute Connectivity-Modell](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) , das Sie bereitstellen möchten.

|**ExpressRoute Integration-option**|**Netzwerk-Umkreis-Sicherheitsmodell**|
|:-----|:-----|
|Co-Location bei einem Cloud Exchange  <br/> |Neu installieren Sie oder nutzen Sie vorhandene Security/Umkreis-Infrastruktur Einrichtung gemeinsamer Speicherort, in dem die ExpressRoute-Verbindung hergestellt wird.  <br/> Nutzung gemeinsamer Speicherort Einrichtung ausschließlich für routing/interconnect Zwecke und Back Transport Verbindungen von Co-Location Facility in die lokale Security/Umkreis-Infrastruktur.  <br/> |
|Point-Ethernet  <br/> |Trennen Sie in der vorhandenen lokalen Security/Umkreis-Infrastruktur Ort Point ExpressRoute Verbindung.  <br/> Installieren von neuen Security/Umkreis-Infrastruktur, die bestimmte auf den Pfad ExpressRoute und beendet die Verbindung vorhanden.  <br/> |
|N: N-IPVPN  <br/> |Nutzen Sie eine vorhandene Infrastruktur mit lokalen Security/Umkreisnetzwerk an allen Standorten, die in der IPVPN für Office 365-Konnektivität für ExpressRoute verwendete egress.  <br/> Hairpin bestimmt die IPVPN für ExpressRoute für Office 365 verwendet, um bestimmte lokale Speicherorte als des Sicherheitsbereichs dienen soll.  <br/> |

Einige Dienstanbieter bieten auch verwaltete Security/Umkreis-Funktionalität als Teil ihrer Lösungen Integration mit Azure ExpressRoute.
  
Wenn Sie die Topologie Platzierung der Netzwerk-Sicherheit Umkreis-Optionen für ExpressRoute für Office 365-Verbindungen verwendet, sind folgende zusätzliche Überlegungen
  
- Die Netzwerk-Sicherheit Steuerelemente Tiefe und Typ möglicherweise Beeinträchtigung der Leistung und Skalierbarkeit des Benutzererlebnisses Office 365.

- Ausgehend (auf-lokale -\>Microsoft) und eingehenden (Microsoft -\>lokale) [Wenn aktiviert] fließt möglicherweise unterschiedliche Anforderungen. Dies sind wahrscheinlich an allgemeine Internet Ziele ausgehend unterscheidet.

- Office 365-Anforderungen für Ports-Protokolle und die erforderlichen IP-Subnetze sind gleich, ob Datenverkehr durch ExpressRoute für Office 365 oder über das Internet weitergeleitet wird.

- Topologie Platzierung der Steuerelemente Netzwerk/Sicherheit Kunden kann bestimmt das ultimative End-to-End-Netzwerk zwischen dem Benutzer und Office 365-Dienst und eine erhebliche Auswirkungen auf die Netzwerklatenz und Überlastung.

- Benutzer werden aufgefordert, ihre Security/Umkreis-Topologie für die Verwendung mit ExpressRoute für Office 365 gemäß den best Practices für Redundanz, hohe Verfügbarkeit und notfallwiederherstellung zu entwerfen.

Es folgt ein Beispiel der Woodgrove Bank, die die verschiedenen Optionen der Azure-ExpressRoute-Konnektivität mit den oben beschriebenen Umkreisnetzwerk Security-Modellen vergleicht.
  
### <a name="example-1-securing-azure-expressroute"></a>In Beispiel 1: Sichern von Azure ExpressRoute
  
Woodgrove Bank ist in Erwägung ziehen Azure ExpressRoute implementieren und nach dem Planen der optimalen Architektur für [Routing mit ExpressRoute für Office 365](routing-with-expressroute.md) und dem mit der obigen Anleitung um zu verstehen, erforderliche Bandbreite, sind sie bestimmen die bewährte Methode für ihre Umgebung sichern.
  
Sicherheit muss alle Perimeter erstrecken, für Woodgrove eine multinationale Organisation mit Standorten in mehreren Kontinenten. Die optimale Konnektivitätsoption für Woodgrove ist eine Verbindung mit mehreren Punkt mit mehreren Peers Standorten auf der ganzen Welt an die Bedürfnissen der Mitarbeiter in jeden Kontinent-service. Jeden Kontinent redundante Azure ExpressRoute Stromkreise innerhalb der Kontinent enthält, und Sicherheit muss alle diese umfassen.
  
Vorhandene Infrastruktur des Woodgrove zuverlässig und kann den zusätzlichen Aufwand verarbeiten, daher Woodgrove Bank kann die Infrastruktur für ihre Azure ExpressRoute und Internet Umkreis-Sicherheit verwenden. Wenn dies nicht der Fall waren, konnte Woodgrove verhindern, dass zusätzliche Geräte ihre vorhandenen Geräte ergänzen oder eine andere Art von Verbindung behandeln anschaffen.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Hohe Verfügbarkeit und Failover mit Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Es wird empfohlen, mindestens zwei aktiven Circuits aus jeder Ausgang mit ExpressRoute an Ihren Anbieter ExpressRoute bereitstellen. Dies ist die am häufigsten wir finden Sie unter Fehler für Kunden und Sie können es auf einfache Weise vermeiden, indem Sie ein Paar von aktiv/aktiv ExpressRoute Circuits-Bereitstellung. Wir empfehlen auch mindestens zwei aktiv/aktiv-Internet-Schaltkreise, da viele Office 365-Dienste nur über das Internet zur Verfügung stehen.
  
Innerhalb des Netzwerks Austritt sind viele andere Geräte und Circuits, die wie Personen Verfügbarkeit Wahrnehmung eine wichtige Rolle spielen. Diese Teile der Konnektivität Szenarien nicht von ExpressRoute oder Office 365 SLAs abgedeckt werden, aber sie spielt eine wichtige Rolle in der Verfügbarkeit Ende zum als wahrgenommene von Personen in Ihrer Organisation.
  
Konzentrieren Sie sich auf die Personen, die unter Verwendung der und erleben Sie die Verwendung des Diensts, suchen Sie nach Möglichkeiten zum Einschränken der Gesamtprozentsatz der betroffenen Personen Betrieb von Office 365, wenn es sich bei ein Fehler für jede Komponente ein Personen auswirken würde. Wenn ein Failovermodus den niedrigsten komplex ist, sollten Sie die Personen konferenzmöglichkeiten für einen längeren Zeitraum zur Wiederherstellung, und suchen Sie nach den niedrigsten einfache, automatische Failover Modi.
  
Außerhalb von Netzwerk, Office 365, ExpressRoute und Ihren ExpressRoute-Anbieter verfügen alle verschiedene Ebenen der Verfügbarkeit.
  
### <a name="service-availability"></a>Service Availability
  
- Office 365-Dienste werden mit klar definierten [Vereinbarungen zum Servicelevel](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx), behandelt, die ein Betriebszeit und Verfügbarkeit Metriken für einzelne Dienste enthalten. Ein Grund, die Office 365 solche hohe Verfügbarkeit Servicelevel ist die Möglichkeit für einzelne Komponenten an nahtlosen Failover zwischen der vielen Microsoft-Rechenzentren, über die globale Microsoft-Netzwerk verwalten können. Diese Failover aus dem Rechenzentrum und dem Netzwerk, die mehrere Internet Ausgang Punkte erweitert und ermöglicht das Failover nahtlos aus der Sicht der Personen, die Verwendung des Diensts.

- ExpressRoute [bietet eine Verfügbarkeit von 99,9 % SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) einzelne dedizierten Circuits zwischen dem Microsoft-Netzwerk und die ExpressRoute Anbieter oder Partner-Infrastruktur. Diese Service-Level gelten auf Ebene der ExpressRoute Verbindung besteht aus [zwei unabhängigen Verbindungen](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) zwischen der redundante Ausrüstung Microsoft und die Netzwerkgeräte Anbieter an jedem Standort Peers.

### <a name="provider-availability"></a>Provider-Verfügbarkeit
  
- Microsoft Service Level Modalitäten Beenden des ExpressRoute Anbieter oder Partner. Dies ist auch die zentrale Position, die Sie eine Auswahl treffen können, die Ihre Verfügbarkeit beeinflussen wird. Sie sollten die Architektur, Verfügbarkeit und ausfallsicherheit Merkmale des Anbieters ExpressRoute bietet eng bewerten, zwischen Umkreisnetzwerk und die Verbindung Anbieter an jedem Microsoft Peers Standort. Achten Sie besonders auf die logische und physische Aspekte der Redundanz, Peers Ausrüstung, WAN Circuits Netzbetreiber bereitgestellt und alle zusätzlichen Wert Dienste wie NAT-Dienste oder verwalteten Firewalls hinzufügen.

### <a name="designing-your-availability-plan"></a>Entwerfen Ihrer Verfügbarkeitsplan
  
Es wird dringend empfohlen, dass Sie planen und Entwerfen hohe Verfügbarkeit und ausfallsicherheit in Ihre End-to-End-Konnektivität Szenarien für Office 365. Ein Entwurf sollte enthalten;
  
- keine einzelnen Fehlerquellen, einschließlich Internet- und ExpressRoute Circuits.

- Minimieren die Anzahl der betroffenen Personen und die Dauer der Auswirkungen, diese für die meisten erwarteten verschiedene Arten von Ausfällen.

- Optimieren von am erwarteten verschiedene Arten von Ausfällen für die einfache, wiederholbare und automatische Wiederherstellung.

- die vollständigen topologieoption den Netzwerkverkehr und Funktionen über redundante Pfade ohne Beeinträchtigung der wesentlichen unterstützen.

Ihre Verbindung Szenarien sollte eine Netzwerktopologie enthalten, die für mehrere unabhängige und aktiv Netzwerkpfade zu Office 365 optimiert ist. Dies ergibt eine besser End-to-End-Verfügbarkeit als eine Topologie, die nur für Redundanz auf Ebene der einzelnen Gerät oder Geräte optimiert ist.
  
> [!TIP]
> Wenn Ihre Benutzer auf mehreren Kontinenten oder geografische Bereiche verteilt werden und die einzelnen Pfade stellt eine über redundante WAN Stromkreise an einen einfachen lokalen Speicherort Verbindung, in einer einzelnen ExpressRoute Netzfrequenz gespeichert ist, werden Ihre Benutzer kleiner bemerken End-to-End-Verfügbarkeit als ein Netzwerk Entwerfen der Topologie, die unabhängige ExpressRoute Circuits, mit denen die unterschiedlichen Regionen enthält auf die nächste peering zugänglich Speicherort.
  
Es wird empfohlen, mindestens zwei ExpressRoute Circuits mit jeder Verbindung herstellen einer Verbindung mit mit einem unterschiedlichen geografischen Peers Ort bereitstellen. Sie sollten diese aktiv / aktiv-Paar Stromkreise für jede Region bereitstellen, in dem Personen ExpressRoute Konnektivität für Office 365-Dienste verwendet werden soll. Dadurch wird jeder Region verbundenen während eines Notfalls bleiben, die einen größeren Standort wie ein Datencenter oder Peers Speicherort betrifft. Konfigurieren sie in als aktiv/aktiv kann Endbenutzer-Datenverkehrs über mehrere Netzwerkpfade verteilt werden. Dies reduziert den Bereich der Personen, die bei Gerät oder Network Equipment Ausfällen betroffen.
  
Es wird nicht empfohlen, eine einzelne ExpressRoute Verbindung mit dem Internet als Sicherungskopie verwenden.
  
### <a name="example-2-failover-and-high-availability"></a>Beispiel 2: Failover und hohe Verfügbarkeit
  
Woodgrove Bank mit mehreren geografischen Entwurf wurde unterzogen einen Überblick über routing, Bandbreite, Sicherheit und jetzt über eine hohe Verfügbarkeit Überprüfung wechseln muss. Woodgrove geht davon aus, Informationen zu hoher Verfügbarkeit umfassen drei Kategorien; Flexibilität, Zuverlässigkeit und Redundanz.
  
Resiliency ermöglicht Woodgrove, Fehlern schnell wiederherzustellen. Zuverlässigkeit ermöglicht Woodgrove ein konsistentes Ergebnis innerhalb des Systems anbieten möchten. Redundanz ermöglicht Woodgrove zu einer Verschiebung zwischen mindestens einen gespiegelten Instanzen der Infrastruktur.
  
In den einzelnen Konfigurationen Edge hat Woodgrove redundante Firewalls, Proxys und IDS. Nordamerika hat Woodgrove eine Konfiguration für Zugriffsedge im Rechenzentrum Dallas und eine andere Konfiguration für Zugriffsedge im Rechenzentrum Virginia. Die redundante Ausrüstung an jedem Standort bietet Flexibilität zu diesem Speicherort.
  
Die Netzwerkkonfiguration Woodgrove Bank basiert auf einige wichtige Prinzipien basiert:
  
- Innerhalb jeder Region und gibt es mehrere Azure ExpressRoute Circuits.

- Jede Verbindung innerhalb eines Bereichs kann alle des Netzwerkdatenverkehrs innerhalb der jeweiligen Region unterstützen.

- Routing wird deutlich bevorzugen eine oder den anderen Pfad je nach Verfügbarkeit, Speicherort und so weiter.

- Failover zwischen Azure ExpressRoute Circuits erfolgt automatisch ohne zusätzliche Konfiguration oder eine Aktion Woodgrove durchführen.

- Failover zwischen Internet Circuits erfolgt automatisch ohne zusätzliche Konfiguration oder eine Aktion Woodgrove durchführen.

Woodgrove Bank kann in dieser Konfiguration mit Redundanz auf Ebene der physischen und virtuellen lokalen Resiliency, regionalen Resiliency und globale Resiliency zuverlässige bieten. Woodgrove gewählt diese Konfiguration nach der Auswertung einer einzelnen Azure ExpressRoute Netzfrequenz pro Region als auch die Möglichkeit, Ausführen eines Failovers für mit dem Internet.
  
Wenn Woodgrove haben mehrere Azure ExpressRoute Circuits pro Region konnte, würde routing Datenverkehr in Nordamerika zu der Netzfrequenz Azure ExpressRoute in Asien-Pazifik akzeptable der Wartezeit und der erforderlichen DNS-Weiterleitungskonfiguration hinzufügen. erhöht die Komplexität.
  
Nutzen das Internet als eine Sicherung der Konfiguration wird nicht empfohlen. Dies Seitenumbrüche Woodgrove Zuverlässigkeit Prinzip resultierendes Inkonsistenzen mithilfe der Verbindung. Manueller Konfiguration wäre darüber hinaus erforderlich, damit das Failover Berücksichtigung der Werbung BGP, die konfiguriert wurden, NAT-Konfiguration, DNS-Konfiguration und der Proxy-Konfiguration. Dies hinzugefügt Failover Komplexität der Zeit bis zur Wiederherstellung erhöht und verringert die Fähigkeit zum Identifizieren und beheben die folgenden Schritte ausgeführt werden.
  
Noch Fragen zum Planen und Implementieren von Datenverkehr Management oder Azure ExpressRoute immer? Lesen Sie die restlichen [Anweisungen Netzwerk- und Leistung](https://aka.ms/tune) der oder die [Azure ExpressRoute – häufig gestellte Fragen](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Arbeiten mit Azure ExpressRoute-Anbieter
<a name="BKMK_high-availability"> </a>

Wählen Sie die Speicherorte der Stromkreise basierend auf Ihrer Bandbreite, Latenz, Sicherheit und hohe Verfügbarkeit zu planen. Wenn Sie die optimale Speicherorte wissen platzieren möchten auslöst, [Überprüfen Sie die aktuelle Liste der Anbieter nach Region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Arbeiten Sie mit Ihrer mindestens einen Authentifizierungsanbieter an die besten Konnektivitätsoptionen Point, Mehrpunkt oder gehostete auswählen. Beachten Sie, dass Sie kombinieren und die Konnektivitätsoptionen übereinstimmen, solange die Bandbreite und andere redundanten Komponenten Ihrer routing und hohe Verfügbarkeit entwerfen unterstützen können.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen
<a name="BKMK_high-availability"> </a>

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Verwenden von BGP-Communitys in ExpressRoute für Office 365-Szenarien (Vorschau)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
  
[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
