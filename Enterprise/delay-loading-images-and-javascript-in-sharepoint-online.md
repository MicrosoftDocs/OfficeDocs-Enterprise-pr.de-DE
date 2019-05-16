---
title: Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: In diesem Artikel wird beschrieben, wie Sie die Ladezeit für SharePoint Online-Seiten reduzieren können, indem Sie JavaScript verwenden, um das Laden von Bildern zu verzögern, und außerdem darauf warten, nicht erforderliches JavaScript zu laden, bis die Seite geladen wurde.
ms.openlocfilehash: 6b2e91ca4b8642ac7129e353f2527db60a32d75b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067981"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="42219-103">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="42219-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="42219-104">In diesem Artikel wird beschrieben, wie Sie die Ladezeit für SharePoint Online-Seiten reduzieren können, indem Sie JavaScript verwenden, um das Laden von Bildern zu verzögern, und außerdem darauf warten, nicht erforderliches JavaScript zu laden, bis die Seite geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="42219-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="42219-105">Bilder können sich negativ auf die Seiten ladegeschwindigkeiten bei SharePoint Online auswirken.</span><span class="sxs-lookup"><span data-stu-id="42219-105">Images can negatively affect page load speeds on SharePoint Online.</span></span> <span data-ttu-id="42219-106">Standardmäßig holen die meisten modernen Internet Browser Bilder beim Laden einer HTML-Seite vor.</span><span class="sxs-lookup"><span data-stu-id="42219-106">By default, most modern Internet browsers pre-fetch images when loading an HTML page.</span></span> <span data-ttu-id="42219-107">Dies kann dazu führen, dass die Seite unnötig langsam geladen wird, wenn die Bilder auf dem Bildschirm nicht sichtbar sind, bis der Benutzer einen Bildlauf nach unten durchgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="42219-107">This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down.</span></span> <span data-ttu-id="42219-108">Die Bilder können verhindern, dass der Browser den sichtbaren Teil der Seite lädt.</span><span class="sxs-lookup"><span data-stu-id="42219-108">The images can block the browser from loading the visible part of the page.</span></span> <span data-ttu-id="42219-109">Um dieses Problem zu umgehen, können Sie JavaScript verwenden, um das Laden der Bilder zuerst zu überspringen.</span><span class="sxs-lookup"><span data-stu-id="42219-109">To work around this problem, you can use JavaScript to skip loading the images first.</span></span> <span data-ttu-id="42219-110">Außerdem kann das Laden nicht erforderlicher JavaScript-Dateien die Ladezeiten auf Ihren SharePoint-Seiten verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="42219-110">Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too.</span></span> <span data-ttu-id="42219-111">In diesem Thema werden einige Methoden beschrieben, mit denen Sie Seitenladezeiten mit JavaScript in SharePoint Online verbessern können.</span><span class="sxs-lookup"><span data-stu-id="42219-111">This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="42219-112">Verbessern der Seitenladezeiten durch verzögertes Laden von Bildern in SharePoint Online-Seiten mithilfe von JavaScript</span><span class="sxs-lookup"><span data-stu-id="42219-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="42219-113">Sie können JavaScript verwenden, um zu verhindern, dass ein Webbrowser Bilder vorab abruft.</span><span class="sxs-lookup"><span data-stu-id="42219-113">You can use JavaScript to prevent a web browser from pre-fetching images.</span></span> <span data-ttu-id="42219-114">Dadurch wird das Gesamtdokument Rendering beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="42219-114">This speeds up overall document rendering.</span></span> <span data-ttu-id="42219-115">Zu diesem Zweck entfernen Sie den Wert des src-Attributs aus dem \<IMG\> -Tag und ersetzen ihn durch den Pfad zu einer Datei in einem Data-Attribut wie: Data-src. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="42219-115">To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="42219-116">Bei Verwendung dieser Methode werden die Bilder vom Browser nicht sofort heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="42219-116">By using this method, the browser doesn't download the images immediately.</span></span> <span data-ttu-id="42219-117">Wenn sich das Bild bereits im Ansichtsfenster befindet, weist JavaScript den Browser an, die URL aus dem Data-Attribut abzurufen und als Wert für das src-Attribut einzufügen.</span><span class="sxs-lookup"><span data-stu-id="42219-117">If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute.</span></span> <span data-ttu-id="42219-118">Das Bild wird nur geladen, wenn der Benutzer einen Bildlauf durchführt und es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="42219-118">The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="42219-119">Um dies zu erreichen, müssen Sie JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="42219-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="42219-120">Definieren Sie in einer Textdatei die **isElementInViewport ()** -Funktion, um zu überprüfen, ob sich ein Element in dem Teil des Browsers befindet, der für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="42219-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

<span data-ttu-id="42219-121">Als nächstes verwenden Sie **isElementInViewport ()** in der **loadItemsInView ()** -Funktion.</span><span class="sxs-lookup"><span data-stu-id="42219-121">Next, use **isElementInViewport()** in the **loadItemsInView()** function.</span></span> <span data-ttu-id="42219-122">Die **loadItemsInView ()** -Funktion lädt alle Bilder mit einem Wert für das Data-src-Attribut, wenn Sie sich im Browser Teil befinden, der für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="42219-122">The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user.</span></span> <span data-ttu-id="42219-123">Fügen Sie die folgende Funktion zur Textdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="42219-123">Add the following function to the text file:</span></span> 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="42219-124">Rufen Sie schließlich **loadItemsInView ()** innerhalb von **Window. OnScroll ()** auf, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="42219-124">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example.</span></span> <span data-ttu-id="42219-125">Dadurch wird sichergestellt, dass alle im Viewport enthaltenen Bilder geladen werden, wenn der Benutzer Sie benötigt, jedoch nicht zuvor.</span><span class="sxs-lookup"><span data-stu-id="42219-125">This ensures that any images that are in the viewport are loaded as the user needs them, but not before.</span></span> <span data-ttu-id="42219-126">Fügen Sie Folgendes zur Textdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="42219-126">Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="42219-127">Für SharePoint Online müssen Sie die folgende Funktion an das Scroll-Ereignis im #S4-Workspace \<div\> -Tag anfügen.</span><span class="sxs-lookup"><span data-stu-id="42219-127">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag.</span></span> <span data-ttu-id="42219-128">Der Grund dafür ist, dass die Window-Ereignisse überschrieben werden, um sicherzustellen, dass das Menüband am oberen Rand der Seite befestigt bleibt.</span><span class="sxs-lookup"><span data-stu-id="42219-128">This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="42219-129">Speichern Sie die Textdatei als JavaScript-Datei mit der Erweiterung. js, beispielsweise "delayLoadImages. js".</span><span class="sxs-lookup"><span data-stu-id="42219-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="42219-130">Nachdem Sie delayLoadImages. js geschrieben haben, können Sie den Inhalt der Datei einer Gestaltungsvorlage in SharePoint Online hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="42219-130">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online.</span></span> <span data-ttu-id="42219-131">Hierzu fügen Sie der Kopfzeile auf der Gestaltungsvorlage einen Skript Link hinzu.</span><span class="sxs-lookup"><span data-stu-id="42219-131">You do this by adding a script link to the header in the master page.</span></span> <span data-ttu-id="42219-132">Sobald Sie sich in einer Gestaltungsvorlage befindet, wird das JavaScript auf alle Seiten Ihrer SharePoint Online-Website angewendet, die dieses Gestaltungsvorlagen Layout verwenden.</span><span class="sxs-lookup"><span data-stu-id="42219-132">Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout.</span></span> <span data-ttu-id="42219-133">Wenn Sie dies nur auf einer Seite Ihrer Website verwenden möchten, verwenden Sie alternativ das Skript-Editor-Webpart, um das JavaScript in die Seite einzubetten.</span><span class="sxs-lookup"><span data-stu-id="42219-133">Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page.</span></span> <span data-ttu-id="42219-134">Weitere Informationen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="42219-134">See these topics for more information:</span></span>
  
- [<span data-ttu-id="42219-135">Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="42219-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="42219-136">Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="42219-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="42219-137">**Beispiel: verweisen auf die JavaScript-Datei delayLoadImages. js von einer Gestaltungsvorlage in SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="42219-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="42219-138">Damit dies funktioniert, müssen Sie auf der Gestaltungsvorlage auch auf jQuery verweisen.</span><span class="sxs-lookup"><span data-stu-id="42219-138">In order for this to work, you also need to reference jQuery in the master page.</span></span> <span data-ttu-id="42219-139">Im folgenden Beispiel sehen Sie in der anfänglichen Seite laden, dass nur ein Bild geladen ist, aber es gibt noch einige mehr auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="42219-139">In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Screenshot mit einem auf der Seite geladenen Bild](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="42219-141">Im folgenden Screenshot werden die restlichen Bilder angezeigt, die nach dem Scrollen in der Ansicht heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="42219-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Screenshot mit mehreren auf der Seite geladenen Bildern](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="42219-143">Das Verzögern des Ladens von Bildern mithilfe von JavaScript kann eine effektive Methode zur Steigerung der Leistung sein. Wenn die Technik jedoch auf einer öffentlichen Website angewendet wird, können Suchmaschinen die Bilder nicht auf die gleiche Weise Crawlen wie ein regelmäßig geformtes Bild.</span><span class="sxs-lookup"><span data-stu-id="42219-143">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image.</span></span> <span data-ttu-id="42219-144">Dies kann sich auf Rankings in Suchmaschinen auswirken, da Metadaten im Bild selbst nicht wirklich vorhanden sind, bis die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="42219-144">This can affect rankings on search engines because metadata on the image itself is not really there until the page loads.</span></span> <span data-ttu-id="42219-145">Suchmaschinen-Crawler lesen nur den HTML-Code und sehen daher die Bilder nicht als Inhalt auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="42219-145">Search engine crawlers only read the HTML and therefore will not see the images as content on the page.</span></span> <span data-ttu-id="42219-146">Bilder sind einer der Faktoren, mit denen Seiten in Suchergebnissen bewertet werden.</span><span class="sxs-lookup"><span data-stu-id="42219-146">Images are one of the factors used to rank pages in search results.</span></span> <span data-ttu-id="42219-147">Eine Möglichkeit, um dies zu umgehen, ist die Verwendung von einführenden Text für Ihre Bilder.</span><span class="sxs-lookup"><span data-stu-id="42219-147">One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="42219-148">GitHub-Codebeispiel: Einfügen von JavaScript zur Verbesserung der Leistung</span><span class="sxs-lookup"><span data-stu-id="42219-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="42219-149">Verpassen Sie nicht den Artikel und das Codebeispiel zur [JavaScript-Injektion](https://go.microsoft.com/fwlink/p/?LinkId=524759) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="42219-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="42219-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="42219-150">See also</span></span>

[<span data-ttu-id="42219-151">Unterstützte Browser in Office 2013 und Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="42219-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="42219-152">Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="42219-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="42219-153">Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="42219-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

