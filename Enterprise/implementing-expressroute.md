---
title: Implementierung von ExpressRoute für Office 365
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
description: ExpressRoute für Office 365 bietet einen alternativen Pfad routing mit vielen Internet facing Office 365-Dienste. Die Architektur von ExpressRoute für Office 365 basiert auf Office 365-Diensten, die bereits zugänglich über das Internet in den bereitgestellten ExpressRoute Stromkreisen für nachfolgende Redistribution diese IP-Präfixe in sind öffentliche IP-Präfixen Werbung Ihr Netzwerk. Mit ExpressRoute können Sie effektiv mehrere verschiedene routing Pfade, über das Internet und über ExpressRoute, für viele Office 365-Dienste. Diesen Zustand in Ihrem Netzwerk weiterleiten kann eine erhebliche Änderung zum Aufbau der internen Netzwerktopologie darstellen.
ms.openlocfilehash: e535135557f7f2f64077c1d926f120fff78dbd42
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25715871"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementierung von ExpressRoute für Office 365

ExpressRoute für Office 365 bietet einen alternativen Pfad routing mit vielen Internet facing Office 365-Dienste. Die Architektur von ExpressRoute für Office 365 basiert auf Office 365-Diensten, die bereits zugänglich über das Internet in den bereitgestellten ExpressRoute Stromkreisen für nachfolgende Redistribution diese IP-Präfixe in sind öffentliche IP-Präfixen Werbung Ihr Netzwerk. Mit ExpressRoute können Sie effektiv mehrere verschiedene routing Pfade, über das Internet und über ExpressRoute, für viele Office 365-Dienste. Diesen Zustand in Ihrem Netzwerk weiterleiten kann eine erhebliche Änderung zum Aufbau der internen Netzwerktopologie darstellen.
  
 **Status:** Vollständiges Handbuch v2
  
Sie müssen Ihre ExpressRoute für Office 365-Implementierung für die Netzwerk-Komplexität ergebende routing über beide eine dedizierte Verbindung mit Routen in Ihrer Kernnetzwerk und dem Internet eingefügten einzeln zu autorisieren sorgfältig planen. Wenn Sie und Ihr Team die detaillierte Planung und Tests in diesem Handbuch nicht ausführen, besteht ein hohes Risiko, die auftreten können zeitweilige oder insgesamt Verlust der Konnektivität mit Office 365-Dienste bei der Netzfrequenz ExpressRoute aktiviert ist.
  
Um eine erfolgreiche Implementierung haben, müssen Sie analysieren Ihrer infrastrukturanforderungen, detaillierte Netzwerk Assessment durchlaufen und entwerfen, sorgfältig planeinführung auf eine Weise mehrstufige und gesteuerte und erstellen eine detaillierte Überprüfung und Test Plan. Für eine große, verteilte Umgebung ist es nicht ungewöhnlich, umfassen einige Monate Implementierungen finden Sie unter. Dieses Handbuch soll Vorausplanung helfen.
  
Große Bereitstellungen erfolgreiche kann sechs Monate dauern, bei der Planung und häufig Teammitglieder von vielen Bereichen in der Organisation, einschließlich Netzwerk, Firewall- und Proxy-Server-Administratoren, Office 365-Administratoren, Sicherheit, Endbenutzersupport, Project enthalten Management und Führungskräfte. Ihre Investitionen in den Planungsprozess reduziert die Wahrscheinlichkeit, die Bereitstellungsfehler, was zu Ausfallzeiten oder komplex und kostspielig Problembehandlung auftreten können.
  
Wir erwarten, dass die folgenden erforderlichen Komponenten ausgeführt werden, bevor dieses Implementierungshandbuch gestartet wird.
  
1. Sie haben eine Bewertung Netzwerk, um festzustellen, ob ExpressRoute empfohlen und ist abgeschlossen.

2. Sie haben einen ExpressRoute Netzwerk-Dienstanbieter ausgewählt. Hier finden Sie Informationen zu den [ExpressRoute Partner und Peers Speicherorte](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Sie haben bereits lesen und Verstehen der [ExpressRoute Dokumentation](https://azure.microsoft.com/documentation/services/expressroute/) und des internen Netzwerks ist berechtigt, ExpressRoute erforderlichen Komponenten Ende zum erfüllen.

4. Ihr Team Leseberechtigungen aller öffentlichen Anleitungen und -Dokumentation unter [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert), und überwacht die Datenreihe [Azure ExpressRoute für Office 365-Schulungen](https://channel9.msdn.com/series/aer) auf Channel 9 zu wichtigen technischen Einzelheiten, einschließlich vertraut:

      - Die Internet Abhängigkeiten SaaS-Dienste.

      - Informationen zum Vermeiden asymmetrischen Routen und komplexe routing behandeln.

      - Informationen zum Umkreis-Sicherheit, Verfügbarkeit und Ebene Anwendungssteuerelemente integrieren.

## <a name="begin-by-gathering-requirements"></a>Beginnen Sie mit dem Erfassen von Anforderungen
<a name="requirements"> </a>

Starten Sie, indem Sie bestimmen, welche Features und Dienste, die Sie in Ihrer Organisation einführen möchten. Sie müssen ermitteln, welche Features von verschiedenen Office 365-Dienste verwendet werden soll und welche Standorte in Ihrem Netzwerk Personen, die diese Features verwenden gehostet werden. Mit dem Katalog Szenarien, müssen Sie das Netzwerk-Attribute, die Hinzufügen jedes dieser Szenarien erfordern. wie ein-und ausgehenden Datenverkehr fließt und wenn die Office 365-Endpunkte verfügbar über ExpressRoute oder nicht sind.
  
Um den Anforderungen der Organisation zu erfassen:
  
- Katalog mit den für eingehenden und ausgehenden Netzwerkdatenverkehr für die Office 365-Dienste Ihrer Organisation verwendeten. Die Beschreibung der Abläufe, die erfordern unterschiedliche Office 365-Bereitstellungsszenarios finden Sie in Office 365-URLs und IP-Adressbereiche Seite.

- Sammeln Sie die Dokumentation der vorhandenen Netzwerktopologie mit Details zu Ihrer internen WAN-Backbone und Topologie, die Konnektivität von Satelliten Websites, letzten Meile Benutzerkonnektivität: routing an Netzwerk Umkreisnetzwerk Ausgang Punkt und Proxy-Dienste.

  - Identifizieren Sie eingehende Dienstendpunkten auf die Netzwerkdiagramme, die Office 365 und andere Microsoft-Dienste, eine Verbindung herstellt, Internet und vorgeschlagenen ExpressRoute Verbindungspfade anzeigt.

  - Identifizieren Sie alle geografische Standorte und WAN-Konnektivität zwischen Standorten zusammen mit welche Standorte ein Ausgang zum Internet haben und welche Standorte vorgeschlagen werden, ein Ausgang mit einem ExpressRoute Peers Speicherort haben.

  - Identifizieren Sie alle Edge-Geräte, beispielsweise Proxys, durch Firewalls und So weiter und ihre Beziehung fließt Überblick über das Internet und ExpressRoute catalog.

  - Dokumentieren Sie, ob Endbenutzer mit Office 365-Diensten über direkte routing oder indirekte Anwendungsproxy für Internet- und ExpressRoute Datenflüsse zugreift.

- Fügen Sie den Speicherort Ihres Mandanten und erfüllen-me Standorte Netzwerkdiagramm.

- Schätzen Sie die erwartete und beobachteten Netzwerk Leistung und Wartezeit Merkmale von wichtigen Benutzerspeicherorten zu Office 365. Beachten Sie, dass Office 365 global und verteilt Reihe an Diensten ist und verbindet Benutzer für Speicherorte, die sich aus dem Speicherort ihrer Mandanten liegen möglicherweise beibehalten. Aus diesem Grund wird empfohlen, messen und Wartezeit zwischen dem Benutzer und am nächstgelegenen Rand Ihres globaler Microsoft-Netzwerk über Verbindungen mit ExpressRoute und Internet optimieren. Ihre Ergebnisse aus der Netzwerk-Bewertung können Sie um mit dieser Aufgabe zu unterstützen.

- Liste Unternehmen Network Security und Anforderungen nach hoher Verfügbarkeit, die mit der neuen Verbindung ExpressRoute erfüllt sein müssen. Angenommen, wie Benutzer weiterhin Zugriff auf Office 365 bei Internet Ausgang oder ExpressRoute Netzfrequenz Fehler zu erhalten.

- Dokument die eingehende und ausgehende Office 365-Netzwerk fließt verwendet den Pfad Internet, und die ExpressRoute verwenden. Die Merkmale der geografischen Standorten Ihrer Benutzer und Details Ihrer lokalen Netzwerktopologie erfordern möglicherweise Planen von Speicherort für einen Benutzer zu einer anderen unterscheiden.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Katalog mit den ausgehenden und eingehenden Netzwerkverkehr
<a name="trafficCatalog"> </a>

Um Routing- und anderen Netzwerk Komplexität zu minimieren, wird empfohlen, dass Sie nur ExpressRoute für Office 365 für die Netzwerk-Datenverkehr fließt, die erforderlich sind verwenden, um über eine dedizierte Verbindung aufgrund von behördlichen Vorschriften oder als Ergebnis der Bewertung Netzwerk zu wechseln. Darüber hinaus wird empfohlen, dass Sie den Bereich der ExpressRoute routing und Ansatz Netzwerk ausgehenden und eingehenden Datenverkehr fließt als unterschiedliche Phasen des Implementierungsprojekts bereitstellen. Bereitstellen von ExpressRoute für Office 365 für nur Benutzer initiiert Netzwerk ausgehenden Datenverkehr fließt und Netzwerk eingehenden Datenverkehr fließt über das Internet unterstützt Sie dabei, die Anhebung der Topologie Komplexität und Risiken der Einführung von zusätzlichen steuern lassen asymmetrischen Mögliche Werte-Routing.
  
Netzwerk-Datenverkehr Katalog sollten Auflistungen von alle ein-und ausgehenden Verbindungen enthalten, die Sie zwischen Ihrer lokalen Netzwerk und Microsoft.
  
- Netzwerk ausgehende Datenverkehr fließt werden alle Szenarien, in dem eine Verbindung aus der lokalen Umgebung, wie beispielsweise von internen Clients oder Servern mit einem Ziel der Microsoft-Dienste gestartet wird. Diese Verbindungen möglicherweise zu Office 365 direkt oder indirekt, z. B., wenn die Verbindung über Proxyserver, Firewalls oder andere Netzwerkgeräte im Pfad zu Office 365 gesendet wird.

- Netzwerk eingehenden Datenverkehr fließt werden alle Szenarien, in dem eine Verbindung mit einem lokalen Host aus der Microsoft-Cloud gestartet wird. Diese Verbindungen müssen in der Regel durchlaufen Firewall und anderen Sicherheitsinfrastruktur, die Kunden Codezugriffssicherheits-Richtlinie für externen Quelle stammen Datenflüsse erforderlich sind.

Lesen Sie den Abschnitt **sicherstellen Route Symmetrie** des Artikels [Routing mit ExpressRoute für Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) , um zu bestimmen, welche Dienste eingehenden Datenverkehr zu senden und suchen Sie nach der Spalte in der Office 365 [ **ExpressRoute für Office 365** gekennzeichnet wird Endpunkte](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) Referenzartikel, um die restlichen die Konnektivitätsinformationen zu bestimmen.
  
Für jeden Dienst, die eine ausgehende Verbindung erforderlich sind, möchten Sie die geplante-Konnektivität für den Dienst, einschließlich Netzwerkrouting, Proxykonfiguration, Paketinspektion beschreiben und Bandbreite benötigt.
  
Für jeden Dienst, die eine eingehende Verbindung erforderlich sind, benötigen Sie einige zusätzliche Informationen. Server in der Microsoft-Cloud werden Verbindungen zu Ihrem lokalen Netzwerk herstellen. um sicherzustellen, dass die Verbindung ordnungsgemäß hergestellt werden, möchten Sie alle Aspekte der dieser Konnektivität, einschließlich beschreiben. die öffentlichen DNS-Einträge für die Dienste, die diese eingehenden Verbindungen akzeptiert werden, die CIDR formatiert IPv4-IP-Adressen, welche Geräte Internetdienstanbieter beteiligt ist, und wie eingehenden NAT oder Quell-NAT für diese Verbindungen behandelt wird.
  
Eingehende Verbindungen überprüft werden sollten, unabhängig davon, ob sie über das Internet herstellen oder ExpressRoute, um sicherzustellen, dass asymmetrische routing noch nicht eingeführt wurden. In einigen Fällen auf die lokale Endpunkte, dass Office 365-Diensten auch eingehende Verbindungen und Mai Initiieren von anderen Microsoft und nicht-Microsoft-Dienste zugegriffen werden müssen. Aktivieren von ExpressRoute auf diese Dienste für Office 365 Zwecke routing andere Szenarien Unterbrechungsmodus nicht die Lektüre wird. In vielen Fällen können-Kunden müssen bestimmte Änderungen an ihrem internen Netzwerk, implementieren wie Quelle basierend NAT, um sicherzustellen, dass eingehende fließt von Microsoft symmetrischen bleiben, nachdem ExpressRoute aktiviert ist.
  
Es folgt ein Beispiel für die Detailebene erforderlich. In diesem Fall weitergeleitet Exchange Hybrid an das lokale System über ExpressRoute.

|**Connection-Eigenschaft**|**Wert**|
|:-----|:-----|
|**Richtung der Netzwerk-Datenverkehr** <br/> |Eingehend  <br/> |
|**Dienst** <br/> |Exchange Hybrid  <br/> |
|**Öffentliche Office 365-Endpunkt (Quelle)** <br/> |Exchange Online (IP-Adressen)  <br/> |
|**Öffentliche lokalen Endpunkt (Ziel)** <br/> |5.5.5.5  <br/> |
|**Öffentliche (Internet) DNS-Eintrag** <br/> |Autodiscover.contoso.com  <br/> |
|**Diese lokalen Endpunkt wird von anderen Microsoft-Diensten (nicht Office 365) für verwendet werden** <br/> |Nein  <br/> |
|**Diesen lokalen Endpunkt wird von Benutzern/Systeme im Internet verwendet werden** <br/> |Ja  <br/> |
|**Interne Systeme über öffentliche Endpunkte veröffentlicht** <br/> |Exchange Server ClientAccess-Funktion (lokal) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**IP-Ankündigung des öffentlichen Endpunkts** <br/> |**Internet**: 5.5.0.0/16  <br/> **Um ExpressRoute**: 5.5.5.0/24  <br/> |
|**Sicherheit/Umkreis-Steuerelemente** <br/> |**Internet Pfad**: DeviceID_002  <br/> **ExpressRoute Pfad**: DeviceID_003  <br/> |
|**Hohe Verfügbarkeit** <br/> |Aktiv/aktiv über georedundantes 2  <br/> ExpressRoute Circuits - Chicago und Dallas  <br/> |
|**Pfad Symmetrie-Steuerelement** <br/> |**Methode**: Quell-NAT  <br/> **Internet Pfad**: Quell-NAT eingehende Verbindungen mit 192.168.5.5  <br/> |**ExpressRoute Pfad**: Quell-NAT-Verbindungen für 192.168.1.0 (Chicago) und 192.168.2.0 (Dallas)  <br/> |

Es folgt ein Beispiel für einen Dienst, der nur ausgehende ist:

|**Connection-Eigenschaft**|**Wert**|
|:-----|:-----|
|**Richtung der Netzwerk-Datenverkehr** <br/> |Ausgehend  <br/> |
|**Dienst** <br/> |SharePoint Online  <br/> |
|**Der lokale Endpunkt (Quelle)** <br/> |Arbeitsstation des Benutzers  <br/> |
|**Öffentliche Office 365-Endpunkt (Ziel)** <br/> |SharePoint Online (IP-Adressen)  <br/> |
|**Öffentliche (Internet) DNS-Eintrag** <br/> |\*. sharepoint.com (und zusätzliche FQDNs)  <br/> |
|**CDN-Verweise** <br/> |CDN.sharepointonline.com (und zusätzliche FQDNs) - IP-Adressen von CDN-Anbietern verwaltet)  <br/> |
|**IP-Ankündigung und NAT verwendet** <br/> |**Internet Pfad/Quell-NAT**: 1.1.1.0/24  <br/> **ExpressRoute Pfad/Quell-NAT**: 1.1.2.0/24 (Chicago) und 1.1.3.0/24 (Dallas)  <br/> |
|**Konnektivitätsmethode** <br/> |**Internet**: über Layer 7-Proxy (dafür)  <br/> **ExpressRoute**: Direktes routing (keine Proxy)  <br/> |
|**Sicherheit/Umkreis-Steuerelemente** <br/> |**Internet Pfad**: DeviceID_002  <br/> **ExpressRoute Pfad**: DeviceID_003  <br/> |
|**Hohe Verfügbarkeit** <br/> |**Internet Pfad**: redundante Internet Ausgang  <br/> **ExpressRoute Pfad**: aktiv/aktiv "Hot Kartoffel' routing über 2 georedundantes ExpressRoute-Circuits - Chicago und Dallas  <br/> |
|**Pfad Symmetrie-Steuerelement** <br/> |**Methode**: Quell-NAT für alle Verbindungen  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Ihr Topologieentwurf Netzwerk mit regionalen-Konnektivität
<a name="topology"> </a>

Wenn Sie die Dienste und deren zugeordneten Netzwerk Datenverkehr fließt verstanden haben, können Sie ein Netzwerkdiagramm erstellen, die diese neue Konnektivitätsanforderungen beinhaltet und veranschaulicht die Änderungen machen Sie ExpressRoute für Office 365 verwenden. Ihr Diagramm sollte Folgendes enthalten:
  
1. Alle Benutzer Speicherorte, auf dem Office 365 und andere Dienste aus zugegriffen werden.

2. Alle Internet- und ExpressRoute Ausgang Punkt.

3. Alle ausgehenden und eingehenden Geräte, die Konnektivität an-oder im Netzwerk, einschließlich Router, Firewalls, Proxy-Anwendungsservern und Erkennung/Intrusionsprävention verwalten.

4. Interne Ziele für alle eingehenden Datenverkehr wie internen AD FS-Server, die Verbindungen von ADFS Web Application Proxy-Server zu übernehmen.

5. Katalog aller IP-Subnetze, der angezeigt wird

6. Identifizieren von jedem Standort, auf dem Benutzer Zugriff auf Office 365 aus und Auflisten der Besprechung-me Standorte, die für ExpressRoute verwendet werden soll.

7. Speicherorte und Teile des internen Netzwerktopologie, auf dem Microsoft IP Präfixe und Erfahrungen aus dem ExpressRoute akzeptiert werden, gefiltert und an weitergegeben.

8. Topologie des Netzwerks sollten veranschaulichen der geografische Standort jedes Netzwerksegment und wie sie mit Microsoft Network über ExpressRoute und/oder dem Internet verbunden.

Im nachstehenden Diagramm zeigt die einzelnen Speicherort, in dem Benutzer Office 365 aus zusammen mit der eingehende und ausgehende routing Werbung zu Office 365 verwenden werden.
  
![Regionale geografische Meet ExpressRoute-me](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Für ausgehenden Datenverkehr Zugriff die Personen Office 365 in drei Möglichkeiten:
  
1. Über eine Sofortbesprechung-me Speicherort in Nordamerika für Personen, die in Kalifornien (CA).

2. Über eine Sofortbesprechung-me Speicherort in Hongkong für Personen, die in Hongkong.

3. Über das Internet in Bangladesch, in denen weniger Personen vorhanden sind und keine ExpressRoute Netzfrequenz bereitgestellt.

![Ausgehende Verbindungen für regionale Diagramm](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Entsprechend gibt der eingehenden Datenverkehr von Office 365 in drei verschiedene Arten zurück:
  
1. Über eine Sofortbesprechung-me Speicherort in Nordamerika für Personen, die in Kalifornien (CA).

2. Über eine Sofortbesprechung-me Speicherort in Hongkong für Personen, die in Hongkong.

3. Über das Internet in Bangladesch, in denen weniger Personen vorhanden sind und keine ExpressRoute Netzfrequenz bereitgestellt.

![Eingehende Verbindungen für regionale Diagramm](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Bestimmen der geeigneten Meet-me Speicherort

Die Auswahl von Meet-me Speicherorte, die den physischen Standort, an dem Ihre Netzfrequenz ExpressRoute Ihr Netzwerk mit dem Microsoft-Netzwerk verbunden, sind, hängt von den Speicherorten, in dem Personen greifen auf Office 365 aus, ab. Als eine SaaS-Lösung funktioniert Office 365 unter IaaS oder PaaS regionalen Modell auf die gleiche Weise wie nicht wie Azure. Office 365 ist stattdessen eine verteilte Gruppe von Collaboration Services, in dem Benutzer müssen möglicherweise eine Verbindung mit Endpunkten in mehreren Rechenzentren und Bereiche, die es unbedingt möglicherweise nicht in der gleichen Speicherort oder die Region, in dem Mandanten des Benutzers gehostet wird.
  
Dies bedeutet, dass die wichtigste Überlegung Sie bei der Auswahl Meet müssen-me Speicherorte für ExpressRoute für Office 365 ist, auf dem die Personen in Ihrer Organisation aus Verbindung hergestellt werden soll. Die allgemeine Empfehlung für eine optimale Office 365-Diensten ist implementieren routing, sodass Benutzeranfragen zu Office 365-Diensten in Microsoft Network über den kürzesten Netzwerkpfad übergeben werden, dies ist auch wird so genannte 'Hot Kartoffel' routing. Angenommen, wenn die meisten Office 365-Benutzer in einem oder zwei Standorten befinden, auswählen Meet-me Speicherorte, die in der nächsten Nähe zum Speicherort der diese Benutzer sind werden das optimale Design erstellen. Wenn Ihr Unternehmen in vielen unterschiedlichen Regionen großen Benutzeranzahl verfügt, möglicherweise möchten Sie erwägen Sie mehrere ExpressRoute Circuits und erfüllen-me Speicherorte. Für einige Ihrer Standorte der kürzeste/den optimalen Pfad in Microsoft-Netzwerk und Office 365, möglicherweise nicht über Ihre internen WAN und ExpressRoute Meet-me Datenpunkte, aber über das Internet.
  
Häufig sind mehrere Meet-me Speicherorte, die innerhalb eines Bereichs mit relativen Nähe für Ihre Benutzer ausgewählt werden konnte. Füllen Sie in der folgenden Tabelle Ihre Entscheidungen, leiten lassen.

|**Geplante ExpressRoute Meet-me Speicherorten in Kalifornien (CA) und New York**||
|:-----|:-----|
|Standort  <br/> |Anzahl der Personen  <br/> |Wartezeit zu Microsoft-Netzwerk über Internet-Ausgang erwartet  <br/> |Erwartete Wartezeit zu Microsoft-Netzwerk über ExpressRoute  <br/> |
|München  <br/> |10,000  <br/> |~ 15ms  <br/> |~ 10 ms (über Silicon Valley)  <br/> |
|Washington DC  <br/> |15,000  <br/> |~ 20 ms  <br/> |~ 10 ms (über New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15ms  <br/> |~ 40ms (über New York)  <br/> |

Nachdem der globalen Netzwerkarchitektur zeigt die Office 365-Region, ExpressRoute Netzwerk-Dienstanbieter erfüllen-me Speicherorte und der Menge der Personen, hängt vom Speicherort wurde entwickelt, um festzustellen, ob alle Optimierungen hergestellt werden können verwendet werden. Gegebenenfalls wird auch angezeigt globale Hairpin Netzwerkverbindungen, in dem leitet den Datenverkehr an einem entfernten Standort, um der Besprechung erhalten-me Speicherort. Wenn ein Hairpin im globalen Netzwerk erkannt wird, dass diese vor dem Fortfahren beseitigt werden sollte. Entweder suchen Sie nach einem anderen Meet-me Speicherort, oder verwenden Sie selektive Internet separate Ausgang zeigt auf das Hairpin zu vermeiden.
  
Im erste Diagramm zeigt ein Beispiel eines Kunden mit zwei physische Standorte in Nordamerika. Sie können die Informationen zu Standorten, Speicherorte für Office 365-Mandanten, sehen und erfüllen mehrere Auswahlmöglichkeiten ExpressRoute-me Speicherorte. In diesem Beispiel wird der Kunde der Besprechung ausgewählt-me Speicherort basierend auf zwei Prinzipien, in der Reihenfolge:
  
1. Die Personen in ihrer Organisation am nächsten in der Nähe.

2. Nächste in der Nähe einer Microsoft-Rechenzentrum, in Office 365 gehostet wird.

![Geografische Meet ExpressRoute US-me](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Erweitern dieses Konzepts etwas weiter, das zweite Diagramm zeigt ein Beispiel multinationale Kunden mit ähnlichen Informationen und entscheidungsfindungen konfrontiert. Diese Kunden verfügt über ein kleines Büro in Bangladesch mit nur einem kleinen Team konzentriert sich ihre Präsenz in der Region wachsende zehn Personen. Es wird eine Besprechung-mich Speicherort in Chennai und einem Microsoft Datacenter mit Office 365 gehostet in Chennai so eine Sofortbesprechung-mich Speicherort wäre sinnvoll; Es ist jedoch für zehn Personen die Ausgaben für die zusätzliche Leitung aufwändige. Wie Sie Ihr Netzwerk betrachten, müssen Sie ermitteln, ob die Wartezeit beim Senden des Netzwerkverkehrs in Ihrem Netzwerk effektiver als Ausgaben Kapital, um eine andere ExpressRoute Netzfrequenz zu erwerben ist.
  
Alternativ können die zehn Personen in Bangladesch auftreten eine bessere Leistung mit Datenverkehr über das Internet mit dem Microsoft-Netzwerk gesendet wird, als sie in ihrem internen Netzwerk routing würden, wie es in den Diagrammen einführenden ergab und reproduziert unten.
  
![Ausgehende Verbindungen für regionale Diagramm](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Erstellen Sie Ihre ExpressRoute für Office 365-Implementierungsplan
<a name="implementation"> </a>

Ihr Plan zur Implementierung sollte die technischen Einzelheiten konfigurieren ExpressRoute als auch die Informationen zum Konfigurieren von allen anderen Infrastruktur in Ihrem Netzwerk, wie die folgenden umfassen.
  
- Planen der Dienste zwischen ExpressRoute und Internet aufgeteilt.

- Planen der Bandbreite, Sicherheit, hohe Verfügbarkeit und Failover.

- Entwerfen Sie eingehende und ausgehende routing, einschließlich der richtigen routing Pfad Optimierungen unterschiedlichen Standorten

- Entscheiden Sie, wie weit ExpressRoute Routen in Ihrem Netzwerk angezeigt werden und was ist der Mechanismus für Clients Internet- oder ExpressRoute Pfad aus. beispielsweise direktes routing oder-Anwendung Proxy.

- Planen der DNS-Datensatz ändert, einschließlich [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) Einträge.

- Planen der Quelle des ausgehenden und eingehenden NAT einschließlich NAT-Strategie

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planen Sie Ihre routing mit Internet- und Netzwerkpfade ExpressRoute
<a name="paths"> </a>

- Für die anfängliche Bereitstellung werden alle eingehenden Dienste, wie eingehende e-Mail oder hybridkonnektivität, auf das Internet empfohlen.

- Planen von Endbenutzer Client LAN-routing, wie das [Konfigurieren einer Datei PAC/WPAD](https://aka.ms/manageo365endpoints), Standardroute, Proxyservern und BGP Route anzeigen.

- Planen der Umkreis-routing, einschließlich Proxyservern, Firewalls und Cloud-Proxys.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planen einer Ihrer Bandbreite, Sicherheit, hohe Verfügbarkeit und failover
<a name="availability"> </a>

Erstellen eines Plans für die Bandbreite für jede Haupt-Arbeitslast für Office 365. Schätzen Sie Exchange Online, SharePoint Online und Skype separat für Business Online erforderliche Bandbreite. Sie können die Berechnungsmodule für die Schätzung, den, die wir für Exchange Online und Skype für Unternehmen als Ausgangspunkt bereitgestellt haben. ein Pilottest mit repräsentative, Benutzerprofile und Speicherorte ist jedoch erforderlich, damit die bandbreitenanforderungen Ihrer Organisation vollständig zu verstehen.
  
Hinzufügen, wie Sicherheit auf jedem Internet- und ExpressRoute Ausgang Speicherort auf Ihrem Plan verarbeitet wird, denken Sie daran alle ExpressRoute Verbindungen mit Office 365 verwenden, öffentliche peering und weiterhin gemäß Ihrer Firma Sicherheitsrichtlinien Verbinden mit externen gesichert werden muss Netzwerke.
  
Hinzufügen von Details zu Ihren Plan darüber, den welche Personen betroffen sind, durch die Art des Ausfalls und wie die Personen ihre Aufgaben die einfachste Weise voller Auslastung betrieben werden können.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planen der bandbreitenanforderungen einschließlich Skype für geschäftlichen Anforderungen auf Jitter, Latenz, Überlastung und Reserven
  
Skype für Business Online hat auch bestimmte zusätzliche netzwerkanforderungen für die im Artikel [Medienqualität und Leistung des Netzwerks Connectivity in Skype für Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)ausführlich dargestellt werden.
  
Lesen Sie den Abschnitt in [netzwerkplanung mit ExpressRoute für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd) **Bandbreite für Azure ExpressRoute planen** .
  
Wenn Sie eine Bewertung Bandbreite mit Pilotbenutzer ausführen, können Sie unsere Guide. [Office 365 leistungsoptimierung Baselines und Leistung Verlaufslisten verwenden](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planen der Anforderungen nach hoher Verfügbarkeit
  
Erstellen eines Plans für hohe Verfügbarkeit für Ihre Bedürfnisse und integrieren Sie dies in Ihrer aktualisierten Topologie Netzplandiagramm. Lesen Sie den Abschnitt **hohe Verfügbarkeit und Failover mit Azure ExpressRoute** in [netzwerkplanung mit ExpressRoute für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planen der Sicherheit netzwerkanforderungen
  
Erstellen Sie einen Plan für Ihr Netzwerk Sicherheit erfüllen und integrieren Sie dies in Ihrer aktualisierten Topologie Netzplandiagramm. Lesen Sie den Abschnitt **anwenden Security-Steuerelemente Azure ExpressRoute für Office 365-Szenarien** in [netzwerkplanung mit ExpressRoute für Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Entwerfen von ausgehenden Service-Konnektivität
<a name="outbound"> </a>

ExpressRoute für Office 365 verfügt über *ausgehende* netzwerkanforderungen, die möglicherweise nicht vertraut sind. Insbesondere die IP-Adressen, die Ihre Benutzer und Netzwerke zu Office 365 darstellen und fungieren als die Source-Endpunkte für ausgehende Netzwerkverbindungen an Microsoft spezifische Anforderungen unten beschriebenen einhalten müssen.
  
1. Die Endpunkte müssen öffentliche IP-Adressen sein, die an Ihr Unternehmen oder an Netzbetreiber bereitstellen ExpressRoute Konnektivität für Sie registriert sind.

2. Die Endpunkte müssen zusätzliche an Microsoft und validiert/akzeptierte durch ExpressRoute werden.

3. Die Endpunkte müssen nicht mit dem Internet mit der gleichen oder mehr bevorzugte routing Metrik angekündigt.

4. Die Endpunkte müssen nicht für Verbindung mit Microsoft Services verwendet werden, die nicht über ExpressRoute konfiguriert sind.

Wenn des netzwerkdesigns diese Kriterien nicht erfüllt, ist ein hohes Risiko, das Ihre Benutzer zu Office 365 und andere Microsoft-Dienste aufgrund von asymmetrischen routing oder Schwarz holing Route Verbindungsfehler treten. Dies tritt auf, wenn Anforderungen an Microsoft Services über ExpressRoute, weitergeleitet werden jedoch Antworten werden über das Internet zurück (oder umgekehrt) weitergeleitet, und die Antworten werden durch dynamische Netzwerkgeräte wie Firewalls gelöscht.
  
Die am häufigsten verwendete-Methode, die Sie verwenden können, um die oben beschriebenen Anforderungen erfüllen ist die Verwendung der Quell-NAT, entweder als Teil Ihres Netzwerks implementiert oder von Ihrem Netzbetreiber ExpressRoute bereitgestellt. Quell-NAT können Sie die Details und private IP-Adressierung des Netzwerks Internet aus ExpressRoute abstrakten und; gekoppelt mit Werbung von erforderlichen IP-Route, geben Sie einen einfachen Mechanismus zum Pfad Symmetrie sicherzustellen. Wenn Sie dynamische Netzwerkgeräte, die speziell für ExpressRoute Peers Speicherorte sind verwenden, müssen Sie separate NAT-Pools für jeden um Pfad Symmetrie sicherzustellen peering ExpressRoute implementieren.
  
Erfahren Sie mehr über die [ExpressRoute NAT-Anforderungen](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Fügen Sie die Änderungen für ausgehende Verbindungen an die Netzwerktopologie.
  
### <a name="design-inbound-service-connectivity"></a>Entwerfen von eingehenden Service-Konnektivität
<a name="inbound"> </a>

Die meisten Unternehmen Office 365-Bereitstellungen wird davon ausgegangen gewisse eingehende Verbindung zwischen Office 365 und lokale Dienste, wie beispielsweise für Exchange, SharePoint und Skype für Business hybridszenarien, Postfachmigrationen und Authentifizierung mithilfe von ADFS Infrastruktur. Wenn ExpressRoute Sie eine zusätzliche Routingpfad zwischen dem lokalen Netzwerk und Microsoft für ausgehende Verbindungen aktivieren, diese eingehenden Verbindungen erforderlich, auf den asymmetrischen routing versehentlich auswirken, selbst wenn Sie beabsichtigen, haben diese Abläufe werden weiter Verwenden Sie das Internet. Einige Vorsichtsmaßnahmen unten beschriebenen werden empfohlen, um sicherzustellen, dass wirkt sich nicht auf das Internet zur lokalen Systemen eingehende fließt von Office 365-basierten vorhanden ist.
  
Zum Minimieren der Risiken von asymmetrischen routing für Netzwerk eingehenden Datenverkehr fließt sollten alle eingehenden Verbindungen Quell-NAT verwenden, bevor sie in Segmente für Ihr Netzwerk weitergeleitet werden die routing Einblick in ExpressRoute haben. Wenn eingehenden Verbindungen auf einem Netzwerksegment routing Einblick in ExpressRoute ohne Quell-NAT zulässig sind, Anfragen von Office 365 werden aus dem Internet eingeben, aber die Antwort zurückgehen zu Office 365 wird die ExpressRoute bevorzugen Netzwerkpfad wieder mit dem Microsoft-Netzwerk, asymmetrischen routing verursacht.
  
Sie sollten eine der folgenden Implementierungsmuster zu dieser Anforderung erfüllen:
  
1. Quell-NAT ausführen, bevor Anfragen weitergeleitet werden, in das interne Netzwerk mit Netzwerkgeräte wie Firewalls oder Lastenausgleichsmodule verwenden auf den Pfad aus dem Internet für Ihre lokale-Systeme.

2. Stellen Sie sicher, dass die Netzwerksegmente, an dem eingehende Dienste, wie vorne Beenden von Servern oder reverse Proxy-Systemen, Behandeln von Internet Verbindungen befinden sich, nicht ExpressRoute Routen weitergegeben werden.

Explizit accounting für diese Szenarien in Ihrem Netzwerk und Sicherheit für alle eingehenden Netzwerkdatenverkehr werden über das Internet hilft bei der Bereitstellung und betriebliche Risiken asymmetrischen Routing Minimierung übertragen.
  
Möglicherweise Fällen, in dem Sie auswählen können, um einige eingehende fließt über ExpressRoute Verbindungen zu leiten. Übernehmen Sie für diese Szenarien folgende zusätzliche Aspekte berücksichtigt.
  
1. Office 365 können nur Ziel lokalen-Endpunkte, die öffentliche IP-Adressen verwenden. Dies bedeutet, dass auch wenn der lokalen, die eingehende Endpunkt nur für Office 365 über ExpressRoute verfügbar gemacht wird, noch ein öffentlichen IP-Adresse zugeordnet haben.

2. Alle DNS-namensauflösung, die Office 365-Dienste ausführen, um lokale Endpunkte zu beheben Vorkommen von öffentlichen DNS-Servers. Dies bedeutet, dass Sie eingehende Dienstendpunkten FQDN IP-Zuordnungen im Internet registrieren müssen.

3. Um eingehende Netzwerkverbindungen über ExpressRoute zu erhalten, müssen die öffentliche IP-Subnetze für diese Endpunkte über ExpressRoute an Microsoft angekündigt.

4. Diese Netzwerk eingehenden Datenverkehr fließt um die ordnungsgemäße Sicherheit sicherzustellen sorgfältig und Netzwerk-Steuerelemente werden angewendet wird, gemäß Ihrer Firma Sicherheit und Netzwerkrichtlinien.

5. Einmal Ihre lokale, die eingehende Endpunkte an Microsoft über ExpressRoute bekannt gegeben werden, ExpressRoute effektiv der bevorzugten Routingpfad zu diese Endpunkte für alle Microsoft-Dienste, einschließlich Office 365 werden. Dies bedeutet, dass die Endpunkt-Subnetze nur für die Kommunikation mit Office 365-Diensten und keine anderen Dienste auf dem Microsoft-Netzwerk verwendet werden müssen. Andernfalls wird Ihres Entwurfs verursacht asymmetrischen routing eingehende Verbindungen von anderen Microsoft Services weiterleiten möchten, auf dem über ExpressRoute, eingehend, während der Rückgabe Pfad im Internet verwendet werden soll.

6. Verbindung ist das Ereignis ein ExpressRoute oder erfüllen-me Speicherort steht nicht zur Verfügung, um sicherzustellen, dass die lokalen müssen eingehende Endpunkte sind weiterhin verfügbar, die über einen separaten Netzwerkpfad annehmen. Dies kann für diese Endpunkte über mehrere ExpressRoute Schaltkreise Werbung Subnetze bedeuten.

7. Es wird empfohlen, Quell-NAT für alle Netzwerk eingehenden Datenverkehr fließt eingeben Ihres Netzwerks durch ExpressRoute, insbesondere dann, wenn diese Datenflüsse dynamische Netzwerkgeräte wie Firewalls schneidet anwenden.

8. Einige lokale Dienste, wie AD FS-Proxy oder Exchange-AutoErmittlung können eingehende Anfragen von Office 365-Diensten und Benutzer aus dem Internet erhalten. Für diese Anforderungen zielt Office 365 demselben FQDN wie Benutzeranfragen über das Internet. Festlegen, dass eingehende benutzerverbindungen über das Internet diese Endpunkte lokalen beim Erzwingen der Office 365-Verbindungen mit ExpressRoute, stellt erhebliche routing Komplexität. Für den Großteil der Kunden wird implementieren solche komplexen Szenarien über ExpressRoute aufgrund von betrieblichen Aspekte nicht empfohlen. Diese zusätzliche Aufwand umfasst, Verwalten von Risiken asymmetrischen weiterleiten und erfordert, dass Sie sorgfältig routing Werbung und Richtlinien über mehrere Dimensionen verwalten.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Aktualisieren Sie Ihre Topologie Netzwerkplan angezeigt, wie Sie asymmetrische Routen vermeiden möchten
<a name="asymmetric"> </a>

Möchten Sie vermeiden asymmetrischen routing, um sicherzustellen, dass Personen in Ihrer Organisation nahtlos Office 365 sowie andere wichtige Dienste im Internet verwenden können. Es gibt zwei allgemeine Konfigurationen haben Kunden, die dazu führen, asymmetrische routing dass. Jetzt ist ein guter Zeitpunkt für die Netzwerkkonfiguration überprüfen Sie planen, verwenden, und überprüfen Sie, ob eines dieser Szenarien für den asymmetrischen routing vorhanden sein.
  
Zunächst wird ein paar Situationen folgenden Netzwerkdiagramm zugeordnet untersucht. In diesem Diagramm allen Servern, die eingehende Anfragen erhalten beispielsweise ADFS oder lokale hybride Server sind im Rechenzentrum New Jersey und werden mit dem Internet angekündigt.
  
1. Während das Umkreisnetzwerk sicher ist, ist keine Quell-NAT für eingehende Anforderungen zur Verfügung.

2. Die Servern im Rechenzentrum New Jersey können Internet und ExpressRoute Routen finden Sie unter.

![ExpressRoute Connectivity (Übersicht)](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Wir haben auch Vorschläge zu deren Lösung.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1: Cloud, um lokale Verbindung über das Internet
  
Das folgende Diagramm veranschaulicht den asymmetrischen Netzwerkpfad ausgeführt, wenn die Netzwerkkonfiguration NAT für eingehende Anfragen von der Microsoft-Cloud über das Internet zur Verfügung steht.
  
1. Die eingehende Anforderung von Office 365 Ruft die IP-Adresse des lokalen Endpunkts aus öffentlichen DNS und sendet die Anforderung an das Umkreisnetzwerk.

2. In dieser Konfiguration fehlerhaften keine Quell-NAT konfiguriert ist oder das Umkreisnetzwerk, in dem der Datenverkehr wird, über gesendete resultierendes in die tatsächliche Quell-IP-Adresse als Ziel für die Rückgabe verwendet wird.

  - Der Server in Ihrem Netzwerk leitet die Rückgabe von Daten zu Office 365 über alle verfügbaren ExpressRoute Netzwerk.

  - Das Ergebnis ist eine asymmetrische Pfad für diese Fluss zu Office 365, wodurch eine unterbrochene Verbindung.

![ExpressRoute Asymetric routing Problem 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Lösung 1a: Quell-NAT
  
Einfach auf die eingehende Anforderung hinzufügen eine Quell-NAT löst dieses Netzwerk nicht richtig konfiguriert. In diesem Diagramm:
  
1. Die eingehende Anforderung weiterhin über Umkreisnetzwerk des Rechenzentrums New Jersey eingeben. Dieses Mal Quell-NAT ist verfügbar.

2. Die Antwort vom Server Routen zurück in die IP-Adresse zugeordneten Datenquelle NAT anstelle der ursprünglichen IP-Adresse in der Antwort zurückgeben entlang der Netzwerkpfad resultierendes Richtung.

![ExpressRoute Asymetric routing-Lösung 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Lösung 1 b: Route Bereichsdefinierung
  
Alternativ können Sie auswählen, nicht die ExpressRoute BGP Präfixe bekannt gegeben werden, können alternative Netzwerkpfad für diesen Computer zu entfernen. In diesem Diagramm:
  
1. Die eingehende Anforderung weiterhin über Umkreisnetzwerk des Rechenzentrums New Jersey eingeben. Diesmal die Präfixe über der Netzfrequenz ExpressRoute von Microsoft angekündigt sind nicht im Rechenzentrum New Jersey verfügbar.

2. Die Antwort vom Server Routen zurück in die IP-Adresse die ursprüngliche IP-Adresse zugeordnet sind, über die einzige Route verfügbar ist, in der Antwort zurückgeben entlang der Netzwerkpfad resultierendes Richtung.

![ExpressRoute Asymetric routing-Lösung 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2: Cloud, um lokale Verbindung über ExpressRoute
  
Das folgende Diagramm veranschaulicht den asymmetrischen Netzwerkpfad ausgeführt, wenn die Netzwerkkonfiguration NAT für eingehende Anfragen von der Microsoft-Cloud über ExpressRoute zur Verfügung steht.
  
1. Die eingehende Anforderung von Office 365 Ruft die IP-Adresse aus DNS und sendet die Anforderung an das Umkreisnetzwerk.

2. In dieser Konfiguration fehlerhaften keine Quell-NAT konfiguriert ist oder das Umkreisnetzwerk, in dem der Datenverkehr wird, über gesendete resultierendes in die tatsächliche Quell-IP-Adresse als Ziel für die Rückgabe verwendet wird.

  - Der Computer in Ihrem Netzwerk leitet die Rückgabe von Daten zu Office 365 über alle verfügbaren ExpressRoute Netzwerk.

  - Das Ergebnis ist eine asymmetrische Verbindung mit Office 365.

![ExpressRoute Asymetric routing Problem 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Lösung 2: Quell-NAT
  
Einfach auf die eingehende Anforderung hinzufügen eine Quell-NAT löst dieses Netzwerk nicht richtig konfiguriert. In diesem Diagramm:
  
1. Die eingehende Anforderung weiterhin über Umkreisnetzwerk des Rechenzentrums New York eingeben. Dieses Mal Quell-NAT ist verfügbar.

2. Die Antwort vom Server Routen zurück in die IP-Adresse zugeordneten Datenquelle NAT anstelle der ursprünglichen IP-Adresse in der Antwort zurückgeben entlang der Netzwerkpfad resultierendes Richtung.

![ExpressRoute Asymetric routing-Lösung 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papier stellen Sie sicher, dass das Netzwerk-Design Pfad Symmetrie verfügt

Zu diesem Zeitpunkt müssen Sie auf Papier stellen Sie sicher, dass Ihr Plan zur Implementierung Route Symmetrie für die verschiedenen Szenarien bietet, in dem Sie Office 365 verwenden möchten. Sie können die bestimmte Netzwerkroute identifizieren, die erwartet ausgeführt werden soll, wenn eine Person unterschiedlichen Features von den Dienst verwendet wird. Aus dem lokalen Netzwerk und WAN-routing für die Umkreis-Geräte, auf den Pfad der Konnektivität; ExpressRoute oder im Internet und bei der Verbindung mit den online-Endpunkt.
  
Sie müssen diesen Vorgang für alle Office 365 Netzwerkdienste führen, die zuvor als Dienste identifiziert wurden, die Ihre Organisation übernommen werden.
  
Es ist hilfreich, führen Sie diese Papier Durchlauf über Routen mit einer zweiten Person. Erklären Sie ihnen, wenn jedes Netzwerk-Hop, zum Abrufen der nächsten Route aus und stellen Sie sicher erwartet wird, dass Sie mit den routing Pfaden vertraut sind. Denken Sie daran, dass ExpressRoute immer eine weitere Bereichsbezogene Route zu Microsoft Server-IP-Adressen zuweisen niedrigeren Route Kosten als eine Standardroute Internet bereitstellt.
  
### <a name="design-client-connectivity-configuration"></a>Design Connectivity Clientkonfiguration
<a name="asymmetric"> </a>

![Verwenden von PAC-Dateien mit ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Wenn Sie verwenden ein Proxyserver für Internetwebsites gebunden Datenverkehr und dann müssen Sie alle PAC anpassen oder Client-Konfigurationsdateien, um sicherzustellen, dass Clientcomputern in Ihrem Netzwerk zum Senden von des gewünschten ExpressRoute-Datenverkehrs zu Office 365 ohne Emissionswerte ordnungsgemäß konfiguriert sind Proxy-Server und den verbleibenden Datenverkehr, einschließlich einiger Office 365-Datenverkehr wird an den entsprechenden Proxy gesendet. Lesen Sie unsere Leitfaden zum [Verwalten von Office 365-Endpunkten](https://aka.ms/manageo365endpoints) beispielsweise PAC-Dateien.
  
> [!NOTE]
> Die Endpunkte ändern häufig, so oft wie wöchentlich. Sie sollten nur basierte auf die Dienste und Features, die Ihrer Organisation eingeführt hat, um die Anzahl der Änderungen zu reduzieren, müssen Sie auf dem laufenden nehmen Sie, Änderungen vornehmen. Besonders auf das **Gültigkeitsdatum** in den RSS-Feed, in denen die Änderungen werden angekündigt, und ein Datensatz gespeichert wird der alle in der Vergangenheit ändert, IP-Adressen, die bekannt gegeben werden, möglicherweise nicht angekündigt, oder entfernt werden von Werbung, bis das aktuelle Datum erreicht ist.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Erstellen von Ihrer Bereitstellung und die Testverfahren
<a name="testing"> </a>

Ihr Plan zur Implementierung sollte sowohl testen und Rollback Planung enthalten. Wenn die Implementierung nicht wie erwartet funktioniert, sollten der Plan soll am wenigsten beeinflussen Nummern von Personen, bevor Probleme auftreten. Im folgenden sind einige allgemeinen Prinzipien, die Ihr Plan berücksichtigen sollten.
  
1. Bereitstellen der Netzwerk-Segment und Benutzer Service Onboarding um Unterbrechung zu minimieren.

2. Plan für das Testen von Routen mit Traceroute und TCP aus einem separaten Internet verbundenen Host herstellen.

3. Vorzugsweise, sollte das Testen von Diensten für eingehende und ausgehende eine isolierte Netzwerk mit einem Test Office 365-Mandanten durchgeführt werden.

      - Alternativ kann Testen in einem Produktionsnetzwerk ausgeführt werden, wenn der Kunde Office 365 noch nicht verwenden ist oder befindet sich in der Pilotphase.

      - Alternativ kann testen werden während eines Ausfalls von Produktion, der reserviert für Test wird ausgeführt und Überwachung nur.

      - Alternativ kann testen erfolgen Mobilgeräts Routen für jeden Dienst auf den einzelnen Layer 3-Router-Knoten. Diese Fallbacks sollte nur verwendet werden, wenn keine anderen Tests möglich ist, da fehlender physischen testen Risiko führt.

### <a name="build-your-deployment-procedures"></a>Erstellen Sie Ihre Bereitstellungsverfahren

Die Bereitstellungsverfahren sollte an eine kleine Gruppe von Personen in Phasen vor der Bereitstellung von an eine größere Gruppe von Personen zu Testzwecken zulassen einführen. Im folgenden Code werden verschiedene Möglichkeiten, die Bereitstellung von ExpressRoute Phase.
  
1. Einrichten von ExpressRoute mit Microsoft peering und haben die Route Werbung weitergeleitet an einen einzigen Host nur für Testzwecke bereitgestellt.

2. Kündigen Sie Routen mit dem Netzwerk ExpressRoute mit einem einzelnen Netzwerksegment zunächst an, und erweitern Sie Route Werbung mithilfe eines Netzwerksegments oder einer Region.

3. Wenn Office 365 zum ersten Mal bereitstellen, verwenden Sie das ExpressRoute-Netzwerk-Bereitstellung als Pilot für eine kleine Anzahl von Personen.

4. Wenn Sie Proxy-Server verwenden, können Sie alternativ eine PAC-Testdatei um eine kleine Anzahl von Personen zu ExpressRoute mit testen und Feedback zu leiten, vor dem Hinzufügen weiterer konfigurieren.

Ihr Plan zur Implementierung sollte Listen alle Bereitstellungsverfahren, die ausgeführt werden müssen, oder Befehle, die verwendet werden, um die Netzwerkkonfiguration bereitstellen müssen. Wenn die Netzwerk-Ausfallzeit alle Änderungen empfangene gemacht wird von der schriftliche Bereitstellungsplan im Voraus geschriebenem und Peer sein sollte überprüft. Finden Sie in der Anleitung in der technischen Konfiguration des ExpressRoute.
  
- Aktualisieren Ihre SPF TXT-Einträge sollten Sie die IP-Adressen für alle lokalen Server geändert haben, die weiterhin e-Mail senden.

- Aktualisieren von DNS-Einträge für lokalen Servern sollten Sie die IP-Adressen, um eine neue Konfiguration des NAT aufzunehmen geändert haben.

- Stellen Sie sicher, dass Sie den RSS-feed für Office 365 Endpunkt Benachrichtigungen an alle Konfigurationen routing oder der Proxy verwalten abonniert haben.

Nach Abschluss die Bereitstellung ExpressRoute sollte die Verfahren in den Testplan ausgeführt werden. Ergebnisse für die einzelnen Verfahren müssen angemeldet sein. Sie müssen die Verfahren zum Zurücksetzen auf die ursprüngliche produktionsumgebung in der Ereignisprozedur die Testergebnisse Plan anzugeben, dass die Implementierung nicht erfolgreich war einschließen.
  
### <a name="build-your-test-procedures"></a>Erstellen Sie Ihre Testen von Prozeduren

Die Testverfahren sollte Tests für jede ausgehenden und eingehenden Netzwerkdienst für Office 365, die ExpressRoute verwenden und solche, die nicht enthalten. Die Verfahren sollte enthalten Testen von jeder eindeutigen Netzwerkspeicherort, einschließlich Benutzer, die nicht lokal des Unternehmens-LANS befinden.
  
Einige Beispiele für Testaktivitäten sind die folgenden.
  
1. Pingen Sie auf Ihr Netzwerk Operator Router aus dem lokalen Router.

2. Überprüfen Sie die 500 + Office 365 und CRM Online IP-Adresse ein, Werbung von Ihren lokalen Router empfangen werden.

3. Überprüfen der eingehenden und ausgehenden NAT wird zwischen ExpressRoute und dem internen Netzwerk.

4. Überprüfen, ob die Routen für Ihr NAT-Gerät aus dem Router angekündigt werden.

5. Überprüfen, ob die ExpressRoute Ihrer Ankündigungen entsprechen Präfixe angenommen hat.

      - Verwenden Sie das folgende Cmdlet Peers Werbung zu überprüfen:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Überprüfen Sie Ihre öffentlichen NAT IP Bereich, wenn sie eine bestimmte Teilmenge der einen größeren Wertebereich wie im vorherigen Beispiel ist nicht mit Microsoft über andere ExpressRoute oder öffentliche Internet Netzwerk Netzfrequenz angekündigt wird.

7. ExpressRoute Circuits kombiniert werden, überprüfen, dass beide Sitzungen BGP ausgeführt werden.

8. Richten Sie einen einzelnen Host innerhalb des Ihr NAT-Gerät und verwenden Sie Ping-, Tracert- und Tcpping zum Testen der Konnektivität über die neue Verbindung mit der Host-outlook.office365.com. Alternativ können Sie einem Tool wie Wireshark oder Microsoft Network Monitor 3.4 eines gespiegelten Ports, die einen MSEE, um Sie zu überprüfen sind zur outlook.office365.com zugeordnete IP-Adresse eine Verbindung herstellen können.

9. Testen der Ebene Anwendungsfunktionalität für Exchange Online.

  - Testen von Outlook kann eine Verbindung mit Exchange Online und e-Mail senden/empfangen.

  - Testen von Outlook kann-Onlinemodus verwenden.

  - Smartphone-Konnektivität und senden-empfangen-Funktion zu testen.

10. Testen der Ebene Anwendungsfunktionalität für SharePoint Online

  - OneDrive for Business-Synchronisierungsclient zu testen.

  - Testen von SharePoint Online Web Access.

11. Testen der Ebene Anwendungsfunktionalität für Skype für aufrufende Geschäftsszenarien:

  - Teilnehmen Sie an einer Telefonkonferenz als authentifizierter Benutzer [einladen, die vom Benutzer initiiert].

  - Laden Sie Telefonkonferenz [einladen von MCU gesendete] Benutzer ein.

  - An Konferenz teilnehmen als anonyme Benutzer mithilfe der Skype für Business Web-Anwendung.

  - Teilnehmen an, die aus Ihrer Kabelverbindung PC, IP-Telefon und mobilen Gerät.

  - Aufrufen, um Verbundbenutzer o Anruf auf PSTN-Überprüfung: Anruf abgeschlossen ist, die Anrufqualität ist akzeptabel, Verbindungszeit akzeptabel ist.

  - Überprüfen Sie Anwesenheitsstatus für Kontakte wird für beide Member des Mandanten aktualisiert und verbundene Benutzer.

### <a name="common-problems"></a>Häufige Probleme

Asymmetrische routing ist die am häufigsten verwendeten Implementierung Problem. Es folgen einige allgemeinen Quellen suchen:
  
- Bei Verwendung Routingtopologie einer geöffneten oder flache Netzwerk ohne Quell-NAT vorhanden.

- Verwenden nicht SNAT zum Weiterleiten an eingehende Verbindungen, über das Internet und die ExpressRoute services.

- Testen eingehende Dienste auf dem ExpressRoute in einem Testnetzwerk vor der Bereitstellung im Allgemeinen gibt es nicht.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Bereitstellen von ExpressRoute Konnektivität über das Netzwerk
<a name="testing"> </a>

Phase der bereitstellungs auf einem Segment des Netzwerks jeweils die Konnektivität mit anderen Teilen des Netzwerks mit eines Plans für jedes neue Netzwerksegment Rollback stetig Rollout. Wenn Ihre Bereitstellung mit einer Office 365-Bereitstellung ausgerichtet wird, zuerst an Office 365 Pilotbenutzer bereitstellen, und Erweitern von dort aus.
  
Zuerst für den Test und dann für die Produktion:
  
- Führen Sie die Schritte zur Bereitstellung, um ExpressRoute zu aktivieren.

- Testen Sie Ihre sehen, dass die Netzwerkrouten sind wie erwartet.

- Führen Sie Tests auf jeden Dienst für eingehende und ausgehende.

- Rollback, wenn Sie Probleme erkennen.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Richten Sie eine Testverbindung, um ExpressRoute mit einem Netzwerksegment test

Nun, da Sie die abgeschlossenen Planung auf Papier haben sich Gedanken darüber machen im kleinen Maßstab zu testen. In diesem Test werden Sie eine einzelne ExpressRoute Verbindung mit Microsoft Peering für einen Test Subnetz in Ihrem lokalen Netzwerk einrichten. Sie können konfigurieren Sie eine [Testversion von Office 365-Mandanten](https://go.microsoft.com/fwlink/p/?LinkID=403802) mit Verbindung mit und aus dem Subnetz Test, und schließen alle ausgehenden und eingehenden Dienste, die Sie verwenden werden in der Produktion in das Test-Subnetz. Einrichten von DNS für das Netzwerksegment Test und alle eingehenden und ausgehenden Dienste einrichten. Testplan ausführen, und stellen Sie sicher, dass Sie mit dem routing für jeden Dienst und die Route Ausbreitung vertraut sind.
  
### <a name="execute-the-deployment-and-test-plans"></a>Führen Sie die Bereitstellung und Test-Pläne

Wie Sie die oben beschriebenen Elementen abgeschlossen haben, überprüfen Sie deaktiviert die Bereiche abgeschlossen haben, und stellen Sie sicher, und Ihr Team haben sie vor die Bereitstellung ausführen und Testen von Plänen überprüft.
  
- Liste der ausgehenden und eingehenden Dienste, die an die netzwerkänderung beteiligt sind.

- Globale-Architektur Netzwerkdiagramm mit Internet Ausgang und ExpressRoute Meet-me Speicherorte.

- Routing Netzplandiagramm demonstrieren die unterschiedlichen Netzwerkpfade für jeden Dienst bereitgestellt verwendet.

- Planen einer Bereitstellung, Schritte aus, um die Änderungen und Rollback implementieren, falls erforderlich.

- Ein Plan zum Testen von für jeden Office 365 und Netzwerk-Dienst zu testen.

- Papier Validierung der Produktion Routen für eingehende und ausgehende Services abgeschlossen.

- Einen abgeschlossenen Test über einen Test Netzwerksegment einschließlich Testen der Verfügbarkeit.

Auswählen einer Ausfallzeit, die lange genug sind, um über den gesamten Bereitstellungsplan und den Testplan ausgeführt wird, verfügt über einige Zeit für die Problembehandlung verfügbar und die Uhrzeit für die Einführung der zurück, falls erforderlich.
  
> [!CAUTION]
> Aufgrund der komplexen Natur von routing über das Internet und die ExpressRoute empfiehlt es sich, dass dieses Fenster zum Verarbeiten von komplexen routing Problembehandlung zusätzliche Pufferzeit hinzugefügt wird.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurieren von QoS für Skype Business Online

QoS ist erforderlich, VoIP und Meeting Vorteile für Skype für Business Online zu erhalten. Sie können QoS konfigurieren, nachdem Sie sichergestellt haben, dass die Netzwerkschnittstelle ExpressRoute Ihre Office 365-Dienst Zugriff nicht blockiert. Konfiguration für QoS wird im Artikel [ExpressRoute und QoS in Skype für Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) beschrieben.
  
## <a name="troubleshooting-your-implementation"></a>Problembehandlung bei der Implementierung
<a name="troubleshooting"> </a>

Die zentrale Position zum Suchen wird an die Schritte in diesem Implementierungshandbuch wurden alle, die in Ihrer Implementierung planen? Gehen Sie zurück, und führen Sie weitere kleines Netzwerk nach Möglichkeit zum Replizieren des Fehlers und Debuggen sie es testen.
  
Identifizieren Sie die eingehende oder ausgehende Dienste während der Tests ist fehlgeschlagen. Rufen Sie insbesondere die IP-Adressen und Subnetze für die einzelnen für Dienste, die nicht erfolgreich. Fahren Sie fort und im Netzwerktopologiediagramm auf Papier durchlaufen und das routing zu überprüfen. Überprüfen Sie, insbesondere, in dem das ExpressRoute routing angekündigt ist, testen Sie, dass die Weiterleitung während des Ausfalls möglichst mit Spuren.
  
PSPing mit einer Netzwerk-Trace auf jeden Endpunkt Kunden ausgeführt werden, und Auswerten von Quell- und Ziel-IP-Adressen, um zu überprüfen, dass sie erwartungsgemäß sind. Führen Sie Telnet an beliebige e-Mail-Hosts, die Sie an Port 25 verfügbar machen, und stellen Sie sicher, dass SNAT die ursprüngliche IP-Quelladresse ausgeblendet wird, wenn dies erwartet wird.
  
Denken Sie daran, die beim Bereitstellen von Office 365 mit einer ExpressRoute-Verbindung, die Sie benötigen, um sicherzustellen, dass sowohl die Netzwerkkonfiguration für ExpressRoute optimal entwickelt wurde, und Sie haben auch die anderen Komponenten in Ihrem Netzwerk wie Clientcomputer optimiert. Zusätzlich zur Verwendung von diesem Planungshandbuch die Schritte behoben werden, die verpassten, haben wir auch einen [Plan für Office 365 Behandlung von Leistungsproblemen](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) geschrieben.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Verwenden von BGP-Communitys in ExpressRoute für Office 365-Szenarien (Vorschau)](bgp-communities-in-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
