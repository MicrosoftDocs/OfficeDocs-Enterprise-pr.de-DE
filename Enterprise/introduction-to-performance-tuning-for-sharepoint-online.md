---
title: Einführung in die Leistungsoptimierung für SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: In diesem Artikel wird erläutert, welche Aspekte beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigt werden müssen.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487161"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Einführung in die Leistungsoptimierung für SharePoint Online

In diesem Artikel wird erläutert, welche Aspekte beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigt werden müssen.
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online-Metriken

Die folgenden allgemeinen Metriken für SharePoint Online bieten reale Daten zur Leistung:
  
- Wie schnelle Seiten geladen werden
    
- Wie viele Roundtrips pro Seite erforderlich sind
    
- Probleme mit dem Dienst
    
- Andere Aspekte, die zu Leistungsbeeinträchtigungen führen
    
### <a name="conclusions-reached-because-of-the-data"></a>Schlussfolgerungen aufgrund der Daten

Die Daten teilen uns Folgendes mit:
  
- Die meisten Seiten werden in SharePoint Online gut ausgeführt.
    
- Nicht angepasste Seiten werden sehr schnell geladen.
    
- OneDrive for Business, Teamwebsites und System Seiten wie _layouts usw. sind alle schnell zu laden.
    
- Die langsamsten 1% der SharePoint Online-Seiten benötigen mehr als 5.000 Millisekunden.
    
Ein einfacher Benchmark-Test, den Sie verwenden können, wäre das Messen der Leistung, indem die Ladezeit des eigenen Portals mit der Ladezeit der OneDrive for Business-Startseite verglichen wird, da nur wenige angepasste Features verwendet werden. Dies ist häufig der erste Schritt, den Sie beim Beheben von Problemen mit der Netzwerkleistung bei der Unterstützung durchführen müssen.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Verwenden eines Standardbenutzerkontos beim Überprüfen der Leistung

Ein Website Sammlungs Administrator, Websitebesitzer, Editor oder mitWirkender gehört zu zusätzlichen Sicherheitsgruppen, verfügt über zusätzliche Berechtigungen und verfügt daher über zusätzliche Elemente, die SharePoint auf einer Seite lädt.
  
Dies gilt für SharePoint on-premises und SharePoint Online, aber in einem lokalen Szenario sind die Unterschiede nicht so leicht zu erkennen wie in SharePoint Online.
  
Um zu ermitteln, wie eine Seite für Benutzer ausgeführt wird, sollten Sie ein Standardbenutzerkonto verwenden, um die Erstellungs Steuerelemente und den zusätzlichen Datenverkehr im Zusammenhang mit Sicherheitsgruppen zu vermeiden.
  
## <a name="connection-categories-for-performance-tuning"></a>Verbindungskategorien für die Leistungsoptimierung

Sie können die Verbindungen zwischen dem Server und dem Benutzer in drei Hauptkomponenten kategorisieren. Berücksichtigen Sie diese beim Entwerfen von SharePoint Online-Seiten für Einblicke in Ladezeiten.
  
- **Server** Die Server, die Microsoft in Rechenzentren hostet.
    
- **Netzwerk** Das Microsoft-Netzwerk, das Internet und Ihr lokales Netzwerk zwischen dem Rechenzentrum und ihren Benutzern.
    
- **Browser** Wo die Seite geladen wird.
    
Innerhalb dieser drei Verbindungen gibt es normalerweise fünf Gründe, die 95% der langsamen Seiten verursachen. Jeder dieser Gründe wird in diesem Artikel behandelt:
  
- Navigationsprobleme
    
- Inhalts Rollup
    
- Umfangreiche Dateien
    
- Viele Anforderungen an den Server
    
- Webpart-Verarbeitung
    
### <a name="server-connection"></a>Server Verbindung

Viele der Probleme, die sich auf die Leistung mit SharePoint lokal auswirken, gelten auch für SharePoint Online.
  
Wie Sie erwarten, haben Sie weitaus mehr Kontrolle darüber, wie Server mit lokalem SharePoint ausgeführt werden. Bei SharePoint Online sind die Dinge etwas anders. Je mehr Arbeit Sie an einem Server vornehmen, desto länger dauert das Rendern einer Seite. Bei SharePoint ist der größte Übeltäter in dieser Hinsicht komplexe Seiten mit mehreren Webparts.
  
SharePoint Server lokal
  
![Screenshot des lokalen Servers](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Screenshot von Server Online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Bei SharePoint Online können bestimmte Seitenanforderungen tatsächlich mehrere Server anrufen. Sie können eine Matrix von Anforderungen zwischen Servern für eine einzelne Anforderung erhalten. Diese Interaktionen sind aus der Seiten Lade Perspektive teuer und machen die Dinge langsam.
  
Beispiele für diese Server-zu-Server-Interaktionen sind:
  
- Web-zu-SQL-Server
    
- Webserver für Anwendungsserver
    
Das andere, was die Serverinteraktionen verlangsamen kann, sind Cachefehler. Im Gegensatz zu lokalen SharePoint, gibt es eine sehr geringe Wahrscheinlichkeit, dass Sie den gleichen Server für eine Seite getroffen haben, die Sie zuvor besucht haben; Dadurch ist das Objekt Zwischenspeichern veraltet.
  
### <a name="network-connection"></a>Netzwerkverbindung 

Bei der lokalen SharePoint-Anwendung, die kein WAN verwendet, können Sie eine Hochgeschwindigkeitsverbindung zwischen Datencenter und Endbenutzern verwenden. Im Allgemeinen ist die Verwaltung über eine Netzwerk Perspektive einfach.
  
Bei SharePoint Online gibt es einige weitere Faktoren, die berücksichtigt werden müssen. Zum Beispiel:
  
- Das Microsoft-Netzwerk
    
- Das Internet
    
- Der ISP
    
Unabhängig davon, welche Version von SharePoint (und welches Netzwerk) Sie verwenden, können die folgenden Aspekte in der Regel dazu führen, dass das Netzwerk ausgelastet ist:
  
- Hohe Nutzlast
    
- Viele Dateien
    
- Grosser physischer Abstand zum Server
    
Ein Feature, das Sie in SharePoint Online nutzen können, ist das Microsoft CDN (Content Delivery Network). Ein CDN ist im Grunde eine verteilte Sammlung von Servern, die über mehrere Rechenzentren bereitgestellt werden. Mit einem CDN können Inhalte auf Seiten auf einem Server in der Nähe des Clients gehostet werden, selbst wenn der Client weit entfernt vom ursprünglichen SharePoint-Server ist. Microsoft verwendet dies künftig mehr, um lokale Instanzen von Seiten zu speichern, die nicht angepasst werden können, beispielsweise die Homepage des SharePoint Online-Administrators. Weitere Informationen zu CDNs finden Sie unter [Content](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)Subnetze.
  
Etwas, das Sie beachten müssen, aber möglicherweise nicht viel zu tun ist, ist die Verbindungsgeschwindigkeit Ihres ISP. Mit einem einfachen Geschwindigkeitstest Tool wird Ihnen die Verbindungsgeschwindigkeit mitgeteilt.
  
### <a name="browser-connection"></a>Browser Verbindung

Es gibt einige Faktoren, die von einer Leistungsperspektive aus mit Webbrowsern berücksichtigt werden sollten.
  
Der Besuch komplexer Seiten wirkt sich auf die Leistung aus. Die meisten Browser haben nur einen kleinen Cache (um 90MB), während die durchschnittliche Webseite normalerweise ungefähr 1,6 MB beträgt. Es dauert nicht lange, bis Sie sich verbraucht haben.
  
Bandbreite kann auch ein Problem sein. Wenn ein Benutzer beispielsweise Videos in einer anderen Sitzung ansieht, wirkt sich dies auf die Leistung Ihrer SharePoint-Seite aus. Sie können zwar nicht verhindern, dass Benutzer Streaming-Medien, aber Sie steuern, wie eine Seite für Benutzer geladen wird.
  
In den folgenden Artikeln finden Sie unterschiedliche Techniken für die SharePoint Online-Seite und andere bewährte Methoden, um eine optimale Leistung zu erzielen.
  
- [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Verwenden des Seiten Diagnosetools für SharePoint Online](page-diagnostics-for-spo.md)
    
- [Bildoptimierung für SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimierung und Bündelung in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Verwenden von Netzwerken für die Inhaltsübermittlung](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Verwenden des Webparts für die Inhaltssuche anstelle des Inhaltsabfrage-Webparts zur Verbesserung der Leistung in SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Kapazitätsplanung und Auslastungstests für SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnose von Leistungsproblemen mit SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Verwenden des Objektcaches mit SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Gewusst wie: Vermeiden von Einschränkungen oder Sperren in SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

