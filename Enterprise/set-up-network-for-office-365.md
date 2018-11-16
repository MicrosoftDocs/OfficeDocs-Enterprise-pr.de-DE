---
title: Einrichten Ihres Netzwerks für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Zusammenfassung: Lesen Sie diese Artikel, um mehr über das Netzwerk von Office 365 zu erfahren.'
ms.openlocfilehash: 10f5742e8fc38af49df95e98c4f512eeddc9377f
ms.sourcegitcommit: b94bd747d0797a5889294f4794e8cfc0310f5539
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "26034886"
---
# <a name="set-up-your-network-for-office-365"></a>Einrichten Ihres Netzwerks für Office 365

**Zusammenfassung:** Lesen Sie diese Artikel, um mehr über das Netzwerk von Office 365 zu erfahren.
  
Ein wichtiger Bestandteil Ihres Office 365-Onboarding ist sicherzustellen, dass Ihr Netzwerk und Ihre Internetverbindungen für den optimalen Zugriff eingerichtet sind. Das Konfigurieren Ihres lokalen Netzwerks für den Zugriff auf eine global verbreitete Software-as-a-Service (SaaS) Cloud unterscheidet sich von einem herkömmlichen Netzwerk, das für den Datenverkehr in lokalen Datencentern optimiert ist. 

Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edge-Geräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Benutzerleistung zu erreichen.

## <a name="how-office-365-networking-works"></a>Funktionsweise von Office 365-Netzwerk

In den folgenden Artikeln erhalten Sie eine Übersicht über die Konnektivität von Office 365:

- [Office 365 – Überblick über die Netzwerkkonnektivität](office-365-networking-overview.md)
- [Prinzipien von Office 365-Netzwerkverbindungen](office-365-network-connectivity-principles.md)
- [Netzwerkkonnektivität mit Office 365](network-connectivity.md)

Hinweise zur Verbesserung der Leistung, finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Unterstützen Sie das Office 365-Netzwerk als Lieferant von Netzwerkgeräten

Wenn Sie ein Lieferant von Netzwerkgeräten sind, treten Sie dem [Office 365-Netzwerk-Partnerprogramm](office-365-networking-partner-program.md) bei. Registrieren Sie sich für das Programm, um Kennektivitätsprinzipien von Office 365-Netzwerken in Ihre Produkte und Lösungen zu integrieren. 

## <a name="office-365-endpoints"></a>Office 365-Endpunkte

Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet. 

Zum Optimieren der Leistung von auf Office 365-Cloud basierten Diensten benötigen diese Endpunkte besondere Behandlung durch Ihre Clientbrowser und die Geräte in Ihrem Edge-Netzwerk. Diese Geräten umfassen Firewalls, SSL Unterbrechung und Überprüfung, Paketüberprüfungsgeräte und Datensysteme Schutz vor Datenverlust.

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


## <a name="additional-topics-for-office-365-networking"></a>Weitere Themen zu Office 365-Netzwerk

Die folgenden Artikel behandeln spezielle Themen zum Office 365-Netzwerk:

- [Netzwerke für die Inhaltsübermittlung](content-delivery-networks.md)
- [IPv6-Unterstützung in Office 365-Diensten](ipv6-support.md)
- [NAT-Unterstützung bei Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute für Office 365

In den folgenden Artikeln finden Sie Informationen über die Verwendung von ExpressRoute für Office 365-Datenverkehr:

- [Azure ExpressRoute für Office 365](azure-expressroute.md)
- [Implementierung von ExpressRoute für Office 365](implementing-expressroute.md)
- [Netzwerkplanung mit ExpressRoute für Office 365](network-planning-with-expressroute.md)
- [Routing mit ExpressRoute für Office 365](routing-with-expressroute.md)
