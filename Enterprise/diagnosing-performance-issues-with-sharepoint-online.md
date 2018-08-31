---
title: Diagnose von Leistungsproblemen mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: In diesem Artikel wird gezeigt, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mit Internet Explorer-Entwicklertools diagnostizieren können.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540876"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnose von Leistungsproblemen mit SharePoint Online

In diesem Artikel wird gezeigt, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mit Internet Explorer-Entwicklertools diagnostizieren können.
  
Es gibt drei Möglichkeiten, wie Sie erkennen, dass eine Seite auf einer SharePoint Online-Website ein Leistungsproblem bei Anpassungen hat.
  
- Netzwerkmonitor in der F12-Symbolleiste
    
- Vergleich mit einer nicht angepassten Baseline
    
- Metriken eines SharePoint Online-Antwortheaders
    
In diesem Thema wird beschrieben, wie diese Methoden zur diagnose von Leistungsproblemen verwenden. Nachdem Sie sich die Ursache des Problems berechnet haben, können Sie arbeiten an einer Lösung mit den Artikeln zum Verbessern der Leistung von SharePoint, die auf http://aka.ms/tune.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Verwenden Sie die F12-Symbolleiste, um die Leistung in SharePoint Online zu diagnostizieren.
<a name="F12ToolInfo"> </a>

In diesem Artikel wird Internet Explorer 11 verwendet. Die Versionen der F12-Entwicklertools in anderen Browsern haben ähnliche Funktionen, auch wenn sie unter Umständen etwas anders aussehen. Informationen zu den F12-Entwicklertools finden Sie unter:
  
- [Was ist neu in F12-Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Verwenden die F12-Entwicklertools](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Zum Aufrufen der Entwicklertools drücken Sie **F12** und klicken dann auf das WiFi-Symbol: 
 
  
![Screenshot von F12-Entwicklertools (WLAN-Symbol)](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Klicken Sie auf der Registerkarte **Netzwerk** auf die grüne Wiedergabeschaltfläche, um eine Seite zu laden. Das Tool gibt alle Dateien, die der Browser anfordert, zurück, um die angeforderte Seite zu erhalten. Der folgende Screenshot zeigt eine solche Liste. 
  
![Screenshot der Liste der Dateien, die mit einer Seitenanforderung zurückgegeben wurden.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Auf der rechten Seite werden außerdem die Downloadzeiten der Dateien angezeigt, wie in diesem Screenshot dargestellt.
  
![Diagramm, das die Zeit zeigt, die für das Laden der erforderlichen Seiten von SharePoint benötigt wird](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
So wird visuell dargestellt, wie lange die Datei zum Laden brauchte. Die grüne Linie gibt an, wann die Seite vom Browser gerendert werden kann. So erhalten Sie einen schnellen Überblick über die verschiedenen Dateien, die ggf. das Laden von Seiten auf Ihrer Website verlangsamen.

  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Einrichten von nicht angepassten Grundlinie für SharePoint Online
<a name="F12ToolInfo"> </a>

Die beste Möglichkeit zum Ermitteln Ihrer Website Leistung Schwachpunkte ist eine vollständig Out-of-the-Box-Websitesammlung in SharePoint Online einrichten. Auf diese Weise können Sie die verschiedenen Aspekte der Website mit mit keine Anpassung auf der Seite erhalten würden vergleichen. Die OneDrive for Business-Homepage ist ein gutes Beispiel einer separaten Websitesammlung, die wahrscheinlich auf Anpassungen ist.
  
## <a name="viewing-sharepoint-response-header-information"></a>Anzeigen der Informationen im SharePoint-Antwortheader
<a name="F12ToolInfo"> </a>

In SharePoint Online und SharePoint Server 2013 können Sie die an den Browser zurückgesendeten Informationen im Antwortheader für jede Datei anzeigen. Die zwei hilfreichsten Werte für die Diagnose von Leistungsproblemen sind "SPRequestDuration" und "X-SharePointHealthScore":
  
- **SPRequestDuration**
    
    Dies ist die Zeitspanne, die die Verarbeitung der Anforderung auf dem Server dauerte. So können Sie bestimmen, ob die Anforderung sehr umfangreich und ressourcenintensiv ist. Dadurch erhalten Sie optimale Einblicke dahingehend, wie viel Arbeit der Server leistet, um die Seite zu verarbeiten.
    
- **X-SharePointHealthScore**
    
    Dies gibt an, die Auslastung des Servers oder der CPU, auf dem SharePoint-Instanz ausgeführt wird. Diese Zahl zwischen 0 und 10, wobei 0 gibt an, der Server befindet sich im Leerlauf und 10 gibt den Server, ist ausgelastet. Eine HealthScore, die konsistent 9 oder 10 ist möglicherweise eine laufende Leistungsproblem mit dem Server. Eine beliebige andere Zahl gibt an, dass es sich bei diesem Server innerhalb des erwarteten Bereichs arbeitet.
    
 **So zeigen Sie die Informationen des SharePoint-Antwortheaders an**
  
1. Stellen Sie sicher, dass Sie die F12-Tools installiert haben. Weitere Informationen zum Herunterladen und Installation dieser Tools finden Sie unter [Was ist neu in F12-Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. Klicken Sie in den F12-Tools auf der Registerkarte **Netzwerk** auf die grüne Wiedergabeschaltfläche, um eine Seite zu laden. 
    
3. Klicken Sie auf eine der vom Tool zurückgegebenen ASPX-Dateien, und klicken Sie dann auf **DETAILS**. 
    
    ![Zeigt Details des Antwortheaders](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Klicken Sie auf **Antwortheader**. 
    
    ![Diagramm mit der URL des Antwortheaders](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Was verursacht Leistungsprobleme in SharePoint Online?
<a name="F12ToolInfo"> </a>

Im Artikel [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) zeigt ein Beispiel der Verwendung des SPRequestDuration Werts zum feststellen, dass die komplizierte strukturelle Navigation auf die Seite, um eine lange dauern auf dem Server verarbeitet verursacht wurde. Über den Wert für eine Website Baseline (ohne Anpassung), ist es möglich, festzustellen, ob eine bestimmte Datei geladen lange ist. Das Beispiel aus der [Optionen für die Websitenavigation für SharePoint Online](navigation-options-for-sharepoint-online.md) ist der wichtigste ASPX-Datei. Diese Datei enthält die meisten der ASP.NET-Code, der für Ihre Laden der Seite ausgeführt wird. Abhängig von der Websitevorlage, die Sie verwenden, kann dies start.aspx, home.aspx, default.aspx oder einen anderen Namen handeln, wenn Sie die Homepage anpassen. Wenn diese Nummer erheblich höher ist als der Baseline-Website ist, ist es ein guter Hinweis darauf, den es etwas komplex sein und sollte ist auf der Seite, die Leistungsprobleme verursacht. 
  
Nachdem Sie ein spezielles Problem mit Ihrer Website identifiziert haben, sollten Sie herausfinden, wodurch die Leistungseinbußen verursacht werden. So können Sie alle möglichen Ursachen beseitigen, z. B. Seitenanpassungen, und die einzelnen Anpassungen dann wieder nacheinander zur Website hinzufügen. Nachdem Sie so viele Anpassungen entfernt haben, dass die Seite wieder gut funktioniert, können Sie bestimmte Anpassungen wieder einzeln hinzufügen.
  
Wenn Sie beispielsweise über eine sehr komplexe Navigation verfügen, versuchen Sie, die Navigation so zu ändern, dass keine Unterwebsites angezeigt werden. Überprüfen Sie dann in den Entwicklertools, ob dies einen Unterschied macht. Oder wenn eine große Menge an Inhaltrollups vorhanden ist, entfernen Sie sie von Ihrer Seite, und schauen Sie, ob sich die Leistung dadurch verbessert. Wenn Sie alle der möglichen Ursachen beseitigen und die Elemente einzeln wieder hinzufügen, können Sie leicht herausfinden, welche Merkmale am problematischsten sind, und eine Lösung finden. 

  

