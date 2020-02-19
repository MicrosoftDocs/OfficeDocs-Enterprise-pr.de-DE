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
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="62083-103">Office 365 Einblicke in die Netzwerkleistung (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="62083-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="62083-104">Die Microsoft 365 Admin Center-Netzwerk Leistungs Seiten zeigen Office 365 Einblicke in das Netzwerk, die beim Entwerfen von Netzwerkperimetern für Ihre Office-Standorte hilfreich sein können.</span><span class="sxs-lookup"><span data-stu-id="62083-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="62083-105">Es gibt fünf spezifische Einblicke in das Netzwerk, die für die einzelnen Office-Standorte möglicherweise angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="62083-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="62083-106">Empfehlungen zur Netzwerkleistung, Einblicke und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="62083-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="62083-107">Ausstieg aus dem backhauld-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="62083-107">Backhauled network egress</span></span>

<span data-ttu-id="62083-108">Der Abstand zwischen dem Benutzerstandort und dem Ausstiegs Netzwerk beträgt mehr als 500 Meilen (800 Kilometer), was sich auf die Leistung auswirken dürfte.</span><span class="sxs-lookup"><span data-stu-id="62083-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="62083-109">Lokaler Ausstieg näher am Benutzer wird empfohlen.</span><span class="sxs-lookup"><span data-stu-id="62083-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="62083-110">Dadurch wird feststellen, dass der Abstand zwischen dem Bürostandort und dem Netzwerk Ausstieg mehr als 500 Meilen beträgt.</span><span class="sxs-lookup"><span data-stu-id="62083-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="62083-111">Der Standort des Büros wird durch einen verborgenen Clientcomputer Speicherort identifiziert, und der Netzwerk Ausgangsspeicherort wird mithilfe von Reverse IP Address to Location Databases identifiziert.</span><span class="sxs-lookup"><span data-stu-id="62083-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="62083-112">Der Office-Standort ist möglicherweise ungenau, wenn Windows-Ortungsdienste auf Computern deaktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="62083-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="62083-113">Der Netzwerk Ausgangsspeicherort ist möglicherweise ungenau, wenn die Datenbankinformationen der Reverse-IP-Adresse ungenau sind.</span><span class="sxs-lookup"><span data-stu-id="62083-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="62083-114">Details für diese Einblicke sind der Office-Standort, der Netzwerk Ausgangsstandort und der Abstand dazwischen.</span><span class="sxs-lookup"><span data-stu-id="62083-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="62083-115">Für diese Einblicke empfehlen wir einen Netzwerk Ausstieg näher am Bürostandort, damit die Konnektivität optimal an das Microsoft-Netzwerk im Internet und auf Office 365 Dienst-Fronttüren weitergeleitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="62083-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="62083-116">Das Schließen des Netzwerk Ausstiegs für Benutzer in Office-Standorten ermöglicht auch in Zukunft eine verbesserte Leistung, da Microsoft in Zukunft sowohl Netzwerk Points of Presence als auch Office 365-Service-Front-Doors erweitert.</span><span class="sxs-lookup"><span data-stu-id="62083-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="62083-117">Diese Einblicke wird in einigen zusammenfassungsansichten als "Ausstieg" abgekürzt.</span><span class="sxs-lookup"><span data-stu-id="62083-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="62083-118">Bessere Leistung für Kunden in Ihrer Nähe erkannt</span><span class="sxs-lookup"><span data-stu-id="62083-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="62083-119">Da eine beträchtliche Anzahl von Kunden in Ihrem Metro-Bereich eine bessere Leistung hat als Benutzer in Ihrer Organisation an diesem Standort.</span><span class="sxs-lookup"><span data-stu-id="62083-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="62083-120">Dabei wird die Gesamtleistung der Office 365 Kunden in derselben Stadt wie dieser Bürostandort betrachtet.</span><span class="sxs-lookup"><span data-stu-id="62083-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Relative Netzwerkleistung](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="62083-122">Wir berechnen den Prozentsatz der Office 365 Kunden in der gleichen Stadt in besseren Leistungs Buckets.</span><span class="sxs-lookup"><span data-stu-id="62083-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="62083-123">Wenn diese Zahl, wenn 10% von mehr dann zeigen wir die Netzwerk Einblicke.</span><span class="sxs-lookup"><span data-stu-id="62083-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="62083-124">Diese Einblicke wird in einigen zusammenfassungsansichten als "Peers" abgekürzt.</span><span class="sxs-lookup"><span data-stu-id="62083-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="62083-125">Verwenden eines nicht optimalen Exchange Online-Dienst-Front-Door</span><span class="sxs-lookup"><span data-stu-id="62083-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="62083-126">Der Benutzer stellt keine Verbindung zu einem optimalen Office 365-Dienst vor der Haustür her, und dies wird voraussichtlich Auswirkungen auf die Leistung haben.</span><span class="sxs-lookup"><span data-stu-id="62083-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="62083-127">Wir führen Exchange Online Service-Fronttüren auf, die für die Verwendung aus der Office-Standort Stadt mit guter Leistung geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="62083-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="62083-128">Wenn der aktuelle Test die Verwendung eines Exchange Online-Dienst-Front-Doors nicht in dieser Liste zeigt, wird diese Empfehlung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="62083-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="62083-129">Die Verwendung eines nicht optimalen Exchange Online Dienst-Front-Door könnte durch Netzwerk Backhaul vor dem Ausstieg des Unternehmensnetzwerks verursacht werden, in diesem Fall empfehlen wir den Ausstieg aus dem lokalen und direkten Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="62083-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="62083-130">Es kann auch durch die Verwendung eines Remote-DNS-rekursive Auflösungs Servers verursacht werden, in dem der Fall empfohlen wird, den DNS-rekursive Auflösungs Server mit dem Netzwerk Ausstieg auszurichten.</span><span class="sxs-lookup"><span data-stu-id="62083-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="62083-131">Diese Einblicke wird in einigen zusammenfassungsansichten als "Routing" abgekürzt.</span><span class="sxs-lookup"><span data-stu-id="62083-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="62083-132">Verwendung von nicht optimaler SharePoint Online Dienst-Haustür</span><span class="sxs-lookup"><span data-stu-id="62083-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="62083-133">Der Benutzer stellt keine Verbindung mit der nächstgelegenen SharePoint Online-Dienst-Haustür her.</span><span class="sxs-lookup"><span data-stu-id="62083-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="62083-134">Dies wird voraussichtlich Auswirkungen auf die Leistung haben.</span><span class="sxs-lookup"><span data-stu-id="62083-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="62083-135">Wir identifizieren die SharePoint Online-Dienst-Haustür, mit der der Testclient eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="62083-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="62083-136">Für die Office-Standort Stadt vergleichen wir dies mit der erwarteten SharePoint Online-Service-Haustür für diese Stadt.</span><span class="sxs-lookup"><span data-stu-id="62083-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="62083-137">Wenn er nicht übereinstimmt, machen wir diese Empfehlung.</span><span class="sxs-lookup"><span data-stu-id="62083-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="62083-138">Diese Einblicke wird in einigen zusammenfassungsansichten als "ausschließend" abgekürzt.</span><span class="sxs-lookup"><span data-stu-id="62083-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="62083-139">Niedrige Downloadgeschwindigkeit von SharePoint-Haustür</span><span class="sxs-lookup"><span data-stu-id="62083-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="62083-140">Unter optimale Netzwerk Downloadgeschwindigkeit ermittelt, die Auswirkungen auf die Dauer hat, die zum Laden von Dokumenten aus OneDrive für Unternehmen benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="62083-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="62083-141">Die Downloadgeschwindigkeit, die ein Benutzer von SharePoint Online-und OneDrive für Unternehmen-Dienst-Fronttüren erhalten kann, wird in Megabytes pro Sekunde (Mbps) gemessen.</span><span class="sxs-lookup"><span data-stu-id="62083-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="62083-142">Wenn dieser Wert kleiner als 1 Mbit/s ist, stellen wir diese Einblicke bereit.</span><span class="sxs-lookup"><span data-stu-id="62083-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="62083-143">Um die Downloadgeschwindigkeit zu verbessern, die ein Benutzer Bandbreite erhalten kann, müssen Sie möglicherweise erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="62083-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="62083-144">Alternativ kann es zu Netzwerküberlastung zwischen Benutzercomputern am Office-Standort und der Front-Door-SharePoint Online Dienst geben.</span><span class="sxs-lookup"><span data-stu-id="62083-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="62083-145">Dies wird manchmal als Überlastungs Verlust bezeichnet und schränkt die Downloadgeschwindigkeit ein, die Benutzern zur Verfügung steht, auch wenn genügend Bandbreite zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="62083-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="62083-146">Diese Einblicke wird in einigen zusammenfassungsansichten als "Durchsatz" abgekürzt.</span><span class="sxs-lookup"><span data-stu-id="62083-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="62083-147">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="62083-147">Related topics</span></span>

[<span data-ttu-id="62083-148">Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="62083-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="62083-149">Office 365 Netzwerkbewertung (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="62083-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="62083-150">Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="62083-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
