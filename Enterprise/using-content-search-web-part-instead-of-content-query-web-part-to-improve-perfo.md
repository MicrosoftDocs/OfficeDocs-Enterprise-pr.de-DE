---
title: Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: In diesem Artikel wird beschrieben, wie auf die Leistung zu erhöhen, indem Sie das Webpart für Inhaltsabfragen durch das Inhaltssuche-Webpart in SharePoint Server 2013 und SharePoint Online ersetzen.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541039"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online

In diesem Artikel wird beschrieben, wie auf die Leistung zu erhöhen, indem Sie das Webpart für Inhaltsabfragen durch das Inhaltssuche-Webpart in SharePoint Server 2013 und SharePoint Online ersetzen.
  
Eine effizienteste neue Features von SharePoint Server 2013 und SharePoint Online ist das Content Search Web Part (CSWP). Dieses Webpart verwendet den Suchindex schnell Ergebnisse abgerufen, die dem Benutzer angezeigt werden. Verwenden Sie das Inhaltssuche-Webpart anstelle der Content Abfrage Web Part (CQWP) auf den Seiten zum Verbessern der Leistung für Ihre Benutzer.
  
Verwenden ein Inhaltssuche-Webpart über ein Webpart für Inhaltsabfragen wird deutlich besser seitenladeleistung SharePoint Online fast immer führen. Es ist eine wenig zusätzliche Konfiguration die richtige Abfrage abgerufen, aber die verbesserte Leistung und happier Benutzer sind.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Der Leistungsgewinn vergleichen, die aus der Inhaltssuche-Webpart verwenden, anstatt Webpart für Inhaltsabfragen

Die folgenden Beispiele zeigen die relative Leistungsgewinnen, die möglicherweise angezeigt wird, wenn Sie ein Inhaltssuche-Webpart anstelle von einem Webpart für Inhaltsabfragen verwenden. Die Effekte sind deutlicher mit einer komplexen Websitestruktur und sehr große Content-Abfragen.
  
In diesem Beispiel Website weist folgende Merkmale auf:
  
- 8 Ebenen von Unterwebsites.
    
- Enthält einen benutzerdefinierten "Obst" Inhaltstyp verwenden.
    
- Im Webpart ist das Inhaltsabfrage umfassende, alle Elemente mit dem Inhaltstyp "Frucht" zurückgeben.
    
- Im Beispiel wird nur 50 Elemente 8 Standorten verwendet. Die Effekte werden auch für Websites mit Weitere Inhalte zu deutlicher.
    
Es folgt ein Screenshot der Ergebnisse der das Webpart für Inhaltsabfragen.
  
![Grafische Darstellung der Inhaltsabfrage-Webparts](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Verwenden Sie in Internet Explorer die Registerkarte **Netzwerk** der F12-Entwicklertools betrachten Sie die Details für den Antwortheader. Im folgenden Screenshot ist der Wert für die **SPRequestDuration** für diese Seite Last 924 Millisekunden. 
  
![Screenshot mit Anforderungsdauer von 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** gibt den Zeitraum der Arbeit, ausgeführt wird, auf dem Server auf die Seite vorbereiten. Ändern des Inhalts von Webparts für Inhaltsabfragen mit Inhalt von Suchwebparts erheblich verringert den Zeitaufwand zum Rendern der Seite. Im Gegensatz dazu hat eine Seite mit einer gleichwertigen Inhaltssuche-Webpart, die gleiche Anzahl von Ergebnissen zurückgeben **SPRequestDuration** Wert 106 Millisekunden wie in diesem Screenshot dargestellt: 
  
![Screenshot mit Anforderungsdauer von 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Hinzufügen eines Inhaltssuche-Webparts in SharePoint Online

Hinzufügen einer Inhaltssuche-Webpart ist sehr ähnlich einer regulären Webpart für Inhaltsabfragen. Finden Sie im Abschnitt *"Hinzufügen eines Inhaltssuche-Webpart"* unter [Configure ein Inhaltssuche-Webpart in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Erstellen die richtigen Suchabfrage für die Inhaltssuche-Webpart

Nachdem Sie ein Inhaltssuche-Webpart hinzugefügt haben, können Sie verfeinern die Suche und die gewünschten Elemente zurückgeben. Ausführliche Informationen hierzu finden Sie im Abschnitt, *"Content durch Konfigurieren einer erweiterten Abfrage in ein Inhaltssuche-Webpart anzeigen"* unter [Konfigurieren eines Inhalts-Webparts in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Entwickeln und Testen von Tool Abfragen

Ein Tool zum Erstellen und Testen komplexe Abfragen finden Sie unter dem [Search-Abfrage-Tool](https://sp2013searchtool.codeplex.com/) bei Codeplex. 
  

