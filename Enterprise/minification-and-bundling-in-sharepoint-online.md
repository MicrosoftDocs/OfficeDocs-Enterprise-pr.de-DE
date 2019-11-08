---
title: Minimierung und Bündelung in SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: In diesem Artikel wird beschrieben, wie Sie Minimierungs-und Kopplungstechniken mit WebEssentials verwenden, um die Anzahl der HTTP-Anforderungen zu reduzieren und die Zeit zu reduzieren, die zum Laden von Seiten in SharePoint Online benötigt wird.
ms.openlocfilehash: 3303ea49a1308e4ad7b3139547c20b4351fc84b5
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031310"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="50e27-103">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="50e27-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="50e27-104">In diesem Artikel wird beschrieben, wie Sie Minimierungs-und Kopplungstechniken mit WebEssentials verwenden, um die Anzahl der HTTP-Anforderungen zu reduzieren und die Zeit zu reduzieren, die zum Laden von Seiten in SharePoint Online benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="50e27-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="50e27-105">Wenn Sie Ihre Website anpassen, können Sie am Ende eine große Anzahl zusätzlicher Dateien auf dem Server hinzufügen, um die Anpassung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="50e27-105">When you customize your website you can end up adding a large number of extra files to the server to support the customization.</span></span> <span data-ttu-id="50e27-106">Durch Hinzufügen von zusätzlichen JavaScript-, CSS-und Bilddateien wird die Anzahl der HTTP-Anforderungen an den Server erhöht, was wiederum die Zeit für die Anzeige einer Webseite erhöht.</span><span class="sxs-lookup"><span data-stu-id="50e27-106">Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page.</span></span> <span data-ttu-id="50e27-107">Wenn Sie mehrere Dateien desselben Typs haben, können Sie diese Dateien bündeln, damit diese Dateien schneller heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="50e27-107">If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="50e27-108">Bei JavaScript-und CSS-Dateien können Sie auch einen Ansatz namens "Minimierungs" verwenden, bei dem Sie die Gesamtgröße von Dateien verringern, indem Sie Leerzeichen und andere nicht benötigte Zeichen entfernen.</span><span class="sxs-lookup"><span data-stu-id="50e27-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="50e27-109">Minimierungs und Bündelung von JavaScript-und CSS-Dateien mit WebEssentials</span><span class="sxs-lookup"><span data-stu-id="50e27-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="50e27-110">Sie können Drittanbietersoftware wie WebEssentials verwenden, um CSS-und JavaScript-Dateien zu bündeln.</span><span class="sxs-lookup"><span data-stu-id="50e27-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="50e27-111">WebEssentials ist ein Open-Source-Projekt von Drittanbietern, das auf communitybasis basiert.</span><span class="sxs-lookup"><span data-stu-id="50e27-111">Web Essentials is a third-party, open-source, community-based project.</span></span> <span data-ttu-id="50e27-112">Die Software ist eine Erweiterung für Visual Studio 2012 und Visual Studio 2013 und wird von Microsoft nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="50e27-112">The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft.</span></span> <span data-ttu-id="50e27-113">Um Web Essentials herunterzuladen, besuchen Sie die [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)Website unter.</span><span class="sxs-lookup"><span data-stu-id="50e27-113">To download Web Essentials, visit the website at [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="50e27-114">WebEssentials bietet zwei Formen der Bündelung:</span><span class="sxs-lookup"><span data-stu-id="50e27-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="50e27-115">. Bundle: für CSS-und JavaScript-Dateien</span><span class="sxs-lookup"><span data-stu-id="50e27-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="50e27-116">. Sprite: für Bilder (nur in Visual Studio 2013 verfügbar)</span><span class="sxs-lookup"><span data-stu-id="50e27-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="50e27-117">Sie können WebEssentials verwenden, wenn Sie ein vorhandenes Feature mit einigen Branding-Elementen haben, auf die in einer benutzerdefinierten Gestaltungsvorlage verwiesen wird, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="50e27-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Screenshot des Marken Elements in der benutzerdefinierten Gestaltungsvorlage](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="50e27-119">**So erstellen Sie ein TE000127218-und CSS-Bundle in WebEssentials**</span><span class="sxs-lookup"><span data-stu-id="50e27-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="50e27-120">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="50e27-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="50e27-121">Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü die Option **WebEssentials** \> **Create JavaScript Bundle File** aus.</span><span class="sxs-lookup"><span data-stu-id="50e27-121">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu.</span></span> <span data-ttu-id="50e27-122">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="50e27-122">For example:</span></span> 
    
    ![Screenshot mit WebEssentials-Menü Optionen](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="50e27-124">Anzeigen der Ergebnisse der Bündelung von JavaScript-und CSS-Dateien</span><span class="sxs-lookup"><span data-stu-id="50e27-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="50e27-125">Wenn Sie ein JavaScript-und CSS-Bundle erstellen, erstellt WebEssentials eine XML-Datei namens "Rezept Datei", in der die JavaScript-und CSS-Dateien sowie einige andere Konfigurationsinformationen identifiziert werden:</span><span class="sxs-lookup"><span data-stu-id="50e27-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Screenshot der JavaScript-und CSS-Rezept Datei](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="50e27-127">Wenn das minimieren-Flag in der Kopplungs Rezeptur auf true festgelegt ist, werden die Dateien zudem sowohl in der Größe als auch in der zusammengefassten Form reduziert.</span><span class="sxs-lookup"><span data-stu-id="50e27-127">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together.</span></span> <span data-ttu-id="50e27-128">Dies bedeutet, dass neue, minimierte Versionen der JavaScript-Dateien erstellt wurden, auf die Sie in ihrer Gestaltungsvorlage verweisen können.</span><span class="sxs-lookup"><span data-stu-id="50e27-128">This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Screenshot des minimieren-Flags auf true festgelegt](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="50e27-130">Wenn Sie eine Seite von Ihrer Website laden, können Sie die Entwicklertools aus Ihrem Webbrowser wie Internet Explorer 11 verwenden, um zu sehen, wie viele Anforderungen an den Server gesendet wurden und wie lange die einzelnen Dateien zum Laden benötigt wurden.</span><span class="sxs-lookup"><span data-stu-id="50e27-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="50e27-131">Die folgende Abbildung ist das Ergebnis des Ladens der JavaScript-und CSS-Dateien vor Minimierungs.</span><span class="sxs-lookup"><span data-stu-id="50e27-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Screenshot mit 80 Elementen, die heruntergeladen werden](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="50e27-133">Nachdem die CSS-und JavaScript-Dateien zusammen gebündelt wurden, wurde die Anzahl der Anforderungen auf 74 und jede Datei dauerte nur geringfügig länger als die ursprünglichen Dateien einzeln heruntergeladen werden:</span><span class="sxs-lookup"><span data-stu-id="50e27-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Screenshot mit 74 Elementen, die heruntergeladen werden](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="50e27-135">Nach dem bündeln wird die JavaScript-Bundle-Datei erheblich von 815KB auf 365KB reduziert:</span><span class="sxs-lookup"><span data-stu-id="50e27-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Screenshot mit reduzierter Downloadgröße](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="50e27-137">Bilder bündeln, indem Sie ein Bild Sprite erstellen</span><span class="sxs-lookup"><span data-stu-id="50e27-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="50e27-138">Ähnlich wie Sie JavaScript-und CSS-Dateien bündeln, können Sie viele kleine Symbole und andere allgemeine Bilder in ein größeres Sprite-Blatt kombinieren und dann mit CSS die einzelnen Bilder aufdecken.</span><span class="sxs-lookup"><span data-stu-id="50e27-138">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images.</span></span> <span data-ttu-id="50e27-139">Anstatt jedes einzelne Bild herunterzuladen, downloadet der Webbrowser des Benutzers das Sprite-Blatt einmal und speichert es dann auf dem lokalen Computer zwischen.</span><span class="sxs-lookup"><span data-stu-id="50e27-139">Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer.</span></span> <span data-ttu-id="50e27-140">Dadurch wird die Seiten Ladeleistung verbessert, indem die Anzahl der Downloads und Roundtrips auf dem Webserver reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="50e27-140">This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="50e27-141">**So erstellen Sie ein Image-Sprite in WebEssentials**</span><span class="sxs-lookup"><span data-stu-id="50e27-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="50e27-142">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="50e27-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="50e27-143">Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü die Option **WebEssentials** \> **Create Image Sprite** aus.</span><span class="sxs-lookup"><span data-stu-id="50e27-143">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu.</span></span> <span data-ttu-id="50e27-144">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="50e27-144">For example:</span></span> 
    
    ![Screenshot, der zeigt, wie ein Bild Sprite erstellt wird](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="50e27-146">Wählen Sie einen Speicherort aus, um die Sprite-Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="50e27-146">Choose a location to save the sprite file.</span></span> <span data-ttu-id="50e27-147">Die Sprite-Datei ist eine XML-Datei, in der die Einstellungen und Dateien im Sprite beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="50e27-147">The .sprite file is an XML file that describes the settings and files in the sprite.</span></span> <span data-ttu-id="50e27-148">Die folgenden Abbildungen zeigen ein Beispiel für eine Sprite-PNG-Datei und die zugehörige Sprite-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="50e27-148">The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Screenshot einer Sprite-Datei](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Screenshot der Sprite-XML-Datei](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

