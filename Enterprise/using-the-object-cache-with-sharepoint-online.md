---
title: Verwenden des Objektcaches mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: In diesem Artikel wird der Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 und SharePoint Online erläutert.
ms.openlocfilehash: 16805aee0c6c6828fc2bf81370046dfd0f1c5a70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070541"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="53c56-103">Verwenden des Objektcaches mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53c56-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="53c56-104">In diesem Artikel wird der Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 und SharePoint Online erläutert.</span><span class="sxs-lookup"><span data-stu-id="53c56-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="53c56-105">Die Nutzung des Objektcaches in der SharePoint Online-Bereitstellung hat erhebliche negative Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="53c56-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="53c56-106">Jede Abhängigkeit vom Objektcache in SharePoint Online verringert die Zuverlässigkeit Ihrer Seite.</span><span class="sxs-lookup"><span data-stu-id="53c56-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="53c56-107">Funktionsweise des SharePoint Online-und SharePoint Server 2013-Objektcaches</span><span class="sxs-lookup"><span data-stu-id="53c56-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="53c56-108">Wenn SharePoint Server 2013 lokal gehostet wird, verfügt der Kunde über private Front-End-Webserver, die den Objektcache hosten.</span><span class="sxs-lookup"><span data-stu-id="53c56-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="53c56-109">Dies bedeutet, dass der Cache nur einem Kunden zugeordnet ist und nur durch den verfügbaren Arbeitsspeicher und die Zuordnung zum Objektcache begrenzt wird.</span><span class="sxs-lookup"><span data-stu-id="53c56-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="53c56-110">Da im lokalen Szenario nur ein Kunde bedient wird, haben die Front-End-Webserver in der Regel immer wieder Anforderungen an dieselben Standorte.</span><span class="sxs-lookup"><span data-stu-id="53c56-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="53c56-111">Dies führt dazu, dass der Cache vollständig schnell und voll von den Listen Abfrageergebnissen und SharePoint-Objekten bleibt, die von Ihren Benutzern regelmäßig angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="53c56-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Zeigt Datenverkehr und Last auf lokalen Front-End-Webservern](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="53c56-113">Wenn ein Benutzer zum zweiten Mal eine Seite besucht, wird die Ladezeit der Seite verbessert.</span><span class="sxs-lookup"><span data-stu-id="53c56-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="53c56-114">Nach mindestens vier Lasten derselben Seite wird die Seite auf allen Front-End-Webservern zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="53c56-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="53c56-115">Im Gegensatz dazu gibt es in SharePoint Online viel mehr Server, aber auch viele weitere Websites.</span><span class="sxs-lookup"><span data-stu-id="53c56-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="53c56-116">Jeder Benutzer kann eine Verbindung mit einem anderen Front-End-Webserver herstellen, auf dem der Cache nicht aufgefüllt ist.</span><span class="sxs-lookup"><span data-stu-id="53c56-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="53c56-117">Oder vielleicht wird der Cache für einen Server aufgefüllt, aber der nächste Benutzer des Front-End-Webservers fordert eine Seite von einer anderen Website an.</span><span class="sxs-lookup"><span data-stu-id="53c56-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="53c56-118">Oder, auch wenn der nächste Benutzer dieselbe Seite wie bei seinem vorherigen Besuch anfordert, wird er auf einen anderen Front-End-Webserver verteilt, der diese Seite nicht im Cache hat.</span><span class="sxs-lookup"><span data-stu-id="53c56-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="53c56-119">In diesem letzten Fall helfen die Zwischenspeicherung nicht den Benutzern.</span><span class="sxs-lookup"><span data-stu-id="53c56-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="53c56-120">In der folgenden Abbildung stellt jeder Punkt eine Seite dar, die ein Benutzer anfordert und wo er zwischengespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="53c56-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="53c56-121">Unterschiedliche Farben repräsentieren unterschiedliche Kunden, die die SaaS-Infrastruktur gemeinsam nutzen.</span><span class="sxs-lookup"><span data-stu-id="53c56-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Zeigt die Ergebnisse der Objektzwischenspeicherung in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="53c56-123">Wie Sie im Diagramm sehen können, sind die Chancen eines Benutzers, der einen Server mit der zwischengespeicherten Version Ihrer Seite trifft, gering.</span><span class="sxs-lookup"><span data-stu-id="53c56-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="53c56-124">Außerdem kann der Cache aufgrund des großen Durchsatzes und der Tatsache, dass die Server von vielen Standorten gemeinsam genutzt werden, nicht lange dauern, da nur so viel Speicherplatz zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="53c56-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="53c56-125">Aus all diesen Gründen ist es nicht sinnvoll, Benutzer mit zwischengespeicherten Objekten zu befassen, um eine hohe Benutzerfreundlichkeit und Seitenladezeiten in SharePoint Online sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="53c56-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="53c56-126">Was verwenden wir stattdessen, wenn wir uns nicht auf den Objektcache verlassen können, um die Leistung in SharePoint Online zu verbessern?</span><span class="sxs-lookup"><span data-stu-id="53c56-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="53c56-127">Da Sie in SharePoint Online keine Zwischenspeicherung benötigen, sollten Sie alternative Entwurfsansätze für SharePoint-Anpassungen bewerten, die den Objektcache verwenden.</span><span class="sxs-lookup"><span data-stu-id="53c56-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="53c56-128">Dies führt dazu, dass Ansätze für Leistungsprobleme verwendet werden, die nicht auf der Objektzwischenspeicherung basieren, um für Benutzer gute Ergebnisse zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="53c56-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="53c56-129">Dies wird in einigen der anderen Artikel in dieser Reihe beschrieben und umfasst:</span><span class="sxs-lookup"><span data-stu-id="53c56-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="53c56-130">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53c56-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="53c56-131">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53c56-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="53c56-132">Verwenden von Netzwerken für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="53c56-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="53c56-133">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53c56-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

