---
title: Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: Dieser Artikel ist eine barrierefreie Textversion des Diagramms „Lokaler eDiscovery-Datenfluss“.
ms.openlocfilehash: bdaf46c552b346d0e6966cd3589f239146ddadc5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068531"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Zugängliches Diagramm – Lokaler eDiscovery-Datenfluss

**Zusammenfassung:** Dieser Artikel ist eine barrierefreie Textversion des Diagramms mit dem Namen "on-premises eDiscovery Flow".
  
Dieses Poster bietet Details zu Architektur und Datenfluss bei Serverprodukten. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>SharePoint, Exchange, Lync und Dateifreigaben

Das Diagramm zeigt, wie ein Benutzer eine Abfrage sendet, die auf zwei Serverfarmen, eine SharePoint 2013 Enterprise-App-Farm und eine SharePoint 2013-Dienstfarm zugreift. Die SharePoint 2013 Services-Farm kommuniziert mit einer SharePoint 2013-Inhaltsfarm, Exchange Server 2013 (die mit lync 2013 kommuniziert) und Windows-Dateifreigaben. 
  
In der eDiscovery-Ablaufliste werden der Datenfluss und die Reihenfolge beschrieben, in der Abfrageaktionen von eDiscovery in SharePoint, Exchange, Lync und Dateifreigaben erfolgen.  
  
Die eDiscovery-Ablaufliste wird zuerst detailliert beschrieben. Danach folgt eine detaillierte Beschreibung der im Diagramm abgebildeten Features.  
  
### <a name="ediscovery-flow-list"></a>eDiscovery-Ablaufliste

Die Zahlen für die einzelnen in der Liste beschriebenen Schritte gehören zu einem im Diagramm abgebildeten Schritt. Das Diagramm wird weiter unten in diesem Dokument ausführlich beschrieben.  
  
1. eDiscovery-Fälle werden im eDiscovery Center (EDC) erstellt, verwaltet und verwendet. Die EDC ist eine SharePoint 2013-Websitesammlung. Hier werden Fälle definiert, nachzuverfolgende Quellen bestimmt, Abfragen gestartet, Abfrageergebnisse geprüft und Sperren für Inhalte aktiviert oder aufgehoben. 
    
2. Die eDiscovery-Abfrage oder -Aktion, wie „Im Archiv platzieren“, „ReleaseHold“ oder „GetStatus“, wird vom EDC an den Proxy der Suchdienstanwendung (Search Service Application, SSA) in der App-Farm des Unternehmens weitergeleitet. Der Proxy der Suchdienstanwendung leitet anschließend den Datenverkehr an die SSA in der Dienst-App-Farm weiter. In diesem Beispiel ist die Anforderung, alle Elemente in der SharePoint-Inhalts Farm mit "Contoso" in den zu speichernden Dateinamen zu platzieren. 
    
3. Wenn die Anforderung vorsieht, einen Fall abzufragen, konsultiert die Suchdienstanwendung den Suchindex. Dann wird das Resultset der eDiscovery-Abfrage über das EDC an den Benutzer zurückgegeben.  
    
4. Wenn die Anforderung eine Aktion ist, z. B. „Im Archiv platzieren“ oder „ReleaseHold“, wird diese Aktion in die Tabelle „Actions“ in der Verwaltungsdatenbank der Suchdienstanwendung geschrieben. In diesem Beispiel wird eine Hold-Anforderung für irgendetwas in der SharePoint-Inhalts Farm mit "Contoso" in das Actions_Table geschrieben. 
    
5. In regelmäßigen Abständen wird der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher der Inhaltsfarm aktiviert, der eine Anforderung ausstehender Aktionen generiert und Statusaktualisierungen über den SSA-Proxy an die SSA sendet. 
    
6. Die Abfrage ausstehender Aktionen wird an die zentrale Suchdienstanwendung weitergeleitet, die die Tabelle „Actions“ auf ausstehende Aktionen für die Inhaltsfarm konsultiert. Der Zeitgeberauftrag für den In-Situ-Speicher der Inhaltsfarm sendet außerdem Statusaktualisierungen für empfangene Objekte und Aktionen, die in die Tabelle „Actions“ geschrieben werden. 
    
7. Die Hold-Anforderung für alle Inhalte mit "Contoso" im Namen in der SharePoint 2013-Inhaltsfarm wird von der SSA an den in-situ-Speicher-Zeitgeberauftrag in der Inhaltsfarm gesendet. 
    
8. Der Zeitgeberauftrag für den eDiscovery-in-Place-Speicher platziert die "Contoso-Website" und "Contoso-Inhalte" in der Warteschleife. 
    
9. Der Zeitgeberauftrag für den eDiscovery-In-Situ-Speicher wird in der Unternehmens-App-Farm regelmäßig ausgeführt, um den Status von Ermittlungsaktionen zu prüfen und zu aktualisieren.  
    
10. Die Statusabfrage wird über den Proxy der Suchdienstanwendung der Unternehmens-App-Farm an die Suchdienstanwendung der SharePoint Services-Farm weitergeleitet.  
    
11. Die Suchdienstanwendung ruft den Status der Tabelle „Actions“ ab und gibt ihn an den Zeitgeberauftrag in der Unternehmens-App-Farm zurück, die die Statusaktualisierungen per Push-Verfahren in das EDC überträgt. 
    
12. Wenn der eDiscovery-Benutzer Exchange-Quellen durchsucht, z. B. ein Postfach oder archivierte Lync-Inhalte (oder eine Aktion darauf anwendet), verwendet die zentrale Suchdienstanwendung den Exchange-Webdienste-Proxy (Exchange Web Services, EWS) zum Abfragen von Exchange-Webdiensten. Exchange hat eine eigene Suchfunktion und eDiscovery-Infrastruktur und verwaltet alle eDiscovery-Aufrufe intern. 
    
13. Exchange-Webdienste antwortet der Suchdienstanwendung mit eDiscovery-Suchergebnissen oder einer Antwort auf eine Statusanforderung eines abfragebasierten Archivs, das wiederum an das EDC weitergeleitet wird.  
    
#### <a name="prerequisites"></a>Voraussetzungen

- Die SharePoint-Unternehmenssuche muss konfiguriert sein, Inhaltsquellen (SharePoint- und Windows-Dateifreigaben) müssen erfolgreich durchforstetet werden, und alle Inhaltsquellen müssen sich im Index befinden.  
    
- Die Server-zu-Server-Vertrauensstellung und -Authentifizierung muss zwischen der SharePoint Services-Farm und Exchange sowie zwischen Exchange und Lync konfiguriert sein.  
    
### <a name="description-of-components-in-the-diagram"></a>Beschreibung der im Diagramm dargestellten Komponenten

Das Diagramm zeigt, wie ein Benutzer eine Abfrage sendet, die auf zwei Serverfarmen, eine SharePoint 2013 Enterprise-App-Farm und eine SharePoint 2013-Dienstfarm zugreift. Die SharePoint Services-Farm Schnittstellen mit einer SharePoint 2013-Inhalts Farm, Exchange Server 2013 (mit lync 2013) und Windows-Dateifreigaben. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>SharePoint 2013 Enterprise-App-Farm

Die SharePoint 2013 Enterprise-App-Farm enthält die folgenden Komponenten: 
  
- EDC
    
- SSA-Proxy  
    
- Zeitgeberauftrag 
    
Eine Abfrage oder eine Aktion, die vom Benutzer gesendet wird, wird an das EDC in der Unternehmens-App-Farm gesendet. Es geschieht Folgendes:  
  
- Die Abfrage oder die Aktion wird an den SSA-Proxy übermittelt.  
    
- Der SSA-Proxy sendet eine Statusabfrage oder -antwort an den Zeitgeberauftrag in der Unternehmens-App-Farm. Zudem sendet er eine Statusabfrage oder -antwort an den SSA-Dienst in der SharePoint Services-Farm. Die Aktionen, die sich hieraus ergeben, werden im Abschnitt über die SharePoint Services-Farm beschrieben.  
    
- Wenn der Zeitgeberauftrag eine Antwort erhält, sendet er diese an den SSA-Proxy und das EDC.  
    
- Ergebnisse der Abfrage oder Aktion werden aus dem EDC an den Benutzer gesendet.  
    
#### <a name="sharepoint-2013-services-farm"></a>SharePoint-2013-Dienst Farm

Die SharePoint 2013 Services-Farm enthält die folgenden Komponenten: 
  
- SSA-Dienst  
    
- Suchindexdatenbank 
    
- Verwaltungsdatenbank der Suchdienstanwendung. Die Tabelle „Actions“ in dieser Datenbank enthält: Archiv, ReleaseHold, GetStatus 
    
- EWS-Proxy  
    
Wenn der SSA-Proxy in der SharePoint-Unternehmens-App-Farm eine Statusabfrage an die SSA in der SharePoint Services-Farm sendet, geschieht Folgendes:  
  
- Wenn die Anforderung eine Abfrage ist, konsultiert die Suchdienstanwendung den Suchindex. Die Antwort der Ermittlung wird an die SSA und dann über das EDC an den Benutzer zurückgegeben.  
    
- Wenn die Anforderung eine Schreibaktion ist, sendet der SSA-Dienst die Schreibaktion an die Verwaltungsdatenbank der Suchdienstanwendung.  
    
- Eine Anforderung zum Crawlen und Antworten der Ergebnisse wird von der SSA an die SharePoint 2013-Inhalts Farm gesendet, und eine Antwort wird an die SSA zurückgegeben. 
    
- Eine Anforderung für Durchforstung und Antwortergebnisse wird von der SSA an die Windows-Dateifreigaben gesendet, und eine Antwort wird an die SSA zurückgegeben.  
    
- Eine Abfrage für ausstehenden Aktion(en), Antworten oder Statusaktualisierungen wird von der SSA an den SSA-Proxy in der SharePoint-Inhaltsfarm gesendet, und eine Antwort wird an die SSA zurückgegeben.  
    
- Eine Aktions-/Statusanforderung von Exchange wird von der SSA an den EWS-Proxy gesendet, der eine Aktions-/Statusanforderung für eine Exchange-Abfrage an den Exchange-Webdienst auf dem Exchange 2013-Server sendet.   
    
- Eine Statusabfrage/-antwort wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben.  
    
- Eine Abfrage/Antwort für eine ausstehende Aktion wird von der SSA an die Verwaltungsdatenbank der Suchdienstanwendung gesendet und an die SSA zurückgegeben.  
    
#### <a name="sharepoint-2013-content-farm"></a>SharePoint 2013-Inhalts Farm

Die SharePoint 2013-Inhalts Farm enthält die folgenden Komponenten: 
  
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
  
- Server-zu-Server-Vertrauensstellung/OAuth wird zwischen der SharePoint 2013-Inhalts Farm und Exchange 2013 verarbeitet. 
    
- Server-zu-Server-Vertrauensstellung/OAuth erfolgt zwischen Exchange 2013 und Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

Die Lync 2013-Komponente archiviert Lync-Inhalte in Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Windows-Dateifreigaben

Die Windows-Dateifreigaben-Komponente stellt Durchforstungsergebnisse für die SSA in der SharePoint Services-Farm bereit.  
  
### <a name="legend"></a>Legende

Die Legende für dieses Diagramm enthält eine grafische Darstellung der verschiedenen zwischen den Komponenten gezeigten Datenverkehrstypen in Form verschiedenfarbiger Linien, wie nachfolgend beschrieben:  
  
- Hellblaue Linien: Abfrage/Aktion – eDiscovery-Abfrage-oder Aktionsdaten 
    
- Orangefarbene Leitung: eDiscovery-Antwort – eDiscovery-Abfrageantwort Daten 
    
- Grüne Leitung: Statusabfrage/-Antwort – eDiscovery-Statusabfrage/Antwortdaten 
    
- Violette Leitung: Exchange-Aktion/Statusanforderung – eDiscovery-Anforderung für Aktionsstatus für Exchange-Datenverkehr. 
    
- Rote Leitung: Exchange-Daten/Statusantwort – eDiscovery-Abfrage oder Statusantwort von Exchange. 
    
- Gepunktete schwarze Linie: Server-zu-Server-Vertrauensstellung/OAuth  
    
- Durchgezogene schwarze Linie: Durchforstung/Ergebnisse  
    

