---
title: Die Inhaltsübermittlung
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
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
description: Mithilfe dieser Informationen erfahren Sie mehr über Content Delivery Networks (CDNs) und wie Sie Office 365 nutzt. CDNs, zur Sicherheit von Office 365 schnell und zuverlässig für Endbenutzer. Mit CDNs herunterladen Clouddiensten wie Office 365 schnell generischen Inhalte wie Symbole an, zum Browser Ihrer Benutzer, wenn sie den Dienst über einen Webclient verwenden.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540981"
---
# <a name="content-delivery-networks"></a>Die Inhaltsübermittlung

Mithilfe dieser Informationen erfahren Sie mehr über Content Delivery Networks (CDNs) und wie Sie Office 365 nutzt. CDNs, zur Sicherheit von Office 365 schnell und zuverlässig für Endbenutzer. Mit CDNs herunterladen Clouddiensten wie Office 365 schnell generischen Inhalte wie Symbole an, zum Browser Ihrer Benutzer, wenn sie den Dienst über einen Webclient verwenden.
  
 **Head zurück an** [Netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune).
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Wie sollte ich mein Netzwerk einrichten, sodass CDNs mit Office 365 am besten geeignet?

Wenn Sie [die Netzwerkkonnektivität zu Office 365](network-connectivity.md)planen, ist es hilfreich, zu verstehen, wie CDNs funktionieren. Es ist außerdem wichtig zu verstehen, dass Sie die Verbindung mit der CDNs durch IP-Adresse filtern ist nicht möglich. Wir stellen eine beste Effort Liste der IP-Adressen für die Dienste in Office 365, wie Exchange Online. Erfahren Sie mehr über unsere Empfehlungen zum [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="how-do-cdns-make-services-work-faster"></a>Wie beschleunigen CDNs Dienste?

Allgemeine Kriterien wie Symbole immer wieder herunterladen kann Netzwerkbandbreite in Anspruch nehmen, die für das Herunterladen von wichtige persönliche Inhalte wie e-Mail oder Dokumente besser verwendet werden können. Da Office 365 eine Architektur verwendet, die enthält CDNs, Symbole, Skripts und andere generische Inhalte von Servern näher an Clientcomputern arbeiten, machen die folgenden Downloads schneller heruntergeladen werden kann. Dies bedeutet schnelleren Zugriff auf Ihre persönlichen Inhalte, die in Office 365 Rechenzentren sicher gespeichert ist.
  
## <a name="what-exactly-is-a-cdn"></a>Was genau ist ein CDN?

CDNs werden von den meisten Unternehmen Cloud-Dienste verwendet. Clouddiensten wie Office 365 haben Millionen von Kunden, die eine Kombination von proprietäre Inhalts (beispielsweise-e-Mails) und generische Inhalte (wie Symbole) gleichzeitig herunterladen. Es ist effizienter, Bilder, die jeder verwendet, die wie Symbole werden, erreicht bald Computer des Benutzers wie möglich zu platzieren. Noch nicht für jede Clouddienst CDN Rechenzentren erstellen, bei die dieser generischen Inhalt in jeder Stadtgebiet oder sogar in jeder Haupt-Internet-Hub auf der ganzen Welt gespeichert, sodass einige der folgenden CDNs gemeinsam genutzt werden.
  
CDNs können privat oder öffentlich sein. Private CDNs gehört und wird durch ein einzelnes Unternehmen betrieben werden, und nur des Unternehmens Anwendungen und Dienste verwenden. Öffentliche CDNs werden von Unternehmen ausgeführt, die Auslastung auf mehrere Unternehmen zu verleasen. Je nachdem, wo Sie gespeichert sind ist es möglicherweise am effizientesten für Office 365 generische Bilder für Sie ein CDN, die Eigentümer von Office 365 und ausgeführt wird, ein öffentliche CDN oder eine Kombination aus beidem herunterladen. Unabhängig davon, welche Art von CDN verwendet wird sind die Schritte zum Abrufen der Daten identisch.
  
1. Der Client fordert Daten von Office 365.

2. Office 365 Daten direkt an den Client zurückgegeben, oder leitet den Client zu einem CDN.

3. Wenn die Daten bereits auf dem CDN zwischengespeichert werden, downloads Ihrer Client die Daten direkt aus dem nächsten CDN-Speicherort zum im Internet-Client an.

4. Wenn die Daten auf dem CDN zwischengespeichert nicht zur Verfügung, der Knoten CDN fordert die Daten aus Office 365, und klicken Sie dann den Cache die Daten für eine bestimmte Zeitspanne, nachdem der Client die Daten heruntergeladen.

Die CDNs pull-Dateien und Bildern aus der nächsten Office 365-Rechenzentrum und wiederum der Client Dateien und Bilder aus dem nächsten CDN abruft. Wenn der Benutzer Zugriff auf eine Cloud-Dienst wie das Lesen von e-Mail in Outlook Web App versucht der Browser des Benutzers zum Abrufen von Dateien und Bildern aus dem Office 365-Rechenzentrum. Anstelle von Ausgaben Bandbreite, die Bereitstellung von Dateien und die Uhrzeit, leitet Office 365 den Browser auf dem CDN. Das CDN engsten Datencenter an Browser des Benutzers ermittelt und Verwenden der Umleitung, downloads die generische Bilder von dort aus. Verwenden diese CDN-Umleitung ist schnell, und speichert Benutzer viel Downloadzeit.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Gibt es eine Liste mit allen FQDNs, die CDNs nutzen?

Die Liste der FQDNs und wie sie CDNs Änderung im Laufe der Zeit nutzen, finden Sie in unseren veröffentlichten [Office 365-Endpunkten Seite](https://go.microsoft.com/fwlink/p/?LinkID=293744) auf dem aktuellen Stand auf die neuesten FQDNs abgerufen, die CDNs nutzen.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Gibt es eine Liste mit allen CDNs, die Office 365 verwendet?

Die Verwendung von Office 365 CDNs sind immer kann geändert und in vielen Fällen stehen mehrere CDN Partner konfiguriert im Falle einer nicht verfügbar ist. Die beiden am häufigsten verwendeten CDNs verwendeten sind [Akamai](https://www.akamai.com/us/en/cdn.jsp) und [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Beide diese Lösungen CDN verfügen über eine Verbesserung der Reichweite des Diensts auf Weitere Ecken der Welt globaler Reichweite. Der Inhalt, der es gespeichert ist enthält allgemeine Office 365-Skripts, Dateien und Bildern. Wenn Sie sich portal.office.com anmelden, werden die Bilder aus dem nächsten CDN, um die Seitenladezeiten zu beschleunigen abgerufen. Andere Beispiele sind Office 365 ProPlus speichern die installationsbits auf ein CDN beschleunigt die Zeitspanne, die zum Herunterladen der neuesten Version von Office benötigt. Es gibt auch einige proprietäre Inhalte, die auf CDNs wie die Videodateien für Office 365 Video gespeichert ist. Nachdem Sie die Videos hochladen, werden die Dateien verschlüsselt und klicken Sie dann im verschlüsselten Format mit Azure Media-Dienste gespeichert. Bei der Office 365-video-Player das Video abgerufen wird er zuerst zwischengespeichert zu dem nächsten CDN vor, um die Zeitdauer, die benötigt wird, um das Video herunterzuladen beschleunigen heruntergeladen werden.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Bietet Office 365 ein CDN, die ich für eigene Dateien verwenden können?

Ja! Nun Ihr Office 365-Abonnement umfasst ein CDN, die von Azure getrennt ist, die speziell für Ihre SharePoint Online-Ressourcen verwendet werden können. Informationen zur Verwendung der Office 365-CDN finden Sie unter [Verwenden der Office 365 Content Delivery Networks mit SharePoint Online](use-office-365-cdn-with-spo.md).
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>Kann ich meinen eigenen CDN und Cache Inhalte im lokalen Netzwerk verwenden?

Wir gesuchten ständig neue Wege zur Unterstützung von unseren Kunden Anforderungen und die Verwendung des Zwischenspeicherns von Proxylösungen und andere lokale CDN-Lösungen sind derzeit erkunden.
  
## <a name="is-my-data-safe"></a>Sind meine Daten sicher?

Wir müssen Sie dazu beitragen, dass wir die Daten zu schützen, die Ihr Unternehmen ausgeführt wird. Die gespeicherten Content Delivery Network Partner Elemente ist entweder verschlüsselt. wie mit [Office 365-Video](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)oder keine bestimmte; Kunden wie die Office 365 ProPlus-Installationsdateien. Head auf über die [Office 365-Trust Center](https://go.microsoft.com/fwlink/p/?LinkId=397383) erfahren Sie mehr über unsere tief anstrengungen, die Ihre Daten und Ihre Privatsphäre zu schützen.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Wie kann mein Netzwerk mit diesen 3. Partei Diensten werden gesichert?

Eine umfassende Sammlung von Partnerdienste Nutzung ermöglicht Office 365 zu skalieren und Verfügbarkeit erfüllen sowie zum Verbessern der benutzererfahrung bei Office 365 verwenden. Die 3. Party-Dienste, die Office 365 nutzt enthalten sowohl Zertifikatsperrlisten. wie crl.microsoft.com oder sa.symcb.com und CDNs; wie r3.res.outlook.com. Jeder CDN FQDN Office 365 verwendet wird, eine benutzerdefinierte FQDN für Office 365, wenn Sie auf einen FQDN auf die Anforderung von Office 365 gesendet werden Sie können sicher, dass wir den FQDN und die zugrunde liegende Content an dieser Stelle steuern.
  
Für Kunden möchten, die noch Isolieren von Anfragen für ein Microsoft oder Office 365 Datencenter von Anfragen, die für eine 3. Partei, bestimmt sind wir haben von Anweisungen unter [Verwalten von Office 365-Endpunkten](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)geschrieben.
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Verwende ich Azure ExpressRoute für Office 365, ändert, die Dinge?

[Azure ExpressRoute für Office 365](azure-expressroute.md) bietet eine dedizierte Verbindung mit Office 365-Infrastruktur, die getrennt ist, aus dem öffentlichen Internet. Dies bedeutet, dass Clients immer noch eine Verbindung herstellen über nicht ExpressRoute Verbindungen zum Verbinden mit CDNs und andere Microsoft-Infrastruktur, die nicht explizit in der Liste der Dienste von ExpressRoute unterstützt enthalten ist. Weitere Informationen dazu, wie Sie bestimmten Datenverkehr wie Anfragen für CDNs verwendet finden Sie unter [Office 365 Netzwerk Datenverkehr Management](routing-with-expressroute.md).
  
Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Siehe auch

[Häufig gestellte Fragen zu Office 365-Endpunkten](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
