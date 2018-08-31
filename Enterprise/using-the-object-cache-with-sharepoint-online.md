---
title: Verwenden des Objektcaches mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: In diesem Artikel erläutert den Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 lokal und SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540874"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="52def-103">Verwenden des Objektcaches mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52def-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="52def-104">In diesem Artikel erläutert den Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 lokal und SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="52def-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="52def-p101">Wenn Sie sich auf den Objektcache in SharePoint Online verlassen, ist dies mit bedeutenden Nachteilen verbunden. Jede Abhängigkeit vom Objektcache in SharePoint Online beeinträchtigt die Zuverlässigkeit der Seite.</span><span class="sxs-lookup"><span data-stu-id="52def-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="52def-107">Wie die SharePoint Online und SharePoint Server 2013 Cache arbeitet Geschäftsobjekt</span><span class="sxs-lookup"><span data-stu-id="52def-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="52def-p102">Wenn SharePoint Server 2013 gehosteten lokalen ist, kann der Kunde auf private Front-End-Webservern, die den Objektcache zu hosten. Dies bedeutet, dass Cache ist ausschließlich für einen Kunden und wird nur begrenzt, nach wie viel Arbeitsspeicher verfügbar und den Objektcache zugewiesen ist. Da nur einen Kunden im lokalen Szenario mit die Front-End-Webservern in der Regel bereitgestellt wird, können Sie Benutzer, die Anfragen immer wieder an dieselben Standorte vorgenommen. Dies bedeutet, dass der Cache vollständige schnell ruft und bleibt die vollständige Liste Abfrageergebnissen und SharePoint-Objekte, die Ihre Benutzer in regelmäßigen Abständen anfordern.</span><span class="sxs-lookup"><span data-stu-id="52def-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Zeigt lokalen Front-End-Webservern Datenverkehr und Auslastung](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="52def-p103">Wenn ein Benutzer also eine Seite zum zweiten Mal besucht, verbessert sich die Ladezeit der Seite. Nach mindestens vier Ladevorgängen der gleichen Seite wird die Seite auf allen Front-End-Webservern zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="52def-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="52def-p104">Im Gegensatz dazu in SharePoint Online sind viele weitere Server jedoch auch viele weitere Websites. Jeder Benutzer kann auf einen anderen Front-End-Webserver verbinden, für das die Clientcache gefüllt ist. Oder vielleicht der Cache für einen Server aufgefüllt erhalten möchten, aber die fordert eine Seite an des nächsten Benutzers an diesen Front-End-Webserver aus einer anderen Website. Oder, selbst wenn der nächste Benutzer die gleiche Seite wie bei ihrer vorherigen Besuch anfordert, sie sind mit Lastenausgleich an einem anderen Front-End-Webserver, der diese Seite nicht in seinem Cache enthalten ist. In diesem Fall helfen nicht Zwischenspeichern der Benutzer in allen.</span><span class="sxs-lookup"><span data-stu-id="52def-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="52def-p105">In der folgenden Abbildung stellt jeder Punkt eine Seite dar, die ein Benutzer anfordert, und gibt an, wo sie zwischengespeichert ist. Die verschiedenen Farben stehen für die unterschiedlichen Kunden, die die SaaS-Infrastruktur gemeinsam nutzen.</span><span class="sxs-lookup"><span data-stu-id="52def-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Zeigt die Ergebnisse der Zwischenspeicherung von Objekten in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="52def-p106">Wie Sie aus dem Diagramm sehen können, sind die Wahrscheinlichkeit, dass alle Benutzer auf einem Server mit der ihre Seite die zwischengespeicherte Version schlanke. Darüber hinaus letzte nicht aufgrund der großen Durchsatz und die Tatsache, dass die Server von vielen Standorten gemeinsam genutzt werden, der Cache lange, da nur so viel Speicherplatz für das Zwischenspeichern vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="52def-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="52def-125">Aus all diesen Gründen sollte man sich nicht darauf verlassen, dass die Benutzer zwischengespeicherte Objekte aufrufen. Dies ist kein effektiver Ansatz, um eine hohe Benutzerfreundlichkeit und ein schnelles Laden von Seiten in SharePoint Online sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="52def-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="52def-126">Aber wenn wir uns nicht auf den Objektcache zur Verbesserung der Leistung in SharePoint Online verlassen können, was können wir stattdessen verwenden?</span><span class="sxs-lookup"><span data-stu-id="52def-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="52def-p107">Da Sie sich nicht auf die Zwischenspeicherung in SharePoint Online verlassen sollten, müssen Sie alternative Designansätze für SharePoint-Anpassungen erwägen, die den Objektcache verwenden. Sie sollten Ansätze für Leistungsprobleme finden, die sich nicht auf das Zwischenspeichern von Objekten stützen, um für die Benutzer gute Ergebnisse zu erzielen. Dies wird in einigen der anderen Artikel dieser Reihe beschrieben:</span><span class="sxs-lookup"><span data-stu-id="52def-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="52def-130">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52def-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="52def-131">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52def-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="52def-132">Verwenden von Netzwerken für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="52def-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="52def-133">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="52def-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

