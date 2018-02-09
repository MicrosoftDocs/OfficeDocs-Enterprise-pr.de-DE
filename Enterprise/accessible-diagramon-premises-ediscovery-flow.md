---
title: "Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Lokaler eDiscovery-Datenfluss“."
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss

**Zusammenfassung:** Dieser Artikel ist eine Version verfügbaren Text des Diagramms mit dem Namen der lokale eDiscovery Flow.
  
Dieses Poster bietet Details zu Architektur und Datenfluss bei Serverprodukten. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>SharePoint, Exchange, Lync und Dateifreigaben

Das Diagramm zeigt die einen Benutzer sendet eine Abfrage, die auf zwei Serverfarmen, einer SharePoint 2013 Enterprise-App-Farm und einer SharePoint 2013-Dienstfarm zugreift. SharePoint 2013-Services-Farm kommuniziert mit einer SharePoint 2013-Inhalt Farm, Exchange Server 2013 (die mit Lync 2013 kommuniziert), und Windows-Dateifreigaben. 
  
In der eDiscovery-Ablaufliste werden der Datenfluss und die Reihenfolge beschrieben, in der Abfrageaktionen von eDiscovery in SharePoint, Exchange, Lync und Dateifreigaben erfolgen.  
  
Die eDiscovery-Ablaufliste wird zuerst detailliert beschrieben. Danach folgt eine detaillierte Beschreibung der im Diagramm abgebildeten Features.  
  
### <a name="ediscovery-flow-list"></a>eDiscovery-Ablaufliste

Die Zahlen für die einzelnen in der Liste beschriebenen Schritte gehören zu einem im Diagramm abgebildeten Schritt. Das Diagramm wird weiter unten in diesem Dokument ausführlich beschrieben.  
  
1. eDiscovery-Fälle werden erstellt, verwaltet und in das eDiscovery Center (EDC) verwendet. Das EDC ist eine SharePoint 2013-Websitesammlung. Dies ist, in dem Fällen definiert sind, Quellen nachverfolgt werden erkannt werden, Abfragen werden ausgegeben, Abfrageergebnisse werden überprüft und Haltebereiche auf Inhalt platziert oder entfernt werden. 
    
2. Die eDiscovery-Abfrage oder eine Aktion wie etwa Ort einer Warteschleife, ReleaseHold oder GetStatus, wird an den Proxy (Search Service Application, SSA) in der Enterprise-App-Farm aus der EDC weitergeleitet. Der SSA Proxy leitet dann den Datenverkehr, der die SSA in der App-Services-Farm weiter. In diesem Beispiel wird in den Dateinamen in der Warteschleife Anforderung alles in der SharePoint-Inhaltsfarm mit "CONTOSO" platziert ist. 
    
3. Wenn die Anforderung vorsieht, einen Fall abzufragen, konsultiert die Suchdienstanwendung den Suchindex. Dann wird das Resultset der eDiscovery-Abfrage über das EDC an den Benutzer zurückgegeben.  
    
4. Wenn die Anforderung einer Aktion wie etwa eine Warteschleife oder ReleaseHold, Ort ist wird diese Aktion in der Actions_Table in der administrativen SSA Datenbank geschrieben. In diesem Beispiel wird eine Anforderung Haltestatus für alle in der SharePoint-Inhaltsfarm mit "CONTOSO" in die Actions_Table geschrieben. 
    
5. In regelmäßigen Abständen wird der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher der Inhaltsfarm aktiviert, der eine Anforderung ausstehender Aktionen generiert und Statusaktualisierungen über den SSA-Proxy an die SSA sendet.  
    
6. Die Abfrage für Ausstehende Aktionen ist an der zentralen SSA weitergeleitet, die die Action_Table für alle ausstehenden Aktionen für die Inhaltsfarm konsultiert. Der Inhaltsfarm Compliance-Archiv-Zeitgeberauftrag sendet auch statusaktualisierungen für Objekte und Aktionen, die sie erhalten hat, die in die ActionsTable geschrieben werden. 
    
7. Die Anforderung Haltestatus für alle Inhalte mit "CONTOSO" in den Namen in der SharePoint 2013 Inhalte Farm wird durch die SSA an den eDiscovery-Compliance-Archiv-Zeitgeberauftrag in der Farm Inhalte gesendet. 
    
8. Die eDiscovery-Compliance-Archiv Timer Job-Orte, halten Sie die "CONTOSO-Website" und "CONTOSO Content" auf. 
    
9. Der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher wird in der Unternehmens-App-Farm regelmäßig ausgeführt, um den Status von Ermittlungsaktionen zu prüfen und zu aktualisieren.  
    
10. Die Statusabfrage wird über den Proxy der Suchdienstanwendung der Unternehmens-App-Farm an die Suchdienstanwendung der SharePoint Services-Farm weitergeleitet.  
    
11. Die Suchdienstanwendung ruft den Status der Tabelle „Actions“ ab und gibt ihn an den Zeitgeberauftrag in der Unternehmens-App-Farm zurück, die die Statusaktualisierungen per Push-Verfahren in das EDC überträgt.  
    
12. Wenn ist der Benutzer eDiscovery-Suche (oder Ausführen einer Aktion) für Exchange-Quellen, wie ein Postfach oder archivierten Lync-Inhalten, die Zentraladministration SSA Proxy Abfrage Exchange-Webdienste (Exchange Web Services, EWS) verwendet. Exchange verfügt über eine eigene Such- und eDiscovery-Infrastruktur und alle eDiscovery Anrufe intern verwaltet. 
    
13. Exchange-Webdienste antwortet der Suchdienstanwendung mit eDiscovery-Suchergebnissen oder einer Antwort auf eine Statusanforderung eines abfragebasierten Archivs, das wiederum an das EDC weitergeleitet wird.  
    
#### <a name="prerequisites"></a>Voraussetzungen

- Die SharePoint-Unternehmenssuche muss konfiguriert sein, Inhaltsquellen (SharePoint- und Windows-Dateifreigaben) müssen erfolgreich durchforstetet werden, und alle Inhaltsquellen müssen sich im Index befinden.  
    
- Die Server-zu-Server-Vertrauensstellung und -Authentifizierung muss zwischen der SharePoint Services-Farm und Exchange sowie zwischen Exchange und Lync konfiguriert sein.  
    
### <a name="description-of-components-in-the-diagram"></a>Beschreibung der im Diagramm dargestellten Komponenten

Das Diagramm zeigt einen Benutzer eine Abfrage, wodurch greift auf zwei Serverfarmen einer SharePoint 2013 Enterprise-App-Farm und einer SharePoint 2013-Dienstfarm senden. Der SharePoint Services-Farm mit einer SharePoint 2013 Inhalte Farm Exchange Server 2013 (welche mit Lync 2013 Schnittstellen), Schnittstellen und Windows-Dateifreigaben. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 Enterprise-App-Farm

SharePoint 2013 Enterprise-App-Farm enthält die folgenden Komponenten: 
  
- EDC
    
- SSA-Proxy  
    
- Zeitgeberauftrag 
    
Eine Abfrage oder eine Aktion, die vom Benutzer gesendet wird, wird an das EDC in der Unternehmens-App-Farm gesendet. Es geschieht Folgendes:  
  
- Die Abfrage oder die Aktion wird an den SSA-Proxy übermittelt.  
    
- Der SSA-Proxy sendet eine Statusabfrage oder -antwort an den Zeitgeberauftrag in der Unternehmens-App-Farm. Zudem sendet er eine Statusabfrage oder -antwort an den SSA-Dienst in der SharePoint Services-Farm. Die Aktionen, die sich hieraus ergeben, werden im Abschnitt über die SharePoint Services-Farm beschrieben.  
    
- Wenn der Zeitgeberauftrag eine Antwort erhält, sendet er diese an den SSA-Proxy und das EDC.  
    
- Ergebnisse der Abfrage oder Aktion werden aus dem EDC an den Benutzer gesendet.  
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint 2013-Dienstefarm

SharePoint 2013-Services-Farm enthält die folgenden Komponenten: 
  
- SSA-Dienst  
    
- Suchindexdatenbank  
    
- SSA Admin_db-Datenbank. Die Tabelle Aktionen in dieser Datenbank enthält: Halten Version halten GetStatus 
    
- EWS-Proxy  
    
Wenn der SSA-Proxy in der SharePoint-Unternehmens-App-Farm eine Statusabfrage an die SSA in der SharePoint Services-Farm sendet, geschieht Folgendes:  
  
- Wenn die Anforderung eine Abfrage ist, konsultiert die Suchdienstanwendung den Suchindex. Die Antwort der Ermittlung wird an die SSA und dann über das EDC an den Benutzer zurückgegeben.  
    
- Wenn die Anforderung eine Schreibaktion ist, sendet der SSA-Dienst die Schreibaktion an die Verwaltungsdatenbank der Suchdienstanwendung.  
    
- Eine Durchforstung und reagiert Ergebnisse Anforderung wird an der SharePoint 2013 Inhalte Farm aus der SSA gesendet und eine Antwort wird an die SSA zurückgegeben. 
    
- Eine Anforderung für Durchforstung und Antwortergebnisse wird von der SSA an die Windows-Dateifreigaben gesendet, und eine Antwort wird an die SSA zurückgegeben.  
    
- Eine Abfrage für ausstehenden Aktion(en), Antworten oder Statusaktualisierungen wird von der SSA an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet, und eine Antwort wird an die SSA zurückgegeben.  
    
- Eine Aktions-/Statusanforderung von Exchange wird von der SSA an den EWS-Proxy gesendet, der eine Aktions-/Statusanforderung für eine Exchange-Abfrage an den Exchange-Webdienst auf dem Exchange 2013-Server sendet.   
    
- Eine Statusabfrage/-antwort wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben.  
    
- Eine Abfrage/Antwort für eine ausstehende Aktion wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben.  
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013 Inhalte Farm

Der SharePoint 2013 Inhalte Farm enthält die folgenden Komponenten: 
  
- SSA-Proxy  
    
- Zeitgeberauftrag 
    
- Contoso SharePoint-Website  
    
- Contoso SharePoint-Inhalte  
    
Wenn die SSA in der SharePoint Services-Farm eine Statusabfrage an den SSA-Proxy in der SharePoint-Inhaltsfarm sendet, geschieht Folgendes:  
  
- Der SSA-Proxy in der SharePoint-Inhaltsfarm sendet eine Abfrage für ausstehende Aktionen/Statusantwort an den Zeitgeberauftrag.  
    
- Der Zeitgeberauftrag sendet eine Anforderung an die Contoso SharePoint-Website, die die Contoso SharePoint-Inhalte überprüft.  
    
- Die Antwort auf die Abfrage der ausstehenden Aktionen/Statusabfrage wird von dem Zeitgeberauftrag an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet. Anschließend wird sie an den SSA-Dienst in der SharePoint Services-Farm gesendet.  
    
#### <a name="exchange-2013"></a>Exchange 2013

Die Exchange 2013-Serverkomponente enthält den Exchange-Webdienst und bietet Folgendes:  
  
- Server-zu-Server-Vertrauensstellung/OAuth wird zwischen der SharePoint 2013 Inhalte Farm und Exchange 2013 behandelt. 
    
- Server-zu-Server-Vertrauensstellung/OAuth erfolgt zwischen Exchange 2013 und Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

Die Lync 2013-Komponente archiviert Lync-Inhalte in Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Windows-Dateifreigaben

Die Windows-Dateifreigaben-Komponente stellt Durchforstungsergebnisse für die SSA in der SharePoint Services-Farm bereit.  
  
### <a name="legend"></a>Legende

Die Legende für dieses Diagramm enthält eine grafische Darstellung der verschiedenen zwischen den Komponenten gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben:  
  
- Hell blauen Linie: Abfragevorgang - eDiscovery-Abfrage oder eine Aktion Daten 
    
- Orangefarbene Linie: eDisovery Antwort - Antwort eDiscovery-Abfragen von Daten 
    
- Grüne Linie: Status-Abfrage/Antwort - eDiscovery-Abfrage/Antwort-Statusdaten 
    
- Violett Linie: Exchange-Aktion/Status Anforderung - eDiscovery-Anforderung für den Status der Aktion für den Exchange-Datenverkehr. 
    
- Rote Linie: Exchange Datenstatus/Antwort - eDiscovery-Abfrage oder Status Antwort vom Exchange. 
    
- Gepunktete schwarze Linie: Server-zu-Server-Vertrauensstellung/OAuth  
    
- Durchgezogene schwarze Linie: Durchforstung/Ergebnisse  
    

