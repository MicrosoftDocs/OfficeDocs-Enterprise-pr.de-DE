---
title: Diagnose von Leistungsproblemen mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: In diesem Artikel wird gezeigt, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mit Internet Explorer-Entwicklertools diagnostizieren können.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540876"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="d94c1-103">Diagnose von Leistungsproblemen mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d94c1-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="d94c1-104">In diesem Artikel wird gezeigt, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mit Internet Explorer-Entwicklertools diagnostizieren können.</span><span class="sxs-lookup"><span data-stu-id="d94c1-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="d94c1-105">Es gibt drei Möglichkeiten, wie Sie erkennen, dass eine Seite auf einer SharePoint Online-Website ein Leistungsproblem bei Anpassungen hat.</span><span class="sxs-lookup"><span data-stu-id="d94c1-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="d94c1-106">Netzwerkmonitor in der F12-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="d94c1-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="d94c1-107">Vergleich mit einer nicht angepassten Baseline</span><span class="sxs-lookup"><span data-stu-id="d94c1-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="d94c1-108">Metriken eines SharePoint Online-Antwortheaders</span><span class="sxs-lookup"><span data-stu-id="d94c1-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="d94c1-p101">In diesem Thema wird beschrieben, wie diese Methoden zur diagnose von Leistungsproblemen verwenden. Nachdem Sie sich die Ursache des Problems berechnet haben, können Sie arbeiten an einer Lösung mit den Artikeln zum Verbessern der Leistung von SharePoint, die auf http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="d94c1-111">Verwenden Sie die F12-Symbolleiste, um die Leistung in SharePoint Online zu diagnostizieren.</span><span class="sxs-lookup"><span data-stu-id="d94c1-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="d94c1-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d94c1-112"></span></span>

<span data-ttu-id="d94c1-p102">In diesem Artikel wird Internet Explorer 11 verwendet. Die Versionen der F12-Entwicklertools in anderen Browsern haben ähnliche Funktionen, auch wenn sie unter Umständen etwas anders aussehen. Informationen zu den F12-Entwicklertools finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="d94c1-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="d94c1-116">Was ist neu in F12-Tools</span><span class="sxs-lookup"><span data-stu-id="d94c1-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="d94c1-117">Verwenden die F12-Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="d94c1-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="d94c1-118">Zum Aufrufen der Entwicklertools drücken Sie **F12** und klicken dann auf das WiFi-Symbol: 
</span><span class="sxs-lookup"><span data-stu-id="d94c1-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Screenshot von F12-Entwicklertools (WLAN-Symbol)](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="d94c1-p103">Klicken Sie auf der Registerkarte **Netzwerk** auf die grüne Wiedergabeschaltfläche, um eine Seite zu laden. Das Tool gibt alle Dateien, die der Browser anfordert, zurück, um die angeforderte Seite zu erhalten. Der folgende Screenshot zeigt eine solche Liste.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Screenshot der Liste der Dateien, die mit einer Seitenanforderung zurückgegeben wurden.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="d94c1-124">Auf der rechten Seite werden außerdem die Downloadzeiten der Dateien angezeigt, wie in diesem Screenshot dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d94c1-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagramm, das die Zeit zeigt, die für das Laden der erforderlichen Seiten von SharePoint benötigt wird](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="d94c1-p104">So wird visuell dargestellt, wie lange die Datei zum Laden brauchte. Die grüne Linie gibt an, wann die Seite vom Browser gerendert werden kann. So erhalten Sie einen schnellen Überblick über die verschiedenen Dateien, die ggf. das Laden von Seiten auf Ihrer Website verlangsamen.
</span><span class="sxs-lookup"><span data-stu-id="d94c1-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="d94c1-129">Einrichten von nicht angepassten Grundlinie für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d94c1-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="d94c1-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d94c1-130"></span></span>

<span data-ttu-id="d94c1-p105">Die beste Möglichkeit zum Ermitteln Ihrer Website Leistung Schwachpunkte ist eine vollständig Out-of-the-Box-Websitesammlung in SharePoint Online einrichten. Auf diese Weise können Sie die verschiedenen Aspekte der Website mit mit keine Anpassung auf der Seite erhalten würden vergleichen. Die OneDrive for Business-Homepage ist ein gutes Beispiel einer separaten Websitesammlung, die wahrscheinlich auf Anpassungen ist.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="d94c1-134">Anzeigen der Informationen im SharePoint-Antwortheader</span><span class="sxs-lookup"><span data-stu-id="d94c1-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="d94c1-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d94c1-135"></span></span>

<span data-ttu-id="d94c1-p106">In SharePoint Online und SharePoint Server 2013 können Sie die an den Browser zurückgesendeten Informationen im Antwortheader für jede Datei anzeigen. Die zwei hilfreichsten Werte für die Diagnose von Leistungsproblemen sind "SPRequestDuration" und "X-SharePointHealthScore":</span><span class="sxs-lookup"><span data-stu-id="d94c1-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="d94c1-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="d94c1-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="d94c1-p107">Dies ist die Zeitspanne, die die Verarbeitung der Anforderung auf dem Server dauerte. So können Sie bestimmen, ob die Anforderung sehr umfangreich und ressourcenintensiv ist. Dadurch erhalten Sie optimale Einblicke dahingehend, wie viel Arbeit der Server leistet, um die Seite zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="d94c1-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="d94c1-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="d94c1-p108">Dies gibt an, die Auslastung des Servers oder der CPU, auf dem SharePoint-Instanz ausgeführt wird. Diese Zahl zwischen 0 und 10, wobei 0 gibt an, der Server befindet sich im Leerlauf und 10 gibt den Server, ist ausgelastet. Eine HealthScore, die konsistent 9 oder 10 ist möglicherweise eine laufende Leistungsproblem mit dem Server. Eine beliebige andere Zahl gibt an, dass es sich bei diesem Server innerhalb des erwarteten Bereichs arbeitet.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="d94c1-147">**So zeigen Sie die Informationen des SharePoint-Antwortheaders an**</span><span class="sxs-lookup"><span data-stu-id="d94c1-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="d94c1-p109">Stellen Sie sicher, dass Sie die F12-Tools installiert haben. Weitere Informationen zum Herunterladen und Installation dieser Tools finden Sie unter [Was ist neu in F12-Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="d94c1-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="d94c1-150">Klicken Sie in den F12-Tools auf der Registerkarte **Netzwerk** auf die grüne Wiedergabeschaltfläche, um eine Seite zu laden.</span><span class="sxs-lookup"><span data-stu-id="d94c1-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="d94c1-151">Klicken Sie auf eine der vom Tool zurückgegebenen ASPX-Dateien, und klicken Sie dann auf **DETAILS**.</span><span class="sxs-lookup"><span data-stu-id="d94c1-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Zeigt Details des Antwortheaders](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="d94c1-153">Klicken Sie auf **Antwortheader**.</span><span class="sxs-lookup"><span data-stu-id="d94c1-153">Click **Response headers**.</span></span> 
    
    ![Diagramm mit der URL des Antwortheaders](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="d94c1-155">Was verursacht Leistungsprobleme in SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="d94c1-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="d94c1-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d94c1-156"></span></span>

<span data-ttu-id="d94c1-p110">Im Artikel [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) zeigt ein Beispiel der Verwendung des SPRequestDuration Werts zum feststellen, dass die komplizierte strukturelle Navigation auf die Seite, um eine lange dauern auf dem Server verarbeitet verursacht wurde. Über den Wert für eine Website Baseline (ohne Anpassung), ist es möglich, festzustellen, ob eine bestimmte Datei geladen lange ist. Das Beispiel aus der [Optionen für die Websitenavigation für SharePoint Online](navigation-options-for-sharepoint-online.md) ist der wichtigste ASPX-Datei. Diese Datei enthält die meisten der ASP.NET-Code, der für Ihre Laden der Seite ausgeführt wird. Abhängig von der Websitevorlage, die Sie verwenden, kann dies start.aspx, home.aspx, default.aspx oder einen anderen Namen handeln, wenn Sie die Homepage anpassen. Wenn diese Nummer erheblich höher ist als der Baseline-Website ist, ist es ein guter Hinweis darauf, den es etwas komplex sein und sollte ist auf der Seite, die Leistungsprobleme verursacht.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="d94c1-p111">Nachdem Sie ein spezielles Problem mit Ihrer Website identifiziert haben, sollten Sie herausfinden, wodurch die Leistungseinbußen verursacht werden. So können Sie alle möglichen Ursachen beseitigen, z. B. Seitenanpassungen, und die einzelnen Anpassungen dann wieder nacheinander zur Website hinzufügen. Nachdem Sie so viele Anpassungen entfernt haben, dass die Seite wieder gut funktioniert, können Sie bestimmte Anpassungen wieder einzeln hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d94c1-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="d94c1-p112">Wenn Sie beispielsweise über eine sehr komplexe Navigation verfügen, versuchen Sie, die Navigation so zu ändern, dass keine Unterwebsites angezeigt werden. Überprüfen Sie dann in den Entwicklertools, ob dies einen Unterschied macht. Oder wenn eine große Menge an Inhaltrollups vorhanden ist, entfernen Sie sie von Ihrer Seite, und schauen Sie, ob sich die Leistung dadurch verbessert. Wenn Sie alle der möglichen Ursachen beseitigen und die Elemente einzeln wieder hinzufügen, können Sie leicht herausfinden, welche Merkmale am problematischsten sind, und eine Lösung finden. 
</span><span class="sxs-lookup"><span data-stu-id="d94c1-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

