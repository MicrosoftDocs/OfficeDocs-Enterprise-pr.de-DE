---
title: Navigationsoptionen für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: In diesem Artikel wird beschrieben, wie die Seitenladezeiten für SharePoint Online zu verbessern, verwaltete Navigation oder suchgesteuerte Navigation im klassischen Veröffentlichung verwenden.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540988"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="d8d44-103">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d8d44-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="d8d44-104">In diesem Artikel wird beschrieben, wie die Seitenladezeiten für SharePoint Online zu verbessern, verwaltete Navigation oder suchgesteuerte Navigation im klassischen Veröffentlichung verwenden.</span><span class="sxs-lookup"><span data-stu-id="d8d44-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="d8d44-105">SharePoint Online mit klassischen Veröffentlichung aktiviert hat zwei Navigationsbereiche. Globale Navigation und aktuelle Navigation.</span><span class="sxs-lookup"><span data-stu-id="d8d44-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="d8d44-106">Globale Navigation ist im Menü der oberen Navigationsleiste während aktuelle Navigation auf der Seite oder im Kontext links/rechts Navigation hängt von der Sprachkonfiguration und Gestaltungsvorlage verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d8d44-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="d8d44-107">Navigation kann für das gesamte Portal Leistung beeinträchtigen, wie es häufig für die gesamte Portal Verwendung konfiguriert ist und daher ein wichtiger Bestandteil einer SharePoint-Website ist.</span><span class="sxs-lookup"><span data-stu-id="d8d44-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="d8d44-108">Strukturelle Navigation ist nicht die Navigationsoption empfohlene in SharePoint Online, wie es für eine lokalen-Topologie mit Einschränkung aus Sicherheitsgründen entwickelt wurde und Design bewirkt, dass aufgrund einer Anrufe und wirkt sich auf Leistung, wenn sie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d8d44-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="d8d44-p101">Dass Entwurf geändert hat, mit der Einführung von modernen SharePoint-Websites, in denen modernen verfügt über eine vereinfachte vereinfachte Websitehierarchie. Dies wurde mit einer vereinfachten Hierarchie Navigation vereinfacht, die Leistungsprobleme im Zusammenhang mit der Navigation gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="d8d44-p102">Es gibt zwei Optionen für die wichtigsten Out-of-Box Websitenavigation in SharePoint als auch eine dritte, benutzerdefinierte, suchbasierte Ansatz. Alternativ ist auch häufig Option und eine vierte eine benutzerdefinierte Navigation-Datenanbieter erstellen. Überprüfen Sie [Navigation Lösungen für SharePoint Online-Portale](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) Hinweise auf eine benutzerdefinierte Navigationsanbieter.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="d8d44-114">Jede Option hat vor- und Nachteile, wie in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d8d44-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="d8d44-115">**Strukturelle Navigation**</span><span class="sxs-lookup"><span data-stu-id="d8d44-115">**Structural navigation**</span></span>|<span data-ttu-id="d8d44-116">**Verwaltete Navigation**</span><span class="sxs-lookup"><span data-stu-id="d8d44-116">**Managed navigation**</span></span>|<span data-ttu-id="d8d44-117">**Suchgesteuerte Navigation**</span><span class="sxs-lookup"><span data-stu-id="d8d44-117">**Search-driven navigation**</span></span>||<span data-ttu-id="d8d44-118">**Benutzerdefinierte Navigation-Anbieter**</span><span class="sxs-lookup"><span data-stu-id="d8d44-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="d8d44-119">Vorteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-119">Pros:</span></span>  <br/>  <span data-ttu-id="d8d44-120">Einfach zu konfigurieren</span><span class="sxs-lookup"><span data-stu-id="d8d44-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="d8d44-121">Sicherheitskürzung</span><span class="sxs-lookup"><span data-stu-id="d8d44-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="d8d44-122">Automatische Aktualisierung beim Hinzufügen von Websites</span><span class="sxs-lookup"><span data-stu-id="d8d44-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="d8d44-123">Vorteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-123">Pros:</span></span>  <br/>  <span data-ttu-id="d8d44-124">Einfach zu verwalten</span><span class="sxs-lookup"><span data-stu-id="d8d44-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="d8d44-125">Empfohlene option</span><span class="sxs-lookup"><span data-stu-id="d8d44-125">Recommended option</span></span>  <br/> | <span data-ttu-id="d8d44-126">Vorteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-126">Pros:</span></span>  <br/>  <span data-ttu-id="d8d44-127">Sicherheitskürzung</span><span class="sxs-lookup"><span data-stu-id="d8d44-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="d8d44-128">Automatische Aktualisierung beim Hinzufügen von Websites</span><span class="sxs-lookup"><span data-stu-id="d8d44-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="d8d44-129">Schnelle Ladezeiten und lokal zwischengespeicherte Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="d8d44-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="d8d44-130">Vorteile</span><span class="sxs-lookup"><span data-stu-id="d8d44-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="d8d44-131">Größere Auswahl / Optionen zur Verfügung</span><span class="sxs-lookup"><span data-stu-id="d8d44-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="d8d44-132">Laden von fast beim Zwischenspeichern wird ordnungsgemäß verwendet.</span><span class="sxs-lookup"><span data-stu-id="d8d44-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="d8d44-133">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-133">Cons:</span></span>  <br/> <span data-ttu-id="d8d44-134">**Nicht empfohlen**</span><span class="sxs-lookup"><span data-stu-id="d8d44-134">**Not recommended**</span></span> <br/> <span data-ttu-id="d8d44-135">**Auf die Leistung auswirkt**</span><span class="sxs-lookup"><span data-stu-id="d8d44-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="d8d44-136">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-136">Cons:</span></span>  <br/>  <span data-ttu-id="d8d44-137">Keine automatische Aktualisierung zur Abbildung der Websitestruktur</span><span class="sxs-lookup"><span data-stu-id="d8d44-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="d8d44-138">Leistung auswirkt, wenn die Einschränkung aus Sicherheitsgründen aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="d8d44-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="d8d44-139">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-139">Cons:</span></span>  <br/>  <span data-ttu-id="d8d44-140">Keine Möglichkeit, Websites einfach anzuordnen</span><span class="sxs-lookup"><span data-stu-id="d8d44-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="d8d44-141">Erfordert die Anpassung der Masterseite (technische Kenntnisse erforderlich)</span><span class="sxs-lookup"><span data-stu-id="d8d44-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="d8d44-142">Nachteile:</span><span class="sxs-lookup"><span data-stu-id="d8d44-142">Cons:</span></span>  <br/>  <span data-ttu-id="d8d44-143">Benutzerdefinierte Entwicklung ist erforderlich</span><span class="sxs-lookup"><span data-stu-id="d8d44-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="d8d44-144">Externe Datenquelle / Cache gespeichert ist erforderlich, z. B. Azure</span><span class="sxs-lookup"><span data-stu-id="d8d44-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="d8d44-p103">Die am besten geeignete Option für Ihre Website hängen auf Ihren Anforderungen Website und auf Ihrer Eignung. Wenn Sie eine benutzerdefinierte Gestaltungsvorlage mit vertraut sind und einige Funktionen in der Organisation, um die Änderungen zu verwalten, die die Standardgestaltungsvorlage für SharePoint Online auftreten, erzeugt die Option suchbasierte die beste benutzerumgebung. Wenn Sie einen einfachen Kompromiss zwischen die strukturelle Out-of-Box-Navigation und Suche möchten, ist die verwaltete Navigation eine sehr gute Wahl. Die Option verwaltete Navigation über verwaltet Konfiguration umfassen nicht Anpassungsdateien Code, und es ist wesentlich schneller als die strukturelle Out-of-Box-Navigation.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="d8d44-p104">Die allgemeine Struktur der klassische Portal ähnlich wie in modernem vereinfachen, unterstützt die allgemeine Leistung und Skalierung sowie. Dies bedeutet, der anstelle einer einzelnen Websitesammlung mit Hunderten / Tausende von Standorten (Unterwebsites), einen besseren Ansatz besteht darin, zahlreiche Websitesammlungen mit sehr wenige Unterwebsites (Unterwebsites).</span><span class="sxs-lookup"><span data-stu-id="d8d44-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="d8d44-151">Dies bietet zusätzliche Optionen für die Skalierung im Dienst, vermeidet eine große Datenbank Inbetriebnahme alle Inhalte und letztlich größere Flexibilität für Navigation und größerer Sicherheit.</span><span class="sxs-lookup"><span data-stu-id="d8d44-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="d8d44-152">Verwenden der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d8d44-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="d8d44-p105">Die Out-of-Box-Navigation standardmäßig verwendet und ist die einfachste Lösung Dies ist ein Kompromiss teurer Leistung als solche hat. Es muss keine Anpassung und einen technischen Benutzer kann auch problemlos Elemente hinzufügen, Ausblenden von Elementen und verwalten die Navigation auf der Seite Einstellungen. Hierbei handelt es sich jedoch auch True für die verwaltete Navigation, daher wird empfohlen, verwaltete Navigation als, kann auch auf einfache Weise werden verwaltet und gesteuert sowie.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="d8d44-156">Aktivieren der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d8d44-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="d8d44-p106">Erläutern, wie die Leistung in einer standard-SharePoint Online-Lösung mit strukturellen Navigation und anzeigen die Option Unterwebsites aktiviert. Im folgenden ist ein Screenshot Einstellungen finden Sie auf der Seite **Websiteeinstellungen** \> **Navigation**.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Screenshot mit Unterwebsites](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="d8d44-160">Analysieren der Leistung der strukturellen Navigation in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d8d44-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="d8d44-161">Zum Analysieren der Leistung einer SharePoint-Seite verwenden Sie die Registerkarte **Netzwerk** der F12-Entwicklertools in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d8d44-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Screenshot mit Registerkarte "F12 Dev Tools-Netzwerk"](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="d8d44-163">Klicken Sie auf der Registerkarte **Netzwerk** auf die ASPX-Seite, die geladen wird, und klicken Sie dann auf die Registerkarte **Details**.</span><span class="sxs-lookup"><span data-stu-id="d8d44-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Screenshot der Detailregisterkarte](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="d8d44-165">Klicken Sie auf **Antwortheader**.</span><span class="sxs-lookup"><span data-stu-id="d8d44-165">Click **Response headers**.</span></span>
  
![Screenshot der Registerkarte "Details"](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="d8d44-p107">SharePoint gibt einige nützliche Diagnoseinformationen in seinen Antwortheadern zurück. Einer der nützlichsten Werte ist **SPRequestDuration**. Er gibt in Millisekunden an, wie lange die Verarbeitung einer Anforderung auf dem Server dauerte.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="d8d44-p108">Im folgenden Screenshot **Unterwebsites anzeigen** ist für die strukturelle Navigation nicht aktiviert. Dies bedeutet, dass nur die Site Collection Verknüpfung in der globalen Navigation vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="d8d44-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Screenshot mit Ladezeiten als Anforderungsdauer](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="d8d44-p109">Der Schlüssel für **SPRequestDuration** hat einen Wert von 245 Millisekunden. Dies ist die Zeit die Anforderung zurückgegeben. Da nur ein Navigationselement auf der Website vorhanden ist, ist dies eine gute Richtlinie für ohne extra fette Navigation wie SharePoint Online ausführt. Der nächste Screenshot zeigt, wie in Unterwebsites Hinzufügen dieser Schlüssel auswirkt.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Screenshot mit einer Anforderungsdauer von 2.502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="d8d44-177">Das Hinzufügen von Unterwebsites hat die für die Rückgabe der Seitenanforderung benötigte Zeit deutlich erhöht.</span><span class="sxs-lookup"><span data-stu-id="d8d44-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="d8d44-178">Die Vorteile der Verwendung der regulären strukturierten Navigation ist, dass Sie auf einfache Weise organisieren Sie die Reihenfolge, Ausblenden von Websites, Seiten hinzufügen können, die Ergebnisse werden Sicherheit verkürzt und Sie werden nicht aus der unterstützten Gestaltungsvorlagen in SharePoint Online verwendeten abweichen.</span><span class="sxs-lookup"><span data-stu-id="d8d44-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="d8d44-179">Verwenden der verwalteten Navigation und verwalteter Metadaten in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d8d44-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="d8d44-180">Die verwaltete Navigation ist eine weitere sofort nutzbare Option, die Sie verwenden können, um die gleiche Art von Funktionalität wie bei der strukturellen Navigation neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d8d44-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="d8d44-p110">Die Vorteile der Verwendung verwalteter Metadaten ist wesentlich schneller als die Verwendung von Inhalt nach Abfrage zum Erstellen der Websitenavigation Datenabfrage werden kann. Es handelt sich um viel schneller besteht keine Möglichkeit trim Sicherheit auf die Ergebnisse also wenn ein Benutzer Zugriff auf eine bestimmte Website, nicht der Link zeigt immer noch Obgleich wird dazu führen, dass eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="d8d44-183">**So implementieren Sie die verwaltete Navigation und die Ergebnisse**</span><span class="sxs-lookup"><span data-stu-id="d8d44-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="d8d44-184">Es gibt mehrere Artikel auf TechNet zu den Details der verwalteten Navigation beispielsweise, finden Sie unter [Übersicht über die verwaltete Navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="d8d44-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="d8d44-p111">Um die verwaltete Navigation implementieren zu können, benötigen Sie Administratorberechtigungen für den Terminologiespeicher. Durch Einrichten von Begriffen mit URLs, die der Struktur einer Websitesammlung entsprechen, kann die verwaltete Navigation anstatt einer strukturellen Navigation verwendet werden. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d8d44-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Screenshot von Subsite1-Beispiel](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="d8d44-189">Das folgende Beispiel zeigt die Leistung der komplexen Navigation bei Verwendung der verwalteten Navigation.</span><span class="sxs-lookup"><span data-stu-id="d8d44-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Screenshot von SPRequestDuration-Beispiel](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="d8d44-191">Mithilfe der verwalteten Navigation lässt sich die Leistung im Vergleich zum Ansatz der strukturellen Navigation "Inhalt von Abfrage" konsistent verbessern.</span><span class="sxs-lookup"><span data-stu-id="d8d44-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="d8d44-192">Verwenden einer suchbasierten, clientseitigen Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="d8d44-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="d8d44-p112">Mithilfe der Suchfunktion können Sie die Indizes nutzen, die im Hintergrund mithilfe der kontinuierlichen Durchforstung aufgebaut werden. Dies bedeutet, dass es keine übermäßig vielen Inhaltsabfragen gibt. Die Suchergebnisse werden aus dem Suchindex abgerufen, und die Ergebnisse werden sicherheitsgekürzt. Dies geht schneller als die Verwendung regulärer Inhaltsabfragen. Wenn Sie die Suche für strukturelle Navigation verwenden, insbesondere dann, wenn Sie über eine komplexe Websitestruktur verfügen, lässt sich das Laden von Seiten erheblich beschleunigen. Der Hauptvorteil dieser überverwalteten Navigation ist, dass Sie von der Sicherheitskürzung profitieren.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="d8d44-p113">Dieser Ansatz umfasst das Erstellen einer benutzerdefinierten Masterseite und die Ersetzung sofort nutzbaren Navigationscodes durch benutzerdefiniertes HTML. Gehen Sie folgendermaßen vor, um den Navigationscode in der Datei "seattle.html" zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="d8d44-201">In diesem Beispiel wird öffnen Sie die Datei seattle.html und ersetzt das gesamte Element **Id = "DeltaTopNavigation"** mit der benutzerdefinierten HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="d8d44-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="d8d44-202">**Beispiel: So ersetzen Sie den sofort nutzbaren Navigationscode auf einer Masterseite**</span><span class="sxs-lookup"><span data-stu-id="d8d44-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="d8d44-203">Navigieren Sie zur Seite **Websiteeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d8d44-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="d8d44-204">Öffnen Sie durch Klicken auf **Masterseiten** den Masterseitenkatalog.</span><span class="sxs-lookup"><span data-stu-id="d8d44-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="d8d44-205">Von hier aus können Sie durch die Bibliothek navigieren und die Datei **seattle.master** herunterladen.</span><span class="sxs-lookup"><span data-stu-id="d8d44-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="d8d44-206">Bearbeiten Sie den Code mit einem Texteditor, und löschen Sie den Codeblock im folgenden Screenshot.</span><span class="sxs-lookup"><span data-stu-id="d8d44-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Screenshot von zu löschendem DeltaTopNavigation-Code](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="d8d44-208">Entfernen Sie den Code zwischen den \<SharePoint:AjaxDelta Id = "DeltaTopNavigation"\> und \<\SharePoint:AjaxDelta\> tags und ersetzt ihn durch den folgenden Codeausschnitt:</span><span class="sxs-lookup"><span data-stu-id="d8d44-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="d8d44-p114">Ersetzen Sie die URL in das Laden image Anchortag am Anfang, mit einem Link zu einem Bild laden in Ihrer Websitesammlung. Nachdem Sie die Änderungen vorgenommen haben, benennen Sie die Datei, und klicken Sie dann auf den Gestaltungsvorlagenkatalog hochladen. Dadurch wird eine neue Master-Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="d8d44-p115">Dieser HTML-Code wird die grundlegende Markup, das von der Suchergebnisse aus JavaScript-Code aufgefüllt wird. Sie müssen so bearbeiten Sie den folgenden Code zum Ändern des Werts für die `var root = "site collection URL"` wie im folgenden Codeausschnitt veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="d8d44-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="d8d44-214">Die gesamte JavaScript-Datei sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="d8d44-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="d8d44-215">$("li.level1").mouseover (Funktion {)</span><span class="sxs-lookup"><span data-stu-id="d8d44-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="d8d44-216">Var Position = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="d8d44-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="d8d44-217">$(this).find("ul.level2").css ({Breite: 100; Links: top-position.left + 10: 50});</span><span class="sxs-lookup"><span data-stu-id="d8d44-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="d8d44-218">.MouseOut (Funktion {)</span><span class="sxs-lookup"><span data-stu-id="d8d44-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="d8d44-219">$(this).find("ul.level2").css ({linken:-99999, Top: 0});</span><span class="sxs-lookup"><span data-stu-id="d8d44-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="d8d44-220">});</span><span class="sxs-lookup"><span data-stu-id="d8d44-220"></span></span>
  
<span data-ttu-id="d8d44-221">$("li.level2").mouseover (Funktion {)</span><span class="sxs-lookup"><span data-stu-id="d8d44-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="d8d44-222">Var Position = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="d8d44-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="d8d44-223">Console.log(JSON.stringify(Position));</span><span class="sxs-lookup"><span data-stu-id="d8d44-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="d8d44-224">$(this).find("ul.level3").css ({Breite: 100; Links: position.left + 95, top: position.top});</span><span class="sxs-lookup"><span data-stu-id="d8d44-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="d8d44-225">.MouseOut (Funktion {)</span><span class="sxs-lookup"><span data-stu-id="d8d44-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="d8d44-226">$(this).find("ul.level3").css ({linken:-99999, Top: 0});</span><span class="sxs-lookup"><span data-stu-id="d8d44-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="d8d44-227">});</span><span class="sxs-lookup"><span data-stu-id="d8d44-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="d8d44-p116">Im nächsten Schritt die Ergebnisse werden in das Array **[self.nodes]** zugewiesen und eine Hierarchie basiert der Objekte mit linq.js ein Array **[self.heirarchy]** die Ausgabe zuweisen. Dieses Array ist das Objekt, das an den HTML-Code gebunden ist. Dies in der Funktion **[toggleView()]** erfolgt, indem Sie das Self-Objekt an die Funktion **[ko.applyBinding()]** übergeben. Dies führt dann Hierarchie Array folgenden HTML-Code gebunden werden:</span><span class="sxs-lookup"><span data-stu-id="d8d44-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="d8d44-232">Schließlich werden die Ereignishandler für **[Mouseenter]** und **[Mouseexit]** zum der Navigation auf oberster Ebene der Unterwebsite Dropdownmenüs behandeln hinzugefügt, die in der Funktion **[addEventsToElements()]** erfolgt.</span><span class="sxs-lookup"><span data-stu-id="d8d44-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="d8d44-233">Im folgenden Screenshot können die Ergebnisse der Navigation angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="d8d44-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Screenshot der Ergebnisse der navigation](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="d8d44-235">In unserem komplexen Navigationsbeispiel zeigt das Laden einer leeren Seite ohne lokales Zwischenspeichern, dass die Zeit auf dem Server von der strukturellen Benchmarknavigation auf ein ähnliches Ergebnis reduziert wurde wie beim Ansatz der verwalteten Navigation.</span><span class="sxs-lookup"><span data-stu-id="d8d44-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Screenshot von SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="d8d44-237">Ein wesentlicher Vorteil dieses Ansatzes ist, dass durch Verwendung des lokalen HTML5-Speichers die Navigation lokal für den Benutzer gespeichert wird, wenn er die Seite das nächste Mal lädt.</span><span class="sxs-lookup"><span data-stu-id="d8d44-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="d8d44-p117">Wir profitieren von einer wesentlichen Leistungssteigerung, wenn wir die Such-API für die strukturelle Navigation verwenden, allerdings müssen dafür technische Funktionen ausgeführt und angepasst werden. Bei der Beispielimplementierung werden die Websites auf die gleiche Weise angeordnet wie bei der sofort nutzbaren strukturellen Navigation, nämlich in alphabetischer Reihenfolge. Wenn Sie von dieser Reihenfolge abweichen möchten, ist dies komplizierter zu entwickeln und zu verwalten. Außerdem müssen Sie dann auch von den unterstützten Masterseiten abweichen. Wenn die benutzerdefinierte Masterseite nicht verwaltet wird, verpassen Sie für Ihre Website Updates und Verbesserungen, die Microsoft an den Masterseiten vornimmt.</span><span class="sxs-lookup"><span data-stu-id="d8d44-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="d8d44-243">Im oben stehenden Code gelten die folgenden Abhängigkeiten:</span><span class="sxs-lookup"><span data-stu-id="d8d44-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="d8d44-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="d8d44-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="d8d44-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="d8d44-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="d8d44-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), oder [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="d8d44-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="d8d44-p118">Die aktuelle Version von LinqJS enthält nicht die ByHierarchy-Methode verwendet, die im obigen Code und unterbricht den Navigationscode. Um dieses Problem zu beheben, fügen Sie die folgende Methode zur Datei Linq.js vor der Zeile "Flatten: Funktion ()".</span><span class="sxs-lookup"><span data-stu-id="d8d44-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


