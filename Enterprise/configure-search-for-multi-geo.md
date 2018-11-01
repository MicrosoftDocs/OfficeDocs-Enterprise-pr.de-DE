---
title: Konfigurieren der Suche für Multi-Geo in OneDrive for Business
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Dieser Artikel enthält Informationen zum Konfigurieren der Suche in einer Multi-Geo-Umgebung.
ms.openlocfilehash: 5ca2a35385ab2c246b78dc8811e8435bbdec25c7
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849911"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="a5740-103">Konfigurieren der Suche für Multi-Geo in OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="a5740-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="a5740-104">In einer OneDrive for Business-Umgebung mit Multi-Geo kann eine Organisation über einen Office 365-Mandanten verfügen, ihre OneDrive for Business-Inhalte jedoch an mehreren geografischen Standorten speichern – einem zentralen Standort und einem oder mehreren Satellitenstandorten.</span><span class="sxs-lookup"><span data-stu-id="a5740-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="a5740-p101">Jeder geografische Standort verfügt über einen eigenen Suchindex und ein Suchcenter. Wenn ein Benutzer eine Suche durchführt, wird die Abfrage in alle Indizes aufgefächert, und die zurückgegebenen Ergebnisse werden zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="a5740-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="a5740-p102">Ein Benutzer an einem geografischen Standort kann zum Beispiel nach Inhalten an einem anderen Standort oder auf einer SharePoint-Website suchen, die auf einen anderen geografischen Standort eingeschränkt ist. Wenn der Benutzer Zugriff auf diese Inhalte hat, wird das Suchergebnis angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5740-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="a5740-109">Welche Suchclients können in einer Multi-Geo-Umgebung verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="a5740-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="a5740-110">Diese Clients können von allen geografischen Standorten Ergebnisse zurückgeben:</span><span class="sxs-lookup"><span data-stu-id="a5740-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="a5740-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="a5740-111">OneDrive for Business</span></span>

-   <span data-ttu-id="a5740-112">Delve</span><span class="sxs-lookup"><span data-stu-id="a5740-112">Delve</span></span>

-   <span data-ttu-id="a5740-113">Die SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="a5740-113">The SharePoint home page</span></span>

-   <span data-ttu-id="a5740-114">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="a5740-114">The Search Center</span></span>

-   <span data-ttu-id="a5740-115">Benutzerdefinierte Suchanwendungen, die die SharePoint-Suche-API verwenden</span><span class="sxs-lookup"><span data-stu-id="a5740-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="a5740-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="a5740-116">OneDrive for Business</span></span>

<span data-ttu-id="a5740-117">Sobald die Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die eine Suche in OneDrive durchführen, Ergebnisse aus allen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="a5740-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="a5740-118">Delve</span><span class="sxs-lookup"><span data-stu-id="a5740-118">Delve</span></span>

<span data-ttu-id="a5740-119">Sobald die Multi-Geo-Umgebung eingerichtet wurde, erhalten Benutzer, die eine Suche in Delve durchführen, Ergebnisse aus allen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="a5740-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="a5740-p103">Der Delve-Feed und die Profilkarte zeigen nur eine Vorschau der Dateien an, die sich an dem **zentralen** Standort befinden. Für Dateien, die sich an Satellitenstandorten befinden, wird stattdessen das Symbol für den Dateityp angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5740-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="a5740-122">Die SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="a5740-122">The SharePoint home page</span></span>

<span data-ttu-id="a5740-p104">Sobald die Multi-Geo-Umgebung eingerichtet wurde, werden Benutzern Neuigkeiten, zuletzt verwendete und gefolgte Websites von mehreren geografischen Standorten auf ihrer SharePoint-Homepage angezeigt. Wenn sie das Suchfeld auf der SharePoint-Homepage verwenden, werden die Ergebnisse aus mehreren geografischen Standorten zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="a5740-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="a5740-125">Das Suchcenter</span><span class="sxs-lookup"><span data-stu-id="a5740-125">The Search Center</span></span>

<span data-ttu-id="a5740-p105">Sobald die Multi-Geo-Umgebung eingerichtet wurde, zeigt jedes Suchcenter weiterhin nur die Ergebnisse vom eigenen geografischen Standort an. Administratoren müssen [die Einstellungen für jedes Suchcenter ändern](#_Set_up_a_1), um Ergebnisse aus allen geografischen Standorten zu erhalten. Anschließend erhalten Benutzer, die eine Suche im Suchcenter durchführen, Ergebnisse aus allen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="a5740-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="a5740-129">Benutzerdefinierte Suchanwendungen</span><span class="sxs-lookup"><span data-stu-id="a5740-129">Custom search applications</span></span>

<span data-ttu-id="a5740-p106">Wie üblich interagieren benutzerdefinierte Suchanwendungen mit den Suchindizes, indem die vorhandenen SharePoint-Suche-REST-APIs verwendet werden. Um Ergebnisse aus allen oder einigen geografischen Standorten zu erhalten, muss die Anwendung [die API aufrufen und die neuen Multi-Geo-Abfrageparameter](#_Get_custom_search) zu der Anforderung hinzufügen. Dadurch wird die Abfrage in alle geografischen Standorte aufgefächert.</span><span class="sxs-lookup"><span data-stu-id="a5740-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="a5740-133">Welche Unterschiede gibt es bei der Suche in einer Multi-Geo-Umgebung?</span><span class="sxs-lookup"><span data-stu-id="a5740-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="a5740-134">Einige Suchfunktionen, die Sie möglicherweise bereits kennen, funktionieren in einer Multi-Geo-Umgebung anders.</span><span class="sxs-lookup"><span data-stu-id="a5740-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a5740-135"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="a5740-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a5740-136"><strong>Funktionsweise</strong></span><span class="sxs-lookup"><span data-stu-id="a5740-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="a5740-137"><strong>Problemumgehung</strong></span><span class="sxs-lookup"><span data-stu-id="a5740-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-138">Höhergestufte Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="a5740-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="a5740-p107">Sie können Abfrageregeln mit höhergestuften Ergebnissen auf verschiedenen Ebenen erstellen: für den gesamten Mandanten, für eine Websitesammlung oder für eine Website. Definieren Sie in einer Multi-Geo-Umgebung höhergestufte Ergebnisse auf der <strong>Mandantenebene</strong>, wenn die Ergebnisse in den Suchcentern an <strong>allen</strong> geografischen Standorten höhergestuft werden sollen. Wenn Sie <strong>nur</strong> Ergebnisse im Suchcenter, das sich an einem geografischen Standort der Websitesammlung oder Website befindet, höherstufen möchten, definieren Sie die Ergebnisse auf der <strong>Websitesammlungs</strong>- oder <strong>Website</strong>ebene.</span><span class="sxs-lookup"><span data-stu-id="a5740-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="a5740-142">Wenn Sie keine anderen höhergestuften Ergebnisse pro geografischem Standort benötigen, zum Beispiel verschiedene Regeln für Reisen, wird empfohlen, höhergestufte Ergebnisse auf Mandantenebene zu definieren.</span><span class="sxs-lookup"><span data-stu-id="a5740-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a5740-143">Sucheinschränkungen</span><span class="sxs-lookup"><span data-stu-id="a5740-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="a5740-p108">Die Suche gibt Einschränkungen aus allen geografischen Standorten eines Mandanten zurück und aggregiert diese dann. Die Aggregation ist die beste Bemühung und bedeutet, dass die Anzahl der Einschränkungen nicht exakt 100%ig ist. Für die meisten suchgesteuerten Szenarien ist diese Genauigkeit ausreichend. </span><span class="sxs-lookup"><span data-stu-id="a5740-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="a5740-147">Führen Sie für suchgesteuerte Anwendungen, die von der Vollständigkeit der Einschränkungen abhängig sind, eine Abfrage für jeden geografischen Standort getrennt voneinander durch, ohne die Multi-Geo-Auffächerung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a5740-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="a5740-148">Das dynamische Zuordnen von Buckets für numerische Einschränkungen wird von der Multi-Geo-Suche nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a5740-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="a5740-149">Verwenden Sie den <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">„Discretize“-Parameter</a> für numerische Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="a5740-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a5740-150">Dokument-IDs</span><span class="sxs-lookup"><span data-stu-id="a5740-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="a5740-151">Wenn Sie eine suchgesteuerte Anwendung entwickeln, die von Dokument-IDs abhängig ist, müssen Sie beachten, dass die Dokument-IDs in einer Multi-Geo-Umgebung nicht standortübergreifend eindeutig sind, sie sind jeweils pro Standort eindeutig.</span><span class="sxs-lookup"><span data-stu-id="a5740-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="a5740-p109">Es wurde eine Spalte hinzugefügt, die den geografischen Standort identifiziert. Verwenden Sie diese Spalte, um Eindeutigkeit zu erreichen. Diese Spalte trägt den Namen „GeoLocationSource“.</span><span class="sxs-lookup"><span data-stu-id="a5740-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-155">Anzahl der Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="a5740-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="a5740-156">Auf der Seite mit den Suchergebnissen werden die kombinierten Ergebnisse von den geografischen Standorten angezeigt, die Seite darf jedoch 500 Ergebnisse nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="a5740-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="a5740-157">Was wird bei der Suche in einer Multi-Geo-Umgebung nicht unterstützt?</span><span class="sxs-lookup"><span data-stu-id="a5740-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="a5740-158">Einige Suchfunktionen, die Sie möglicherweise bereits kennen, werden in einer Multi-Geo-Umgebung nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a5740-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a5740-159"><strong>Suchfunktion</strong></span><span class="sxs-lookup"><span data-stu-id="a5740-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="a5740-160"><strong>Hinweis</strong></span><span class="sxs-lookup"><span data-stu-id="a5740-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-161">Nur-App-Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="a5740-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="a5740-162">Nur-App-Authentifizierung (privilegierter Zugriff von Diensten) wird bei der Multi-Geo-Suche nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a5740-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a5740-163">Gastbenutzer</span><span class="sxs-lookup"><span data-stu-id="a5740-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="a5740-164">Gastbenutzer erhalten nur Ergebnisse von dem geografischen Standort, aus dem Sie die Suche durchführen.</span><span class="sxs-lookup"><span data-stu-id="a5740-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="a5740-165">Wie funktioniert die Suche in einer Multi-Geo-Umgebung?</span><span class="sxs-lookup"><span data-stu-id="a5740-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="a5740-166">**Alle** Suchclients verwenden die vorhandenen SharePoint-Suche-REST-APIs für die Interaktion mit den Suchindizes.</span><span class="sxs-lookup"><span data-stu-id="a5740-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="a5740-167">Ein Suchclient ruft den REST-Endpunkt für die Suche mit der Abfrageeigenschaft „EnableMultiGeoSearch= true“ auf.</span><span class="sxs-lookup"><span data-stu-id="a5740-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="a5740-168">Die Abfrage wird an alle geografischen Standorte im Mandanten gesendet.</span><span class="sxs-lookup"><span data-stu-id="a5740-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="a5740-169">Die Suchergebnisse von jedem geografischen Standort werden zusammengeführt und bewertet.</span><span class="sxs-lookup"><span data-stu-id="a5740-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="a5740-170">Der Client erhält einheitliche Suchergebnisse.</span><span class="sxs-lookup"><span data-stu-id="a5740-170">The client gets unified search results.</span></span>



<span data-ttu-id="a5740-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Beachten Sie, dass die Suchergebnisse erst dann zusammengeführt werden, wenn die Ergebnisse von allen geografischen Standorten abgerufen wurden. Dies bedeutet, dass Multi-Geo-Suchen im Vergleich zu den Suchen in einer Umgebung mit nur einem geografischen Standort eine zusätzliche Wartezeit aufweisen.</span><span class="sxs-lookup"><span data-stu-id="a5740-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="a5740-173">Anzeigen der Ergebnisse von allen geografischen Standorten in einem Suchcenter</span><span class="sxs-lookup"><span data-stu-id="a5740-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="a5740-174">Jedes Suchcenter verfügt über mehrere Suchsparten, und Sie müssen jede Sparte einzeln einrichten.</span><span class="sxs-lookup"><span data-stu-id="a5740-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="a5740-175">Stellen Sie sicher, dass Sie diese Schritte mit einem Konto ausführen, das über die Berechtigung zum Bearbeiten der Suchergebnisseite und des Suchergebnisse-Webparts verfügt.</span><span class="sxs-lookup"><span data-stu-id="a5740-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="a5740-176">Navigieren Sie zur Seite mit den Suchergebnissen (siehe [Liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) der Suchergebnisseiten).</span><span class="sxs-lookup"><span data-stu-id="a5740-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="a5740-p111">Wählen Sie die Sparte, die Sie einrichten möchten, klicken Sie in der oberen rechten Ecke auf das Zahnradsymbol für **Einstellungen**, und klicken Sie auf **Seite bearbeiten**. Die Seite mit den Suchergebnissen wird im Bearbeitungsmodus geöffnet.</span><span class="sxs-lookup"><span data-stu-id="a5740-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="a5740-p112">Bewegen Sie im Suchergebnisse-Webpart den Mauszeiger in die obere rechte Ecke des Webparts, und klicken Sie dann im Menü auf **Webpart bearbeiten**. Der Toolbereich für das Suchergebnisse-Webpart wird unter dem Menüband oben rechts auf der Seite geöffnet. ![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="a5740-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="a5740-181">Wählen Sie im Webpart-Toolbereich im Abschnitt **Einstellungen** unter **Einstellungen für das Ergebnissteuerelement** die Option **Multi-Geo-Ergebnisse anzeigen**, damit das Suchergebnisse-Webpart Ergebnisse von allen geografischen Standorten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a5740-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="a5740-182">Klicken Sie auf **OK**, um Ihre Änderungen zu speichern und den Webpart-Toolbereich zu schließen.</span><span class="sxs-lookup"><span data-stu-id="a5740-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="a5740-183">Überprüfen Sie Ihre Änderungen an dem Suchergebnisse-Webpart, indem Sie im Hauptmenü auf der Registerkarte „Seite“ auf **Einchecken** klicken.</span><span class="sxs-lookup"><span data-stu-id="a5740-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="a5740-184">Veröffentlichen Sie die Änderungen über den Link in der Notiz oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="a5740-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="a5740-185">Anzeigen von Ergebnissen von allen oder einigen geografischen Standorten in benutzerdefinierten Suchanwendungen</span><span class="sxs-lookup"><span data-stu-id="a5740-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="a5740-p113">Benutzerdefinierte Anwendungen rufen Ergebnisse von allen oder einigen geografischen Standorten ab, indem Sie Abfrageparameter mit der Anforderung an die SharePoint-Suche-REST-API angeben. Je nach Abfrageparameter wird die Abfrage in alle geografischen Standorte oder in einige geografischen Standorte aufgefächert. Wenn nur einige geografischen Standorte abgefragt werden sollen, können Sie die Auffächerung nur für diese einschränken. Wenn die Anforderung erfolgreich ist, gibt die SharePoint-Suche-REST-API die Antwortdaten zurück.</span><span class="sxs-lookup"><span data-stu-id="a5740-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="a5740-190">Abfrageparameter</span><span class="sxs-lookup"><span data-stu-id="a5740-190">Query parameters</span></span>

<span data-ttu-id="a5740-p114">EnableMultiGeoSearch – Dies ist ein boolescher Wert, der angibt, ob die Abfrage in Indizes anderer geografischer Standorte des Multi-Geo-Mandanten aufgefächert werden soll. Legen Sie diesen Wert auf **true** fest, um die Abfrage aufzufächern, oder auf **false**, wenn die Abfrage nicht aufgefächert werden soll. Standardwert ist **false**. Wenn dieser Parameter nicht enthalten ist, wird die Abfrage **nicht** in andere geografischen Standorte aufgefächert. Wenn Sie den Parameter in einer Nicht-Multi-Geo-Umgebung verwenden, wird der Parameter ignoriert.</span><span class="sxs-lookup"><span data-stu-id="a5740-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="a5740-p115">ClientType – Dies ist eine Zeichenfolge. Geben Sie einen eindeutigen Clientnamen für jede Suchanwendung an. Wenn Sie diesen Parameter nicht hinzufügen, wird die Abfrage **nicht** in andere geografischen Standorte aufgefächert.</span><span class="sxs-lookup"><span data-stu-id="a5740-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="a5740-p116">MultiGeoSearchConfiguration – Dies ist eine optionale Liste mit geografischen Standorten im Multi-Geo-Mandanten, für die die Auffächerung der Abfrage erfolgen soll, wenn **EnableMultiGeoSearch** auf **true** festgelegt ist. Wenn Sie nicht diesen Parameter angeben oder leer lassen, wird die Abfrage für alle geografischen Standorte aufgefächert. Geben Sie für jeden geografischen Standort die folgenden Elemente im JSON-Format an:</span><span class="sxs-lookup"><span data-stu-id="a5740-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a5740-202">Element</span><span class="sxs-lookup"><span data-stu-id="a5740-202">Item</span></span></th>
<th align="left"><span data-ttu-id="a5740-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5740-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="a5740-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="a5740-205">Der geografische Standort, zum Beispiel NAM.</span><span class="sxs-lookup"><span data-stu-id="a5740-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a5740-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="a5740-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="a5740-207">Der Endpunkt für die Verbindung, zum Beispiel https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="a5740-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="a5740-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="a5740-209">Die GUID der Ergebnisquelle, zum Beispiel B81EAB55-3140-4312-B0F4-9459D1B4FFE.</span><span class="sxs-lookup"><span data-stu-id="a5740-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a5740-p117">Wenn Sie DataLocation oder Endpunkt weglassen, oder wenn DataLocation doppelt vorhanden ist, tritt bei der Anforderung ein Fehler auf. [Informationen zu dem Endpunkt von geografischen Standorten eines Mandanten können Sie mithilfe von Microsoft Graph](https://docs.microsoft.com/de-DE/sharepoint/dev/solution-guidance/multigeo-discovery) abrufen.</span><span class="sxs-lookup"><span data-stu-id="a5740-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/de-DE/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="a5740-212">Antwortdaten</span><span class="sxs-lookup"><span data-stu-id="a5740-212">Response data</span></span>

<span data-ttu-id="a5740-p118">MultiGeoSearchStatus – Dies ist eine Eigenschaft, die die SharePoint-Suche-API als Reaktion auf eine Anforderung zurückgibt. Der Wert der Eigenschaft ist eine Zeichenfolge und bietet die folgenden Informationen zu den Ergebnissen, die die SharePoint-Suche-API zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="a5740-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a5740-215">Wert</span><span class="sxs-lookup"><span data-stu-id="a5740-215">Value</span></span></th>
<th align="left"><span data-ttu-id="a5740-216">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5740-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-217">Vollständig</span><span class="sxs-lookup"><span data-stu-id="a5740-217">Full</span></span></td>
<td align="left"><span data-ttu-id="a5740-218">Vollständige Ergebnisse von <strong>allen</strong> geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="a5740-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a5740-219">Teilweise</span><span class="sxs-lookup"><span data-stu-id="a5740-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="a5740-p119">Teilweise Ergebnisse von einem oder mehreren geografischen Standorten. Die Ergebnisse sind aufgrund eines vorübergehenden Fehlers unvollständig.</span><span class="sxs-lookup"><span data-stu-id="a5740-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="a5740-222">Abfrage mithilfe des REST-Diensts</span><span class="sxs-lookup"><span data-stu-id="a5740-222">Query using the REST service</span></span>

<span data-ttu-id="a5740-p120">Mit einer GET-Anforderung geben Sie die Abfrageparameter in der URL an. Mit einer POST-Anforderung übergeben Sie die Abfrageparameter im Text im JSON-Format.</span><span class="sxs-lookup"><span data-stu-id="a5740-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="a5740-225">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a5740-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a5740-226">Name</span><span class="sxs-lookup"><span data-stu-id="a5740-226">Name</span></span></th>
<th align="left"><span data-ttu-id="a5740-227">Wert</span><span class="sxs-lookup"><span data-stu-id="a5740-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a5740-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="a5740-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="a5740-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="a5740-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a5740-230">Beispiel für eine GET-Anforderung, die für **alle** geografischen Standorte aufgefächert wird</span><span class="sxs-lookup"><span data-stu-id="a5740-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="a5740-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="a5740-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="a5740-232">Beispiel für eine GET-Anforderung, die für **einige** geografischen Standorte aufgefächert wird</span><span class="sxs-lookup"><span data-stu-id="a5740-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="a5740-233">https:// \<Mandant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="a5740-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="a5740-p121">Kommas und Doppelpunkten in der Liste der geografischen Standorte für die Eigenschaft MultiGeoSearchConfiguration wird ein **umgekehrtes Schrägstrichzeichen** vorangestellt. Dies hat den Grund, dass in GET-Anforderungen Doppelpunkte zum Trennen von Eigenschaften und Kommas zum Trennen von Argumenten von Eigenschaften verwendet werden. Ohne den umgekehrten Schrägstrich als Escapezeichen würde die MultiGeoSearchConfiguration-Eigenschaft falsch interpretiert.</span><span class="sxs-lookup"><span data-stu-id="a5740-p121">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="a5740-237">Beispiel für eine POST-Anforderung, die für **alle** geografischen Standorte aufgefächert wird</span><span class="sxs-lookup"><span data-stu-id="a5740-237">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="a5740-238">Beispiel für eine POST-Anforderung, die für **einige** geografischen Standorte aufgefächert wird</span><span class="sxs-lookup"><span data-stu-id="a5740-238">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="a5740-239">Abfrage mithilfe von CSOM</span><span class="sxs-lookup"><span data-stu-id="a5740-239">Query using CSOM</span></span>

<span data-ttu-id="a5740-240">Im Folgenden finden Sie ein Beispiel für eine CSOM-Abfrage, die für **alle** geografischen Standorte aufgefächert wird:</span><span class="sxs-lookup"><span data-stu-id="a5740-240">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

