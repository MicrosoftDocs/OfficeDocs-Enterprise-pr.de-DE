---
title: Routing mit ExpressRoute für Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/14/2017
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
description: Um das Routing von Datenverkehr zu Office 365 mithilfe von Azure Express Route richtig zu verstehen, benötigen Sie ein festes Verständnis der wichtigsten Express Route-Routing Anforderungen und der Express Route-Schaltungen und-Routingdomänen. Diese legen die Grundlagen für die Verwendung von Express Route, auf die sich Office 365-Kunden verlassen.
ms.openlocfilehash: 83c3801e7886bf44500f1dc0b185782e2a7f3bc1
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957716"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing mit ExpressRoute für Office 365

Um das Routing von Datenverkehr zu Office 365 mithilfe von Azure Express Route richtig zu verstehen, benötigen Sie ein festes Verständnis der wichtigsten [Express Route-Routing Anforderungen](https://azure.microsoft.com/documentation/articles/expressroute-routing/) und der [Express Route-Schaltungen und-Routingdomänen](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Diese legen die Grundlagen für die Verwendung von Express Route, auf die sich Office 365-Kunden verlassen.
  
Zu den wichtigsten Elementen in den obigen Artikeln, die Sie verstehen müssen, gehört Folgendes:
  
- Express Route-Schaltungen werden keiner bestimmten physischen Infrastruktur zugeordnet, sondern sind eine logische Verbindung, die von Microsoft und einem Peering-Anbieter in Ihrem Namen an einem einzigen Peering-Standort vorgenommen wurde.

- Es gibt eine 1:1-Zuordnung zwischen einer Express Route-Schaltung und einem Kunden-s-Schlüssel.

- Jede Schaltung kann bis zu 3 unabhängige Peering-Beziehungen (Azure Public Peering, Azure private Peering und Microsoft Peering); Office 365 erfordert Microsoft-Peering.

- Jede Schaltung hat eine feste Bandbreite, die für alle Peering-Beziehungen freigegeben ist.

- Alle öffentlichen IPv4-Adressen und öffentlichen als Nummern, die für die Express Route-Schaltung verwendet werden, müssen als im Besitz von Ihnen oder ausschließlich Ihnen vom Besitzer des Adressbereichs zugewiesen validiert werden.

- Die virtuellen Express Route-Schaltungen sind Global redundant und folgen standardmäßigen BGP-Routingmethoden. Aus diesem Grund empfehlen wir zwei physische Schaltungen pro Ausstieg für Ihren Anbieter in einer aktiv/aktiv-Konfiguration.

Weitere Informationen zu den unterstützten Diensten, Kosten und Konfigurationsdetails finden Sie auf der [FAQ-Seite](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) . Informationen zur Liste der Verbindungsanbieter, die Microsoft-Peering-Support bieten, finden Sie im [Artikel Express Route Locations](https://azure.microsoft.com/documentation/articles/expressroute-locations/) . Außerdem haben wir eine 10-teilige [Azure Express Route für Office 365-Schulungs](https://channel9.msdn.com/series/aer) Reihe auf Kanal 9 aufgezeichnet, um die Konzepte genauer zu erläutern.
  
## <a name="ensuring-route-symmetry"></a>Sicherstellen der Routen Symmetrie

Auf die Office 365-Front-End-Server kann sowohl über das Internet als auch über Express Route zugegriffen werden. Diese Server ziehen es vor, über Express Route-Schaltungen zurückzukehren, wenn beide verfügbar sind. Aus diesem Grund besteht die Möglichkeit einer Routen Asymmetrie, wenn der Datenverkehr aus Ihrem Netzwerk eine Weiterleitung über Ihre Internet Schaltkreise vorzieht. Asymmetrische Routen stellen ein Problem dar, da Geräte, die eine statusbehaftete Paketprüfung durchführen, Datenverkehr blockieren können, der einem anderen Pfad als den folgenden ausgehenden Paketen folgt.
  
Unabhängig davon, ob Sie eine Verbindung mit Office 365 über das Internet oder Express Route initiieren, muss es sich bei der Quelle um eine öffentlich routingfähige Adresse handeln. Da viele Kunden sich direkt mit Microsoft unterhalten, sind private Adressen, in denen eine Duplizierung zwischen Kunden möglich ist, nicht möglich.
  
In den folgenden Szenarien wird die Kommunikation von Office 365 zu Ihrem lokalen Netzwerk initiiert. Um Ihr Netzwerk Design zu vereinfachen, sollten Sie diese über den Internet Pfad weiterleiten.
  
- SMTP-Dienste wie e-Mail von einem Exchange Online-Mandanten zu einem lokalen Host oder eine SharePoint Online-e-Mail, die von SharePoint Online an einen lokalen Host gesendet werden. Das SMTP-Protokoll wird im Microsoft-Netzwerk breiter verwendet als die für Express Route-Schaltungen freigegebenen Routen Präfixe und lokale SMTP-Server über Express Route führen zu Fehlern bei diesen anderen Diensten.

- ADFS während der Kennwortüberprüfung für die Anmeldung.

- [Exchange Server-Hybrid Bereitstellungen](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- [SharePoint-Verbund Hybrid Suche](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint-Hybrid-BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype for Business-Hybrid](https://technet.microsoft.com/en-us/library/jj205403.aspx) -und/oder [Skype for Business-Verbund](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype for Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Damit Microsoft für diesen bidirektionalen Datenverkehr in Ihr Netzwerk zurückgeleitet wird, müssen die BGP-Routen zu Ihren lokalen Geräten für Microsoft freigegeben werden. Wenn Sie Routen Präfixe an Microsoft über Express Route ankündigen, sollten Sie die folgenden bewährten Methoden befolgen:

1) Werben Sie nicht das gleiche öffentliche IP-Adress-Routenpräfix für das öffentliche Internet und über Express Route. Es wird dringend empfohlen, dass die IP-BGP-Routenpräfix-Ankündigungen an Microsoft über Express Route aus einem Programm stammt, das nicht im Internet angezeigt wird. Wenn dies aufgrund des verfügbaren IP-Adressraums nicht möglich ist, müssen Sie sicherstellen, dass Sie einen spezifischeren Bereich über Express Route als alle Internet Schaltkreise werben.

2) Verwenden Sie separate NAT-IP-Pools pro Express Route-Schaltung, und trennen Sie diese von den Internet Schaltkreisen.

3) Beachten Sie, dass alle für Microsoft angekündigten Routen den Netzwerkdatenverkehr von einem beliebigen Server im Microsoft-Netzwerk anziehen, nicht nur für die Routen, die über Express Route für Ihr Netzwerk angekündigt werden. Werben Sie nur Routen zu Servern, auf denen Routingszenarien definiert und von Ihrem Team verstanden werden. Werben separater IP-Adress-Routen Präfixe für mehrere Express Route-Schaltungen in Ihrem Netzwerk. 
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Entscheiden, welche Anwendungen und Features über Express Route werden sollen

Wenn Sie eine Peering-Beziehung mithilfe der Microsoft-Peering-Routingdomäne konfigurieren und für den entsprechenden Zugriff genehmigt werden, können Sie alle PaaS-und SaaS-Dienste über Express Route. Die für Express Route entworfenen Office 365-Dienste können mit [BGP-Communities](https://aka.ms/bgpexpressroute365) oder [Routenfiltern](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)verwaltet werden.
  
Andere Anwendungen wie Office 365 Video, ist eine Office 365-Anwendung; Office 365-Videos bestehen jedoch aus drei verschiedenen Komponenten, dem Portal, dem Streamingdienst und dem Content-Zulieferungs Netzwerk. Das Portal lebt in SharePoint Online, der Streamingdienst lebt in Azure Media Services, und das Content Delivery Network lebt innerhalb des Azure CDN. In der folgenden Tabelle werden diese Komponenten beschrieben.
  
| |
|**Komponente**|**ZuGrunde liegende Anwendung**|**Enthalten in SharePoint Online BGP Community?**|**Verwendung**|
|:-----|:-----|:-----|:-----|
|Office 365-Video Portal  <br/> |SharePoint Online  <br/> |Ja  <br/> |Konfiguration, hochladen  <br/> |
|Office 365 Video Streaming-Dienst  <br/> |Azure Media Services  <br/> |Nein  <br/> |Streamingdienst, verwendet für den Fall, dass das Video aus dem CDN nicht verfügbar ist  <br/> |
|Office 365-Video Inhalts Bereitstellungsnetzwerk  <br/> |Azure CDN  <br/> |Nein  <br/> |Primäre Quelle für Video-Downloads/Streaming. [Erfahren Sie mehr über Office 365-Video Netzwerke](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).  <br/> |

Jede der Office 365-Features, die mit Microsoft-Peering verfügbar sind, finden Sie im [Artikel office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) -Endpunkte nach Anwendungstyp und FQDN. Der Grund für die Verwendung des FQDN in den Tabellen besteht darin, Kunden das Verwalten von Datenverkehr mit PAC-Dateien oder anderen Proxy Konfigurationen zu gestatten: Lesen Sie unseren Leitfaden zum [Verwalten von Office 365](https://aka.ms/manageo365endpoints) -Endpunkten zum Beispiel PAC-Dateien.
  
In einigen Situationen haben wir eine Platzhalterdomäne verwendet, in der eine oder mehrere untergeordnete FQDNs anders als die übergeordnete Platzhalterdomäne beworben werden. Dies ist in der Regel der Fall, wenn der Platzhalter eine lange Liste von Servern darstellt, die alle für Express Route und das Internet angekündigt werden, während eine kleine Untergruppe von Zielen nur im Internet beworben wird oder umgekehrt. In den Tabellen unten finden Sie Informationen zu den unterschieden.
  
In dieser Tabelle werden die Platzhalter-FQDNs angezeigt, die sowohl für die Internet-als auch für die Azure-Express Route neben den unter FQDNs, die nur im Internet beworben werden, angekündigt werden.

|**Platzhalterdomäne, die Express Route und Internet Schaltkreisen angekündigt wurde**|**Unter-FQDN nur für Internet-Schaltungen**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.Email.microsoftonline.com  <br/> Portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.Live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> CDN.ODC.officeapps.Live.com  <br/> OLS.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> OCWs.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

In der Regel sollen PAC-Dateien Netzwerkanforderungen an Express Route-angekündigte Endpunkte direkt an den Circuit und alle anderen Netzwerkanforderungen an Ihren Proxy senden. Wenn Sie eine PAC-Datei wie diese konfigurieren, erstellen Sie Ihre PAC-Datei in der folgenden Reihenfolge:
  
1. Schließen Sie die Sub-FQDNs aus Spalte 2 in der obigen Tabelle oben in ihrer PAC-Datei ein, und senden Sie den Datenverkehr zu Ihrem Proxy. Wir haben eine PAC-Beispieldatei erstellt, die Sie in unserem Artikel zum [Verwalten von Office 365](https://aka.ms/manageexpressroute365)-Endpunkten verwenden können.

2. Schließen Sie alle für Express Route markierten FQDNs in [diesem Artikel](https://aka.ms/o365endpoints) unterhalb des ersten Abschnitts ein, und senden Sie den Datenverkehr direkt an Ihre Express Route-Schaltung.

3. Schließen Sie alle anderen Netzwerkendpunkte oder-Regeln unter diesen beiden Einträgen ein, und senden Sie den Datenverkehr zu Ihrem Proxy.

In dieser Tabelle werden die Platzhalterdomänen angezeigt, die nur mit den untergeordneten FQDNs, die für Azure Express Route und Internet Schaltkreise angekündigt werden, für Internet Schaltkreise angekündigt werden. Für Ihre oben genannte PAC-Datei werden die FQDNs in Spalte 2 in der folgenden Tabelle als Express Route in dem referenzierten Link angezeigt, was bedeuten würde, dass Sie in die zweite Gruppe von Einträgen in der Datei eingeschlossen werden sollen.

|**Platzhalterdomäne, die nur für Internet-Leitungen beworben wird**|**Unter-FQDN, der Express Route und Internet Schaltkreisen angekündigt wurde**|
|:-----|:-----|
|\*. Office.com  <br/> |\*. Outlook.Office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. Office.net  <br/> |Agent.Office.net  <br/> |
|\*. office365.com  <br/> |Outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*. Outlook.com  <br/> |\*. Protection.Outlook.com  <br/> \*. Mail.Protection.Outlook.com  <br/> autodiscover\<-\>Tenant. Outlook.com  <br/> |
|\*. Windows.net  <br/> |Login.Windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing Office 365-Datenverkehr über das Internet und Express Route

Um zur Office 365-Anwendung Ihrer Wahl weiterzuleiten, müssen Sie eine Reihe von Schlüsselfaktoren festlegen.
  
1. Wie viel Bandbreite die Anwendung benötigt. Das Sampling der vorhandenen Nutzung ist die einzige zuverlässige Methode, um dies in Ihrer Organisation zu ermitteln.

2. Welchen Ausgangsstandort (en) Sie möchten, dass der Netzwerkdatenverkehr Ihr Netzwerk verlässt. Sie sollten die Netzwerkwartezeit für die Konnektivität zu Office 365 minimieren, da dies die Leistung beeinträchtigt. Da Skype for Business Echtzeit-sprach-und Videofunktionen verwendet, ist es besonders anfällig für eine schlechte Netzwerklatenz.

3. Wenn Sie möchten, dass alle oder eine Teilmenge ihrer Netzwerkstandorte Express Route nutzt.

4. An welchen Standorten Ihr ausgewählter Netzwerkanbieter Express Route anbietet.

Nachdem Sie die Antworten auf diese Fragen ermittelt haben, können Sie eine Express Route-Schaltung bereitstellen, die die Anforderungen an die Bandbreite und die Standorte erfüllt. Weitere Informationen zur Netzwerkplanung finden Sie im [Office 365 Network Tuning Guide](https://aka.ms/tune) und in der [Fallstudie, wie Microsoft die Netzwerk Leistungsplanung handhabt](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Beispiel 1: einzelner geographischer Standort
  
Dieses Beispiel ist ein Szenario für ein fiktives Unternehmen namens Trey Research, das einen einzelnen geografischen Standort hat.
  
Mitarbeiter bei Trey Research dürfen nur eine Verbindung mit den Diensten und Websites im Internet herstellen, die von der Sicherheitsabteilung explizit für das Paar von ausgehenden Proxys zulässig sind, die sich zwischen dem Unternehmensnetzwerk und Ihrem ISP befinden.
  
Trey Research plant die Verwendung von Azure Express Route für Office 365 und erkennt, dass einige Datenverkehr wie Datenverkehr, der für Inhalts Bereitstellungs Netzwerke bestimmt ist, nicht über die Express Route für Office 365-Verbindung geroutet werden kann. Da der gesamte Datenverkehr bereits standardmäßig an die Proxy Geräte weitergeleitet wird, funktionieren diese Anforderungen weiterhin wie zuvor. Nachdem Trey Research festgestellt hat, dass Sie die Anforderungen an das Azure-Express Route-Routing erfüllen können, fahren Sie fort, eine Leitung zu erstellen, das Routing zu konfigurieren und die neue Express Route-Schaltung mit einem virtuellen Netzwerk zu verknüpfen. Sobald die grundlegende Konfiguration von Azure Express Route vorhanden ist, verwendet Trey Research die [#2 PAC-Datei, die wir veröffentlichen](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) , um Datenverkehr mit kundenspezifischen Daten über die direkten Express Route für Office 365-Verbindungen weiterzuleiten.
  
Wie im folgenden Diagramm dargestellt, ist Trey Research in der Lage, die Anforderung zur Weiterleitung von Office 365-Datenverkehr über das Internet und eine Teilmenge des Datenverkehrs über Express Route mithilfe einer Kombination aus Routing-und ausgehenden Proxy Konfigurationsänderungen zu erfüllen.
  
1. Verwenden der [#2 PAC-Datei, die wir veröffentlichen](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) , um den Datenverkehr über einen separaten Internet-Ausgangspunkt für Azure Express Route für Office 365 zu leiten.

2. Clients sind mit einer Standardroute zu den Proxys von Trey Research konfiguriert.

In diesem Beispielszenario verwendet Trey Research ein ausgehendes Proxygerät. In ähnlicher Weise möchten Kunden, die Azure Express Route für Office 365 nicht verwenden, diese Methode verwenden, um Datenverkehr basierend auf den Kosten der Überprüfung des Datenverkehrs zu leiten, der für bekannte Hochleistungs Endpunkte bestimmt ist.
  
Die höchsten Volumen-FQDNs für Exchange Online, SharePoint Online und Skype for Business Online sind folgende:
  
![Express Route-Kunden-Edge-Netzwerk](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.office365.com, Outlook.Office.com

- \<mandantenname\>. sharepoint.com, \<mandantenname\>-my.sharepoint.com, \<mandantenname\>-\<-\>app. sharepoint.com

- \*. Lync.com zusammen mit den IP-Bereichen für nicht-TCP-Datenverkehr

- \*Broadcast.officeapps.Live.com, \*Excel.officeapps.Live.com, \*OneNote.officeapps.Live.com, \*PowerPoint.officeapps.Live.com, \*View.officeapps.Live.com, \*Visio.officeapps.Live.com \* , Word-Edit.officeapps.Live.com, \*Word-View.officeapps.Live.com, Office.Live.com

Erfahren Sie mehr über das [bereitstellen und Verwalten von Proxyeinstellungen in Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) und [sicherStellen, dass Office 365 nicht von Ihrem Proxy gedrosselt wird](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Bei einer einzelnen Express Route-Schaltung gibt es keine hohe Verfügbarkeit für Trey Research. Wenn treys redundantes Paar von Edge-Geräten, die die Express Route-Konnektivität warten, fehlschlägt, gibt es keinen zusätzlichen Express Route-Kreislauf für das Failover. Dies führt dazu, dass Trey Research in einer misslichen Lage ist, da das Failover zum Internet eine manuelle Neukonfiguration und in einigen Fällen neue IP-Adressen erfordert. Wenn Trey eine hohe Verfügbarkeit hinzufügen möchte, besteht die einfachste Lösung darin, für jeden Standort zusätzliche Express Route-Schaltungen hinzuzufügen und die Schaltungen aktiv/aktiv zu konfigurieren.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing-Express Route für Office 365 mit mehreren Standorten

Im letzten Szenario ist das Routing von Office 365-Datenverkehr über Express Route die Grundlage für noch komplexere Routing Architekturen. Unabhängig von der Anzahl der Standorte, der Anzahl der Kontinente, in denen diese Standorte vorhanden sind, Anzahl der Express Route-Schaltungen, und so weiter, die Möglichkeit, etwas Datenverkehr an das Internet und einige Datenverkehr über Express Route zu leiten, ist erforderlich.
  
Zu den zusätzlichen Fragen, die für Kunden mit mehreren Standorten in mehreren Regionen beantwortet werden müssen, gehört Folgendes:
  
1. Benötigen Sie an jedem Standort eine Express Route-Schaltung? Wenn Sie Skype for Business Online verwenden oder sich mit Latenz Sensitivität für SharePoint Online oder Exchange Online befassen, wird an jedem Standort ein redundantes Paar aktiver/aktiver Express Route-Schaltungen empfohlen. Weitere Informationen finden Sie unter Skype for Business Media Quality and Network Connectivity Guide.

2. Wenn in einer bestimmten Region kein Express Route-Schaltkreis verfügbar ist, wie soll Office 365 für den Datenverkehr bestimmt werden?

3. Was ist die bevorzugte Methode zum Konsolidieren von Datenverkehr im Fall von Netzwerken mit vielen kleinen Standorten?

Jede dieser Lösungen stellt eine einzigartige Herausforderung dar, bei der Sie Ihr eigenes Netzwerk und die von Microsoft verfügbaren Optionen bewerten müssen.

|**Berücksichtigt**|**Auszuwertende Netzwerkkomponenten**|
|:-----|:-----|
|Schaltungen an mehreren Standorten  <br/> |Es wird empfohlen, mindestens zwei Schaltungen aktiv/aktiv zu konfigurieren.  <br/> Die Kosten, die Wartezeit und die Bandbreitenanforderungen müssen verglichen werden.  <br/> Verwenden Sie BGP Route costs, PAC Files und NAT, um das Routing mit mehreren Schaltkreisen zu verwalten.  <br/> |
|WeiterLeitung von Standorten ohne Express Route-Schaltung  <br/> |Wir empfehlen die Ausstiegs-und DNS-Auflösung in der Nähe der Person, die die Anforderung für Office 365 initiiert.  <br/> DNS-Weiterleitung kann verwendet werden, damit Remotebüros den entsprechenden Endpunkt ermitteln können.  <br/> Für Clients in der Remoteniederlassung muss eine Route verfügbar sein, die den Zugriff auf die Express Route-Schaltung ermöglicht.  <br/> |
|Kleine Office-Konsolidierung  <br/> |Die verfügbare Bandbreite und die Datennutzung sollten sorgfältig verglichen werden.  <br/> |

> [!NOTE]
> Microsoft bevorzugt Express Route über das Internet, wenn die Route unabhängig vom physischen Standort verfügbar ist.
  
Jede dieser Überlegungen muss für jedes eindeutige Netzwerk berücksichtigt werden. Nachfolgend finden Sie ein Beispiel.
  
### <a name="example-2-multi-geographic-locations"></a>Beispiel 2: Standorte mit mehreren Standorten
  
Dieses Beispiel ist ein Szenario für ein fiktives Unternehmen namens Humongous Insurance, das über mehrere geographische Standorte verfügt.
  
Humongous Insurance ist geografisch verstreut mit Büros auf der ganzen Welt. Sie möchten Azure Express Route für Office 365 implementieren, um den Großteil des Office 365-Datenverkehrs auf direkten Netzwerkverbindungen zu halten. Humongous Insurance hat auch Niederlassungen auf zwei weiteren Kontinenten. Die Mitarbeiter in der Remoteniederlassung, in denen Express Route ist, müssen zu einer oder beiden primären Einrichtungen zurückkehren, um eine Express Route-Verbindung zu verwenden.
  
Das Leitprinzip besteht darin, den von Office 365 bestimmten Datenverkehr so schnell wie möglich an ein Microsoft-Datencenter zu bringen. In diesem Beispiel muss Humongous Insurance entscheiden, ob Ihre Remoteniederlassungen über das Internet weitergeleitet werden sollen, um so schnell wie möglich über eine Verbindung zu einem Microsoft-Datencenter zu gelangen, oder wenn Ihre Remoteniederlassungen über ein internes Netzwerk geroutet werden sollen, um zu einem Microsoft Datencenter über eine Express Route-Verbindung so schnell wie möglich.
  
Die Rechenzentren, Netzwerke und Anwendungsarchitekturen von Microsoft sind so konzipiert, dass Sie Global unterschiedliche Kommunikationen ermöglichen und Sie auf die effizienteste Art und Weise bedienen. Dies ist eines der größten Netzwerke der Welt. Anforderungen für Office 365, die länger als erforderlich in Kundennetzwerken verbleiben, werden diese Architektur nicht nutzen können.
  
In der Situation von Humongous Insurance sollten Sie in Abhängigkeit von den Anwendungen, die Sie für Express Route verwenden möchten, fortgesetzt werden. Wenn Sie beispielsweise Skype for Business Online-Kunden sind oder die Express Route-Konnektivität beim Herstellen einer Verbindung mit externen Skype for Business Online-Besprechungen nutzen möchten, wird das in der Skype for Business Online-Medienqualität und im Netzwerk empfohlene Design empfohlen. Connectivity Guide dient zum Einrichten einer zusätzlichen Express Route-Schaltung für den dritten Standort. Dies kann aus einer Netzwerk Perspektive teurer sein; das Weiterleiten von Anforderungen von einem Kontinent zu einem anderen vor dem Bereitstellen an ein Microsoft-Datencenter kann jedoch zu einer schlechten oder unbrauchbaren Erfahrung bei Skype for Business Online-Besprechungen und-Kommunikation führen.
  
Wenn Humongous Insurance nicht verwendet oder nicht plant, Skype for Business Online in irgendeiner Weise zu nutzen, kann das Routing von Office 365 bestimmt Netzwerkdatenverkehr zurück zu einem Kontinent mit einer Express Route-Verbindung möglicherweise möglich sein, kann jedoch zu unnötiger Wartezeit oder TCP führen. Überlastung. In beiden Fällen wird empfohlen, Internet-Datenverkehr an das Internet am lokalen Standort weiterzuleiten, um die Vorteile der Inhalts Bereitstellungs Netzwerke zu nutzen, auf denen Office 365 basiert.
  
![Express Route Multi-geography](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Wenn Humongous Insurance ihre mehr geografischen Strategien plant, gibt es eine Reihe von Faktoren, die sich auf die Größe der Schaltung, die Anzahl der Leitungen, das Failover usw. beziehen.
  
Bei Express Route an einem zentralen Standort mit mehreren Regionen, die versuchen, den Circuit zu verwenden, möchte Humongous Insurance sicherstellen, dass Verbindungen mit Office 365 von der Remote-Niederlassung an das nächstgelegene Office 365 Datacenter gesendet werden und von der Hauptsitz. Zu diesem Zweck implementiert Humongous Insurance die DNS-Weiterleitung, um die Anzahl der Roundtrips und DNS-Lookups zu verringern, die erforderlich sind, um die entsprechende Verbindung mit der Office 365-Umgebung am nächsten zum Internet-Ausgangspunkt des Hauptsitzes herzustellen. Dadurch wird verhindert, dass der Client einen lokalen Front-End-Server auflöst und sicherstellt, dass der Front-End-Server, mit dem die Person eine Verbindung herstellt, sich in der Nähe der Zentrale befindet, auf der Humongous Insurance mit Microsoft Peering Sie können auch erfahren, [wie Sie eine bedingte Weiterleitung für einen Domänennamen zuweisen](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
In diesem Szenario würde der Datenverkehr von der Remoteniederlassung die Office 365-Front-End-Infrastruktur in Nordamerika auflösen und Office 365 nutzen, um eine Verbindung mit den Back-End-Servern entsprechend der Architektur der Office 365-Anwendung herzustellen. Beispielsweise würde Exchange Online die Verbindung in Nordamerika beenden, und diese Front-End-Server stellen eine Verbindung mit dem Back-End-Postfachserver her, wo sich der Mandant befand. Alle Dienste verfügen über einen weit verteilten Front-Door-Dienst, der aus Unicast-und Anycastadresse-Destinationen besteht.
  
Wenn Humongous über größere Niederlassungen in mehreren Kontinenten verfügt, werden mindestens zwei aktive/aktive Stromkreise pro Region empfohlen, um die Wartezeit für vertrauliche Anwendungen wie Skype for Business Online zu verringern. Wenn sich alle Niederlassungen auf einem einzigen Kontinent befinden oder keine Zusammenarbeit in Echtzeit verwendet wird, ist die Verwendung eines konsolidierten oder verteilten Ausstiegs Punkts eine kundenspezifische Entscheidung. Wenn mehrere Schaltkreise verfügbar sind, stellt das BGP-Routing ein Failover sicher, falls eine einzelne Schaltung nicht mehr verfügbar ist.
  
Weitere Informationen zu Beispiel [Routingkonfigurationen](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) und [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Selektives Routing mit Express Route

Das selektive Routing mit Express Route kann aus einer Vielzahl von Gründen erforderlich sein, wie beispielsweise dem Testen und der Einführung von Express Route für eine Teilmenge von Benutzern. Es gibt verschiedene Tools, mit denen Kunden den Office 365-Netzwerkdatenverkehr selektiv über Express Route weiterleiten können:
  
1. **Routen Filterung/-Segregation** – das Zulassen der BGP-Routen zu Office 365 über Express Route zu einer Teilmenge der Subnetze oder Router. Dies wird selektiv nach Kundennetzwerk Segment oder physischem Bürostandort geleitet. Dies ist üblich für die Staffelung des Rollouts von Express Route für Office 365 und wird auf Ihren BGP-Geräten konfiguriert.

2. **PAC-Dateien/URLs** -leiten von Office 365 für bestimmte FQDNs zum Weiterleiten an einen bestimmten Pfad. Dies führt selektiv nach Clientcomputern, die von der [PAC-Datei Bereitstellung](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies)identifiziert werden.

3. **** Routefilter Routenfilter sind eine Möglichkeit, einen Teil der unterstützten Dienste über Microsoft-Peering zu nutzen.[](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)  - 

4. **BGP Communities** -Filterung basierend auf [BGP-Community-Tags](https://aka.ms/bgpexpressroute365) ermöglicht einem Kunden zu ermitteln, welche Office 365-Anwendungen Express Route durchlaufen und welches das Internet durchlaufen wird.

Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimieren Ihres Netzwerks für Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Express Route und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit Express Route](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Verwenden von BGP-Communities in Express Route für Office 365-Szenarien](bgp-communities-in-expressroute.md)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)
