---
title: Implementieren von ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Express Route für Office 365 bietet einen alternativen Routingpfad zu vielen mit dem Internet verbundenen Office 365-Diensten. Die Architektur von Express Route für Office 365 basiert auf öffentlich zugänglichen IP-Präfixen von Office 365-Diensten, die bereits über das Internet in Ihre bereitgestellten Express Route-Schaltungen für eine spätere Umverteilung dieser IP-Präfixe in Netzwerk. Mit Express Route können Sie für viele Office 365-Dienste mehrere verschiedene Routingpfade über das Internet und über Express Route effektiv aktivieren. Dieser Status des Routings in Ihrem Netzwerk kann eine wesentliche Änderung der Entwicklung der internen Netzwerktopologie darstellen.
ms.openlocfilehash: e535135557f7f2f64077c1d926f120fff78dbd42
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491676"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementieren von ExpressRoute für Office 365

Express Route für Office 365 bietet einen alternativen Routingpfad zu vielen mit dem Internet verbundenen Office 365-Diensten. Die Architektur von Express Route für Office 365 basiert auf öffentlich zugänglichen IP-Präfixen von Office 365-Diensten, die bereits über das Internet in Ihre bereitgestellten Express Route-Schaltungen für eine spätere Umverteilung dieser IP-Präfixe in Netzwerk. Mit Express Route können Sie für viele Office 365-Dienste mehrere verschiedene Routingpfade über das Internet und über Express Route effektiv aktivieren. Dieser Status des Routings in Ihrem Netzwerk kann eine wesentliche Änderung der Entwicklung der internen Netzwerktopologie darstellen.
  
 **Status:** Vollständige Anleitung v2
  
Sie müssen Ihre Express Route für Office 365-Implementierung sorgfältig planen, um die Netzwerkkomplexität des Routings über eine dedizierte Leitung mit Routen zu ermöglichen, die in Ihr Kernnetzwerk und das Internet eingespritzt werden. Wenn Sie und Ihr Team die detaillierten Planungs-und Testschritte in diesem Handbuch nicht durchführen, besteht ein hohes Risiko, dass Sie bei aktivierter Express Route-Schaltung mit einem intermittierenden oder einem Totalverlust der Konnektivität zu Office 365-Diensten arbeiten.
  
Um eine erfolgreiche Implementierung zu erhalten, müssen Sie Ihre Infrastrukturanforderungen analysieren, detaillierte Netzwerkbewertung und-Entwurf durchlaufen, die Einführung schrittweise und kontrolliert planen und einen detaillierten Validierungs-und Testplan erstellen. Bei einer umfangreichen, verteilten Umgebung ist es nicht unüblich, dass Implementierungen mehrere Monate umfassen. Dieses Handbuch soll Ihnen bei der Planung helfen.
  
Große erfolgreiche Bereitstellungen können bei der Planung sechs Monate dauern und häufig Teammitglieder aus vielen Bereichen der Organisation einschließen, einschließlich Netzwerk-, Firewall-und Proxy Serveradministratoren, Office 365-Administratoren, Sicherheit, Endbenutzer Unterstützung, Projekt Verwaltung und Führungskräfte Sponsoring. Ihre Investition in den Planungsprozess verringert die Wahrscheinlichkeit, dass Bereitstellungsfehler auftreten, die zu Ausfallzeiten oder komplexen und kostspieligen Problembehandlung führen.
  
Wir erwarten, dass die folgenden Voraussetzungen erfüllt sein müssen, bevor dieser Einführungsleitfaden gestartet wird.
  
1. Sie haben eine Netzwerkbewertung durchgeführt, um zu ermitteln, ob Express Route empfohlen und genehmigt wurde.

2. Sie haben einen Express Route-Netzwerkdienst Anbieter ausgewählt. Hier finden Sie Details zu den [Express Route-Partnern und Peering-Standorten](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Sie haben bereits die [Express Route-Dokumentation](https://azure.microsoft.com/documentation/services/expressroute/) gelesen und verstanden, und Ihr internes Netzwerk kann die Voraussetzungen für Express Route erfüllen.

4. ihr team hat alle öffentlichen anleitungen und dokumentationen unter [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365) [https://aka.ms/ert](https://aka.ms/ert)gelesen und die [Azure express route für Office 365-schulungs](https://channel9.msdn.com/series/aer) reihe auf kanal 9 beobachtet, um sich mit wichtigen technischen details vertraut zu machen, einschließlich:

      - Die Internet Abhängigkeiten von SaaS-Diensten.

      - Vermeiden von asymmetrischen Routen und behandeln eines komplexen Routings.

      - Integrieren von Sicherheits-, Verfügbarkeits-und Anwendungsebenen-Steuerelementen

## <a name="begin-by-gathering-requirements"></a>Beginnen Sie mit der Erfassung von Anforderungen
<a name="requirements"> </a>

Legen Sie zunächst fest, welche Features und Dienste Sie in Ihrer Organisation einführen möchten. Sie müssen ermitteln, welche Funktionen der verschiedenen Office 365-Dienste verwendet werden sollen und welche Standorte in Ihrem Netzwerk Personen mit diesen Funktionen hosten werden. Mit dem Katalog von Szenarien müssen Sie die Netzwerkattribute hinzufügen, die für jedes dieser Szenarien erforderlich sind. wie ein eingehender und ausgehender Netzwerkdatenverkehr und ob die Office 365-Endpunkte über Express Route zur Verfügung stehen.
  
So erfassen Sie die Anforderungen Ihrer Organisation:
  
- Katalogisieren Sie den eingehenden und ausgehenden Netzwerkdatenverkehr für die Office 365-Dienste, die Ihre Organisation verwendet. Konsultieren Sie die Seite Office 365-URLs und IP-Adressbereiche für die Beschreibung der Abläufe, die unterschiedliche Office 365-Szenarien erfordern.

- Erfassen Sie Dokumentation der vorhandenen Netzwerktopologie mit Details zu Ihrem internen WAN-Backbone und der Topologie, der Konnektivität von Satellitenstandorten, der Konnektivität der letzten Meile-Benutzer, dem Routing zu Netzwerkperimeter-Ausgangspunkten und Proxy Diensten.

  - Identifizieren Sie eingehende Dienstendpunkte in den Netzwerkdiagrammen, mit denen Office 365 und andere Microsoft-Dienste eine Verbindung herstellen, und zeigen Sie sowohl Internet als auch vorgeschlagene Express Route-Verbindungspfade an.

  - Identifizieren Sie alle geographischen Benutzer Standorte und die WAN-Konnektivität Zwischenstand Orten, an denen Standorte derzeit einen Ausstieg ins Internet haben und an welchen Standorten ein Ausstieg an einen Express Route-Peering-Standort vorgeschlagen wird.

  - Identifizieren Sie alle edgegeräte, wie Proxys, Firewalls usw., und Katalogisieren Sie Ihre Beziehung zu Flows, die über das Internet und Express Route gehen.

  - Dokumentieren Sie, ob Endbenutzer über direktes Routing oder indirekten Anwendungsproxy für Internet-und Express Route-Datenströme auf Office 365-Dienste zugreifen.

- Fügen Sie dem Netzwerkdiagramm den Speicherort Ihrer Mandanten-und Meet-Me-Speicherorte hinzu.

- Schätzen Sie die erwarteten und beobachteten Merkmale der Netzwerkleistung und-Latenz von Hauptbenutzer Standorten zu Office 365. Beachten Sie, dass Office 365 eine globale und verteilte Gruppe von Diensten ist und Benutzer eine Verbindung zu Standorten herstellen, die sich möglicherweise vom Standort Ihres Mandanten unterscheiden. Aus diesem Grund wird empfohlen, die Wartezeit zwischen dem Benutzer und dem engsten Rand des globalen Microsoft-Netzwerks über Express Route und Internet Verbindungen zu messen und zu optimieren. Sie können Ihre Ergebnisse aus der Netzwerkbewertung zur Unterstützung dieser Aufgabe verwenden.

- AufListen von Unternehmensnetzwerk Sicherheit und Anforderungen an hohe Verfügbarkeit, die mit der neuen Express Route-Verbindung erfüllt werden müssen. So erhalten Benutzer beispielsweise weiterhin Zugriff auf Office 365 im Fall des Ausfalls des Internet Austritts oder Express Route.

- Dokument, in dem ein-und ausgehende Office 365-Netzwerk Flüsse den Internet Pfad verwenden und Express Route verwenden. Die Spezifika der geografischen Standorte Ihrer Benutzer und Details Ihrer lokalen Netzwerktopologie erfordern möglicherweise, dass sich der Plan von einem Benutzerstandort zu einem anderen unterscheidet.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Katalogisieren des ausgehenden und eingehenden Netzwerkdatenverkehrs
<a name="trafficCatalog"> </a>

Zur Minimierung des Routings und anderer Netzwerk Komplexitäten wird empfohlen, nur Express Route für Office 365 für die Netzwerkdatenverkehr zu verwenden, die aufgrund behördlicher Vorschriften oder als Ergebnis der Netzwerkbewertung für eine dedizierte Verbindung erforderlich sind. Darüber hinaus empfiehlt es sich, den Umfang des Express Route-Routings zu inszenieren und die ausgehenden und eingehenden Netzwerkdatenverkehr als unterschiedliche und eindeutige Phasen des Implementierungsprojekts zu erreichen. Bereitstellen von Express Route für Office 365 für nur vom Benutzer initiierte ausgehende Netzwerkdatenverkehr und überlassen des eingehenden Netzwerkdatenverkehrs über das Internet kann dazu beitragen, die zunehmende topologische Komplexität zu kontrollieren und die Risiken der Einführung zusätzlicher asymmetrischer Routing Möglichkeiten.
  
Ihr Netzwerkdaten Verkehrs Katalog sollte Auflistungen aller eingehenden und ausgehenden Netzwerkverbindungen enthalten, die Sie zwischen Ihrem lokalen Netzwerk und Microsoft haben.
  
- Ausgehende Netzwerkdatenverkehr sind Szenarien, in denen eine Verbindung von Ihrer lokalen Umgebung, beispielsweise von internen Clients oder Servern, mit einem Ziel der Microsoft-Dienste initiiert wird. Diese Verbindungen können direkt in Office 365 oder indirekt erfolgen, beispielsweise wenn die Verbindung über Proxy Server, Firewalls oder andere Netzwerkgeräte auf dem Pfad zu Office 365 übermittelt wird.

- Eingehende Netzwerkdatenverkehr sind Szenarien, in denen eine Verbindung von der Microsoft-Cloud zu einem lokalen Host initiiert wird. Diese Verbindungen müssen in der Regel Firewall und andere Sicherheitsinfrastrukturen durchlaufen, die von der Kunden Sicherheitsrichtlinie für extern entstandene Abläufe benötigt werden.

Lesen Sie den Abschnitt **sicherstellen von Routen Symmetrie** im Artikel [Routing mit express route für Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) , um festzustellen, welche Dienste eingehenden datenVerkehr senden und suchen Sie nach der spalte **Express Route für Office 365** im [Office 365 ](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)Referenzartikel zu Endpunkten, um die restlichen Verbindungsinformationen zu bestimmen.
  
Für jeden Dienst, für den eine ausgehende Verbindung erforderlich ist, sollten Sie die geplante Konnektivität für den Dienst beschreiben, einschließlich Netzwerkrouting, Proxykonfiguration, Paketüberprüfung und Bandbreitenanforderungen.
  
Für jeden Dienst, für den eine eingehende Verbindung erforderlich ist, benötigen Sie zusätzliche Informationen. Server in der Microsoft-Cloud stellen Verbindungen mit Ihrem lokalen Netzwerk her. um sicherzustellen, dass die Verbindungen ordnungsgemäß hergestellt werden, sollten Sie alle Aspekte dieser Konnektivität beschreiben, einschließlich; die öffentlichen DNS-Einträge für die Dienste, die diese eingehenden Verbindungen akzeptieren, die in CIDR formatierten IPv4-IP-Adressen, die ISP-Geräte, und wie eingehende NAT-oder Quell-NAT für diese Verbindungen behandelt werden.
  
Eingehende Verbindungen sollten unabhängig davon überprüft werden, ob Sie eine Verbindung über das Internet oder Express Route herstellen, um sicherzustellen, dass kein asymmetrisches Routing eingeführt wurde. In einigen Fällen müssen lokale Endpunkte, für die Office 365-Dienste eingehende Verbindungen initiieren, möglicherweise auch von anderen Microsoft-und nicht-Microsoft-Diensten aufgerufen werden. Es ist von größter Bedeutung, dass das Express Route-Routing zu diesen Diensten für Office 365-Zwecke keine anderen Szenarien unterbricht. In vielen Fällen müssen Kunden möglicherweise bestimmte Änderungen an Ihrem internen Netzwerk implementieren, wie etwa Quell basierte NAT, um sicherzustellen, dass eingehende Datenflüsse von Microsoft symmetrisch bleiben, nachdem Express Route aktiviert wurde.
  
Hier ist ein Beispiel für die erforderliche Detailstufe. In diesem Fall wird die Exchange-Hybrid Verbindung zum lokalen System über Express Route weitergeleitet.

|**Connection-Eigenschaft**|**Wert**|
|:-----|:-----|
|**Richtung des Netzwerkverkehrs** <br/> |Eingehend  <br/> |
|**Dienst** <br/> |Exchange Hybrid  <br/> |
|**Öffentlicher Office 365-Endpunkt (Quelle)** <br/> |Exchange Online (IP-Adressen)  <br/> |
|**Öffentlicher lokale Endpunkt (Ziel)** <br/> |5.5.5.5  <br/> |
|**Öffentlicher (Internet) DNS-Eintrag** <br/> |Autodiscover.contoso.com  <br/> |
|**Wird dieser lokale Endpunkt für andere Microsoft-Dienste (nicht für Office 365) verwendet** <br/> |Nein  <br/> |
|**Wird dieser lokale Endpunkt von Benutzern/Systemen im Internet verwendet** <br/> |Ja  <br/> |
|**Interne Systeme, die über öffentliche Endpunkte veröffentlicht wurden** <br/> |Exchange Server-clientzugriffsrolle (lokal) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**IP-Werbung des öffentlichen Endpunkts** <br/> |**An Internet**: 5.5.0.0/16  <br/> **Bis Express Route**: 5.5.5.0/24  <br/> |
|**Sicherheits-/Umkreis Steuerungen** <br/> |**Internet Pfad**: DeviceID_002  <br/> **Express Route-Pfad**: DeviceID_003  <br/> |
|**Hohe Verfügbarkeit** <br/> |Aktiv/aktiv über 2 Geo-redundant  <br/> Express Route Circuits-Chicago und Dallas  <br/> |
|**Pfad Symmetrie-Steuerelement** <br/> |**Methode**: Quell-NAT  <br/> **Internet Pfad**: Quell-NAT-eingehende Verbindungen zu 192.168.5.5  <br/> |**Express Route-Pfad**: Quell-NAT-Verbindungen mit 192.168.1.0 (Chicago) und 192.168.2.0 (Dallas)  <br/> |

Im folgenden finden Sie ein Beispiel für einen Dienst, der nur ausgehend ist:

|**Connection-Eigenschaft**|**Wert**|
|:-----|:-----|
|**Richtung des Netzwerkverkehrs** <br/> |Ausgehend  <br/> |
|**Dienst** <br/> |SharePoint Online  <br/> |
|**Lokalen Endpunkt (Quelle)** <br/> |Benutzer Arbeitsstation  <br/> |
|**Öffentlicher Office 365-Endpunkt (Ziel)** <br/> |SharePoint Online (IP-Adressen)  <br/> |
|**Öffentlicher (Internet) DNS-Eintrag** <br/> |\*. sharepoint.com (und zusätzliche FQDNs)  <br/> |
|**CDN-Empfehlungen** <br/> |cdn.sharepointonline.com (und zusätzliche FQDNs) – von CDN-Anbietern verwaltete IP-Adressen)  <br/> |
|**IP-Werbung und NAT wird verwendet** <br/> |**Internet Pfad/Quell-NAT**: 1.1.1.0/24  <br/> **Express Route Pfad/Quell-NAT**: 1.1.2.0/24 (Chicago) und 1.1.3.0/24 (Dallas)  <br/> |
|**Connectivity-Methode** <br/> |**Internet**: über Layer 7-Proxy (PAC-Datei)  <br/> **Express Route**: Direktes Routing (kein Proxy)  <br/> |
|**Sicherheits-/Umkreis Steuerungen** <br/> |**Internet Pfad**: DeviceID_002  <br/> **Express Route-Pfad**: DeviceID_003  <br/> |
|**Hohe Verfügbarkeit** <br/> |**Internetpfad**: redundanter Internet Ausstieg  <br/> **Express Route Pfad**: aktiv/aktiv ' Hot Potato ' Routing über 2 Geo-redundante Express Route Circuits-Chicago und Dallas  <br/> |
|**Pfad Symmetrie-Steuerelement** <br/> |**Methode**: Quell-NAT für alle Verbindungen  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Entwurf Ihrer Netzwerktopologie mit regionaler Konnektivität
<a name="topology"> </a>

Nachdem Sie die Dienste und die dazugehörigen Netzwerkdatenverkehr verstanden haben, können Sie ein Netzwerkdiagramm erstellen, das diese neuen Verbindungsanforderungen enthält, und die Änderungen, die Sie für die Verwendung von Express Route für Office 365 vornehmen werden, veranschaulichen. Ihr Diagramm sollte Folgendes aufweisen:
  
1. Alle Benutzer Standorte, von denen aus auf Office 365 und andere Dienste zugegriffen wird.

2. Alle Internet-und Express Route-Ausstiegspunkte.

3. Alle ausgehenden und eingehenden Geräte, die die Konnektivität innerhalb und außerhalb des Netzwerks verwalten, einschließlich Router, Firewalls, Anwendungsproxy Server und Intrusion Detection/Prevention.

4. Interne Ziele für alle eingehenden Datenverkehr, beispielsweise interne ADFS-Server, die Verbindungen von den ADFS-Webanwendungs-Proxyservern akzeptieren.

5. Katalog aller IP-Subnetze, die angekündigt werden

6. Identifizieren Sie jeden Standort, von dem aus auf Office 365 zugegriffen wird, und Listen Sie die Meet-Me-Speicherorte auf, die für Express Route verwendet werden.

7. Standorte und Teile Ihrer internen Netzwerktopologie, in der von Express Route erlernte Microsoft-IP-Präfixe akzeptiert, gefiltert und an Sie weitergegeben werden.

8. Die Netzwerktopologie sollte den geografischen Standort jedes Netzwerksegments und die Verbindung mit dem Microsoft-Netzwerk über Express Route und/oder das Internet veranschaulichen.

Das folgende Diagramm zeigt die einzelnen Standorte, an denen Personen Office 365 von zusammen mit den eingehenden und ausgehenden Routing Ankündigungen an Office 365 verwenden.
  
![Express Route Regional Geographic Meet-Me](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Für ausgehenden Datenverkehr wird auf drei Arten auf Office 365 zugegriffen:
  
1. Durch einen Meet-Me-Standort in Nordamerika für die Personen in Kalifornien.

2. Durch einen Meet-Me-Standort in Hongkong für die Menschen in Hongkong.

3. Über das Internet in Bangladesch, wo weniger Personen und keine Express Route-Schaltungen vorhanden sind.

![Ausgehende Verbindungen für ein regionales Diagramm](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Entsprechend gibt der eingehende Netzwerkdatenverkehr von Office 365 auf drei Arten zurück:
  
1. Durch einen Meet-Me-Standort in Nordamerika für die Personen in Kalifornien.

2. Durch einen Meet-Me-Standort in Hongkong für die Menschen in Hongkong.

3. Über das Internet in Bangladesch, wo weniger Personen und keine Express Route-Schaltungen vorhanden sind.

![Eingehende Verbindungen für regionales Diagramm](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Bestimmen des geeigneten Standorts für "Meet-Me"

Die Auswahl von "Meet-Me"-Standorten, die der physische Standort sind, an dem Ihre Express Route-Schaltung Ihr Netzwerk mit dem Microsoft-Netzwerk verbindet, wird von den Standorten beeinflusst, an denen Benutzer auf Office 365 von zugreifen. Als SaaS-Angebot funktioniert Office 365 nicht auf die gleiche Weise wie Azure unter dem regionalen IaaS-oder PaaS-Modell. Office 365 ist vielmehr eine verteilte Gruppe von Diensten für die Zusammenarbeit, bei der Benutzer möglicherweise eine Verbindung zu Endpunkten über mehrere Rechenzentren und Regionen herstellen müssen, die sich möglicherweise nicht am selben Standort oder in der gleichen Region befinden, in der der Mandant des Benutzers gehostet wird.
  
Dies bedeutet, dass die wichtigsten Überlegungen, die Sie bei der Auswahl von Meet-Me-Standorten für Express Route für Office 365 treffen müssen, in dem die Personen in Ihrer Organisation eine Verbindung herstellen. Die allgemeine Empfehlung für eine optimale Office 365-Konnektivität ist die Implementierung des Routings, sodass Benutzeranfragen an Office 365-Dienste über den kürzesten Netzwerkpfad in das Microsoft-Netzwerk übertragen werden, dies wird häufig auch als "Hot Potato"-Routing bezeichnet. Wenn sich beispielsweise die meisten Office 365-Benutzer an einem oder an zwei Standorten befinden, wird der optimale Entwurf erstellt, wenn Sie sich in der Nähe des Standorts dieser Benutzer befinden. Wenn Ihr Unternehmen große Benutzer Populationen in vielen verschiedenen Regionen hat, können Sie erwägen, mehrere Express Route-Schaltungen und Meet-Me-Standorte zu verwenden. Für einige Ihrer Benutzer Standorte kann der kürzeste/optimale Pfad zu Microsoft Network und Office 365 nicht über Ihre internen WAN-und Express Route-Meet-Me-Punkte erfolgen, sondern über das Internet.
  
Oftmals gibt es mehrere Meet-Me-Speicherorte, die in einer Region mit relativer Nähe zu Ihren Benutzern ausgewählt werden können. Füllen Sie die folgende Tabelle aus, um Ihre Entscheidungen zu treffen.

|**Geplante Express Route Meet-Me-Standorte in Kalifornien und New York**||
|:-----|:-----|
|Ort  <br/> |Anzahl der Personen  <br/> |Erwartete Latenz des Microsoft-Netzwerks über Internet-Ausstieg  <br/> |Erwartete Latenz beim Microsoft-Netzwerk über Express Route  <br/> |
|München  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10ms (via Silicon Valley)  <br/> |
|Washington DC  <br/> |15,000  <br/> |~ 20 ms  <br/> |~ 10ms (über New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms (über New York)  <br/> |

Sobald die globale Netzwerkarchitektur mit der Office 365-Region, dem Express Route-Netzwerkdienst Anbieter und der Anzahl der Personen nach Standort entwickelt wurde, kann Sie verwendet werden, um zu ermitteln, ob Optimierungen vorgenommen werden können. Möglicherweise werden auch globale Haarnadel-Netzwerkverbindungen angezeigt, bei denen der Datenverkehr zu einem entfernten Standort geleitet wird, um den Standort "Meet-Me" zu erhalten. Wenn eine Haarnadel im globalen Netzwerk erkannt wird, sollte Sie vor dem Fortfahren korrigiert werden. Suchen Sie sich einen anderen Standort in Meet-Me aus, oder verwenden Sie selektive Internet Breakout-Ausstiegspunkte, um die Haarnadel zu vermeiden.
  
Das erste Diagramm zeigt ein Beispiel für einen Kunden mit zwei physikalischen Standorten in Nordamerika. Sie können die Informationen zu Office-Standorten, Office 365-Mandanten Standorten und verschiedene Auswahlmöglichkeiten für Express Route Meet-Me-Standorte anzeigen. In diesem Beispiel hat der Kunde den Standort "Meet-Me" basierend auf zwei Prinzipien in der folgenden Reihenfolge ausgewählt:
  
1. Nähe zu den Personen in Ihrer Organisation.

2. Am nächsten in der Nähe eines Microsoft-Datencenters, in dem Office 365 gehostet wird.

![Express Route US Geographic Meet-Me](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Das zweite Diagramm zeigt ein Beispiel für Multi-nationale Kunden mit ähnlichen Informationen und Entscheidungsfindung. Dieser Kunde verfügt über ein kleines Büro in Bangladesch mit nur einem kleinen Team von zehn Personen, das sich auf die wachsende Präsenz in der Region konzentriert. Es gibt einen Meet-Me-Standort in Chennai und ein Microsoft-Datencenter mit Office 365, die in Chennai gehostet werden, sodass ein Meet-Me-Standort sinnvoll wäre; für zehn Personen sind die Kosten der zusätzlichen Schaltung jedoch aufwändig. Wenn Sie sich Ihr Netzwerk ansehen, müssen Sie ermitteln, ob die Wartezeit beim Senden des Netzwerkdatenverkehrs in Ihrem Netzwerk effektiver ist, als die Anschaffung eines anderen Express Route-Circuits durch das Kapital zu verbringen.
  
Alternativ können die zehn Personen in Bangladesch mit dem Netzwerkdatenverkehr, der über das Internet an das Microsoft-Netzwerk gesendet wird, eine bessere Leistung erzielen, als Sie in Ihrem internen Netzwerk weiterleiten würden, wie in den einführenden Diagrammen gezeigt und reproduziert unten.
  
![Ausgehende Verbindungen für ein regionales Diagramm](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Erstellen des Express Route für Office 365-Implementierungsplans
<a name="implementation"> </a>

Ihr Implementierungsplan sollte sowohl die technischen Details der Konfiguration von Express Route als auch die Details der Konfiguration aller anderen Infrastruktur in Ihrem Netzwerk umfassen, wie beispielsweise die folgenden.
  
- Planen Sie, welche Dienste zwischen Express Route und Internet aufgeteilt werden.

- Planen der Bandbreite, der Sicherheit, der hohen Verfügbarkeit und des Failovers.

- Entwurf für ein-und ausgehendes Routing, einschließlich ordnungsgemäßer Routingpfad Optimierungen für verschiedene Standorte

- Entscheiden Sie, wie weit Express Route-Routen in Ihrem Netzwerk angekündigt werden sollen und was der Mechanismus für Clients zum Auswählen des Internet-oder Express Route-Pfads ist. beispielsweise Direktes Routing oder Anwendungsproxy.

- Planen von DNS-Eintrags Änderungen, einschließlich [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) -Einträgen.

- Planen der NAT-Strategie einschließlich ausgehender und eingehender Quell-NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planen des Routings mit Internet-und Express Route-Netzwerkpfaden
<a name="paths"> </a>

- Für die anfängliche Bereitstellung werden alle eingehenden Dienste wie eingehende e-Mail oder Hybrid Konnektivität empfohlen, um das Internet zu verwenden.

- Planen des Endbenutzer-LAN-Routings, beispielsweise [Konfigurieren einer PAC/WPAD-Datei](https://aka.ms/manageo365endpoints), Standardroute, Proxy Server und BGP-Routenankündigungen.

- Planen des Umkreis Routings, einschließlich Proxyservern, Firewalls und Cloud-Proxies.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planen der Bandbreite, der Sicherheit, der hohen Verfügbarkeit und des Failovers
<a name="availability"> </a>

Erstellen Sie einen Plan für die erforderliche Bandbreite für jede größere Office 365-Arbeitsauslastung. Abschätzen der Bandbreitenanforderungen von Exchange Online, SharePoint Online und Skype for Business Online. Sie können die schätzungs Rechner verwenden, die wir für Exchange Online und Skype for Business als Ausgangspunkt bereitgestellt haben. Es ist jedoch ein Pilot Test mit einem repräsentativen Beispiel der Benutzerprofile und Speicherorte erforderlich, um die Bandbreitenanforderungen Ihrer Organisation vollständig zu verstehen.
  
Fügen Sie hinzu, wie die Sicherheit an den einzelnen Internet-und Express Route-Ausstiegs Orten in Ihrem Plan behandelt wird, denken Sie daran, dass alle Express Route-Verbindungen mit Office 365 öffentliche Peering verwenden und weiterhin in Übereinstimmung mit den Sicherheitsrichtlinien des Unternehmens zur Verbindung mit externen Netzwerke.
  
Fügen Sie Details zu Ihrem Plan hinzu, welche Personen von welcher Art von Ausfall betroffen sind und wie diese Personen auf einfachste Weise ihre Arbeit mit voller Kapazität ausführen können.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planen der Bandbreitenanforderungen einschließlich Skype for Business-Anforderungen für Jitter, Latenz, Überlastung und kopfFreiheit
  
Skype for Business Online verfügt außerdem über spezifische zusätzliche Netzwerkanforderungen, die im Artikel [Medienqualität und Leistung der Netzwerkkonnektivität in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)erläutert werden.
  
Lesen Sie den Abschnitt **Bandbreitenplanung für Azure Express Route** in der [Netzwerkplanung mit express route für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Wenn Sie eine Bandbreiten Bewertung mit ihren Pilotbenutzern durchführen, können Sie unseren Leitfaden verwenden; [Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planen der Anforderungen an hohe Verfügbarkeit
  
Erstellen Sie einen Plan für hohe Verfügbarkeit, um Ihre Anforderungen zu erfüllen, und integrieren Sie diesen in Ihr aktualisiertes Netzwerktopologie-Diagramm. Lesen Sie den Abschnitt **Hochverfügbarkeit und Failover mit Azure Express Route** in der [Netzwerkplanung mit express route für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planen der Anforderungen an die Netzwerksicherheit
  
Erstellen Sie einen Plan zur Erfüllung ihrer Anforderungen an die Netzwerksicherheit, und integrieren Sie diesen in Ihr aktualisiertes Netzwerktopologie-Diagramm. Lesen Sie den Abschnitt **Anwenden von Sicherheitskontrollen auf Azure Express Route für office 365-Szenarien** in der [Netzwerkplanung mit express route für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Entwerfen der Verbindung mit ausgehenden Diensten
<a name="outbound"> </a>

Express Route für Office 365 verfügt über *ausgehende* Netzwerkanforderungen, die möglicherweise nicht bekannt sind. Insbesondere müssen die IP-Adressen, die Ihre Benutzer und Netzwerke zu Office 365 darstellen und als Quell Endpunkte für ausgehende Netzwerkverbindungen mit Microsoft fungieren, die folgenden spezifischen Anforderungen erfüllen.
  
1. Die Endpunkte müssen öffentliche IP-Adressen sein, die für Ihr Unternehmen oder für den Netzbetreiber registriert sind, der Ihnen Express Route-Konnektivität bereitstellt.

2. Die Endpunkte müssen für Microsoft angekündigt und von Express Route validiert/akzeptiert werden.

3. Die Endpunkte dürfen nicht mit der gleichen oder bevorzugten Routingmetrik für das Internet angekündigt werden.

4. Die Endpunkte dürfen nicht für Verbindungen mit Microsoft-Diensten verwendet werden, die nicht über Express Route konfiguriert sind.

Wenn Ihr Netzwerk Design diese Anforderungen nicht erfüllt, besteht ein hohes Risiko, dass die Benutzer Verbindungsfehler mit Office 365 und anderen Microsoft-Diensten aufgrund von schwarzer holing oder asymmetrischem Routing erfahren. Dies tritt auf, wenn Anforderungen an Microsoft-Dienste über Express Route weitergeleitet werden, aber Antworten über das Internet weitergeleitet werden, oder umgekehrt, und die Antworten werden von Stateful-Netzwerkgeräten wie Firewalls gelöscht.
  
Die häufigste Methode, die Sie verwenden können, um die obigen Anforderungen zu erfüllen, ist die Verwendung der Quell-NAT, die entweder als Teil Ihres Netzwerks implementiert oder von Ihrem Express Route-Carrier bereitgestellt wird. Mit der Quell-NAT können Sie die Details und die private IP-Adressierung Ihres Internetnetzwerks von Express Route aus abstrahieren. gekoppelt mit richtigen IP-Routenankündigungen bieten Sie einen einfachen Mechanismus zur Sicherstellung der Pfad Symmetrie. Wenn Sie Stateful-Netzwerkgeräte verwenden, die spezifisch für Express Route-Peering-Standorte sind, müssen Sie für jedes Express Route-Peering separate NAT-Pools implementieren, um die Pfad Symmetrie sicherzustellen.
  
Lesen Sie mehr über die [Express Route-NAT-Anforderungen](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Fügen Sie die Änderungen für die ausgehende Konnektivität zum Netzwerktopologie-Diagramm hinzu.
  
### <a name="design-inbound-service-connectivity"></a>Entwerfen der Konnektivität für eingehende Dienste
<a name="inbound"> </a>

Die Mehrzahl der Enterprise Office 365-Bereitstellungen übernehmen eine Art von eingehender Konnektivität von Office 365 zu lokalen Diensten, beispielsweise für Exchange-, SharePoint-und Skype for Business-Hybrid Szenarien, Postfachmigrationen und Authentifizierung mithilfe von ADFS. Infrastruktur. Wenn Sie einen zusätzlichen Routingpfad zwischen Ihrem lokalen Netzwerk und Microsoft für ausgehende Verbindungen aktivieren, können diese eingehenden Verbindungen versehentlich durch asymmetrisches Routing beeinträchtigt werden, selbst wenn Sie beabsichtigen, diese Express Route Verwenden Sie das Internet. Es werden einige Vorsichtsmaßnahmen empfohlen, um sicherzustellen, dass der Internet basierte eingehende Fluss von Office 365 zu lokalen Systemen nicht beeinträchtigt wird.
  
Um die Risiken eines asymmetrischen Routings für eingehende Netzwerkdatenverkehr zu minimieren, sollten alle eingehenden Verbindungen die Quell-NAT verwenden, bevor Sie in Segmente Ihres Netzwerks weitergeleitet werden, die über Routing Sichtbarkeit in Express Route verfügen. Wenn die eingehenden Verbindungen in einem Netzwerksegment mit Routing Sichtbarkeit in Express Route ohne Quell-NAT zulässig sind, werden Anforderungen von Office 365 aus dem Internet eingehen, aber die Antwort, die auf Office 365 zurückgeht, bevorzugt die Express Route Netzwerkpfad zurück zum Microsoft-Netzwerk, wodurch asymmetrisches Routing verursacht wird.
  
Sie können eine der folgenden Implementierungsmuster berücksichtigen, um diese Anforderung zu erfüllen:
  
1. Führen Sie die Quell-NAT aus, bevor Anforderungen an Ihr internes Netzwerk über Netzwerkgeräte wie Firewalls oder Lastenausgleichsmodule auf dem Pfad vom Internet zu Ihren lokalen Systemen weitergeleitet werden.

2. Stellen Sie sicher, dass Express Route-Routen nicht an die Netzwerksegmente weitergegeben werden, in denen eingehende Dienste wie Front-End-Server oder Reverseproxy-Systeme, die Internet Verbindungen behandeln, gespeichert werden.

Die explizite Bilanzierung dieser Szenarien in Ihrem Netzwerk und das aufrecht erhalten des eingehenden Netzwerkverkehrs über das Internet helfen bei der Minimierung der Bereitstellung und des operationellen Risikos des asymmetrischen Routings.
  
Es kann vorkommen, dass Sie einige eingehende Flüsse über Express Route-Verbindungen leiten können. Berücksichtigen Sie für diese Szenarien die folgenden zusätzlichen Aspekte.
  
1. Office 365 kann nur auf lokale Endpunkte ausgerichtet werden, die öffentliche IPs verwenden. Dies bedeutet, dass auch dann, wenn der lokale eingehende Endpunkt nur für Office 365 über Express Route verfügbar gemacht wird, ihm dennoch öffentliche IP-Adressen zugeordnet werden müssen.

2. Die gesamte DNS-Namensauflösung, die von Office 365-Diensten zur Behebung von lokalen Endpunkten ausgeführt wird, erfolgt mithilfe öffentlicher DNS. Dies führt dazu, dass Sie den FQDN des eingehenden Diensts für IP-Zuordnungen im Internet registrieren müssen.

3. Um eingehende Netzwerkverbindungen über Express Route zu erhalten, müssen die öffentlichen IP-Subnetze für diese Endpunkte an Microsoft über Express Route angekündigt werden.

4. Bewerten Sie diese eingehenden Netzwerkdatenverkehr sorgfältig, um sicherzustellen, dass in Übereinstimmung mit ihren Unternehmens Sicherheits-und Netzwerkrichtlinien entsprechende Sicherheits-und Netzwerk Steuerungen darauf angewendet werden.

5. Sobald Ihre lokalen eingehenden Endpunkte Microsoft über Express Route angekündigt wurden, wird Express Route effektiv der bevorzugte Routingpfad zu diesen Endpunkten für alle Microsoft-Dienste, einschließlich Office 365. Dies heißt, dass diese Endpunkt Subnetze nur für die Kommunikation mit Office 365-Diensten und keine anderen Dienste im Microsoft-Netzwerk verwendet werden dürfen. Andernfalls verursacht Ihr Entwurf ein asymmetrisches Routing, bei dem eingehende Verbindungen von anderen Microsoft-Diensten die Weiterleitung von eingehenden über Express Route bevorzugen, während der Rückgabepfad das Internet verwendet.

6. Wenn ein Express Route-oder Meet-Me-Standort ausgefallen ist, müssen Sie sicherstellen, dass die lokalen eingehenden Endpunkte weiterhin verfügbar sind, um Anforderungen über einen separaten Netzwerkpfad zu akzeptieren. Dies kann Werbe Subnetze für diese Endpunkte über mehrere Express Route-Schaltungen bedeuten.

7. Es wird empfohlen, Quell-NAT für alle eingehenden Netzwerkdatenverkehr einzusetzen, die über Express Route in Ihr Netzwerk eindringen, insbesondere dann, wenn diese über Stateful-Netzwerkgeräte wie Firewalls übertragen werden.

8. Einige lokale Dienste wie ADFS-Proxy oder Exchange-AutoErmittlung erhalten möglicherweise eingehende Anfragen sowohl von Office 365-Diensten als auch von Benutzern aus dem Internet. Für diese Anforderungen wird Office 365 auf denselben FQDN wie Benutzeranforderungen über das Internet ausgerichtet. Das Zulassen eingehender Benutzer Verbindungen aus dem Internet zu den lokalen Endpunkten, während Office 365-Verbindungen für die Verwendung von Express Route erzwungen werden, stellt eine erhebliche Routing Komplexität dar. Für die große Mehrheit der Kunden, die solche komplexen Szenarien über Express Route implementieren, wird aufgrund betrieblicher Überlegungen nicht empfohlen. Dieser zusätzliche Aufwand umfasst das Verwalten von Risiken des asymmetrischen Routings und erfordert die sorgfältige Verwaltung von Routing Ankündigungen und-Richtlinien über mehrere Dimensionen hinweg.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Aktualisieren des Plans für die Netzwerktopologie, um zu zeigen, wie asymmetrische Routen vermieden werden
<a name="asymmetric"> </a>

Sie möchten ein asymmetrisches Routing vermeiden, um sicherzustellen, dass Personen in Ihrer Organisation Office 365 und andere wichtige Dienste im Internet nahtlos nutzen können. Es gibt zwei allgemeine Konfigurationen, die Kunden haben, die ein asymmetrisches Routing verursachen. Sehen Sie sich jetzt die Netzwerkkonfiguration an, die Sie verwenden möchten, und prüfen Sie, ob eines dieser asymmetrischen Routingszenarien vorhanden sein könnte.
  
Zunächst werden einige verschiedene Situationen im Zusammenhang mit dem folgenden Netzwerkdiagramm untersucht. In diesem Diagramm befinden sich alle Server, die eingehende Anforderungen wie ADFS oder lokale hybridserver empfangen, im New Jersey-Datencenter und werden dem Internet angekündigt.
  
1. Während das Umkreisnetzwerk sicher ist, ist für eingehende Anforderungen keine Quell-NAT verfügbar.

2. Die Server im New Jersey-Rechenzentrum können sowohl Internet-als auch Express Route-Routen anzeigen.

![Übersicht über die Express Route-Konnektivität](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Wir haben auch Vorschläge, wie Sie behoben werden können.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1: Cloud-zu-lokal-Verbindung über das Internet
  
Das folgende Diagramm veranschaulicht den asymmetrischen Netzwerkpfad, der verwendet wird, wenn Ihre Netzwerkkonfiguration keine NAT für eingehende Anfragen aus der Microsoft-Cloud über das Internet bereitstellt.
  
1. Die eingehende Anforderung von Office 365 Ruft die IP-Adresse des lokalen Endpunkts aus dem öffentlichen DNS ab und sendet die Anforderung an das Umkreisnetzwerk.

2. In dieser fehlerhaften Konfiguration ist kein Quell-NAT konfiguriert oder ist im Umkreisnetzwerk verfügbar, in dem der Datenverkehr gesendet wird, wodurch die tatsächliche Quell-IP-Adresse als Rückgabe Ziel verwendet wird.

  - Der Server in Ihrem Netzwerk leitet den Rückgabe Datenverkehr über eine beliebige verfügbare Express Route-Netzwerkverbindung an Office 365 weiter.

  - Das Ergebnis ist ein asymmetrischer Pfad für diesen Fluss zu Office 365, was zu einer fehlerhaften Verbindung führt.

![Express Route ASYMETRIC-Routing Problem 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Lösung 1a: Quell-NAT
  
Durch das Hinzufügen einer Quell-NAT zur eingehenden Anforderung wird dieses falsch konfigurierte Netzwerk gelöst. Inhalt dieses Diagramms:
  
1. Die eingehende Anforderung wird weiterhin über das Umkreisnetzwerk des New Jersey-Rechenzentrums eingehen. Dieses Mal ist die Quell-NAT verfügbar.

2. Die Antwort vom Server geht zurück in Richtung der IP-Adresse, die der Quell-NAT zugeordnet ist, anstelle der ursprünglichen IP-Adressen, was dazu führt, dass die Antwort über denselben Netzwerkpfad zurückgegeben wird.

![Express Route ASYMETRIC-Routinglösung 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Lösung 1B: Routendefinition
  
Alternativ können Sie nicht zulassen, dass die Express Route-BGP-Präfixe angekündigt werden, sondern den alternativen Netzwerkpfad für diese Computer entfernen. Inhalt dieses Diagramms:
  
1. Die eingehende Anforderung wird weiterhin über das Umkreisnetzwerk des New Jersey-Rechenzentrums eingehen. Dieses Mal sind die von Microsoft über die Express Route-Schaltung angekündigten Präfixe für das New Jersey-Datencenter nicht verfügbar.

2. Die Antwort des Servers führt zurück zur IP-Adresse, die der ursprünglichen IP-Adressen zugeordnet ist, über die einzige verfügbare Route, wodurch die Antwort über denselben Netzwerkpfad zurückgegeben wird.

![Express Route ASYMETRIC-Routinglösung 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2: Cloud to on-premises Connection over Express Route
  
Das folgende Diagramm veranschaulicht den asymmetrischen Netzwerkpfad, der verwendet wird, wenn Ihre Netzwerkkonfiguration keine NAT für eingehende Anfragen aus der Microsoft-Cloud über Express Route bereitstellt.
  
1. Die eingehende Anforderung von Office 365 Ruft die IP-Adresse aus dem DNS ab und sendet die Anforderung an Ihr Umkreisnetzwerk.

2. In dieser fehlerhaften Konfiguration ist kein Quell-NAT konfiguriert oder ist im Umkreisnetzwerk verfügbar, in dem der Datenverkehr gesendet wird, wodurch die tatsächliche Quell-IP-Adresse als Rückgabe Ziel verwendet wird.

  - Der Computer in Ihrem Netzwerk leitet den Rückgabe Datenverkehr über eine beliebige verfügbare Express Route-Netzwerkverbindung an Office 365 weiter.

  - Das Ergebnis ist eine asymmetrische Verbindung zu Office 365.

![Express Route ASYMETRIC Routing Problem 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Lösung 2: Quell-NAT
  
Durch das Hinzufügen einer Quell-NAT zur eingehenden Anforderung wird dieses falsch konfigurierte Netzwerk gelöst. Inhalt dieses Diagramms:
  
1. Die eingehende Anforderung wird weiterhin über das Umkreisnetzwerk des New Yorker Rechenzentrums eingehen. Dieses Mal ist die Quell-NAT verfügbar.

2. Die Antwort vom Server geht zurück in Richtung der IP-Adresse, die der Quell-NAT zugeordnet ist, anstelle der ursprünglichen IP-Adressen, was dazu führt, dass die Antwort über denselben Netzwerkpfad zurückgegeben wird.

![Express Route-ASYMETRIC-Routinglösung 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papier stellen Sie sicher, dass das Netzwerk Design Pfad Symmetrie aufweist

Zu diesem Zeitpunkt müssen Sie auf Papier überprüfen, ob Ihr Implementierungsplan eine Routen Symmetrie für die verschiedenen Szenarien bietet, in denen Sie Office 365 verwenden werden. Sie identifizieren die spezifische Netzwerkroute, die angenommen wird, wenn eine Person unterschiedliche Features des Diensts verwendet. Vom lokalen Netzwerk und WAN-Routing zu den Umkreis Geräten, zum Verbindungspfad; Express Route oder das Internet und die Verbindung mit dem Online-Endpunkt.
  
Sie müssen dies für alle Office 365-Netzwerkdienste tun, die zuvor als Dienste identifiziert wurden, die von Ihrer Organisation übernommen werden.
  
Es hilft bei dieser Papier Wanderung von Routen mit einer zweiten Person. Erläutern Sie, wo für jeden Netzwerk Hop erwartet wird, dass er seine nächste Route erhält, und stellen Sie sicher, dass Sie mit den Routingpfaden vertraut sind. Denken Sie daran, dass Express Route immer eine weiter reichende Route zu Microsoft-Server-IP-Adressen bereitstellt, die eine geringere Route kostet als eine Internet Standardroute.
  
### <a name="design-client-connectivity-configuration"></a>Entwerfen der Client Verbindungskonfiguration
<a name="asymmetric"> </a>

![Verwenden von PAC-Dateien mit Express Route](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Wenn Sie einen Proxy Server für den internetgebundenen Datenverkehr verwenden, müssen Sie alle PAC-oder Clientkonfigurationsdateien anpassen, um sicherzustellen, dass die Clientcomputer in Ihrem Netzwerk ordnungsgemäß konfiguriert sind, um den gewünschten Express Route-Datenverkehr an Office 365 ohne Transit zu senden. Ihr Proxy Server und der verbleibende Datenverkehr, einschließlich einiger Office 365-Datenverkehr, werden an den entsprechenden Proxy gesendet. Lesen Sie unseren Leitfaden zum [Verwalten von Office 365](https://aka.ms/manageo365endpoints) -Endpunkten zum Beispiel PAC-Dateien.
  
> [!NOTE]
> Die Endpunkte ändern sich häufig, so oft wie wöchentlich. Sie sollten nur Änderungen basierend auf den Diensten und Features vornehmen, die Ihre Organisation übernommen hat, um die Anzahl der Änderungen zu reduzieren, die Sie vornehmen müssen, um den aktuellen Stand zu halten. Achten Sie genau auf das **Datum** des Inkrafttretens im RSS-Feed, in dem die Änderungen angekündigt werden, und ein Datensatz aller Änderungen, die angekündigten IP-Adressen, möglicherweise erst dann angekündigt oder aus der Werbung entfernt werden, wenn das Gültigkeitsdatum erreicht ist.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Erstellen Ihrer Bereitstellungs-und Testverfahren
<a name="testing"> </a>

Der Implementierungsplan sollte sowohl Test-als auch Roll Back Planung einschließen. Wenn Ihre Implementierung nicht wie erwartet funktioniert, sollte der Plan so konzipiert werden, dass er sich auf die geringste Anzahl von Personen auswirkt, bevor Probleme erkannt werden. Im folgenden finden Sie einige allgemeine Grundsätze, die Ihr Plan berücksichtigen sollte.
  
1. Stufen Sie das Netzwerksegment und den Benutzer Dienst Onboarding ein, um die Unterbrechung zu minimieren.

2. Planen Sie das Testen von Routen mit traceroute und TCP-Verbindung von einem separaten mit dem Internet verbundenen Host.

3. VorZugsweise sollten Tests für eingehende und ausgehende Dienste in einem isolierten Testnetzwerk mit einem Test Office 365-Mandanten durchgeführt werden.

      - Alternativ können Tests in einem Produktionsnetzwerk durchgeführt werden, wenn der Kunde noch nicht Office 365 verwendet oder sich im Pilotprojekt befindet.

      - Alternativ können Tests während eines Produktionsausfalls ausgeführt werden, der nur für Test und Überwachung reserviert ist.

      - Alternativ können Tests durchgeführt werden, indem Sie die Routen für jeden Dienst auf jedem Layer 3-Router-Knoten überprüfen. Dieser Rückgang sollte nur dann verwendet werden, wenn keine anderen Tests möglich sind, da bei mangelnder physischer Tests Risiken auftreten.

### <a name="build-your-deployment-procedures"></a>Erstellen der Bereitstellungsverfahren

Die Bereitstellungsverfahren sollten in kleinen Gruppen von Personen stufenweise ausgeführt werden, um Tests vor der Bereitstellung in größeren Gruppen von Personen zu ermöglichen. Es folgen mehrere Möglichkeiten, die Bereitstellung von Express Route zu inszenieren.
  
1. Richten Sie Express Route mit Microsoft Peering ein, und lassen Sie die Routen Werbung nur zu Testzwecken an einen einzelnen Host weitergeleitet werden.

2. Werben Sie die Routen zum Express Route-Netzwerk zunächst an ein einzelnes Netzwerksegment, und erweitern Sie dann "Routenankündigungen nach Netzwerksegment oder Region".

3. Wenn Sie Office 365 zum ersten Mal bereitstellen, verwenden Sie die Express Route-Netzwerkbereitstellung als Pilotprojekt für eine kleine Anzahl von Personen.

4. Bei Verwendung von Proxyservern können Sie alternativ eine Test-PAC-Datei so konfigurieren, dass eine kleine Anzahl von Personen vor dem Hinzufügen von Express Route mit Tests und Feedback umgeleitet wird.

Der Implementierungsplan sollte alle Bereitstellungsverfahren auflisten, die ausgeführt werden müssen, oder Befehle, die zum Bereitstellen der Netzwerkkonfiguration verwendet werden müssen. Wenn die Netzwerkausfall Zeit ankommt, sollten alle vorgenommenen Änderungen aus dem schriftlichen Bereitstellungsplan, der im Voraus geschrieben wurde, und Peer-Review erfolgen. Lesen Sie unsere Anweisungen zur technischen Konfiguration von Express Route.
  
- Aktualisieren von SPF TXT-Einträgen, wenn Sie die IP-Adressen für lokale Server geändert haben, die weiterhin e-Mails senden.

- Aktualisieren von DNS-Einträgen für lokale Server, wenn Sie die IP-Adressen für eine neue NAT-Konfiguration geändert haben.

- Stellen Sie sicher, dass Sie den RSS-Feed für Office 365-Endpunkt Benachrichtigungen abonniert haben, um Routing-oder Proxy Konfigurationen zu verwalten.

Nachdem die Express Route-Bereitstellung abgeschlossen ist, sollten die Verfahren im Testplan ausgeführt werden. Die Ergebnisse für jede Prozedur sollten protokolliert werden. Für den Fall, dass die Implementierung nicht erfolgreich war, müssen Sie Verfahren zum Zurücksetzen auf die ursprüngliche Produktionsumgebung einbeziehen.
  
### <a name="build-your-test-procedures"></a>Erstellen der Testprozeduren

Ihre Testverfahren sollten Tests für jeden ausgehenden und eingehenden Netzwerkdienst für Office 365 sowohl verwenden, die Express Route verwendet werden, als auch diejenigen, die dies nicht tun. Die Verfahren sollten Tests von jedem eindeutigen Netzwerkstandort umfassen, einschließlich der Benutzer, die nicht lokal im LAN des Unternehmens vorhanden sind.
  
Beispiele für Testaktivitäten sind folgende:
  
1. Pingen Sie vom lokalen Router an den Router Ihres Netzbetreibers.

2. Überprüfen Sie, ob die 500 + Office 365-und CRM Online-IP-Adress Ankündigungen vom lokalen Router empfangen werden.

3. ÜberPrüfen Sie, ob ein-und ausgehendes NAT zwischen Express Route und dem internen Netzwerk funktioniert.

4. Überprüfen Sie, ob von Ihrem Router aus Routen zu ihrer NAT angekündigt werden.

5. Überprüfen Sie, ob Express Route ihre angekündigten Präfixe akzeptiert hat.

      - Verwenden Sie das folgende Cmdlet, um Peering Advertisements zu überprüfen:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Überprüfen Sie, ob Ihr öffentlicher NAT-IP-Bereich nicht über andere Express Route-oder öffentliche Internet-Netzwerk Schaltkreise für Microsoft angekündigt wird, es sei denn, es handelt sich um eine bestimmte Teilmenge eines größeren Bereiches wie im vorherigen Beispiel.

7. Express Route-Schaltungen werden gepaart, überprüfen Sie, ob beide BGP-Sitzungen laufen.

8. Richten Sie einen einzelnen Host im Inneren ihrer NAT ein, und verwenden Sie Ping, tracert und tcpping, um die Konnektivität zwischen dem neuen Stromkreis und dem Host outlook.office365.com zu testen. Alternativ können Sie ein Tool wie Wireshark oder Microsoft Network Monitor 3,4 auf einem gespiegelten Port zum MSEE verwenden, um zu überprüfen, ob Sie eine Verbindung mit der IP-Adresse herstellen können, die outlook.office365.com zugeordnet ist.

9. Testen Sie die Funktionalität der Anwendungsebene für Exchange Online.

  - Test Outlook kann eine Verbindung mit Exchange Online herstellen und e-Mails senden/empfangen.

  - Test Outlook kann den Onlinemodus verwenden.

  - Testen Sie die Smartphone-Konnektivität und senden/empfangen-Funktion.

10. Testen der Funktionalität der Anwendungsebene für SharePoint Online

  - Testen Sie den OneDrive for Business-synchronisierungsclient.

  - Testen Sie SharePoint Online Web Access.

11. Testen der Funktionalität der Anwendungsebene für Skype für Business-Anrufszenarien:

  - Join to Conference Call as Authenticated User [invite initiiert von Endbenutzer].

  - Benutzer zu Telefonkonferenzen einladen [invite sent from MCU].

  - Beitreten der Konferenz als anonymer Benutzer mithilfe der Skype for Business-Webanwendung.

  - Join-Anruf über Ihre kabelgebundene PC-Verbindung, ein IP-Telefon und ein mobiles Gerät.

  - Anruf bei Verbundbenutzer o Anruf bei PSTN-Validierung: Anruf ist abgeschlossen, Anrufqualität akzeptabel, Verbindungszeit ist akzeptabel.

  - Überprüfen des Anwesenheitsstatus für Kontakte wird für die Mitglieder des Mandanten und der Verbundbenutzer aktualisiert.

### <a name="common-problems"></a>Häufige Probleme

Das asymmetrische Routing ist das häufigste Problem bei der Implementierung. Nachfolgend finden Sie einige häufige Quellen, nach denen gesucht werden muss:
  
- Verwenden einer offenen oder flachen Netzwerkrouting Topologie ohne Quell-NAT.

- Verwenden von SNAT nicht zum Weiterleiten an eingehende Dienste über die Internet-und Express Route-Verbindungen.

- Testen Sie keine eingehenden Dienste auf Express Route in einem Testnetzwerk vor der Bereitstellung allgemein.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Bereitstellen der Express Route-Konnektivität über Ihr Netzwerk
<a name="testing"> </a>

Stufen Sie die Bereitstellung gleichzeitig in einem Segment des Netzwerks ein, und führen Sie die Konnektivität mit einem Plan für jedes neue Netzwerksegment schrittweise aus. Wenn Ihre Bereitstellung an einer Office 365-Bereitstellung ausgerichtet ist, stellen Sie zuerst Ihre Office 365-Pilotbenutzer bereit, und erweitern Sie von dort.
  
Zuerst für den Test und dann für die Produktion:
  
- Führen Sie die Bereitstellungsschritte aus, um Express Route zu aktivieren.

- Testen Sie die Netzwerkrouten wie erwartet.

- Führen Sie Tests für jeden eingehenden und ausgehenden Dienst aus.

- Rollback, wenn Probleme auftreten.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Einrichten einer Testverbindung mit Express Route mit einem Testnetzwerk Segment

Nun, da Sie den abgeschlossenen Plan auf dem Papier haben, ist es Zeit, im kleinen Maßstab zu testen. In diesem Test richten Sie eine einzelne Express Route-Verbindung mit Microsoft-Peering zu einem Test Subnetz in Ihrem lokalen Netzwerk ein. Sie können einen [Test Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) -Mandanten mit Konnektivität zum und vom Test-Subnetz konfigurieren und alle ausgehenden und eingehenden Dienste einbeziehen, die Sie in der Produktion im Test-Subnetz verwenden werden. Richten Sie DNS für das Testnetzwerk Segment ein, und richten Sie alle eingehenden und ausgehenden Dienste ein. Führen Sie den Testplan aus, und stellen Sie sicher, dass Sie mit dem Routing für jeden Dienst und der Routen Verteilung vertraut sind.
  
### <a name="execute-the-deployment-and-test-plans"></a>Ausführen der Bereitstellungs-und Testpläne

Wenn Sie die oben beschriebenen Elemente abgeschlossen haben, überprüfen Sie die Bereiche, die Sie abgeschlossen haben, und stellen Sie sicher, dass Sie und Ihr Team diese überprüft haben, bevor Sie Ihre Bereitstellungs-und Testpläne ausführen.
  
- Liste der ausgehenden und eingehenden Dienste, die an der Netzwerkänderung beteiligt sind.

- Diagramm für eine globale Netzwerkarchitektur, das sowohl Internet Ausgänge als auch Express Route Meet-Me zeigt.

- Netzwerkrouting Diagramm, in dem die verschiedenen Netzwerkpfade veranschaulicht werden, die für jeden bereitgestellten Dienst verwendet werden.

- Ein Bereitstellungsplan mit Schritten zum Implementieren der Änderungen und des Rollbacks, falls erforderlich.

- Ein Testplan zum Testen der einzelnen Office 365-und Netzwerkdienste.

- Vollständige Papier Validierung von Produktions Routen für eingehende und ausgehende Dienste.

- Ein abgeschlossener Test in einem Testnetzwerk Segment einschließlich Verfügbarkeitstests.

Wählen Sie ein Ausfallfenster aus, das lang genug ist, um den gesamten Bereitstellungsplan und den Testplan auszuführen, verfügt über einige Zeit für die Problembehandlung und Zeit für ein Rollback, falls erforderlich.
  
> [!CAUTION]
> Aufgrund der komplexen Art des Routings sowohl über das Internet als auch über das Express Route wird empfohlen, diesem Fenster zusätzliche Pufferzeit hinzuzufügen, um die Problembehandlung für komplexes Routing zu bewältigen.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurieren von QoS für Skype for Business Online

QoS ist erforderlich, um Sprach-und Besprechungs Vorteile für Skype for Business Online zu erhalten. Sie können QoS konfigurieren, nachdem Sie sichergestellt haben, dass die Express Route-Netzwerkverbindung keinen anderen Office 365-Dienst Zugriff blockiert. Die Konfiguration für QoS wird im Artikel [Express Route und QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) beschrieben.
  
## <a name="troubleshooting-your-implementation"></a>Problembehandlung bei der Implementierung
<a name="troubleshooting"> </a>

Den ersten Blick auf die Schritte in diesem Einführungsleitfaden haben, die in Ihrem Implementierungsplan verpasst wurden? Gehen Sie zurück, und führen Sie nach Möglichkeit weitere kleine Netzwerktests aus, um den Fehler zu replizieren und dort zu debuggen.
  
Ermitteln, welche eingehenden oder ausgehenden Dienste während des Tests fehlgeschlagen sind. Holen Sie sich insbesondere die IP-Adressen und Subnetze für jeden der Dienste, die nicht erfolgreich waren. Gehen Sie vor, und führen Sie das Diagramm zur Netzwerktopologie auf Papier, und überprüfen Sie das Routing. ÜberPrüfen Sie insbesondere, wo das Express Route-Routing angekündigt wird, das Routing während des ausFalls, wenn möglich, mit Ablaufverfolgungen.
  
Führen Sie PSPing mit einer Netzwerkablaufverfolgung für jeden Kunden Endpunkt aus, und bewerten Sie die Quell-und Ziel-IP-Adressen, um zu prüfen, ob Sie erwartungsgemäß sind Führen Sie Telnet für einen beliebigen e-Mail-Host aus, den Sie auf dem Server mit dem Anschluß 25 verfügbar machen, und überprüfen Sie, ob SNAT die ursprüngliche Quell-IP-Adresse ausblenden sollte.
  
Beachten Sie, dass Sie bei der Bereitstellung von Office 365 mit einer Express Route-Verbindung sicherstellen müssen, dass die Netzwerkkonfiguration für Express Route optimal ausgelegt ist und Sie auch die anderen Komponenten in Ihrem Netzwerk wie Clientcomputer optimiert haben. Zusätzlich zur Verwendung dieses Planungshandbuchs zur Fehlerbehebung für die Schritte, die Sie möglicherweise übersehen haben, haben wir auch einen [Leistungsproblem Plan für Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) geschrieben.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Verwenden von BGP-Communities in Express Route für Office 365-Szenarien (Preview)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Express Route und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit Express Route](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
