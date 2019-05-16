---
title: Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: In diesem Artikel wird beschrieben, wie Sie die Leistung steigern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.
ms.openlocfilehash: 590cd5f60dedf870d58d053b01e4e1b45469bfa4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070551"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="1bbcf-103">Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1bbcf-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="1bbcf-104">In diesem Artikel wird beschrieben, wie Sie die Leistung steigern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="1bbcf-105">Eine der leistungsfähigsten neuen Features von SharePoint Server 2013 und SharePoint Online ist das Inhaltssuche-Webpart (Inhaltssuche).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="1bbcf-106">Dieses Webpart verwendet den Suchindex, um schnell Ergebnisse abzurufen, die dem Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="1bbcf-107">Verwenden Sie das Inhaltssuche-Webpart anstelle des Inhaltsabfrage-Webparts (CQWP) auf Ihren Seiten, um die Leistung für Ihre Benutzer zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="1bbcf-108">Die Verwendung eines Inhaltssuche-Webparts über ein Inhaltsabfrage-Webpart führt fast immer zu einer deutlich besseren Seiten Ladeleistung in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="1bbcf-109">Es gibt eine kleine zusätzliche Konfiguration, um die richtige Abfrage zu erhalten, aber die Vorteile sind verbesserte Leistung und zufriedenere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="1bbcf-110">Vergleich der Leistungssteigerung, die Sie mit dem Webpart "Inhaltssuche" erhalten, anstelle des Webparts für Inhaltsabfragen</span><span class="sxs-lookup"><span data-stu-id="1bbcf-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="1bbcf-111">Die folgenden Beispiele zeigen die relativen Leistungssteigerungen, die beim Verwenden eines Inhaltssuche-Webparts anstelle eines Inhaltsabfrage-Webparts auftreten können.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="1bbcf-112">Die Effekte sind bei einer komplexen Websitestruktur und sehr umfangreichen Inhaltsabfragen deutlicher.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="1bbcf-113">Diese Beispielwebsite weist die folgenden Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="1bbcf-114">8 Stufen der Unterwebsites.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="1bbcf-115">Listen, die einen benutzerdefinierten Inhaltstyp "Fruit" verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="1bbcf-116">Im Webpart ist die Inhaltsabfrage breit und gibt alle Elemente mit dem Inhaltstyp "Fruit" zurück.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="1bbcf-117">Das Beispiel verwendet nur 50-Elemente in den 8-Standorten.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="1bbcf-118">Die Effekte werden für Websites mit mehr Inhalt noch ausgeprägter.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="1bbcf-119">Im folgenden finden Sie einen Screenshot der Ergebnisse des Inhaltsabfrage-Webparts.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Grafik mit Inhaltsabfrage für WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="1bbcf-121">Verwenden Sie in Internet Explorer auf der Registerkarte **Netzwerk** der F12-Entwicklertools die Details für den Antwortheader.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="1bbcf-122">Im folgenden Screenshot beträgt der Wert für die **SPRequestDuration** für diese Seite 924 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Screenshot mit der Anforderungsdauer von 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="1bbcf-124">**SPRequestDuration** gibt an, wie viel Arbeit auf dem Server ausgeführt wird, um die Seite vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="1bbcf-125">Das Wechseln von Inhalten durch Abfrage Webparts mit Inhalten durch Such-Webparts reduziert die Zeit, die zum Rendern der Seite erforderlich ist, drastisch.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="1bbcf-126">Dagegen hat eine Seite mit einem äquivalenten Inhaltssuche-Webpart, der die gleiche Anzahl von Ergebnissen zurückgibt, einen **SPRequestDuration** -Wert von 106 Millisekunden, wie in diesem Screenshot gezeigt:</span><span class="sxs-lookup"><span data-stu-id="1bbcf-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Screenshot mit der Anforderungsdauer von 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="1bbcf-128">Hinzufügen eines Inhaltssuche-Webparts in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1bbcf-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="1bbcf-129">Das Hinzufügen eines Inhaltssuche-Webparts ähnelt einem Webpart für reguläre Inhaltsabfragen.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="1bbcf-130">Weitere Informationen finden Sie im Abschnitt *"Hinzufügen eines Inhaltssuche-Webparts"* unter [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="1bbcf-131">Erstellen der richtigen Suchabfrage für Ihr Inhaltssuche-Webpart</span><span class="sxs-lookup"><span data-stu-id="1bbcf-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="1bbcf-132">Nachdem Sie ein Inhaltssuche-Webpart hinzugefügt haben, können Sie die Suche verfeinern und die gewünschten Elemente zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="1bbcf-133">Ausführliche Anweisungen dazu finden Sie im Abschnitt *"Anzeigen von Inhalten durch Konfigurieren einer erweiterten Abfrage in einem Inhaltssuche-Webpart"* unter [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="1bbcf-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="1bbcf-134">Tool zum Erstellen und Testen von Abfragen</span><span class="sxs-lookup"><span data-stu-id="1bbcf-134">Query building and testing tool</span></span>

<span data-ttu-id="1bbcf-135">Ein Tool zum Erstellen und Testen komplexer Abfragen finden Sie im [Suchabfrage Tool](https://sp2013searchtool.codeplex.com/) unter CodePlex.</span><span class="sxs-lookup"><span data-stu-id="1bbcf-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

