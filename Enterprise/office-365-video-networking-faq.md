---
title: Häufig gestellte Fragen zu Office 365-Video Netzwerken
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Mit dem Office 365 Video-Repository und den Streaming Services lassen sich Videos in Ihrer Organisation einfach speichern und streamen. Es gibt eine Menge toller Informationen zu Office 365 Video; Diese häufig gestellten Fragen rund um die Bandbreitenplanung und-Verschlüsselung sowie die Art und Weise, wie der Dienst Content-zuStellungs Netzwerke (CDNs) nutzt.
ms.openlocfilehash: f11bd8baff7c2527287f6e1249ad4dae1928bdd2
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491926"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Häufig gestellte Fragen zu Office 365-Video Netzwerken

Mit dem Office 365 Video-Repository und den Streaming Services lassen sich Videos in Ihrer Organisation einfach speichern und streamen. Es gibt eine Menge toller [Informationen zu Office 365 Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50); Diese häufig gestellten Fragen rund um die Bandbreitenplanung und-Verschlüsselung sowie die Art und Weise, wie der Dienst Content-zuStellungs [Netzwerke](content-delivery-networks.md) (CDNs) nutzt.
  
Wenn Sie nicht bereits gründlich verstehen, was passiert, wenn ein Video hochgeladen oder wiedergegeben wird, werfen Sie einen Blick auf dieses Video, das wir zusammengestellt haben, [Was passiert, wenn eine Videodatei in Office 365 Video hochgeladen](https://www.youtube.com/watch?v=HXSZ0jYBKlM)wird.
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Was sind die Anforderungen an die Video Bandbreite für Office 365?

Es gibt zahlreiche [Unterstützte Videoformate](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) , die in Office 365 hochgeladen werden können. Jede Videodatei wird dann in einem Standardformat mit verschiedenen videoqualitäten für die Wiedergabe codiert. Office 365 Video verwendet Adaptive Bitrate Streaming, um die beste Videowiedergabequalität basierend auf der verfügbaren Netzwerkbandbreite und der Größe des Videoplayers auszuwählen. Dazu fordert der Player zunächst die niedrigste Wiedergabequalität an. Der Dienst beginnt dann, zwei Sekunden Videosegmente an den Video Player zu senden. Der Spieler kann dann eine höhere oder niedrigere Wiedergabequalität anfordern, je nachdem, wie schnell jedes Segment zugestellt wird.
  
Das Streaming der adaptiven Bitrate bewirkt dies im Hintergrund, während das Video mit der geringsten Störungs-oder Pufferzeit wiedergegeben wird. Während der Videowiedergabe ermöglicht der Video Player dem Betrachter, die automatische Wiedergabequalität manuell zu überschreiben, um eine bestimmte Videowiedergabequalität auszuwählen.
  
Es folgt eine schnell Tabelle, in der die Netzwerkanforderungen für die einzelnen Videowiedergabe Qualitäten erläutert werden. Die minimale Bandbreite pro Person, die zum Abspielen eines Videos benötigt wird, ist 802Kbps.
  
|||
|:-----|:-----|
|**Wiedergabequalität** <br/> |**Netzwerkgeschwindigkeit** <br/> |
|288p  <br/> |802Kbps  <br/> |
|360p  <br/> |1,2 Mbps  <br/> |
|576p  <br/> |2,5 Mbps  <br/> |
|720p  <br/> |3,8 Mbps  <br/> |

([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>Wie helfen Inhalts Bereitstellungs Netzwerke (CDNs) bei der Videowiedergabe?

Wenn mehrere Personen aus derselben Organisation innerhalb desselben geografischen Standorts dasselbe Video (n) streamen, speichert CDNs eine Kopie dieser Videos an einem Speicherort, der näher an dieser geographischen Region liegt. Wenn das Video an der nächstgelegenen Position gespeichert oder zwischengespeichert wird, strömt jede Person das Video von dem am nächsten gelegenen Ort anstelle eines weiteren Standorts. Office 365 Video verwendet Azure Media Services, um zu verwalten, was in der Azure-CDNs zwischengespeichert wird, und für wie lange. Azure Media Services kann beliebige [Azure CDN-Speicherorte](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) verwenden, um Videofragmente und Manifeste für einige Tage zwischenzuspeichern. Wenn Personen in Ihrer Organisation weiterhin die zwischengespeicherten Videos ansehen, bleiben Sie im Cache. Wenn niemand mehrere Tage auf das Video zugreift, wird das Video schließlich aus dem Cache gelöscht. Das nächste Mal, wenn jemand versucht, das Video zu sehen, wird es wieder am nächstgelegenen CDN-Standort zwischengespeichert.
  
Jeder, der versucht, das Video zu beobachten, während der Inhalt an einem nahe gelegenen CDN zwischengespeichert wird, profitiert davon, dass das Video näher rückt und in den meisten Fällen weniger Hops entfernt ist. Dies verbessert die Videowiedergabegeschwindigkeit; die Netzwerkanforderung zum Abspielen des Videos wird jedoch nicht geändert.
  
> [!NOTE]
> Es gibt einige Umstände, wie zum Beispiel unsere Kapazitätsgrenze, bei der das Video entfernt werden kann, bevor die drei Tage erreicht wurden.
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>Kann ich die Videos lokal zwischenspeichern, um die Wiedergabe zu beschleunigen?

Ja. Office 365 verhindert nicht, dass Sie ein lokales CDN oder einen Cacheproxy verwenden, um Video-oder andere Office 365-Inhalte für einen schnelleren Zugriff in Ihr lokales Netzwerk zu übertragen. Es gibt mehrere Möglichkeiten, um eine lokale zwischen Speicherungs Lösung in Ihrem Netzwerk zu implementieren, die häufigste Methode ist die Verwendung einer Proxy Lösung, die Inhalte lokal zwischenspeichert. Sobald ein Proxy oder ein privates CDN die Videofragmente und-Manifeste zwischengespeichert hat, werden zukünftige Anforderungen für diese Dateien, die durch den Proxy oder das private CDN geroutet werden, aus dem lokalen Cache abgerufen und nicht von einem Internetspeicherort abgerufen. Berücksichtigen Sie bei der Planung einer solchen Lösung die Netzwerkbandbreite, die Kapazität und die Videowiedergabe Gleichzeitigkeit.
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Wie werden Videos verschlüsselt und gesichert?

Office 365 Video weiß, wie wichtig es ist, Ihre Daten sicher und privat zu halten. [Microsoft Trust Center](https://products.office.com/business/office-365-trust-center-welcome) beschreibt unsere Verpflichtung gegenüber dem Datenschutz und der Sicherheit Ihrer Inhalte. Bei der Videowiedergabe ist die Geschwindigkeit wichtig für eine gute Erfahrung; Allerdings gefährden wir nicht Ihre Sicherheit oder Ihren Datenschutz im Gegenzug für die Geschwindigkeit. Hier erfahren Sie, wie wir Geschwindigkeit, Sicherheit und Datenschutz einHalten.
  
Wenn Sie oder eine Person in Ihrer Organisation ein neues Video hochladen, wird dieses Video transcodiert, mit der AES-128-Verschlüsselung verschlüsselt und in Azure Media Services gespeichert. Dies führt dazu, dass die Videos sowohl während der Übertragung als auch in Ruhe verschlüsselt werden.
  
Wenn jemand in Ihrer Organisation versucht, ein neues Video zu sehen, führen Sie die folgenden Schritte aus:
  
1. Fragen Sie SharePoint Online, ob Sie über die Berechtigung zum Anzeigen des Videos verfügen.

2. SharePoint Online verwendet die Dateiberechtigungen, um zu bestimmen, ob die Person das Video ansehen kann.

3. Wenn Sie zulässig sind, ruft SharePoint Online ein Token aus Azure ab, um es an den Video Player zu übergeben.

4. Der Video Player verwendet dann das Token, um den Entschlüsselungsschlüssel von Azure anzufordern.

5. Mit dem Entschlüsselungsschlüssel in der Hand kann der Video Player das Video streamen.

![O365 Video Wiedergabe](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Was sind die Voraussetzungen für die Wiedergabe von Office 365 Video?

Office 365 Video unterstützte Betriebssysteme und Webbrowser sind identisch mit den SharePoint Online-Anforderungen in [office 365-Systemanforderungen](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Je nachdem, welches Betriebssystem und welche Webbrowserkonfiguration Sie haben, werden die spezifischen Anforderungen des Videoplayers bestimmt. Hier finden Sie weitere Informationen zu Anforderungen an die [Videowiedergabe](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Ich kann Office 365 Video nicht zur Arbeit bringen, wo sollte ich beginnen?

Die Problembehandlung der Konnektivität mit Office 365-Videos umfasst die Problembehandlung Ihres Netzwerks, Ihres ISP (s) und ihrer Konfiguration von Office 365. Der erste Anlaufpunkt ist das Service Health Dashboard. Auf diese Weise erfahren Sie, dass das Video von Office 365 ein Problem hat oder nicht. Wenn alles gut aussieht, finden Sie hier einige zusätzliche Ressourcen, die Ihnen helfen können.
  
- Stellen Sie sicher, dass Sie eine Verbindung mit den [für Office 365 Video erforderlichen Netzwerk](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)Endpunkten herstellen können.

- Überprüfen Sie die Netzwerkkonnektivität mithilfe unseres [Office 365 Network Troubleshooting Guide](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Sehen Sie [sich unsere bewährten Methoden für die Verwendung von Office 365 in einem langsamen Netzwerk an](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- [Hier finden Sie Hilfe zur Video Konfiguration von Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 Video-Ressourcen

Hier finden Sie einige weitere Ressourcen, die Ihnen bei der erfolgreichen Bereitstellung und Verwendung von Office 365-Videos helfen:
  
[Hier finden Sie Hilfe zur Video Konfiguration von Office 365](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[Erkunden von Office 365 Video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Erstellen und Verwalten eines Kanals in Office 365 Video](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  

  [Verwalten Ihres Office 365 Video-Portals](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Videoformate, die in Office 365 Video funktionieren](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
Mit diesem kurzen Link gelangen Sie wieder hierher zurück: [https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
