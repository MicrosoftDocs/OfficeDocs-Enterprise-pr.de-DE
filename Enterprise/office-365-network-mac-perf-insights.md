---
title: Office 365 Einblicke in die Netzwerkleistung (Vorschau)
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
description: Office 365 Einblicke in die Netzwerkleistung (Vorschau)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106334"
---
# <a name="office-365-network-performance-insights-preview"></a>Office 365 Einblicke in die Netzwerkleistung (Vorschau)

Die Microsoft 365 Admin Center-Netzwerk Leistungs Seiten zeigen Office 365 Einblicke in das Netzwerk, die beim Entwerfen von Netzwerkperimetern für Ihre Office-Standorte hilfreich sein können. Es gibt fünf spezifische Einblicke in das Netzwerk, die für die einzelnen Office-Standorte möglicherweise angezeigt werden.

>[!IMPORTANT]
>Empfehlungen zur Netzwerkleistung, Einblicke und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.

## <a name="backhauled-network-egress"></a>Ausstieg aus dem backhauld-Netzwerk

Der Abstand zwischen dem Benutzerstandort und dem Ausstiegs Netzwerk beträgt mehr als 500 Meilen (800 Kilometer), was sich auf die Leistung auswirken dürfte. Lokaler Ausstieg näher am Benutzer wird empfohlen.

Dadurch wird feststellen, dass der Abstand zwischen dem Bürostandort und dem Netzwerk Ausstieg mehr als 500 Meilen beträgt. Der Standort des Büros wird durch einen verborgenen Clientcomputer Speicherort identifiziert, und der Netzwerk Ausgangsspeicherort wird mithilfe von Reverse IP Address to Location Databases identifiziert. Der Office-Standort ist möglicherweise ungenau, wenn Windows-Ortungsdienste auf Computern deaktiviert sind. Der Netzwerk Ausgangsspeicherort ist möglicherweise ungenau, wenn die Datenbankinformationen der Reverse-IP-Adresse ungenau sind.

Details für diese Einblicke sind der Office-Standort, der Netzwerk Ausgangsstandort und der Abstand dazwischen.

Für diese Einblicke empfehlen wir einen Netzwerk Ausstieg näher am Bürostandort, damit die Konnektivität optimal an das Microsoft-Netzwerk im Internet und auf Office 365 Dienst-Fronttüren weitergeleitet werden kann. Das Schließen des Netzwerk Ausstiegs für Benutzer in Office-Standorten ermöglicht auch in Zukunft eine verbesserte Leistung, da Microsoft in Zukunft sowohl Netzwerk Points of Presence als auch Office 365-Service-Front-Doors erweitert.

Diese Einblicke wird in einigen zusammenfassungsansichten als "Ausstieg" abgekürzt.

## <a name="better-performance-detected-for-customers-near-you"></a>Bessere Leistung für Kunden in Ihrer Nähe erkannt

Da eine beträchtliche Anzahl von Kunden in Ihrem Metro-Bereich eine bessere Leistung hat als Benutzer in Ihrer Organisation an diesem Standort.

Dabei wird die Gesamtleistung der Office 365 Kunden in derselben Stadt wie dieser Bürostandort betrachtet.

![Relative Netzwerkleistung](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

Wir berechnen den Prozentsatz der Office 365 Kunden in der gleichen Stadt in besseren Leistungs Buckets. Wenn diese Zahl, wenn 10% von mehr dann zeigen wir die Netzwerk Einblicke.

Diese Einblicke wird in einigen zusammenfassungsansichten als "Peers" abgekürzt.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Verwenden eines nicht optimalen Exchange Online-Dienst-Front-Door

Der Benutzer stellt keine Verbindung zu einem optimalen Office 365-Dienst vor der Haustür her, und dies wird voraussichtlich Auswirkungen auf die Leistung haben.

Wir führen Exchange Online Service-Fronttüren auf, die für die Verwendung aus der Office-Standort Stadt mit guter Leistung geeignet sind. Wenn der aktuelle Test die Verwendung eines Exchange Online-Dienst-Front-Doors nicht in dieser Liste zeigt, wird diese Empfehlung aufgerufen.

Die Verwendung eines nicht optimalen Exchange Online Dienst-Front-Door könnte durch Netzwerk Backhaul vor dem Ausstieg des Unternehmensnetzwerks verursacht werden, in diesem Fall empfehlen wir den Ausstieg aus dem lokalen und direkten Netzwerk. Es kann auch durch die Verwendung eines Remote-DNS-rekursive Auflösungs Servers verursacht werden, in dem der Fall empfohlen wird, den DNS-rekursive Auflösungs Server mit dem Netzwerk Ausstieg auszurichten.

Diese Einblicke wird in einigen zusammenfassungsansichten als "Routing" abgekürzt.

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>Verwendung von nicht optimaler SharePoint Online Dienst-Haustür

Der Benutzer stellt keine Verbindung mit der nächstgelegenen SharePoint Online-Dienst-Haustür her. Dies wird voraussichtlich Auswirkungen auf die Leistung haben.

Wir identifizieren die SharePoint Online-Dienst-Haustür, mit der der Testclient eine Verbindung herstellt. Für die Office-Standort Stadt vergleichen wir dies mit der erwarteten SharePoint Online-Service-Haustür für diese Stadt. Wenn er nicht übereinstimmt, machen wir diese Empfehlung.

Diese Einblicke wird in einigen zusammenfassungsansichten als "ausschließend" abgekürzt.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Niedrige Downloadgeschwindigkeit von SharePoint-Haustür

Unter optimale Netzwerk Downloadgeschwindigkeit ermittelt, die Auswirkungen auf die Dauer hat, die zum Laden von Dokumenten aus OneDrive für Unternehmen benötigt wird.

Die Downloadgeschwindigkeit, die ein Benutzer von SharePoint Online-und OneDrive für Unternehmen-Dienst-Fronttüren erhalten kann, wird in Megabytes pro Sekunde (Mbps) gemessen. Wenn dieser Wert kleiner als 1 Mbit/s ist, stellen wir diese Einblicke bereit.

Um die Downloadgeschwindigkeit zu verbessern, die ein Benutzer Bandbreite erhalten kann, müssen Sie möglicherweise erhöht werden. Alternativ kann es zu Netzwerküberlastung zwischen Benutzercomputern am Office-Standort und der Front-Door-SharePoint Online Dienst geben. Dies wird manchmal als Überlastungs Verlust bezeichnet und schränkt die Downloadgeschwindigkeit ein, die Benutzern zur Verfügung steht, auch wenn genügend Bandbreite zur Verfügung steht.

Diese Einblicke wird in einigen zusammenfassungsansichten als "Durchsatz" abgekürzt.

## <a name="related-topics"></a>Verwandte Themen

[Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)](office-365-network-mac-perf-overview.md)

[Office 365 Netzwerkbewertung (Vorschau)](office-365-network-mac-perf-score.md)

[Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)](office-365-network-mac-perf-onboarding-tool.md)
