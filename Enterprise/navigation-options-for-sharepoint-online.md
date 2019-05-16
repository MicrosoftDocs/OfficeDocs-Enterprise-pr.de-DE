---
title: Navigationsoptionen für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In diesem Artikel werden Navigations Options Websites beschrieben, in denen SharePoint Publishing in SharePoint Online aktiviert ist. Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus.
ms.openlocfilehash: 9bf2010000f14b173b63574fab4ee77cb772b3f4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069941"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="34c98-104">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c98-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="34c98-105">In diesem Artikel werden Navigations Options Websites beschrieben, in denen SharePoint Publishing in SharePoint Online aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="34c98-106">Die Auswahl und Konfiguration der Navigation wirkt sich erheblich auf die Leistung und Skalierbarkeit von Websites in SharePoint Online aus.</span><span class="sxs-lookup"><span data-stu-id="34c98-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="34c98-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="34c98-107">Overview</span></span>

<span data-ttu-id="34c98-108">Die Konfiguration des Navigations Anbieters kann sich erheblich auf die Leistung für den gesamten Standort auswirken, und es muss sorgfältig überlegt werden, einen Navigationsanbieter und eine Konfiguration auszuwählen, die für die Anforderungen einer SharePoint-Website effektiv skaliert werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="34c98-109">Es gibt zwei out-of-the-Box-Navigationsanbieter sowie benutzerdefinierte Navigations Implementierungen.</span><span class="sxs-lookup"><span data-stu-id="34c98-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="34c98-110">Die erste Option, [**verwaltete (Metadaten) Navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), wird empfohlen und ist eine der Standardoptionen in SharePoint Online; Es wird jedoch empfohlen, dass das Sicherheits Trimmen deaktiviert ist, sofern nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="34c98-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="34c98-111">Die Einschränkung der Sicherheit ist als Standardeinstellung für diesen Navigationsanbieter aktiviert. für viele Websites ist jedoch der Aufwand an Sicherheitseinschränkungen nicht erforderlich, da Navigationselemente häufig für alle Benutzer der Website konsistent sind.</span><span class="sxs-lookup"><span data-stu-id="34c98-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="34c98-112">Bei der empfohlenen Konfiguration zur Deaktivierung des Sicherheits Trimmens erfordert dieser Navigationsanbieter keine Aufzählung der Websitestruktur und ist hoch skalierbar mit akzeptablen Leistungseinbußen.</span><span class="sxs-lookup"><span data-stu-id="34c98-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="34c98-113">Die zweite Option, [**strukturelle Navigation**](#using-structural-navigation-in-sharepoint-online), **ist keine empfohlene Navigationsoption in SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="34c98-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="34c98-114">Dieser Navigationsanbieter wurde für eine lokale Topologie entwickelt, die nur in SharePoint Online unterstützt werden kann.</span><span class="sxs-lookup"><span data-stu-id="34c98-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="34c98-115">Während es einige zusätzliche Funktionen im Vergleich zu anderen Navigationsoptionen bietet, werden diese Features, einschließlich der Sicherheits Kürzung und der Aufzählung der Websitestruktur, zu Kosten von übermäßigen Server aufrufen und Auswirkungen auf die Skalierbarkeit und Leistung bei der Verwendung.</span><span class="sxs-lookup"><span data-stu-id="34c98-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="34c98-116">Websites, die eine Struktur Navigation verwenden und übermäßige Ressourcen nutzen, können möglicherweise eingeschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-116">Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="34c98-117">Neben den Out-of-the-Box-Navigations Anbietern haben viele Kunden erfolgreich Alternative benutzerdefinierte Navigations Implementierungen implementiert.</span><span class="sxs-lookup"><span data-stu-id="34c98-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="34c98-118">Eine allgemeine Klasse benutzerdefinierter Navigations Implementierungen umfasst Client gerenderte Entwurfsmuster, die einen lokalen Cache von Navigationsknoten speichern.</span><span class="sxs-lookup"><span data-stu-id="34c98-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="34c98-119">(Siehe **[Such gesteuerte clientseitige Skripterstellung](#using-search-driven-client-side-scripting)** in diesem Artikel.)</span><span class="sxs-lookup"><span data-stu-id="34c98-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="34c98-120">Diese Navigationsanbieter haben eine Reihe von wichtigen Vorteilen:</span><span class="sxs-lookup"><span data-stu-id="34c98-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="34c98-121">Sie funktionieren im Allgemeinen gut mit reaktionsfähigen Seitendesigns.</span><span class="sxs-lookup"><span data-stu-id="34c98-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="34c98-122">Sie sind extrem skalierbar und leistungsfähig, da Sie ohne Ressourcenkosten gerendert werden können (und nach einem Timeout im Hintergrund aktualisieren).</span><span class="sxs-lookup"><span data-stu-id="34c98-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="34c98-123">Diese Navigationsanbieter können Navigationsdaten mithilfe verschiedener Strategien abrufen, von einfachen statischen Konfigurationen bis hin zu verschiedenen dynamischen Datenanbietern.</span><span class="sxs-lookup"><span data-stu-id="34c98-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="34c98-124">Ein Beispiel für einen Datenanbieter ist die Verwendung einer **Such gesteuerten Navigation**, die Flexibilität beim Aufzählen der Navigationsknoten und beim effizienten Umgang mit dem Sicherheits Trimmen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="34c98-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="34c98-125">Es gibt weitere beliebte Optionen zum Erstellen **benutzerdefinierter Navigationsanbieter**.</span><span class="sxs-lookup"><span data-stu-id="34c98-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="34c98-126">Weitere Informationen zum Erstellen eines benutzerdefinierten Navigations Anbieters finden Sie unter [Navigation Solutions for SharePoint Online Portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) .</span><span class="sxs-lookup"><span data-stu-id="34c98-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="34c98-127">Vor-und Nachteile von SharePoint Online-Navigationsoptionen</span><span class="sxs-lookup"><span data-stu-id="34c98-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="34c98-128">In der folgenden Tabelle werden die vor-und Nachteile der einzelnen Optionen zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="34c98-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="34c98-129">Verwaltete Navigation</span><span class="sxs-lookup"><span data-stu-id="34c98-129">Managed navigation</span></span>  |<span data-ttu-id="34c98-130">Strukturelle Navigation</span><span class="sxs-lookup"><span data-stu-id="34c98-130">Structural navigation</span></span>  |<span data-ttu-id="34c98-131">Such gesteuerte Navigation</span><span class="sxs-lookup"><span data-stu-id="34c98-131">Search-driven navigation</span></span>  |<span data-ttu-id="34c98-132">Anbieter für die benutzerdefinierte Navigation</span><span class="sxs-lookup"><span data-stu-id="34c98-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="34c98-133">Experten</span><span class="sxs-lookup"><span data-stu-id="34c98-133">Pros:</span></span><br/><br/><span data-ttu-id="34c98-134">Einfache Wartung</span><span class="sxs-lookup"><span data-stu-id="34c98-134">Easy to maintain</span></span><br/><span data-ttu-id="34c98-135">Empfohlene Option</span><span class="sxs-lookup"><span data-stu-id="34c98-135">Recommended option</span></span><br/>     |<span data-ttu-id="34c98-136">Experten</span><span class="sxs-lookup"><span data-stu-id="34c98-136">Pros:</span></span><br/><br/><span data-ttu-id="34c98-137">Einfach zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="34c98-137">Easy to configure</span></span><br/><span data-ttu-id="34c98-138">Getrimmte Sicherheit</span><span class="sxs-lookup"><span data-stu-id="34c98-138">Security trimmed</span></span><br/><span data-ttu-id="34c98-139">Automatisch aktualisiert, wenn Inhalt hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="34c98-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="34c98-140">Experten</span><span class="sxs-lookup"><span data-stu-id="34c98-140">Pros:</span></span><br/><br/><span data-ttu-id="34c98-141">Getrimmte Sicherheit</span><span class="sxs-lookup"><span data-stu-id="34c98-141">Security trimmed</span></span><br/><span data-ttu-id="34c98-142">Wird automatisch aktualisiert, wenn Websites hinzugefügt werden</span><span class="sxs-lookup"><span data-stu-id="34c98-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="34c98-143">Schnelle Ladezeit und lokal zwischengespeicherte Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="34c98-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="34c98-144">Experten</span><span class="sxs-lookup"><span data-stu-id="34c98-144">Pros:</span></span><br/><br/><span data-ttu-id="34c98-145">Breitere Auswahl an verfügbaren Optionen</span><span class="sxs-lookup"><span data-stu-id="34c98-145">Wider choice of options available</span></span><br/><span data-ttu-id="34c98-146">Schnelles Laden bei richtiger Zwischenspeicherung</span><span class="sxs-lookup"><span data-stu-id="34c98-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="34c98-147">Viele Optionen funktionieren gut mit responsive Page Design</span><span class="sxs-lookup"><span data-stu-id="34c98-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="34c98-148">Nachteile</span><span class="sxs-lookup"><span data-stu-id="34c98-148">Cons:</span></span><br/><br/><span data-ttu-id="34c98-149">Nicht automatisch aktualisiert, um die Websitestruktur widerzuspiegeln</span><span class="sxs-lookup"><span data-stu-id="34c98-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="34c98-150">Auswirkungen auf die Leistung, wenn das Sicherheits Trimmen aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="34c98-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="34c98-151">Nachteile</span><span class="sxs-lookup"><span data-stu-id="34c98-151">Cons:</span></span><br/><br/><span data-ttu-id="34c98-152">**Nicht empfohlen**</span><span class="sxs-lookup"><span data-stu-id="34c98-152">**Not recommended**</span></span><br/><span data-ttu-id="34c98-153">**Auswirkungen auf Leistung und Skalierbarkeit**</span><span class="sxs-lookup"><span data-stu-id="34c98-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="34c98-154">**Einschränkungs Einschränkungen**</span><span class="sxs-lookup"><span data-stu-id="34c98-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="34c98-155">Nachteile</span><span class="sxs-lookup"><span data-stu-id="34c98-155">Cons:</span></span><br/><br/><span data-ttu-id="34c98-156">Keine Möglichkeit zum einfachen Sortieren von Websites</span><span class="sxs-lookup"><span data-stu-id="34c98-156">No ability to easily order sites</span></span><br/><span data-ttu-id="34c98-157">Erfordert die Anpassung der Gestaltungsvorlage (technische Fertigkeiten erforderlich)</span><span class="sxs-lookup"><span data-stu-id="34c98-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="34c98-158">Nachteile</span><span class="sxs-lookup"><span data-stu-id="34c98-158">Cons:</span></span><br/><br/><span data-ttu-id="34c98-159">Benutzerdefinierte Entwicklung ist erforderlich</span><span class="sxs-lookup"><span data-stu-id="34c98-159">Custom development is required</span></span><br/><span data-ttu-id="34c98-160">Die externe Datenquelle/der gespeicherte Cache wird benötigt, beispielsweise Azure.</span><span class="sxs-lookup"><span data-stu-id="34c98-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="34c98-161">Die am besten geeignete Option für Ihre Website hängt von Ihren Website Anforderungen und ihren technischen Funktionen ab.</span><span class="sxs-lookup"><span data-stu-id="34c98-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="34c98-162">Wenn Sie einen skalierbaren, out-of-Box-Navigationsanbieter wünschen, ist die verwaltete Navigation mit deaktiviertem Sicherheits Trimmen eine sehr gute Option.</span><span class="sxs-lookup"><span data-stu-id="34c98-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="34c98-163">Die Option für die verwaltete Navigation kann über die Konfiguration verwaltet werden, beinhaltet keine Code Anpassungsdateien und ist wesentlich schneller als die strukturelle Navigation.</span><span class="sxs-lookup"><span data-stu-id="34c98-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="34c98-164">Wenn Sie Sicherheits Kürzung benötigen und über eine benutzerdefinierte Gestaltungsvorlage verfügen und in der Organisation die Möglichkeit haben, die Änderungen, die in der standardgestaltungsvorlage für SharePoint Online auftreten können, zu verwalten, kann die Such gesteuerte Option zu einer besseren Benutzerfreundlichkeit.</span><span class="sxs-lookup"><span data-stu-id="34c98-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="34c98-165">Wenn Sie komplexere Anforderungen haben, ist möglicherweise ein benutzerdefinierter Navigationsanbieter die richtige Wahl.</span><span class="sxs-lookup"><span data-stu-id="34c98-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="34c98-166">Die strukturelle Navigation wird nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="34c98-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="34c98-167">Schließlich ist zu beachten, dass SharePoint zusätzliche Navigationsanbieter und-Funktionen für moderne SharePoint-Website Architekturen hinzufügt, die eine vereinfachte Websitehierarchie und ein Hub-and-Spoke-Modell mit SharePoint-Hub-Websites nutzen.</span><span class="sxs-lookup"><span data-stu-id="34c98-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="34c98-168">Dadurch können viele Szenarien erreicht werden, die nicht die Verwendung des SharePoint-Veröffentlichungsfeatures erfordern, und diese Navigations Konfigurationen sind für Skalierbarkeit und Latenz in SharePoint Online optimiert.</span><span class="sxs-lookup"><span data-stu-id="34c98-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="34c98-169">Beachten Sie, dass die Anwendung desselben Prinzips – Vereinfachung der Gesamtstruktur Ihrer SharePoint-Veröffentlichungswebsite in einer flachen Struktur – häufig auch die Gesamtleistung und Skalierung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="34c98-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="34c98-170">Das bedeutet, dass anstelle einer einzelnen Websitesammlung mit Hunderten von Websites (Unterwebs) ein besserer Ansatz für viele Websitesammlungen mit sehr wenigen Unterwebsites (Unterwebs) besteht.</span><span class="sxs-lookup"><span data-stu-id="34c98-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="34c98-171">Verwenden von verwalteter Navigation und Metadaten in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c98-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="34c98-172">Die verwaltete Navigation ist eine weitere out-of-the-Box-Option, die Sie verwenden können, um die meisten der gleichen Funktionen wie die strukturelle Navigation neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="34c98-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="34c98-173">Verwaltete Metadaten können so konfiguriert werden, dass die Sicherheits Kürzung aktiviert oder deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="34c98-174">Bei deaktivierter Sicherheits Kürzung ist die verwaltete Navigation ziemlich effizient, da Sie alle Navigationslinks mit einer Konstanten Anzahl von Server aufrufen lädt.</span><span class="sxs-lookup"><span data-stu-id="34c98-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="34c98-175">Das Aktivieren der Sicherheits Kürzung negiert jedoch einige Vorteile der verwalteten Navigation, und Kunden können sich für eine optimale Leistung und Skalierbarkeit für eine der benutzerdefinierten Navigationslösungen entscheiden.</span><span class="sxs-lookup"><span data-stu-id="34c98-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="34c98-176">Für viele Websites ist keine Sicherheits Kürzung erforderlich, da die Navigationsstruktur häufig für alle Benutzer der Website konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="34c98-177">Wenn die Sicherheits Kürzung deaktiviert ist und der Navigation ein Link hinzugefügt wird, auf den nicht alle Benutzer zugreifen können, wird die Verknüpfung weiterhin angezeigt, führt jedoch zu einer Meldung, dass der Zugriff verweigert wird.</span><span class="sxs-lookup"><span data-stu-id="34c98-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="34c98-178">Es besteht kein Risiko für versehentlichen Zugriff auf den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="34c98-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="34c98-179">Implementieren der verwalteten Navigation und der Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="34c98-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="34c98-180">Es gibt mehrere Artikel über docs.Microsoft.com zu den Details der verwalteten Navigation, beispielsweise siehe [Übersicht über die verwaltete Navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="34c98-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="34c98-181">Um die verwaltete Navigation zu implementieren, richten Sie Begriffe mit URLs ein, die der Navigationsstruktur der Website entsprechen.</span><span class="sxs-lookup"><span data-stu-id="34c98-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="34c98-182">Die verwaltete Navigation kann sogar manuell kuratiert werden, um die strukturelle Navigation in vielen Fällen zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="34c98-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="34c98-183">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="34c98-183">For example:</span></span>

![SharePoint Online-Websitestruktur](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="34c98-185">Das folgende Beispiel zeigt die Leistung der komplexen Navigation mithilfe der verwalteten Navigation.</span><span class="sxs-lookup"><span data-stu-id="34c98-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Leistung der komplexen Navigation mithilfe der verwalteten Navigation](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="34c98-187">Die Verwendung der verwalteten Navigation verbessert die Leistung im Vergleich zum strukturellen Navigations Ansatz.</span><span class="sxs-lookup"><span data-stu-id="34c98-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="34c98-188">Verwenden der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c98-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="34c98-189">Hierbei handelt es sich um die standardmäßig verwendete Navigation, die die einfachste Lösung ist, aber als solche eine kostspielige Leistungssteigerung zur Folge hat.</span><span class="sxs-lookup"><span data-stu-id="34c98-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="34c98-190">Sie erfordert keine Anpassung, und ein nicht technischer Benutzer kann problemlos Elemente hinzufügen, Elemente ausblenden und die Navigation auf der Einstellungsseite verwalten.</span><span class="sxs-lookup"><span data-stu-id="34c98-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="34c98-191">Dies gilt aber auch für die verwaltete Navigation, daher empfiehlt es sich, die verwaltete Navigation zu verwenden, da dies auch mit höherer Leistung problemlos verwaltet und gesteuert werden kann.</span><span class="sxs-lookup"><span data-stu-id="34c98-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Strukturelle Navigation mit ausgewählten Unterwebsites anzeigen](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="34c98-193">Aktivieren der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c98-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="34c98-194">Erläutern Sie, wie die Leistung in einer standardmäßigen SharePoint Online-Lösung mit struktureller Navigation und der Option Unterwebsites anzeigen aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="34c98-195">Nachfolgend finden Sie einen Screenshot der Einstellungen auf der Seite **Websiteeinstellungen** \> **Navigation**.</span><span class="sxs-lookup"><span data-stu-id="34c98-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Screenshot mit Unterwebsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="34c98-197">Analysieren der Leistung der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="34c98-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="34c98-198">Um die Leistung einer SharePoint-Seite zu analysieren, verwenden Sie die Registerkarte **Netzwerk** der F12-Entwicklertools in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="34c98-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Screenshot mit der Registerkarte "F12 dev Tools Network"](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="34c98-200">Klicken Sie auf der Registerkarte **Netzwerk** auf die ASPX-Seite, die geladen wird, und klicken Sie dann auf die Registerkarte **Details** .</span><span class="sxs-lookup"><span data-stu-id="34c98-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="34c98-201">![Screenshot mit der Registerkarte "Details"](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="34c98-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="34c98-202">Klicken Sie auf **Antwort Kopfzeilen**.</span><span class="sxs-lookup"><span data-stu-id="34c98-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="34c98-203">![Screenshot der Registerkarte "Details"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="34c98-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="34c98-204">SharePoint gibt einige nützliche Diagnoseinformationen in den Antwortheadern zurück.</span><span class="sxs-lookup"><span data-stu-id="34c98-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="34c98-205">Eine der nützlichsten Informationen ist **SPRequestDuration** , bei dem es sich um den Wert in Millisekunden handelt, der angibt, wie lange eine Anforderung zur Verarbeitung auf dem Server dauerte.</span><span class="sxs-lookup"><span data-stu-id="34c98-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="34c98-206">Im folgenden Screenshot zeigen Sie, dass unter **Websites** für die strukturelle Navigation deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="34c98-207">Dies bedeutet, dass es nur den Link Websitesammlung in der globalen Navigation gibt:</span><span class="sxs-lookup"><span data-stu-id="34c98-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="34c98-208">![Screenshot mit Ladezeiten als Anforderungsdauer](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="34c98-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="34c98-209">Der **SPRequestDuration** -Schlüssel hat einen Wert von 245 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="34c98-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="34c98-210">Dies stellt die Zeit für die Rückgabe der Anforderung dar.</span><span class="sxs-lookup"><span data-stu-id="34c98-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="34c98-211">Da es nur ein Navigationselement auf der Website gibt, ist dies ein guter Benchmark für die Leistung von SharePoint Online ohne starke Navigation.</span><span class="sxs-lookup"><span data-stu-id="34c98-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="34c98-212">Der nächste Screenshot zeigt, wie sich das Hinzufügen in den Unterwebsites auf diesen Schlüssel auswirkt.</span><span class="sxs-lookup"><span data-stu-id="34c98-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="34c98-213">![Screenshot mit einer Anforderungsdauer von 2502 MS](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="34c98-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="34c98-214">Durch das Hinzufügen der Unterwebsites wurde die Zeitdauer für die Rückgabe der Seitenanforderung für diese relativ einfache Beispielwebsite erheblich erhöht.</span><span class="sxs-lookup"><span data-stu-id="34c98-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="34c98-215">Komplexe Websitehierarchien, einschließlich Seiten in der Navigation und andere Konfigurations-und Topologie-Optionen, können diese Auswirkungen deutlich erhöhen.</span><span class="sxs-lookup"><span data-stu-id="34c98-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="34c98-216">Verwenden von Such gesteuerten clientseitigen Skripts</span><span class="sxs-lookup"><span data-stu-id="34c98-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="34c98-217">Mithilfe der Suche können Sie die Indizes nutzen, die im Hintergrund mithilfe der fortlaufenden Durchforstung aufgebaut werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="34c98-218">Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse werden mit Sicherheit gekürzt.</span><span class="sxs-lookup"><span data-stu-id="34c98-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="34c98-219">Dies ist im Allgemeinen schneller als bei der bereitgestellten Sicherheitseinschränkung.</span><span class="sxs-lookup"><span data-stu-id="34c98-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="34c98-220">Die Verwendung der Suche für die strukturelle Navigation, insbesondere bei einer komplexen Websitestruktur, beschleunigt die Ladezeit erheblich.</span><span class="sxs-lookup"><span data-stu-id="34c98-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="34c98-221">Der Hauptvorteil dieser über die verwaltete Navigation ist, dass Sie von Sicherheit Kürzung profitieren.</span><span class="sxs-lookup"><span data-stu-id="34c98-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="34c98-222">Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Gestaltungsvorlage und das Ersetzen des vordefinierten Navigations Codes durch benutzerdefinierten HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="34c98-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="34c98-223">Führen Sie die im folgenden Beispiel beschriebenen Schritte aus, um den Navigationscode in der Datei `seattle.html`zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="34c98-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="34c98-224">In diesem Beispiel öffnen Sie die `seattle.html` Datei und ersetzen das gesamte-Element `id=”DeltaTopNavigation”` durch benutzerdefinierten HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="34c98-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="34c98-225">Beispiel: Ersetzen Sie den Out-of-the-Box-Navigationscode auf einer Gestaltungsvorlage.</span><span class="sxs-lookup"><span data-stu-id="34c98-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="34c98-226">Navigieren Sie zur Seite Websiteeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="34c98-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="34c98-227">Öffnen Sie den gestaltungsvorlagenkatalog, indem Sie auf **Masterseiten**klicken.</span><span class="sxs-lookup"><span data-stu-id="34c98-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="34c98-228">Von hier aus können Sie durch die Bibliothek navigieren und die Datei `seattle.master`herunterladen.</span><span class="sxs-lookup"><span data-stu-id="34c98-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="34c98-229">Bearbeiten Sie den Code mit einem Text-Editor, und löschen Sie den Codeblock im folgenden Screenshot.</span><span class="sxs-lookup"><span data-stu-id="34c98-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Löschen des angezeigten Codeblocks](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="34c98-231">Entfernen Sie den Code zwischen `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` den `<\SharePoint:AjaxDelta>` und-Tags, und ersetzen Sie ihn durch den folgenden Ausschnitt:</span><span class="sxs-lookup"><span data-stu-id="34c98-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
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
6. <span data-ttu-id="34c98-232">Ersetzen Sie die URL im Tag "Loading Image Anchor" am Anfang mit einem Link zu einem Ladebild in Ihrer Websitesammlung.</span><span class="sxs-lookup"><span data-stu-id="34c98-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="34c98-233">Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei um, und laden Sie Sie dann in den gestaltungsvorlagenkatalog hoch.</span><span class="sxs-lookup"><span data-stu-id="34c98-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="34c98-234">Dadurch wird eine neue Master-Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="34c98-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="34c98-235">Dieser HTML-Code ist das grundlegende Markup, das von den Suchergebnissen ausgefüllt wird, die von JavaScript-Quellcode zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="34c98-236">Sie müssen den Code bearbeiten, um den Wert für var root = "Website Sammlungs-URL" wie im folgenden Codeausschnitt gezeigt zu ändern:</span><span class="sxs-lookup"><span data-stu-id="34c98-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="34c98-237">Die Ergebnisse werden dem Self. Nodes-Array zugewiesen, und eine Hierarchie besteht aus den Objekten mithilfe von LINQ. js, die die Ausgabe einem Array Self. Hierarchy zuweisen.</span><span class="sxs-lookup"><span data-stu-id="34c98-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="34c98-238">Dieses Array ist das Objekt, das an den HTML-Code gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="34c98-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="34c98-239">Dies erfolgt in der toggleView ()-Funktion durch Übergeben des Self-Objekts an die ko. applyBinding ()-Funktion.</span><span class="sxs-lookup"><span data-stu-id="34c98-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="34c98-240">Dadurch wird das Hierarchie Array an den folgenden HTML-Code gebunden:</span><span class="sxs-lookup"><span data-stu-id="34c98-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="34c98-241">Die Ereignishandler für `mouseenter` und `mouseexit` werden der Navigation auf oberster Ebene hinzugefügt, um die Dropdownmenüs Unterwebsite zu behandeln, die in der `addEventsToElements()` Funktion ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="34c98-242">In unserem Beispiel für eine komplexe Navigation zeigt ein neuer seitenladevorgang ohne lokale Zwischenspeicherung an, wie lange der Server aufgrund der Benchmark-Struktur Navigation gekürzt wurde, um ein ähnliches Ergebnis wie beim verwalteten Navigations Ansatz zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="34c98-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="34c98-243">Informationen zur JavaScript-Datei...</span><span class="sxs-lookup"><span data-stu-id="34c98-243">About the JavaScript file...</span></span>

<span data-ttu-id="34c98-244">Die gesamte JavaScript-Datei lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="34c98-244">The entire JavaScript file is as follows:</span></span>

```
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

    // ByHierarchy method breaks the sorting in chrome and firefix 
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

<span data-ttu-id="34c98-245">Zum Zusammenfassen des oben gezeigten Codes `jQuery $(document).ready` in der Funktion gibt `viewModel object` es eine erstellte und `loadNavigationNodes()` dann die Funktion für dieses Objekt aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="34c98-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="34c98-246">Diese Funktion lädt die zuvor erstellte Navigationshierarchie, die im lokalen HTML5-Speicher des Clientbrowsers gespeichert ist, oder ruft die `queryRemoteInterface()`Funktion auf.</span><span class="sxs-lookup"><span data-stu-id="34c98-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="34c98-247">`QueryRemoteInterface()`erstellt eine Anforderung mithilfe der `getRequest()` -Funktion mit dem zuvor im Skript definierten Abfrageparameter und gibt dann Daten vom Server zurück.</span><span class="sxs-lookup"><span data-stu-id="34c98-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="34c98-248">Diese Daten sind im Wesentlichen ein Array aller Websites in der Websitesammlung, die als datentransferobjekte mit verschiedenen Eigenschaften dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="34c98-249">Diese Daten werden dann in die zuvor definierten `SPO.Models.NavigationNode` Objekte analysiert, die `Knockout.js` zum Erstellen von beobachtbaren Eigenschaften für die Verwendung durch Datenbindung der Werte in den zuvor definierten HTML-Code verwenden.</span><span class="sxs-lookup"><span data-stu-id="34c98-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="34c98-250">Die Objekte werden dann in einem Ergebnisarray platziert.</span><span class="sxs-lookup"><span data-stu-id="34c98-250">The objects are then put into a results array.</span></span> <span data-ttu-id="34c98-251">Dieses Array wird in JSON mithilfe von Knockout analysiert und im lokalen Browser Speicher gespeichert, um die Leistung bei zukünftigen Seitenlasten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="34c98-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="34c98-252">Vorteile dieses Ansatzes</span><span class="sxs-lookup"><span data-stu-id="34c98-252">Benefits of this approach</span></span>

<span data-ttu-id="34c98-253">Ein wesentlicher Vorteil [dieses](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) Ansatzes besteht darin, dass die Navigation lokal für den Benutzer gespeichert wird, wenn Sie die Seite das nächste Mal laden.</span><span class="sxs-lookup"><span data-stu-id="34c98-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="34c98-254">Bei der Verwendung der Such-API für die strukturelle Navigation werden wichtige Leistungsverbesserungen erzielt. Es sind jedoch einige technische Funktionen zum Ausführen und Anpassen dieser Funktionalität erforderlich.</span><span class="sxs-lookup"><span data-stu-id="34c98-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="34c98-255">In der [Beispielimplementierung](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)werden die Websites auf die gleiche Weise wie die Out-of-the-Box-Struktur Navigation sortiert; alphabetische Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="34c98-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="34c98-256">Wenn Sie von dieser Reihenfolge abweichen möchten, wäre es komplizierter zu entwickeln und zu warten.</span><span class="sxs-lookup"><span data-stu-id="34c98-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="34c98-257">Außerdem müssen Sie von den unterstützten Gestaltungsvorlagen abweichen.</span><span class="sxs-lookup"><span data-stu-id="34c98-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="34c98-258">Wenn die benutzerdefinierte Gestaltungsvorlage nicht verwaltet wird, verpassen Ihre Website Updates und Verbesserungen, die von Microsoft an den Gestaltungsvorlagen vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="34c98-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="34c98-259">Der [obige Code](#about-the-javascript-file) weist die folgenden Abhängigkeiten auf:</span><span class="sxs-lookup"><span data-stu-id="34c98-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="34c98-260">jQueryhttp://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="34c98-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="34c98-261">KnockoutJS -http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="34c98-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="34c98-262">LINQ. js- http://linqjs.codeplex.com/oder GitHub.com/neuecc/LINQ.js</span><span class="sxs-lookup"><span data-stu-id="34c98-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="34c98-263">Die aktuelle Version von LinqJS enthält nicht die im obigen Code verwendete ByHierarchy-Methode und unterbricht den Navigationscode.</span><span class="sxs-lookup"><span data-stu-id="34c98-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="34c98-264">Um dies zu beheben, fügen Sie die folgende Methode zur Datei "LINQ. js" `Flatten: function ()`vor der Leitung hinzu.</span><span class="sxs-lookup"><span data-stu-id="34c98-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
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
  
## <a name="related-topics"></a><span data-ttu-id="34c98-265">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="34c98-265">Related topics</span></span>

[<span data-ttu-id="34c98-266">Übersicht über die verwaltete Navigation in SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="34c98-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

