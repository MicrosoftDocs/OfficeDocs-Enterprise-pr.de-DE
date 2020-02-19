---
title: Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)
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
description: Übersicht über Netzwerk Leistungsempfehlungen im Microsoft 365 Admin Center (Vorschau)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106328"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)

Die Seite Netzwerkleistung im Microsoft 365 Admin Center zeigt Netzwerk Einblicke und eine Netzwerkbewertung für Unternehmenskunden an. Network Insights sind spezifische empfohlene Änderungen an der Netzwerkarchitektur zur Verbesserung der Benutzerfreundlichkeit im Zusammenhang mit der Netzwerkkonnektivität mit Office 365 und die Netzwerkbewertung zeigt, wie sich die Netzwerkkonnektivität auf die Benutzeroberfläche auswirkt und den Vergleich von unterschiedliche Netzwerkverbindungen für Benutzer Standorte. Unternehmen, die Office 365 mit mehreren Office-Standorten und nicht-trivialen Netzwerkperimeter-Architekturen verwenden, können davon profitieren, entweder während des ersten onboardings in Office 365 oder um Netzwerkleistungsprobleme zu beheben, die mit der Verwendung ermittelt wurden. Wachstums. Dies ist normalerweise nicht erforderlich für kleine Unternehmen, die Office 365 verwenden, oder für Unternehmen, die bereits über eine einfache und direkte Netzwerkkonnektivität verfügen. Unternehmen mit mehr als 500 Benutzern und mehreren Office-Standorten werden davon ausgehen.

>[!IMPORTANT]
>Empfehlungen zur Netzwerkleistung, Einblicke und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.

## <a name="enterprise-network-connectivity-challenges"></a>Herausforderungen bei der Unternehmensnetzwerk Konnektivität

![Kundennetzwerk in Cloud](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Viele Unternehmen verfügen über Netzwerkumkreis Konfigurationen, die im Laufe der Zeit gewachsen sind und in erster Linie für den Zugriff von Internetwebsites für Mitarbeiter vorgesehen sind, bei denen die meisten Websites nicht vorab bekannt sind und nicht vertrauenswürdig sind. Der vorherrschende und notwendige Fokus besteht darin, Schadsoftware und Angel Angriffe aus diesen unbekannten Websites zu vermeiden. Diese Strategie für die Netzwerkkonfiguration, die aus Sicherheitsgründen hilfreich ist, kann zu Beeinträchtigungen Office 365 Benutzerleistung und Benutzerfreundlichkeit führen. Unternehmen können die Benutzerfreundlichkeit verbessern, aber auch weiterhin ihre Umgebung schützen, indem Sie [Office 365 Konnektivitäts Prinzipien](https://aka.ms/pnc) und in Kürze das neue Netzwerk Leistungsfeature von Microsoft 365 Admin Center verwenden. Dieses Feature unterstützt den Entwurf der Netzwerkarchitektur, der mit den Grundsätzen der Office 365 Konnektivität übereinstimmt und zu einer optimierten Netzwerkleistung für die Konnektivität mit Office 365 führen sollte.

## <a name="how-we-can-solve-these-challenges"></a>Wie können wir diese Herausforderungen lösen?

Microsoft wird manchmal aufgefordert, Netzwerkleistungsprobleme mit Office 365 für große Unternehmenskunden zu untersuchen, und diese weisen häufig eine Hauptursache im Zusammenhang mit der Netzwerk Ausgangs Infrastruktur des Kunden auf. Wenn eine allgemeine Ursache für ein Problem mit dem Umkreis eines Kunden Netzwerks gefunden wird, versuchen wir, einfache Testmessungen zu identifizieren, die diese identifizieren. Ein Test mit einem Schwellenwert für die Messung, mit dem ein bestimmtes Problem identifiziert wird, ist wertvoll, da wir dieselbe Messung an einem beliebigen Ort testen können, um zu ermitteln, ob diese Ursache dort vorhanden ist, und Sie als Netzwerk Einblicke mit dem Administrator freigeben. Einige Netzwerk Einblicke deuten lediglich auf ein Problem hin, das weiter untersucht werden muss. Ein Netzwerk Einblicke, in dem genügend Tests vorhanden sind, um eine bestimmte Korrekturaktion zur Behebung der Stamm Ursache anzuzeigen, wird als empfohlene Aktion aufgeführt. Diese Netzwerk Einblicke basierend auf Messungen über einen vorher festgelegten Schwellenwert sind weitaus wertvoller als allgemeine Ratschläge zur bewährten Vorgehensweise, da Sie nicht Fragen müssen, ob bestimmte bewährte Methoden zutreffen und eine erhebliche Verbesserung der Benutzerfreundlichkeit zur Folge haben oder nicht. .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Übersicht über die Netzwerkleistung im Microsoft 365 Admin Center

Microsoft verfügt über vorhandene Netzwerk Messungen aus mehreren Office-Desktop-und Webclients, die den Betrieb von Office 365 unterstützen. Diese Messungen werden nun verwendet, um Einblicke in die Netzwerkarchitektur und eine Netzwerk Leistungsbewertung bereitzustellen, die auf der Seite "Netzwerkleistung" im Microsoft 365 Admin Center angezeigt werden.

Ungefähre Standortinformationen im Zusammenhang mit den Netzwerk Messungen können den Ort identifizieren, an dem sich die Clientgeräte befinden. Dies wird verwendet, um die Kundenbüro Standorte und Netzwerk Messungen sind gruppiert, um Netzwerk Einblicke für diesen Standort bieten. Die Netzwerkbewertung an jedem Standort wird mit Farbe angezeigt, und die relative Anzahl der Benutzer an jedem Standort wird durch die Größe des Kreises dargestellt. Auf der Übersichtsseite wird auch die Netzwerkbewertung für den Kunden als gewichteter Durchschnitt für alle Office-Standorte angezeigt.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Übersicht über die spezifische Netzwerkleistung für Office-Standorte und Einblicke

Durch die Auswahl eines Office-Standorts wird eine standortspezifische Zusammenfassungsseite geöffnet. Wir zeigen Details des Netzwerk Ausstiegs an, die von Messungen an diesem Standort identifiziert wurden.

Auf der Seite Zusammenfassung der Office-standortzusammenfassung werden außerdem die Netzwerkbewertung der Standorte, das Netzwerk Bewertungs Protokoll, ein Vergleich dieser Punkte mit anderen Kunden in der gleichen Stadt sowie eine Liste mit spezifischen Einblicken und Empfehlungen angezeigt, die der Kunde ausführen kann, um verbessern Sie die Netzwerkkonnektivität. Vergleiche zwischen Kunden in der gleichen Stadt basieren auf der Erwartung, dass alle Kunden gleichberechtigten Zugriff auf Netzwerkdienstanbieter, Telekommunikationsinfrastruktur und in der Nähe befindliche Microsoft-Netzwerk Points of Presence haben.

Auf der Registerkarte "Details" auf der Seite "Office-Standort" werden die spezifischen Messergebnisse angezeigt, die verwendet wurden, um Einblicke, Empfehlungen und das Netzwerk Ergebnis einzuholen. Dies wird bereitgestellt, damit Netzwerkingenieure die Empfehlungen und den Faktor für Einschränkungen oder Besonderheiten in Ihrer Umgebung überprüfen können.
Für Kunden, die die Genauigkeit von Office-Standorten und Empfehlungen verbessern möchten, können Sie spezifischere Informationen eingeben. Dies erfolgt durch Bearbeiten der Informationen über den ermittelten Standort und kann die Näherungswerte verringern, die in den Standortinformationen für Netzwerk Messungen vorhanden sind.

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="what-is-office-365-service-front-door"></a>Was ist Office 365-Service-Haustür?

Die Office 365-Dienst-Haustür ist ein Einstiegspunkt im globalen Microsoft-Netzwerk, in dem Office-Clients und-Dienste Ihre Netzwerkverbindung beenden. Für eine optimale Netzwerkverbindung mit Office 365 wird empfohlen, dass Ihre Netzwerkverbindung an der nächstgelegenen Office 365 Haustür in ihrer Stadt oder Metro endet.
Hinweis: Office 365-Dienst-Haustür verfügt über keine direkte Beziehung zum "Azure Front Door Service"-Produkt, das im Azure Marketplace zur Verfügung steht.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>Was ist eine optimale Office 365-Dienst Haustür?

Eine optimale Office 365 Dienst Haustür ist eine, die Ihrem Netzwerk Austritt am nächsten ist, in der Regel in ihrer Stadt oder Metro. Verwenden Sie das Office 365 Netzwerk-Leistungstool, um die Position der Haustür Ihres in-Use-Office 365 Diensts und der optimalen Service-Haustür zu bestimmen. Wenn das Tool feststellt, dass Ihre in-use-Haustür optimal ist, verbinden Sie sich optimal mit dem globalen Netzwerk von Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Was ist ein Internet Ausstieg-Standort?

Der Internet Ausgangsstandort ist der Ort, an dem Ihr Netzwerkdatenverkehr Ihr Unternehmensnetzwerk verlässt und eine Verbindung mit dem Internet herstellt. Dies wird auch als Standort bezeichnet, an dem Sie ein NAT-Gerät (Network Address Translation, Netzwerkadressübersetzung) haben und in der Regel eine Verbindung mit einem Internetdienstanbieter (Internet Service Provider, ISP) herstellen. Wenn Sie einen langen Abstand zwischen Ihrem Standort und Ihrem Internet Ausgangsstandort sehen, kann dies eine erhebliche WAN-Backhaul erkennen.

## <a name="related-topics"></a>Verwandte Themen

[Office 365 Einblicke in die Netzwerkleistung (Vorschau)](office-365-network-mac-perf-insights.md)

[Office 365 Netzwerkbewertung (Vorschau)](office-365-network-mac-perf-score.md)

[Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)](office-365-network-mac-perf-onboarding-tool.md)
