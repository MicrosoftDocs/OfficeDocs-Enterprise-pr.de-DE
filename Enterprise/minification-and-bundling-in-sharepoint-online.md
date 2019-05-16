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
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minimierung und Bündelung in SharePoint Online

In diesem Artikel wird beschrieben, wie Sie Verkleinerungs verwenden und Techniken mit Web Essentials bündeln, um die Anzahl von HTTP-Anforderungen zu reduzieren und die Zeit zu verringern, die zum Laden von Seiten in SharePoint Online benötigt wird.
  
Wenn Sie Ihre Website anpassen, können Sie dem Server eine Vielzahl zusätzlicher Dateien hinzufügen, um die Anpassung zu unterstützen. Durch Hinzufügen von zusätzlichem JavaScript, CSS und Bildern wird die Anzahl der HTTP-Anforderungen an den Server erhöht, was wiederum die Zeitdauer erhöht, die zum Anzeigen einer Webseite benötigt wird. Wenn Sie über mehrere Dateien vom gleichen Typ verfügen, können Sie diese Dateien bündeln, um das Herunterladen dieser Dateien zu beschleunigen.
  
Bei JavaScript-und CSS-Dateien können Sie auch einen Ansatz namens Verkleinerungs verwenden, in dem Sie die Gesamtgröße der Dateien verringern, indem Sie Leerraum und andere Zeichen entfernen, die nicht erforderlich sind.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Verkleinerungs und bündeln von JavaScript-und CSS-Dateien mit Web Essentials

Sie können Software von Drittanbietern wie Web Essentials verwenden, um CSS-und JavaScript-Dateien zu bündeln.
  
> [!IMPORTANT]
> Web Essentials ist ein Open Source-Community-basiertes Projekt eines Drittanbieters. Die Software ist eine Erweiterung von Visual Studio 2012 und Visual Studio 2013 und wird von Microsoft nicht unterstützt. Besuchen Sie die Website unter [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
Web Essentials bietet zwei Formen der Bündelung:
  
- . Bundle: für CSS-und JavaScript-Dateien
    
- . Sprite: für Bilder (nur in Visual Studio 2013 verfügbar)
    
Sie können Web Essentials verwenden, wenn Sie über ein vorhandenes Feature mit einigen Branding-Elementen verfügen, auf die innerhalb einer benutzerdefinierten Gestaltungsvorlage verwiesen wird, beispielsweise:
  
![Screenshot des Marke-Elements in einer benutzerdefinierten Gestaltungsvorlage](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **So erstellen Sie ein TE000127218-und CSS-Bundle in Web Essentials**
  
1. Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle aufnehmen möchten.
    
2. Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü die Option **Web Essentials** \> **Create JavaScript Bundle File** aus. Zum Beispiel: 
    
    ![Screenshot mit Web Essentials-Menü Optionen](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Anzeigen der Ergebnisse der Bündelung von JavaScript-und CSS-Dateien

Wenn Sie ein JavaScript-und CSS-Bundle erstellen, erstellt Web Essentials eine XML-Datei mit dem Namen eine Rezept Datei, die die JavaScript-und CSS-Dateien sowie einige andere Konfigurationsinformationen identifiziert: 
  
![Screenshot der JavaScript-und CSS-Rezept Datei](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Wenn das minimieren-Flag in der Bundle-Rezeptur auf true festgelegt ist, werden außerdem die Dateien sowohl verkleinert als auch gebündelt. Dies hat zur Folge, dass neue, minimierte Versionen der JavaScript-Dateien erstellt wurden, auf die Sie in ihrer Gestaltungsvorlage verweisen können.
  
![Screenshot des minimieren-Flags, das auf true festgelegt ist](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Wenn Sie eine Seite von Ihrer Website laden, können Sie die Entwicklertools Ihres Webbrowsers, wie etwa Internet Explorer 11, verwenden, um die Anzahl der an den Server gesendeten Anforderungen und die Dauer der Ladevorgang für jede Datei anzuzeigen.
  
Die folgende Abbildung ist das Ergebnis des Ladens der JavaScript-und CSS-Dateien vor Verkleinerungs.
  
![Screenshot mit 80 heruntergeladenen Elementen](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Nachdem die CSS-und JavaScript-Dateien zusammengefasst wurden, wurde die Anzahl der Anforderungen auf 74 und jede Datei nur geringfügig länger als die Originaldateien, die einzeln heruntergeladen wurden:
  
![Screenshot mit 74 heruntergeladenen Elementen](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Nach der Bündelung wird die JavaScript-bundledatei erheblich von 815KB zu 365KB reduziert:
  
![Screenshot mit reduzierter Downloadgröße](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Bündeln von Bildern durch Erstellen eines Image-Sprites

Ähnlich wie Sie JavaScript-und CSS-Dateien bündeln, können Sie viele kleine Symbole und andere gängige Bilder zu einem größeren Sprite-Blatt zusammenfassen und dann mit CSS die einzelnen Bilder anzeigen. Anstatt jedes einzelne Bild herunterzuladen, downloadet der Webbrowser des Benutzers das Sprite-Blatt einmal und speichert es dann auf dem lokalen Computer. Dies verbessert die Seiten Ladeleistung, indem die Anzahl der Downloads und Roundtrips zum Webserver reduziert wird.
  
 **So erstellen Sie ein Image-Sprite in Web Essentials**
  
1. Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die Sie in das Bundle aufnehmen möchten.
    
2. Klicken Sie mit der rechten Maustaste auf die ausgewählten Dateien, und wählen Sie dann im Kontextmenü **Web Essentials** \> **Create Image Sprite** aus. Zum Beispiel: 
    
    ![Screenshot, der zeigt, wie Sie ein Image-Sprite erstellen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Wählen Sie einen Speicherort für die Sprite-Datei aus. Die Sprite-Datei ist eine XML-Datei, in der die Einstellungen und Dateien im Sprite beschrieben werden. Die folgenden Abbildungen zeigen ein Beispiel für eine Sprite-PNG-Datei und die entsprechende Sprite-XML-Datei.
    
    ![Screenshot einer Sprite-Datei](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Screenshot der Sprite-XML-Datei](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

