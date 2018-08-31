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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online

In diesem Artikel wird beschrieben, wie die Ladezeit für SharePoint Online-Seiten mithilfe von JavaScript verzögert Laden von Bildern und auch auf die nicht absolut JavaScript erst nach dem Laden der Seite geladen verringern. 
  
Bilder können das Laden von Seiten in SharePoint Online verlangsamen. Standardmäßig rufen die meisten modernen Internetbrowser Bilder beim Laden einer HTML-Seite vorab ab. Dies kann das Laden der Seite unnötig verlangsamen, wenn die Bilder nicht auf dem Bildschirm sichtbar sind, bis der Benutzer einen Bildlauf nach unten durchführt. Die Bilder können den Browser daran hindern, den sichtbaren Teil der Seite zu laden. Zur Umgehung dieses Problems können Sie JavaScript verwenden, um den Vorgang, dass die Bilder zuerst geladen werden, zu überspringen. Auch das Laden nicht unbedingt erforderlichen JavaScripts kann die Ladezeiten Ihrer SharePoint-Seiten erhöhen. In diesem Thema werden einige Methoden beschrieben, mit deren Hilfe Sie die Seitenladezeiten mit JavaScript in SharePoint Online verbessern können. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Verbessern der Seitenladezeiten durch ein verzögertes Laden von Bildern auf SharePoint Online-Seiten mithilfe von JavaScript

JavaScript können Sie um einen Webbrowser aus vorab ausgewählt Bilder zu verhindern. Dies beschleunigt insgesamt rendern. Hierzu entfernen Sie den Wert der das Src-Attribut aus der \<Img\> tag, und Ersetzen Sie ihn durch den Pfad zu einer Datei in einem Datenattribut z. B.: Daten-Src. Zum Beispiel:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Mithilfe dieser Methode herunterladen nicht im Browser die Bilder sofort. Wenn das Bild bereits in der Ansicht ist, gibt JavaScript im Browser die URL aus der Datenattribut abgerufen, und fügen Sie sie als Wert für das Src-Attribut hat. Das Bild lädt nur als der Benutzer einen Bildlauf, und es geht in der Ansicht.
  
So machen Sie all dies passiert, müssen Sie JavaScript verwenden.
  
Definieren Sie in einer Textdatei die Funktion **isElementInViewport()**, um zu überprüfen, ob sich ein Element in dem Teil des Browsers befindet, der für den Benutzer sichtbar ist. 
  
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

Verwenden Sie anschließend **isElementInViewport()** in der Funktion **loadItemsInView()**. Die Funktion **loadItemsInView()** lädt alle Bilder, die einen Wert für das Attribut "data-scr" haben, wenn sie sich in dem Teil des Browsers befinden, der für den Benutzer sichtbar ist. Fügen Sie die folgende Funktion zur Textdatei hinzu: 
  
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

Rufen Sie abschließend **loadItemsInView()** innerhalb von **window.onscroll()** auf, wie im folgenden Beispiel gezeigt. Dadurch wird sichergestellt, dass alle Bilder, die sich im Viewport befinden, geladen werden, wenn der Benutzer sie benötigt, aber nicht davor. Fügen Sie Folgendes in der Textdatei hinzu: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Für SharePoint Online, müssen Sie die folgende Funktion an die Scroll-Ereignis auf #s4-Arbeitsbereichs anhängen \<Div\> Tag. Dies ist, da die Fensterereignisse überschrieben werden, um sicherzustellen, dass die Multifunktionsleiste an den Anfang der Seite angefügte bleiben.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Speichern Sie die Textdatei als JavaScript-Datei mit der Erweiterung ".js", z. B. "delayLoadImages.js".
  
Nachdem Sie das Schreiben von delayLoadImages.js abgeschlossen haben, können Sie den Inhalt der Datei in eine Gestaltungsvorlage in SharePoint Online hinzufügen. Zu diesem Zweck der Kopfzeile in der Gestaltungsvorlage einen Skript Link hinzugefügt. Nachdem Sie sich in einer Gestaltungsvorlage befindet, wird der JavaScript-Code auf alle Seiten in SharePoint Online-Website angewendet werden, die das Layout der Masterseite verwenden. Alternativ, wenn Sie beabsichtigen, dies nur auf eine Seite der Website verwenden, verwenden Sie den Skript-Editor-Webpart der JavaScript-Code in der Seite einzubetten. Finden Sie weitere Informationen in diesen Themen:
  
- [Vorgehensweise: anwenden eine Gestaltungsvorlage auf eine Website in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Beispiel: Verweisen auf die JavaScript-Datei "delayLoadImages.js" von einer Masterseite in SharePoint Online**
  
Damit dies funktioniert, müssen Sie auch auf die jQuery in der Masterseite verweisen. Im folgenden Beispiel sehen Sie beim ersten Laden der Seite, dass nur ein Bild geladen wird, es auf der Seite aber mehrere Bilder gibt.
  
![Screenshot mit einem geladenen Bild auf der Seite](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Der folgende Screenshot zeigt die restlichen Bilder, die heruntergeladen werden, nachdem sie durch einen Bildlauf sichtbar werden.
  
![Screenshot mit mehreren geladenen Bildern auf der Seite](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Das Verzögern des Ladens von Bildern mithilfe von JavaScript kann sehr effektiv sein, um die Leistung zu erhöhen. Wenn diese Methode jedoch auf eine öffentliche Website angewendet wird, sind die Suchmaschinen nicht in der Lage, die Bilder genauso zu durchforsten wie ein regulär formatiertes Bild. Dies kann sich auf die Priorisierung in den Suchmaschinen auswirken, da die Metadaten für das Bild selbst erst dann wirklich vorhanden sind, wenn die Seite geladen wird. Suchcrawler lesen nur den HTML-Code und erfassen daher die Bilder nicht als Inhalt auf der Seite. Bilder gehören zu den Faktoren, anhand derer Seiten in den Suchergebnissen in einer bestimmten Rangfolge angeordnet werden. Eine Möglichkeit, dieses Problem zu umgehen, besteht darin, Einführungstext für die Bilder zu verwenden.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub-Codebeispiel: Einfügen von JavaScript zur Verbesserung der Leistung

Verpassen Sie nicht im Artikel und Codebeispiele Beispiel auf [JavaScript Einfügung](https://go.microsoft.com/fwlink/p/?LinkId=524759) auf GitHub bereitgestellt. 
  
## <a name="see-also"></a>Siehe auch

[Unterstützte Browser in Office 2013 und Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Vorgehensweise: anwenden eine Gestaltungsvorlage auf eine Website in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

