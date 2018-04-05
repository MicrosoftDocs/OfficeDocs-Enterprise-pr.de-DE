---
title: Konfigurieren der Suche für OneDrive für Unternehmen Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Konfigurieren der Suche in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 5aa1e9eb189e00dbed8f575e88046b661341bf52
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="d8f95-103">Konfigurieren der Suche für OneDrive für Unternehmen Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="d8f95-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="d8f95-104">In einer Umgebung mit mehreren geografisch SharePoint Online (SPO) eine Organisation kann ein Office 365-Mandanten, aber ihre SharePoint-Inhalte an mehreren geografischen Standorten - speichern einem zentralen Standort und mindestens Satellitenassemblys Geo-Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="d8f95-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="d8f95-p101">Jeden geografischen Standort verfügt über eine eigene Suchindex und Suchcenter. Wenn ein Benutzer sucht, wird die Abfrage an alle Indizes aufgefächerte, und die zurückgegebenen Ergebnisse werden zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="d8f95-p102">Beispielsweise kann ein Benutzer in einem Geo Speicherort suchen für Inhalte, die in eine andere Geo Position oder nach Inhalten zu einer SharePoint-Website, die an einen anderen Geo Speicherort eingeschränkt ist. Wenn der Benutzer Zugriff auf diese Inhalte verfügt, wird die Suche das Ergebnis angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="d8f95-109">Die Clients arbeiten in einer Umgebung mit mehreren geografisch suchen?</span><span class="sxs-lookup"><span data-stu-id="d8f95-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="d8f95-110">Diese Clients können aus allen Speicherorten von Geo Ergebnisse zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="d8f95-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="d8f95-111">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="d8f95-111">OneDrive for Business</span></span>

-   <span data-ttu-id="d8f95-112">Delve</span><span class="sxs-lookup"><span data-stu-id="d8f95-112">Delve</span></span>

-   <span data-ttu-id="d8f95-113">SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="d8f95-113">The SharePoint home page</span></span>

-   <span data-ttu-id="d8f95-114">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="d8f95-114">The Search Center</span></span>

-   <span data-ttu-id="d8f95-115">Benutzerdefinierte suchanwendungen, die die SharePoint-Suche-API verwenden</span><span class="sxs-lookup"><span data-stu-id="d8f95-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="d8f95-116">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="d8f95-116">OneDrive for Business</span></span>

<span data-ttu-id="d8f95-117">Als Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die in OneDrive durchsuchen Ergebnisse aus allen geografisch Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="d8f95-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="d8f95-118">Delve</span><span class="sxs-lookup"><span data-stu-id="d8f95-118">Delve</span></span>

<span data-ttu-id="d8f95-119">Als Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die in Delve durchsuchen Ergebnisse aus allen geografisch Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="d8f95-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="d8f95-p103">Die Delve-Feeds und die Profilkarte zeigen nur eine Vorschau der Dateien, die in der **zentralen** Speicherort gespeichert sind. Für Dateien, die in Satelliten Geo Speicherorten gespeichert sind, wird stattdessen das Symbol für den Dateityp angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="d8f95-122">SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="d8f95-122">The SharePoint home page</span></span>

<span data-ttu-id="d8f95-p104">Als Multi-Geo-Umgebung eingerichtet wurde, wird den Benutzern letzte und besuchter Websites aus mehreren geografisch Speicherorten auf ihre SharePoint-Homepage News, angezeigt. Wenn sie das Suchfeld auf der Homepage der SharePoint verwenden, erhalten sie zusammengeführte Ergebnisse aus mehreren geografisch Standorten.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="d8f95-125">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="d8f95-125">The Search Center</span></span>

<span data-ttu-id="d8f95-p105">Nach der Multi-Geo hat Umgebung eingerichtet wurde jedem Suchcenter weiterhin über einen eigenen Geo Ort nur Ergebnisse anzeigen. Administratoren müssen zum Abrufen der Ergebnisse aus allen geografisch Speicherorten [ändern, die von jedem Suchcenter](#_Set_up_a_1) . Anschließend erhalten Benutzer, die für die Suche im Suchcenter Ergebnisse aus allen geografisch Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="d8f95-129">Benutzerdefinierte suchanwendungen</span><span class="sxs-lookup"><span data-stu-id="d8f95-129">Custom search applications</span></span>

<span data-ttu-id="d8f95-p106">Interagieren benutzerdefinierte suchanwendungen wie gewohnt mit der Suchindizes mithilfe der vorhandenen SharePoint Search-REST-APIs. Um die Ergebnisse aller oder einiger Geo-Speicherorte zu erhalten, muss die Anwendung [Aufrufen der API und umfassen die neuen Abfrageparameter Multi-Geo](#_Get_custom_search) in der Anforderung. Dadurch wird einen Lüfter der Abfrage an allen Speicherorten von Geo ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="d8f95-133">Was ist anders bei der Suche in einer Umgebung mit mehreren geografisch?</span><span class="sxs-lookup"><span data-stu-id="d8f95-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="d8f95-134">Einige Suchfeatures, mit denen Sie möglicherweise vertraut sind, funktionieren in einer Umgebung mit mehreren geografisch.</span><span class="sxs-lookup"><span data-stu-id="d8f95-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8f95-135"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="d8f95-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="d8f95-136"><strong>Wie funktioniert</strong></span><span class="sxs-lookup"><span data-stu-id="d8f95-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="d8f95-137"><strong>Dieses Problem zu umgehen</strong></span><span class="sxs-lookup"><span data-stu-id="d8f95-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-138">Höhergestufte Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d8f95-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="d8f95-p107">Erstellen von Abfrageregeln können mit heraufgestufte Ergebnisse auf verschiedenen Ebenen: für den gesamten Mandanten, für eine Websitesammlung oder für eine Website. Definieren Sie in einer Umgebung mit mehreren geografisch heraufgestufte Ergebnisse auf der Ebene der <strong>Mandanten</strong> , wenn Sie die Ergebnisse an die Suchcentern an <strong>allen</strong> Speicherorten von Geo Höherstufen möchten. Wenn Sie <strong>nur</strong> Ergebnisse im Suchcenter Höherstufen möchten, die am Geo der Websitesammlung oder Website befindet, definieren Sie die Ergebnisse Ebene der <strong>Websitesammlung</strong> oder <strong>Website</strong> an.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="d8f95-142">Wenn Sie verschiedene heraufgestufte Ergebnisse pro Geo-Speicherort, beispielsweise unterschiedliche Regeln für Reisen, nicht empfehlen wir definieren auf der Ebene der Mandant Ergebnisse heraufgestuft.</span><span class="sxs-lookup"><span data-stu-id="d8f95-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8f95-143">Sucheinschränkungen</span><span class="sxs-lookup"><span data-stu-id="d8f95-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="d8f95-p108">Suche Einschränkungen aus alle Geo Speicherorte eines Mandanten liegen zurückgegeben, und klicken Sie dann aggregiert werden. Die Aggregation ist bemüht, d. h., die von einschränkungsanzahlen möglicherweise nicht 100 % genau. In den meisten Fällen suchbasierte reicht diese Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="d8f95-147">Suchgesteuerte Anwendungen, die Einschränkung Vollständigkeit abhängen, Fragen Sie jeden Standort Geo unabhängig voneinander ohne Verwendung von Multi-Geo Auffächerung ab.</span><span class="sxs-lookup"><span data-stu-id="d8f95-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="d8f95-148">Multi-Geo Suche unterstützt keine dynamischen das Zuordnen von Buckets für numerische Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="d8f95-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="d8f95-149">Verwenden Sie den <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">Parameter "Discretize"</a> für numerische Einschränkungen an.</span><span class="sxs-lookup"><span data-stu-id="d8f95-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8f95-150">Dokument-IDs</span><span class="sxs-lookup"><span data-stu-id="d8f95-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="d8f95-151">Bei der Entwicklung einer suchbasierte-Anwendung, die von Dokument-IDs abhängt, beachten Sie, dass die Dokument-IDs in einer Umgebung mit mehreren geografisch sind nicht über Geo Standorte eindeutige, sie sind pro Standort Geo eindeutig.</span><span class="sxs-lookup"><span data-stu-id="d8f95-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="d8f95-p109">Wir haben eine Spalte hinzugefügt, die den Speicherort Geo angibt. Verwenden Sie diese Spalte, um Eindeutigkeit zu erreichen. Diese Spalte wird mit der Bezeichnung "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="d8f95-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-155">Anzahl der Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d8f95-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="d8f95-156">Seite mit den Suchergebnissen zeigt kombinierten Ergebnisse aus den Speicherorten Geo, aber es ist nicht möglich, mehr als 500 Ergebnisse Seite.</span><span class="sxs-lookup"><span data-stu-id="d8f95-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="d8f95-157">Was ist nicht für die Suche in einer Umgebung mit mehreren geografisch unterstützt?</span><span class="sxs-lookup"><span data-stu-id="d8f95-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="d8f95-158">Einige der Features für die Suche, die Sie möglicherweise vertraut sind, werden in einer Umgebung mit mehreren geografisch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8f95-159"><strong>Feature für die Suche</strong></span><span class="sxs-lookup"><span data-stu-id="d8f95-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="d8f95-160"><strong>Hinweis</strong></span><span class="sxs-lookup"><span data-stu-id="d8f95-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-161">Nur-App-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="d8f95-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="d8f95-162">Nur-App-Authentifizierung (Systemzugriff von Services) wird bei der Suche mit mehreren geografisch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8f95-163">Gast-Benutzer</span><span class="sxs-lookup"><span data-stu-id="d8f95-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="d8f95-164">Gast-Benutzer erhalten nur Ergebnisse aus dem Geo-Speicherort, dem sie durchsuchen aus.</span><span class="sxs-lookup"><span data-stu-id="d8f95-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="d8f95-165">Wie funktioniert Suche in einer Umgebung mit mehreren geografisch funktionieren?</span><span class="sxs-lookup"><span data-stu-id="d8f95-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="d8f95-166">**Alle** verwenden die Suche Clients der vorhandenen SharePoint Search-REST-APIs zur Interaktion mit der Suchindizes an.</span><span class="sxs-lookup"><span data-stu-id="d8f95-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="d8f95-167">Ein Search-Client Ruft den Search-REST-Endpunkt mit der Abfrageeigenschaft EnableMultiGeoSearch = True.</span><span class="sxs-lookup"><span data-stu-id="d8f95-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="d8f95-168">Die Abfrage wird an alle Geo Speicherorte im Mandanten gesendet.</span><span class="sxs-lookup"><span data-stu-id="d8f95-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="d8f95-169">Suchergebnisse aus jedem Standort Geo zusammengeführt und Rangfolge.</span><span class="sxs-lookup"><span data-stu-id="d8f95-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="d8f95-170">Der Client ruft unified Suchergebnisse ab.</span><span class="sxs-lookup"><span data-stu-id="d8f95-170">The client gets unified search results.</span></span>



<span data-ttu-id="d8f95-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Beachten Sie, dass wir nicht die Suchergebnisse zusammengefügt werden, bis es Ergebnisse aus allen Speicherorten die Geo erhalten haben. Dies bedeutet, dass Multi-Geo Suchvorgänge zusätzlichen Latenz im Vergleich zu Suchvorgänge in einer Umgebung mit nur eine Geo Speicherort.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="d8f95-173">Abrufen eines Suchcenters anzuzeigenden Ergebnisse aus allen geografisch Speicherorten</span><span class="sxs-lookup"><span data-stu-id="d8f95-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="d8f95-174">Jedem Suchcenter hat mehrere vertikale Märkte und müssen Sie jeden vertikal einzeln einrichten.</span><span class="sxs-lookup"><span data-stu-id="d8f95-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="d8f95-175">Stellen Sie sicher, dass das Ausführen dieser Schritte mit einem Konto die Berechtigung zum Bearbeiten der Suchergebnisseite und das Ergebnis-Webpart hat.</span><span class="sxs-lookup"><span data-stu-id="d8f95-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="d8f95-176">Navigieren Sie zur Seite mit Suchergebnissen (siehe die [Liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) der Suche Suchergebnisseiten)</span><span class="sxs-lookup"><span data-stu-id="d8f95-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="d8f95-p111">Wählen Sie die vertikal einrichten, klicken Sie auf die obere rechte Ecke Zahnradsymbol **Einstellungen** , und klicken Sie dann auf **Seite bearbeiten**. Seite mit den Suchergebnissen wird im Bearbeitungsmodus geöffnet.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="d8f95-p112">In den Suchergebnisse-Webpart bewegen Sie den Zeiger auf der oberen rechten Ecke des Webparts, klicken Sie auf den Pfeil, und klicken Sie dann im Menü auf **Webpart bearbeiten** . Der Suchergebnisse-Webpart-Toolbereich wird geöffnet, unter dem Menüband in der oberen rechten Seitenrand.![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="d8f95-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="d8f95-181">Wählen Sie im Toolbereich des Webparts im Abschnitt **Einstellungen** unter **Ergebnisse Einstellungen steuern**, **Ergebnisse anzeigen Multi-Geo** zum Abrufen der Suchergebnisse-Webpart zum Anzeigen der Ergebnisse aus allen geografisch Speicherorten aus.</span><span class="sxs-lookup"><span data-stu-id="d8f95-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="d8f95-182">Klicken Sie auf **OK** , um die Änderung zu speichern und schließen Sie den Webpart-Toolbereich.</span><span class="sxs-lookup"><span data-stu-id="d8f95-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="d8f95-183">Überprüfen Sie Ihre Änderungen an der Suchergebnisse-Webpart, indem Sie auf der Registerkarte Seite im Hauptmenü **Einchecken** .</span><span class="sxs-lookup"><span data-stu-id="d8f95-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="d8f95-184">Veröffentlichen Sie die Änderungen über den Link in der Notiz am oberen Rand der Seite bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d8f95-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="d8f95-185">Abrufen von benutzerdefinierten suchanwendungen zum Anzeigen von Suchergebnissen aus aller oder einiger Geo Speicherorten</span><span class="sxs-lookup"><span data-stu-id="d8f95-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="d8f95-p113">Benutzerdefinierte suchanwendungen erhalten Ergebnisse von Speicherorten für alle oder einige, geografisch durch Angeben von Abfrageparametern mit der Anforderung an SharePoint Search-REST-API. Je nach dem Parameter für die Abfrage ist die Abfrage an alle Geo Speicherorte oder an einigen Standorten Geo aufgefächerte. Wenn Sie nur eine Teilmenge der Geo Speicherorte relevanten Informationen erhalten Abfragen müssen, können Sie beispielsweise den Lüfter nur diese steuern. Wenn die Anforderung erfolgreich ist, gibt der REST-API für SharePoint Search Antwortdaten zurück.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="d8f95-190">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="d8f95-190">Query parameters</span></span>

<span data-ttu-id="d8f95-p114">EnableMultiGeoSearch - ist dies ein boolescher Wert, der angibt, ob die Abfrage auf die Indizes von anderen Speicherorten Geo des Mandanten Multi-Geo aufgefächerte werden muss. Legen Sie es auf **"true"** , die Abfrage Lüfter; **false** , wenn nicht, die Abfrage Lüfter. Der Standardwert ist **false**. Wenn Sie diesen Parameter keinen angeben, wird die Abfrage **nicht** an andere Speicherorte Geo aufgefächerte. Wenn Sie den Parameter in einer Umgebung, die mit mehreren geografisch nicht verwenden, wird der Parameter ignoriert.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="d8f95-p115">Clienttyp - Dies ist eine Zeichenfolge. Geben Sie einen eindeutigen Client-Namen für jede Suchanwendung. Wenn Sie diesen Parameter keinen angeben, wird die Abfrage **nicht** an andere Speicherorte Geo aufgefächerte.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="d8f95-p116">MultiGeoSearchConfiguration - ist dies eine optionale Liste von welche, die Geo Speicherorten in der Multi-Geo Mandanten um die Erweiterung der Abfrage an, wenn **EnableMultiGeoSearch** **true**ist. Wenn Sie nicht fügen Sie diesen Parameter oder leer lassen, wird die Abfrage an allen Speicherorten von Geo aufgefächerte. Geben Sie für jeden Standort Geo die folgenden Elemente im JSON-Format ein:</span><span class="sxs-lookup"><span data-stu-id="d8f95-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8f95-202">Element</span><span class="sxs-lookup"><span data-stu-id="d8f95-202">Item</span></span></th>
<th align="left"><span data-ttu-id="d8f95-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d8f95-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="d8f95-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="d8f95-205">Geo-Speicherort, beispielsweise Name.</span><span class="sxs-lookup"><span data-stu-id="d8f95-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8f95-206">Endpunkt</span><span class="sxs-lookup"><span data-stu-id="d8f95-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="d8f95-207">Der Endpunkt für die Verbindung, beispielsweisehttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="d8f95-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="d8f95-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="d8f95-209">Die GUID der ergebnisquelle, beispielsweise B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="d8f95-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d8f95-p117">Wenn Sie DataLocation oder Endpunkt weglassen oder wenn ein DataLocation doppelt vorhanden ist, schlägt die Anforderung fehl. [Sie erhalten Informationen zu den Endpunkt des einen Mandanten Geo Speicherorte mithilfe von Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="d8f95-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="d8f95-212">Antwortdaten</span><span class="sxs-lookup"><span data-stu-id="d8f95-212">Response data</span></span>

<span data-ttu-id="d8f95-p118">MultiGeoSearchStatus – ist dies eine Eigenschaft, die SharePoint-Suche API als Antwort auf eine Anforderung zurückgibt. Der Wert der Eigenschaft ist eine Zeichenfolge und gibt die folgende Informationen über die Ergebnisse, die die SharePoint-Suche-API zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="d8f95-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8f95-215">Wert</span><span class="sxs-lookup"><span data-stu-id="d8f95-215">Value</span></span></th>
<th align="left"><span data-ttu-id="d8f95-216">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d8f95-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-217">Vollständig</span><span class="sxs-lookup"><span data-stu-id="d8f95-217">Full</span></span></td>
<td align="left"><span data-ttu-id="d8f95-218">Vollständige Ergebnisse aus <strong>allen</strong> die Geo-Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="d8f95-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d8f95-219">Teilweise</span><span class="sxs-lookup"><span data-stu-id="d8f95-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="d8f95-p119">Partielle Ergebnisse aus einem oder mehreren geografisch Standorten. Die Ergebnisse sind unvollständig aufgrund eines vorübergehenden Fehlers.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="d8f95-222">Ausführen von Abfragen mithilfe des REST-Diensts</span><span class="sxs-lookup"><span data-stu-id="d8f95-222">Query using the REST service</span></span>

<span data-ttu-id="d8f95-p120">Mit GET-Anforderung Geben Sie Parameter für die Abfrage in der URL. Mit einer POST-Anforderung übergeben Sie Parameter für die Abfrage in den Hauptteil in JavaScript Object Notation (JSON)-Format.</span><span class="sxs-lookup"><span data-stu-id="d8f95-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="d8f95-225">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="d8f95-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d8f95-226">Name</span><span class="sxs-lookup"><span data-stu-id="d8f95-226">Name</span></span></th>
<th align="left"><span data-ttu-id="d8f95-227">Wert</span><span class="sxs-lookup"><span data-stu-id="d8f95-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d8f95-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="d8f95-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="d8f95-229">Application/Json; Odata = verbose</span><span class="sxs-lookup"><span data-stu-id="d8f95-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="d8f95-230">Beispiel: eine GET-Anforderung für **Alle** Geo Speicherorte aufgefächerte</span><span class="sxs-lookup"><span data-stu-id="d8f95-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="d8f95-231">https:// \<Mandanten\>/\_api/Search/Query?querytext = "Sharepoint" & Eigenschaften = 'EnableMultiGeoSearch:true' & Clienttyp =' Meine\_Client\_Id'</span><span class="sxs-lookup"><span data-stu-id="d8f95-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="d8f95-232">Beispiel GET-Anforderung an die Erweiterung auf **einige** Geo-Speicherorte</span><span class="sxs-lookup"><span data-stu-id="d8f95-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="d8f95-233">https:// <tenant>/_api/search/query?querytext = 'Site' & Clienttyp = 'My_client_id' & Eigenschaften ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{DataLocation\:"Name"\,Endpunkt\:"Https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"Können"\,Endpunkt\:" Https\://contosoCAN.sharepoint-df.com "}]"</span><span class="sxs-lookup"><span data-stu-id="d8f95-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="d8f95-234">Beispiel-POST-Anforderung, die **Alle** Geo Speicherorte aufgefächerte</span><span class="sxs-lookup"><span data-stu-id="d8f95-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="d8f95-235">Beispiel: eine POST-Anforderung für **einige** Geo Speicherorte aufgefächerte</span><span class="sxs-lookup"><span data-stu-id="d8f95-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="d8f95-236">Abfrage mit CSOM</span><span class="sxs-lookup"><span data-stu-id="d8f95-236">Query using CSOM</span></span>

<span data-ttu-id="d8f95-237">Hier ist eine CSOM-Beispielabfrage, die **Alle** Geo Speicherorte aufgefächerte:</span><span class="sxs-lookup"><span data-stu-id="d8f95-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

