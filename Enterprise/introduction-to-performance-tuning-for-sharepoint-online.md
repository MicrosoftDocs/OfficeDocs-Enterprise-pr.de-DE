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
description: In diesem Artikel wird erläutert, welche bestimmter Aspekte, die Sie beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigen müssen.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219875"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Einführung in die Leistungsoptimierung für SharePoint Online

In diesem Artikel wird erläutert, welche bestimmter Aspekte, die Sie beim Entwerfen von Seiten für eine optimale Leistung in SharePoint Online berücksichtigen müssen.
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online-Metriken

Die folgenden umfassenden Metriken für SharePoint Online liefern reale Leistungsdaten:
  
- Wie schnell Seiten geladen werden
    
- Wie viele Roundtrips pro Seite erforderlich sind
    
- Probleme mit dem Dienst
    
- Andere Aspekte, die zu Leistungseinbußen führen
    
### <a name="conclusions-reached-because-of-the-data"></a>Schlussfolgerungen aufgrund der Daten

Den Daten können wir Folgendes entnehmen:
  
- Die meisten Seiten zeigen auf SharePoint Online eine gute Leistung.
    
- Nicht angepasste Seiten werden sehr schnell geladen.
    
- OneDrive for Business, Teamwebsites und Systemseiten, z. B. "_layouts" usw., lassen sich alle schnell laden.
    
- Die langsamsten 1 % der SharePoint Online-Seiten brauchen mehr als 5.000 Millisekunden zum Laden.
    
Ein einfacher Benchmarktest wäre, die Leistung durch Vergleichen der Ladezeit Ihres eigenen Portals mit der Ladezeit der OneDrive for Business-Homepage zu messen, da sie wenig benutzerdefinierte Funktionen verwendet. Dies ist oft der erste Schritt, um den Sie vom Support gebeten werden, wenn es um die Behandlung von Problemen mit der Netzwerkleistung geht.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Verwenden Sie ein standard-Benutzerkonto, bei der Leistung

Ein Websitesammlungsadministrator, Websitebesitzer, Editor oder Mitwirkender kann zusätzliche Sicherheitsgruppen angehören, sind zusätzliche Berechtigungen und aus diesem Grund haben weitere Elemente, die SharePoint auf einer Seite geladen wird.
  
Dies gilt für die lokale SharePoint- und SharePoint Online, aber in einem Szenario: lokal die Unterschiede werden nicht so einfach bemerkt wie in SharePoint Online.
  
Um ordnungsgemäß bewerten, wie eine Seite für Benutzer ausgeführt wird, sollten Sie ein standard-Benutzerkonto verwenden, um zu vermeiden, laden das Schreiben von Steuerelementen und zusätzlichen Datenverkehr im Zusammenhang mit Sicherheitsgruppen.
  
## <a name="connection-categories-for-performance-tuning"></a>Verbindungskategorien für die Leistungsoptimierung

Die Verbindungen zwischen Server und Benutzer lassen sich in drei Hauptkomponenten unterteilen. Berücksichtigen Sie diese beim Entwerfen von SharePoint Online-Seiten, um Einblicke in die Ladezeiten zu erhalten.
  
- **Server** Die Server, dass Microsoft in Rechenzentren hostet.
    
- **Netzwerk** Microsoft Network, dem Internet und Ihrem lokalen Netzwerk zwischen dem Rechenzentrum und Ihre Benutzer.
    
- **Browser** In dem die Seite geladen wird.
    
Im Zusammenhang mit diesen drei Verbindungen gibt es in der Regel fünf Gründe, die 95 % der langsamen Seiten verursachen. Jeder dieser Gründe wird in diesem Artikel erläutert:
  
- Probleme bei der Navigation
    
- Rollup von Inhalten
    
- Große Dateien
    
- Viele Anforderungen an den Server
    
- Verarbeitung von Webparts
    
### <a name="server-connection"></a>Serververbindung

Viele der Probleme, die die Leistung einer lokalen SharePoint-Implementierung beeinflussen, gelten auch für SharePoint Online.
  
Erwartungsgemäß verfügen Sie bei einer lokalen SharePoint-Implementierung über weitaus mehr Kontrolle über die Leistung der Server. Bei SharePoint Online ist das ein wenig anders. Je mehr Arbeit Sie einen Server machen lassen, desto länger dauert das Rendern einer Seite. Bei Share Point liegt das zum größten Teil an komplexen Seiten mit mehreren Webparts.
  
SharePoint Server lokal
  
![Screenshot von Server lokal](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Screenshot von Server online](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Bei SharePoint Online kann es vorkommen, dass bestimmte Seitenanforderungen am Ende mehrere Server aufrufen. So kann es zu einer Kombination aus Anforderungen zwischen Servern für nur eine Anforderung kommen. Diese Interaktionen können die Leistung beim Laden von Seiten stark beeinträchtigen.
  
Beispiele für diese Server-zu-Server-Interaktionen sind:
  
- Web- zu SQL-Servern
    
- Web- zu Anwendungsservern
    
Ein weiterer Faktor, der die Serverinteraktionen verlangsamen kann, sind Cachefehler. Im Gegensatz zum lokalen SharePoint besteht die sehr geringe Möglichkeit, dass der gleiche Server für eine Seite verwendet wird, die Sie zuvor besucht haben. Dies führt dazu, dass eine Objektzwischenspeicherung veraltet.
  
### <a name="network-connection"></a>Netzwerkverbindung

Mit lokalen SharePoint nicht, die über ein WAN nutzen, können Sie eine schnelle Verbindung zwischen Datacenter und Endbenutzern verwenden. Im Allgemeinen Dinge einfach, aus der Sicht Netzwerk zu verwalten.
  
Bei SharePoint Online gibt es einige weitere Faktoren, die berücksichtigt werden müssen, zum Beispiel:
  
- Das Microsoft-Netzwerk
    
- Das Internet
    
- Der Internetdienstanbieter
    
Unabhängig davon, welche Version von SharePoint (und welches Netzwerk) Sie verwenden, können folgende Faktoren dazu führen, dass das Netzwerk ausgelastet ist:
  
- Große Nutzlast
    
- Viele Dateien
    
- Große physische Entfernung zum Server
    
Eine Funktion, die Sie in SharePoint Online nutzen können ist dem Microsoft CDN (Content Delivery Network). Ein CDN ist im Wesentlichen eine verteilte Sammlung von Servern, die in mehreren Rechenzentren bereitgestellt. Mit einem CDN kann Inhalte auf Seiten auf einem Server in der Nähe des Clients gehostet werden, selbst wenn der Client weit weg von der SharePoint-Ausgangsserver ist. Microsoft wird dieses Thema in der Zukunft verwenden, um lokale Instanzen von Seiten, die nicht angepasst werden können, beispielsweise der SharePoint Online Admin Homepage gespeichert. Weitere Informationen zu CDNs finden Sie unter [Inhaltsübermittlung](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).
  
Etwas, das Sie berücksichtigen müssen, aber möglicherweise nicht großartig beeinflussen können, ist die Verbindungsgeschwindigkeit des Internetdienstanbieters. Mit einem einfachen Tool zum Testen der Geschwindigkeit können Sie die Verbindungsgeschwindigkeit messen.
  
### <a name="browser-connection"></a>Browserverbindung

Es gibt einige Faktoren, die hinsichtlich der Leistung bei Webbrowsern zu berücksichtigen sind.
  
Besuchen komplexe Seiten wird die Leistung beeinträchtigen. Den meisten Browsern haben nur einen kleinen Cache (etwa 90MB), während der Durchschnitt Webseite ist in der Regel rund um 1,6 MB. Nicht dauert aufgebraucht lange.
  
Bandbreite sein ein Problem auch. Beispielsweise wenn ein Benutzer in einer anderen Sitzung sich Videos ansehen ist, wirkt die Leistung Ihrer SharePoint-Seite sich dies. Während Sie streaming Media verhindert, dass Benutzer ist nicht möglich, können Sie die Möglichkeit für Benutzer eine Seite lädt steuern.
  
Checken Sie die folgenden Artikel für verschiedene SharePoint Online Seite Anpassungsmethoden und andere empfohlene Vorgehensweisen können Sie eine optimale Leistung zu erzielen.
  
- [Navigationsoptionen für SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Verwenden Sie das Seite-Diagnosetool für SharePoint Online](page-diagnostics-for-spo.md)
    
- [Bildoptimierung für SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Verzögerung beim Laden von Bildern und JavaScript in SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimierung und Bündelung in SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Verwenden von Netzwerken für die Inhaltsübermittlung](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Über Inhaltssuche-Webpart anstatt Webpart für Inhaltsabfragen zum Verbessern der Leistung in SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Capacity planning und Auslastungstests SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnose von Leistungsproblemen mit SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Verwenden des Objektcaches mit SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Gewusst wie: Vermeiden von Drosselung und Sperren in SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

