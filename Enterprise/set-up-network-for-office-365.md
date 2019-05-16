---
title: Einrichten Ihres Netzwerks für Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Zusammenfassung: Lesen Sie diese Artikel, um mehr über das Netzwerk von Office 365 zu erfahren.'
ms.openlocfilehash: 6fb1d4d441719f61886b9263b30cdf27cbe7eaf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070821"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="0eb3a-103">Einrichten Ihres Netzwerks für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-103">Set up your network for Office 365</span></span>

<span data-ttu-id="0eb3a-104">**Zusammenfassung:** Lesen Sie diese Artikel, um mehr über das Netzwerk von Office 365 zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="0eb3a-p101">Ein wichtiger Bestandteil Ihres Office 365-Onboarding ist sicherzustellen, dass Ihr Netzwerk und Ihre Internetverbindungen für den optimalen Zugriff eingerichtet sind. Das Konfigurieren Ihres lokalen Netzwerks für den Zugriff auf eine global verbreitete Software-as-a-Service (SaaS) Cloud unterscheidet sich von einem herkömmlichen Netzwerk, das für den Datenverkehr in lokalen Datencentern optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="0eb3a-107">Lesen Sie diese Artikel, um die wichtigsten Unterschiede zu verstehen und um Ihre Edge-Geräte, Clientcomputer und lokalen Netzwerk zu ändern, um die beste Benutzerleistung zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="0eb3a-108">Funktionsweise von Office 365-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="0eb3a-108">How Office 365 networking works</span></span>

<span data-ttu-id="0eb3a-109">In den folgenden Artikeln erhalten Sie eine Übersicht über die Konnektivität von Office 365:</span><span class="sxs-lookup"><span data-stu-id="0eb3a-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="0eb3a-110">Office 365 – Überblick über die Netzwerkkonnektivität</span><span class="sxs-lookup"><span data-stu-id="0eb3a-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="0eb3a-111">Prinzipien von Office 365-Netzwerkverbindungen</span><span class="sxs-lookup"><span data-stu-id="0eb3a-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="0eb3a-112">Netzwerkkonnektivität mit Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-112">Network connectivity to Office 365</span></span>](network-connectivity.md)

<span data-ttu-id="0eb3a-113">Hinweise zur Verbesserung der Leistung, finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="0eb3a-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="0eb3a-114">Unterstützen Sie das Office 365-Netzwerk als Lieferant von Netzwerkgeräten</span><span class="sxs-lookup"><span data-stu-id="0eb3a-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="0eb3a-p102">Wenn Sie ein Lieferant von Netzwerkgeräten sind, treten Sie dem [Office 365-Netzwerk-Partnerprogramm](office-365-networking-partner-program.md) bei. Registrieren Sie sich für das Programm, um Kennektivitätsprinzipien von Office 365-Netzwerken in Ihre Produkte und Lösungen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="0eb3a-117">Office 365-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="0eb3a-117">Office 365 endpoints</span></span>

<span data-ttu-id="0eb3a-118">Endpunkte sind die Gruppe von Ziel-IP-Adressen, DNS-Domänennamen und URLs für Office 365-Datenverkehr über das Internet.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="0eb3a-p103">Zum Optimieren der Leistung von auf Office 365-Cloud basierten Diensten benötigen diese Endpunkte besondere Behandlung durch Ihre Clientbrowser und die Geräte in Ihrem Edge-Netzwerk. Diese Geräten umfassen Firewalls, SSL Unterbrechung und Überprüfung, Paketüberprüfungsgeräte und Datensysteme Schutz vor Datenverlust.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="0eb3a-121">Weitere Details finden Sie unter [ Verwalten von Office 365-Endpunkten](managing-office-365-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="0eb3a-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="0eb3a-p104">Es gibt derzeit fünf verschiedene Office 365-Clouds. Über diese Tabelle gelangen Sie zur Liste der jeweiligen Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="0eb3a-124">Weltweite Endpunkte</span><span class="sxs-lookup"><span data-stu-id="0eb3a-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="0eb3a-125">Die Endpunkte für weltweite Office 365-Abonnements, welche die United States Government Community Cloud (GCC) umfassen.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="0eb3a-126">DoD-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="0eb3a-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="0eb3a-127">Die Endpunkte für United States Department of Defense (DoD)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="0eb3a-128">GCC High-Endpunkte für US Government</span><span class="sxs-lookup"><span data-stu-id="0eb3a-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="0eb3a-129">Die Endpunkte für United States Government Community Cloud High (GCC High)-Abonnements.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="0eb3a-130">Endpunkte von Office 365, betrieben von 21Vianet</span><span class="sxs-lookup"><span data-stu-id="0eb3a-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="0eb3a-131">Die Endpunkte für Office 365 betrieben von 21Vianet, das darauf ausgelegt ist, den Anforderungen für Office 365 in China zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="0eb3a-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="0eb3a-132">Endpunkte für Office 365 Deutschland</span><span class="sxs-lookup"><span data-stu-id="0eb3a-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="0eb3a-133">Die Endpunkte für eine separate Cloud in Europa für die meisten regulierten Kunden in Deutschland, der Europäischen Union (EU) und der Europäischen Freihandelszone (EFTA).</span><span class="sxs-lookup"><span data-stu-id="0eb3a-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="0eb3a-134">Informationen über das automatische Abrufen der neuesten Liste der Endpunkte für Ihre Office 365-Cloud finden Sie unter [Office 365-IP-Adresse und URL-Web-Dienst](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="0eb3a-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="0eb3a-135">Weitere Informationen über zusätzliche Endpunkte finden Sie in folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="0eb3a-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="0eb3a-136">Zusätzliche, nicht in den Webdiensten enthaltene Endpunkte</span><span class="sxs-lookup"><span data-stu-id="0eb3a-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="0eb3a-137">Netzwerkanforderungen in Office 2016 für Mac</span><span class="sxs-lookup"><span data-stu-id="0eb3a-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="0eb3a-138">Weitere Themen zu Office 365-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="0eb3a-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="0eb3a-139">Die folgenden Artikel behandeln spezielle Themen zum Office 365-Netzwerk:</span><span class="sxs-lookup"><span data-stu-id="0eb3a-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="0eb3a-140">Netzwerke für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="0eb3a-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="0eb3a-141">IPv6-Unterstützung in Office 365-Diensten</span><span class="sxs-lookup"><span data-stu-id="0eb3a-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="0eb3a-142">NAT-Unterstützung bei Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="0eb3a-143">ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="0eb3a-144">In den folgenden Artikeln finden Sie Informationen über die Verwendung von ExpressRoute für Office 365-Datenverkehr:</span><span class="sxs-lookup"><span data-stu-id="0eb3a-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="0eb3a-145">Azure ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="0eb3a-146">Implementierung von ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="0eb3a-147">Netzwerkplanung mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="0eb3a-148">Routing mit ExpressRoute für Office 365</span><span class="sxs-lookup"><span data-stu-id="0eb3a-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
