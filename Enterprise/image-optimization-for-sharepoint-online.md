---
title: Bildoptimierung für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Erfahren Sie, wie von Darstellungen und Sprites zum Verbessern der Leistung von Bild auf Ihrer SharePoint Online-Websites.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540742"
---
# <a name="image-optimization-for-sharepoint-online"></a>Bildoptimierung für SharePoint Online

Die Geschwindigkeit beim Laden einer Webseite hängt die Gesamtgröße aller Komponenten, die zum Rendern der Seite, einschließlich Bilder, HTML, JavaScript und CSS-erforderlich. Bilder sind eine hervorragende Möglichkeit zum Ihrer Website ansprechender zu gestalten, aber ihre Größe kann die Leistung beeinträchtigen. Durch Optimieren der Abbilder mit Komprimierung und Ändern der Größe und Verwendung von Sprites, können Sie die Effekte der sehr großen Bilder versetzen. Bilddarstellungen SharePoint verwenden, können Sie ein einzelnes großes Bild hochladen und Anzeigen von Abschnitten des Bilds, sodass es, sondern wiederverwendet werden erneut geladen.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Verwenden von Sprites für ein schnelleres Laden von Bildern in SharePoint Online

|||
|:-----|:-----|
| Ein Bild Sprite enthält viele kleinere Bilder heruntergeladen. Verwendung von CSS, wählen Sie einen Teil der zusammengesetzten Bilds auf einem bestimmten Teil der Seite mit absolute Positionierung angezeigt. Im Grunde Sie ein einzelnes Bild auf der Seite anstelle von laden mehrere Bilder zu verschieben, und stellen einen kleinen Teil dieses Bild sichtbar über einem kleinen Fenster, in dem die erforderliche Komponente des Bilds Sprite angezeigt wird, für den Endbenutzer. SharePoint Online verwendet Sprites, um die verschiedenen Symbole in der Sprite spcommon.png anzuzeigen.  <br/>  Was ist hier behandelt:  <br/>  Bildkomprimierung  <br/>  Bild-Optimierung  <br/>  SharePoint-bilddarstellungen  <br/> |![Screenshot des spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Dies kann die Leistung verbessern, da Sie nur ein Bild anstelle mehrerer herunterladen und Zwischenspeichern und das Abbild. Selbst wenn das Bild nicht zwischengespeicherten, bleibt, wenn ein einzelnes Bild anstatt mehrere Bilder, reduziert diese Methode die Gesamtzahl der HTTP-Anforderungen an den Server, und wie oft Laden der Seite wird. Dies ist eine Form des Image bündeln. Dies ist ein sehr nützliches Verfahren wenn die Bilder nicht sehr häufig, z. B. Symbole an, ändern wie im obigen Beispiel SharePoint dargestellt. Sie können zum [Web Essentials](http://vswebessentials.com/), ein Projekt von Drittanbietern, Open Source, Community-basierten ganz einfach in Microsoft Visual Studio dazu verwenden. Weitere Informationen finden Sie unter [Verkleinerung und bündeln in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Verwenden von Bildkomprimierung und -optimierung für ein schnelleres Laden von Seiten in SharePoint

Bei Bildkomprimierung und -optimierung wird dafür gesorgt, dass die Dateigröße der Bilder reduziert wird, die Sie auf Ihrer Website verwenden. Oft ist die beste Methode zum Reduzieren der Größe eines Bilds, die Größe des Bilds auf die maximalen Abmessungen zu ändern, mit denen es auf der Website angezeigt wird. Es ist nicht sinnvoll, ein Bild größer zu machen, als es je angezeigt wird. Mit einem Bildeditor können Sie sicherstellen, dass die Bilder die richtigen Maße haben, und so die Größe Ihrer Seite schnell und einfach verringern.
  
Nachdem die richtige Größe sind, besteht der nächste Schritt die Komprimierung von diese Bilder zu optimieren. Es gibt verschiedene Tools zur Verfügung, für die Komprimierung und Optimierung, einschließlich Photo Gallery und Drittanbietertools verwenden. Die Komprimierung ist die Dateigröße so weit wie möglich zu verringern, ohne Beeinträchtigung der alle erkennbaren Qualität für Endbenutzer. Stellen Sie sicher, dass Sie testen die komprimierten Dateien auf einem High-Definition-Display, um sicherzustellen, dass sie immer noch eine gute aussieht.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Beschleunigen von Seitendownloads mithilfe von SharePoint-Bildwiedergaben

Bilddarstellungen sind ein Feature in SharePoint Online, die verschiedenen Versionen von Images basierend auf vordefinierten Image Dimensionen bereitgestellt werden können. Dies ist besonders wichtig, wenn benutzergenerierten Bildinhalt vorhanden ist oder der Bildgröße, z. B. Breite und Höhe durch den CSS-Code auf der Website behoben werden. Selbst wenn ein Bild durch CSS behoben ist, wird das vollständige Lösung Bild noch geladen. In diesem Fall kann die Dateigröße mithilfe von bilddarstellungen reduziert werden.
  
> [!NOTE]
> Darstellungen sind nur verfügbar für SharePoint, wenn die Veröffentlichung aktiviert ist. Sie können die Veröffentlichung unter Einstellungen aktivieren \> Websiteeinstellungen \> Websitefeatures verwalten \> SharePoint Server-Veröffentlichung. Die Option wird andernfalls nicht angezeigt. 
  
Bei der Größenänderung durch Bildwiedergaben wird die kleinste Dimension, die Sie definieren, herangezogen, entweder Breite oder Höhe. Dann wird die Größe des Bilds so geändert, dass automatisch auch die Größe der anderen Dimension auf dem gesperrten Seitenverhältnis geändert wird. Standardmäßig wird durch die verbleibenden Dimensionen das Bild von der Mitte zugeschnitten. Beispiel: Wenn Sie eine Bildwiedergabe mit 100 Pixel Breite und 50 Pixel Höhe definieren und das ursprüngliche Bild 1.000 Pixel breit und 800 Pixel hoch ist, wird dessen Größe so geändert, dass die Dimension der 800 Pixel jetzt 50 Pixel beträgt, und die Dimension der 1.000 Pixel (jetzt 62,5 Pixel) wird von der Mitte des Bilds zugeschnitten.
  
Die Schritte sind relativ einfach. Damit für Bilder aber Bildwiedergaben verwendet werden können, müssen sich die Bildwiedergaben auf der SharePoint-Website befinden, bevor Sie die Bilder hinzufügen. Darüber hinaus müssen Sie auch die Funktionen SharePoint Server-Veröffentlichungsinfrastruktur (Websitesammlungsebene) und SharePoint Server-Veröffentlichung (Websiteebene) aktiviert haben.
  
 **Hinzufügen einer Wiedergabe eines beschnittenen Bildes um Laden der Seite zu beschleunigen**
  
1. Stellen Sie sicher, dass das Benutzerkonto, mit das dieser Vorgang ausgeführt wird, mindestens Entwurfsberechtigungen für die Website auf oberster Ebene der Websitesammlung, und die Website auf einer Webseite veröffentlicht wird.
    
2. Wechseln Sie in einem Webbrowser zu der Website auf oberster Ebene der veröffentlichenden Websitesammlung.
    
3. Wählen Sie das Symbol **Einstellungen** aus. 
    
4. Auf der Seite **Websiteeinstellungen** im Abschnitt **Aussehen und Verhalten** sehen Sie die integrierten Bildwiedergaben. 
    
    Sie können sofort nutzbare Bildwiedergaben verwenden oder **Bildwiedergaben** auswählen, um eine neue zu erstellen. 
    
    ![Screenshot der Wiedergabe eines beschnittenen Bildes](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Wählen Sie auf der Seite **Bildwiedergaben** die Option **Neues Element hinzufügen** aus.
    
    ![Screenshot von "Neues Element hinzufügen"](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Geben Sie auf der Seite **Neue Bildwiedergabe** im Feld **Name** einen Namen für die Bildwiedergabe ein. 
    
7. Geben Sie in den Textfeldern **Breite** und **Höhe** die Breite und Höhe für die Bildwiedergabe in Pixel ein, und wählen Sie dann **Speichern** aus.
    
    ![Screenshot des Bildwiedergabenamens](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Benutzerdefiniertes Zuschneiden mit Bildwiedergaben in SharePoint

Standardmäßig wird eine Wiedergabe eines beschnittenen Bildes aus der Mitte des Bilds generiert. Sie können die Wiedergabe eines beschnittenen Bildes für einzelne Bilder anpassen, indem Sie zuschneiden den Teil des Bilds, das Sie verwenden möchten. Sie können die Bilder einzeln, pro Wiedergabe zuschneiden. Zuschneiden die Bilder beschleunigt mithilfe SharePoints BLOB-Cache, erstellen Sie eine Version des Bilds für jede Wiedergabe Laden der Seite ab. Auf diese Weise die Serverlast wird reduziert, da das Bild nur einmal Größe wird und bereit ist, um mehrere Male für Endbenutzer zu verarbeiten. Weitere Informationen zum ein Wiedergabe eines beschnittenen Bildes zuzuschneiden finden Sie unter [ein Wiedergabe eines beschnittenen Bildes zuzuschneiden](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

