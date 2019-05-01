---
title: Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online
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
description: In diesem Artikel wird beschrieben, wie Sie die Leistung steigern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492166"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online

In diesem Artikel wird beschrieben, wie Sie die Leistung steigern, indem Sie das Webpart für Inhaltsabfragen durch das Webpart für die Inhaltssuche in SharePoint Server 2013 und SharePoint Online ersetzen.
  
Eine der leistungsfähigsten neuen Features von SharePoint Server 2013 und SharePoint Online ist das Inhaltssuche-Webpart (INHALTSSUCHE). Dieses Webpart verwendet den Suchindex, um schnell Ergebnisse abzurufen, die dem Benutzer angezeigt werden. Verwenden Sie das Inhaltssuche-Webpart anstelle des Inhaltsabfrage-Webparts (CQWP) auf Ihren Seiten, um die Leistung für Ihre Benutzer zu verbessern.
  
Die Verwendung eines Inhaltssuche-Webparts über ein Inhaltsabfrage-Webpart führt fast immer zu einer deutlich besseren Seiten Ladeleistung in SharePoint Online. Es gibt eine kleine zusätzliche Konfiguration, um die richtige Abfrage zu erhalten, aber die Vorteile sind verbesserte Leistung und zufriedenere Benutzer.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Vergleich der Leistungssteigerung, die Sie mit dem Webpart "Inhaltssuche" erhalten, anstelle des Webparts für Inhaltsabfragen

Die folgenden Beispiele zeigen die relativen Leistungssteigerungen, die beim Verwenden eines Inhaltssuche-Webparts anstelle eines Inhaltsabfrage-Webparts auftreten können. Die Effekte sind bei einer komplexen Websitestruktur und sehr umfangreichen Inhaltsabfragen deutlicher.
  
Diese Beispielwebsite weist die folgenden Merkmale auf:
  
- 8 Stufen der Unterwebsites.
    
- Listen, die einen benutzerdefinierten Inhaltstyp "Fruit" verwenden.
    
- Im Webpart ist die Inhaltsabfrage breit und gibt alle Elemente mit dem Inhaltstyp "Fruit" zurück.
    
- Das Beispiel verwendet nur 50-Elemente in den 8-Standorten. Die Effekte werden für Websites mit mehr Inhalt noch ausgeprägter.
    
Im folgenden finden Sie einen Screenshot der Ergebnisse des Inhaltsabfrage-Webparts.
  
![Grafik mit Inhaltsabfrage für WebPart](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Verwenden Sie in Internet Explorer auf der Registerkarte **Netzwerk** der F12-Entwicklertools die Details für den Antwortheader. Im folgenden Screenshot beträgt der Wert für die **SPRequestDuration** für diese Seite 924 Millisekunden. 
  
![Screenshot mit der Anforderungsdauer von 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** gibt an, wie viel Arbeit auf dem Server ausgeführt wird, um die Seite vorzubereiten. Das Wechseln von Inhalten durch Abfrage Webparts mit Inhalten durch Such-Webparts reduziert die Zeit, die zum Rendern der Seite erforderlich ist, drastisch. Dagegen hat eine Seite mit einem äquivalenten Inhaltssuche-Webpart, der die gleiche Anzahl von Ergebnissen zurückgibt, einen **SPRequestDuration** -wert von 106 Millisekunden, wie in diesem Screenshot gezeigt: 
  
![Screenshot mit der AnforderungsDauer von 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Hinzufügen eines Inhaltssuche-Webparts in SharePoint Online

Das Hinzufügen eines Inhaltssuche-Webparts ähnelt einem Webpart für reguläre Inhaltsabfragen. Weitere Informationen finden Sie im Abschnitt *"Hinzufügen eines Inhaltssuche-Webparts"* unter [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Erstellen der richtigen Suchabfrage für Ihr Inhaltssuche-Webpart

Nachdem Sie ein Inhaltssuche-Webpart hinzugefügt haben, können Sie die Suche verfeinern und die gewünschten Elemente zurückgeben. Ausführliche Anweisungen dazu finden Sie im Abschnitt *"Anzeigen von Inhalten durch Konfigurieren einer erweiterten Abfrage in einem Inhaltssuche-Webpart"* unter [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Tool zum Erstellen und Testen von Abfragen

Ein Tool zum Erstellen und Testen komplexer Abfragen finden Sie im [Suchabfrage Tool](https://sp2013searchtool.codeplex.com/) unter CodePlex. 
  

