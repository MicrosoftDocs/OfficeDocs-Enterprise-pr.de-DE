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
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540729"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="ec368-103">Einführung in die Leistungsoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="ec368-104">In diesem Artikel wird erläutert, welche bestimmter Aspekte, die Sie beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="ec368-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="ec368-105">Inhalt dieses Artikels</span><span class="sxs-lookup"><span data-stu-id="ec368-105">In this article</span></span>

- <span data-ttu-id="ec368-106">[SharePoint Online Metriken](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) und [Schlussfolgerungen aufgrund der Daten](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="ec368-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="ec368-107">Verwenden Sie ein standard-Benutzerkonto, bei der Leistung</span><span class="sxs-lookup"><span data-stu-id="ec368-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="ec368-108">[Verbindung Kategorien für die leistungsoptimierung](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server-Verbindung](introduction-to-performance-tuning-for-sharepoint-online.md#server), [-Verbindung](introduction-to-performance-tuning-for-sharepoint-online.md#network)und [Browser-Verbindung](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="ec368-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="ec368-109">SharePoint Online-Metriken</span><span class="sxs-lookup"><span data-stu-id="ec368-109">SharePoint Online metrics</span></span>
<span data-ttu-id="ec368-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-110"></span></span>

<span data-ttu-id="ec368-111">Die folgenden umfassenden Metriken für SharePoint Online liefern reale Leistungsdaten:</span><span class="sxs-lookup"><span data-stu-id="ec368-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="ec368-112">Wie schnell Seiten geladen werden</span><span class="sxs-lookup"><span data-stu-id="ec368-112">How fast pages load</span></span>
    
- <span data-ttu-id="ec368-113">Wie viele Roundtrips pro Seite erforderlich sind</span><span class="sxs-lookup"><span data-stu-id="ec368-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="ec368-114">Probleme mit dem Dienst</span><span class="sxs-lookup"><span data-stu-id="ec368-114">Issues with the service</span></span>
    
- <span data-ttu-id="ec368-115">Andere Aspekte, die zu Leistungseinbußen führen</span><span class="sxs-lookup"><span data-stu-id="ec368-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="ec368-116">Schlussfolgerungen aufgrund der Daten</span><span class="sxs-lookup"><span data-stu-id="ec368-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="ec368-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-117"></span></span>

<span data-ttu-id="ec368-118">Den Daten können wir Folgendes entnehmen:</span><span class="sxs-lookup"><span data-stu-id="ec368-118">The data tells us:</span></span>
  
- <span data-ttu-id="ec368-119">Die meisten Seiten zeigen auf SharePoint Online eine gute Leistung.</span><span class="sxs-lookup"><span data-stu-id="ec368-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="ec368-120">Nicht angepasste Seiten werden sehr schnell geladen.</span><span class="sxs-lookup"><span data-stu-id="ec368-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="ec368-121">OneDrive for Business, Teamwebsites und Systemseiten, z. B. "_layouts" usw., lassen sich alle schnell laden.</span><span class="sxs-lookup"><span data-stu-id="ec368-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="ec368-122">Die langsamsten 1 % der SharePoint Online-Seiten brauchen mehr als 5.000 Millisekunden zum Laden.</span><span class="sxs-lookup"><span data-stu-id="ec368-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="ec368-p101">Ein einfacher Benchmarktest wäre, die Leistung durch Vergleichen der Ladezeit Ihres eigenen Portals mit der Ladezeit der OneDrive for Business-Homepage zu messen, da sie wenig benutzerdefinierte Funktionen verwendet. Dies ist oft der erste Schritt, um den Sie vom Support gebeten werden, wenn es um die Behandlung von Problemen mit der Netzwerkleistung geht.</span><span class="sxs-lookup"><span data-stu-id="ec368-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="ec368-125">Verwenden Sie ein standard-Benutzerkonto, bei der Leistung</span><span class="sxs-lookup"><span data-stu-id="ec368-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="ec368-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-126"></span></span>

<span data-ttu-id="ec368-127">Ein Websitesammlungsadministrator, Websitebesitzer, Editor oder Mitwirkender kann zusätzliche Sicherheitsgruppen angehören, sind zusätzliche Berechtigungen und aus diesem Grund haben weitere Elemente, die SharePoint auf einer Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="ec368-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="ec368-128">Dies gilt für die lokale SharePoint- und SharePoint Online, aber in einem Szenario: lokal die Unterschiede werden nicht so einfach bemerkt wie in SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ec368-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="ec368-129">Um ordnungsgemäß bewerten, wie eine Seite für Benutzer ausgeführt wird, sollten Sie ein standard-Benutzerkonto verwenden, um zu vermeiden, laden das Schreiben von Steuerelementen und zusätzlichen Datenverkehr im Zusammenhang mit Sicherheitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="ec368-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="ec368-130">Verbindungskategorien für die Leistungsoptimierung</span><span class="sxs-lookup"><span data-stu-id="ec368-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="ec368-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-131"></span></span>

<span data-ttu-id="ec368-p102">Die Verbindungen zwischen Server und Benutzer lassen sich in drei Hauptkomponenten unterteilen. Berücksichtigen Sie diese beim Entwerfen von SharePoint Online-Seiten, um Einblicke in die Ladezeiten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ec368-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="ec368-134">**Server.** Die Server, dass Microsoft in Rechenzentren hostet.</span><span class="sxs-lookup"><span data-stu-id="ec368-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="ec368-135">**Netzwerk.** Microsoft Network, dem Internet und Ihrem lokalen Netzwerk zwischen dem Rechenzentrum und Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ec368-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="ec368-136">**Browser.** In dem die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="ec368-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="ec368-p103">Im Zusammenhang mit diesen drei Verbindungen gibt es in der Regel fünf Gründe, die 95 % der langsamen Seiten verursachen. Jeder dieser Gründe wird in diesem Artikel erläutert:</span><span class="sxs-lookup"><span data-stu-id="ec368-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="ec368-139">Probleme bei der Navigation</span><span class="sxs-lookup"><span data-stu-id="ec368-139">Navigation issues</span></span>
    
- <span data-ttu-id="ec368-140">Rollup von Inhalten</span><span class="sxs-lookup"><span data-stu-id="ec368-140">Content roll up</span></span>
    
- <span data-ttu-id="ec368-141">Große Dateien</span><span class="sxs-lookup"><span data-stu-id="ec368-141">Large files</span></span>
    
- <span data-ttu-id="ec368-142">Viele Anforderungen an den Server</span><span class="sxs-lookup"><span data-stu-id="ec368-142">Many requests to the server</span></span>
    
- <span data-ttu-id="ec368-143">Verarbeitung von Webparts</span><span class="sxs-lookup"><span data-stu-id="ec368-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="ec368-144">Serververbindung</span><span class="sxs-lookup"><span data-stu-id="ec368-144">Server connection</span></span>
<span data-ttu-id="ec368-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-145"></span></span>

<span data-ttu-id="ec368-146">Viele der Probleme, die die Leistung einer lokalen SharePoint-Implementierung beeinflussen, gelten auch für SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ec368-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="ec368-p104">Erwartungsgemäß verfügen Sie bei einer lokalen SharePoint-Implementierung über weitaus mehr Kontrolle über die Leistung der Server. Bei SharePoint Online ist das ein wenig anders. Je mehr Arbeit Sie einen Server machen lassen, desto länger dauert das Rendern einer Seite. Bei Share Point liegt das zum größten Teil an komplexen Seiten mit mehreren Webparts.</span><span class="sxs-lookup"><span data-stu-id="ec368-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="ec368-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-151">SharePoint Online</span></span>
  
![Screenshot von Server online](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="ec368-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="ec368-153">SharePoint</span></span>
  
![Screenshot von Server lokal](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="ec368-p105">Bei SharePoint Online kann es vorkommen, dass bestimmte Seitenanforderungen am Ende mehrere Server aufrufen. So kann es zu einer Kombination aus Anforderungen zwischen Servern für nur eine Anforderung kommen. Diese Interaktionen können die Leistung beim Laden von Seiten stark beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="ec368-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="ec368-158">Beispiele für diese Server-zu-Server-Interaktionen sind:</span><span class="sxs-lookup"><span data-stu-id="ec368-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="ec368-159">Web- zu SQL-Servern</span><span class="sxs-lookup"><span data-stu-id="ec368-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="ec368-160">Web- zu Anwendungsservern</span><span class="sxs-lookup"><span data-stu-id="ec368-160">Web to application servers</span></span>
    
<span data-ttu-id="ec368-p106">Ein weiterer Faktor, der die Serverinteraktionen verlangsamen kann, sind Cachefehler. Im Gegensatz zum lokalen SharePoint besteht die sehr geringe Möglichkeit, dass der gleiche Server für eine Seite verwendet wird, die Sie zuvor besucht haben. Dies führt dazu, dass eine Objektzwischenspeicherung veraltet.</span><span class="sxs-lookup"><span data-stu-id="ec368-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="ec368-163">Netzwerkverbindung</span><span class="sxs-lookup"><span data-stu-id="ec368-163">Network connection</span></span>
<span data-ttu-id="ec368-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-164"></span></span>

<span data-ttu-id="ec368-p107">Mit lokalen SharePoint nicht, die über ein WAN nutzen, können Sie eine schnelle Verbindung zwischen Datacenter und Endbenutzern verwenden. Im Allgemeinen Dinge einfach, aus der Sicht Netzwerk zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ec368-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="ec368-167">Bei SharePoint Online gibt es einige weitere Faktoren, die berücksichtigt werden müssen, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ec368-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="ec368-168">Das Microsoft-Netzwerk</span><span class="sxs-lookup"><span data-stu-id="ec368-168">The Microsoft network</span></span>
    
- <span data-ttu-id="ec368-169">Das Internet</span><span class="sxs-lookup"><span data-stu-id="ec368-169">The Internet</span></span>
    
- <span data-ttu-id="ec368-170">Der Internetdienstanbieter</span><span class="sxs-lookup"><span data-stu-id="ec368-170">The ISP</span></span>
    
<span data-ttu-id="ec368-171">Unabhängig davon, welche Version von SharePoint (und welches Netzwerk) Sie verwenden, können folgende Faktoren dazu führen, dass das Netzwerk ausgelastet ist:</span><span class="sxs-lookup"><span data-stu-id="ec368-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="ec368-172">Große Nutzlast</span><span class="sxs-lookup"><span data-stu-id="ec368-172">Large payload</span></span>
    
- <span data-ttu-id="ec368-173">Viele Dateien</span><span class="sxs-lookup"><span data-stu-id="ec368-173">Many files</span></span>
    
- <span data-ttu-id="ec368-174">Große physische Entfernung zum Server</span><span class="sxs-lookup"><span data-stu-id="ec368-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="ec368-p108">Eine Funktion, die Sie in SharePoint Online nutzen können ist dem Microsoft CDN (Content Delivery Network). Ein CDN ist im Wesentlichen eine verteilte Sammlung von Servern, die in mehreren Rechenzentren bereitgestellt. Mit einem CDN kann Inhalte auf Seiten auf einem Server in der Nähe des Clients gehostet werden, selbst wenn der Client weit weg von der SharePoint-Ausgangsserver ist. Microsoft wird dieses Thema in der Zukunft verwenden, um lokale Instanzen von Seiten, die nicht angepasst werden können, beispielsweise der SharePoint Online Admin Homepage gespeichert. Weitere Informationen zu CDNs finden Sie unter [Inhaltsübermittlung](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span><span class="sxs-lookup"><span data-stu-id="ec368-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="ec368-p109">Etwas, das Sie berücksichtigen müssen, aber möglicherweise nicht großartig beeinflussen können, ist die Verbindungsgeschwindigkeit des Internetdienstanbieters. Mit einem einfachen Tool zum Testen der Geschwindigkeit können Sie die Verbindungsgeschwindigkeit messen.</span><span class="sxs-lookup"><span data-stu-id="ec368-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="ec368-182">Browserverbindung</span><span class="sxs-lookup"><span data-stu-id="ec368-182">Browser connection</span></span>
<span data-ttu-id="ec368-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="ec368-183"></span></span>

<span data-ttu-id="ec368-184">Es gibt einige Faktoren, die hinsichtlich der Leistung bei Webbrowsern zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="ec368-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="ec368-p110">Besuchen komplexe Seiten wird die Leistung beeinträchtigen. Den meisten Browsern haben nur einen kleinen Cache (etwa 90MB), während der Durchschnitt Webseite ist in der Regel rund um 1,6 MB. Nicht dauert aufgebraucht lange.</span><span class="sxs-lookup"><span data-stu-id="ec368-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="ec368-p111">Bandbreite sein ein Problem auch. Beispielsweise wenn ein Benutzer in einer anderen Sitzung sich Videos ansehen ist, wirkt die Leistung Ihrer SharePoint-Seite sich dies. Während Sie streaming Media verhindert, dass Benutzer ist nicht möglich, können Sie die Möglichkeit für Benutzer eine Seite lädt steuern.</span><span class="sxs-lookup"><span data-stu-id="ec368-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="ec368-191">Checken Sie die folgenden Artikel für verschiedene SharePoint Online Seite Anpassungsmethoden und andere empfohlene Vorgehensweisen können Sie eine optimale Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="ec368-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="ec368-192">Navigationsoptionen für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-193">Verwenden Sie das Seite-Diagnosetool für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="ec368-194">Bildoptimierung für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-195">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-196">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-197">Verwenden von Netzwerken für die Inhaltsübermittlung</span><span class="sxs-lookup"><span data-stu-id="ec368-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-198">Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="ec368-199">Capacity planning und Auslastungstests SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-200">Diagnose von Leistungsproblemen mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-201">Verwenden des Objektcaches mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="ec368-202">Gewusst wie: Vermeiden von Drosselung und Sperren in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec368-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

