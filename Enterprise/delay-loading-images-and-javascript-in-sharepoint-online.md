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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online

In diesem Artikel wird beschrieben, wie Sie die Ladezeit für SharePoint Online-Seiten reduzieren können, indem Sie JavaScript verwenden, um das Laden von Bildern zu verzögern, und außerdem darauf warten, nicht erforderliches JavaScript zu laden, bis die Seite geladen wurde. 
  
Bilder können sich negativ auf die Seiten ladegeschwindigkeiten bei SharePoint Online auswirken. Standardmäßig holen die meisten modernen Internet Browser Bilder beim Laden einer HTML-Seite vor. Dies kann dazu führen, dass die Seite unnötig langsam geladen wird, wenn die Bilder auf dem Bildschirm nicht sichtbar sind, bis der Benutzer einen Bildlauf nach unten durchgeführt hat. Die Bilder können verhindern, dass der Browser den sichtbaren Teil der Seite lädt. Um dieses Problem zu umgehen, können Sie JavaScript verwenden, um das Laden der Bilder zuerst zu überspringen. Außerdem kann das Laden nicht erforderlicher JavaScript-Dateien die Ladezeiten auf Ihren SharePoint-Seiten verlangsamen. In diesem Thema werden einige Methoden beschrieben, mit denen Sie Seitenladezeiten mit JavaScript in SharePoint Online verbessern können. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Verbessern der Seitenladezeiten durch verzögertes Laden von Bildern in SharePoint Online-Seiten mithilfe von JavaScript

Sie können JavaScript verwenden, um zu verhindern, dass ein Webbrowser Bilder vorab abruft. Dadurch wird das Gesamtdokument Rendering beschleunigt. Zu diesem Zweck entfernen Sie den Wert des src-Attributs aus dem \<IMG\> -Tag und ersetzen ihn durch den Pfad zu einer Datei in einem Data-Attribut wie: Data-src. Zum Beispiel:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Bei Verwendung dieser Methode werden die Bilder vom Browser nicht sofort heruntergeladen. Wenn sich das Bild bereits im Ansichtsfenster befindet, weist JavaScript den Browser an, die URL aus dem Data-Attribut abzurufen und als Wert für das src-Attribut einzufügen. Das Bild wird nur geladen, wenn der Benutzer einen Bildlauf durchführt und es angezeigt wird.
  
Um dies zu erreichen, müssen Sie JavaScript verwenden.
  
Definieren Sie in einer Textdatei die **isElementInViewport ()** -Funktion, um zu überprüfen, ob sich ein Element in dem Teil des Browsers befindet, der für den Benutzer sichtbar ist. 
  
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

Als nächstes verwenden Sie **isElementInViewport ()** in der **loadItemsInView ()** -Funktion. Die **loadItemsInView ()** -Funktion lädt alle Bilder mit einem Wert für das Data-src-Attribut, wenn Sie sich im Browser Teil befinden, der für den Benutzer sichtbar ist. Fügen Sie die folgende Funktion zur Textdatei hinzu: 
  
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

Rufen Sie schließlich **loadItemsInView ()** innerhalb von **Window. OnScroll ()** auf, wie im folgenden Beispiel gezeigt. Dadurch wird sichergestellt, dass alle im Viewport enthaltenen Bilder geladen werden, wenn der Benutzer Sie benötigt, jedoch nicht zuvor. Fügen Sie Folgendes zur Textdatei hinzu: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Für SharePoint Online müssen Sie die folgende Funktion an das Scroll-Ereignis im #S4-Workspace \<div\> -Tag anfügen. Der Grund dafür ist, dass die Window-Ereignisse überschrieben werden, um sicherzustellen, dass das Menüband am oberen Rand der Seite befestigt bleibt.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Speichern Sie die Textdatei als JavaScript-Datei mit der Erweiterung. js, beispielsweise "delayLoadImages. js".
  
Nachdem Sie delayLoadImages. js geschrieben haben, können Sie den Inhalt der Datei einer Gestaltungsvorlage in SharePoint Online hinzufügen. Hierzu fügen Sie der Kopfzeile auf der Gestaltungsvorlage einen Skript Link hinzu. Sobald Sie sich in einer Gestaltungsvorlage befindet, wird das JavaScript auf alle Seiten Ihrer SharePoint Online-Website angewendet, die dieses Gestaltungsvorlagen Layout verwenden. Wenn Sie dies nur auf einer Seite Ihrer Website verwenden möchten, verwenden Sie alternativ das Skript-Editor-Webpart, um das JavaScript in die Seite einzubetten. Weitere Informationen finden Sie in den folgenden Themen:
  
- [Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Beispiel: verweisen auf die JavaScript-Datei delayLoadImages. js von einer Gestaltungsvorlage in SharePoint Online**
  
Damit dies funktioniert, müssen Sie auf der Gestaltungsvorlage auch auf jQuery verweisen. Im folgenden Beispiel sehen Sie in der anfänglichen Seite laden, dass nur ein Bild geladen ist, aber es gibt noch einige mehr auf der Seite.
  
![Screenshot mit einem auf der Seite geladenen Bild](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Im folgenden Screenshot werden die restlichen Bilder angezeigt, die nach dem Scrollen in der Ansicht heruntergeladen werden.
  
![Screenshot mit mehreren auf der Seite geladenen Bildern](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Das Verzögern des Ladens von Bildern mithilfe von JavaScript kann eine effektive Methode zur Steigerung der Leistung sein. Wenn die Technik jedoch auf einer öffentlichen Website angewendet wird, können Suchmaschinen die Bilder nicht auf die gleiche Weise Crawlen wie ein regelmäßig geformtes Bild. Dies kann sich auf Rankings in Suchmaschinen auswirken, da Metadaten im Bild selbst nicht wirklich vorhanden sind, bis die Seite geladen wird. Suchmaschinen-Crawler lesen nur den HTML-Code und sehen daher die Bilder nicht als Inhalt auf der Seite. Bilder sind einer der Faktoren, mit denen Seiten in Suchergebnissen bewertet werden. Eine Möglichkeit, um dies zu umgehen, ist die Verwendung von einführenden Text für Ihre Bilder.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub-Codebeispiel: Einfügen von JavaScript zur Verbesserung der Leistung

Verpassen Sie nicht den Artikel und das Codebeispiel zur [JavaScript-Injektion](https://go.microsoft.com/fwlink/p/?LinkId=524759) auf GitHub. 
  
## <a name="see-also"></a>Siehe auch

[Unterstützte Browser in Office 2013 und Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Vorgehensweise: Anwenden einer Gestaltungsvorlage auf eine Website in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Vorgehensweise: Erstellen eines Seitenlayouts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

