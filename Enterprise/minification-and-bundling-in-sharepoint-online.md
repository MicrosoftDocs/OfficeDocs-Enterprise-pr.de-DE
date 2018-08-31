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
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minimierung und Bündelung in SharePoint Online

In diesem Artikel wird beschrieben, wie Sie bei einer Verkleinerung und Techniken mit Web Essentials bündeln zur Reduzierung der Anzahl der HTTP-Anfragen und zu den Zeitraum zu verkürzen, die zum Laden von Seiten in SharePoint Online benötigt wird.
  
Es kann sein, dass Sie beim Anpassen Ihrer Website eine große Anzahl zusätzlicher Dateien zum Server hinzufügen müssen, um die Anpassung zu unterstützen. Durch Hinzufügen von zusätzlichen JavaScript-, CSS- und Bilddateien erhöht sich die Anzahl der HTTP-Anforderungen an den Server, was wiederum die Anzeige einer Webseite verlangsamt. Wenn Sie über mehrere Dateien desselben Typs verfügen, können Sie diese Dateien bündeln bzw. in einem Paket zusammenfassen, um das Herunterladen dieser Dateien zu beschleunigen.
  
Für JavaScript und CSS-Dateien können Sie auch einen Ansatz Verkleinerung, aufgerufen, in dem Sie reduzieren der Gesamtgröße von Dateien durch Entfernen von Leerzeichen und Sonderzeichen, die nicht erforderlich sind.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minimierung und Bündelung von JavaScript- und CSS-Dateien mit Web Essentials

Sie können eine Drittanbietersoftware verwenden, z. B. Web Essentials, um CSS- und JavaScript-Dateien zu bündeln.
  
> [!IMPORTANT]
> Web Essentials ist ein Drittanbieter-, Open Source, Community-basierte Projekt. Die Software ist eine Erweiterung für Visual Studio 2012 und Visual Studio 2013 und wird von Microsoft nicht unterstützt. Informationen zum Herunterladen von Web Essentials finden Sie auf der Website unter [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
Web Essentials bietet zwei Arten der Bündelung an:
  
- BUNDLE: für CSS- und JavaScript-Dateien
    
- SPRITE: für Bilder (nur verfügbar in Visual Studio 2013)
    
Sie können Web Essentials verwenden, wenn Sie über ein vorhandenes Feature mit Brandingelementen verfügen, auf die innerhalb einer benutzerdefinierten Masterseite verwiesen wird, zum Beispiel:
  
![Screenshot des Markenelements in der benutzerdefinierten Gestaltungsvorlage](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Zum Erstellen einer TE000127218 und CSS-Bundle in Web Essentials**
  
1. Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die im Paket enthalten sein sollen.
    
2. Mit der rechten Maustaste der ausgewählten Dateien, und wählen Sie **Web Essentials** \> **JavaScript erstellen Bundle-Datei** aus dem Kontextmenü. Zum Beispiel: 
    
    ![Screenshot mit Web Essentials-Menüoptionen](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Anzeigen der Ergebnisse der Bündelung von JavaScript- und CSS-Dateien

Bei der Erstellung eines JavaScript- und CSS-Pakets erstellt Web Essentials eine XML-Datei, die als Rezeptdatei bezeichnet wird. Sie gibt die JavaScript- und CSS-Dateien und weitere Konfigurationsinformationen an: 
  
![Screenshot von JavaScript- und CSS-Rezeptdatei](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Wenn das Kennzeichen für die Minimierung im Bündelungsrezept auf "wahr" gesetzt ist, werden die Dateien größenmäßig reduziert und zu einem Paket zusammengefasst. Auf diese Weise werden neue, verkleinerte Versionen der JavaScript-Dateien erstellt, auf die Sie in Ihrer Masterseite verweisen können.
  
![Screenshot der Verkleinerungskennzeichnung, die auf "true" eingestellt ist](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Wenn Sie eine Seite von Ihrer Website laden, können Sie die Entwicklertools Ihres Webbrowsers, z. B. Internet Explorer 11, verwenden, um die Anzahl der Anforderungen an den Server anzuzeigen und einzusehen, wie lange jede Datei zum Laden gebraucht hat.
  
Die folgende Abbildung zeigt das Ergebnis des Ladens der JavaScript- und CSS-Dateien vor der Minimierung.
  
![Screenshot mit 80 Elementen, die heruntergeladen werden](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Nach Bündelung der CSS- und JavaScript-Dateien hat sich die Anzahl der Anforderungen auf 74 verringert, und jede Datei brauchte nur geringfügig länger als die ursprünglichen Dateien beim einzelnen Herunterladen:
  
![Screenshot mit 74 Elementen, die heruntergeladen werden](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Nach der Bündelung hat sich die JavaScript-Paketdatei deutlich von 815 KB auf 365 KB reduziert:
  
![Screenshot mit reduzierter Downloadgröße](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Bündelung von Bildern durch Erstellen eines Image Sprite

Ähnlich wie Sie JavaScript und CSS-Dateien verpacken, können viele kleine Symbole und andere allgemeine Bilder in einem größeren Sprite Blatt kombinieren und dann CSS verwenden, um die einzelnen Bilder anzuzeigen. Nicht auf jedes einzelne Bild herunterladen, Webbrowser des Benutzers das Blatt Sprite einmal downloads und speichert es auf dem lokalen Computer. Dadurch wird die seitenladeleistung durch verringert die Anzahl der Downloads und Roundtrips an den Webserver verbessert.
  
 **So erstellen Sie ein Image Sprite in Web Essentials**
  
1. Wählen Sie in Visual Studio im Projektmappen-Explorer die Dateien aus, die im Paket enthalten sein sollen.
    
2. Mit der rechten Maustaste der ausgewählten Dateien, und wählen Sie **Web Essentials** \> **erstellen Bild Sprite** im Kontextmenü aus. Zum Beispiel: 
    
    ![Screenshot zeigt, wie Sie ein Bild-Sprite erstellen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Wählen Sie einen Speicherort für die Sprite-Datei aus. Bei der Sprite-Datei handelt es sich um eine XML-Datei, die die Einstellungen und Dateien im Sprite beschreibt. Die folgenden Abbildungen zeigen ein Beispiel für eine Sprite-PNG-Datei und die zugehörige Sprite-XML-Datei.
    
    ![Screenshot einer Sprite-Datei](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Screenshot der Sprite-XML-Datei](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

