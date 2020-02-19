---
title: Office 365 Netzwerkbewertung (Vorschau)
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
description: Office 365 Netzwerkbewertung (Vorschau)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106327"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="c1873-103">Office 365 Netzwerkbewertung (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="c1873-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="c1873-104">Die Office 365 Netzwerkbewertung gibt an, wie sich die Benutzererfahrung auf die Netzwerkkonnektivität des Kunden auswirkt.</span><span class="sxs-lookup"><span data-stu-id="c1873-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="c1873-105">Die Auswirkungen von Microsoft-eigenen Netzwerkverbindungen sind hiervon ausgeschlossen, damit Kundennetzwerk Designs optimieren können, für die Sie verantwortlich sind.</span><span class="sxs-lookup"><span data-stu-id="c1873-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="c1873-106">Sie wird anhand von Messungen berechnet, die sich auf die Benutzererfahrung bei Schlüssel Office 365 Arbeitsauslastungen auswirken und als Prozentsatz mit einem Bereich von 0 bis 100 angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1873-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="c1873-107">Eine sehr niedrige Netzwerkbewertung deutet darauf hin, dass Office 365 Clients erhebliche Probleme beim Verbinden oder verbleibenden Benutzer reagieren haben.</span><span class="sxs-lookup"><span data-stu-id="c1873-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="c1873-108">Eine Punktzahl von 80% steht für Netzwerkkonnektivität, bei der Sie nicht erwarten können, dass Benutzer Beschwerden über Ihre Office 365 Benutzererfahrung aufgrund ihrer Netzwerkleistung erhalten.</span><span class="sxs-lookup"><span data-stu-id="c1873-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="c1873-109">Wenn Verbesserungen bei der Netzwerkkonnektivität vorgenommen werden, nimmt diese Bewertung zusammen mit der Benutzeroberfläche zu.</span><span class="sxs-lookup"><span data-stu-id="c1873-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c1873-110">Empfehlungen zur Netzwerkleistung, Einblicke und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und sind nur für Office 365 Mandanten verfügbar, die im Feature Preview-Programm registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="c1873-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="c1873-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c1873-111">Exchange Online</span></span>

<span data-ttu-id="c1873-112">Für Exchange Online wird die TCP-Wartezeit vom Clientcomputer auf den Exchange-Front-End-Server gemessen.</span><span class="sxs-lookup"><span data-stu-id="c1873-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="c1873-113">Dies kann durch die Entfernung beeinträchtigt werden, über die das Netzwerk über die Kunden LAN und WAN reist.</span><span class="sxs-lookup"><span data-stu-id="c1873-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="c1873-114">Es kann auch durch Netzwerk-zwischengeschaltete Geräte oder Dienste beeinträchtigt werden, die die Konnektivität verzögern oder dazu führen, dass Pakete erneut gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1873-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="c1873-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c1873-115">SharePoint Online</span></span>

<span data-ttu-id="c1873-116">Für SharePoint Online wird die Downloadgeschwindigkeit gemessen, die ein Benutzer für den Zugriff auf ein Dokument zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="c1873-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="c1873-117">Dies kann durch die verfügbare Bandbreite zwischen dem Clientcomputer und dem Netzwerk von Microsoft auf Netzwerk Schaltkreisen beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1873-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="c1873-118">Es wird auch häufig von Netzwerküberlastung beeinflusst, die in Engpässen bei komplexen Netzwerkgeräten oder in schlechten WLAN-Abdeckungsbereichen vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c1873-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="c1873-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c1873-119">Microsoft Teams</span></span>

<span data-ttu-id="c1873-120">Für Microsoft Teams wird die Netzwerkqualität als UDP-Wartezeit, UDP-Jitter und UDP-Paketverlust gemessen.</span><span class="sxs-lookup"><span data-stu-id="c1873-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="c1873-121">UDP wird für die Audio-und Video Medien Konnektivität für Anrufe und Konferenzen für Microsoft Teams verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1873-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="c1873-122">Dies kann durch die gleichen Faktoren wie Wartezeit und Downloadgeschwindigkeit sowie Verbindungs Lücken in der UDP-Unterstützung eines Netzwerks beeinträchtigt werden, da UDP separat mit dem häufigeren TCP-Protokoll konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="c1873-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="c1873-123">Netzwerkbewertung für Mandanten und Office-Standort</span><span class="sxs-lookup"><span data-stu-id="c1873-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="c1873-124">Eine Netzwerkbewertung misst den Entwurf des Netzwerkperimeters eines Office-Standorts für das Microsoft-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="c1873-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="c1873-125">Verbesserungen am Netzwerkperimeter werden am besten an jedem Office-Standort vorgenommen, oder wenn die Netzwerkkonnektivität aggregiert ist, können Verbesserungen auftreten, die sich auf mehrere Standorte auswirken.</span><span class="sxs-lookup"><span data-stu-id="c1873-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="c1873-126">Wir zeigen eine Netzwerkbewertung für den gesamten Office 365 Mandanten auf der Übersichtsseite "Netzwerkleistung" und eine bestimmte Netzwerkbewertung für jeden erkannten Office-Standort auf der Zusammenfassungsseite dieses Standorts an.</span><span class="sxs-lookup"><span data-stu-id="c1873-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="c1873-127">Bereich "Netzwerkbewertung"</span><span class="sxs-lookup"><span data-stu-id="c1873-127">Network score panel</span></span>

<span data-ttu-id="c1873-128">Jedes Netzwerk Ergebnis gibt an, ob für den Mandanten oder für einen bestimmten Bürostandort ein Bereich mit Details zur Partitur angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c1873-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="c1873-129">In diesem Bereich wird ein Balkendiagramm des Ergebnisses sowohl als Prozentsatz als auch als Gesamtpunktzahl für jede Arbeitsauslastung der Komponente angezeigt, einschließlich der Arbeitslasten, bei denen Messdaten empfangen wurden.</span><span class="sxs-lookup"><span data-stu-id="c1873-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="c1873-130">Für eine Bürostandort-Netzwerkbewertung zeigen wir auch einen Benchmark an, bei dem es sich um den Median aller Office 365-Clients handelt, von denen Daten in derselben Stadt wie Ihr Bürostandort gemeldet wurden.</span><span class="sxs-lookup"><span data-stu-id="c1873-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="c1873-131">Der Bewertungs Aufschlüsselung in der Gruppe zeigt die Bewertung für jede Arbeitsauslastung der Komponente an.</span><span class="sxs-lookup"><span data-stu-id="c1873-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="c1873-132">Der Bewertungsverlauf zeigt die letzten 30 Tage der Bewertung und die Benchmark an.</span><span class="sxs-lookup"><span data-stu-id="c1873-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c1873-133">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c1873-133">Related topics</span></span>

[<span data-ttu-id="c1873-134">Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="c1873-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="c1873-135">Office 365 Einblicke in die Netzwerkleistung (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="c1873-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="c1873-136">Office 365 Netzwerk-Onboarding-Tool im M365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="c1873-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
