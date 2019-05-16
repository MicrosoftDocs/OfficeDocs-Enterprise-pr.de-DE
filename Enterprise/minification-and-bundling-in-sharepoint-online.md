---
title: Minimierung und Bündelung in SharePoint Online
ms.author: krowley
author: kccross
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
description: In diesem Artikel wird beschrieben, wie Sie Verkleinerungs verwenden und Techniken mit Web Essentials bündeln, um die Anzahl von HTTP-Anforderungen zu reduzieren und die Zeit zu verringern, die zum Laden von Seiten in SharePoint Online benötigt wird.
ms.openlocfilehash: d73bc6cc86ea1ea4ecba5395f22a20befdc64b13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070261"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="ed560-103">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ed560-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="ed560-104">In diesem Artikel wird beschrieben, wie Sie Verkleinerungs verwenden und Techniken mit Web Essentials bündeln, um die Anzahl von HTTP-Anforderungen zu reduzieren und die Zeit zu verringern, die zum Laden von Seiten in SharePoint Online benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="ed560-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="ed560-105">Wenn Sie Ihre Website anpassen, können Sie dem Server eine Vielzahl zusätzlicher Dateien hinzufügen, um die Anpassung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ed560-105">When you customize your website you can end up adding a large number of extra files to the server to support the customization.</span></span> <span data-ttu-id="ed560-106">Durch Hinzufügen von zusätzlichem JavaScript, CSS und Bildern wird die Anzahl der HTTP-Anforderungen an den Server erhöht, was wiederum die Zeitdauer erhöht, die zum Anzeigen einer Webseite benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="ed560-106">Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page.</span></span> <span data-ttu-id="ed560-107">Wenn Sie über mehrere Dateien vom gleichen Typ verfügen, können Sie diese Dateien bündeln, um das Herunterladen dieser Dateien zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="ed560-107">If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="ed560-108">Bei JavaScript-und CSS-Dateien können Sie auch einen Ansatz namens Verkleinerungs verwenden, in dem Sie die Gesamtgröße der Dateien verringern, indem Sie Leerraum und andere Zeichen entfernen, die nicht erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="ed560-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="ed560-109">Verkleinerungs und bündeln von JavaScript-und CSS-Dateien mit Web Essentials</span><span class="sxs-lookup"><span data-stu-id="ed560-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="ed560-110">Sie können Software von Drittanbietern wie Web Essentials verwenden, um CSS-und JavaScript-Dateien zu bündeln.</span><span class="sxs-lookup"><span data-stu-id="ed560-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="ed560-111">Web Essentials ist ein Open Source-Community-basiertes Projekt eines Drittanbieters.</span><span class="sxs-lookup"><span data-stu-id="ed560-111">Web Essentials is a third-party, open-source, community-based project.</span></span> <span data-ttu-id="ed560-112">Die Software ist eine Erweiterung von Visual Studio 2012 und Visual Studio 2013 und wird von Microsoft nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ed560-112">The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft.</span></span> <span data-ttu-id="ed560-113">Besuchen Sie die Website unter [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="ed560-113">To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="ed560-114">Web Essentials bietet zwei Formen der Bündelung:</span><span class="sxs-lookup"><span data-stu-id="ed560-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="ed560-115">. Bundle: für CSS-und JavaScript-Dateien</span><span class="sxs-lookup"><span data-stu-id="ed560-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="ed560-116">. Sprite: für Bilder (nur in Visual Studio 2013 verfügbar)</span><span class="sxs-lookup"><span data-stu-id="ed560-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="ed560-117">Sie können Web Essentials verwenden, wenn Sie über ein vorhandenes Feature mit einigen Branding-Elementen verfügen, auf die innerhalb einer benutzerdefinierten Gestaltungsvorlage verwiesen wird, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="ed560-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Screenshot des Marke-Elements in einer benutzerdefinierten Gestaltungsvorlage](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="ed560-119">**So erstellen Sie ein TE000127218-und CSS-Bundle in Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="ed560-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="ed560-120">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle aufnehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="ed560-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="ed560-121">Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü die Option **Web Essentials** \> **Create JavaScript Bundle File** aus.</span><span class="sxs-lookup"><span data-stu-id="ed560-121">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu.</span></span> <span data-ttu-id="ed560-122">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ed560-122">For example:</span></span> 
    
    ![Screenshot mit Web Essentials-Menü Optionen](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="ed560-124">Anzeigen der Ergebnisse der Bündelung von JavaScript-und CSS-Dateien</span><span class="sxs-lookup"><span data-stu-id="ed560-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="ed560-125">Wenn Sie ein JavaScript-und CSS-Bundle erstellen, erstellt Web Essentials eine XML-Datei mit dem Namen eine Rezept Datei, die die JavaScript-und CSS-Dateien sowie einige andere Konfigurationsinformationen identifiziert:</span><span class="sxs-lookup"><span data-stu-id="ed560-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Screenshot der JavaScript-und CSS-Rezept Datei](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="ed560-127">Wenn das minimieren-Flag in der Bundle-Rezeptur auf true festgelegt ist, werden außerdem die Dateien sowohl verkleinert als auch gebündelt.</span><span class="sxs-lookup"><span data-stu-id="ed560-127">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together.</span></span> <span data-ttu-id="ed560-128">Dies hat zur Folge, dass neue, minimierte Versionen der JavaScript-Dateien erstellt wurden, auf die Sie in ihrer Gestaltungsvorlage verweisen können.</span><span class="sxs-lookup"><span data-stu-id="ed560-128">This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Screenshot des minimieren-Flags, das auf true festgelegt ist](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="ed560-130">Wenn Sie eine Seite von Ihrer Website laden, können Sie die Entwicklertools Ihres Webbrowsers, wie etwa Internet Explorer 11, verwenden, um die Anzahl der an den Server gesendeten Anforderungen und die Dauer der Ladevorgang für jede Datei anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ed560-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="ed560-131">Die folgende Abbildung ist das Ergebnis des Ladens der JavaScript-und CSS-Dateien vor Verkleinerungs.</span><span class="sxs-lookup"><span data-stu-id="ed560-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Screenshot mit 80 heruntergeladenen Elementen](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="ed560-133">Nachdem die CSS-und JavaScript-Dateien zusammengefasst wurden, wurde die Anzahl der Anforderungen auf 74 und jede Datei nur geringfügig länger als die Originaldateien, die einzeln heruntergeladen wurden:</span><span class="sxs-lookup"><span data-stu-id="ed560-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Screenshot mit 74 heruntergeladenen Elementen](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="ed560-135">Nach der Bündelung wird die JavaScript-bundledatei erheblich von 815KB zu 365KB reduziert:</span><span class="sxs-lookup"><span data-stu-id="ed560-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Screenshot mit reduzierter Downloadgröße](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="ed560-137">Bündeln von Bildern durch Erstellen eines Image-Sprites</span><span class="sxs-lookup"><span data-stu-id="ed560-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="ed560-138">Ähnlich wie Sie JavaScript-und CSS-Dateien bündeln, können Sie viele kleine Symbole und andere gängige Bilder zu einem größeren Sprite-Blatt zusammenfassen und dann mit CSS die einzelnen Bilder anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ed560-138">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images.</span></span> <span data-ttu-id="ed560-139">Anstatt jedes einzelne Bild herunterzuladen, downloadet der Webbrowser des Benutzers das Sprite-Blatt einmal und speichert es dann auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="ed560-139">Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer.</span></span> <span data-ttu-id="ed560-140">Dies verbessert die Seiten Ladeleistung, indem die Anzahl der Downloads und Roundtrips zum Webserver reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="ed560-140">This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="ed560-141">**So erstellen Sie ein Image-Sprite in Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="ed560-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="ed560-142">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle aufnehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="ed560-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="ed560-143">Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü **Web Essentials** \> **Create Image Sprite** aus.</span><span class="sxs-lookup"><span data-stu-id="ed560-143">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu.</span></span> <span data-ttu-id="ed560-144">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ed560-144">For example:</span></span> 
    
    ![Screenshot, der zeigt, wie Sie ein Image-Sprite erstellen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="ed560-146">Wählen Sie einen Speicherort für die Sprite-Datei aus.</span><span class="sxs-lookup"><span data-stu-id="ed560-146">Choose a location to save the sprite file.</span></span> <span data-ttu-id="ed560-147">Die Sprite-Datei ist eine XML-Datei, in der die Einstellungen und Dateien im Sprite beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="ed560-147">The .sprite file is an XML file that describes the settings and files in the sprite.</span></span> <span data-ttu-id="ed560-148">Die folgenden Abbildungen zeigen ein Beispiel für eine Sprite-PNG-Datei und die entsprechende Sprite-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="ed560-148">The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Screenshot einer Sprite-Datei](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Screenshot der Sprite-XML-Datei](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

