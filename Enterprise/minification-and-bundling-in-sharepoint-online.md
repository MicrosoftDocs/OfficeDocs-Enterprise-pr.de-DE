---
title: Minimierung und Bündelung in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: In diesem Artikel wird beschrieben, wie Sie bei einer Verkleinerung und Techniken mit Web Essentials bündeln zur Reduzierung der Anzahl der HTTP-Anfragen und zu den Zeitraum zu verkürzen, die zum Laden von Seiten in SharePoint Online benötigt wird.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540707"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="d5287-103">Minimierung und Bündelung in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d5287-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="d5287-104">In diesem Artikel wird beschrieben, wie Sie bei einer Verkleinerung und Techniken mit Web Essentials bündeln zur Reduzierung der Anzahl der HTTP-Anfragen und zu den Zeitraum zu verkürzen, die zum Laden von Seiten in SharePoint Online benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="d5287-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="d5287-p101">Es kann sein, dass Sie beim Anpassen Ihrer Website eine große Anzahl zusätzlicher Dateien zum Server hinzufügen müssen, um die Anpassung zu unterstützen. Durch Hinzufügen von zusätzlichen JavaScript-, CSS- und Bilddateien erhöht sich die Anzahl der HTTP-Anforderungen an den Server, was wiederum die Anzeige einer Webseite verlangsamt. Wenn Sie über mehrere Dateien desselben Typs verfügen, können Sie diese Dateien bündeln bzw. in einem Paket zusammenfassen, um das Herunterladen dieser Dateien zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="d5287-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="d5287-108">Für JavaScript und CSS-Dateien können Sie auch einen Ansatz Verkleinerung, aufgerufen, in dem Sie reduzieren der Gesamtgröße von Dateien durch Entfernen von Leerzeichen und Sonderzeichen, die nicht erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d5287-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="d5287-109">Minimierung und Bündelung von JavaScript- und CSS-Dateien mit Web Essentials</span><span class="sxs-lookup"><span data-stu-id="d5287-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="d5287-110">Sie können eine Drittanbietersoftware verwenden, z. B. Web Essentials, um CSS- und JavaScript-Dateien zu bündeln.</span><span class="sxs-lookup"><span data-stu-id="d5287-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="d5287-p102">Web Essentials ist ein Drittanbieter-, Open Source, Community-basierte Projekt. Die Software ist eine Erweiterung für Visual Studio 2012 und Visual Studio 2013 und wird von Microsoft nicht unterstützt. Informationen zum Herunterladen von Web Essentials finden Sie auf der Website unter [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="d5287-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="d5287-114">Web Essentials bietet zwei Arten der Bündelung an:</span><span class="sxs-lookup"><span data-stu-id="d5287-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="d5287-115">BUNDLE: für CSS- und JavaScript-Dateien</span><span class="sxs-lookup"><span data-stu-id="d5287-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="d5287-116">SPRITE: für Bilder (nur verfügbar in Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="d5287-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="d5287-117">Sie können Web Essentials verwenden, wenn Sie über ein vorhandenes Feature mit Brandingelementen verfügen, auf die innerhalb einer benutzerdefinierten Masterseite verwiesen wird, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d5287-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Screenshot des Markenelements in der benutzerdefinierten Gestaltungsvorlage](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="d5287-119">**Zum Erstellen einer TE000127218 und CSS-Bundle in Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="d5287-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="d5287-120">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die im Paket enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="d5287-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="d5287-p103">Mit der rechten Maustaste der ausgewählten Dateien, und wählen Sie **Web Essentials** \> **JavaScript erstellen Bundle-Datei** aus dem Kontextmenü. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d5287-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Screenshot mit Web Essentials-Menüoptionen](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="d5287-124">Anzeigen der Ergebnisse der Bündelung von JavaScript- und CSS-Dateien</span><span class="sxs-lookup"><span data-stu-id="d5287-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="d5287-125">Bei der Erstellung eines JavaScript- und CSS-Pakets erstellt Web Essentials eine XML-Datei, die als Rezeptdatei bezeichnet wird. Sie gibt die JavaScript- und CSS-Dateien und weitere Konfigurationsinformationen an:</span><span class="sxs-lookup"><span data-stu-id="d5287-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Screenshot von JavaScript- und CSS-Rezeptdatei](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="d5287-p104">Wenn das Kennzeichen für die Minimierung im Bündelungsrezept auf "wahr" gesetzt ist, werden die Dateien größenmäßig reduziert und zu einem Paket zusammengefasst. Auf diese Weise werden neue, verkleinerte Versionen der JavaScript-Dateien erstellt, auf die Sie in Ihrer Masterseite verweisen können.</span><span class="sxs-lookup"><span data-stu-id="d5287-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Screenshot der Verkleinerungskennzeichnung, die auf "true" eingestellt ist](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="d5287-130">Wenn Sie eine Seite von Ihrer Website laden, können Sie die Entwicklertools Ihres Webbrowsers, z. B. Internet Explorer 11, verwenden, um die Anzahl der Anforderungen an den Server anzuzeigen und einzusehen, wie lange jede Datei zum Laden gebraucht hat.</span><span class="sxs-lookup"><span data-stu-id="d5287-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="d5287-131">Die folgende Abbildung zeigt das Ergebnis des Ladens der JavaScript- und CSS-Dateien vor der Minimierung.</span><span class="sxs-lookup"><span data-stu-id="d5287-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Screenshot mit 80 Elementen, die heruntergeladen werden](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="d5287-133">Nach Bündelung der CSS- und JavaScript-Dateien hat sich die Anzahl der Anforderungen auf 74 verringert, und jede Datei brauchte nur geringfügig länger als die ursprünglichen Dateien beim einzelnen Herunterladen:</span><span class="sxs-lookup"><span data-stu-id="d5287-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Screenshot mit 74 Elementen, die heruntergeladen werden](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="d5287-135">Nach der Bündelung hat sich die JavaScript-Paketdatei deutlich von 815 KB auf 365 KB reduziert:</span><span class="sxs-lookup"><span data-stu-id="d5287-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Screenshot mit reduzierter Downloadgröße](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="d5287-137">Bündelung von Bildern durch Erstellen eines Image Sprite</span><span class="sxs-lookup"><span data-stu-id="d5287-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="d5287-p105">Ähnlich wie Sie JavaScript und CSS-Dateien verpacken, können viele kleine Symbole und andere allgemeine Bilder in einem größeren Sprite Blatt kombinieren und dann CSS verwenden, um die einzelnen Bilder anzuzeigen. Nicht auf jedes einzelne Bild herunterladen, Webbrowser des Benutzers das Blatt Sprite einmal downloads und speichert es auf dem lokalen Computer. Dadurch wird die seitenladeleistung durch verringert die Anzahl der Downloads und Roundtrips an den Webserver verbessert.</span><span class="sxs-lookup"><span data-stu-id="d5287-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="d5287-141">**So erstellen Sie ein Image Sprite in Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="d5287-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="d5287-142">Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die im Paket enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="d5287-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="d5287-p106">Mit der rechten Maustaste der ausgewählten Dateien, und wählen Sie **Web Essentials** \> **erstellen Bild Sprite** im Kontextmenü aus. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d5287-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![Screenshot zeigt, wie Sie ein Bild-Sprite erstellen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="d5287-p107">Wählen Sie einen Speicherort für die Sprite-Datei aus. Bei der Sprite-Datei handelt es sich um eine XML-Datei, die die Einstellungen und Dateien im Sprite beschreibt. Die folgenden Abbildungen zeigen ein Beispiel für eine Sprite-PNG-Datei und die zugehörige Sprite-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="d5287-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Screenshot einer Sprite-Datei](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Screenshot der Sprite-XML-Datei](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

