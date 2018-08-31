---
title: Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: In diesem Artikel wird beschrieben, wie die Ladezeit für SharePoint Online-Seiten mithilfe von JavaScript verzögert Laden von Bildern und auch auf die nicht absolut JavaScript erst nach dem Laden der Seite geladen verringern.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540957"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="c915d-103">Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c915d-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="c915d-104">In diesem Artikel wird beschrieben, wie die Ladezeit für SharePoint Online-Seiten mithilfe von JavaScript verzögert Laden von Bildern und auch auf die nicht absolut JavaScript erst nach dem Laden der Seite geladen verringern.</span><span class="sxs-lookup"><span data-stu-id="c915d-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="c915d-p101">Bilder können das Laden von Seiten in SharePoint Online verlangsamen. Standardmäßig rufen die meisten modernen Internetbrowser Bilder beim Laden einer HTML-Seite vorab ab. Dies kann das Laden der Seite unnötig verlangsamen, wenn die Bilder nicht auf dem Bildschirm sichtbar sind, bis der Benutzer einen Bildlauf nach unten durchführt. Die Bilder können den Browser daran hindern, den sichtbaren Teil der Seite zu laden. Zur Umgehung dieses Problems können Sie JavaScript verwenden, um den Vorgang, dass die Bilder zuerst geladen werden, zu überspringen. Auch das Laden nicht unbedingt erforderlichen JavaScripts kann die Ladezeiten Ihrer SharePoint-Seiten erhöhen. In diesem Thema werden einige Methoden beschrieben, mit deren Hilfe Sie die Seitenladezeiten mit JavaScript in SharePoint Online verbessern können.</span><span class="sxs-lookup"><span data-stu-id="c915d-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="c915d-112">Verbessern der Seitenladezeiten durch ein verzögertes Laden von Bildern auf SharePoint Online-Seiten mithilfe von JavaScript</span><span class="sxs-lookup"><span data-stu-id="c915d-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="c915d-p102">JavaScript können Sie um einen Webbrowser aus vorab ausgewählt Bilder zu verhindern. Dies beschleunigt insgesamt rendern. Hierzu entfernen Sie den Wert der das Src-Attribut aus der \<Img\> tag, und Ersetzen Sie ihn durch den Pfad zu einer Datei in einem Datenattribut z. B.: Daten-Src. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c915d-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="c915d-p103">Mithilfe dieser Methode herunterladen nicht im Browser die Bilder sofort. Wenn das Bild bereits in der Ansicht ist, gibt JavaScript im Browser die URL aus der Datenattribut abgerufen, und fügen Sie sie als Wert für das Src-Attribut hat. Das Bild lädt nur als der Benutzer einen Bildlauf, und es geht in der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c915d-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="c915d-119">So machen Sie all dies passiert, müssen Sie JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="c915d-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="c915d-120">Definieren Sie in einer Textdatei die Funktion **isElementInViewport()**, um zu überprüfen, ob sich ein Element in dem Teil des Browsers befindet, der für den Benutzer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="c915d-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
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

<span data-ttu-id="c915d-p104">Verwenden Sie anschließend **isElementInViewport()** in der Funktion **loadItemsInView()**. Die Funktion **loadItemsInView()** lädt alle Bilder, die einen Wert für das Attribut "data-scr" haben, wenn sie sich in dem Teil des Browsers befinden, der für den Benutzer sichtbar ist. Fügen Sie die folgende Funktion zur Textdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="c915d-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
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

<span data-ttu-id="c915d-p105">Rufen Sie abschließend **loadItemsInView()** innerhalb von **window.onscroll()** auf, wie im folgenden Beispiel gezeigt. Dadurch wird sichergestellt, dass alle Bilder, die sich im Viewport befinden, geladen werden, wenn der Benutzer sie benötigt, aber nicht davor. Fügen Sie Folgendes in der Textdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="c915d-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="c915d-p106">Für SharePoint Online, müssen Sie die folgende Funktion an die Scroll-Ereignis auf #s4-Arbeitsbereichs anhängen \<Div\> Tag. Dies ist, da die Fensterereignisse überschrieben werden, um sicherzustellen, dass die Multifunktionsleiste an den Anfang der Seite angefügte bleiben.</span><span class="sxs-lookup"><span data-stu-id="c915d-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="c915d-129">Speichern Sie die Textdatei als JavaScript-Datei mit der Erweiterung ".js", z. B. "delayLoadImages.js".</span><span class="sxs-lookup"><span data-stu-id="c915d-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="c915d-p107">Nachdem Sie das Schreiben von delayLoadImages.js abgeschlossen haben, können Sie den Inhalt der Datei in eine Gestaltungsvorlage in SharePoint Online hinzufügen. Zu diesem Zweck der Kopfzeile in der Gestaltungsvorlage einen Skript Link hinzugefügt. Nachdem Sie sich in einer Gestaltungsvorlage befindet, wird der JavaScript-Code auf alle Seiten in SharePoint Online-Website angewendet werden, die das Layout der Masterseite verwenden. Alternativ, wenn Sie beabsichtigen, dies nur auf eine Seite der Website verwenden, verwenden Sie den Skript-Editor-Webpart der JavaScript-Code in der Seite einzubetten. Finden Sie weitere Informationen in diesen Themen:</span><span class="sxs-lookup"><span data-stu-id="c915d-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="c915d-135">Vorgehensweise: anwenden eine Gestaltungsvorlage auf eine Website in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c915d-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="c915d-136">Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c915d-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="c915d-137">**Beispiel: Verweisen auf die JavaScript-Datei "delayLoadImages.js" von einer Masterseite in SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="c915d-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="c915d-p108">Damit dies funktioniert, müssen Sie auch auf die jQuery in der Masterseite verweisen. Im folgenden Beispiel sehen Sie beim ersten Laden der Seite, dass nur ein Bild geladen wird, es auf der Seite aber mehrere Bilder gibt.</span><span class="sxs-lookup"><span data-stu-id="c915d-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Screenshot mit einem geladenen Bild auf der Seite](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="c915d-141">Der folgende Screenshot zeigt die restlichen Bilder, die heruntergeladen werden, nachdem sie durch einen Bildlauf sichtbar werden.</span><span class="sxs-lookup"><span data-stu-id="c915d-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Screenshot mit mehreren geladenen Bildern auf der Seite](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="c915d-p109">Das Verzögern des Ladens von Bildern mithilfe von JavaScript kann sehr effektiv sein, um die Leistung zu erhöhen. Wenn diese Methode jedoch auf eine öffentliche Website angewendet wird, sind die Suchmaschinen nicht in der Lage, die Bilder genauso zu durchforsten wie ein regulär formatiertes Bild. Dies kann sich auf die Priorisierung in den Suchmaschinen auswirken, da die Metadaten für das Bild selbst erst dann wirklich vorhanden sind, wenn die Seite geladen wird. Suchcrawler lesen nur den HTML-Code und erfassen daher die Bilder nicht als Inhalt auf der Seite. Bilder gehören zu den Faktoren, anhand derer Seiten in den Suchergebnissen in einer bestimmten Rangfolge angeordnet werden. Eine Möglichkeit, dieses Problem zu umgehen, besteht darin, Einführungstext für die Bilder zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c915d-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="c915d-148">GitHub-Codebeispiel: Einfügen von JavaScript zur Verbesserung der Leistung</span><span class="sxs-lookup"><span data-stu-id="c915d-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="c915d-149">Verpassen Sie nicht im Artikel und Codebeispiele Beispiel auf [JavaScript Einfügung](https://go.microsoft.com/fwlink/p/?LinkId=524759) auf GitHub bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="c915d-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c915d-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c915d-150">See also</span></span>

[<span data-ttu-id="c915d-151">Unterstützte Browser in Office 2013 und Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="c915d-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="c915d-152">Vorgehensweise: anwenden eine Gestaltungsvorlage auf eine Website in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c915d-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="c915d-153">Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c915d-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

