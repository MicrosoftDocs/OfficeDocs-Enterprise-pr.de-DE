---
title: Verwenden des Objektcaches mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: In diesem Artikel erläutert den Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 lokal und SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540874"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Verwenden des Objektcaches mit SharePoint Online

In diesem Artikel erläutert den Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 lokal und SharePoint Online.
  
Wenn Sie sich auf den Objektcache in SharePoint Online verlassen, ist dies mit bedeutenden Nachteilen verbunden. Jede Abhängigkeit vom Objektcache in SharePoint Online beeinträchtigt die Zuverlässigkeit der Seite. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Wie die SharePoint Online und SharePoint Server 2013 Cache arbeitet Geschäftsobjekt

Wenn SharePoint Server 2013 gehosteten lokalen ist, kann der Kunde auf private Front-End-Webservern, die den Objektcache zu hosten. Dies bedeutet, dass Cache ist ausschließlich für einen Kunden und wird nur begrenzt, nach wie viel Arbeitsspeicher verfügbar und den Objektcache zugewiesen ist. Da nur einen Kunden im lokalen Szenario mit die Front-End-Webservern in der Regel bereitgestellt wird, können Sie Benutzer, die Anfragen immer wieder an dieselben Standorte vorgenommen. Dies bedeutet, dass der Cache vollständige schnell ruft und bleibt die vollständige Liste Abfrageergebnissen und SharePoint-Objekte, die Ihre Benutzer in regelmäßigen Abständen anfordern.
  
![Zeigt lokalen Front-End-Webservern Datenverkehr und Auslastung](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Wenn ein Benutzer also eine Seite zum zweiten Mal besucht, verbessert sich die Ladezeit der Seite. Nach mindestens vier Ladevorgängen der gleichen Seite wird die Seite auf allen Front-End-Webservern zwischengespeichert.
  
Im Gegensatz dazu in SharePoint Online sind viele weitere Server jedoch auch viele weitere Websites. Jeder Benutzer kann auf einen anderen Front-End-Webserver verbinden, für das die Clientcache gefüllt ist. Oder vielleicht der Cache für einen Server aufgefüllt erhalten möchten, aber die fordert eine Seite an des nächsten Benutzers an diesen Front-End-Webserver aus einer anderen Website. Oder, selbst wenn der nächste Benutzer die gleiche Seite wie bei ihrer vorherigen Besuch anfordert, sie sind mit Lastenausgleich an einem anderen Front-End-Webserver, der diese Seite nicht in seinem Cache enthalten ist. In diesem Fall helfen nicht Zwischenspeichern der Benutzer in allen.
  
In der folgenden Abbildung stellt jeder Punkt eine Seite dar, die ein Benutzer anfordert, und gibt an, wo sie zwischengespeichert ist. Die verschiedenen Farben stehen für die unterschiedlichen Kunden, die die SaaS-Infrastruktur gemeinsam nutzen.
  
![Zeigt die Ergebnisse der Zwischenspeicherung von Objekten in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Wie Sie aus dem Diagramm sehen können, sind die Wahrscheinlichkeit, dass alle Benutzer auf einem Server mit der ihre Seite die zwischengespeicherte Version schlanke. Darüber hinaus letzte nicht aufgrund der großen Durchsatz und die Tatsache, dass die Server von vielen Standorten gemeinsam genutzt werden, der Cache lange, da nur so viel Speicherplatz für das Zwischenspeichern vorhanden ist.
  
Aus all diesen Gründen sollte man sich nicht darauf verlassen, dass die Benutzer zwischengespeicherte Objekte aufrufen. Dies ist kein effektiver Ansatz, um eine hohe Benutzerfreundlichkeit und ein schnelles Laden von Seiten in SharePoint Online sicherzustellen.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Aber wenn wir uns nicht auf den Objektcache zur Verbesserung der Leistung in SharePoint Online verlassen können, was können wir stattdessen verwenden?

Da Sie sich nicht auf die Zwischenspeicherung in SharePoint Online verlassen sollten, müssen Sie alternative Designansätze für SharePoint-Anpassungen erwägen, die den Objektcache verwenden. Sie sollten Ansätze für Leistungsprobleme finden, die sich nicht auf das Zwischenspeichern von Objekten stützen, um für die Benutzer gute Ergebnisse zu erzielen. Dies wird in einigen der anderen Artikel dieser Reihe beschrieben:
  
- [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimierung und Bündelung in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Verwenden von Netzwerken für die Inhaltsübermittlung](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

