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
description: Erfahren Sie, wie Sie Darstellungen und Sprites verwenden, um die Bildleistung auf Ihren SharePoint Online-Websites zu verbessern.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487361"
---
# <a name="image-optimization-for-sharepoint-online"></a>Bildoptimierung für SharePoint Online

Die Ladegeschwindigkeit einer Webseite hängt von der Gesamtgröße aller Komponenten ab, die zum Rendern der Seite erforderlich sind, einschließlich Bildern, HTML, JavaScript und CSS. Bilder sind eine großartige Möglichkeit, Ihre Website attraktiver zu gestalten, ihre Größe kann jedoch die Leistung beeinträchtigen. Wenn Sie Ihre Bilder durch Komprimierung und Größenänderung optimieren und mithilfe von Sprites können Sie die Effekte von sehr großen Bildern kompensieren. Mithilfe von SharePoint-Bilddarstellungen können Sie ein einzelnes groß Bild hochladen und Abschnitte des Bilds anzeigen, sodass es wieder verwendet und nicht erneut geladen wird.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Verwenden von Sprites zum Beschleunigen des Ladens von Bildern in SharePoint Online

|||
|:-----|:-----|
| Ein Image-Sprite enthält viele kleinere Bilder. Mit CSS wählen Sie einen Teil des zusammengesetzten Bilds aus, der auf einem bestimmten Teil der Seite mit absoluter Positionierung angezeigt werden soll. Grundsätzlich verschieben Sie ein einzelnes Bild um die Seite, anstatt mehrere Bilder zu laden, und machen einen kleinen Teil dieses Bilds sichtbar durch ein kleines Fenster, in dem der erforderliche Teil des Sprite-Bilds für den Endbenutzer angezeigt wird. SharePoint Online verwendet Sprites, um die unterschiedlichen Symbole in der aufeinander.  <br/>  Hier finden Sie die folgenden Themen:  <br/>  Bildkomprimierung  <br/>  Bildoptimierung  <br/>  SharePoint-Bilddarstellungen  <br/> |![Screenshot von "häufiger"](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Dies kann die Leistung verbessern, da Sie nur ein Bild anstatt mehrerer herunterladen und dann dieses Bild Zwischenspeichern und wieder verwenden. Auch wenn das Bild nicht zwischengespeichert bleibt, indem Sie ein einzelnes Bild anstelle von mehreren Bildern haben, wird durch diese Methode die Gesamtzahl der HTTP-Anforderungen an den Server reduziert, wodurch die Seitenladezeiten verkürzt werden. Dies ist wirklich eine Form der Bild Bündelung. Dies ist eine sehr nützliche Methode, wenn sich die Bilder nicht sehr häufig ändern, beispielsweise Symbole, wie im obigen SharePoint-Beispiel dargestellt. Sie können [Web Essentials](http://vswebessentials.com/), ein Open Source-Community-basiertes Projekt von Drittanbietern verwenden, um dies problemlos in Microsoft Visual Studio zu erreichen. Weitere Informationen finden Sie unter [Verkleinerungs und Bündelung in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Verwenden von Bildkomprimierung und-Optimierung, um das Laden von Seiten in SharePoint zu beschleunigen

Bei der Bildkomprimierung und-Optimierung geht es darum, die Dateigröße der Bilder, die Sie auf Ihrer Website verwenden, zu reduzieren. Die beste Technik, um die Größe eines Bilds zu verringern, besteht oft in der Größe des Bilds auf die maximalen Dimensionen, die auf der Website angezeigt werden. Es hat keinen Sinn, ein Bild größer zu haben, als es jemals angezeigt wird. Sicherstellen, dass die Bilder in den richtigen Dimensionen mit einem Bild-Editor sind, ist eine schnelle und einfache Möglichkeit, um die Größe Ihrer Seite zu reduzieren.
  
Sobald Bilder die richtige Größe haben, besteht der nächste Schritt darin, die Komprimierung dieser Bilder zu optimieren. Für Komprimierung und Optimierung stehen verschiedene Tools zur Verfügung, darunter Fotogalerie und Drittanbietertools. Der Schlüssel zur Komprimierung besteht darin, die Dateigröße so weit wie möglich zu reduzieren, ohne für Endbenutzer eine erkennbare Qualität zu verlieren. Vergewissern Sie sich, dass Sie Ihre komprimierten Dateien auf einer hochauflösenden Anzeige testen, um sicherzustellen, dass Sie immer noch gut aussehen.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Beschleunigen von Seitendownloads mithilfe von SharePoint-Bilddarstellungen

Bildwiedergaben sind ein Feature in SharePoint Online, mit dem Sie verschiedene Versionen von Bildern basierend auf vordefinierten Bilddimensionen bereitstellen können. Dies ist besonders wichtig, wenn Benutzer generierte Bildinhalte vorhanden sind oder die Bildabmessungen wie Breite und Höhe durch den CSS auf der Website festgelegt sind. Auch wenn ein Bild mit CSS festgelegt ist, wird das vollständige Bild der Auflösung immer noch geladen. In diesem Fall kann die Dateigröße mithilfe von Bilddarstellungen reduziert werden.
  
> [!NOTE]
> Darstellungen sind nur für SharePoint verfügbar, wenn die Veröffentlichung aktiviert ist. Sie können die Veröffentlichung unter Einstellungen \> Websiteeinstellungen \> Verwalten von Website \> Features SharePoint Server Publishing aktivieren. Die Option wird nicht anders angezeigt. 
  
Die Größenänderung der Bildwiedergabe wird durch die kleinste von Ihnen definierte Dimension, entweder Breite oder Höhe, und durch anschließende Änderung der Größe des Bilds, sodass die andere Bemaßung automatisch auf Grundlage des gesperrten Seitenverhältnisses angepasst wird. Standardmäßig wird das Bild von der Mitte um die restlichen Bemaßungen zugeschnitten. Wenn Sie beispielsweise eine Darstellung von 100px Wide und 50px High definieren und Ihr Originalbild 1000px breit und 800px hoch ist, wird die Größe geändert, sodass die 800px-Dimension jetzt 50px ist und die 1000px-Dimension (jetzt 62,5 px) von der Mitte des Bilds abgeschnitten wird.
  
Die Schritte sind relativ einfach, aber damit Bilder die Darstellungen verwenden können, müssen die Formatvarianten auf der SharePoint-Website sein, bevor Sie die Bilder hinzufügen. Außerdem müssen Sie die SharePoint Server-Veröffentlichungs Infrastruktur (WebsitesammlungsEbene) und die SharePoint Server-Veröffentlichungsfeatures (Websiteebene) aktiviert haben.
  
 **Hinzufügen einer Bildwiedergabe zur Beschleunigung des Seitenladevorgangs**
  
1. Stellen Sie sicher, dass das Benutzerkonto, mit dem dieses Verfahren ausgeführt wird, mindestens über Entwurfsberechtigungen für die Website auf oberster Ebene der Websitesammlung verfügt und dass die Website auf einer Webseite veröffentlicht wird.
    
2. Wechseln Sie in einem Webbrowser zur Website auf oberster Ebene der Veröffentlichungswebsite Sammlung.
    
3. Klicken Sie auf das Symbol **Einstellungen**. 
    
4. Auf der Seite **Websiteeinstellungen** im Abschnitt **Aussehen und Verhalten** werden die integrierten Bilddarstellungen angezeigt. 
    
    Sie können die Out-of-Box-Formatvarianten verwenden oder **Bilddarstellungen** auswählen, um eine neue zu erstellen. 
    
    ![Screenshot der Bilddarstellung](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Wählen Sie auf der Seite **Bildwiedergaben** die Option **Neues Element hinzufügen**.
    
    ![Screenshot des neuen Elements hinzufügen](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Geben Sie auf der Seite **Neue Bildwiedergabe** in das Feld **Name** einen Namen für die Darstellung ein, z. 
    
7. Geben Sie in die Textfelder **Breite** und **Höhe** die Breite und Höhe der Darstellung in Pixel ein, und klicken Sie dann auf **Speichern**.
    
    ![Screenshot des Bildwiedergabe namens](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Benutzerdefiniertes Zuschneiden mit Bilddarstellungen in SharePoint

Standardmäßig wird eine Bilddarstellung aus der Mitte des Bilds generiert. Sie können die Bilddarstellung für einzelne Bilder anpassen, indem Sie den Teil des Bilds zuschneiden, den Sie verwenden möchten. Sie können die Bilder pro Darstellung individuell zuschneiden. Das zuSchneiden der Bilder beschleunigt das Laden der Seite, indem der BLOB-Cache von SharePoint zum Erstellen einer Version des Bilds für jede Darstellung verwendet wird. Auf diese Weise wird die Serverlast reduziert, da das Bild nur einmal geändert wird und dann den Endbenutzern mehrmals zur Verfügung steht. Weitere Informationen zum Zuschneiden einer Bilddarstellung finden Sie unter [Zuschneiden einer Bilddarstellung](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

