---
title: Diagnose von Leistungsproblemen mit SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: In diesem Artikel erfahren Sie, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mithilfe von Internet Explorer-Entwicklertools diagnostizieren können.
ms.openlocfilehash: dfc66822a98ce26bfd9fd94d9d58882b8b140831
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067861"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnose von Leistungsproblemen mit SharePoint Online

In diesem Artikel erfahren Sie, wie Sie häufige Probleme mit Ihrer SharePoint Online-Website mithilfe von Internet Explorer-Entwicklertools diagnostizieren können.
  
Es gibt drei verschiedene Möglichkeiten, um festzustellen, ob eine Seite auf einer SharePoint Online-Website ein Leistungsproblem mit den Anpassungen aufweist.
  
- Der F12-Tool Balken-Netzwerkmonitor
    
- Vergleich mit einer nicht angepassten Baseline
    
- Metriken für SharePoint Online-Antwortheader
    
In diesem Thema wird beschrieben, wie Sie die einzelnen Methoden zur Diagnose von Leistungsproblemen verwenden. Nachdem Sie die Ursache des Problems herausgefunden haben, können Sie mit den Artikeln zur Verbesserung der Leistung von SharePoint, die Sie finden können, auf http://aka.ms/tuneeine Lösung hinarbeiten.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Verwenden der F12-Symbolleiste zum Diagnostizieren der Leistung in SharePoint Online
<a name="F12ToolInfo"> </a>

In diesem Artikel wird Internet Explorer 11 verwendet. Versionen der F12-Entwicklertools in anderen Browsern weisen ähnliche Features auf, obwohl Sie möglicherweise etwas anders aussehen. Weitere Informationen zu den F12-Entwicklertools finden Sie unter:
  
- [Neuigkeiten in den F12-Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Verwenden der F12-Entwicklertools](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Drücken Sie **F12** , um die Entwicklertools aufzurufen, und klicken Sie dann auf das WLAN-Symbol: 
  
![Screenshot von F12 Developer Tools WiFi-Symbol](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Drücken Sie auf der Registerkarte **Netzwerk** die grüne Wiedergabeschaltfläche, um eine Seite zu laden. Das Tool gibt alle Dateien zurück, die der Browser anfordert, um die von Ihnen gewünschte Seite zu erhalten. Der folgende Screenshot zeigt eine solche Liste. 
  
![Screenshot der Liste der Dateien, die mit einer Seitenanforderung zurückgegeben werden.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Sie können auch die Downloadzeiten der Dateien auf der rechten Seite sehen, wie in diesem Screenshot gezeigt.
  
![Diagramm mit der Zeit, die zum Laden der angeforderten Seiten aus SharePoint benötigt wird](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Dadurch erhalten Sie eine visuelle Darstellung, wie lange die Datei geladen wurde. Die grüne Liniendarstellung zeigt an, wann die Seite vom Browser gerendert werden kann. Auf diese Weise können Sie schnell die verschiedenen Dateien anzeigen, die zu langsamen Seitenlasten auf Ihrer Website führen.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Einrichten einer nicht angepassten Baseline für SharePoint Online
<a name="F12ToolInfo"> </a>

Die beste Möglichkeit, die Leistung Ihrer Website zu schwächen, besteht darin, eine vollständig out-of-the-Box-Websitesammlung in SharePoint Online einzurichten. Auf diese Weise können Sie alle verschiedenen Aspekte Ihrer Website mit dem vergleichen, was Sie ohne Anpassung auf der Seite erhalten würden. Die OneDrive for Business-Startseite ist ein gutes Beispiel für eine separate Websitesammlung, die keine Anpassungen aufweisen kann.
  
## <a name="viewing-sharepoint-response-header-information"></a>Anzeigen von SharePoint-Antwortheader Informationen
<a name="F12ToolInfo"> </a>

In SharePoint Online und SharePoint Server 2013 können Sie auf die Informationen zugreifen, die im Antwortheader für jede Datei an den Browser zurückgesendet werden. Die beiden hilfreichsten Werte für die Diagnose von Leistungsproblemen sind SPRequestDuration und X-SharePointHealthScore:
  
- **SPRequestDuration**
    
    Dies ist die Zeitdauer, die die Anforderung für die Verarbeitung des Servers übernommen hat. Dies kann helfen festzustellen, ob die Anforderung sehr schwer und ressourcenintensiv ist. Dies ist die beste Einblicke in die Menge an Arbeit, die der Server für die Bereitstellung der Seite leistet.
    
- **X-SharePointHealthScore**
    
    Dies gibt die Auslastung des Servers oder der CPU an, auf dem Ihre SharePoint-Instanz ausgeführt wird. Diese Zahl liegt zwischen 0 und 10, wobei 0 angibt, dass der Server inaktiv ist und 10 angibt, dass der Server sehr ausgelastet ist. Ein HealthScore, das konsistent 9 oder 10 ist, kann auf ein ständiges Leistungsproblem mit dem Server hindeuten. Eine beliebige andere Zahl weist darauf hin, dass der Server innerhalb des erwarteten Zeitraums betrieben wird.
    
 **So zeigen Sie SharePoint-Antwortheader Informationen an**
  
1. Stellen Sie sicher, dass die F12-Tools installiert sind. Weitere Informationen zum herunterladen und Installieren dieser Tools finden Sie unter [What es New in F12 Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. Drücken Sie in den F12-Tools auf der Registerkarte **Netzwerk** die grüne Wiedergabeschaltfläche, um eine Seite zu laden. 
    
3. Klicken Sie auf eine der vom Tool zurückgegebenen ASPX-Dateien, und klicken Sie dann auf **Details**. 
    
    ![Zeigt Details des Antwortheaders an.](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Klicken Sie auf **Antwort Kopfzeilen**. 
    
    ![Diagramm mit der URL des Antwortheaders](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Was verursacht Leistungsprobleme in SharePoint Online?
<a name="F12ToolInfo"> </a>

Die Artikel [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) zeigen ein Beispiel für die Verwendung des SPRequestDuration-Werts, um festzustellen, dass die umständliche strukturelle Navigation dazu führte, dass die Verarbeitung der Seite auf dem Server lange dauert. Durch die Verwendung eines Werts für eine Basis Website (ohne Anpassung) kann ermittelt werden, ob eine bestimmte Datei sehr viel Zeit in Anspruch nimmt. Das in den [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md) verwendete Beispiel ist die Hauptdatei. aspx. Diese Datei enthält den größten Teil des ASP.NET-Codes, der für das Laden der Seite ausgeführt wird. Je nach verwendeter Websitevorlage kann dies "Start. aspx", "Home. aspx", "default. aspx" oder ein anderer Name sein, wenn Sie die Homepage anpassen. Wenn diese Zahl deutlich höher als die Baseline-Website ist, ist es ein guter Hinweis darauf, dass auf Ihrer Seite etwas komplexes auftritt, das zu Leistungsproblemen führt. 
  
Nachdem Sie festgestellt haben, dass ein Problem, das für Ihre Website spezifisch ist, wird empfohlen, um herauszufinden, was die Leistung beeinträchtigt, wenn Sie alle möglichen Ursachen wie Seiten Anpassungen beseitigen und diese dann nacheinander wieder zur Website hinzufügen. Nachdem Sie genügend Anpassungen entfernt haben, die von der Seite ausgeführt werden, können Sie eine nach dem anderen wieder hinzufügen.
  
Wenn Sie beispielsweise eine sehr komplexe Navigation haben, versuchen Sie, die Navigation so zu ändern, dass Unterwebsites nicht angezeigt werden, und überprüfen Sie die Entwicklertools, ob dies einen Unterschied macht. Oder wenn Sie über eine Vielzahl von Inhalts-Rollups verfügen, versuchen Sie, Sie von Ihrer Seite zu entfernen, und sehen Sie nach, ob dies etwas verbessert. Wenn Sie alle möglichen Ursachen beseitigen und Sie wieder einzeln hinzufügen, können Sie leicht erkennen, welche Funktionen das größte Problem darstellen, und dann an einer Lösung arbeiten.
  

