---
title: Diagnose von Leistungsproblemen mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: In diesem Artikel erfahren Sie, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mithilfe von Internet Explorer-Entwicklertools diagnostizieren können.
ms.openlocfilehash: dfc66822a98ce26bfd9fd94d9d58882b8b140831
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067861"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="cb06c-103">Diagnose von Leistungsproblemen mit SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb06c-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="cb06c-104">In diesem Artikel erfahren Sie, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mithilfe von Internet Explorer-Entwicklertools diagnostizieren können.</span><span class="sxs-lookup"><span data-stu-id="cb06c-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="cb06c-105">Es gibt drei verschiedene Möglichkeiten, um festzustellen, ob eine Seite auf einer SharePoint Online-Website ein Leistungsproblem mit den Anpassungen aufweist.</span><span class="sxs-lookup"><span data-stu-id="cb06c-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="cb06c-106">Der F12-Tool Balken-Netzwerkmonitor</span><span class="sxs-lookup"><span data-stu-id="cb06c-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="cb06c-107">Vergleich mit einer nicht angepassten Baseline</span><span class="sxs-lookup"><span data-stu-id="cb06c-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="cb06c-108">Metriken für SharePoint Online-Antwortheader</span><span class="sxs-lookup"><span data-stu-id="cb06c-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="cb06c-109">In diesem Thema wird beschrieben, wie Sie die einzelnen Methoden zur Diagnose von Leistungsproblemen verwenden.</span><span class="sxs-lookup"><span data-stu-id="cb06c-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="cb06c-110">Nachdem Sie die Ursache des Problems herausgefunden haben, können Sie mit den Artikeln zur Verbesserung der Leistung von SharePoint, die Sie finden können, auf http://aka.ms/tuneeine Lösung hinarbeiten.</span><span class="sxs-lookup"><span data-stu-id="cb06c-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="cb06c-111">Verwenden der F12-Symbolleiste zum Diagnostizieren der Leistung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb06c-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="cb06c-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="cb06c-112"></span></span>

<span data-ttu-id="cb06c-113">In diesem Artikel wird Internet Explorer 11 verwendet.</span><span class="sxs-lookup"><span data-stu-id="cb06c-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="cb06c-114">Versionen der F12-Entwicklertools in anderen Browsern weisen ähnliche Features auf, obwohl Sie möglicherweise etwas anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="cb06c-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="cb06c-115">Weitere Informationen zu den F12-Entwicklertools finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="cb06c-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="cb06c-116">Neuigkeiten in den F12-Tools</span><span class="sxs-lookup"><span data-stu-id="cb06c-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="cb06c-117">Verwenden der F12-Entwicklertools</span><span class="sxs-lookup"><span data-stu-id="cb06c-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="cb06c-118">Drücken Sie **F12** , um die Entwicklertools aufzurufen, und klicken Sie dann auf das WLAN-Symbol:</span><span class="sxs-lookup"><span data-stu-id="cb06c-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Screenshot von F12 Developer Tools WiFi-Symbol](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="cb06c-120">Drücken Sie auf der Registerkarte **Netzwerk** die grüne Wiedergabeschaltfläche, um eine Seite zu laden.</span><span class="sxs-lookup"><span data-stu-id="cb06c-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="cb06c-121">Das Tool gibt alle Dateien zurück, die der Browser anfordert, um die von Ihnen gewünschte Seite zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="cb06c-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="cb06c-122">Der folgende Screenshot zeigt eine solche Liste.</span><span class="sxs-lookup"><span data-stu-id="cb06c-122">The following screen shot shows one such list.</span></span> 
  
![Screenshot der Liste der Dateien, die mit einer Seitenanforderung zurückgegeben werden.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="cb06c-124">Sie können auch die Downloadzeiten der Dateien auf der rechten Seite sehen, wie in diesem Screenshot gezeigt.</span><span class="sxs-lookup"><span data-stu-id="cb06c-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagramm mit der Zeit, die zum Laden der angeforderten Seiten aus SharePoint benötigt wird](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="cb06c-126">Dadurch erhalten Sie eine visuelle Darstellung, wie lange die Datei geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="cb06c-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="cb06c-127">Die grüne Liniendarstellung zeigt an, wann die Seite vom Browser gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="cb06c-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="cb06c-128">Auf diese Weise können Sie schnell die verschiedenen Dateien anzeigen, die zu langsamen Seitenlasten auf Ihrer Website führen.</span><span class="sxs-lookup"><span data-stu-id="cb06c-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="cb06c-129">Einrichten einer nicht angepassten Baseline für SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb06c-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="cb06c-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="cb06c-130"></span></span>

<span data-ttu-id="cb06c-131">Die beste Möglichkeit, die Leistung Ihrer Website zu schwächen, besteht darin, eine vollständig out-of-the-Box-Websitesammlung in SharePoint Online einzurichten.</span><span class="sxs-lookup"><span data-stu-id="cb06c-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="cb06c-132">Auf diese Weise können Sie alle verschiedenen Aspekte Ihrer Website mit dem vergleichen, was Sie ohne Anpassung auf der Seite erhalten würden.</span><span class="sxs-lookup"><span data-stu-id="cb06c-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="cb06c-133">Die OneDrive for Business-Startseite ist ein gutes Beispiel für eine separate Websitesammlung, die keine Anpassungen aufweisen kann.</span><span class="sxs-lookup"><span data-stu-id="cb06c-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="cb06c-134">Anzeigen von SharePoint-Antwortheader Informationen</span><span class="sxs-lookup"><span data-stu-id="cb06c-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="cb06c-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="cb06c-135"></span></span>

<span data-ttu-id="cb06c-136">In SharePoint Online und SharePoint Server 2013 können Sie auf die Informationen zugreifen, die im Antwortheader für jede Datei an den Browser zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb06c-136">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="cb06c-137">Die beiden hilfreichsten Werte für die Diagnose von Leistungsproblemen sind SPRequestDuration und X-SharePointHealthScore:</span><span class="sxs-lookup"><span data-stu-id="cb06c-137">The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="cb06c-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="cb06c-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="cb06c-139">Dies ist die Zeitdauer, die die Anforderung für die Verarbeitung des Servers übernommen hat.</span><span class="sxs-lookup"><span data-stu-id="cb06c-139">This is the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="cb06c-140">Dies kann helfen festzustellen, ob die Anforderung sehr schwer und ressourcenintensiv ist.</span><span class="sxs-lookup"><span data-stu-id="cb06c-140">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="cb06c-141">Dies ist die beste Einblicke in die Menge an Arbeit, die der Server für die Bereitstellung der Seite leistet.</span><span class="sxs-lookup"><span data-stu-id="cb06c-141">This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="cb06c-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="cb06c-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="cb06c-143">Dies gibt die Auslastung des Servers oder der CPU an, auf dem Ihre SharePoint-Instanz ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cb06c-143">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs.</span></span> <span data-ttu-id="cb06c-144">Diese Zahl liegt zwischen 0 und 10, wobei 0 angibt, dass der Server inaktiv ist und 10 angibt, dass der Server sehr ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="cb06c-144">This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy.</span></span> <span data-ttu-id="cb06c-145">Ein HealthScore, das konsistent 9 oder 10 ist, kann auf ein ständiges Leistungsproblem mit dem Server hindeuten.</span><span class="sxs-lookup"><span data-stu-id="cb06c-145">A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server.</span></span> <span data-ttu-id="cb06c-146">Eine beliebige andere Zahl weist darauf hin, dass der Server innerhalb des erwarteten Zeitraums betrieben wird.</span><span class="sxs-lookup"><span data-stu-id="cb06c-146">Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="cb06c-147">**So zeigen Sie SharePoint-Antwortheader Informationen an**</span><span class="sxs-lookup"><span data-stu-id="cb06c-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="cb06c-148">Stellen Sie sicher, dass die F12-Tools installiert sind.</span><span class="sxs-lookup"><span data-stu-id="cb06c-148">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="cb06c-149">Weitere Informationen zum herunterladen und Installieren dieser Tools finden Sie unter [What es New in F12 Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="cb06c-149">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="cb06c-150">Drücken Sie in den F12-Tools auf der Registerkarte **Netzwerk** die grüne Wiedergabeschaltfläche, um eine Seite zu laden.</span><span class="sxs-lookup"><span data-stu-id="cb06c-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="cb06c-151">Klicken Sie auf eine der vom Tool zurückgegebenen ASPX-Dateien, und klicken Sie dann auf **Details**.</span><span class="sxs-lookup"><span data-stu-id="cb06c-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Zeigt Details des Antwortheaders an.](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="cb06c-153">Klicken Sie auf **Antwort Kopfzeilen**.</span><span class="sxs-lookup"><span data-stu-id="cb06c-153">Click **Response headers**.</span></span> 
    
    ![Diagramm mit der URL des Antwortheaders](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="cb06c-155">Was verursacht Leistungsprobleme in SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="cb06c-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="cb06c-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="cb06c-156"></span></span>

<span data-ttu-id="cb06c-157">Die Artikel [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) zeigen ein Beispiel für die Verwendung des SPRequestDuration-Werts, um festzustellen, dass die umständliche strukturelle Navigation dazu führte, dass die Verarbeitung der Seite auf dem Server lange dauert.</span><span class="sxs-lookup"><span data-stu-id="cb06c-157">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="cb06c-158">Durch die Verwendung eines Werts für eine Basis Website (ohne Anpassung) kann ermittelt werden, ob eine bestimmte Datei sehr viel Zeit in Anspruch nimmt.</span><span class="sxs-lookup"><span data-stu-id="cb06c-158">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="cb06c-159">Das in den [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) verwendete Beispiel ist die Hauptdatei. aspx.</span><span class="sxs-lookup"><span data-stu-id="cb06c-159">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="cb06c-160">Diese Datei enthält den größten Teil des ASP.NET-Codes, der für das Laden der Seite ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cb06c-160">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="cb06c-161">Je nach verwendeter Websitevorlage kann dies "Start. aspx", "Home. aspx", "default. aspx" oder ein anderer Name sein, wenn Sie die Homepage anpassen.</span><span class="sxs-lookup"><span data-stu-id="cb06c-161">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="cb06c-162">Wenn diese Zahl deutlich höher als die Baseline-Website ist, ist es ein guter Hinweis darauf, dass auf Ihrer Seite etwas komplexes auftritt, das zu Leistungsproblemen führt.</span><span class="sxs-lookup"><span data-stu-id="cb06c-162">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="cb06c-163">Nachdem Sie festgestellt haben, dass ein Problem, das für Ihre Website spezifisch ist, wird empfohlen, um herauszufinden, was die Leistung beeinträchtigt, wenn Sie alle möglichen Ursachen wie Seiten Anpassungen beseitigen und diese dann nacheinander wieder zur Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cb06c-163">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="cb06c-164">Nachdem Sie genügend Anpassungen entfernt haben, die von der Seite ausgeführt werden, können Sie eine nach dem anderen wieder hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cb06c-164">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="cb06c-165">Wenn Sie beispielsweise eine sehr komplexe Navigation haben, versuchen Sie, die Navigation so zu ändern, dass Unterwebsites nicht angezeigt werden, und überprüfen Sie die Entwicklertools, ob dies einen Unterschied macht.</span><span class="sxs-lookup"><span data-stu-id="cb06c-165">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="cb06c-166">Oder wenn Sie über eine Vielzahl von Inhalts-Rollups verfügen, versuchen Sie, Sie von Ihrer Seite zu entfernen, und sehen Sie nach, ob dies etwas verbessert.</span><span class="sxs-lookup"><span data-stu-id="cb06c-166">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="cb06c-167">Wenn Sie alle möglichen Ursachen beseitigen und Sie wieder einzeln hinzufügen, können Sie leicht erkennen, welche Funktionen das größte Problem darstellen, und dann an einer Lösung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="cb06c-167">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

