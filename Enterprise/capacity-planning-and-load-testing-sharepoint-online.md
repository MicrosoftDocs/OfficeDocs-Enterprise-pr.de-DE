---
title: Capacity planning und Auslastungstests SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Dieser Artikel beschreibt, wie Sie bereitstellen können mit SharePoint Online ohne herkömmlichen Auslastungstests, da es nicht zulässig ist.
ms.openlocfilehash: 6a22ee089adc0817f5c52bbfee5f2b41d7e5d80c
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181026"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="c3437-103">Capacity planning und Auslastungstests SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c3437-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="c3437-104">Dieser Artikel beschreibt, wie Sie bereitstellen, können mit SharePoint Online ohne herkömmlichen Auslastungstests, da Auslastungstests abgeraten wird.</span><span class="sxs-lookup"><span data-stu-id="c3437-104">This article describes how you can deploy to SharePoint Online without traditional load testing, since load-testing is strongly discouraged.</span></span>
  
<span data-ttu-id="c3437-105">Obwohl active Auslastungstests SharePoint Online wird nicht empfohlen, es einige andere Möglichkeiten, den, die Sie Folgendes sicherstellen können, erzeugt eine Website nicht benutzerfreundlich beim Starten der Website.</span><span class="sxs-lookup"><span data-stu-id="c3437-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="c3437-p101">Mit SharePoint Online müssen Sie kapazitätsplanung, wie dies für Sie als Teil des unser Serviceangebot. Mit lokalen Umgebungen Auslastungstests wird horizontal Annahme überprüfen und letztlich suchen die neueste Punkt einer Farm. durch eine es mit Last. Mit SharePoint Online muss anders Dinge. Wird eine Umgebung mit mehreren Mandanten, haben wir schützen Sie alle Mandanten in der gleichen Farm aus, damit es keine Auslastungstests automatisch gedrosselt wird. Dies bedeutet, dass Sie erhalten enttäuschend und potenziell irreführende Ergebnisse, wenn Sie versuchen, laden Testen Ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="c3437-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="c3437-p102">Eines der wichtigsten Vorteile von SharePoint Online über eine lokale Bereitstellung ist der Elastizität der Cloud. Unsere großen Umgebung eingerichtet ist mit Millionen von Benutzern auf täglicher Basis-Dienst so wichtig ist, dass wir Kapazität effektiv behandeln, indem Sie die Farmen, automatisch angepasst wird, wie und, falls erforderlich. In diesem Artikel wird erläutert, wie wir für Kapazitätswachstum und einem festen Maßstab planen Out vorhanden. Der Artikel behandelt auch Ansätze für die Verwendung von, an denen Auslastungstests nicht beteiligt.</span><span class="sxs-lookup"><span data-stu-id="c3437-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="c3437-115">Wie Office 365 prognostiziert laden und erweitert Kapazität</span><span class="sxs-lookup"><span data-stu-id="c3437-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="c3437-116">SharePoint Online Server Capacity Management Arbeit erfolgt über zwei Methoden:</span><span class="sxs-lookup"><span data-stu-id="c3437-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="c3437-117">Kapazität-Planung</span><span class="sxs-lookup"><span data-stu-id="c3437-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="c3437-118">Netzwerklastenausgleich auf einzelnen Serverfarmen</span><span class="sxs-lookup"><span data-stu-id="c3437-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="c3437-p103">Anders als bei der Planung einer lokalen Umgebung für die Kapazität in SharePoint Online-Planung können wir Statistiken sowie grafisch potenzielle Anforderungen in keiner bestimmten Server-Gruppe. Der aggregierte bei Bedarf sieht etwa die Anforderungen in der Zone (wobei für eine Zone ist eine Gruppe von SharePoint-Farmen) Wachstum Zeile in der folgenden Abbildung:</span><span class="sxs-lookup"><span data-stu-id="c3437-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Diagramm der vorhergesagten Kapazität: Prognose](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="c3437-p104">Während das Wachstum in jeder Farm eine unvorhersehbare befindet, ist die aggregierte Summe von Anforderungen in einer Zone vorhersehbar. Durch die Ermittlung der geometrischen Trends in SharePoint Online, können wir für die zukünftige Erweiterung planen.</span><span class="sxs-lookup"><span data-stu-id="c3437-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="c3437-p105">Um effizient Kapazität verwenden und befassen sich mit der unerwartete Zunahme jede Farm haben wir die Automatisierung, Front-End-System verfolgt und bei Bedarf von direkten, skaliert. Die wichtigste Metrik, die wir verwenden, wie ein Signal zum Skalieren von Front-ends ist CPU-Auslastung. Unser Ziel ist es, die CPU-Belastung weniger als 40 % zu halten. Dies ist, um genügend Puffer zu unerwarteten Spitzen kompensieren zu lassen. Load Ansätze 40 % im stabilen Zustand fügen wir front-Ends Farmen hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3437-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Diagramm der vorhergesagten Kapazität: Verwalten von Farmen](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="c3437-130">Zusätzliche Server können schnell zu einer Farm, mit denen, die zuvor durch die Planung Syntax der Zone hinzugefügt wurden hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c3437-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="c3437-131">Wie plane ich für eine Website starten?</span><span class="sxs-lookup"><span data-stu-id="c3437-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="c3437-p106">Sie sollten erwarten, dass die Farm, auf der die neue Website startet, automatisch überwacht werden, sodass neue Front-End-Server hinzugefügt werden, wie oben beschrieben. Aus diesem Grund benötigen nicht wir keine Benachrichtigung für die neue Website starten.</span><span class="sxs-lookup"><span data-stu-id="c3437-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="c3437-134">Weitere bewährten Methoden für eine einzelne Seite auf SharePoint Online ist es unwahrscheinlich, dass eine neue Website zu öffnen, auch 100.000 Benutzer alle in der Farm auswirken.</span><span class="sxs-lookup"><span data-stu-id="c3437-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="c3437-p107">Es gibt einige Strategien zum Planen einer Version einer neuen SharePoint Online-Website. Wie in der folgenden Abbildung gezeigt, ist die Anzahl von Benutzern, die eingeladen werden häufig deutlich höher ist als die, die die Website zu verwenden. Diese Abbildung zeigt eine Strategie zur Verwendung einer Version Rollout. Diese Methode ist nicht nur nützlich, um zu Leistung beim Laden jedoch auch kann identifizieren Möglichkeiten zur Verbesserung der SharePoint-Website, bevor die Mehrzahl der Benutzer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c3437-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Diagramm der eingeladenen und aktiven Benutzer](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="c3437-p108">In der Pilotphase Geschäftsobjekts Feedback von Benutzern zu erhalten, dass die Organisation vertraut und weiß anderweitig werden sollen. Auf diese Weise ist es möglich, wie das System verwendet wird und wie es ausgeführt wird, zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="c3437-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="c3437-p109">Danach beginnt für alle Benutzer in hochrangige Rollout; Einholen von Feedback und die Leistung regelmäßig zu überprüfen. Dies hat den Vorteil langsam Einführung in das System und bei dessen Verbesserung, wenn das System Weitere verwendet wird. Dadurch können auch auf die erhöhte Last zu reagieren, wie die Website für mehr Benutzer eingeführt.</span><span class="sxs-lookup"><span data-stu-id="c3437-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="c3437-p110">Schließlich während Auslastungstests nicht zulässig sind, können Kunden regelmäßige Ping an den Dienst Measure Verfügbarkeit und Latenz einrichten möchten. Identifizieren dieses Grundlinie für ihre Website. Allerdings müssen diese geringe Häufigkeit Drosselung zuvor beschriebenen Probleme vermieden aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="c3437-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

