---
title: Verwalten von ExpressRoute für Office 365-Diensten
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
description: ExpressRoute für Office 365 bietet eine alternative Routingpfad um viele Office 365-Dienste zu erreichen, ohne dass der gesamte Datenverkehr mit dem Internet egress. Zwar die Internet-Verbindung zu Office 365 noch benötigt wird, stellen Sie bestimmten Routen, die Microsoft in Ihr Netzwerk über BGP Ankündigung der direkten ExpressRoute Netzfrequenz bevorzugt, es sei denn, es weitere Konfigurationen in Ihrem Netzwerk sind. Die drei allgemeine Bereiche, den, die Sie konfigurieren, die zum Verwalten dieser routing einschließen möchten, Präfix filtern, Sicherheit und Compliance.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540780"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Verwalten von ExpressRoute für Office 365-Diensten

ExpressRoute für Office 365 bietet eine alternative Routingpfad um viele Office 365-Dienste zu erreichen, ohne dass der gesamte Datenverkehr mit dem Internet egress. Zwar die Internet-Verbindung zu Office 365 noch benötigt wird, stellen Sie bestimmten Routen, die Microsoft in Ihr Netzwerk über BGP Ankündigung der direkten ExpressRoute Netzfrequenz bevorzugt, es sei denn, es weitere Konfigurationen in Ihrem Netzwerk sind. Die drei allgemeine Bereiche, den, die Sie konfigurieren, die zum Verwalten dieser routing einschließen möchten, Präfix filtern, Sicherheit und Compliance.
  
> [!NOTE]
> Microsoft geändert, wie die Domäne für das Microsoft Peering routing für Azure ExpressRoute überprüft werden. Ab dem 31. Juli 2017 können alle Azure ExpressRoute Kunden Microsoft Peering direkt von der Azure-Verwaltungskonsole oder über PowerShell aktivieren. Nach der Aktivierung von Microsoft Peering kann kundenspezifischen Routefilter empfangen BGP Route Werbung für Dynamics 365 Kundenprojekt Applications (vormals CRM Online) erstellen. Kunden, die Azure ExpressRoute für Office 365 benötigen Überprüfen von Microsoft Routefilter für Office 365 erstellt werden können. Wenden Sie sich an Ihrem Microsoft Account Team um kennen zu lernen, wie Sie eine Überprüfung für die Aktivierung von Office 365 ExpressRoute anfordern. Nicht autorisierter Abonnements für Office 365 Routefilter erstellen möchten erhalten eine [Fehlermeldung](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Präfix filtern

Microsoft empfiehlt, dass Kunden alle BGP Routen akzeptieren, wie von Microsoft angekündigt, die Routen bereitgestellt unterzogen strengen Überprüfung und Validierung der Prozess entfernen alle Vorteile der Prüfung hinzugefügt werden. ExpressRoute bietet die empfohlenen Steuerelemente wie IP-Präfix Ownership, Integrität und Scale – systemintern keine eingehenden Route auf der Seite Customer filtern.
  
Wenn Sie zusätzliche Überprüfung der Route Gesamtbetriebskosten über ExpressRoute öffentlichen peering benötigen, können Sie anhand der Liste mit allen Präfixen für IPv4 und IPv6-IP-Routen angekündigten überprüfen, die [öffentliche IP-Adressbereiche Microsofts](https://www.microsoft.com/download/details.aspx?id=53602)darstellen. Diese Bereiche behandelt den vollständigen Microsoft-Adressraum und selten, ändern Sie einen zuverlässigen Satz von Bereichen für die gefiltert, die auch die zusätzlichen Schutz für Kunden, die nicht von Microsoft stammenden gehören Routen bereitstellt in Eindruck befürchten Bereitstellen ihrer Umgebung. Im Ereignisprotokoll geändert wird, wird auf den 1. des Monats erfolgen und die Versionsnummer im Abschnitt **Details** der Seite ändert sich jedes Mal, wenn die Datei aktualisiert wird.
  
Es gibt eine Reihe von Gründe für die Verwendung der [Office 365-URLs und IP-Adressbereiche](https://aka.ms/o365endpoints) für das Präfix Mail-Filterlisten generieren zu vermeiden. Einschließlich der folgenden:
  
- Die Office 365-IP-Präfixe unterzogen werden viele der Änderungen in regelmäßigen Abständen.

- Die Office 365-URLs und IP-Adresse, die Bereiche für die Verwaltung von Firewall vorgesehen sind Listen und Proxy-Infrastruktur nicht routing zulassen.

- Die Office 365-URLs und IP-Adressbereiche werden andere Microsoft-Dienste nicht behandelt, die für Ihre ExpressRoute Verbindungen im Bereich sein können.

| |
|**Option**|**Komplexität**|**Steuerelement ändern**|
|:-----|:-----|:-----|
|Alle Microsoft Routen akzeptieren  <br/> |**Niedrig:** Kunden beruht auf der Microsoft-Steuerelemente, um sicherzustellen, dass alle Routen ordnungsgemäß gehören.  <br/> |Keine  <br/> |
|Microsoft Filter gehören supernets  <br/> |**Mittel:** Kunden implementiert zusammengefassten Präfix Mail-Filterlisten, um nur die Routen gehören Microsoft ermöglichen.  <br/> |Kunden müssen sicherstellen, dass die seltene Updates in Routefilter übernommen werden.  <br/> |
|Filtern von Office 365 IP-Bereichen  <br/> [!CAUTION] Wird nicht empfohlen
|**Hohe:** Kunden Filter basierte auf definierten Präfixe für Office 365 IP-Routen.  <br/> |Kunden müssen eine robuste Änderungsmanagementprozesses die monatlichen Updates implementieren.  <br/> [!CAUTION]Diese Lösung erfordert erhebliche kontinuierliches Änderungen. Änderungen in Zeit führt wahrscheinlich zu einem Dienstausfall nicht implementiert.   |

Herstellen einer Verbindung mit Office 365 mit Azure ExpressRoute BGP Werbung von bestimmten IP-Subnetze basiert auf, die Netzwerke darstellen, in der Office 365-Endpunkten bereitgestellt werden. Aufgrund der globalen Eigenschaften von Office 365 und der Zahl der Dienste, die Office 365 bilden, haben Kunden häufig muss der Werbung verwalten, die sie in ihrem Netzwerk zu akzeptieren. Wenn Sie die betreffende Anzahl von Präfixen angekündigt in Ihrer Umgebung sind, können die [BGP Community](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) -Funktion zum Filtern der Werbung zu einem bestimmten Satz von Office 365-Dienste. Dieses Feature ist jetzt in der Vorschau.
  
Unabhängig davon, wie Sie die BGP Route anzeigen, die von Microsoft verwalten werden nicht Sie besonderen Belichtung zu Office 365-Diensten im Vergleich zum Herstellen einer Verbindung zu Office 365 über ein Internet Netzfrequenz allein erhalten. Microsoft behält die gleiche Sicherheit, Compliance und Leistungsmerkmale unabhängig von der Art der Verbindung, die ein Kunden für die Verbindung zu Office 365 verwendet werden.
  
### <a name="security"></a>Sicherheit

Microsoft empfiehlt, dass Sie Ihre eigenen Netzwerk und Sicherheit Umkreis-Steuerelemente für Verbindungen zu und von öffentlichen ExpressRoute und Microsoft peering, verwalten die Verbindungen zwischen Office 365-Dienste enthält. Sicherheitssteuerelemente sollten für Netzwerk-Anforderungen erfüllt sind, die aus dem Netzwerk, Microsoft Netzwerk ausgehende Reisen sowie eingehend von Microsoft Netzwerk mit dem Netzwerk.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Ausgehend von einem Kunden in Microsoft
  
Bei Computern mit Office 365 herzustellen, verbinden sie den gleichen Satz von Endpunkten, unabhängig davon, ob die Verbindung über eine Internet- oder ExpressRoute Verbindung hergestellt wird. Unabhängig von der Netzfrequenz verwendet wird empfiehlt es sich, dass Sie Office 365-Dienste als mehr als generische Internet Ziele vertrauenswürdig behandelt. Die Steuerelemente ausgehende Sicherheit sollten konzentrieren Sie sich auf die Ports und Protokolle zu reduzieren und laufenden Wartung zu minimieren. Die erforderlichen Portinformationen ist in der [Office 365-Endpunkten](https://aka.ms/o365endpoints) Referenzartikel verfügbar.
  
Für die hinzugefügten Steuerelementen können Sie FQDN Ebene innerhalb Ihrer Infrastruktur Proxy Filtern einschränken oder Überprüfen Sie einige oder alle Netzwerkanfragen für das Internet oder Office 365. Verwalten Sie die Liste FQDNs, wie Features veröffentlicht werden und die Office 365-Dienstangebote weiterentwickelt erfordert stabilere Änderungsmanagement und Nachverfolgen von Änderungen an der veröffentlichten [Office 365-Endpunkten](https://aka.ms/o365endpoints).
  
> [!CAUTION]
> Microsoft empfiehlt, dass Sie ausschließlich auf IP-Präfixe für die ausgehenden Sicherheit zu Office 365 verwalten verlassen nicht.

|**Option**|**Komplexität**|**Steuerelement ändern**|
|:-----|:-----|:-----|
|Keine Einschränkungen  <br/> |**Niedrig:** Kunden kann nicht eingeschränkt ausgehenden Zugriff auf Microsoft.  <br/> |Keine  <br/> |
|Port-Einschränkungen  <br/> |**Niedrig:** Kunden ausgehenden Zugriff auf Microsoft durch die erwartete Ports eingeschränkt.  <br/> |Seltene.  <br/> |
|FQDN-Einschränkungen  <br/> |**Hohe:** Kunden ausgehenden Zugriff auf Office 365 basierend auf der veröffentlichten FQDNs eingeschränkt.  <br/> |Monatliche Änderungen.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Eingehend von Microsoft zu Kunden
  
Es gibt mehrere optionale Szenarien, die erfordern Microsoft Verbindungen zu Ihrem Netzwerk zu initiieren.
  
- ADFS während der Überprüfung des Kennworts für die Anmeldung.

- [Exchange Server-hybridbereitstellungen](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- E-Mail von einem Exchange Online-Mandanten mit einem lokalen Host.

- SharePoint Online-Mail senden an einen lokalen Host aus SharePoint Online.

- [SharePoint-hybridsuche Verbund](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint Hybrid BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype für hybride Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) und/oder [Skype für den Verbund Business](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype für Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft empfiehlt, dass Sie diese Verbindungen über Ihre Internet Netzfrequenz anstelle der Netzfrequenz ExpressRoute zur Reduzierung der Komplexität akzeptieren. Wenn die Einhaltung von Bestimmungen oder der Leistung muss bestimmen, dass diese eingehenden Verbindungen über ein ExpressRoute Netzfrequenz akzeptiert werden müssen, wird empfohlen, verwenden eine Firewall oder der Reverseproxy beschränken die akzeptierten Verbindungen von. Die [Office 365-Endpunkten](https://aka.ms/o365endpoints) können Sie herausfinden, rechts FQDNs und IP-Präfixe.
  
### <a name="compliance"></a>Compliance

Wir verlassen nicht auf dem Routingpfad, mit denen, die Sie für alle unsere Compliance-Steuerelemente verwenden. Unabhängig davon, ob Sie zu Office 365-Diensten über ein ExpressRoute oder Internet Netzfrequenz verbunden ändert nicht unsere Compliance-Steuerelemente. Überprüfen Sie die verschiedenen Einhaltung von Vorschriften und Zertifizierung Sicherheitsebenen für Office 365, die beste Wahl zur Erfüllung der Anforderungen Ihrer Organisation zu ermitteln.
  
Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Verwandte Themen

[Die Inhaltsübermittlung](content-delivery-networks.md)
  
[URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Schulung zu Azure ExpressRoute für Office 365](https://channel9.msdn.com/series/aer)
