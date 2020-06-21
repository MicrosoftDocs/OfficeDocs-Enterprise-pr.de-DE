---
title: Einrichten Ihres Netzwerks für Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Zusammenfassung: in diesen Artikeln erfahren Sie, wie Sie Netzwerke für Microsoft 365 verstehen.'
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735657"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Einrichten Ihres Netzwerks für Microsoft 365

*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*

An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection. 

Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edgegeräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Leistung für Ihre lokalen Benutzer zu erreichen.

## <a name="how-microsoft-365-networking-works"></a>Funktionsweise von Microsoft 365-Netzwerk

In diesen Artikeln finden Sie eine Übersicht über die Konnektivität für Microsoft 365:

- [Microsoft 365 – Überblick über die Netzwerkkonnektivität](office-365-networking-overview.md)
- [Microsoft 365-Prinzipien für die Netzwerkkonnektivität](office-365-network-connectivity-principles.md)
- [Bewerten der Microsoft 365-Netzwerkkonnektivität](assessing-network-connectivity.md)

Ratschläge zur Verbesserung der Leistung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Unterstützung von Microsoft 365 Networking als Netzwerkgeräte Anbieter

If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions. 

## <a name="office-365-endpoints"></a>Office 365-Endpunkte

Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet. 

To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.

Weitere Details finden Sie unter [ Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).

There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.

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
