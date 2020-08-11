---
title: Einrichten Ihres Netzwerks für Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Hier finden Sie Links zu Artikeln mit Informationen, die Sie beim Einrichten Ihres Netzwerks für Microsoft 365 unterstützen, einschließlich einer Übersicht über die Netzwerkkonnektivität und einer Liste der Endpunkte.
ms.openlocfilehash: 2c5966dc169a189a4f5040d4b5673859a38e6640
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605207"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Einrichten Ihres Netzwerks für Microsoft 365

*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*

Ein wichtiger Bestandteilihres Microsoft 365-onboardings besteht darin, sicherzustellen, dass Ihre Netzwerk-und Internet Verbindungen für einen optimierten Zugriff eingerichtet sind. Das Konfigurieren Ihres lokalen Netzwerks für den Zugriff auf eine global verteilte Software-as-a-Service (SaaS)-Cloud unterscheidet sich von einem herkömmlichen Netzwerk, das für den Datenverkehr zu lokalen Rechenzentren und einer zentralen Internet Verbindung optimiert ist. 

Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edgegeräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Leistung für Ihre lokalen Benutzer zu erreichen.

## <a name="how-microsoft-365-networking-works"></a>Funktionsweise von Microsoft 365-Netzwerk

In diesen Artikeln finden Sie eine Übersicht über die Konnektivität für Microsoft 365:

- [Microsoft 365 – Überblick über die Netzwerkkonnektivität](office-365-networking-overview.md)
- [Microsoft 365-Prinzipien für die Netzwerkkonnektivität](office-365-network-connectivity-principles.md)
- [Bewerten der Microsoft 365-Netzwerkkonnektivität](assessing-network-connectivity.md)

Ratschläge zur Verbesserung der Leistung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Unterstützung von Microsoft 365 Networking als Netzwerkgeräte Anbieter

Wenn Sie ein Lieferant von Netzwerkgeräten sind, treten Sie dem [Office 365-Netzwerk-Partnerprogramm](office-365-networking-partner-program.md) bei. Registrieren Sie sich für das Programm, um Kennektivitätsprinzipien von Office 365-Netzwerken in Ihre Produkte und Lösungen zu integrieren. 

## <a name="office-365-endpoints"></a>Office 365-Endpunkte

Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet. 

Zum Optimieren der Leistung von auf Office 365-Cloud basierten Diensten benötigen einige Endpunkte besondere Behandlung durch Ihre Clientbrowser und die Geräte in Ihrem Umkreisnetzwerk. Diese Geräten umfassen Firewalls, SSL Unterbrechung und Überprüfung, Paketüberprüfungsgeräte und Datensysteme Schutz vor Datenverlust.

Weitere Details finden Sie unter [ Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).

Es gibt derzeit fünf verschiedene Office 365-Clouds. Über diese Tabelle gelangen Sie zur Liste der jeweiligen Endpunkte.

|||
|:-------|:-----|
| [Weltweite Endpunkte](urls-and-ip-address-ranges.md) | Die Endpunkte für weltweite Office 365-Abonnements, welche die United States Government Community Cloud (GCC) umfassen. |
| [DoD-Endpunkte für US Government](office-365-u-s-government-dod-endpoints.md) | Die Endpunkte für United States Department of Defense (DoD)-Abonnements. |
| [GCC High-Endpunkte für US Government](office-365-u-s-government-gcc-high-endpoints.md) | Die Endpunkte für United States Government Community Cloud High (GCC High)-Abonnements. |
| [Endpunkte von Office 365, betrieben von 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Die Endpunkte für Office 365 betrieben von 21Vianet, das darauf ausgelegt ist, den Anforderungen für Office 365 in China zu erfüllen. |
| [Endpunkte für Office 365 Deutschland](office-365-germany-endpoints.md) | Die Endpunkte für eine separate Cloud in Europa für die meisten regulierten Kunden in Deutschland, der Europäischen Union (EU) und der Europäischen Freihandelszone (EFTA). |
|||

Informationen über das automatische Abrufen der neuesten Liste der Endpunkte für Ihre Office 365-Cloud finden Sie unter [Office 365-IP-Adresse und URL-Web-Dienst](office-365-ip-web-service.md).

Weitere Informationen über zusätzliche Endpunkte finden Sie in folgenden Artikeln:

- [Zusätzliche, nicht in den Webdiensten enthaltene Endpunkte](additional-office365-ip-addresses-and-urls.md)
- [Netzwerkanforderungen in Office 2016 für Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Weitere Themen für Microsoft 365 Networking

In diesen Artikeln finden Sie spezielle Themen in Microsoft 365 Networking:

- [Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
- [IPv6-Unterstützung in Office 365-Diensten](ipv6-support.md)
- [NAT-Unterstützung bei Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute für Microsoft 365

In den folgenden Artikeln finden Sie Informationen über die Verwendung von ExpressRoute für Office 365-Datenverkehr:

- [Azure ExpressRoute für Office 365](azure-expressroute.md)
- [Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
- [Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
- [Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
