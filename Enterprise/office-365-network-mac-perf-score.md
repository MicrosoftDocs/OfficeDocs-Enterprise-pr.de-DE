---
title: Office 365 Netzwerkbewertung (Vorschau)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 Netzwerkbewertung (Vorschau)
ms.openlocfilehash: 24ecea73d9ecb6ae73b26e42a25749c846e3a281
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890362"
---
# <a name="office-365-network-assessment-preview"></a>Office 365 Netzwerkbewertung (Vorschau)

In der Microsoft 365 Admin Center-Verbindung mit der Microsoft 365-Seite destillieren **Netzwerkbewertungen** ein Aggregat vieler Netzwerk Leistungs Metriken in einer Momentaufnahme ihres Unternehmensnetzwerk Status, dargestellt durch einen Points-Wert von 1-100. Netzwerkbewertungen sind sowohl für den gesamten Mandanten als auch für jeden geografischen Standort ausgelegt, von dem die Benutzer eine Verbindung mit Ihrem Mandanten herstellen, sodass Office 365 Administratoren eine einfache Möglichkeit haben, eine Gestalt der Netzwerkintegrität des Unternehmens zu erfassen und schnell zu bohren. unten in einen detaillierten Bericht für einen beliebigen globalen Bürostandort.

Der Wert Netzwerk Bewertungspunkte ist eine durchschnittliche Messung der Wartezeit, der Bandbreite, der Downloadgeschwindigkeit und der Verbindungs Qualitäts Metriken, die zum Zeitpunkt der Anzeige Live kompiliert wurden. Leistungs Metriken für in Microsoft befindliche Netzwerke werden von diesen Messungen ausgeschlossen, um sicherzustellen, dass die Bewertungsergebnisse eindeutig und für das Unternehmensnetzwerk spezifisch sind.

![Netzwerk Bewertungs Wert](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Ein sehr niedriger Netzwerk Bewertungs Wert deutet darauf hin, dass Office 365 Clients erhebliche Probleme beim Herstellen einer Verbindung mit dem Mandanten oder beim aufrecht erhalten einer reaktionsfähigen Benutzeroberfläche haben, während ein hoher Wert ein ordnungsgemäß konfiguriertes Netzwerk mit wenigen fortlaufenden Leistungen angibt. Probleme. Ein Wert von 80% stellt eine gesunde Basislinie dar, bei der nicht erwartet werden soll, dass aufgrund der Netzwerkleistung regelmäßige Benutzer Beschwerden über Office 365 Konnektivität oder Reaktionsfähigkeit empfangen werden. Wenn die Verbesserungen für eine iterative Netzwerkkonnektivität vorgenommen werden, steigt dieser Wert zusammen mit der Benutzeroberfläche.

>[!IMPORTANT]
>Netzwerk Einblicke, Leistungsempfehlungen und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.

## <a name="network-assessment-panel"></a>Netzwerk Bewertungsbereich

Bei jeder Netzwerkbewertung, unabhängig davon, ob Sie auf den Mandanten oder einen bestimmten Standort beschränkt ist, wird ein Bereich mit Details zur Bewertung angezeigt. Dieses Panel zeigt ein Balkendiagramm der Bewertung sowohl als Prozentsatz als auch als Gesamtpunktzahl für jede Arbeitsauslastung der Komponente einschließlich der Arbeitslasten, bei denen Messdaten empfangen wurden. Für eine Bewertung des Office-Standortnetzwerks zeigen wir auch einen Benchmark an, bei dem es sich um den Median aller Office 365-Clients handelt, von denen Daten in derselben Stadt wie Ihr Bürostandort gemeldet wurden.

![Beispiel für einen Netzwerk Bewertungs Wert](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

Der **Bewertungs Aufschlüsselung** im Bereich zeigt die Bewertung für jede der Komponenten Arbeitsauslastungen.

Der **Bewertungsverlauf** zeigt die letzten 30 Tage der Bewertung und die Benchmark an.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Assessments für Mandanten Netzwerke und Netzwerkbewertungen für Office-Standorte

Eine Netzwerkbewertung misst den Entwurf des Netzwerkperimeters eines Office-Standorts für das Microsoft-Netzwerk. Verbesserungen am Netzwerkperimeter werden am besten an jedem Office-Standort vorgenommen, oder wenn die Netzwerkkonnektivität aggregiert ist, können Verbesserungen auftreten, die sich auf mehrere Standorte auswirken.

Wir zeigen einen Wert für die Netzwerkbewertung für den gesamten Office 365 Mandanten auf der Seite "Netzwerk Leistungsübersicht" und einen bestimmten Wert für jeden erkannten Office-Standort auf der Zusammenfassungsseite dieses Speicherorts an.

## <a name="exchange-online"></a>Exchange Online

Für Exchange Online wird die TCP-Wartezeit vom Clientcomputer auf den Exchange-Front-End-Server gemessen. Dies kann durch die Entfernung beeinträchtigt werden, über die das Netzwerk über die Kunden LAN und WAN reist. Es kann auch durch Netzwerk-zwischengeschaltete Geräte oder Dienste beeinträchtigt werden, die die Konnektivität verzögern oder dazu führen, dass Pakete erneut gesendet werden.

## <a name="sharepoint-online"></a>SharePoint Online

Für SharePoint Online wird die Downloadgeschwindigkeit gemessen, die ein Benutzer für den Zugriff auf ein Dokument zur Verfügung stellt. Dies kann durch die verfügbare Bandbreite zwischen dem Clientcomputer und dem Netzwerk von Microsoft auf Netzwerk Schaltkreisen beeinträchtigt werden. Es wird auch häufig von Netzwerküberlastung beeinflusst, die in Engpässen bei komplexen Netzwerkgeräten oder in schlechten WLAN-Abdeckungsbereichen vorhanden ist.

## <a name="microsoft-teams"></a>Microsoft Teams

Für Microsoft Teams wird die Netzwerkqualität als UDP-Wartezeit, UDP-Jitter und UDP-Paketverlust gemessen. UDP wird für die Audio-und Video Medien Konnektivität für Anrufe und Konferenzen für Microsoft Teams verwendet. Dies kann durch die gleichen Faktoren wie Wartezeit und Downloadgeschwindigkeit sowie Verbindungs Lücken in der UDP-Unterstützung eines Netzwerks beeinträchtigt werden, da UDP separat mit dem häufigeren TCP-Protokoll konfiguriert wird.

## <a name="related-topics"></a>Verwandte Themen

[Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)](office-365-network-mac-perf-overview.md)

[Office 365 Einblicke in die Netzwerkleistung (Vorschau)](office-365-network-mac-perf-insights.md)

[Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)](office-365-network-mac-perf-onboarding-tool.md)

[Office 365 Network Insights Privacy and Terms of use (Preview)](office-365-network-mac-perf-privacy.md)
