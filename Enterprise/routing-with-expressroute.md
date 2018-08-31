---
title: Routing mit ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Um routing Datenverkehr zu Office 365 mit Azure ExpressRoute ordnungsgemäß zu verstehen, benötigen Sie Kunden die Überzeugung der Core ExpressRoute Routinganforderungen und ExpressRoute Circuits und routing-Domänen. Diese gestalten Sie die Grundlagen für die Verwendung von ExpressRoute, die Office 365-Kunden verwenden werden.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540768"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing mit ExpressRoute für Office 365

Um routing Datenverkehr zu Office 365 mit Azure ExpressRoute ordnungsgemäß zu verstehen, benötigen Sie Kunden die Überzeugung der Kern [-Routinganforderungen ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) und [ExpressRoute Schaltkreise und routing-Domänen](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Diese gestalten Sie die Grundlagen für die Verwendung von ExpressRoute, die Office 365-Kunden verwenden werden.
  
Einige wichtige Elemente in den oben aufgeführten Artikeln, die Sie benötigen, zu verstehen sind:
  
- ExpressRoute Circuits werden nicht an bestimmten physischen Infrastruktur zugeordnet, aber eine logische Verbindung von Microsoft und einen Peers Anbieter in Ihrem Auftrag an einem einzelnen Standort Peers vorgenommen werden.

- Es ist eine 1:1-Zuordnung zwischen einer ExpressRoute Netzfrequenz und eine Customer s-Taste.

- Jede Verbindung kann bis zu 3 unabhängige Peers Beziehungen (Azure öffentliche peering, Azure Private peering und Microsoft peering); unterstützen. Office 365 erfordert Microsoft peering.

- Jede Verbindung verfügt über eine feste Bandbreite, die von allen Peers Beziehungen gemeinsam genutzt wird.

- Alle öffentlichen IPv4-Adressen und öffentliche als Zahlen, die verwendet werden für die ExpressRoute Netzfrequenz muss als Besitzer wird Sie bestätigt, oder ausschließlich, die Sie durch den Besitzer des Adressbereichs zugewiesen.

- Die virtual Circuits ExpressRoute sind redundant Global und standard BGP routing Methoden vor. Deshalb ist es zwei physische Stromkreisen pro Ausgang an Ihren Anbieter in einer Aktiv/Aktiv-Konfiguration wird empfohlen.

Finden Sie auf der [Seite häufig gestellte Fragen zu](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) für Weitere Informationen zu Diensten unterstützt, Kosten und Konfigurationsdetails. Informationen finden Sie die [ExpressRoute Speicherorte Artikel](https://azure.microsoft.com/documentation/articles/expressroute-locations/) in der Liste der Konnektivität Anbieter anbieten Peers Support von Microsoft. Wir haben auch eine 10-Teil [Azure ExpressRoute für Office 365-Schulung](https://channel9.msdn.com/series/aer) Reihe auf Channel 9, unterstützen die Konzepte mehr sorgfältig erläutern aufgezeichnet.
  
## <a name="ensuring-route-symmetry"></a>Sicherstellen, dass Route Symmetrie

Die Office 365-Front-End-Server werden im Internet und die ExpressRoute zugegriffen. Diese Server werden lieber über ExpressRoute Circuits weitergeleitet werden soll, wenn beide verfügbar sind. Aus diesem Grund besteht die Möglichkeit der Route Asymmetrie Wenn Datenverkehr aus dem Netzwerk bevorzugt über den Stromkreisen Internet weitergeleitet. Asymmetrische Routen sind ein Problem, da Geräte, die Überprüfung ausführen return Datenverkehr abgewehrt werden können, die auf einen anderen Pfad als die ausgehenden Pakete gefolgt folgt.
  
Unabhängig davon, ob Sie eine Verbindung zu Office 365 über das Internet oder ExpressRoute initiieren muss die Quelle eine öffentlich routingfähige Adresse sein. Mit vielen Kunden direkt mit Microsoft peering ist nicht mit privaten Adressen wobei Duplizierung zwischen Kunden möglich ist möglich.
  
Im folgenden werden die Szenarien, in dem Kommunikation von Office 365 zu Ihrem lokalen Netzwerk ausgelöst werden. Zur Vereinfachung des netzwerkdesigns wird empfohlen, diese über den Pfad des Internet-routing.
  
- ADFS während der Überprüfung des Kennworts für die Anmeldung.

- [Exchange Server-hybridbereitstellungen](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Mail-von Exchange Online-Mandanten mit einem lokalen Host.

- SharePoint Online-Mail senden an einen lokalen Host aus SharePoint Online.

- [SharePoint-hybridsuche Verbund](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint Hybrid BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype für hybride Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) und/oder [Skype für den Verbund Business](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype für Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Für Microsoft wieder auf Ihr Netzwerk für diese bidirektionalen Datenverkehr fließt weitergeleitet müssen die BGP Routen zu Ihrem lokalen Geräten mit Microsoft gemeinsam genutzt werden.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Entscheiden, welche Anwendungen und Features über ExpressRoute weiterleiten

Wenn Sie eine Microsoft Peers Domäne für das routing von Peers Beziehung konfigurieren und für den entsprechenden Zugriff zugelassen werden, müssen Sie alle PaaS und SaaS Services über ExpressRoute finden Sie unter sein. Ist ausgelegt für ExpressRoute Office 365-Dienste können mit [BGP Communitys](https://aka.ms/bgpexpressroute365) oder [Routefilter](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)verwaltet werden.
  
Andere Anwendungen wie etwa Office 365-Video, handelt es sich um ein Office 365-Anwendung. jedoch Video für Office 365 drei Komponenten, die Portal, streaming-Dienst und der Content Delivery Networks besteht. Das Portal befindet sich in SharePoint Online und das streaming Service angesiedelt Azure Media-Dienste, und der Content Delivery Networks befindet sich innerhalb der Azure CDN. In der folgenden Tabelle werden diese Komponenten beschrieben.
  
| |
|**Komponente**|**Zugrunde liegende Anwendung**|**Enthalten in SharePoint Online BGP Community?**|**Verwendung**|
|:-----|:-----|:-----|:-----|
|Office 365-Video-portal  <br/> |SharePoint Online  <br/> |Ja  <br/> |Konfiguration, hochladen  <br/> |
|Office 365-Video-streaming-Dienst  <br/> |Azure Media Services  <br/> |Nein  <br/> |Streaming-Dienst verwendet den Fall, dass das Video aus dem CDN nicht verfügbar ist  <br/> |
|Office 365 Video Content Delivery Networks  <br/> |Azure CDN  <br/> |Nein  <br/> |Primäre Datenquelle Download/Videostreaming. [Erfahren Sie mehr über Office 365-video-Netzwerke](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

Der Office 365-Features, die mit Microsoft peering verfügbar sind sind in [Office 365-Endpunkten Artikel](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) mit Anwendungstyp und den FQDN aufgeführt. Der Grund für die Verwendung des FQDN in den Tabellen ist mit Kunden zur Verwaltung des Datenverkehrs mit PAC-Dateien oder andere Proxykonfigurationen finden Sie unter unsere Leitfaden zum [Verwalten von Office 365-Endpunkten](https://aka.ms/manageo365endpoints) beispielsweise PAC Dateien ermöglichen.
  
In manchen Fällen haben wir eine Platzhalterdomäne verwendet, in dem eine oder mehrere Sub-FQDNs anders als die höhere Ebene Platzhalterdomäne bekannt gegeben werden. Dies geschieht in der Regel auf, wenn der Platzhalter eine lange Liste von Servern, der alle bekannt ExpressRoute und das Internet darstellt, gegeben werden während Sie mit dem Internet oder umgekehrt werden nur eine kleine Untergruppe der Ziele angekündigt. Finden Sie in den Tabellen zu verstehen, wo die Unterschiede sind unten.
  
Diese Tabelle zeigt den Platzhalter FQDNs, die bekannt gegeben werden mit dem Internet und die Azure ExpressRoute zusammen mit der Sub-FQDNs, die nur mit dem Internet bekannt gegeben werden.

|**Platzhalterdomäne angekündigt ExpressRoute und Internet circuits**|**Sub-FQDN angekündigt, um nur Internet circuits**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.Email.microsoftonline.com  <br/> Portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> CDN.ODC.officeapps.Live.com  <br/> ols.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> ocws.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

In der Regel PAC-Dateien sind vorgesehen für Netzwerk Anfragen an ExpressRoute direkt an der Netzfrequenz-Endpunkten und alle anderen Netzwerk Anforderungen an den Proxy angekündigt. Wenn Sie eine PAC-Datei wie folgt konfigurieren, erstellen Sie Ihre PAC-Datei in der folgenden Reihenfolge:
  
1. Enthalten Sie die Sub-FQDNs aus zwei Spalte in der obigen Tabelle am oberen Rand der PAC-Datei den Datenverkehr zu den Proxy zu senden. Wir haben eine PAC-Beispieldatei für die Verwendung in unserem Artikel zum [Verwalten von Office 365-Endpunkten](https://aka.ms/manageexpressroute365)erstellt.

2. Alle FQDNs markiert angekündigt, ExpressRoute in [diesem Artikel](https://aka.ms/o365endpoints) unterhalb des ersten Abschnitts, senden den Datenverkehr direkt an Ihre ExpressRoute Netzfrequenz enthalten.

3. Enthalten Sie andere Netzwerkendpunkte oder Regeln diese zwei Einträge, senden den Datenverkehr zu den Proxy.

Diese Tabelle zeigt die Platzhalterdomänen, die bekannt gegeben werden Internet Circuits zu Internet Circuits nur zusammen mit Sub-FQDNs auf Azure ExpressRoute bekannt gegeben werden. Für die PAC-Datei über die FQDNs in zwei-Spalte in der unter Tabelle als, ExpressRoute in den Link auf die verwiesen wird, d. h., sie in der zweiten Gruppe von Einträgen in der Datei eingeschlossen werden würde angekündigt aufgeführt sind.

|**Nur Internet Circuits angekündigt Platzhalter-Domäne**|**Sub-FQDN angekündigt ExpressRoute und Internet circuits**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. office.net  <br/> |Agent.Office.NET  <br/> |
|\*. office365.com  <br/> |Outlook.Office365.com  <br/> SMTP.Office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> AutoErmittlung -\<Mandanten\>. outlook.com  <br/> |
|\*. Windows  <br/> |Login.Windows.NET  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing Office 365-Datenverkehr über das Internet und ExpressRoute

Wenn Sie an der Office 365 weiterleiten müssen Anwendung Ihrer Wahl eine Anzahl von wichtigen Faktoren bestimmen.
  
1. Wie viel Bandbreite erfordert die Anwendung. Vorhandene Usage Sampling ist die einzige zuverlässige Methode zur Bestimmung dies in Ihrer Organisation.

2. Welche den Netzwerkdatenverkehr gewünschte Ausgang Speicherorte lassen Sie Ihr Netzwerk aus. Planen Sie auch die Netzwerklatenz für eine Verbindung zu Office 365 zu minimieren, da dies die Leistung auswirkt. Da Skype für Unternehmen in Echtzeit Sprach- und Videofunktionen verwendet, ist es besonders anfällig für unzureichende Netzwerklatenz.

3. Wenn Sie alle oder einen Teil Ihrer Netzwerkadressen ExpressRoute nutzen möchten.

4. Welche Standorte bietet der gewählten Netzwerkanbieter ExpressRoute aus.

Nachdem Sie die Antworten auf diese Fragen ermittelt haben, können Sie ein ExpressRoute Netzfrequenz bereitstellen, die den Bedürfnissen Bandbreite und Speicherort entspricht. Weitere Hilfe zur netzwerkplanung finden Sie in der [Office 365-Netzwerk tuning Guide](https://aka.ms/tune) und der [Fallstudie auf wie Microsoft steuert leistungsplanung Netzwerk](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>In Beispiel 1: Einzelnen geografischen Standort
  
In diesem Beispiel wird ein Szenario für einen fiktiven Unternehmens Trey Research aufgerufen, der über einen einzelnen geografischen Standort verfügt.
  
Mitarbeiter bei Trey Research dürfen nur eine Verbindung mit der Dienste und Websites im Internet, das dem Sicherheitsdienst explizit auf die zwei ausgehenden Proxys ermöglicht, die zwischen dem Unternehmensnetzwerk und ihren Internetdienstanbieter befinden.
  
Trey Research plant, Azure ExpressRoute für Office 365 verwenden und erkennt, dass einige Datenverkehr wie Datenverkehr für die Inhaltsübermittlung über die ExpressRoute für Office 365-Verbindung weitergeleitet werden kann. Da alle Routen für die Proxy-Geräte bereits standardmäßig Datenverkehr, werden diese Anforderungen weiterhin wie gewohnt. Nach Trey Research, dass sie die Azure ExpressRoute Routinganforderungen erfüllen können feststellt, fahren sie routing, und verknüpfen die neue ExpressRoute-Leitung mit eines virtuellen Netzwerks konfigurieren, erstellen eine Verbindung fort. Nachdem die grundlegende Konfiguration von Azure ExpressRoute vorhanden ist, verwendet Trey Research die [#2 PAC-Datei, die wir veröffentlichen](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) für die Weiterleitung Verkehr mit bestimmten Kundendaten über die direkte ExpressRoute für Office 365-Verbindungen.
  
Wie in der folgenden Abbildung gezeigt, kann Trey Research die Anforderung zu Office 365 über das Internet und eine Teilmenge des Datenverkehrs über ExpressRoute mit einer Kombination von Proxy-konfigurationsänderungen routing und ausgehenden Datenverkehr zu erfüllen.
  
1. Verwenden die [#2 PAC-Datei, die wir veröffentlichen](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) für die Weiterleitung von Verkehr über eine separate Internet Austritt für Azure ExpressRoute für Office 365.

2. Clients werden mit einer Standardroute zu Trey Research des Proxys konfiguriert.

In diesem Beispielszenario verwendet Trey Research ein ausgehende Proxygerät. Kunden, die keine Azure ExpressRoute für Office 365 verwenden möchten auf ähnliche Weise, verwenden Sie dieses Verfahren für die Weiterleitung Verkehr basierend auf den Kosten für das Prüfen von Datenverkehr für bekannte große Menge Endpunkte.
  
Dem höchsten zu erwartenden FQDNs für Exchange Online, SharePoint Online und Skype für Business Online sind folgende:
  
![ExpressRoute Edge Kundennetzwerk](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.Office365.com, outlook.office.com

- \<Name des Mandanten\>. sharepoint.com, \<Mandantennamen\>-my.sharepoint.com, \<Mandantennamen\>-\<app\>. sharepoint.com

- \*. Lync.com herzustellen, zusammen mit der IP-Adressbereiche für nicht-TCP-Datenverkehr

- \*Broadcast.officeapps.Live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* Word-edit.officeapps.live.com, \*Word-view.officeapps.live.com, office.live.com

Weitere Informationen zum [Bereitstellen und Verwalten von Proxyeinstellungen in Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) und [sicherstellen, dass Office 365 durch Ihre Proxy gedrosselt nicht zur Verfügung](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Durch eine einzelne ExpressRoute ist es keine hoher Verfügbarkeit für Trey Research. In der Ereignisprozedur Trey redundante Edge-Geräte, die die Konnektivität ExpressRoute bedienen ausfallen, ist keine zusätzliche ExpressRoute Netzfrequenz zum Failover auf. Dies bewirkt, dass Trey Research ein Problem beim Ausführen eines Failovers für mit dem Internet die manuelle Neukonfiguration erfordern und in einigen Fällen neue IP-Adressen. Wenn hohen Verfügbarkeit hinzufügen Trey möchte, ist die einfachste Lösung auf zusätzliche ExpressRoute Stromkreise für jeden Standort hinzufügen und Konfigurieren von Stromkreise in einer Aktiv/Aktiv-Weise.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing ExpressRoute für Office 365 mit mehreren Standorten

Das letzte Szenario, routing von Office 365-Datenverkehr über ExpressRoute bildet die Grundlage für noch komplexere routing-Architektur. Unabhängig von der Anzahl der Standorte, Anzahl der Kontinente, wo diese Standorte vorhanden sind, Anzahl der ExpressRoute Circuits usw., werden für einige Datenverkehr an das Internet und einige Datenverkehr über ExpressRoute erforderlich sein.
  
Zusätzlichen Fragen, die für Kunden mit mehreren Standorten in mehreren Ländern beantwortet werden müssen, gehören:
  
1. Sie benötigen ein ExpressRoute Netzfrequenz an jedem Standort? Wenn Sie Skype für Business Online verwenden oder mit Wartezeit Vertraulichkeit für SharePoint Online oder Exchange Online befürchten, eine redundante aktiv/aktiv ExpressRoute Stromkreise an jedem Standort empfohlen. Finden Sie unter der Skype für Business Media Quality und Network Connectivity-Handbuch für weitere Details.

2. Ist ein ExpressRoute Netzfrequenz in einer bestimmten Region nicht verfügbar, sollte wie Office 365 bestimmt Datenverkehr werden weitergeleitet?

3. Was ist die bevorzugte Methode zur Konsolidierung von Datenverkehr im Fall von Netzwerken viele kleine Positionen?

Jede dieser stellt eine eindeutige Herausforderung, die zum Auswerten von Ihrem eigenen Netzwerk als auch der von Microsoft verfügbaren Supportoptionen erforderlich sind.

|**Überlegung**|**Netzwerkkomponenten für ausgewertet werden soll**|
|:-----|:-----|
|Stromkreise in mehr als einem Standort  <br/> |Es wird empfohlen, mindestens zwei Stromkreisen in einer Aktiv/Aktiv-Weise konfiguriert.  <br/> Kosten, Latenz und Bandbreite Anforderungen müssen verglichen werden.  <br/> Verwenden Sie zum Verwalten von routing mit mehreren Circuits BGP Route Kosten-, PAC-Dateien und NAT.  <br/> |
|Routing von Standorte ohne eine ExpressRoute-Verbindung  <br/> |Es wird empfohlen, sollten Sie den Ausgangs- und DNS-Auflösung als ungefähr die Person Einleiten der Anforderung für Office 365.  <br/> DNS-Weiterleitung kann verwendet werden, um Zweigstellen ermitteln können, den entsprechenden Endpunkt zu ermöglichen.  <br/> Clients in den Zweigstellen benötigen eine Route verfügbar, die Zugriff auf die Netzfrequenz ExpressRoute bereitstellt.  <br/> |
|Büro-Konsolidierung  <br/> |Verwendung von verfügbaren Bandbreite und Daten sollte sorgfältig verglichen werden.  <br/> |

> [!NOTE]
> Microsoft wird über das Internet ExpressRoute bevorzugen, wenn die Route unabhängig vom physischen Standort zur Verfügung steht.
  
Jede dieser Aspekte muss für jede eindeutige Netzwerk berücksichtigt werden. Es folgt ein Beispiel.
  
### <a name="example-2-multi-geographic-locations"></a>Beispiel 2: Mit mehreren geografischen Standorten
  
In diesem Beispiel wird ein Szenario für einen fiktiven Unternehmens Humongous Insurance aufgerufen, der mehrere geografische Standorte hinweg hat.
  
Humongous Insurance ist mit Büros auf der ganzen Welt geografisch verteilte. Implementiert werden sollen Azure ExpressRoute für Office 365, den Großteil ihrer Office 365-Datenverkehr auf direkte Netzwerkverbindungen zu speichern. Humongous Insurance hat auch zwei zusätzliche Kontinente Büros. Weiterleiten an eine oder beide der primären Anlagen eine ExpressRoute Verbindung verwenden müssen die Mitarbeiter in remote-Standort, auf dem ExpressRoute nicht möglich ist.
  
Das Prinzip ist so schnell wie möglich abzurufenden bestimmt ist Office 365-Datenverkehr an einem Microsoft-Rechenzentrum. In diesem Beispiel müssen Humongous Insurance entscheiden, ob ihre Zweigstellen weitergeleitet werden, über das Internet abzurufenden in einem Microsoft-Rechenzentrum über Verbindung so schnell wie möglich ist oder über ein internes Netzwerk an einen Microsoft Abrufen ihrer Zweigstellen weitergeleitet werden Rechenzentrum über eine Verbindung ExpressRoute so schnell wie möglich.
  
Microsoft Rechenzentren, Netzwerke und Anwendungsarchitektur dienen Global unterschiedliche Communications und effizient wie möglich Dienstleistungen bereit. Dies ist einer der größten Netzwerke in der ganzen Welt. Anfragen für Office 365, die für Kundennetzwerke länger als notwendig verbleibt wird nicht diese Architektur nutzen können.
  
In Humongous Insurance des Fall sollten sie je nach den Anwendungen fortfahren, die er über ExpressRoute verwenden möchten. Wenn sie einen Skype für Unternehmen Online Kunden, oder planen, ExpressRoute-Konnektivität zu nutzen, beim Verbinden mit externen Skype für Onlinekonferenzen Business, den Entwurf der Skype für Business Online Medienqualität und Netzwerk empfohlen, beispielsweise Connectivity-Handbuch ist eine zusätzliche ExpressRoute Netzfrequenz für die dritte Position bereit. Dies kann aus Sicht der Netzwerke teurer sein. Das routing jedoch Anfragen aus einem Kontinent in eine andere vor der Bereitstellung in einem Microsoft-Rechenzentrum eine schlechte oder nicht mehr Erfahrung bei Skype für Business onlinebesprechungen und Kommunikation führen kann.
  
Wenn Humongous Insurance ist nicht oder nicht Skype für Business Online keinerlei nutzen möchten, verursachen Office 365 bestimmt den Netzwerkverkehr wieder auf einen Kontinent mit einer Verbindung möglicherweise ExpressRoute routing machbare gegenüber unnötige Wartezeit oder TCP eine Überlastung. In beiden Fällen nutzt routing Internet Ziel zugeordneter Datenverkehr mit dem Internet am lokalen Standort empfohlen wird, die die Inhaltsübermittlung die Office 365 nutzen.
  
![ExpressRoute mit mehreren Geografie](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Wenn Humongous Insurance ihrer Strategie mit mehreren Geografie plant, sind eine Reihe von Punkten berücksichtigen, um die Größe der Netzfrequenz, weniger Stromkreise, Failover und so weiter.
  
Mit ExpressRoute in einen einzelnen Standort mit mehreren Bereichen einsetzen, um der Netzfrequenz, Humongous Insurance möchte sicherstellen, dass Verbindungen mit Office 365 vom remote-Standort sind in der Office 365-Rechenzentrum am nächsten gelegenen Unternehmenszentrale gesendet und werden empfangen die Hauptsitz. Zu diesem Zweck implementiert Humongous Insurance DNS-Weiterleitung zur Verringerung der Anzahl von Roundtrips und DNS-Lookups erforderlich, um die entsprechende Verbindung mit Office 365-Umgebung am nächsten Austritt zentrale Internet herstellen. Dadurch wird den Client Auflösen von einem lokalen Front-End-Server und stellt sicher, dass der Front-End-Servers, den die Person, die Verbindung mit in der Nähe der zentrale befindet, in dem mit Microsoft Humongous Insurance peering ist. Sie können auch [Eine bedingte Weiterleitung für einen Domänennamen](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx)zuweisen informieren.
  
In diesem Szenario würden Datenverkehr vom remote-Standort beheben die Office 365-Front-End-Infrastruktur in Nordamerika und nutzen Office 365 Verbindung mit der Back-End-Servern entsprechend der Architektur der Office 365-Anwendung. Beispielsweise Exchange Online würde beendet die Verbindung in Nordamerika und diesen Front-End-Servern würde Herstellen einer Verbindung mit dem Back-End-Postfachserver unabhängig von dessen Speicherort der Mandanten befand. Alle Dienste werden weit verteilten vorderer Klappe Dienst Unicast und Anycast Ziele besteht aus.
  
Weist Humongous Insurance großen Zweigstellen in mehrere Kontinente, mindestens zwei aktiv/aktiv-Stromkreisen pro Region, um die Senkung der Wartezeit für vertrauliche Anwendungen wie Skype für Business Online empfohlen. Wenn alle Niederlassungen befinden sich in einer einzelnen Kontinent oder Zusammenarbeit in Echtzeit ist nicht verwenden, ist eine konsolidierte oder verteilte Ausgang, zeigen Sie eine spezifische Kunden Entscheidung. Wenn mehrere Circuits verfügbar sind, BGP routing Failover stellen Sie sicher jeder einzelnen Netzfrequenz nicht mehr verfügbar sein soll.
  
Erfahren Sie mehr über die Beispiel- [routing-Konfigurationen](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) und [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Selektive routing mit ExpressRoute

Selektive routing mit ExpressRoute möglicherweise für eine Vielzahl von Gründen testen, benötigt Rollout ExpressRoute auf eine Teilmenge der Benutzer. Es gibt verschiedene Tools, mit denen Kunden selektiv Office 365-Netzwerk-Datenverkehr über ExpressRoute verwendet:
  
1. **Filtern von Route/Trennung** - BGP-Routen zu Office 365 über ExpressRoute auf eine Teilmenge der Subnetze oder Router zulassen. Damit wird selektiv durch Kunden eines Netzwerksegments oder physischen Standort. Dies ist häufig gestaffelte Einführung von ExpressRoute für Office 365 verwendet und auf Ihren Geräten BGP konfiguriert ist.

2. **PAC Dateien/URLs** - Umleiten von Office 365 bestimmt den Netzwerkverkehr für bestimmte FQDNs auf einen bestimmten Pfad weitergeleitet. Damit wird selektiv Clientcomputer durch die [Bereitstellung der PAC-Datei](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)identifiziert.

3. **Filtern von Route** - [Routefilter](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) bieten eine Möglichkeit, eine Teilmenge der unterstützten Dienste über Microsoft peering nutzen.

4. **BGP Communitys** - Filterung basierend auf [BGP gemeinschaftlichen Tags](https://aka.ms/bgpexpressroute365) ermöglicht Kunden, die ermitteln, welche Office 365-Anwendungen ExpressRoute durchlaufen werden und dem Internet durchlaufen wird.

Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität zu Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Diensten](managing-expressroute-for-connectivity.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Implementieren von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Medienqualität und Konnektivität Leistung des Netzwerks in Skype für Unternehmen Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihr Netzwerk für Skype für Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute und QoS in Skype für Unternehmen Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Verwenden von BGP Communitys in ExpressRoute für Office 365-Szenarien](bgp-communities-in-expressroute.md)
  
[Office 365 Performance tuning mit Baselines und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Leistungsbezogene Problembehandlung Plan für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 Netzwerk- und Optimieren der Leistung](network-planning-and-performance.md)
