---
title: Einführung in die Leistungsoptimierung für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: In diesem Artikel wird erläutert, welche bestimmter Aspekte, die Sie beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigen müssen.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219875"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="5602c-103">Einführung in die Leistungsoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="5602c-104">In diesem Artikel wird erläutert, welche bestimmter Aspekte, die Sie beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="5602c-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="5602c-105">SharePoint Online-Metriken</span><span class="sxs-lookup"><span data-stu-id="5602c-105">SharePoint Online metrics</span></span>

<span data-ttu-id="5602c-106">Die folgenden umfassenden Metriken für SharePoint Online liefern reale Leistungsdaten:</span><span class="sxs-lookup"><span data-stu-id="5602c-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="5602c-107">Wie schnell Seiten geladen werden</span><span class="sxs-lookup"><span data-stu-id="5602c-107">How fast pages load</span></span>
    
- <span data-ttu-id="5602c-108">Wie viele Roundtrips pro Seite erforderlich sind</span><span class="sxs-lookup"><span data-stu-id="5602c-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="5602c-109">Probleme mit dem Dienst</span><span class="sxs-lookup"><span data-stu-id="5602c-109">Issues with the service</span></span>
    
- <span data-ttu-id="5602c-110">Andere Aspekte, die zu Leistungseinbußen führen</span><span class="sxs-lookup"><span data-stu-id="5602c-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="5602c-111">Schlussfolgerungen aufgrund der Daten</span><span class="sxs-lookup"><span data-stu-id="5602c-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="5602c-112">Den Daten können wir Folgendes entnehmen:</span><span class="sxs-lookup"><span data-stu-id="5602c-112">The data tells us:</span></span>
  
- <span data-ttu-id="5602c-113">Die meisten Seiten zeigen auf SharePoint Online eine gute Leistung.</span><span class="sxs-lookup"><span data-stu-id="5602c-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="5602c-114">Nicht angepasste Seiten werden sehr schnell geladen.</span><span class="sxs-lookup"><span data-stu-id="5602c-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="5602c-115">OneDrive for Business, Teamwebsites und Systemseiten, z. B. "_layouts" usw., lassen sich alle schnell laden.</span><span class="sxs-lookup"><span data-stu-id="5602c-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="5602c-116">Die langsamsten 1 % der SharePoint Online-Seiten brauchen mehr als 5.000 Millisekunden zum Laden.</span><span class="sxs-lookup"><span data-stu-id="5602c-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="5602c-p101">Ein einfacher Benchmarktest wäre, die Leistung durch Vergleichen der Ladezeit Ihres eigenen Portals mit der Ladezeit der OneDrive for Business-Homepage zu messen, da sie wenig benutzerdefinierte Funktionen verwendet. Dies ist oft der erste Schritt, um den Sie vom Support gebeten werden, wenn es um die Behandlung von Problemen mit der Netzwerkleistung geht.</span><span class="sxs-lookup"><span data-stu-id="5602c-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="5602c-119">Verwenden Sie ein standard-Benutzerkonto, bei der Leistung</span><span class="sxs-lookup"><span data-stu-id="5602c-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="5602c-120">Ein Websitesammlungsadministrator, Websitebesitzer, Editor oder Mitwirkender kann zusätzliche Sicherheitsgruppen angehören, sind zusätzliche Berechtigungen und aus diesem Grund haben weitere Elemente, die SharePoint auf einer Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="5602c-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="5602c-121">Dies gilt für die lokale SharePoint- und SharePoint Online, aber in einem Szenario: lokal die Unterschiede werden nicht so einfach bemerkt wie in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5602c-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="5602c-122">Um ordnungsgemäß bewerten, wie eine Seite für Benutzer ausgeführt wird, sollten Sie ein standard-Benutzerkonto verwenden, um zu vermeiden, laden das Schreiben von Steuerelementen und zusätzlichen Datenverkehr im Zusammenhang mit Sicherheitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="5602c-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="5602c-123">Verbindungskategorien für die Leistungsoptimierung</span><span class="sxs-lookup"><span data-stu-id="5602c-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="5602c-p102">Die Verbindungen zwischen Server und Benutzer lassen sich in drei Hauptkomponenten unterteilen. Berücksichtigen Sie diese beim Entwerfen von SharePoint Online-Seiten, um Einblicke in die Ladezeiten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5602c-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="5602c-126">**Server** Die Server, dass Microsoft in Rechenzentren hostet.</span><span class="sxs-lookup"><span data-stu-id="5602c-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="5602c-127">**Netzwerk** Microsoft Network, dem Internet und Ihrem lokalen Netzwerk zwischen dem Rechenzentrum und Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5602c-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="5602c-128">**Browser** In dem die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="5602c-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="5602c-p103">Im Zusammenhang mit diesen drei Verbindungen gibt es in der Regel fünf Gründe, die 95 % der langsamen Seiten verursachen. Jeder dieser Gründe wird in diesem Artikel erläutert:</span><span class="sxs-lookup"><span data-stu-id="5602c-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="5602c-131">Probleme bei der Navigation</span><span class="sxs-lookup"><span data-stu-id="5602c-131">Navigation issues</span></span>
    
- <span data-ttu-id="5602c-132">Rollup von Inhalten</span><span class="sxs-lookup"><span data-stu-id="5602c-132">Content roll up</span></span>
    
- <span data-ttu-id="5602c-133">Große Dateien</span><span class="sxs-lookup"><span data-stu-id="5602c-133">Large files</span></span>
    
- <span data-ttu-id="5602c-134">Viele Anforderungen an den Server</span><span class="sxs-lookup"><span data-stu-id="5602c-134">Many requests to the server</span></span>
    
- <span data-ttu-id="5602c-135">Verarbeitung von Webparts</span><span class="sxs-lookup"><span data-stu-id="5602c-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="5602c-136">Serververbindung</span><span class="sxs-lookup"><span data-stu-id="5602c-136">Server connection</span></span>

<span data-ttu-id="5602c-137">Viele der Probleme, die die Leistung einer lokalen SharePoint-Implementierung beeinflussen, gelten auch für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5602c-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="5602c-p104">Erwartungsgemäß verfügen Sie bei einer lokalen SharePoint-Implementierung über weitaus mehr Kontrolle über die Leistung der Server. Bei SharePoint Online ist das ein wenig anders. Je mehr Arbeit Sie einen Server machen lassen, desto länger dauert das Rendern einer Seite. Bei Share Point liegt das zum größten Teil an komplexen Seiten mit mehreren Webparts.</span><span class="sxs-lookup"><span data-stu-id="5602c-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="5602c-142">SharePoint Server lokal</span><span class="sxs-lookup"><span data-stu-id="5602c-142">SharePoint Server on-premises</span></span>
  
![Screenshot von Server lokal](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="5602c-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-144">SharePoint Online</span></span>
  
![Screenshot von Server online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="5602c-p105">Bei SharePoint Online kann es vorkommen, dass bestimmte Seitenanforderungen am Ende mehrere Server aufrufen. So kann es zu einer Kombination aus Anforderungen zwischen Servern für nur eine Anforderung kommen. Diese Interaktionen können die Leistung beim Laden von Seiten stark beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="5602c-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="5602c-149">Beispiele für diese Server-zu-Server-Interaktionen sind:</span><span class="sxs-lookup"><span data-stu-id="5602c-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="5602c-150">Web- zu SQL-Servern</span><span class="sxs-lookup"><span data-stu-id="5602c-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="5602c-151">Web- zu Anwendungsservern</span><span class="sxs-lookup"><span data-stu-id="5602c-151">Web to application servers</span></span>
    
<span data-ttu-id="5602c-p106">Ein weiterer Faktor, der die Serverinteraktionen verlangsamen kann, sind Cachefehler. Im Gegensatz zum lokalen SharePoint besteht die sehr geringe Möglichkeit, dass der gleiche Server für eine Seite verwendet wird, die Sie zuvor besucht haben. Dies führt dazu, dass eine Objektzwischenspeicherung veraltet.</span><span class="sxs-lookup"><span data-stu-id="5602c-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="5602c-154">Netzwerkverbindung</span><span class="sxs-lookup"><span data-stu-id="5602c-154">Network connection</span></span>

<span data-ttu-id="5602c-p107">Mit lokalen SharePoint nicht, die über ein WAN nutzen, können Sie eine schnelle Verbindung zwischen Datacenter und Endbenutzern verwenden. Im Allgemeinen Dinge einfach, aus der Sicht Netzwerk zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="5602c-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="5602c-157">Bei SharePoint Online gibt es einige weitere Faktoren, die berücksichtigt werden müssen, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5602c-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="5602c-158">Das Microsoft-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="5602c-158">The Microsoft network</span></span>
    
- <span data-ttu-id="5602c-159">Das Internet</span><span class="sxs-lookup"><span data-stu-id="5602c-159">The Internet</span></span>
    
- <span data-ttu-id="5602c-160">Der Internetdienstanbieter</span><span class="sxs-lookup"><span data-stu-id="5602c-160">The ISP</span></span>
    
<span data-ttu-id="5602c-161">Unabhängig davon, welche Version von SharePoint (und welches Netzwerk) Sie verwenden, können folgende Faktoren dazu führen, dass das Netzwerk ausgelastet ist:</span><span class="sxs-lookup"><span data-stu-id="5602c-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="5602c-162">Große Nutzlast</span><span class="sxs-lookup"><span data-stu-id="5602c-162">Large payload</span></span>
    
- <span data-ttu-id="5602c-163">Viele Dateien</span><span class="sxs-lookup"><span data-stu-id="5602c-163">Many files</span></span>
    
- <span data-ttu-id="5602c-164">Große physische Entfernung zum Server</span><span class="sxs-lookup"><span data-stu-id="5602c-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="5602c-p108">Eine Funktion, die Sie in SharePoint Online nutzen können ist dem Microsoft CDN (Content Delivery Network). Ein CDN ist im Wesentlichen eine verteilte Sammlung von Servern, die in mehreren Rechenzentren bereitgestellt. Mit einem CDN kann Inhalte auf Seiten auf einem Server in der Nähe des Clients gehostet werden, selbst wenn der Client weit weg von der SharePoint-Ausgangsserver ist. Microsoft wird dieses Thema in der Zukunft verwenden, um lokale Instanzen von Seiten, die nicht angepasst werden können, beispielsweise der SharePoint Online Admin Homepage gespeichert. Weitere Informationen zu CDNs finden Sie unter [Inhaltsübermittlung](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="5602c-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="5602c-p109">Etwas, das Sie berücksichtigen müssen, aber möglicherweise nicht großartig beeinflussen können, ist die Verbindungsgeschwindigkeit des Internetdienstanbieters. Mit einem einfachen Tool zum Testen der Geschwindigkeit können Sie die Verbindungsgeschwindigkeit messen.</span><span class="sxs-lookup"><span data-stu-id="5602c-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="5602c-172">Browserverbindung</span><span class="sxs-lookup"><span data-stu-id="5602c-172">Browser connection</span></span>

<span data-ttu-id="5602c-173">Es gibt einige Faktoren, die hinsichtlich der Leistung bei Webbrowsern zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="5602c-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="5602c-p110">Besuchen komplexe Seiten wird die Leistung beeinträchtigen. Den meisten Browsern haben nur einen kleinen Cache (etwa 90MB), während der Durchschnitt Webseite ist in der Regel rund um 1,6 MB. Nicht dauert aufgebraucht lange.</span><span class="sxs-lookup"><span data-stu-id="5602c-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="5602c-p111">Bandbreite sein ein Problem auch. Beispielsweise wenn ein Benutzer in einer anderen Sitzung sich Videos ansehen ist, wirkt die Leistung Ihrer SharePoint-Seite sich dies. Während Sie streaming Media verhindert, dass Benutzer ist nicht möglich, können Sie die Möglichkeit für Benutzer eine Seite lädt steuern.</span><span class="sxs-lookup"><span data-stu-id="5602c-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="5602c-180">Checken Sie die folgenden Artikel für verschiedene SharePoint Online Seite Anpassungsmethoden und andere empfohlene Vorgehensweisen können Sie eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="5602c-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="5602c-181">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-182">Verwenden Sie das Seite-Diagnosetool für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="5602c-183">Bildoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-184">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-185">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-186">Verwenden von Netzwerken für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="5602c-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-187">Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="5602c-188">Capacity planning und Auslastungstests SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-189">Diagnose von Leistungsproblemen mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-190">Verwenden des Objektcaches mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="5602c-191">Gewusst wie: Vermeiden von Drosselung und Sperren in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5602c-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

