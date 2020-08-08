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
ms.assetid: ''
description: 'Zusammenfassung: in diesen Artikeln erfahren Sie, wie Sie Netzwerke für Microsoft 365 verstehen.'
ms.openlocfilehash: b1497c214777e34ce4a85701ce6596f50e59910d
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592149"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="e56fc-103">Einrichten Ihres Netzwerks für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="e56fc-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="e56fc-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e56fc-p101">Ein wichtiger Bestandteilihres Microsoft 365-onboardings besteht darin, sicherzustellen, dass Ihre Netzwerk-und Internet Verbindungen für einen optimierten Zugriff eingerichtet sind. Das Konfigurieren Ihres lokalen Netzwerks für den Zugriff auf eine global verteilte Software-as-a-Service (SaaS)-Cloud unterscheidet sich von einem herkömmlichen Netzwerk, das für den Datenverkehr zu lokalen Rechenzentren und einer zentralen Internet Verbindung optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="e56fc-p101">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="e56fc-107">Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edgegeräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Leistung für Ihre lokalen Benutzer zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="e56fc-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="e56fc-108">Funktionsweise von Microsoft 365-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="e56fc-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="e56fc-109">In diesen Artikeln finden Sie eine Übersicht über die Konnektivität für Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="e56fc-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="e56fc-110">Microsoft 365 – Überblick über die Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="e56fc-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="e56fc-111">Microsoft 365-Prinzipien für die Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="e56fc-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="e56fc-112">Bewerten der Microsoft 365-Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="e56fc-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="e56fc-113">Ratschläge zur Verbesserung der Leistung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="e56fc-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="e56fc-114">Unterstützung von Microsoft 365 Networking als Netzwerkgeräte Anbieter</span><span class="sxs-lookup"><span data-stu-id="e56fc-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="e56fc-p102">Wenn Sie ein Lieferant von Netzwerkgeräten sind, treten Sie dem [Office 365-Netzwerk-Partnerprogramm](office-365-networking-partner-program.md) bei. Registrieren Sie sich für das Programm, um Kennektivitätsprinzipien von Office 365-Netzwerken in Ihre Produkte und Lösungen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="e56fc-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="e56fc-117">Office 365-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e56fc-117">Office 365 endpoints</span></span>

<span data-ttu-id="e56fc-118">Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet.</span><span class="sxs-lookup"><span data-stu-id="e56fc-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="e56fc-p103">Zum Optimieren der Leistung von auf Office 365-Cloud basierten Diensten benötigen einige Endpunkte besondere Behandlung durch Ihre Clientbrowser und die Geräte in Ihrem Umkreisnetzwerk. Diese Geräten umfassen Firewalls, SSL Unterbrechung und Überprüfung, Paketüberprüfungsgeräte und Datensysteme Schutz vor Datenverlust.</span><span class="sxs-lookup"><span data-stu-id="e56fc-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="e56fc-121">Weitere Details finden Sie unter [ Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="e56fc-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="e56fc-p104">Es gibt derzeit fünf verschiedene Office 365-Clouds. Über diese Tabelle gelangen Sie zur Liste der jeweiligen Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="e56fc-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="e56fc-124">Weltweite Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e56fc-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="e56fc-125">Die Endpunkte für weltweite Office 365-Abonnements, welche die United States Government Community Cloud (GCC) umfassen.</span><span class="sxs-lookup"><span data-stu-id="e56fc-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="e56fc-126">DoD-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="e56fc-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="e56fc-127">Die Endpunkte für United States Department of Defense (DoD)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="e56fc-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="e56fc-128">GCC High-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="e56fc-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="e56fc-129">Die Endpunkte für United States Government Community Cloud High (GCC High)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="e56fc-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="e56fc-130">Endpunkte von Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e56fc-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="e56fc-131">Die Endpunkte für Office 365 betrieben von 21Vianet, das darauf ausgelegt ist, den Anforderungen für Office 365 in China zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="e56fc-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="e56fc-132">Endpunkte für Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="e56fc-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="e56fc-133">Die Endpunkte für eine separate Cloud in Europa für die meisten regulierten Kunden in Deutschland, der Europäischen Union (EU) und der Europäischen Freihandelszone (EFTA).</span><span class="sxs-lookup"><span data-stu-id="e56fc-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="e56fc-134">Informationen über das automatische Abrufen der neuesten Liste der Endpunkte für Ihre Office 365-Cloud finden Sie unter [Office 365-IP-Adresse und URL-Web-Dienst](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="e56fc-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="e56fc-135">Weitere Informationen über zusätzliche Endpunkte finden Sie in folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="e56fc-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="e56fc-136">Zusätzliche, nicht in den Webdiensten enthaltene Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e56fc-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="e56fc-137">Netzwerkanforderungen in Office 2016 für Mac</span><span class="sxs-lookup"><span data-stu-id="e56fc-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="e56fc-138">Weitere Themen für Microsoft 365 Networking</span><span class="sxs-lookup"><span data-stu-id="e56fc-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="e56fc-139">In diesen Artikeln finden Sie spezielle Themen in Microsoft 365 Networking:</span><span class="sxs-lookup"><span data-stu-id="e56fc-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="e56fc-140">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="e56fc-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="e56fc-141">IPv6-Unterstützung in Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="e56fc-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="e56fc-142">NAT-Unterstützung bei Office 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="e56fc-143">ExpressRoute für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="e56fc-144">In den folgenden Artikeln finden Sie Informationen über die Verwendung von ExpressRoute für Office 365-Datenverkehr:</span><span class="sxs-lookup"><span data-stu-id="e56fc-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="e56fc-145">Azure ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="e56fc-146">Implementierung von ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="e56fc-147">Netzwerkplanung mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="e56fc-148">Routing mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="e56fc-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
