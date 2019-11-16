---
title: Verwenden des Inhaltssuche-Webparts anstelle des Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: In diesem Artikel wird beschrieben, wie Sie die Leistung verbessern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.
ms.openlocfilehash: e2a3a1dd5a0010fcf1bbf61a039ca1d23292f70d
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "38077944"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="8f38e-103">Verwenden des Inhaltssuche-Webparts anstelle des Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8f38e-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="8f38e-104">In diesem Artikel wird beschrieben, wie Sie die Leistung verbessern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8f38e-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="8f38e-105">Eines der leistungsstärksten neuen Features von SharePoint Server 2013 und SharePoint Online ist das Inhaltssuche-Webpart (CSWP).</span><span class="sxs-lookup"><span data-stu-id="8f38e-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="8f38e-106">Dieses Webpart verwendet den Suchindex, um schnell Ergebnisse abzurufen, die dem Benutzer angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8f38e-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="8f38e-107">Verwenden Sie das Inhaltssuche-Webpart anstelle des Inhaltsabfrage-Webparts (CQWP) auf Ihren Seiten, um die Leistung für Ihre Benutzer zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="8f38e-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="8f38e-108">Die Verwendung eines Inhaltssuche-Webparts über ein Inhaltsabfrage-Webpart führt fast immer zu einer deutlich besseren Seiten Ladeleistung für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8f38e-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="8f38e-109">Es gibt eine kleine zusätzliche Konfiguration, um die richtige Abfrage zu erhalten, aber die Belohnungen sind verbesserte Leistung und glücklicher Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8f38e-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="8f38e-110">Vergleichen der Leistungssteigerung, die Sie mit dem Webpart "Inhaltssuche" anstelle des Webparts für Inhaltsabfragen erzielen</span><span class="sxs-lookup"><span data-stu-id="8f38e-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="8f38e-111">Die folgenden Beispiele zeigen die relativen Leistungsgewinne, die Sie möglicherweise erhalten, wenn Sie ein Webpart für die Inhaltssuche anstelle eines Inhaltsabfrage-Webparts verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f38e-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="8f38e-112">Die Effekte sind mit einer komplexen Websitestruktur und sehr umfangreichen Inhaltsabfragen deutlicher.</span><span class="sxs-lookup"><span data-stu-id="8f38e-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="8f38e-113">Diese Beispielwebsite weist die folgenden Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="8f38e-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="8f38e-114">8 Ebenen von Unterwebsites.</span><span class="sxs-lookup"><span data-stu-id="8f38e-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="8f38e-115">Listet die Verwendung eines benutzerdefinierten Inhaltstyps "Fruit" auf.</span><span class="sxs-lookup"><span data-stu-id="8f38e-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="8f38e-116">Im Webpart ist die Inhaltsabfrage breit und gibt alle Elemente mit dem Inhaltstyp "Fruit" zurück.</span><span class="sxs-lookup"><span data-stu-id="8f38e-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="8f38e-117">Im Beispiel werden nur 50-Elemente auf den 8 Websites verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f38e-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="8f38e-118">Die Effekte werden für Websites mit mehr Inhalt noch ausgeprägter.</span><span class="sxs-lookup"><span data-stu-id="8f38e-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="8f38e-119">Es folgt ein Screenshot der Ergebnisse des Webpart für Inhaltsabfragen.</span><span class="sxs-lookup"><span data-stu-id="8f38e-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Grafik mit Inhaltsabfrage für WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="8f38e-121">Suchen Sie in Internet Explorer auf der Registerkarte " **Netzwerk** " der F12-Entwicklertools die Details für den Antwortheader.</span><span class="sxs-lookup"><span data-stu-id="8f38e-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="8f38e-122">Im folgenden Screenshot beträgt der Wert für die **SPRequestDuration** für diese Seite 924 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="8f38e-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Screenshot mit Anforderungsdauer von 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="8f38e-124">**SPRequestDuration** gibt an, wie viel Arbeit auf dem Server ausgeführt wird, um die Seite vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="8f38e-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="8f38e-125">Durch das Wechseln von Inhalten nach Abfrage Webparts mit Inhalten durch Such-Webparts wird die Zeit für das Rendern der Seite drastisch reduziert.</span><span class="sxs-lookup"><span data-stu-id="8f38e-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="8f38e-126">Im Gegensatz dazu weist eine Seite mit einem äquivalenten Inhaltssuche-Webpart, das die gleiche Anzahl von Ergebnissen zurückgibt, einen **SPRequestDuration** -Wert von 106 Millisekunden auf, wie in diesem Screenshot gezeigt:</span><span class="sxs-lookup"><span data-stu-id="8f38e-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Screenshot mit Anforderungsdauer von 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="8f38e-128">Hinzufügen eines Inhaltssuche-Webparts in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8f38e-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="8f38e-129">Das Hinzufügen eines Inhaltssuche-Webparts ähnelt einem Webpart für reguläre Inhaltsabfragen sehr.</span><span class="sxs-lookup"><span data-stu-id="8f38e-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="8f38e-130">Weitere Informationen finden Sie im Abschnitt *"Hinzufügen eines Inhaltssuche-Webparts"* unter [Konfigurieren eines Inhaltssuche-Webparts in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="8f38e-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="8f38e-131">Erstellen der richtigen Suchabfrage für das Webpart für die Inhaltssuche</span><span class="sxs-lookup"><span data-stu-id="8f38e-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="8f38e-132">Nachdem Sie das Webpart für die Inhaltssuche hinzugefügt haben, können Sie die Suche verfeinern und die gewünschten Elemente zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8f38e-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="8f38e-133">Ausführliche Anweisungen dazu finden Sie im Abschnitt *"Anzeigen von Inhalten durch Konfigurieren einer erweiterten Abfrage in einem Inhaltssuche-Webpart"* unter [Konfigurieren eines Inhaltssuche-Webparts in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="8f38e-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="8f38e-134">Tool zum Erstellen und Testen von Abfragen</span><span class="sxs-lookup"><span data-stu-id="8f38e-134">Query building and testing tool</span></span>

<span data-ttu-id="8f38e-135">Ein Tool zum Erstellen und Testen komplexer Abfragen finden Sie unter dem [Suchabfrage Tool](https://sp2013searchtool.codeplex.com/) auf CodePlex.</span><span class="sxs-lookup"><span data-stu-id="8f38e-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

