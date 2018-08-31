---
title: Verwenden von BGP Communitys in ExpressRoute für Office 365-Szenarien
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
description: 'Herstellen einer Verbindung mit Office 365 mit Azure ExpressRoute BGP Werbung von bestimmten IP-Subnetze basiert auf, die Netzwerke darstellen, in der Office 365-Endpunkten bereitgestellt werden. Aufgrund der globalen Eigenschaften von Office 365 und der Zahl der Dienste, die Office 365 bilden, haben Kunden häufig muss der Werbung verwalten, die sie in ihrem Netzwerk zu akzeptieren. Reduzieren der Anzahl der IP-Subnetze; als IP-Präfixe im weiteren Verlauf des Artikels BGP Network Management Terminologie ausgerichtet dient die folgenden End-Ziele für Kunden bezeichnet:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540744"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Verwenden von BGP Communitys in ExpressRoute für Office 365-Szenarien

Herstellen einer Verbindung mit Office 365 mit Azure ExpressRoute BGP Werbung von bestimmten IP-Subnetze basiert auf, die Netzwerke darstellen, in der Office 365-Endpunkten bereitgestellt werden. Aufgrund der globalen Eigenschaften von Office 365 und der Zahl der Dienste, die Office 365 bilden, haben Kunden häufig muss der Werbung verwalten, die sie in ihrem Netzwerk zu akzeptieren. Reduzieren der Anzahl der IP-Subnetze; als IP-Präfixe im weiteren Verlauf des Artikels BGP Network Management Terminologie ausgerichtet dient die folgenden End-Ziele für Kunden bezeichnet:
  
- **Verwalten der Ankündigungen entsprechen IP Rufnummernpräfix akzeptiert** - Kunden mit einer internen Netzwerkinfrastruktur oder Netzbetreibers, die unterstützt nur eine begrenzte Anzahl von IP-Präfixen und Kunden, die ein Netzbetreibers, Gebühren für die Annahme von Präfixen haben über eine begrenzte Anzahl wird die Gesamtanzahl der bereits in ihrem Netzwerk angekündigt Präfixe evaluieren möchten und wählen Sie aus, welche Office 365-Anwendungen für ExpressRoute am besten geeignet sind.

- **Verwalten der Bandbreite, die auf der Azure ExpressRoute Netzfrequenz erforderlich** - Kunden den Umschlag Bandbreite von Office 365-Diensten über den Pfad ExpressRoute im Vergleich zu Internet Pfad steuern möchten. Dies ermöglicht Kunden das Reservieren ExpressRoute Bandbreite für bestimmte Anwendungen wie Skype für Unternehmen und Weiterleiten von den verbleibenden Office 365-Anwendungen über das Internet Pfad.

Um Kunden mit dieser Ziele unterstützen, sind Präfixe für Office 365-IP, die über ExpressRoute bekannt gegeben werden mit Dienst spezifischen BGP Community Werte wie im folgenden Beispiel gezeigt markiert.
  
> [!NOTE]
> Sie erwarten, dass einige des Netzwerkverkehrs in Verbindung mit einer anderen Anwendung, die in der Community Wert eingeschlossen werden. Dies ist die erwartete Verhalten für eine globale Software als Dienst, der mit gemeinsamen Diensten und Rechenzentren anbietet. Dies wurde mit der oben genannten zwei Ziele, Verwalten von Präfix Count und/oder Bandbreite, beachten Sie nach Möglichkeit minimiert.

|**Dienst**|**BGP Community-Wert**|**Hinweise**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Enthält Exchange- und EOP-Dienste\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype für Unternehmen\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|andere Office 365-Dienste\*  <br/> |12076:5100  <br/> |Azure Active Directory (Authentifizierung und Verzeichnissynchronisierung Szenarien) umfasst sowie Dienste von Office 365-Portal  <br/> |
|\*Der Umfang der Service-Szenarien in ExpressRoute ist im [Office 365-Endpunkten](https://aka.ms/o365endpoints) Artikel dokumentiert.  <br/> \*\*Zusätzliche Dienste und BGP Community-Werte möglicherweise in Zukunft hinzugefügt werden. [Finden Sie in der aktuellen Liste der BGP Communitys](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Was sind die häufigsten Szenarien für die Verwendung von BGP Communitys?

Kunden können BGP Communitys um Gruppen von IP-Präfixe zu Regeln, die von ihrem Netzwerk über Azure ExpressRoute, daher mit Einfluss auf die Gesamtzahl der IP-Präfix und erwartete Bandbreite Umschlag bestimmter Office 365-Dienste akzeptiert werden. Es ist wichtig zu verstehen, dass alle Office 365 erfordert, dass Internet Datenverkehr unabhängig von der Verwendung von Azure ExpressRoute oder BGP Communitys gebunden. Die folgenden drei Szenarien sind die am häufigsten verwendeten Verwendungsmöglichkeiten für diese Funktionalität.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Szenario 1: Minimieren der Anzahl der Office 365 IP-Präfixe

Contoso Corporation ist ein 50.000 Person, die derzeit Office 365 für Exchange Online und SharePoint Online verwendet wird. Überprüfen von ExpressRoute können nicht Anforderungen, dass Contoso seine Netzwerkgeräte an vielen regionalen Standorten bestimmt routing Tabelle größer als 100 Einträge für zusätzliche Route behandeln. Contoso überprüft die Gesamtzahl der IP-Präfixe, die ExpressRoute würde ankündigen für den vollständigen Satz von Office 365-Diensten und dem Schluss, dass es 100 übersteigt. Um unter den 100 Einträge zusätzliche Route zu bleiben, Bereiche Contoso die Verwendung von ExpressRoute für Office 365 auf nur den SharePoint Online BGP Community Wert 12076:5020, über ExpressRoute Microsoft peering empfangen.

|**BGP Community-Tag verwendet**|**Routingfähige über Azure ExpressRoute Funktionalität**|**Internet Routen erforderlich**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive für Unternehmen  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Diensten über Azure ExpressRoute nicht explizit unterstützt.  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/>  Office 365-Portal, Office 365-Authentifizierung, &amp; Office Online  <br/>  Exchange Online, Exchange Online Protection und Skype für Unternehmen Online  <br/> |

> [!NOTE]
> Um niedrigere Präfix Anzahlen für jeden Dienst zu erreichen, werden die minimalen Überlappung zwischen Diensten beibehalten. Dieses ist Verhalten.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Szenario 2: Gültigkeitsbereichs ExpressRoute und interne Bandbreite verwenden, um einige Office 365-Dienste

Fabrikam Inc, große multinationale Unternehmen mit einem verteilten heterogenen Netzwerk ist ein-Abonnent viele Office 365-Dienste einschließlich. Exchange Online, SharePoint Online und Skype für Unternehmen Online. Interne routing von Fabrikam-Infrastruktur kann Tausende von IP-Präfixe in den Routingtabellen behandeln. Fabrikam möchte jedoch nur ExpressRoute und interne Bandbreite für Office 365-Anwendungen, die am häufigsten Beachtung sind von Netzwerk-Leistung und verwenden Sie ihre vorhandenen Internetbandbreite für Office 365-Anwendungen, bereitstellen.
  
Aus diesem Grund Bereiche Fabrikam seine Azure ExpressRoute Bandbreite für gerade Skype für Business Onlinecommunity BGP Wert 12076:5030, der über Microsoft ExpressRoute peering empfangen. Die verbleibenden des Netzwerkverkehrs in Verbindung mit Office 365 wird weiterhin die Internet Ausgang Punkte verwendet.

|**BGP Community-Tag verwendet**|**Routingfähige über Azure ExpressRoute Funktionalität**|**Internet Routen erforderlich**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP-Signale, Downloads, freigeben Sprach-, Video- und desktop  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Diensten über Azure ExpressRoute nicht explizit unterstützt.  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/>  Office 365-Portal, Office 365-Authentifizierung, &amp; Office Online  <br/>  Skype für Business Telemetrie, Skype Client schnelle Tipps, öffentlichen Instant Messaging-Diensten  <br/>  Exchange Online, Exchange Online Protection und SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Szenario 3: Bereichsdefinierung Azure ExpressRoute für Office 365-Dienste nur

Woodgrove Bank ist ein Kunde von mehrere Microsoft Cloud-Dienste einschließlich Office 365. Nach der Auswertung von ihrem Netzwerks beschließt Kapazität und Auslastung Woodgrove Bank, Azure ExpressRoute als bevorzugter Pfad für die unterstützten Office 365-Dienste bereitstellen. Die Routingtabellen enthalten können die umfassende Auswahl an Office 365 IP-Präfixen und Azure ExpressRoute Stromkreise, den, die Sie mit der Bereitstellung, unterstützen alle voraussichtliche Bandbreite und Wartezeit-Anforderungen.
  
Um sicherzustellen, dass Microsoft Cloud Services zugeordnet, abgesehen von Office 365, Woodgrove Bank legt die Verwendung von ExpressRoute für Office 365 für alle IP-Präfixe Netzwerkdatenverkehr markierte mit Office 365-Community Werte für bestimmte BGP, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**BGP Community-Tag verwendet**|**Routingfähige über Azure ExpressRoute Funktionalität**|**Internet Routen erforderlich**|
|:-----|:-----|:-----|
|Exchange, Skype für Unternehmen, SharePoint, &amp; andere Dienste  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive für Unternehmen  <br/> Skype SIP-Signale, Downloads, freigeben Sprach-, Video- und desktop  <br/> Office 365-Portal, Office 365-Authentifizierung, &amp; Office Online  <br/> | DNS, CRL, &amp; CDN-Anforderungen  <br/>  Alle anderen Office 365-Diensten über Azure ExpressRoute nicht explizit unterstützt.  <br/>  Alle anderen Microsoft Cloud-Dienste  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Wichtige Überlegungen zur Verwendung von BGP Communitys Planung

Kunden, nutzen Sie BGP Communitys zu beeinflussen, wie ExpressRoute angekündigt und über das Kundennetzwerk weitergegeben dauert die folgenden Aspekte berücksichtigen:
  
- Bei Verwendung von BGP Communitys in Ihrem Netzwerkentwurf ist es wichtig, um sicherzustellen, dass verbleibt Route Symmetrie. In einigen Fällen kann das Hinzufügen oder Entfernen von BGP Communitys erstellen eine Situation, in dem symmetrischen routing wird unterbrochen, und Ihre Routingkonfiguration muss aktualisiert werden, um symmetrische routing wiederherzustellen.

- Festlegen des Gültigkeitsbereichs Azure ExpressRoute mit BGP Community Werte ist eine Kunden-Aktion. Microsoft wird die Beziehung Peers, unabhängig davon alle Bereiche durch den Kunden konfiguriert alle IP-Präfixe zugeordnet ankündigen.

- Azure ExpressRoute unterstützt keine Aktionen auf Microsoft Netzwerk basierend auf Kunden BGP Communities zugewiesen.

- Die IP-Präfixe von Office 365are verwendete gekennzeichnet nur mit Dienst bestimmten BGP Community Werten Speicherort bestimmte BGP Communitys werden nicht unterstützt. Office 365-Diensten sind globale Natur, Filterung Präfixe basierend auf den Speicherort des Mandanten oder Daten innerhalb der Office 365-Cloud werden nicht unterstützt. Der empfohlene Ansatz besteht darin, Ihr Netzwerk zur Koordinierung der kürzeste oder die bevorzugte Netzwerkpfad von Speicherort im Netzwerk des Benutzers in der globalen Microsoft-Netzwerk, unabhängig von der physische Standort der IP-Adresse des Office 365-Dienst konfigurieren Sie anfordern.

- Die IP-Präfixe in jedem BGP Community-Wert enthalten darstellen ein Subnetzes, das IP-Adressen für die Office 365-Anwendung, die den Wert enthält. In einigen Fällen hat mehr als eine Office 365-Anwendung in einem resultierenden in vorhandenen im Wert von mehr als eine Community ein Präfix für den IP-Subnetz-IP-Adressen. Hierbei handelt es sich erwartet, obwohl nur selten, Verhalten Zuweisung fragmentiert und hat keinen Einfluss auf die Ziele Präfix Anzahl oder der Bandbreite Management. Benutzer werden aufgefordert, verwenden Sie die "ermöglichen, was benötigt wird" Ansatz, im Gegensatz zu "verweigern, was nicht erforderlich ist" beim Nutzen der Vorteile von BGP Communitys für Office 365, um den Effekt zu minimieren.

- BGP Communitys ändern nicht die zugrunde liegende Connectivity netzwerkanforderungen oder zum Verwenden von Office 365 erforderliche Konfiguration. Kunden, die auf Office 365 zugreifen möchten ist weiterhin erforderlich, um auf das Internet zugreifen zu können.

- Festlegen des Gültigkeitsbereichs Azure ExpressRoute mit BGP Communitys wirkt sich nur auf die Routen, die das interne Netzwerk über die Microsoft Peers Beziehung sehen kann. Sie müssen möglicherweise zusätzliche Konfigurationen auf Systemebene wie die Verwendung einer PAC oder WPAD-Konfiguration in Verbindung mit dem bereichsbezogenen routing vorzunehmen.

- Zusätzlich zur Verwendung der Microsoft BGP Communities zugewiesen, können Kunden ihren eigenen Communitys BGP Office 365 IP Präfixe über Azure ExpressRoute interne routing beeinflussen Erfahrungen zuweisen. Ein beliebte Anwendungsfall ist eine Stelle Grundlage BGP Community alle Routen, die über jeden angegebenen ExpressRoute peering Speicherort und mithilfe dieser Informationen downstream im Netzwerk Kunden der kürzeste koordinieren zuweisen oder am meisten bevorzugte Netzwerkpfad in Microsoft Netzwerk. Die Verwendung von Kunden BGP Communities mit ExpressRoute für Office 365-Szenarien zugewiesen ist außerhalb von Bereich der Microsoft-Steuerelement oder Sichtbarkeit.

Hier ist ein kurzer Link zurückkehren können: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerkkonnektivität zu Office 365](network-connectivity.md)
  
[Azure ExpressRoute für Office 365](azure-expressroute.md)
  
[Verwalten von ExpressRoute für Office 365-Diensten](managing-expressroute-for-connectivity.md)
  
[Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
  
[Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
  
[Medienqualität und Konnektivität Leistung des Netzwerks in Skype für Unternehmen Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute und QoS in Skype für Unternehmen Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Anruffluss mit ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementieren von ExpressRoute für Office 365](implementing-expressroute.md)
  
[Unterstützung für BGP-Communitys](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Office 365 Performance tuning mit Baselines und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)
  
[Leistungsbezogene Problembehandlung Plan für Office 365](performance-troubleshooting-plan.md)
  
[Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer)
