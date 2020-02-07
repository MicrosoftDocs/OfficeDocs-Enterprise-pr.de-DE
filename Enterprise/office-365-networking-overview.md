---
title: Office 365 – Überblick über die Netzwerkkonnektivität
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Erläutert, warum die Netzwerkoptimierung für SaaS-Dienste wichtig ist, das Ziel Office 365 Netzwerke und wie Saas unterschiedliche Netzwerke aus anderen Arbeitslasten benötigt.
ms.openlocfilehash: 3662ca913b78ef10b562defc2fefe62b89fd2ac0
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844356"
---
# <a name="office-365-network-connectivity-overview"></a>Office 365 Netzwerkkonnektivität (Übersicht)

*Dieser Artikel gilt sowohl für Office 365 Enterprise als auch Microsoft 365 Enterprise*.

Office 365 ist eine verteilte Software-as-a-Service-Cloud (SaaS), die Produktivitäts-und Zusammenarbeitsszenarien mithilfe verschiedener Mikro Dienste und Anwendungen bereitstellt. Client Komponenten von Office 365 wie Outlook, Word und PowerPoint werden auf Benutzercomputern ausgeführt und stellen eine Verbindung mit anderen Komponenten von Office 365 her, die in Microsoft-Rechenzentren ausgeführt werden. Der wichtigste Faktor, der die Qualität der Office 365 Endbenutzererfahrung bestimmt, ist die Zuverlässigkeit von Netzwerken und die niedrige Latenz zwischen Office 365-Clients und Office 365-Dienst-Front-Doors.

In diesem Artikel erfahren Sie mehr über die Ziele Office 365 Netzwerks und warum Office 365-Netzwerke einen anderen Ansatz für die Optimierung als generischer Internet Datenverkehr erfordert.

## <a name="office-365-networking-goals"></a>Office 365 von Netzwerkzielen

Das Endziel von Office 365 Vernetzung besteht darin, die Endbenutzerfreundlichkeit zu optimieren, indem der am wenigsten beschränkende Zugriff zwischen Clients und den nächstgelegenen Office 365 Endpunkten ermöglicht wird. Die Qualität der Endbenutzererfahrung steht in direktem Zusammenhang mit der Leistung und Reaktionsfähigkeit der Anwendung, die der Benutzer verwendet. Beispielsweise stützt sich Microsoft Teams auf eine geringe Wartezeit, sodass Benutzer Anrufe, Konferenzen und gemeinsame Bildschirm zusammenarbeiten glitch-frei sind und Outlook eine große Netzwerkkonnektivität für sofort Suchfeatures verwendet, die serverseitige Indizierung und AI nutzen. Funktionen.

Das primäre Ziel im Netzwerkentwurf sollte die Minimierung der Wartezeit sein, indem die Roundtripzeit (Round-Trip Time, RTT) von Clientcomputern auf das globale Microsoft-Netzwerk, das öffentliche Netzwerkbackbone von Microsoft, das alle Microsoft-Rechenzentren mit niedriger Latenz verbindet, verringert wird. , hoch verfügbare Cloud-Anwendungs Einstiegspunkte, die auf der ganzen Welt verteilt sind. Erfahren Sie mehr über das globale Microsoft-Netzwerk unter [So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Die Optimierung Office 365 Netzwerkleistung muss nicht kompliziert sein. Sie können die bestmögliche Leistung erzielen, indem Sie ein paar wichtige Grundsätze befolgen:

- Identifizieren Office 365 Netzwerkdatenverkehrs
- Lokale Verzweigung von Office 365 Netzwerkdatenverkehr zum Internet von jedem Standort aus zulassen, an dem sich Benutzer mit Office 365 verbinden
- Zulassen von Office 365 Datenverkehr zum Umgehen von Proxys und Paket Überprüfungs Geräten

Weitere Informationen zu Office 365 Prinzipien der Netzwerkkonnektivität finden Sie unter [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Herkömmliche Netzwerkarchitekturen und Saas

Die herkömmlichen Prinzipien der Netzwerkarchitektur für Client/Server-Arbeitsauslastungen sind auf die Annahme hin ausgelegt, dass sich der Datenverkehr zwischen Clients und Endpunkten nicht außerhalb des Umkreis Unternehmensnetzwerks erstreckt. Außerdem durchlaufen alle ausgehenden Internet Verbindungen in vielen Unternehmensnetzwerken das Unternehmensnetzwerk und gehen von einem zentralen Standort aus.

In herkömmlichen Netzwerkarchitekturen ist eine höhere Wartezeit für generischen Internetdatenverkehr ein notwendiger Kompromiss, um die Sicherheit des Netzwerkperimeters aufrechtzuerhalten, und die Leistungsoptimierung für den Internetdatenverkehr umfasst normalerweise ein Upgrade oder eine horizontale Skalierung des Geräte an Netzwerk Ausgangspunkten. Bei dieser Vorgehensweise werden jedoch nicht die Anforderungen für eine optimale Netzwerkleistung von Saas-Diensten wie Office 365 behandelt.

## <a name="identifying-office-365-network-traffic"></a>Identifizieren Office 365 Netzwerkdatenverkehrs

Wir machen es einfacher, Office 365 Netzwerkdatenverkehr zu identifizieren und es einfacher zu machen, die Netzwerkidentifikation zu verwalten.

- Neue Kategorien von Netzwerkendpunkten zur Unterscheidung von stark kritischem Netzwerkdatenverkehr vom Netzwerkdatenverkehr, der nicht von Internet Wartezeiten betroffen ist. Es gibt nur eine Handvoll URLs und unterstützende IP-Adressen in der kritischsten Kategorie "optimieren".
- Webdienste zur Skriptnutzung oder direkten Gerätekonfiguration und Änderungsverwaltung Office 365 Netzwerkidentifikation. Änderungen sind über den Webdienst oder im RSS-Format oder per e-Mail mit einer Microsoft-Fluss Vorlage verfügbar.
- [Office 365 Netzwerkpartnerprogramm](https://aka.ms/Office365NPP) mit Microsoft-Partnern, die Geräte oder Dienste bereitstellen, die Office 365 Netzwerk Verbindungs Prinzipien entsprechen und eine einfache Konfiguration aufweisen.

## <a name="securing-office-365-connections"></a>Sichern von Office 365 Verbindungen

Das Ziel der herkömmlichen Netzwerksicherheit ist die Absicherung des Unternehmensnetzwerkperimeters gegen Eindringversuche und böswillige Angriffe. Die meisten Unternehmensnetzwerke erzwingen die Netzwerksicherheit für den Internet Datenverkehr mithilfe von Technologien wie Proxyservern, Firewalls, SSL-Unterbrechung und-Prüfung, Deep Packet Inspection und Verhinderung von Datenverlust. Diese Technologien bieten eine wichtige Risikominderung für generische Internet Anforderungen, können jedoch die Leistung, die Skalierbarkeit und die Qualität der Endbenutzererfahrung drastisch reduzieren, wenn Sie auf Office 365 Endpunkte angewendet werden.

Office 365 hilft, die Anforderungen Ihrer Organisation an Inhaltssicherheit und Daten Nutzungs Konformität mit integrierten Sicherheits-und Steuerungsfeatures zu erfüllen, die speziell für Office 365 Features und Arbeitslasten entwickelt wurden. Weitere Informationen zur Office 365 Sicherheit und Compliance finden Sie in der [Office 365 Security Roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap). Weitere Informationen zu den Empfehlungen und der Unterstützung von Microsoft für erweiterte Netzwerklösungen, mit denen die Verarbeitung auf Office 365 Datenverkehr auf Erweiterter Ebene ausgeführt wird, finden Sie unter [Verwenden von Drittanbieter-Netzwerkgeräten oder Lösungen für Office 365 Datenverkehr](https://support.microsoft.com/help/2690045).

## <a name="why-is-office-365-networking-different"></a>Warum ist Office 365 Vernetzung unterschiedlich?

Office 365 wurde für eine optimale Leistung mithilfe von Endpunktsicherheit und verschlüsselten Netzwerkverbindungen entwickelt, wodurch die Notwendigkeit der Durchsetzung der Umkreis Sicherheit reduziert wird. Office 365 Rechenzentren befinden sich auf der ganzen Welt, und der Dienst ist für die Verwendung verschiedener Methoden zum Verbinden von Clients mit den besten verfügbaren Dienstendpunkten konzipiert. Da Benutzerdaten und-Verarbeitung zwischen vielen Microsoft-Rechenzentren verteilt werden, gibt es keinen einzelnen Netzwerkendpunkt, mit dem Clientcomputer eine Verbindung herstellen können. In der Tat werden Daten und Dienste in Ihrem Office 365 Mandanten vom Microsoft Global Network dynamisch so optimiert, dass Sie sich an die geografischen Standorte anpassen, von denen Endbenutzer auf Sie zugreifen.

Bestimmte allgemeine Leistungsprobleme werden erstellt, wenn Office 365 Datenverkehr der Paketüberprüfung und dem zentralisierten Ausstieg unterliegt:

- Hohe Latenz kann zu extrem schlechter Leistung von Video-und Audiostreams führen und eine langsame Antwort auf den Datenabruf, Suchvorgänge, Echtzeitzusammenarbeit, Kalender Frei/Gebucht-Informationen, produktbezogene Inhalte und andere Dienste verursachen.
- Egressing-Verbindungen von einem zentralen Standort aus besiegen die dynamischen Routingfunktionen des Office 365 globalen Netzwerks, indem Wartezeit und Roundtrip-Zeit hinzugefügt werden.
- Das Entschlüsseln von SSL-gesichertem Office 365 Netzwerkdatenverkehr und erneutes Verschlüsseln kann zu Protokollfehlern führen und ein Sicherheitsrisiko aufweisen.

Wenn Sie den Netzwerkpfad auf Office 365 Einstiegspunkte kürzen, indem Sie den Client Datenverkehr so nah wie möglich an ihren geografischen Standort abgeben lassen, kann dies die Konnektivitäts Leistung und die Endbenutzererfahrung in Office 365 verbessern. Sie kann auch dazu beitragen, die Auswirkungen künftiger Änderungen an der Netzwerkarchitektur auf Office 365 Leistung und Zuverlässigkeit zu reduzieren. Das optimale Verbindungsmodell besteht darin, den Netzwerk Ausstieg immer am Standort des Benutzers bereitzustellen, unabhängig davon, ob sich dies im Unternehmensnetzwerk oder an Remotestandorten wie Home, Hotels, Cafés und Flughäfen befindet. Allgemeiner Internet Datenverkehr und WAN-basierter Unternehmensnetzwerk Datenverkehr werden separat weitergeleitet und verwenden nicht das lokale Direct-Ausstieg-Modell. Dieses Modell mit lokalem direkten Ausgang ist in der nachstehenden Abbildung dargestellt.

![Netzwerkarchitektur mit lokalem Ausgang](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Die lokale Ausgangsarchitektur hat folgende Vorteile für Office 365 Netzwerkdatenverkehr über das herkömmliche Modell:
  
- Bietet optimale Office 365-Leistung durch optimale Routenlänge. Endbenutzer Verbindungen werden dynamisch an den nächstgelegenen Office 365 Einstiegspunkt über die _Front-Door_ -Infrastruktur des Microsoft Global-Netzwerks weitergeleitet, und der Datenverkehr wird dann intern an Daten-und Dienstendpunkte über die hoch Verfügbarkeits-Dark-Fiber von Microsoft mit hoher Verfügbarkeit weitergeleitet.
- Reduziert die Auslastung der Unternehmensnetzwerk Infrastruktur, indem lokale Ausgänge für Office 365 Datenverkehr zugelassen werden und Proxys und Datenverkehrs Kontrollgeräte umgangen werden.
- Sichert Verbindungen an beiden Enden, indem Client-Endpunktsicherheit und Cloud-Sicherheitsfunktionen genutzt werden, wodurch die Anwendung redundanter Netzwerksicherheitstechnologien vermieden wird.

> [!NOTE]
> Die _verteilte Dienst-Front-Door_ -Infrastruktur ist die hoch verfügbare und skalierbare Netzwerk Kante des Microsoft Global Netzwerks mit geografisch verteilten Standorten. Sie beendet Endbenutzer Verbindungen und leitet Sie effizient innerhalb des globalen Netzwerks von Microsoft weiter. Erfahren Sie mehr über das globale Microsoft-Netzwerk unter [So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Weitere Informationen zum Verständnis und zur Anwendung Office 365 Prinzipien der Netzwerkkonnektivität finden Sie unter [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Schlussbemerkung

Die Optimierung Office 365 Netzwerkleistung ist wirklich auf das Entfernen unnötiger Hindernisse beschränkt. Durch das Behandeln von Office 365 Verbindungen als vertrauenswürdigen Datenverkehr können Sie verhindern, dass die Wartezeit durch die Paketüberprüfung und den Wettbewerb um die Proxy Bandbreite eingeführt wird. Durch das zulassen lokaler Verbindungen zwischen Clientcomputern und Office 365 Endpunkten kann der Datenverkehr dynamisch über das globale Microsoft-Netzwerk weitergeleitet werden.

## <a name="related-topics"></a>Verwandte Themen

[Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)

[Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md)

[URLs und IP-Adressbereiche für Office 365](urls-and-ip-address-ranges.md)

[Office 365 – IP-Adress- und URL-Webdienst](office-365-ip-web-service.md)

[Bewerten der Office 365-Netzwerkkonnektivität](assessing-network-connectivity.md)

[Office 365-Netzwerk- und Leistungsoptimierung](network-planning-and-performance.md)

[Bewerten der Office 365-Netzwerkkonnektivität](assessing-network-connectivity.md)

[Office 365-Leistungsoptimierung mit Basisplänen und Leistungsverlauf](performance-tuning-using-baselines-and-history.md)

[Plan zur Problembehandlung für Office 365](performance-troubleshooting-plan.md)

[Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)

[Office 365 Network Onboarding Tool](https://aka.ms/netonboard)

[So erstellt Microsoft sein schnelles und zuverlässiges globales Netzwerk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365-Networking-Blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
