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
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="1bfd3-103">Einrichten Ihres Netzwerks für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="1bfd3-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="1bfd3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1bfd3-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span></span> <span data-ttu-id="1bfd3-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="1bfd3-107">Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edgegeräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Leistung für Ihre lokalen Benutzer zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="1bfd3-108">Funktionsweise von Microsoft 365-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="1bfd3-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="1bfd3-109">In diesen Artikeln finden Sie eine Übersicht über die Konnektivität für Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="1bfd3-110">Microsoft 365 – Überblick über die Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="1bfd3-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="1bfd3-111">Microsoft 365-Prinzipien für die Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="1bfd3-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="1bfd3-112">Bewerten der Microsoft 365-Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="1bfd3-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="1bfd3-113">Ratschläge zur Verbesserung der Leistung finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="1bfd3-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="1bfd3-114">Unterstützung von Microsoft 365 Networking als Netzwerkgeräte Anbieter</span><span class="sxs-lookup"><span data-stu-id="1bfd3-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="1bfd3-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span><span class="sxs-lookup"><span data-stu-id="1bfd3-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span> <span data-ttu-id="1bfd3-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="1bfd3-117">Office 365-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="1bfd3-117">Office 365 endpoints</span></span>

<span data-ttu-id="1bfd3-118">Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="1bfd3-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span></span> <span data-ttu-id="1bfd3-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="1bfd3-121">Weitere Details finden Sie unter [ Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="1bfd3-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="1bfd3-122">There are currently five different Office 365 clouds.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-122">There are currently five different Office 365 clouds.</span></span> <span data-ttu-id="1bfd3-123">This table takes you to the list of endpoints for each one.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-123">This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="1bfd3-124">Weltweite Endpunkte</span><span class="sxs-lookup"><span data-stu-id="1bfd3-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="1bfd3-125">Die Endpunkte für weltweite Office 365-Abonnements, welche die United States Government Community Cloud (GCC) umfassen.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="1bfd3-126">DoD-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="1bfd3-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="1bfd3-127">Die Endpunkte für United States Department of Defense (DoD)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="1bfd3-128">GCC High-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="1bfd3-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="1bfd3-129">Die Endpunkte für United States Government Community Cloud High (GCC High)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="1bfd3-130">Endpunkte von Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="1bfd3-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="1bfd3-131">Die Endpunkte für Office 365 betrieben von 21Vianet, das darauf ausgelegt ist, den Anforderungen für Office 365 in China zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="1bfd3-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="1bfd3-132">Endpunkte für Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="1bfd3-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="1bfd3-133">Die Endpunkte für eine separate Cloud in Europa für die meisten regulierten Kunden in Deutschland, der Europäischen Union (EU) und der Europäischen Freihandelszone (EFTA).</span><span class="sxs-lookup"><span data-stu-id="1bfd3-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="1bfd3-134">Informationen über das automatische Abrufen der neuesten Liste der Endpunkte für Ihre Office 365-Cloud finden Sie unter [Office 365-IP-Adresse und URL-Web-Dienst](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="1bfd3-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="1bfd3-135">Weitere Informationen über zusätzliche Endpunkte finden Sie in folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="1bfd3-136">Zusätzliche, nicht in den Webdiensten enthaltene Endpunkte</span><span class="sxs-lookup"><span data-stu-id="1bfd3-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="1bfd3-137">Netzwerkanforderungen in Office 2016 für Mac</span><span class="sxs-lookup"><span data-stu-id="1bfd3-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="1bfd3-138">Weitere Themen für Microsoft 365 Networking</span><span class="sxs-lookup"><span data-stu-id="1bfd3-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="1bfd3-139">In diesen Artikeln finden Sie spezielle Themen in Microsoft 365 Networking:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="1bfd3-140">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="1bfd3-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="1bfd3-141">IPv6-Unterstützung in Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="1bfd3-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="1bfd3-142">NAT-Unterstützung bei Office 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="1bfd3-143">ExpressRoute für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="1bfd3-144">In den folgenden Artikeln finden Sie Informationen über die Verwendung von ExpressRoute für Office 365-Datenverkehr:</span><span class="sxs-lookup"><span data-stu-id="1bfd3-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="1bfd3-145">Azure ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="1bfd3-146">Implementierung von ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="1bfd3-147">Netzwerkplanung mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="1bfd3-148">Routing mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="1bfd3-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
