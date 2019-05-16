---
title: Verwenden des Objektcaches mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: In diesem Artikel wird der Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 und SharePoint Online erläutert.
ms.openlocfilehash: 16805aee0c6c6828fc2bf81370046dfd0f1c5a70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070541"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Verwenden des Objektcaches mit SharePoint Online

In diesem Artikel wird der Unterschied zwischen der Verwendung des Objektcaches in SharePoint Server 2013 und SharePoint Online erläutert.
  
Die Nutzung des Objektcaches in der SharePoint Online-Bereitstellung hat erhebliche negative Auswirkungen. Jede Abhängigkeit vom Objektcache in SharePoint Online verringert die Zuverlässigkeit Ihrer Seite. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Funktionsweise des SharePoint Online-und SharePoint Server 2013-Objektcaches

Wenn SharePoint Server 2013 lokal gehostet wird, verfügt der Kunde über private Front-End-Webserver, die den Objektcache hosten. Dies bedeutet, dass der Cache nur einem Kunden zugeordnet ist und nur durch den verfügbaren Arbeitsspeicher und die Zuordnung zum Objektcache begrenzt wird. Da im lokalen Szenario nur ein Kunde bedient wird, haben die Front-End-Webserver in der Regel immer wieder Anforderungen an dieselben Standorte. Dies führt dazu, dass der Cache vollständig schnell und voll von den Listen Abfrageergebnissen und SharePoint-Objekten bleibt, die von Ihren Benutzern regelmäßig angefordert werden.
  
![Zeigt Datenverkehr und Last auf lokalen Front-End-Webservern](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Wenn ein Benutzer zum zweiten Mal eine Seite besucht, wird die Ladezeit der Seite verbessert. Nach mindestens vier Lasten derselben Seite wird die Seite auf allen Front-End-Webservern zwischengespeichert.
  
Im Gegensatz dazu gibt es in SharePoint Online viel mehr Server, aber auch viele weitere Websites. Jeder Benutzer kann eine Verbindung mit einem anderen Front-End-Webserver herstellen, auf dem der Cache nicht aufgefüllt ist. Oder vielleicht wird der Cache für einen Server aufgefüllt, aber der nächste Benutzer des Front-End-Webservers fordert eine Seite von einer anderen Website an. Oder, auch wenn der nächste Benutzer dieselbe Seite wie bei seinem vorherigen Besuch anfordert, wird er auf einen anderen Front-End-Webserver verteilt, der diese Seite nicht im Cache hat. In diesem letzten Fall helfen die Zwischenspeicherung nicht den Benutzern.
  
In der folgenden Abbildung stellt jeder Punkt eine Seite dar, die ein Benutzer anfordert und wo er zwischengespeichert wird. Unterschiedliche Farben repräsentieren unterschiedliche Kunden, die die SaaS-Infrastruktur gemeinsam nutzen.
  
![Zeigt die Ergebnisse der Objektzwischenspeicherung in SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Wie Sie im Diagramm sehen können, sind die Chancen eines Benutzers, der einen Server mit der zwischengespeicherten Version Ihrer Seite trifft, gering. Außerdem kann der Cache aufgrund des großen Durchsatzes und der Tatsache, dass die Server von vielen Standorten gemeinsam genutzt werden, nicht lange dauern, da nur so viel Speicherplatz zur Verfügung steht.
  
Aus all diesen Gründen ist es nicht sinnvoll, Benutzer mit zwischengespeicherten Objekten zu befassen, um eine hohe Benutzerfreundlichkeit und Seitenladezeiten in SharePoint Online sicherzustellen.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Was verwenden wir stattdessen, wenn wir uns nicht auf den Objektcache verlassen können, um die Leistung in SharePoint Online zu verbessern?

Da Sie in SharePoint Online keine Zwischenspeicherung benötigen, sollten Sie alternative Entwurfsansätze für SharePoint-Anpassungen bewerten, die den Objektcache verwenden. Dies führt dazu, dass Ansätze für Leistungsprobleme verwendet werden, die nicht auf der Objektzwischenspeicherung basieren, um für Benutzer gute Ergebnisse zu erzielen. Dies wird in einigen der anderen Artikel in dieser Reihe beschrieben und umfasst:
  
- [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimierung und Bündelung in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Verwenden von Netzwerken für die Inhaltsübermittlung](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

