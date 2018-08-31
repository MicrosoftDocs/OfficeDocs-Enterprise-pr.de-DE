---
title: Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: In diesem Artikel wird beschrieben, wie auf die Leistung zu erhöhen, indem Sie das Webpart für Inhaltsabfragen durch das Inhaltssuche-Webpart in SharePoint Server 2013 und SharePoint Online ersetzen.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541039"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="7ff37-103">Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7ff37-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="7ff37-104">In diesem Artikel wird beschrieben, wie auf die Leistung zu erhöhen, indem Sie das Webpart für Inhaltsabfragen durch das Inhaltssuche-Webpart in SharePoint Server 2013 und SharePoint Online ersetzen.</span><span class="sxs-lookup"><span data-stu-id="7ff37-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="7ff37-p101">Eine effizienteste neue Features von SharePoint Server 2013 und SharePoint Online ist das Content Search Web Part (CSWP). Dieses Webpart verwendet den Suchindex schnell Ergebnisse abgerufen, die dem Benutzer angezeigt werden. Verwenden Sie das Inhaltssuche-Webpart anstelle der Content Abfrage Web Part (CQWP) auf den Seiten zum Verbessern der Leistung für Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7ff37-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="7ff37-p102">Verwenden ein Inhaltssuche-Webpart über ein Webpart für Inhaltsabfragen wird deutlich besser seitenladeleistung SharePoint Online fast immer führen. Es ist eine wenig zusätzliche Konfiguration die richtige Abfrage abgerufen, aber die verbesserte Leistung und happier Benutzer sind.</span><span class="sxs-lookup"><span data-stu-id="7ff37-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="7ff37-110">Der Leistungsgewinn vergleichen, die aus der Inhaltssuche-Webpart verwenden, anstatt Webpart für Inhaltsabfragen</span><span class="sxs-lookup"><span data-stu-id="7ff37-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="7ff37-p103">Die folgenden Beispiele zeigen die relative Leistungsgewinnen, die möglicherweise angezeigt wird, wenn Sie ein Inhaltssuche-Webpart anstelle von einem Webpart für Inhaltsabfragen verwenden. Die Effekte sind deutlicher mit einer komplexen Websitestruktur und sehr große Content-Abfragen.</span><span class="sxs-lookup"><span data-stu-id="7ff37-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="7ff37-113">In diesem Beispiel Website weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="7ff37-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="7ff37-114">8 Ebenen von Unterwebsites.</span><span class="sxs-lookup"><span data-stu-id="7ff37-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="7ff37-115">Enthält einen benutzerdefinierten "Obst" Inhaltstyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="7ff37-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="7ff37-116">Im Webpart ist das Inhaltsabfrage umfassende, alle Elemente mit dem Inhaltstyp "Frucht" zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="7ff37-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="7ff37-p104">Im Beispiel wird nur 50 Elemente 8 Standorten verwendet. Die Effekte werden auch für Websites mit Weitere Inhalte zu deutlicher.</span><span class="sxs-lookup"><span data-stu-id="7ff37-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="7ff37-119">Es folgt ein Screenshot der Ergebnisse der das Webpart für Inhaltsabfragen.</span><span class="sxs-lookup"><span data-stu-id="7ff37-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Grafische Darstellung der Inhaltsabfrage-Webparts](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="7ff37-p105">Verwenden Sie in Internet Explorer die Registerkarte **Netzwerk** der F12-Entwicklertools betrachten Sie die Details für den Antwortheader. Im folgenden Screenshot ist der Wert für die **SPRequestDuration** für diese Seite Last 924 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="7ff37-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Screenshot mit Anforderungsdauer von 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="7ff37-p106">**SPRequestDuration** gibt den Zeitraum der Arbeit, ausgeführt wird, auf dem Server auf die Seite vorbereiten. Ändern des Inhalts von Webparts für Inhaltsabfragen mit Inhalt von Suchwebparts erheblich verringert den Zeitaufwand zum Rendern der Seite. Im Gegensatz dazu hat eine Seite mit einer gleichwertigen Inhaltssuche-Webpart, die gleiche Anzahl von Ergebnissen zurückgeben **SPRequestDuration** Wert 106 Millisekunden wie in diesem Screenshot dargestellt:</span><span class="sxs-lookup"><span data-stu-id="7ff37-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Screenshot mit Anforderungsdauer von 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="7ff37-128">Hinzufügen eines Inhaltssuche-Webparts in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7ff37-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="7ff37-p107">Hinzufügen einer Inhaltssuche-Webpart ist sehr ähnlich einer regulären Webpart für Inhaltsabfragen. Finden Sie im Abschnitt *"Hinzufügen eines Inhaltssuche-Webpart"* unter [Configure ein Inhaltssuche-Webpart in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="7ff37-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="7ff37-131">Erstellen die richtigen Suchabfrage für die Inhaltssuche-Webpart</span><span class="sxs-lookup"><span data-stu-id="7ff37-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="7ff37-p108">Nachdem Sie ein Inhaltssuche-Webpart hinzugefügt haben, können Sie verfeinern die Suche und die gewünschten Elemente zurückgeben. Ausführliche Informationen hierzu finden Sie im Abschnitt, *"Content durch Konfigurieren einer erweiterten Abfrage in ein Inhaltssuche-Webpart anzeigen"* unter [Konfigurieren eines Inhalts-Webparts in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="7ff37-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="7ff37-134">Entwickeln und Testen von Tool Abfragen</span><span class="sxs-lookup"><span data-stu-id="7ff37-134">Query building and testing tool</span></span>

<span data-ttu-id="7ff37-135">Ein Tool zum Erstellen und Testen komplexe Abfragen finden Sie unter dem [Search-Abfrage-Tool](https://sp2013searchtool.codeplex.com/) bei Codeplex.</span><span class="sxs-lookup"><span data-stu-id="7ff37-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

