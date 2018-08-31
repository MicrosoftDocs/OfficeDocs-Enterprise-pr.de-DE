---
title: Office 365-Video networking häufig gestellte Fragen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
description: Die Office 365-Video-Repository und das streaming von Services vereinfachen speichern und das streaming von Videos in Ihrer Organisation. Es gibt eine sehr hilfreiche Informationen zu Office 365-Video. dieser Netzwerke häufig gestellte Fragen zu ist darauf ausgelegt, die am häufigsten gestellten Fragen, um die Planung, Verschlüsselung und wie der Dienst für die Inhaltsübermittlung (CDNs) nutzt Bandbreite zu beantworten.
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540791"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Office 365-Video networking häufig gestellte Fragen

Die Office 365-Video-Repository und das streaming von Services vereinfachen speichern und das streaming von Videos in Ihrer Organisation. Es gibt eine sehr hilfreiche [Informationen zu Office 365-Video](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50). dieser Netzwerke häufig gestellte Fragen zu ist darauf ausgelegt, die am häufigsten gestellten Fragen, um die Planung, Verschlüsselung und wie der Dienst für [die Inhaltsübermittlung (CDNs)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)nutzt Bandbreite zu beantworten.
  
Wenn Sie nicht bereits gründliche wissen, was geschieht, wenn ein Video hochgeladen wird oder wiedergegeben, eine Aufstellung der in diesem Video haben zusammengestellt wir, [Was geschieht, wenn eine Videodatei beim Hochladen in Office 365 Video](https://www.youtube.com/watch?v=HXSZ0jYBKlM).
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Was sind die Office 365-Video-bandbreitenanforderungen?

Es gibt zahlreiche [Videoformate unterstützt](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817) , die in Office 365 hochgeladen werden können. Jede Videodatei wird mit verschiedenen anderen video Merkmalen für die Wiedergabe klicken Sie dann auf ein Standardformat codiert. Office 365-Video verwendet adaptive Bitrate streaming, um die beste Videowiedergabequalität basierend auf die verfügbare Netzwerkbandbreite und die Größe des video-Players auszuwählen. Zu diesem Zweck fordert der Player zunächst die niedrigste Wiedergabequalität. Der Dienst beginnt dann 2 Sekunden video Segmente an den Videoplayer senden. Der Player kann dann anfordern höhere oder niedrigere Wiedergabequalität basierend auf jedes Segment wie schnell übermittelt werden.
  
Das adaptive Bitrate streaming erledigt all dies im Hintergrund, während das Video mit den geringsten Unterbrechung oder Pufferung wiedergegeben wird. Während der Videowiedergabe ermöglicht der Videoplayer Betrachter die automatische Wiedergabequalität, um eine bestimmte Videowiedergabequalität auszuwählen manuell außer Kraft gesetzt.
  
Hier ist eine schnelle Tabelle wird, die netzwerkanforderungen für die einzelnen die Videowiedergabe Merkmale erläutert. Die Mindestbandbreite pro Person erforderlich, um ein Video wiedergeben beträgt 802 Kbit / s.
  
|||
|:-----|:-----|
|**Wiedergabequalität** <br/> |**Netzwerkgeschwindigkeit** <br/> |
|288p  <br/> |802 Kbit/s  <br/> |
|360p  <br/> |1.2 Mbit/s  <br/> |
|576p  <br/> |2.5 Mbit/s  <br/> |
|720p  <br/> |3.8 Mbit/s  <br/> |

([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Wie CDNs Videowiedergabe?

Wenn mehrere Personen aus derselben Organisation innerhalb der gleichen geografischen Standort der gleichen Video(s) streaming sind, speichert CDNs eine Kopie der diese Videos an einem Speicherort näher zu diesem geografische Region. Mit dem Video gespeichert oder Cache an die nächste Position überträgt jede Person das Video aus dem Speicherort für diese anstelle eines Speicherorts Weitere engsten "Abwesend" anzeigen. Office 365-Video verwendet Azure Media-Dienste um zu verwalten, was in der Azure-CDNs und für wie lange zwischengespeichert werden. Azure Media-Dienste können [Azure CDN Speicherorte](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/) video Fragmente und Manifeste für binnen weniger Tage zwischengespeichert. Wenn der Benutzer in Ihrer Organisation weiterhin an die zwischengespeicherten Videos ansehen bleiben sie in den Cache. Wenn keine eine greift auf das Video für mehrere Tage, das Video wird schließlich werden Drop aus dem Cache gelöscht. Das nächste Mal, das jemand versucht, des Videos, wird er erneut an den nächstgelegenen Standort CDN zwischengespeichert.
  
Jeder Benutzer, der versucht, während der Inhalt des Videos wird eine in der Nähe CDN Vorteile wird näher ansehen und in den meisten Fällen weniger Hops entfernt zwischengespeichert. Dadurch wird die Videowiedergabe beschleunigt; die Netzwerk-Anforderung an die Videowiedergabe jedoch ändern nicht.
  
> [!NOTE]
> Es gibt Umständen wie unsere Kapazitätsgrenze erreicht wird, wobei das Video vor der drei Tage erreicht wurde entfernt werden kann.
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>Kann die Videos für schnellere Wiedergabe lokal werden zwischengespeichert?

Ja. Office 365 wird nicht verhindern, dass Sie mit einem lokalen CDN oder einen Zwischenspeichern Proxy, Video- und andere Office 365-Inhalte in Ihr lokales Netzwerk für einen schnelleren Zugriff aufzurufen. Es gibt verschiedene Methoden zum Implementieren einer lokalen Zwischenspeichern Lösung in Ihrem Netzwerk, die am häufigsten verwendete Methode besteht darin, eine Proxy-Lösung verwenden, in denen Sie Inhalte lokal zwischengespeichert. Nachdem Sie einen Proxyserver oder private CDN die video-Fragmente und Manifeste zwischengespeichert, werden zukünftige Anforderungen für die Dateien, die durch den Proxy oder private CDN geleitet werden aus dem lokalen Cache abgerufen und nicht aus dem Internet abgerufen. Berücksichtigen Sie bei der Planung einer Lösung wie folgt Netzwerkbandbreite, Kapazität und Videowiedergabe Parallelität.
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>Wie Videos verschlüsselt und geschützt werden?

Office 365-Video weiß, wie wichtig ist damit die Daten sicher und geschützt sind. [Das Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-cloud-computing-security) beschreibt unser Engagement für den Datenschutz und Sicherheit Ihrer Inhalte. Mit Videowiedergabe unbedingt Geschwindigkeit eine gute wünschen. allerdings nicht wir Ihre Sicherheits- oder private gegen Geschwindigkeit gefährden. Hier ist, wie wir Geschwindigkeit, Sicherheit und Datenschutz aufzunehmen.
  
Wenn Sie oder eine Person in Ihrer Organisation ein neues Video hochgeladen wird, ist, dass die videodatenfunktion transcodiert, mit AES-128-Verschlüsselung verschlüsselt und in Azure Media-Dienste gespeichert. Dies bedeutet, dass die Videos sowohl während der Übertragung und im Ruhezustand verschlüsselt werden.
  
Wenn eine Person in Ihrer Organisation versucht, ein neues Video ansehen, gehen sie folgendermaßen vor:
  
1. Bitten Sie SharePoint Online, wenn sie die Berechtigung, um das Video anzuzeigen.

2. SharePoint Online verwendet die Dateiberechtigungen, um zu bestimmen, ob die Person sehen Sie sich das Video kann.

3. Wenn dies zulässig ist, ruft SharePoint Online ein Token aus Azure so übergeben Sie an den Videoplayer.

4. Der Videoplayer verwendet das Token, um Schlüssel für die Entschlüsselung von Azure anzufordern.

5. Mit Schlüssel für die Entschlüsselung in die Hand kann der Videoplayer das Video stream.

![O365 Videowiedergabe](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Was sind die Anforderungen zur Wiedergabe Office 365-Video?

Office 365-Video unterstützten Betriebssystemen und Webbrowsern sind die gleichen wie die SharePoint Online Anforderungen in [Office 365-Systemanforderungen](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45). Je nach dem Betriebssystem und Web bestimmt Browserkonfiguration, die Ihnen die spezifischen Bedürfnissen des video-Players. Nachfolgend finden Sie weitere Informationen zu [Anforderungen für die Wiedergabe von Videos](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6).
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>Ich kann nicht abgerufen werden Office 365 video funktioniert, wobei I gestartet werden soll?

Problembehandlung bei Office 365-Video-Konnektivität umfasst eine Problembehandlung für Ihr Netzwerk, Ihre ISP(s) und die Konfiguration von Office 365. Das Service Health Dashboard ist für die zentrale Position zum Starten. Dadurch wird angewiesen, dass Sie über Office 365-Video oder kein Problem aufgetreten ist. Wenn alles gibt es umfangreiche ist, ist hier einige zusätzlichen Ressourcen, die Sie unterstützen.
  
- Stellen Sie sicher, dass die [Netzwerkendpunkte für Office 365 Video erforderliche](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)hergestellt werden kann.

- Überprüfen Sie die Netzwerkkonnektivität mit unserem [Office 365-Netzwerk Handbuch zur Problembehandlung](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).

- Finden Sie unsere [bewährte Methoden für die Verwendung von Office 365 bei langsamen Netzwerken](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166).

- Hier finden Sie [Hilfe zu Office 365-Video-Konfiguration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).

([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365-Video-Ressourcen

Das Thema bewerten oder einen Kommentar um uns mitzuteilen, wenn wir Ihre Fragen beantwortet haben, oder wenn Sie weiterhin für Antworten suchen. Nachfolgend finden Sie unsere anderen Ressourcen wenige, mit denen Sie die erfolgreiche Bereitstellung und Verwendung von Office 365-Videos:
  
[Hier finden Sie Hilfe zu Office 365-Video-Konfiguration](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50).
  
[Erfüllen von Office 365-Videos](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[Erstellen und Verwalten eines Kanals in Office 365-Videos](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[Verwalten Sie Ihre Office 365-Video-portal](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[Video Formate, die in Office 365-Videos funktionieren](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([Zurück zum Seitenanfang](office-365-video-networking-faq.md))
  
Nachfolgend finden Sie ein kurzer Link, zurückkehren verwendet werden können:[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
