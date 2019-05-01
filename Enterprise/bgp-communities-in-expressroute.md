---
title: Verwenden von BGP-Communities in Express Route für Office 365-Szenarien
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 'Das Herstellen einer Verbindung mit Office 365 mit Azure Express Route basiert auf BGP-Ankündigungen bestimmter IP-Subnetze, die Netzwerke darstellen, in denen Office 365-Endpunkte bereitgestellt werden. Aufgrund des globalen Charakters von Office 365 und der Anzahl von Diensten, die Office 365 darstellen, müssen Kunden häufig die in Ihrem Netzwerk akzeptierten Ankündigungen verwalten. Verringern der Anzahl von IP-Subnetzen; als IP-Präfixe im gesamten Rest dieses Artikels bezeichnet, dient zur Ausrichtung an der BGP-Netzwerk Verwaltungsterminologie folgende Endziele für Kunden:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490921"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Verwenden von BGP-Communities in Express Route für Office 365-Szenarien

Das Herstellen einer Verbindung mit Office 365 mit Azure Express Route basiert auf BGP-Ankündigungen bestimmter IP-Subnetze, die Netzwerke darstellen, in denen Office 365-Endpunkte bereitgestellt werden. Aufgrund des globalen Charakters von Office 365 und der Anzahl von Diensten, die Office 365 darstellen, müssen Kunden häufig die in Ihrem Netzwerk akzeptierten Ankündigungen verwalten. Verringern der Anzahl von IP-Subnetzen; als IP-Präfixe im gesamten Rest dieses Artikels bezeichnet, dient zur Ausrichtung an der BGP-Netzwerk Verwaltungsterminologie folgende Endziele für Kunden:
  
- **Verwalten der Anzahl** der anerkannten IP-Präfixe-Kunden, die über eine interne Netzwerkinfrastruktur oder einen Netzwerkbetreiber verfügen, der nur eine begrenzte Anzahl von IP-Präfixen und Kunden unterstützt, die über einen Netzbetreiber verfügen, der die Annahme von Präfixen anerkennt oberhalb einer begrenzten Anzahl soll die Gesamtzahl der bereits angekündigten Präfixe für Ihr Netzwerk ausgewertet werden, und wählen Sie aus, welche Office 365-Anwendungen am besten für Express Route geeignet sind.

- **Verwalten der erforderlichen Bandbreite für die Azure-Express Route-Schaltung** -Kunden können den Bandbreiten Umschlag der Office 365-Dienste über den Express Route-Pfad vs. Internet-Pfad steuern. So können Kunden Express Route Bandbreite für bestimmte Anwendungen wie Skype for Business reservieren und die restlichen Office 365-Anwendungen über den Internet Pfad weiterleiten.

Um Kunden bei diesen Zielen zu unterstützen, werden Office 365-IP-Präfixe, die über Express Route angekündigt werden, mit dienstspezifischen BGP-Community-Werten versehen, wie im folgenden Beispiel gezeigt.
  
> [!NOTE]
> Sie sollten davon ausgehen, dass im Zusammenhang mit anderen Anwendungen der Netzwerkdatenverkehr in den Community-Wert eingeschlossen wird. Dies ist das erwartete Verhalten für eine globale Software als Dienstangebot mit gemeinsamen Diensten und Datencentern. Dies wurde nach Möglichkeit mit den beiden oben genannten Zielen minimiert, wobei die Anzahl der Präfixe und/oder die Bandbreite berücksichtigt wird.

|**Dienst**|**BGP Community-Wert**|**Hinweise**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Umfasst Exchange-und EOP-Dienste\*  <br/> |
|Share\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype for Business\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|Weitere Office 365-Dienste\*  <br/> |12076:5100  <br/> |Umfasst Azure Active Directory (Authentifizierungs-und Verzeichnis Synchronisierungsszenarien) sowie Office 365-Portal Dienste  <br/> |
|\*Der Umfang der in Express Route enthaltenen Dienst Szenarien ist im [Office 365](https://aka.ms/o365endpoints) -Endpunkte-Artikel dokumentiert.  <br/> \*\*Weitere Dienste und BGP Community-Werte können in der Zukunft hinzugefügt werden. [Sehen Sie sich die aktuelle Liste der BGP-Communities an](https://azure.microsoft.com/documentation/articles/expressroute-routing/).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Was sind die am häufigsten verwendeten Szenarien für die Verwendung von BGP-Communities?

Kunden können BGP-Communities verwenden, um Gruppen von IP-Präfixen zu regulieren, die von Ihrem Netzwerk über Azure Express Route akzeptiert werden, wodurch die Gesamtzahl der IP-Präfixe und der erwartete Bandbreiten Umschlag bestimmter Office 365-Dienste beeinflusst wird. Es ist wichtig zu wissen, dass für alle Office 365 Internet gebundener Datenverkehr unabhängig von der Verwendung von Azure Express Route-oder BGP-Communities erforderlich ist. Die folgenden drei Szenarien sind die am häufigsten verwendeten Funktionen.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Szenario 1: Minimieren der Anzahl von Office 365-IP-Präfixen

Contoso Corporation ist ein Unternehmen mit 50.000 Personen, das Office 365 für Exchange Online und SharePoint Online verwendet. Bei der Überprüfung der Express Route-Anforderungen legt Contoso fest, dass seine Netzwerkgeräte an vielen regionalen Standorten keine Routingtabellen Größen über 100 zusätzliche Routen Einträge verarbeiten können. Contoso hat die Gesamtzahl der IP-Präfixe überprüft, die Express Route für den vollständigen Satz von Office 365-Diensten werben würde und Schlussfolge, dass er 100 überschreitet. Um unter den 100-zusätzlichen Routen Einträgen zu bleiben, stellt Contoso die Verwendung von Express Route für Office 365 auf den SharePoint Online-BGP-communitywert 12076:5020, der über Express Route Microsoft-Peering empfangen wird.

|**BGP-Community-Tag verwendet**|**Routing-Funktion über Azure Express Route**|**Erforderliche Internet Routen**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint &amp; Online-OneDrive for Business  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Dienste, die nicht speziell über Azure Express Route unterstützt werden  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/>  Office 365-Portal, Office 365- &amp; Authentifizierung, Office Online  <br/>  Exchange Online, Exchange Online Protection und Skype for Business Online  <br/> |

> [!NOTE]
> Um eine geringere Anzahl von Präfixen für jeden Dienst zu erreichen, bleibt eine minimale Überlappung zwischen den Diensten erhalten. Dies ist das erwartete Verhalten.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Szenario 2: Festlegen von Express Route und interner Bandbreitenverwendung für einige Office 365-Dienste

Fabrikam Inc, ein umfangreiches multinationales Unternehmen mit einem verteilten heterogenen Netzwerk, ist Abonnent vieler Office 365-Dienste, einschließlich; Exchange Online, SharePoint Online und Skype for Business Online. Die interne Routinginfrastruktur von Fabrikam kann Tausende von IP-Präfixen in ihren Routingtabellen verarbeiten. Fabrikam möchte jedoch nur Express Route und interne Bandbreite für Office 365-Anwendungen bereitstellen, die am empfindlichsten für die Netzwerkleistung sind und Ihre vorhandene Internet Bandbreite für alle anderen Office 365-Anwendungen verwenden.
  
Aus diesem Grund umfasst Fabrikam seine Azure Express Route-Bandbreite auf nur Skype for Business Online BGP Community Value, 12076:5030, empfangen über Express Route Microsoft-Peering. Der restliche Netzwerkdatenverkehr, der mit Office 365 verbunden ist, verwendet weiterhin die Internet-Ausstiegspunkte.

|**BGP-Community-Tag verwendet**|**Routing-Funktion über Azure Express Route**|**Erforderliche Internet Routen**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP-Signalisierung, Downloads, sprach-, Video-und Desktopfreigabe  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Dienste, die nicht speziell über Azure Express Route unterstützt werden  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/>  Office 365-Portal, Office 365- &amp; Authentifizierung, Office Online  <br/>  Skype for Business-Telemetrie, Skype-Client-schnell Tipps, öffentliche Chat-Konnektivität  <br/>  Exchange Online, Exchange Online Protection und SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Szenario 3: Bereichsdefinition für Azure Express Route für Office 365-Dienste

Die Woodgrove Bank ist ein Kunde mehrerer Microsoft-Cloud-Dienste, einschließlich Office 365. Nach Bewertung der Netzwerkkapazität und-Auslastung beschließt die Woodgrove Bank, Azure Express Route als bevorzugten Pfad für die unterstützten Office 365-Dienste bereitzustellen. Die Routingtabellen können den vollständigen Satz von Office 365-IP-Präfixen unterstützen, und die Express Route-Schaltungen, die Sie eingerichtet haben, unterstützen alle erwarteten Anforderungen an die Bandbreite und Latenz.
  
Um den Netzwerkdatenverkehr zu gewährleisten, der mit anderen Microsoft-Cloud-Diensten als Office 365 verbunden ist, umfasst die Woodgrove Bank die Verwendung von Express Route für Office 365 für alle IP-Präfixe, die mit Office 365-spezifischen BGP-Community-Werten, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**BGP-Community-Tag verwendet**|**Routing-Funktion über Azure Express Route**|**Erforderliche Internet Routen**|
|:-----|:-----|:-----|
|Exchange, Skype for Business, SharePoint &amp; , andere Dienste  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint &amp; Online-OneDrive for Business  <br/> Skype SIP-Signalisierung, Downloads, sprach-, Video-und Desktopfreigabe  <br/> Office 365-Portal, Office 365- &amp; Authentifizierung, Office Online  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Dienste, die nicht speziell über Azure Express Route unterstützt werden  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Wichtige Planungsüberlegungen für die Verwendung von BGP-Communities

Kunden, die BGP-Communities nutzen möchten, um zu beeinflussen, wie Express Route über das Kundennetzwerk beworben und propagiert wird, sollten die folgenden Aspekte berücksichtigen:
  
- Bei der Verwendung von BGP-Communities in Ihrem Netzwerkentwurf muss sichergestellt werden, dass die Routen Symmetrie weiterhin beibehalten wird. In einigen Fällen kann das Hinzufügen oder Entfernen von BGP-Communities zu einer Situation führen, in der das symmetrische Routing unterbrochen wird und ihre Routingkonfiguration aktualisiert werden muss, um das symmetrische Routing wiederherzustellen.

- Das Definieren von Azure Express Route mit BGP Community values ist eine Kunden Aktion. Microsoft wirbt für alle IP-Präfixe, die der Peering-Beziehung zugeordnet sind, unabhängig von dem vom Kunden konfigurierten Scoping.

- Azure Express Route unterstützt keine Aktionen im Microsoft-Netzwerk basierend auf vom Kunden zugewiesenen BGP-Communities.

- Die von Office 365are verwendeten IP-Präfixe, die nur mit dienstspezifischen BGP-Community-Werten gekennzeichnet sind, werden nicht unterstützt. Office 365-Dienste sind global in der Natur, Filter Präfixe basierend auf dem Standort des Mandanten oder Daten in der Office 365-Cloud werden nicht unterstützt. Die empfohlene Vorgehensweise besteht darin, Ihr Netzwerk so zu konfigurieren, dass der kürzeste oder bevorzugte Netzwerkpfad vom Netzwerkstandort des Benutzers in das globale Microsoft-Netzwerk koordiniert wird, unabhängig vom physischen Speicherort der IP-Adresse des Office 365-Diensts. Sie fordern.

- Die in den einzelnen BGP-Community-Werten enthaltenen IP-Präfixe stellen ein Subnetz dar, das IP-Adressen für die Office 365-Anwendung enthält, die dem Wert zugeordnet ist. In einigen Fällen verfügt mehr als eine Office 365-Anwendung über IP-Adressen innerhalb eines Subnetzes, wodurch ein IP-Präfix in mehr als einem Community-Wert vorhanden ist. Dies wird erwartet, obwohl das Verhalten aufgrund der Zuordnungs Fragmentierung selten ist und sich nicht auf die Ziele der Präfix Zählung oder der Bandbreitenverwaltung auswirkt. Kunden werden aufgefordert, den Ansatz "Allow What es needed" zu verwenden, im Gegensatz zu "verweigern, was nicht erforderlich ist", wenn Sie BGP-Communities für Office 365 nutzen, um die Auswirkungen zu minimieren.

- Durch die Verwendung von BGP-Communities werden die zugrunde liegenden Netzwerkverbindungsanforderungen oder die Konfiguration für die Verwendung von Office 365 nicht geändert. Kunden, die auf Office 365 zugreifen möchten, müssen weiterhin auf das Internet zugreifen können.

- Das Definieren von Azure Express Route mit BGP-Communities wirkt sich nur auf die Routen aus, die Ihr internes Netzwerk über die Microsoft-Peering-Beziehung sehen kann. Möglicherweise müssen Sie zusätzliche Konfigurationen auf Anwendungsebene vornehmen, wie zum Beispiel die Verwendung einer PAC-oder WPAD-Konfiguration in Verbindung mit dem Bereichs Routing.

- Zusätzlich zur Verwendung der Microsoft-zugewiesenen BGP-Communities können Kunden ihre eigenen BGP-Communities zu Office 365-IP-Präfixen zuweisen, die über Azure Express Route gelernt wurden, um das interne Routing zu beeinflussen. Ein beliebter Anwendungsfall ist das Zuweisen einer standortbasierten BGP-Community zu allen Routen, die über jeden einzelnen Express Route-Peering-Standort erlernt werden, und anschließendes Verwenden dieser Informationen im Kundennetzwerk, um den kürzesten oder am meisten bevorzugten Netzwerkpfad zu koordinieren. Microsoft-Netzwerk. Die Verwendung von Kunden zugewiesenen BGP-Communities mit Express Route für Office 365-Szenarien liegt außerhalb des Bereichs des Microsoft-Steuerelements oder der Sichtbarkeit.

Hier ist ein kurzer Link, den Sie verwenden können, um [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365)zurückzukehren:.
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität mit Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Verbindungen](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Medienqualität und Netzwerkverbindungsleistung in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Express Route und QoS in Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit Express Route](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Unterstützung für BGP-Communities](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)
  
[Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer)
