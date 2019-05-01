---
title: Verwalten von ExpressRoute für Office 365-Verbindungen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Express Route für Office 365 bietet einen alternativen Routingpfad, um viele Office 365-Dienste zu erreichen, ohne dass der gesamte Datenverkehr an das Internet weitergeleitet werden muss. Obwohl die Internetverbindung mit Office 365 weiterhin erforderlich ist, wird die direkte Express Route-Schaltung von den von Microsoft angekündigten Routen über BGP in Ihrem Netzwerk so konfiguriert, dass es keine anderen Konfigurationen in Ihrem Netzwerk gibt. Die drei allgemeinen Bereiche, die Sie für die Verwaltung dieses Routings konfigurieren möchten, sind Präfix Filterung, Sicherheit und Compliance.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487731"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Verwalten von ExpressRoute für Office 365-Verbindungen

Express Route für Office 365 bietet einen alternativen Routingpfad, um viele Office 365-Dienste zu erreichen, ohne dass der gesamte Datenverkehr an das Internet weitergeleitet werden muss. Obwohl die Internetverbindung mit Office 365 weiterhin erforderlich ist, wird die direkte Express Route-Schaltung von den von Microsoft angekündigten Routen über BGP in Ihrem Netzwerk so konfiguriert, dass es keine anderen Konfigurationen in Ihrem Netzwerk gibt. Die drei allgemeinen Bereiche, die Sie für die Verwaltung dieses Routings konfigurieren möchten, sind Präfix Filterung, Sicherheit und Compliance.
  
> [!NOTE]
> Microsoft hat geändert, wie die Microsoft Peering-Routingdomäne für Azure Express Route überprüft wird. Ab dem 31. Juli 2017 können alle Azure Express Route-Kunden Microsoft-Peering direkt über die Azure-Verwaltungskonsole oder über PowerShell aktivieren. Nach der Aktivierung von Microsoft-Peering kann jeder Kunde Routenfilter erstellen, um BGP-Routenankündigungen für Dynamics 365-Kunden Engagement-Anwendungen (früher als CRM Online bezeichnet) zu erhalten. Kunden, die Azure Express Route für Office 365 benötigen, müssen die Überprüfungen von Microsoft erhalten, bevor Sie Routenfilter für Office 365 erstellen können. Wenden Sie sich an Ihr Microsoft-Konto Team, um zu erfahren, wie Sie eine Überprüfungen für die Aktivierung von Office 365 Express Route anfordern. Nicht autorisierte Abonnements, die versuchen, Routenfilter für Office 365 zu erstellen, erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Präfix Filterung

Microsoft empfiehlt, dass Kunden alle BGP-Routen akzeptieren, wie von Microsoft angekündigt, die angegebenen Routen unterliegen einem rigorosen Überprüfung-und Validierungsprozess, wodurch alle Vorteile der zusätzlichen Prüfung beseitigt werden. Express Route bietet systemeigene Empfohlene Steuerelemente wie IP-Präfix-Besitz, Integrität und Skalierung-ohne eingehende Routen Filterung auf Kundenseite.
  
Wenn Sie eine zusätzliche Überprüfung des Routen Besitzes für Express Route Public Peering benötigen, können Sie die angekündigten Routen anhand der Liste aller IPv4-und IPv6-IP-Präfixe, die die [öffentlichen IP-Bereiche von Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)darstellen, überprüfen. Diese Bereiche decken den vollständigen Microsoft-Adressraum ab und ändern sich unregelmäßig, wodurch ein zuverlässiger Satz von Bereichen zum Filtern bereitgestellt wird, die auch zusätzlichen Schutz für Kunden bieten, die sich über nicht von Microsoft besessene Routen in Ihrem Umgebung. Wenn eine Änderung vorliegt, wird Sie am 1. des Monats vorgenommen, und die Versionsnummer im **Detail** Bereich der Seite ändert sich bei jeder Aktualisierung der Datei.
  
Es gibt eine Reihe von Gründen, um die Verwendung der [Office 365-URLs und IP-Adressbereiche](https://aka.ms/o365endpoints) zum Generieren von Präfixfilter Listen zu vermeiden. Einschließlich der folgenden:
  
- Die IP-Präfixe von Office 365 werden häufig geändert.

- Die Office 365-URLs und IP-Adressbereiche sind für die Verwaltung von Firewall-Zulassungslisten und Proxy Infrastrukturen vorgesehen, nicht für Routing.

- Die Office 365-URLs und IP-Adressbereiche umfassen keine anderen Microsoft-Dienste, die sich möglicherweise im Bereich ihrer Express Route-Verbindungen befinden.

| |
|**Option**|**Komplexität**|**Änderungs Steuerelement**|
|:-----|:-----|:-----|
|Alle Microsoft-Routen akzeptieren  <br/> |**Niedrig:** Der Kunde stützt sich auf Microsoft-Steuerelemente, um sicherzustellen, dass alle Routen ordnungsgemäß gehören.  <br/> |Keine  <br/> |
|Filtern von Microsoft owned supernets  <br/> |**Mittel:** Der Kunde implementiert zusammengefasste Präfixfilter Listen, um nur die von Microsoft besessenen Routen zu ermöglichen.  <br/> |Kunden müssen sicherstellen, dass die unregelmäßigen Aktualisierungen in Routenfiltern wiedergegeben werden.  <br/> |
|Filtern von Office 365 IP-Bereichen  <br/> [!CAUTION] Nicht empfohlen
|**Hoch:** Kunden Filter Routen basierend auf definierten Office 365-IP-Präfixen.  <br/> |Kunden müssen einen robusten Change Management-Prozess für die monatlichen Updates implementieren.  <br/> [!CAUTION] Diese Lösung erfordert erhebliche laufende Änderungen. Änderungen, die nicht rechtzeitig implementiert werden, führen wahrscheinlich zu einem Dienstausfall.   |

Das Herstellen einer Verbindung mit Office 365 mit Azure Express Route basiert auf BGP-Ankündigungen bestimmter IP-Subnetze, die Netzwerke darstellen, in denen Office 365-Endpunkte bereitgestellt werden. Aufgrund des globalen Charakters von Office 365 und der Anzahl der Dienste, aus denen Office 365 besteht, müssen Kunden häufig die Ankündigungen verwalten, die Sie in Ihrem Netzwerk akzeptieren. Wenn Sie sich mit der Anzahl von Präfixen befassen, die in Ihrer Umgebung angekündigt wurden, können Sie mit der [BGP-Community](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) -Funktion die Ankündigungen zu einem bestimmten Satz von Office 365-Diensten filtern. Dieses Feature befindet sich jetzt in der Vorschau.
  
Unabhängig davon, wie Sie die BGP-Routenankündigungen von Microsoft verwalten, erhalten Sie keine besondere Exposition gegenüber Office 365-Diensten im Vergleich zur Verbindung mit Office 365 über einen Internet-Kreislauf allein. Microsoft behält die gleichen Sicherheits-, Konformitäts-und Leistungsstufen bei, unabhängig davon, welche Art von Leitung ein Kunde zum Herstellen einer Verbindung mit Office 365 verwendet.
  
### <a name="security"></a>Sicherheit

Microsoft empfiehlt, dass Sie Ihre eigenen Netzwerk-und Sicherheitsperimeter-Steuerelemente für Verbindungen zu und von Express Route Public und Microsoft Peering verwalten, einschließlich Verbindungen zu und von Office 365-Diensten. Sicherheitskontrollen sollten für Netzwerkanforderungen vorhanden sein, die ausgehend vom Netzwerk ins Microsoft-Netzwerk Reisen, sowie vom Microsoft-Netzwerk zu Ihrem Netzwerk.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Ausgehend vom Kunden zu Microsoft
  
Wenn Computer eine Verbindung mit Office 365 herstellen, stellen Sie eine Verbindung mit denselben Endpunkten her, unabhängig davon, ob die Verbindung über eine Internet-oder Express Route-Schaltung hergestellt wird. Unabhängig von der verwendeten Schaltung empfiehlt Microsoft, dass Sie Office 365-Dienste als vertrauenswürdiger als generische Internet Destinationen behandeln. Ihre ausgehenden Sicherheitskontrollen sollten sich auf die Ports und Protokolle konzentrieren, um die Exposition zu verringern und die laufende Wartung zu minimieren. Die erforderlichen Portinformationen sind im Referenzartikel [Office 365](https://aka.ms/o365endpoints) -Endpunkte verfügbar.
  
Für hinzugefügte Steuerelemente können Sie die Filterung auf FQDN-Ebene in ihrer Proxy Infrastruktur verwenden, um einige oder alle Netzwerkanforderungen für das Internet oder Office 365 zu beschränken oder zu überprüfen. Das Verwalten der Liste der FQDNs, während Features veröffentlicht werden und die Office 365-Angebote entwickeln, erfordert eine robustere Änderungsverwaltung und Nachverfolgung von Änderungen an den veröffentlichten [office 365](https://aka.ms/o365endpoints)-Endpunkten.
  
> [!CAUTION]
> Microsoft empfiehlt, dass Sie sich nicht ausschließlich auf IP-Präfixe verlassen, um die ausgehende Sicherheit in Office 365 zu verwalten.

|**Option**|**Komplexität**|**Änderungs Steuerelement**|
|:-----|:-----|:-----|
|Keine Einschränkungen  <br/> |**Niedrig:** Der Kunde ermöglicht den uneingeschränkten ausgehenden Zugriff auf Microsoft.  <br/> |Keine  <br/> |
|Portierungs Einschränkungen  <br/> |**Niedrig:** Der Kunde schränkt den ausgehenden Zugriff auf Microsoft durch die erwarteten Ports ein.  <br/> |Selten.  <br/> |
|FQDN-Einschränkungen  <br/> |**Hoch:** Der Kunde schränkt den ausgehenden Zugriff auf Office 365 basierend auf den veröffentlichten FQDNs ein.  <br/> |Monatliche Änderungen.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Eingehend von Microsoft an den Kunden
  
Es gibt mehrere optionale Szenarios, in denen Microsoft Verbindungen mit Ihrem Netzwerk initiieren muss.
  
- ADFS während der Kennwortüberprüfung für die Anmeldung.

- [Exchange Server-Hybrid Bereitstellungen](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- E-Mails von einem Exchange Online-Mandanten zu einem lokalen Host.

- SharePoint Online-e-Mail-Versand von SharePoint Online an einen lokalen Host.

- [SharePoint-Verbund Hybrid Suche](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint-Hybrid-BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype for Business-Hybrid](https://technet.microsoft.com/en-us/library/jj205403.aspx) -und/oder [Skype for Business-Verbund](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype for Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft empfiehlt, dass Sie diese Verbindungen über Ihren Internet Schaltkreis anstelle ihrer Express Route-Schaltung akzeptieren, um die Komplexität zu verringern. Wenn Ihre Konformitäts-oder Leistungsanforderungen dies erfordern, müssen diese eingehenden Verbindungen über eine Express Route-Schaltung akzeptiert werden, wobei eine Firewall oder ein Reverseproxy zum Bereich der akzeptierten Verbindungen verwendet werden sollte. Sie können die [Office 365](https://aka.ms/o365endpoints) -Endpunkte verwenden, um die richtigen FQDNs und IP-Präfixe herauszufinden.
  
### <a name="compliance"></a>Compliance

Wir verlassen uns nicht auf den Routingpfad, den Sie für unsere Compliance-Kontrollen verwenden. Unabhängig davon, ob Sie eine Verbindung zu Office 365-Diensten über einen Express Route-oder Internet Schaltkreis herstellen, ändern sich unsere Compliance-Steuerelemente nicht. Sie sollten die verschiedenen Kompatibilitäts-und Sicherheits Zertifizierungsstufen für Office 365 überarbeiten, um die beste Wahl für die Erfüllung der Anforderungen Ihrer Organisation zu finden.
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer)
