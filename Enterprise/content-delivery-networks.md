---
title: Netzwerke für die Inhaltsübermittlung
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Anhand dieser Informationen erfahren Sie mehr über Content subNetze (CDNs) und wie Office 365 Sie nutzt.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636096"
---
# <a name="content-delivery-networks"></a>Netzwerke für die Inhaltsübermittlung

Anhand der Informationen in diesem Thema erfahren Sie mehr über Content subNetze (CDNs) und wie diese von Office 365 verwendet werden.

CDNs helfen, Office 365 für Endbenutzer schnell und zuverlässig zu halten. Cloud-Dienste wie Office 365 verwenden CDNs zum Zwischenspeichern statischer Ressourcen in der Nähe der Browser, die Sie anfordern, um die Downloads zu beschleunigen und die Wartezeit zu verringern. Öffentliche CDNs ermöglichen schnellere Downloads generischer Inhalte wie JavaScript-Dateien, Symbole und Bilder, während private CDNs schnellen, sicheren Zugriff auf Benutzer Inhalte wie Videos und SharePoint Online-Dokumentbibliotheken bieten können.
  
 **Zurück zu** [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune).
  
## <a name="what-exactly-is-a-cdn"></a>Was genau ist ein CDN?

CDNs werden von den meisten Enterprise-Cloud-Diensten verwendet. Cloud-Dienste wie Office 365 haben Millionen von Kunden, die gleichzeitig eine Mischung aus proprietären Inhalten (wie e-Mails) und generischen Inhalten (beispielsweise Symbole) herunterladen. Es ist effizienter, Bilder, die von allen Benutzern verwendet werden, wie beispielsweise Symbole, so weit wie möglich auf dem Computer des Benutzers zu platzieren. Dennoch ist es für jeden Cloud-Dienst nicht praktikabel, CDN-Datencenter zu erstellen, in denen dieser generische Inhalt in jedem Ballungsraum oder sogar in jedem wichtigen Internet-Hub auf der ganzen Welt gespeichert ist, sodass einige dieser CDNs gemeinsam genutzt werden.
  
CDNs kann privat oder öffentlich sein. Private CDNs werden von einem einzigen Unternehmen besessen und betrieben, und nur die Anwendungen und Dienste dieses Unternehmens können es verwenden. Öffentliche CDNs werden von Unternehmen ausgeführt, die die Nutzung für mehrere Unternehmen leasen. Je nachdem, wo Sie sich befinden, ist es möglicherweise am effizientesten, dass Office 365 generische Bilder aus einem CDN herunterlädt, das von Office 365 besitzt und ausgeführt wird, ein öffentliches CDN oder eine Kombination der beiden. Unabhängig davon, welche Art von CDN verwendet wird, sind die Schritte zum Abrufen der Daten identisch.
  
1. Ihr Client fordert Daten aus Office 365 an.

2. In Office 365 werden die Daten entweder direkt an den Client zurückgegeben oder Ihr Client wird an ein CDN weitergeleitet.

3. Wenn die Daten bereits im CDN zwischengespeichert sind, downloadet Ihr Client die Daten direkt vom nächstgelegenen CDN-Standort zu Ihrem Client im Internet.

4. Wenn die Daten nicht im CDN zwischengespeichert werden, fordert der CDN-Knoten die Daten von Office 365 an und speichert dann die Daten für einen bestimmten Zeitraum, nachdem der Client die Daten heruntergeladen hat.

Die CDNs ziehen die Dateien und Bilder vom nächsten Office 365-Datencenter ab, und der Client ruft die Dateien und Bilder aus dem nächsten CDN ab. Wenn Benutzer auf einen clouddienst zugreifen, wie das Lesen von e-Mails in Outlook Web App, versucht der Browser des Benutzers, die Dateien und Bilder aus dem Office 365-Datencenter abzurufen. Anstatt die Zeit und die Bandbreite der Dateien zu verbringen, leitet Office 365 den Browser an das CDN weiter. Das CDN stellt das nächstgelegene Rechenzentrum für den Browser des Benutzers dar und downloadet mithilfe der Umleitung die generischen Bilder von dort. Die Verwendung dieser CDN-Umleitung ist schnell und spart Benutzern eine große Downloadzeit.

## <a name="how-do-cdns-make-services-work-faster"></a>Wie können CDNs Dienste schneller arbeiten?

Das Herunterladen von häufig verwendeten Elementen wie Symbolen kann Netzwerkbandbreite beanspruchen, die für das Herunterladen wichtiger persönlicher Inhalte wie e-Mails oder Dokumente besser verwendet werden kann. Da Office 365 eine Architektur mit CDNs verwendet, können die Symbole, Skripts und andere generische Inhalte von Servern heruntergeladen werden, die näher an Clientcomputer Herangehen, wodurch die Downloads schneller ausgeführt werden. Das bedeutet einen schnelleren Zugriff auf Ihre persönlichen Inhalte, der sicher in Office 365-Rechenzentren gespeichert ist.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Wie richte ich mein Netzwerk so ein, dass CDNs am besten mit Office 365 funktioniert?

Wenn Sie [die Netzwerkkonnektivität mit Office 365](network-connectivity.md)planen, ist es hilfreich, zu verstehen, wie CDNs im Allgemeinen funktioniert und wie CDN-Netzwerkdatenverkehr verwaltet werden sollte.

Wenn Sie ein CDN für Ihren Office 365-Mandanten aktivieren, legen Sie zunächst fest, welche Richtlinien für die Inhaltsquellen gelten (als **Ursprung** im Kontext von CDNs), Datenklassifizierungen oder Dateitypen, die über das CDN verteilt werden sollen. Benutzer, die auf den angegebenen Inhalt zugreifen, werden an den nächstgelegenen Speicherort der Datei im CDN umgeleitet. Daher sollten Sie die in [Managing Office 365](managing-office-365-endpoints.md) Endpoints beschriebenen bewährten Methoden verwenden, um sicherzustellen, dass die Netzwerkkonfiguration es Clientbrowsern ermöglicht, direkt auf das CDN zuzugreifen, anstatt CDN-Datenverkehr über zentrale Proxys zu übertragen, um unnötige Wartezeit.

## <a name="is-my-data-safe"></a>Sind meine Daten sicher?

Wir unterstützen Sie dabei, sicherzustellen, dass wir die Daten schützen, die Ihr Unternehmen ausführen. Kundenspezifische Daten, die in CDNs gespeichert sind, werden sowohl während der Übertragung als auch im Rest verschlüsselt.

> [!NOTE]
> CDN-Anbieter haben möglicherweise Datenschutz-und Konformitätsstandards, die von den vom Office 365 Trust Center beschriebenen Verpflichtungen abweichen. Daten, die über den CDN-Dienst zwischengespeichert werden, sind möglicherweise nicht mit den Microsoft-datenVerarbeitungsBedingungen kompatibel und können außerhalb der Kompatibilitäts Grenzen von Office 365 Trust Center liegen.

Ausführliche Informationen zum Datenschutz und zur Sicherheit für Office 365 CDN-Anbieter finden Sie unter:  

+ Weitere Informationen zu Office 365 Datenschutz im [Microsoft Trust Center](https://www.microsoft.com/trustcenter)
+ Weitere Informationen zu Azure Privacy and Data Protection im [Azure Trust Center](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ Erfahren Sie mehr über den Datenschutz und die Vertraulichkeit von Akamai im [Akamai Privacy Trust Center](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp) .

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Wie kann ich mein Netzwerk mit all diesen 3rd-Party-Diensten sichern?

Die Nutzung einer umfangreichen Reihe von Partnerdiensten ermöglicht Office 365 die Skalierung und Erfüllung der Verfügbarkeitsanforderungen sowie die Verbesserung der Benutzerfreundlichkeit bei der Verwendung von Office 365. Die 3rd Party Services Office 365 leverages umfasst beide Zertifikatssperrlisten; wie crl.microsoft.com oder sa.symcb.com und CDNs; wie R3.res.Outlook.com. Jeder CDN-FQDN, den Office 365 verwendet, ist ein benutzerdefinierter FQDN für Office 365. Wenn Sie auf Anforderung von Office 365 an einen FQDN gesendet werden, können Sie sicher sein, dass der CDN-Anbieter den FQDN und den zugrunde liegenden Inhalt an diesem Speicherort steuert.
  
Für Kunden, die Anforderungen für ein Microsoft-oder Office 365-Datencenter aus Anforderungen abtrennen möchten, die für einen Drittanbieter bestimmt sind, haben wir Anweisungen zur [Verwaltung von Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)-Endpunkten verfasst.

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Gibt es eine Liste aller CDNs, die von Office 365 verwendet werden?

Die CDNs, die von Office 365 verwendet werden, können immer geändert werden, und in vielen Fällen werden mehrere CDN-Partner konfiguriert, falls eine nicht verfügbar ist. Die primären CDNs sind:

+ [Office 365 (speziell für SharePoint Online-Inhalte)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

Diese CDN-Lösungen haben eine globale Reichweite, die die Reichweite des Diensts in mehr Ecken der Welt verbessert. Der dort gespeicherte Inhalt enthält allgemeine Office 365-Skripts, Dateien und Bilder. Wenn Sie sich beispielsweise bei portal.office.com anmelden, werden die Bilder aus dem nächsten CDN abgerufen, um die Ladezeiten der Seite zu beschleunigen. Weitere Beispiele sind Office 365 proPlus, die die Installations Bits in einem CDN speichern, um die Zeitdauer zu beschleunigen, die zum Herunterladen der neuesten Version von Office benötigt wird.

Außerdem gibt es einige proprietäre Inhalte, die auf CDNs gespeichert sind, wie beispielsweise Videodateien für Office 365. Nachdem Sie die Videos hochgeladen haben, werden die Dateien verschlüsselt und dann mit Azure Media Services im verschlüsselten Format gespeichert. Wenn der Office 365 Video Player das Video abruft, wird er zunächst auf das nächste CDN zwischengespeichert, bevor es heruntergeladen wird, um die Zeitdauer zu beschleunigen, die zum Herunterladen des Videos benötigt wird.

Informationen zur Verwendung des Office 365 CDN finden Sie unter [Verwenden des office 365 Content Delivery Network mit SharePoint Online](use-office-365-cdn-with-spo.md).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Gibt es eine Liste aller FQDNs, die CDNs nutzen?

Die Liste der FQDNs und ihre Verwendung von CDNs-Änderungen im Laufe der Zeit finden Sie auf der Seite veröffentlichte [Office 365-URLs und IP-Adressbereiche](https://go.microsoft.com/fwlink/p/?LinkID=293744) , um auf dem Laufenden über die neuesten FQDNs zu stehen, die CDNs nutzen.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kann ich mein eigenes CDN verwenden und Inhalte in meinem lokalen Netzwerk Zwischenspeichern?

Wir suchen ständig nach neuen Möglichkeiten, um die Anforderungen unserer Kunden zu erfüllen, und untersuchen derzeit die Verwendung von zwischen Speicherungs Proxy Lösungen und anderen lokalen CDN-Lösungen.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Ich verwende Azure Express Route für Office 365, ändert sich das?

[Azure Express Route für office 365](azure-expressroute.md) bietet eine dedizierte Verbindung zur Office 365-Infrastruktur, die vom öffentlichen Internet getrennt ist. Dies bedeutet, dass Clients weiterhin eine Verbindung über nicht-Express Route-Verbindungen herstellen müssen, um eine Verbindung mit CDNs und anderen Microsoft-Infrastrukturen herzustellen, die nicht explizit in der Liste der von Express Route unterstützten Dienste enthalten sind. Weitere Informationen zum Weiterleiten bestimmter Datenverkehr wie Anforderungen für CDNs finden Sie unter [Office 365 Network Traffic Management](routing-with-expressroute.md).
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Office 365-Endpunkten](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[URLs und IP-Adressbereiche von Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Verwenden des Office 365 Content Delivery Network mit SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Microsoft Trust Center](https://www.microsoft.com/trustcenter)