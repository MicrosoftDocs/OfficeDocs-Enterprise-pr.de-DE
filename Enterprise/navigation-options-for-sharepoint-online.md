---
title: Navigationsoptionen für SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In diesem Artikel werden Navigations Options Websites mit aktivierter SharePoint-Veröffentlichung in SharePoint Online beschrieben. Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus. Dieser Artikel gilt nicht für klassische Teamwebsites.
ms.openlocfilehash: c651530284889d2808c8fa415b72836eb6d14aea
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004760"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="f1a76-105">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f1a76-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="f1a76-106">In diesem Artikel werden Navigations Options Websites mit aktivierter SharePoint-Veröffentlichung in SharePoint Online beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f1a76-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="f1a76-107">Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus.</span><span class="sxs-lookup"><span data-stu-id="f1a76-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span> <span data-ttu-id="f1a76-108">Die Vorlage für die SharePoint-Veröffentlichungswebsite sollte nur bei Bedarf für ein zentralisiertes Portal verwendet werden, und das Veröffentlichungsfeature sollte nur auf bestimmten Websites aktiviert werden und nur, wenn es absolut erforderlich ist, da sich die Leistung bei falscher Verwendung auswirken kann.</span><span class="sxs-lookup"><span data-stu-id="f1a76-108">The SharePoint Publishing site template should only be used if required for a centralized portal and the publishing feature should only be enabled on specific sites and only when absolutely required as it can impact performance when used incorrectly.</span></span>

>[!NOTE]
><span data-ttu-id="f1a76-109">Wenn Sie moderne SharePoint-Navigationsoptionen wie Mega-Menü, kaskadierende Navigation oder Hub-Navigation verwenden, gilt dieser Artikel nicht für Ihre Website.</span><span class="sxs-lookup"><span data-stu-id="f1a76-109">If you're using modern SharePoint navigation options like mega menu, cascading navigation, or hub navigation, this article does not apply to your site.</span></span> <span data-ttu-id="f1a76-110">Moderne SharePoint-Website Architekturen nutzen eine vereinfachte Websitehierarchie und ein Hub-and-Spoke-Modell.</span><span class="sxs-lookup"><span data-stu-id="f1a76-110">Modern SharePoint site architectures leverage a more flattened site hierarchy and a hub-and-spoke model.</span></span> <span data-ttu-id="f1a76-111">Auf diese Weise können viele Szenarien erreicht werden, für die die Verwendung des SharePoint-Veröffentlichungsfeatures nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-111">This allows many scenarios to be achieved that do NOT require use of the SharePoint Publishing feature.</span></span>

## <a name="overview"></a><span data-ttu-id="f1a76-112">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f1a76-112">Overview</span></span>

<span data-ttu-id="f1a76-113">Die Konfiguration des Navigations Anbieters kann die Leistung für den gesamten Standort erheblich beeinträchtigen, und es ist sorgfältig darauf zu achten, dass Sie einen Navigationsanbieter und eine Konfiguration auswählen, die für die Anforderungen einer SharePoint-Website effektiv skaliert wird.</span><span class="sxs-lookup"><span data-stu-id="f1a76-113">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="f1a76-114">Es gibt zwei out-of-the-Box-Navigationsanbieter sowie benutzerdefinierte Navigations Implementierungen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-114">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="f1a76-115">Die erste Option, die [**strukturelle Navigation**](#using-structural-navigation-in-sharepoint-online), ist die empfohlene Navigationsoption in SharePoint Online für klassische SharePoint-Websites, **Wenn Sie die Zwischenspeicherung der Struktur Navigation für Ihre Website aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="f1a76-115">The first option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), is the recommended navigation option in SharePoint Online for classic Sharepoint sites, **if you turn on structural navigation caching for your site**.</span></span> <span data-ttu-id="f1a76-116">Dieser Navigationsanbieter zeigt die Navigationselemente unter der aktuellen Website und optional die aktuelle Website und ihre Geschwister an.</span><span class="sxs-lookup"><span data-stu-id="f1a76-116">This navigation provider displays the navigation items below the current site, and optionally the current site and its siblings.</span></span> <span data-ttu-id="f1a76-117">Es bietet zusätzliche Funktionen wie Sicherheits Kürzung und Websitestruktur Aufzählung.</span><span class="sxs-lookup"><span data-stu-id="f1a76-117">It provides additional capabilities such as security trimming and site structure enumeration.</span></span> <span data-ttu-id="f1a76-118">Wenn die Zwischenspeicherung deaktiviert ist, wirkt sich dies negativ auf die Leistung und Skalierbarkeit aus, und die Einschränkung ist möglicherweise eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-118">If caching is disabled, this will negatively impact performance and scalability, and may be subject to throttling.</span></span>

<span data-ttu-id="f1a76-119">Die zweite Option, [**verwaltete (Metadaten) Navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), stellt Navigationselemente mithilfe eines Ausdruckssatzes für verwaltete Metadaten dar.</span><span class="sxs-lookup"><span data-stu-id="f1a76-119">The second option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), represents navigation items using a Managed Metadata term set.</span></span> <span data-ttu-id="f1a76-120">Es wird empfohlen, die Sicherheits Kürzung nur dann zu deaktivieren, wenn dies erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-120">We recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="f1a76-121">Das Trimmen von Sicherheitsgründen ist als sichere Standardeinstellung für diesen Navigationsanbieter aktiviert. für viele Websites ist jedoch der Aufwand der Sicherheits Kürzung nicht erforderlich, da Navigationselemente häufig für alle Benutzer der Website konsistent sind.</span><span class="sxs-lookup"><span data-stu-id="f1a76-121">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="f1a76-122">Mit der empfohlenen Konfiguration zum Deaktivieren der Einschränkung der Sicherheit erfordert dieser Navigationsanbieter keine Aufzählung der Websitestruktur und ist hochgradig skalierbar mit akzeptabler Leistungsbeeinträchtigung.</span><span class="sxs-lookup"><span data-stu-id="f1a76-122">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="f1a76-123">Neben den standardmäßigen Navigations Anbietern haben viele Kunden erfolgreich Alternative benutzerdefinierte Navigations Implementierungen implementiert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-123">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="f1a76-124">Weitere Informationen finden Sie in diesem Artikel unter [Such gesteuerte clientseitige Skripts](#using-search-driven-client-side-scripting) .</span><span class="sxs-lookup"><span data-stu-id="f1a76-124">See [Search-driven client-side scripting](#using-search-driven-client-side-scripting) in this article.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="f1a76-125">Vorteile und Nachteile von SharePoint Online Navigationsoptionen</span><span class="sxs-lookup"><span data-stu-id="f1a76-125">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="f1a76-126">In der folgenden Tabelle sind die vor-und Nachteile der einzelnen Optionen zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="f1a76-126">The following table summarizes the pros and cons of each option.</span></span>

|<span data-ttu-id="f1a76-127">Strukturelle Navigation</span><span class="sxs-lookup"><span data-stu-id="f1a76-127">Structural navigation</span></span>  |<span data-ttu-id="f1a76-128">Verwaltete Navigation</span><span class="sxs-lookup"><span data-stu-id="f1a76-128">Managed navigation</span></span>  |<span data-ttu-id="f1a76-129">Such gesteuerte Navigation</span><span class="sxs-lookup"><span data-stu-id="f1a76-129">Search-driven navigation</span></span>  |<span data-ttu-id="f1a76-130">Benutzerdefinierter Navigationsanbieter</span><span class="sxs-lookup"><span data-stu-id="f1a76-130">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="f1a76-131">Experten</span><span class="sxs-lookup"><span data-stu-id="f1a76-131">Pros:</span></span><br/><br/><span data-ttu-id="f1a76-132">Einfache Wartung</span><span class="sxs-lookup"><span data-stu-id="f1a76-132">Easy to maintain</span></span><br/><span data-ttu-id="f1a76-133">Getrimmte Sicherheit</span><span class="sxs-lookup"><span data-stu-id="f1a76-133">Security trimmed</span></span><br/><span data-ttu-id="f1a76-134">Wird automatisch innerhalb von 24 Stunden aktualisiert, wenn Inhalte geändert werden</span><span class="sxs-lookup"><span data-stu-id="f1a76-134">Automatically updates within 24 hours when content is changed</span></span><br/>     |<span data-ttu-id="f1a76-135">Experten</span><span class="sxs-lookup"><span data-stu-id="f1a76-135">Pros:</span></span><br/><br/><span data-ttu-id="f1a76-136">Einfache Wartung</span><span class="sxs-lookup"><span data-stu-id="f1a76-136">Easy to maintain</span></span><br/>|<span data-ttu-id="f1a76-137">Experten</span><span class="sxs-lookup"><span data-stu-id="f1a76-137">Pros:</span></span><br/><br/><span data-ttu-id="f1a76-138">Getrimmte Sicherheit</span><span class="sxs-lookup"><span data-stu-id="f1a76-138">Security trimmed</span></span><br/><span data-ttu-id="f1a76-139">Automatisch aktualisieren, wenn Websites hinzugefügt werden</span><span class="sxs-lookup"><span data-stu-id="f1a76-139">Automatically updates as sites are added</span></span><br/><span data-ttu-id="f1a76-140">Schnelle Ladezeit und lokal zwischengespeicherte Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="f1a76-140">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="f1a76-141">Experten</span><span class="sxs-lookup"><span data-stu-id="f1a76-141">Pros:</span></span><br/><br/><span data-ttu-id="f1a76-142">Breitere Auswahl von verfügbaren Optionen</span><span class="sxs-lookup"><span data-stu-id="f1a76-142">Wider choice of options available</span></span><br/><span data-ttu-id="f1a76-143">Schnelles Laden, wenn die Zwischenspeicherung ordnungsgemäß verwendet wird</span><span class="sxs-lookup"><span data-stu-id="f1a76-143">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="f1a76-144">Viele Optionen funktionieren mit dem reaktionsschnellen Seitenentwurf gut</span><span class="sxs-lookup"><span data-stu-id="f1a76-144">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="f1a76-145">Nachteile</span><span class="sxs-lookup"><span data-stu-id="f1a76-145">Cons:</span></span><br/><br/><span data-ttu-id="f1a76-146">**Auswirkungen auf die Leistung, wenn die Zwischenspeicherung deaktiviert ist**</span><span class="sxs-lookup"><span data-stu-id="f1a76-146">**Impacts performance if caching is disabled**</span></span><br/><span data-ttu-id="f1a76-147">Einschränkungen unterliegen</span><span class="sxs-lookup"><span data-stu-id="f1a76-147">Subject to throttling</span></span><br/>|<span data-ttu-id="f1a76-148">Nachteile</span><span class="sxs-lookup"><span data-stu-id="f1a76-148">Cons:</span></span><br/><br/><span data-ttu-id="f1a76-149">Nicht automatisch aktualisiert, um die Websitestruktur widerzuspiegeln</span><span class="sxs-lookup"><span data-stu-id="f1a76-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="f1a76-150">**Auswirkungen auf die Leistung, wenn die Sicherheits Kürzung aktiviert ist** oder wenn die Navigationsstruktur Komplex ist</span><span class="sxs-lookup"><span data-stu-id="f1a76-150">**Impacts performance if security trimming is enabled** or when navigation structure is complex</span></span><br/>|<span data-ttu-id="f1a76-151">Nachteile</span><span class="sxs-lookup"><span data-stu-id="f1a76-151">Cons:</span></span><br/><br/><span data-ttu-id="f1a76-152">Keine Möglichkeit, Websites problemlos zu bestellen</span><span class="sxs-lookup"><span data-stu-id="f1a76-152">No ability to easily order sites</span></span><br/><span data-ttu-id="f1a76-153">Erfordert die Anpassung der Gestaltungsvorlage (erforderliche technische Kenntnisse)</span><span class="sxs-lookup"><span data-stu-id="f1a76-153">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="f1a76-154">Nachteile</span><span class="sxs-lookup"><span data-stu-id="f1a76-154">Cons:</span></span><br/><br/><span data-ttu-id="f1a76-155">Benutzerdefinierte Entwicklung ist erforderlich</span><span class="sxs-lookup"><span data-stu-id="f1a76-155">Custom development is required</span></span><br/><span data-ttu-id="f1a76-156">Externe Datenquelle/Cachespeicherung erforderlich, beispielsweise Azure</span><span class="sxs-lookup"><span data-stu-id="f1a76-156">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="f1a76-157">Die am besten geeignete Option für Ihre Website hängt von den Anforderungen Ihrer Website und ihrer technischen Leistungsfähigkeit ab.</span><span class="sxs-lookup"><span data-stu-id="f1a76-157">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="f1a76-158">Wenn Sie einen einfach zu konfigurierenden Navigationsanbieter wünschen, der automatisch aktualisiert wird, wenn Inhalt geändert wird, ist die strukturelle Navigation [mit aktivierter Zwischenspeicherung](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) eine gute Option.</span><span class="sxs-lookup"><span data-stu-id="f1a76-158">If you want an easy-to-configure navigation provider that automatically updates when content is changed, then structural navigation [with caching enabled](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) is a good option.</span></span>

>[!NOTE]
><span data-ttu-id="f1a76-159">Die Anwendung des gleichen Prinzips wie moderne SharePoint-Websites durch Vereinfachung der allgemeinen Websitestruktur in einer flacheren, nicht hierarchischen Struktur verbessert die Leistung und vereinfacht das Wechseln zu modernen SharePoint-Websites.</span><span class="sxs-lookup"><span data-stu-id="f1a76-159">Applying the same principle as modern SharePoint sites by simplifying the overall site structure to a flatter, non-hierarchical structure improves performance and simplifies moving to modern SharePoint sites.</span></span> <span data-ttu-id="f1a76-160">Dies bedeutet, dass statt einer einzelnen Websitesammlung mit Hunderten von Websites (Unterwebs) ein besserer Ansatz darin besteht, viele Websitesammlungen mit sehr wenigen Unterwebsites (Unterwebs) zu haben.</span><span class="sxs-lookup"><span data-stu-id="f1a76-160">What this means is that instead of having a single site collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="f1a76-161">Analysieren der Navigationsleistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f1a76-161">Analyzing navigation performance in SharePoint Online</span></span>

<span data-ttu-id="f1a76-162">Das [Seiten Diagnosetool für SharePoint](https://aka.ms/perftool) ist eine Browser Erweiterung für Microsoft Edge-und Chrome-Browser, die sowohl SharePoint Online moderne Portal-als auch klassische Veröffentlichungswebsite-Seiten analysiert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-162">The [Page Diagnostics for SharePoint tool](https://aka.ms/perftool) is a browser extension for Microsoft Edge and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="f1a76-163">Dieses Tool funktioniert nur für SharePoint Online und kann nicht auf einer SharePoint-System Seite verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-163">This tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="f1a76-164">Das Tool generiert einen Bericht für jede analysierte Seite, die zeigt, wie die Seite mit einem vordefinierten Satz von Regeln ausgeführt wird, und zeigt ausführliche Informationen an, wenn Ergebnisse für einen Test außerhalb des Basiswerts liegen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-164">The tool generates a report for each analyzed page showing how the page performs against a pre-defined set of rules and displays detailed information when results for a test fall outside the baseline value.</span></span> <span data-ttu-id="f1a76-165">SharePoint Online Administratoren und Designer können das Tool verwenden, um Leistungsprobleme zu beheben, um sicherzustellen, dass neue Seiten vor der Veröffentlichung optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-165">SharePoint Online administrators and designers can use the tool to troubleshoot performance issues to ensure that new pages are optimized prior to publishing.</span></span>

<span data-ttu-id="f1a76-166">**SPRequestDuration** ist insbesondere die Zeit, die SharePoint benötigt, um die Seite zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f1a76-166">**SPRequestDuration** in particular is the time it takes for SharePoint to process the page.</span></span> <span data-ttu-id="f1a76-167">Die schwere Navigation (beispielsweise das Einschließen von Seiten in der Navigation), komplexe Websitehierarchien und andere Konfigurations-und Topologiefunktionen können einen erheblichen Beitrag zur längeren Dauer leisten.</span><span class="sxs-lookup"><span data-stu-id="f1a76-167">Heavy navigation (like including pages in navigation), complex site hierarchies, and other configuration and topology options can all dramatically contribute to longer durations.</span></span>

## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="f1a76-168">Verwenden der Struktur Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f1a76-168">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="f1a76-169">Dies ist die standardmäßig verwendete Navigation, die die einfachste Lösung ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-169">This is the out-of-the-box navigation used by default and is the most straightforward solution.</span></span> <span data-ttu-id="f1a76-170">Es ist keine Anpassung erforderlich, und ein nicht technischer Benutzer kann auch auf einfache Weise Elemente hinzufügen, Elemente ausblenden und die Navigation auf der Seite "Einstellungen" verwalten.</span><span class="sxs-lookup"><span data-stu-id="f1a76-170">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="f1a76-171">Es wird empfohlen, die [Zwischenspeicherung zu aktivieren](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), da andernfalls ein teurer Leistungskompromiss vorliegt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-171">We recommend [enabling caching](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), otherwise there is an expensive performance trade-off.</span></span>

### <a name="how-to-implement-structural-navigation-caching"></a><span data-ttu-id="f1a76-172">Vorgehensweise implementieren der Zwischenspeicherung der Struktur Navigation</span><span class="sxs-lookup"><span data-stu-id="f1a76-172">How to implement structural navigation caching</span></span>

<span data-ttu-id="f1a76-173">Unter **Websiteeinstellungen** > **sehen und fühlen** > **Navigation**können Sie überprüfen, ob die strukturelle Navigation für die globale Navigation oder aktuelle Navigation ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-173">Under **Site Settings** > **Look and Feel** > **Navigation**, you can validate if structural navigation is selected for either global navigation or current navigation.</span></span> <span data-ttu-id="f1a76-174">Das Auswählen von **Seiten anzeigen** wirkt sich negativ auf die Leistung aus.</span><span class="sxs-lookup"><span data-stu-id="f1a76-174">Selecting **Show pages** will have negative impact on performance.</span></span>

![Struktur Navigation mit ausgewählten Unterwebsites anzeigen](media/SPONavOptionsStructuredShowSubsites.png)

<span data-ttu-id="f1a76-176">Die Zwischenspeicherung kann auf Websitesammlungsebene und auf Websiteebene aktiviert oder deaktiviert werden und ist standardmäßig für beide aktiviert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-176">Caching can be enabled or disabled at the site collection level and at the site level, and is enabled for both by default.</span></span> <span data-ttu-id="f1a76-177">Aktivieren Sie das Kontrollkästchen zum **Aktivieren der Zwischenspeicherung**auf Website Sammlungs **Ebene unter** > Website Sammlungs**Verwaltung** > Website Sammlungs**Navigation**.</span><span class="sxs-lookup"><span data-stu-id="f1a76-177">To enable at the site collection level, under **Site Settings** > **Site Collection Administration** > **Site Collection Navigation**, check the box for **Enable caching**.</span></span>

![Aktivieren der Zwischenspeicherung auf Websiteebene](media/structural-nav/structural-nav-caching-site-coll.png)

<span data-ttu-id="f1a76-179">Aktivieren Sie das Kontrollkästchen **Zwischenspeicherung aktivieren**, um auf Websiteebene unter **Websiteeinstellungen** > zu**Navigieren**.</span><span class="sxs-lookup"><span data-stu-id="f1a76-179">To enable at the site level, under **Site Settings** > **Navigation**, check the box for **Enable caching**.</span></span>

![Aktivieren der Zwischenspeicherung auf Websiteebene](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="f1a76-181">Verwenden der verwalteten Navigation und der Metadaten in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f1a76-181">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="f1a76-182">Die verwaltete Navigation ist eine weitere out-of-the-Box-Option, die Sie verwenden können, um die meisten der gleichen Funktionen wie die strukturelle Navigation neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-182">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="f1a76-183">Verwaltete Metadaten können so konfiguriert werden, dass die Sicherheits Kürzung aktiviert oder deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="f1a76-183">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="f1a76-184">Bei deaktivierter Sicherheits Kürzung ist die verwaltete Navigation relativ effizient, da alle Navigationslinks mit einer Konstanten Anzahl von Server aufrufen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-184">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="f1a76-185">Durch das Aktivieren der Sicherheits Kürzung werden jedoch einige der Leistungsvorteile der verwalteten Navigation negiert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-185">Enabling security trimming, however, negates some of the performance advantages of managed navigation.</span></span>

<span data-ttu-id="f1a76-186">Wenn Sie das Kürzen von Sicherheitsgründen aktivieren müssen, empfehlen wir Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f1a76-186">If you need to enable security trimming, we recommend that you:</span></span>

- <span data-ttu-id="f1a76-187">Aktualisieren aller benutzerfreundlichen URL-Links auf einfache Links</span><span class="sxs-lookup"><span data-stu-id="f1a76-187">Update all friendly URL links to simple links</span></span>
- <span data-ttu-id="f1a76-188">Hinzufügen erforderlicher Sicherheits Kürzungs Knoten als benutzerfreundliche URLs</span><span class="sxs-lookup"><span data-stu-id="f1a76-188">Add required security trimming nodes as friendly URLs</span></span>
- <span data-ttu-id="f1a76-189">Beschränken Sie die Anzahl der Navigationselemente auf nicht mehr als 100 und nicht mehr als 3 Ebenen tief</span><span class="sxs-lookup"><span data-stu-id="f1a76-189">Limit the number of navigation items to no more than 100 and no more than 3 levels deep</span></span>

<span data-ttu-id="f1a76-190">Für viele Websites ist keine Sicherheits Kürzung erforderlich, da die Navigationsstruktur häufig für alle Benutzer der Website konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-190">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="f1a76-191">Wenn die Sicherheits Kürzung deaktiviert ist und der Navigation ein Link hinzugefügt wird, auf den nicht alle Benutzer Zugriff haben, wird der Link weiterhin angezeigt, führt jedoch zu einer Meldung mit Zugriff verweigert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-191">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="f1a76-192">Es besteht keine Gefahr eines versehentlichen Zugriffs auf den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-192">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="f1a76-193">Implementieren der verwalteten Navigation und der Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="f1a76-193">How to implement managed navigation and the results</span></span>

<span data-ttu-id="f1a76-194">In docs.Microsoft.com finden Sie verschiedene Artikel zu den Details der verwalteten Navigation.</span><span class="sxs-lookup"><span data-stu-id="f1a76-194">There are several articles on docs.microsoft.com about the details of managed navigation.</span></span> <span data-ttu-id="f1a76-195">Beispiel: siehe [Übersicht über die verwaltete Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="f1a76-195">For example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="f1a76-196">Um die verwaltete Navigation zu implementieren, richten Sie Begriffe mit URLs ein, die der Navigationsstruktur der Website entsprechen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-196">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of the site.</span></span> <span data-ttu-id="f1a76-197">Die verwaltete Navigation kann sogar manuell kuratiert werden, um die Struktur Navigation in vielen Fällen zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-197">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="f1a76-198">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f1a76-198">For example:</span></span>

![SharePoint Online Websitestruktur](media/SPONavOptionsListOfSites.png)<span data-ttu-id="f1a76-200">)</span><span class="sxs-lookup"><span data-stu-id="f1a76-200">)</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="f1a76-201">Verwenden von Such gesteuerten clientseitigen Skripts</span><span class="sxs-lookup"><span data-stu-id="f1a76-201">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="f1a76-202">Eine allgemeine Klasse von Implementierungen für benutzerdefinierte Navigation umfasst Client gerenderte Entwurfsmuster, die einen lokalen Cache von Navigationsknoten speichern.</span><span class="sxs-lookup"><span data-stu-id="f1a76-202">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span>

<span data-ttu-id="f1a76-203">Diese Navigationsanbieter haben einige wichtige Vorteile:</span><span class="sxs-lookup"><span data-stu-id="f1a76-203">These navigation providers have a couple of key advantages:</span></span>

- <span data-ttu-id="f1a76-204">Sie funktionieren im Allgemeinen gut mit reaktionsschnellen Seitendesigns.</span><span class="sxs-lookup"><span data-stu-id="f1a76-204">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="f1a76-205">Sie sind extrem skalierbar und leistungsfähig, da Sie ohne Ressourcenkosten Rendern können (und nach einem Timeout im Hintergrund aktualisieren).</span><span class="sxs-lookup"><span data-stu-id="f1a76-205">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span>
- <span data-ttu-id="f1a76-206">Diese Navigationsanbieter können Navigationsdaten mithilfe verschiedener Strategien abrufen, von einfachen statischen Konfigurationen bis hin zu verschiedenen dynamischen Datenanbietern.</span><span class="sxs-lookup"><span data-stu-id="f1a76-206">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span>

<span data-ttu-id="f1a76-207">Ein Beispiel für einen Datenanbieter ist die Verwendung einer **Such gesteuerten Navigation**, die Flexibilität beim Aufzählen von Navigationsknoten und der effizienten Handhabung von Sicherheits Trimmungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f1a76-207">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span>

<span data-ttu-id="f1a76-208">Es gibt andere beliebte Optionen zum Erstellen **benutzerdefinierter Navigationsanbieter**.</span><span class="sxs-lookup"><span data-stu-id="f1a76-208">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="f1a76-209">Weitere Anleitungen zum Erstellen eines benutzerdefinierten Navigations Anbieters finden Sie unter [Navigationslösungen für SharePoint Online-Portale](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .</span><span class="sxs-lookup"><span data-stu-id="f1a76-209">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>

<span data-ttu-id="f1a76-210">Mithilfe der Suche können Sie die Indizes nutzen, die im Hintergrund mithilfe der kontinuierlichen Durchforstung aufgebaut werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-210">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="f1a76-211">Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse werden Sicherheits getrimmt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-211">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="f1a76-212">Dies ist im Allgemeinen schneller als bei der vordefinierten Navigation, wenn Sicherheits Kürzung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-212">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="f1a76-213">Die Verwendung der Suche für die strukturelle Navigation, insbesondere wenn Sie über eine komplexe Websitestruktur verfügen, beschleunigt die Ladezeit der Seite erheblich.</span><span class="sxs-lookup"><span data-stu-id="f1a76-213">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="f1a76-214">Der Hauptvorteil dieser über die verwaltete Navigation ist, dass Sie von Sicherheit Trimmen profitieren.</span><span class="sxs-lookup"><span data-stu-id="f1a76-214">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="f1a76-215">Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Gestaltungsvorlage und das Ersetzen des vordefinierten Navigations Codes durch benutzerdefinierten HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="f1a76-215">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="f1a76-216">Gehen Sie wie im folgenden Beispiel beschrieben vor, um den Navigationscode in der Datei `seattle.html`zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-216">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="f1a76-217">In diesem Beispiel werden Sie die `seattle.html` Datei öffnen und das gesamte-Element `id="DeltaTopNavigation"` durch benutzerdefinierten HTML-Code ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-217">In this example, you will open the `seattle.html` file and replace the whole element `id="DeltaTopNavigation"` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="f1a76-218">Beispiel: Ersetzen des Standard Navigations Codes in einer Gestaltungsvorlage</span><span class="sxs-lookup"><span data-stu-id="f1a76-218">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1. <span data-ttu-id="f1a76-219">Navigieren Sie zur Seite Websiteeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-219">Navigate to the Site Settings page.</span></span>
2. <span data-ttu-id="f1a76-220">Öffnen Sie den gestaltungsvorlagenkatalog, indem Sie auf **Masterseiten**klicken.</span><span class="sxs-lookup"><span data-stu-id="f1a76-220">Open the master page gallery by clicking **Master Pages**.</span></span>
3. <span data-ttu-id="f1a76-221">Von hier aus können Sie durch die Bibliothek navigieren und die Datei `seattle.master`herunterladen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-221">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4. <span data-ttu-id="f1a76-222">Bearbeiten Sie den Code mit einem Text-Editor, und löschen Sie den Codeblock im folgenden Screenshot.</span><span class="sxs-lookup"><span data-stu-id="f1a76-222">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Löschen des angezeigten Codeblocks](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="f1a76-224">Entfernen Sie den Code zwischen `<SharePoint:AjaxDelta id="DeltaTopNavigation">` den `<\SharePoint:AjaxDelta>` und-Tags, und ersetzen Sie ihn durch den folgenden Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="f1a76-224">Remove the code between the `<SharePoint:AjaxDelta id="DeltaTopNavigation">` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. <span data-ttu-id="f1a76-225">Ersetzen Sie die URL im Tag Loading Image Anchor am Anfang durch einen Link zu einem Bild laden in Ihrer Websitesammlung.</span><span class="sxs-lookup"><span data-stu-id="f1a76-225">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="f1a76-226">Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei um, und laden Sie Sie dann in den gestaltungsvorlagenkatalog hoch.</span><span class="sxs-lookup"><span data-stu-id="f1a76-226">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="f1a76-227">Dadurch wird eine neue Masterdatei generiert.</span><span class="sxs-lookup"><span data-stu-id="f1a76-227">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="f1a76-228">Dieser HTML-Code ist das grundlegende Markup, das von den Suchergebnissen aufgefüllt wird, die von JavaScript-Code zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-228">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="f1a76-229">Sie müssen den Code so bearbeiten, dass der Wert für var root = "Website Sammlungs-URL" geändert wird, wie im folgenden Codeausschnitt gezeigt:</span><span class="sxs-lookup"><span data-stu-id="f1a76-229">You will need to edit the code to change the value for var root = "site collection URL" as demonstrated in the following snippet:</span></span><br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. <span data-ttu-id="f1a76-230">Die Ergebnisse werden dem Self. Nodes-Array zugewiesen, und eine Hierarchie wird aus den Objekten mithilfe von LINQ. js erstellt, die die Ausgabe einem Array Self. Hierarchy zuordnet.</span><span class="sxs-lookup"><span data-stu-id="f1a76-230">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="f1a76-231">Dieses Array ist das Objekt, das an den HTML-Code gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="f1a76-231">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="f1a76-232">Dies erfolgt in der toggleView ()-Funktion, indem das Self-Objekt an die ko. applyBinding ()-Funktion übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="f1a76-232">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="f1a76-233">Dadurch wird das Hierarchie Array an den folgenden HTML-Code gebunden:</span><span class="sxs-lookup"><span data-stu-id="f1a76-233">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

<span data-ttu-id="f1a76-234">Die Ereignishandler für `mouseenter` und `mouseexit` werden zur Navigation auf oberster Ebene hinzugefügt, um die Unterwebsite-Dropdownmenüs zu verarbeiten, die in `addEventsToElements()` der-Funktion ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-234">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="f1a76-235">In unserem komplexen Navigations Beispiel zeigt eine neue Seitenauslastung ohne lokale Zwischenspeicherung, dass die Zeit, die auf dem Server aufgewendet wurde, aus der Benchmark-Struktur Navigation reduziert wurde, um ein ähnliches Ergebnis wie beim verwalteten Navigations Ansatz zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f1a76-235">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="f1a76-236">Informationen zur JavaScript-Datei...</span><span class="sxs-lookup"><span data-stu-id="f1a76-236">About the JavaScript file...</span></span>

>[!NOTE]
><span data-ttu-id="f1a76-237">Wenn Sie benutzerdefiniertes JavaScript verwenden, stellen Sie sicher, dass das öffentliche CDN aktiviert ist und sich die Datei an einem CDN-Speicherort befindet.</span><span class="sxs-lookup"><span data-stu-id="f1a76-237">If using custom JavaScript, ensure that public CDN is enabled and the file is in a CDN location.</span></span>

<span data-ttu-id="f1a76-238">Die gesamte JavaScript-Datei lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f1a76-238">The entire JavaScript file is as follows:</span></span>

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

<span data-ttu-id="f1a76-239">Um den oben gezeigten Code in der `jQuery $(document).ready` Funktion zusammenzufassen, `viewModel object` gibt es eine erstellte `loadNavigationNodes()` und dann die-Funktion für dieses Objekt wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-239">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="f1a76-240">Diese Funktion lädt entweder die zuvor erstellte Navigationshierarchie, die im lokalen HTML5-Speicher des Clientbrowsers gespeichert ist, oder Sie `queryRemoteInterface()`Ruft die Funktion auf.</span><span class="sxs-lookup"><span data-stu-id="f1a76-240">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="f1a76-241">`QueryRemoteInterface()`erstellt eine Anforderung mithilfe der `getRequest()` Funktion mit dem zuvor im Skript definierten Abfrageparameter und gibt dann Daten vom Server zurück.</span><span class="sxs-lookup"><span data-stu-id="f1a76-241">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="f1a76-242">Diese Daten sind im Wesentlichen ein Array aller Websites in der Websitesammlung, die als Daten Übertragungsobjekte mit verschiedenen Eigenschaften dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-242">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span>

<span data-ttu-id="f1a76-243">Diese Daten werden dann in die zuvor definierten `SPO.Models.NavigationNode` Objekte analysiert, die `Knockout.js` zum Erstellen beobachtbarer Eigenschaften für die Verwendung durch Datenbindung der Werte in den HTML-Code verwenden, den wir zuvor definiert haben.</span><span class="sxs-lookup"><span data-stu-id="f1a76-243">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span>

<span data-ttu-id="f1a76-244">Die Objekte werden dann in ein Ergebnisarray eingefügt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-244">The objects are then put into a results array.</span></span> <span data-ttu-id="f1a76-245">Dieses Array wird mithilfe von Knockout in JSON analysiert und im lokalen Browser Speicher gespeichert, um die Leistung bei zukünftigen Seitenlasten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="f1a76-245">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="f1a76-246">Vorteile dieses Ansatzes</span><span class="sxs-lookup"><span data-stu-id="f1a76-246">Benefits of this approach</span></span>

<span data-ttu-id="f1a76-247">Ein wesentlicher Vorteil [dieses Ansatzes](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) ist, dass die Navigation bei Verwendung des lokalen HTML5-Speichers lokal für den Benutzer gespeichert wird, wenn Sie das nächste Mal die Seite laden.</span><span class="sxs-lookup"><span data-stu-id="f1a76-247">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="f1a76-248">Bei der Verwendung der Such-API für die strukturelle Navigation erhalten wir deutliche Leistungsverbesserungen. Es erfordert jedoch einige technische Funktionen zum Ausführen und Anpassen dieser Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="f1a76-248">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span>

<span data-ttu-id="f1a76-249">In der [Beispielimplementierung](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)werden die Websites auf die gleiche Weise wie die standardmäßige Struktur Navigation sortiert. alphabetische Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="f1a76-249">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="f1a76-250">Wenn Sie von dieser Reihenfolge abweichen möchten, wäre es komplizierter zu entwickeln und zu warten.</span><span class="sxs-lookup"><span data-stu-id="f1a76-250">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="f1a76-251">Bei dieser Vorgehensweise müssen Sie auch von den unterstützten Masterseiten abweichen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-251">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="f1a76-252">Wenn die benutzerdefinierte Gestaltungsvorlage nicht beibehalten wird, verpasst ihre Website Updates und Verbesserungen, die Microsoft an den Gestaltungsvorlagen vornimmt.</span><span class="sxs-lookup"><span data-stu-id="f1a76-252">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="f1a76-253">Der [obige Code](#about-the-javascript-file) hat die folgenden Abhängigkeiten:</span><span class="sxs-lookup"><span data-stu-id="f1a76-253">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="f1a76-254">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="f1a76-254">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="f1a76-255">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="f1a76-255">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="f1a76-256">LINQ. js- https://linqjs.codeplex.com/oder GitHub.com/neuecc/LINQ.js</span><span class="sxs-lookup"><span data-stu-id="f1a76-256">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="f1a76-257">Die aktuelle Version von LinqJS enthält nicht die ByHierarchy-Methode, die im obigen Code verwendet wird, und der Navigationscode wird unterbrochen.</span><span class="sxs-lookup"><span data-stu-id="f1a76-257">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="f1a76-258">Um dies zu beheben, fügen Sie die folgende Methode zur Datei LINQ. js vor der `Flatten: function ()`-Verbindung hinzu.</span><span class="sxs-lookup"><span data-stu-id="f1a76-258">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="f1a76-259">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f1a76-259">Related topics</span></span>

[<span data-ttu-id="f1a76-260">Übersicht über die verwaltete Navigation in SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="f1a76-260">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[<span data-ttu-id="f1a76-261">Zwischenspeicherung und Leistung der Struktur Navigation</span><span class="sxs-lookup"><span data-stu-id="f1a76-261">Structural navigation caching and performance</span></span>](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
