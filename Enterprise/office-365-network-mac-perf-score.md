---
title: Office 365 Netzwerkbewertung (Vorschau)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
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
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106327"
---
# <a name="office-365-network-assessment-preview"></a>Office 365 Netzwerkbewertung (Vorschau)

Die Office 365 Netzwerkbewertung gibt an, wie sich die Benutzererfahrung auf die Netzwerkkonnektivität des Kunden auswirkt. Die Auswirkungen von Microsoft-eigenen Netzwerkverbindungen sind hiervon ausgeschlossen, damit Kundennetzwerk Designs optimieren können, für die Sie verantwortlich sind.

Sie wird anhand von Messungen berechnet, die sich auf die Benutzererfahrung bei Schlüssel Office 365 Arbeitsauslastungen auswirken und als Prozentsatz mit einem Bereich von 0 bis 100 angezeigt werden.

Eine sehr niedrige Netzwerkbewertung deutet darauf hin, dass Office 365 Clients erhebliche Probleme beim Verbinden oder verbleibenden Benutzer reagieren haben. Eine Punktzahl von 80% steht für Netzwerkkonnektivität, bei der Sie nicht erwarten können, dass Benutzer Beschwerden über Ihre Office 365 Benutzererfahrung aufgrund ihrer Netzwerkleistung erhalten. Wenn Verbesserungen bei der Netzwerkkonnektivität vorgenommen werden, nimmt diese Bewertung zusammen mit der Benutzeroberfläche zu.

>[!IMPORTANT]
>Empfehlungen zur Netzwerkleistung, Einblicke und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.

## <a name="exchange-online"></a>Exchange Online

Für Exchange Online wird die TCP-Wartezeit vom Clientcomputer auf den Exchange-Front-End-Server gemessen. Dies kann durch die Entfernung beeinträchtigt werden, über die das Netzwerk über die Kunden LAN und WAN reist. Es kann auch durch Netzwerk-zwischengeschaltete Geräte oder Dienste beeinträchtigt werden, die die Konnektivität verzögern oder dazu führen, dass Pakete erneut gesendet werden.

## <a name="sharepoint-online"></a>SharePoint Online

Für SharePoint Online wird die Downloadgeschwindigkeit gemessen, die ein Benutzer für den Zugriff auf ein Dokument zur Verfügung stellt. Dies kann durch die verfügbare Bandbreite zwischen dem Clientcomputer und dem Netzwerk von Microsoft auf Netzwerk Schaltkreisen beeinträchtigt werden. Es wird auch häufig von Netzwerküberlastung beeinflusst, die in Engpässen bei komplexen Netzwerkgeräten oder in schlechten WLAN-Abdeckungsbereichen vorhanden ist.

## <a name="microsoft-teams"></a>Microsoft Teams

Für Microsoft Teams wird die Netzwerkqualität als UDP-Wartezeit, UDP-Jitter und UDP-Paketverlust gemessen. UDP wird für die Audio-und Video Medien Konnektivität für Anrufe und Konferenzen für Microsoft Teams verwendet. Dies kann durch die gleichen Faktoren wie Wartezeit und Downloadgeschwindigkeit sowie Verbindungs Lücken in der UDP-Unterstützung eines Netzwerks beeinträchtigt werden, da UDP separat mit dem häufigeren TCP-Protokoll konfiguriert wird.

## <a name="tenant-network-score-and-office-location-network-score"></a>Netzwerkbewertung für Mandanten und Office-Standort

Eine Netzwerkbewertung misst den Entwurf des Netzwerkperimeters eines Office-Standorts für das Microsoft-Netzwerk. Verbesserungen am Netzwerkperimeter werden am besten an jedem Office-Standort vorgenommen, oder wenn die Netzwerkkonnektivität aggregiert ist, können Verbesserungen auftreten, die sich auf mehrere Standorte auswirken.
Wir zeigen eine Netzwerkbewertung für den gesamten Office 365 Mandanten auf der Übersichtsseite "Netzwerkleistung" und eine bestimmte Netzwerkbewertung für jeden erkannten Office-Standort auf der Zusammenfassungsseite dieses Standorts an.

## <a name="network-score-panel"></a>Bereich "Netzwerkbewertung"

Jedes Netzwerk Ergebnis gibt an, ob für den Mandanten oder für einen bestimmten Bürostandort ein Bereich mit Details zur Partitur angezeigt wird. In diesem Bereich wird ein Balkendiagramm des Ergebnisses sowohl als Prozentsatz als auch als Gesamtpunktzahl für jede Arbeitsauslastung der Komponente angezeigt, einschließlich der Arbeitslasten, bei denen Messdaten empfangen wurden. Für eine Bürostandort-Netzwerkbewertung zeigen wir auch einen Benchmark an, bei dem es sich um den Median aller Office 365-Clients handelt, von denen Daten in derselben Stadt wie Ihr Bürostandort gemeldet wurden.

Der Bewertungs Aufschlüsselung in der Gruppe zeigt die Bewertung für jede Arbeitsauslastung der Komponente an.

Der Bewertungsverlauf zeigt die letzten 30 Tage der Bewertung und die Benchmark an.

## <a name="related-topics"></a>Verwandte Themen

[Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)](office-365-network-mac-perf-overview.md)

[Office 365 Einblicke in die Netzwerkleistung (Vorschau)](office-365-network-mac-perf-insights.md)

[Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)](office-365-network-mac-perf-onboarding-tool.md)
