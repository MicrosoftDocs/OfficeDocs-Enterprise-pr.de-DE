---
title: Einführung in die Leistungsoptimierung für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: In diesem Artikel wird erläutert, welche Aspekte beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigt werden müssen.
ms.openlocfilehash: 4743364f6e8a1e84800085d0875abad84491780b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067211"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="256bc-103">Einführung in die Leistungsoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="256bc-104">In diesem Artikel wird erläutert, welche Aspekte beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="256bc-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="256bc-105">SharePoint Online-Metriken</span><span class="sxs-lookup"><span data-stu-id="256bc-105">SharePoint Online metrics</span></span>

<span data-ttu-id="256bc-106">Die folgenden allgemeinen Metriken für SharePoint Online bieten reale Daten zur Leistung:</span><span class="sxs-lookup"><span data-stu-id="256bc-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="256bc-107">Wie schnelle Seiten geladen werden</span><span class="sxs-lookup"><span data-stu-id="256bc-107">How fast pages load</span></span>
    
- <span data-ttu-id="256bc-108">Wie viele Roundtrips pro Seite erforderlich sind</span><span class="sxs-lookup"><span data-stu-id="256bc-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="256bc-109">Probleme mit dem Dienst</span><span class="sxs-lookup"><span data-stu-id="256bc-109">Issues with the service</span></span>
    
- <span data-ttu-id="256bc-110">Andere Aspekte, die zu Leistungsbeeinträchtigungen führen</span><span class="sxs-lookup"><span data-stu-id="256bc-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="256bc-111">Schlussfolgerungen aufgrund der Daten</span><span class="sxs-lookup"><span data-stu-id="256bc-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="256bc-112">Die Daten teilen uns Folgendes mit:</span><span class="sxs-lookup"><span data-stu-id="256bc-112">The data tells us:</span></span>
  
- <span data-ttu-id="256bc-113">Die meisten Seiten werden in SharePoint Online gut ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="256bc-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="256bc-114">Nicht angepasste Seiten werden sehr schnell geladen.</span><span class="sxs-lookup"><span data-stu-id="256bc-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="256bc-115">OneDrive for Business, Teamwebsites und System Seiten wie _layouts usw. sind alle schnell zu laden.</span><span class="sxs-lookup"><span data-stu-id="256bc-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="256bc-116">Die langsamsten 1% der SharePoint Online-Seiten benötigen mehr als 5.000 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="256bc-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="256bc-117">Ein einfacher Benchmark-Test, den Sie verwenden können, wäre das Messen der Leistung, indem die Ladezeit des eigenen Portals mit der Ladezeit der OneDrive for Business-Startseite verglichen wird, da nur wenige angepasste Features verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="256bc-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="256bc-118">Dies ist häufig der erste Schritt, den Sie beim Beheben von Problemen mit der Netzwerkleistung bei der Unterstützung durchführen müssen.</span><span class="sxs-lookup"><span data-stu-id="256bc-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="256bc-119">Verwenden eines Standardbenutzerkontos beim Überprüfen der Leistung</span><span class="sxs-lookup"><span data-stu-id="256bc-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="256bc-120">Ein Website Sammlungs Administrator, Websitebesitzer, Editor oder Mitwirkender gehört zu zusätzlichen Sicherheitsgruppen, verfügt über zusätzliche Berechtigungen und verfügt daher über zusätzliche Elemente, die SharePoint auf einer Seite lädt.</span><span class="sxs-lookup"><span data-stu-id="256bc-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="256bc-121">Dies gilt für SharePoint on-premises und SharePoint Online, aber in einem lokalen Szenario sind die Unterschiede nicht so leicht zu erkennen wie in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="256bc-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="256bc-122">Um zu ermitteln, wie eine Seite für Benutzer ausgeführt wird, sollten Sie ein Standardbenutzerkonto verwenden, um die Erstellungs Steuerelemente und den zusätzlichen Datenverkehr im Zusammenhang mit Sicherheitsgruppen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="256bc-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="256bc-123">Verbindungskategorien für die Leistungsoptimierung</span><span class="sxs-lookup"><span data-stu-id="256bc-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="256bc-124">Sie können die Verbindungen zwischen dem Server und dem Benutzer in drei Hauptkomponenten kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="256bc-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="256bc-125">Berücksichtigen Sie diese beim Entwerfen von SharePoint Online-Seiten für Einblicke in Ladezeiten.</span><span class="sxs-lookup"><span data-stu-id="256bc-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="256bc-126">**Server** Die Server, die Microsoft in Rechenzentren hostet.</span><span class="sxs-lookup"><span data-stu-id="256bc-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="256bc-127">**Netzwerk** Das Microsoft-Netzwerk, das Internet und Ihr lokales Netzwerk zwischen dem Rechenzentrum und ihren Benutzern.</span><span class="sxs-lookup"><span data-stu-id="256bc-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="256bc-128">**Browser** Wo die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="256bc-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="256bc-129">Innerhalb dieser drei Verbindungen gibt es normalerweise fünf Gründe, die 95% der langsamen Seiten verursachen.</span><span class="sxs-lookup"><span data-stu-id="256bc-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="256bc-130">Jeder dieser Gründe wird in diesem Artikel behandelt:</span><span class="sxs-lookup"><span data-stu-id="256bc-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="256bc-131">Navigationsprobleme</span><span class="sxs-lookup"><span data-stu-id="256bc-131">Navigation issues</span></span>
    
- <span data-ttu-id="256bc-132">Inhalts Rollup</span><span class="sxs-lookup"><span data-stu-id="256bc-132">Content roll up</span></span>
    
- <span data-ttu-id="256bc-133">Umfangreiche Dateien</span><span class="sxs-lookup"><span data-stu-id="256bc-133">Large files</span></span>
    
- <span data-ttu-id="256bc-134">Viele Anforderungen an den Server</span><span class="sxs-lookup"><span data-stu-id="256bc-134">Many requests to the server</span></span>
    
- <span data-ttu-id="256bc-135">Webpart-Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="256bc-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="256bc-136">Server Verbindung</span><span class="sxs-lookup"><span data-stu-id="256bc-136">Server connection</span></span>

<span data-ttu-id="256bc-137">Viele der Probleme, die sich auf die Leistung mit SharePoint lokal auswirken, gelten auch für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="256bc-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="256bc-138">Wie Sie erwarten, haben Sie weitaus mehr Kontrolle darüber, wie Server mit lokalem SharePoint ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="256bc-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="256bc-139">Bei SharePoint Online sind die Dinge etwas anders.</span><span class="sxs-lookup"><span data-stu-id="256bc-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="256bc-140">Je mehr Arbeit Sie an einem Server vornehmen, desto länger dauert das Rendern einer Seite.</span><span class="sxs-lookup"><span data-stu-id="256bc-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="256bc-141">Bei SharePoint ist der größte Übeltäter in dieser Hinsicht komplexe Seiten mit mehreren Webparts.</span><span class="sxs-lookup"><span data-stu-id="256bc-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="256bc-142">SharePoint Server lokal</span><span class="sxs-lookup"><span data-stu-id="256bc-142">SharePoint Server on-premises</span></span>
  
![Screenshot des lokalen Servers](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="256bc-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-144">SharePoint Online</span></span>
  
![Screenshot von Server Online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="256bc-146">Bei SharePoint Online können bestimmte Seitenanforderungen tatsächlich mehrere Server anrufen.</span><span class="sxs-lookup"><span data-stu-id="256bc-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="256bc-147">Sie können eine Matrix von Anforderungen zwischen Servern für eine einzelne Anforderung erhalten.</span><span class="sxs-lookup"><span data-stu-id="256bc-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="256bc-148">Diese Interaktionen sind aus der Seiten Lade Perspektive teuer und machen die Dinge langsam.</span><span class="sxs-lookup"><span data-stu-id="256bc-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="256bc-149">Beispiele für diese Server-zu-Server-Interaktionen sind:</span><span class="sxs-lookup"><span data-stu-id="256bc-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="256bc-150">Web-zu-SQL-Server</span><span class="sxs-lookup"><span data-stu-id="256bc-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="256bc-151">Webserver für Anwendungsserver</span><span class="sxs-lookup"><span data-stu-id="256bc-151">Web to application servers</span></span>
    
<span data-ttu-id="256bc-152">Das andere, was die Serverinteraktionen verlangsamen kann, sind Cachefehler.</span><span class="sxs-lookup"><span data-stu-id="256bc-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="256bc-153">Im Gegensatz zu lokalen SharePoint, gibt es eine sehr geringe Wahrscheinlichkeit, dass Sie den gleichen Server für eine Seite getroffen haben, die Sie zuvor besucht haben; Dadurch ist das Objekt Zwischenspeichern veraltet.</span><span class="sxs-lookup"><span data-stu-id="256bc-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="256bc-154">Netzwerkverbindung </span><span class="sxs-lookup"><span data-stu-id="256bc-154">Network connection</span></span>

<span data-ttu-id="256bc-155">Bei der lokalen SharePoint-Anwendung, die kein WAN verwendet, können Sie eine Hochgeschwindigkeitsverbindung zwischen Datencenter und Endbenutzern verwenden.</span><span class="sxs-lookup"><span data-stu-id="256bc-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="256bc-156">Im Allgemeinen ist die Verwaltung über eine Netzwerk Perspektive einfach.</span><span class="sxs-lookup"><span data-stu-id="256bc-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="256bc-157">Bei SharePoint Online gibt es einige weitere Faktoren, die berücksichtigt werden müssen. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="256bc-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="256bc-158">Das Microsoft-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="256bc-158">The Microsoft network</span></span>
    
- <span data-ttu-id="256bc-159">Das Internet</span><span class="sxs-lookup"><span data-stu-id="256bc-159">The Internet</span></span>
    
- <span data-ttu-id="256bc-160">Der ISP</span><span class="sxs-lookup"><span data-stu-id="256bc-160">The ISP</span></span>
    
<span data-ttu-id="256bc-161">Unabhängig davon, welche Version von SharePoint (und welches Netzwerk) Sie verwenden, können die folgenden Aspekte in der Regel dazu führen, dass das Netzwerk ausgelastet ist:</span><span class="sxs-lookup"><span data-stu-id="256bc-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="256bc-162">Hohe Nutzlast</span><span class="sxs-lookup"><span data-stu-id="256bc-162">Large payload</span></span>
    
- <span data-ttu-id="256bc-163">Viele Dateien</span><span class="sxs-lookup"><span data-stu-id="256bc-163">Many files</span></span>
    
- <span data-ttu-id="256bc-164">Grosser physischer Abstand zum Server</span><span class="sxs-lookup"><span data-stu-id="256bc-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="256bc-165">Ein Feature, das Sie in SharePoint Online nutzen können, ist das Microsoft CDN (Content Delivery Network).</span><span class="sxs-lookup"><span data-stu-id="256bc-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="256bc-166">Ein CDN ist im Grunde eine verteilte Sammlung von Servern, die über mehrere Rechenzentren bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="256bc-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="256bc-167">Mit einem CDN können Inhalte auf Seiten auf einem Server in der Nähe des Clients gehostet werden, selbst wenn der Client weit entfernt vom ursprünglichen SharePoint-Server ist.</span><span class="sxs-lookup"><span data-stu-id="256bc-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="256bc-168">Microsoft verwendet dies künftig mehr, um lokale Instanzen von Seiten zu speichern, die nicht angepasst werden können, beispielsweise die Homepage des SharePoint Online-Administrators.</span><span class="sxs-lookup"><span data-stu-id="256bc-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="256bc-169">Weitere Informationen zu CDNs finden Sie unter [Content](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)Subnetze.</span><span class="sxs-lookup"><span data-stu-id="256bc-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="256bc-170">Etwas, das Sie beachten müssen, aber möglicherweise nicht viel zu tun ist, ist die Verbindungsgeschwindigkeit Ihres ISP.</span><span class="sxs-lookup"><span data-stu-id="256bc-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="256bc-171">Mit einem einfachen Geschwindigkeitstest Tool wird Ihnen die Verbindungsgeschwindigkeit mitgeteilt.</span><span class="sxs-lookup"><span data-stu-id="256bc-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="256bc-172">Browser Verbindung</span><span class="sxs-lookup"><span data-stu-id="256bc-172">Browser connection</span></span>

<span data-ttu-id="256bc-173">Es gibt einige Faktoren, die von einer Leistungsperspektive aus mit Webbrowsern berücksichtigt werden sollten.</span><span class="sxs-lookup"><span data-stu-id="256bc-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="256bc-174">Der Besuch komplexer Seiten wirkt sich auf die Leistung aus.</span><span class="sxs-lookup"><span data-stu-id="256bc-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="256bc-175">Die meisten Browser haben nur einen kleinen Cache (um 90MB), während die durchschnittliche Webseite normalerweise ungefähr 1,6 MB beträgt.</span><span class="sxs-lookup"><span data-stu-id="256bc-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="256bc-176">Es dauert nicht lange, bis Sie sich verbraucht haben.</span><span class="sxs-lookup"><span data-stu-id="256bc-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="256bc-177">Bandbreite kann auch ein Problem sein.</span><span class="sxs-lookup"><span data-stu-id="256bc-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="256bc-178">Wenn ein Benutzer beispielsweise Videos in einer anderen Sitzung ansieht, wirkt sich dies auf die Leistung Ihrer SharePoint-Seite aus.</span><span class="sxs-lookup"><span data-stu-id="256bc-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="256bc-179">Sie können zwar nicht verhindern, dass Benutzer Streaming-Medien, aber Sie steuern, wie eine Seite für Benutzer geladen wird.</span><span class="sxs-lookup"><span data-stu-id="256bc-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="256bc-180">In den folgenden Artikeln finden Sie unterschiedliche Techniken für die SharePoint Online-Seite und andere bewährte Methoden, um eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="256bc-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="256bc-181">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-182">Verwenden des Seiten Diagnosetools für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="256bc-183">Bildoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-184">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-185">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-186">Verwenden von Netzwerken für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="256bc-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-187">Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="256bc-188">Kapazitätsplanung und Auslastungstests für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-189">Diagnose von Leistungsproblemen mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-190">Verwenden des Objektcaches mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="256bc-191">Gewusst wie: Vermeiden von Einschränkungen oder Sperren in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="256bc-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

