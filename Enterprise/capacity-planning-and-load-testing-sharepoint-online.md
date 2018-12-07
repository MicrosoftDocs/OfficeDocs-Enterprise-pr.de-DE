---
title: Capacity planning und Auslastungstests SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Dieser Artikel beschreibt, wie Sie bereitstellen können mit SharePoint Online ohne herkömmlichen Auslastungstests, da es nicht zulässig ist.
ms.openlocfilehash: 6a22ee089adc0817f5c52bbfee5f2b41d7e5d80c
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181026"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Capacity planning und Auslastungstests SharePoint Online

Dieser Artikel beschreibt, wie Sie bereitstellen, können mit SharePoint Online ohne herkömmlichen Auslastungstests, da Auslastungstests abgeraten wird.
  
Obwohl active Auslastungstests SharePoint Online wird nicht empfohlen, es einige andere Möglichkeiten, den, die Sie Folgendes sicherstellen können, erzeugt eine Website nicht benutzerfreundlich beim Starten der Website. 
  
Mit SharePoint Online müssen Sie kapazitätsplanung, wie dies für Sie als Teil des unser Serviceangebot. Mit lokalen Umgebungen Auslastungstests wird horizontal Annahme überprüfen und letztlich suchen die neueste Punkt einer Farm. durch eine es mit Last. Mit SharePoint Online muss anders Dinge. Wird eine Umgebung mit mehreren Mandanten, haben wir schützen Sie alle Mandanten in der gleichen Farm aus, damit es keine Auslastungstests automatisch gedrosselt wird. Dies bedeutet, dass Sie erhalten enttäuschend und potenziell irreführende Ergebnisse, wenn Sie versuchen, laden Testen Ihrer Umgebung.
  
Eines der wichtigsten Vorteile von SharePoint Online über eine lokale Bereitstellung ist der Elastizität der Cloud. Unsere großen Umgebung eingerichtet ist mit Millionen von Benutzern auf täglicher Basis-Dienst so wichtig ist, dass wir Kapazität effektiv behandeln, indem Sie die Farmen, automatisch angepasst wird, wie und, falls erforderlich. In diesem Artikel wird erläutert, wie wir für Kapazitätswachstum und einem festen Maßstab planen Out vorhanden. Der Artikel behandelt auch Ansätze für die Verwendung von, an denen Auslastungstests nicht beteiligt.
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a>Wie Office 365 prognostiziert laden und erweitert Kapazität

SharePoint Online Server Capacity Management Arbeit erfolgt über zwei Methoden:
  
- Kapazität-Planung
    
- Netzwerklastenausgleich auf einzelnen Serverfarmen
    
Anders als bei der Planung einer lokalen Umgebung für die Kapazität in SharePoint Online-Planung können wir Statistiken sowie grafisch potenzielle Anforderungen in keiner bestimmten Server-Gruppe. Der aggregierte bei Bedarf sieht etwa die Anforderungen in der Zone (wobei für eine Zone ist eine Gruppe von SharePoint-Farmen) Wachstum Zeile in der folgenden Abbildung:
  
![Diagramm der vorhergesagten Kapazität: Prognose](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
Während das Wachstum in jeder Farm eine unvorhersehbare befindet, ist die aggregierte Summe von Anforderungen in einer Zone vorhersehbar. Durch die Ermittlung der geometrischen Trends in SharePoint Online, können wir für die zukünftige Erweiterung planen.
  
Um effizient Kapazität verwenden und befassen sich mit der unerwartete Zunahme jede Farm haben wir die Automatisierung, Front-End-System verfolgt und bei Bedarf von direkten, skaliert. Die wichtigste Metrik, die wir verwenden, wie ein Signal zum Skalieren von Front-ends ist CPU-Auslastung. Unser Ziel ist es, die CPU-Belastung weniger als 40 % zu halten. Dies ist, um genügend Puffer zu unerwarteten Spitzen kompensieren zu lassen. Load Ansätze 40 % im stabilen Zustand fügen wir front-Ends Farmen hinzu.
  
![Diagramm der vorhergesagten Kapazität: Verwalten von Farmen](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
Zusätzliche Server können schnell zu einer Farm, mit denen, die zuvor durch die Planung Syntax der Zone hinzugefügt wurden hinzugefügt werden. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>Wie plane ich für eine Website starten?

Sie sollten erwarten, dass die Farm, auf der die neue Website startet, automatisch überwacht werden, sodass neue Front-End-Server hinzugefügt werden, wie oben beschrieben. Aus diesem Grund benötigen nicht wir keine Benachrichtigung für die neue Website starten.
  
Weitere bewährten Methoden für eine einzelne Seite auf SharePoint Online ist es unwahrscheinlich, dass eine neue Website zu öffnen, auch 100.000 Benutzer alle in der Farm auswirken.
  
Es gibt einige Strategien zum Planen einer Version einer neuen SharePoint Online-Website. Wie in der folgenden Abbildung gezeigt, ist die Anzahl von Benutzern, die eingeladen werden häufig deutlich höher ist als die, die die Website zu verwenden. Diese Abbildung zeigt eine Strategie zur Verwendung einer Version Rollout. Diese Methode ist nicht nur nützlich, um zu Leistung beim Laden jedoch auch kann identifizieren Möglichkeiten zur Verbesserung der SharePoint-Website, bevor die Mehrzahl der Benutzer angezeigt wird.
  
![Diagramm der eingeladenen und aktiven Benutzer](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
In der Pilotphase Geschäftsobjekts Feedback von Benutzern zu erhalten, dass die Organisation vertraut und weiß anderweitig werden sollen. Auf diese Weise ist es möglich, wie das System verwendet wird und wie es ausgeführt wird, zu ermitteln.
  
Danach beginnt für alle Benutzer in hochrangige Rollout; Einholen von Feedback und die Leistung regelmäßig zu überprüfen. Dies hat den Vorteil langsam Einführung in das System und bei dessen Verbesserung, wenn das System Weitere verwendet wird. Dadurch können auch auf die erhöhte Last zu reagieren, wie die Website für mehr Benutzer eingeführt.
  
Schließlich während Auslastungstests nicht zulässig sind, können Kunden regelmäßige Ping an den Dienst Measure Verfügbarkeit und Latenz einrichten möchten. Identifizieren dieses Grundlinie für ihre Website. Allerdings müssen diese geringe Häufigkeit Drosselung zuvor beschriebenen Probleme vermieden aufbewahrt werden.
  

