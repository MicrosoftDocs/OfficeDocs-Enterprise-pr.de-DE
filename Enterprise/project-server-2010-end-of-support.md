---
title: Project Server 2010 – End-of-Support-Roadmap
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Am 13. Oktober 2020 die Unterstützung für Project Server 2010. Verwenden Sie diesen Artikel, um das Upgrade jetzt zu planen.
ms.openlocfilehash: 1c8e6eab592e2974c334367e7931395e867ad97e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071041"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Roadmap für Project Server 2010 Ende der Unterstützung

Die Unterstützung wird für Office 2010-Server und-Anwendungen in 2010 beendet, und Sie müssen Pläne für die Migration berücksichtigen. Wenn Sie Project Server 2010 derzeit verwenden, sollten Sie beachten, dass für diese und diese anderen verwandten Produkte die folgenden Support Termine vorliegen:
  
|**Product**|**Ende des Support Datums**|
|:-----|:-----|
|Project Server 2010  <br/> |13. Oktober 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13. Oktober 2020  <br/> |
|Project 2010 Standard  <br/> |13. Oktober 2020  <br/> |
|Project 2010 Professional  <br/> |13. Oktober 2020  <br/> |
   
Weitere Informationen zu Office 2010-Servern, die den Ruhestand erreichen, finden Sie unter [Upgrade von Office 2010-Servern und Clientprodukten](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Was bedeutet End-of-Support?

Project Server hat, wie fast alle Microsoft-Produkte, einen Supportlebenszyklus, in dem wir neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellen. Dieser Lebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts, und das Ende dieses Lebenszyklus wird als Ende des Supports des Produkts bezeichnet. Da Project Server 2010 das Ende der Unterstützung am 10. Oktober 2020 erreicht hat, bietet Microsoft nicht mehr Folgendes an:
  
- Technischer Support für Probleme, die auftreten können.
    
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können.
    
- Sicherheitsfixes für erkannte Sicherheitsanfälligkeiten, die den Server anfällig für Sicherheitsverletzungen machen können.
    
- Zeitzonenaktualisierungen.
    
Die Installation von Project Server 2010 wird nach diesem Datum fortgesetzt. Aufgrund der oben aufgeführten Änderungen wird jedoch dringend empfohlen, dass Sie so bald wie möglich eine Migration von Project Server 2010 durchführen.
  
## <a name="what-are-my-options"></a>Was sind meine Optionen?

Wenn Sie Project Server 2010 verwenden, müssen Sie sich mit den folgenden Migrationsoptionen vertraut machen:
  
- Migrieren zu Project Online
    
- Migrieren Sie zu einer neueren lokalen Version von Project Server (vorzugsweise Project Server 2019).
    
|**Warum sollte ich lieber zu Project Online migrieren?**|**Warum sollte ich lieber zu Project Server 2019 migrieren?**|
|:-----|:-----|
| Ich habe mobile Benutzer.  <br/>  Kosten für die Migration sind ein großes Problem (Hardware, Software, Arbeitszeiten und Implementierungsaufwand usw.).  <br/>  Nach der Migration sind die Kosten für die Verwaltung meiner Umgebung ein großes Problem (beispielsweise automatische Updates, garantierte Betriebszeit usw.).  <br/> | Geschäftsregeln beschränken mich vom Betrieb meines Unternehmens in der Cloud.  <br/>  Ich benötige Kontrolle über Updates für meine Umgebung.  <br/> |
   
> [!NOTE]
> Weitere Informationen zu Optionen für den Wechsel von Ihren Office 2010-Servern finden Sie unter [Ressourcen zum Upgrade von Office 2010-Servern und-Clients](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Beachten Sie, dass Project Server keine Hybrid Konfiguration unterstützt, da Project Server und Project Online nicht denselben Ressourcenpool verwenden können. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Wichtige Überlegungen, die Sie bei der Planung der Migration von Project Server 2010 vornehmen müssen

Bei der Planung der Migration von Project Server 2010 müssen Sie Folgendes berücksichtigen:
  
- **Hilfe von einem Microsoft-Partner** : das Upgrade von Project Server 2010 kann eine Herausforderung sein und erfordert viel Vorbereitung und Planung. Es kann besonders schwierig sein, wenn Sie nicht derjenige waren, der Project Server 2010 ursprünglich installiert und konfiguriert hat. Glücklicherweise gibt es Microsoft-Partner, an die Sie sich wenden können, wenn Sie die Migration zu Project Server 2019 oder Project Online ausführen möchten. Sie können nach einem Microsoft-Partner suchen, der Sie bei ihrer Migration im [Microsoft Partner Center](https://go.microsoft.com/fwlink/p/?linkid=841249)unterstützt. Sie können eine Liste aller Microsoft-Partner mit Fachwissen in Project abrufen, indem Sie den Begriff " *Gold Project" und "Portfolio Management* " Durchsuchen. 
    
- **Planen Ihrer Anpassungen** – beachten Sie, dass viele der Anpassungen, die Sie in der Project Server 2010-Umgebung ausgeführt haben, möglicherweise nicht bei der Migration zu Project Server 2019 oder Project Online funktionieren. Es gibt große Unterschiede zwischen den Versionen der Project Server-Architektur sowie den erforderlichen Betriebssystemen, Datenbankservern und Client Webbrowser, die für die Verwendung mit der neueren Version unterstützt werden. Planen Sie, wie Sie Ihre Anpassungen in ihrer neuen Umgebung testen oder neu erstellen. Die Planung Ihres Upgrades ist auch eine gute Gelegenheit, um zu überprüfen, ob eine bestimmte Anpassung tatsächlich erforderlich ist, wenn Sie fortfahren. [Erstellen eines Plans für aktuelle Anpassungen beim Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) enthält einige allgemeine Informationen zur Bewertung und Planung Ihrer aktuellen Anpassungen beim Upgrade. 
    
- **Zeit und Geduld** – die Planung, Ausführung und das Testen von Upgrades erfordern viel Zeit und Aufwand, insbesondere bei einem Upgrade auf Project Server 2019. Wenn Sie beispielsweise eine Migration von Project Server 2010 zu Project Server 2019 durchführen, müssen Sie zunächst von Project Server 2010 zu Project Server 2013 migrieren und dann Ihre Daten überprüfen und dann dasselbe tun, wenn Sie zu jeder nachfolgenden Version migrieren (Project Server 2016 und dann Project Server 2019). Möglicherweise möchten Sie sich bei einem Microsoft-Partner erkundigen, wie Sie Ihre geschätzten Kosten mit ihren Schätzungen für die Dauer ihrer Ausführung und zu welchen Kosten vergleichen. 
    
## <a name="migrate-to-project-online"></a>Migrieren zu Project Online

Wenn Sie sich für eine Migration von Project Server 2010 zu Project Online entscheiden, können Sie die folgenden Schritte ausführen, um die Projektplandaten manuell zu migrieren:
  
1. Speichern Sie Ihre Projektpläne von Project Server 2010 in. MPP-Format.
    
2. Öffnen Sie jede MPP-Datei mit Project Professional 2016, Project Professional 2019 oder dem Project Online-Desktop Client, und speichern und veröffentlichen Sie Sie dann in Project online.
    
Sie können die PWA-Konfiguration in Project Online manuell erstellen (beispielsweise alle erforderlichen benutzerdefinierten Felder oder Enterprise-Kalender neu erstellen). Microsoft-Partner können Ihnen dabei helfen.
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Erste Schritte mit Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Einrichten und Verwenden von Project online.  <br/> |
|[Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informationen zu den verschiedenen Project Online-Plänen, die Ihnen zur Verfügung stehen.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrieren zu einer neueren lokalen Version von Project Server

Wir sind zwar der festen Überzeugung, dass Sie durch die Migration zu Project Online den bestmöglichen Wert und die beste Benutzererfahrung erzielen können, aber wir wissen, dass einige Organisationen Projektdaten in einer lokalen Umgebung speichern müssen. Wenn Sie Ihre Projektdaten lokal beibehalten möchten, können Sie Ihre Project Server 2010-Umgebung zu Project Server 2013, Project Server 2016 oder Project Server 2019 migrieren.
  
Es wird empfohlen, zu Project Server 2019 zu migrieren, wenn Sie nicht zu Project Online migrieren können. Project Server 2019 enthält die meisten der wichtigsten Features und Fortschritte, die in früheren Versionen von Project Server enthalten sind, und entspricht den verfügbaren Funktionen von Project Online (obwohl einige Features nur in Project online verfügbar sind).
  
Nachdem Sie jede Migration abgeschlossen haben, sollten Sie Ihre Daten überprüfen, um sicherzustellen, dass Sie erfolgreich migriert wurde.
  
> [!NOTE]
> Wenn Sie nur eine Migration zu Project Server 2013 erwägen, wenn Sie auf eine lokale Lösung beschränkt sind, müssen Sie beachten, dass nur noch einige weitere Jahre Unterstützung übrig bleiben. Project Server 2013 mit Service Pack 2-Ende des Supports ist 10/13/2023. Weitere Informationen zum Ende der Support Termine finden Sie unter [Microsoft Product Lifecycle Policy](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Wie kann ich zu Project Server 2019 migrieren?

Die architektonischen Unterschiede zwischen Project Server 2010 und Project Server 2019 verhindern einen direkten Migrationspfad. Dies führt dazu, dass Sie Ihre Project Server 2010-Daten auf die nächste aufeinanderfolgende Version von Project Server migrieren müssen, bis Sie auf Project Server 2019 aktualisieren.
  
Sie müssen Folgendes ausführen, um ein Upgrade auf Project Server 2019 durchzuführen:
  
1. Schritt 1: Migrieren Sie Ihre Daten von Project Server 2010 zu Project Server 2013.
    
2. Schritt 2: Migrieren Sie Ihre Daten von Project Serve 2013 zu Project Server 2016.
    
3. Schritt 3: Migrieren Sie Ihre Daten von Project Server 2016 zu Project Server 2019.
    
Nachdem Sie jede Migration abgeschlossen haben, sollten Sie Ihre Daten überprüfen, um sicherzustellen, dass Sie erfolgreich migriert wurde.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Schritt 1: Migrieren zu Project Server 2013

Der erste Schritt bei der Migration Ihrer Project Server 2010-Daten zu Project Server 2019 besteht darin, zunächst zu Project Server 2013 zu migrieren. 
  
Umfassende Informationen dazu, was Sie für ein Upgrade von Project Server 2010 auf Project Server 2013 tun müssen, finden Sie unter [Upgrade auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) Content Set auf TechNet. 
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2013-Upgradevorgang](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Informieren Sie sich über die erforderlichen Schritte zum Upgrade von Project Server 2010 auf Project Server 2013.  <br/> |
|[Planen des Upgrades auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Sehen Sie sich die Planungsüberlegungen an, die Sie beim Upgrade von Project Server 2010 auf Project Server 2013 vornehmen müssen, einschließlich System Anforderungen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wissenswertes über das Upgrade auf diese Version

[Was ist neu in Project Server 2013 Upgrade](https://go.microsoft.com/fwlink/p/?linkid=841824) erfahren Sie einige wichtige Änderungen für das Upgrade für diese Version, die bemerkenswerteste ist: 
  
- Es gibt kein direktes Upgrade auf Project Server 2013. Die Methode zur Datenbankanfügung ist die einzige unterstützte Methode für das Upgrade von Project Server 2010 auf Project Server 2013.
    
- Durch den Upgradeprozess werden nicht nur Ihre Project Server 2010-Daten in das Project Server 2013-Format konvertiert, sondern auch die vier Project Server 2010-Datenbanken in einer einzelnen Project Web App-Datenbank konsolidiert.
    
- Sowohl SharePoint Server 2013 als auch Project Server 2013 wurden von der vorherigen Version zur anspruchsbasierten Authentifizierung geändert. Sie müssen bei der Verwendung der klassischen Authentifizierung Überlegungen vornehmen. Weitere Informationen finden Sie unter [Migrieren von der klassischen Authentifizierung zur anspruchsbasierten Authentifizierung in SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Weitere Ressourcen:
  
- [Übersicht über den Prozess zum Upgrade auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Upgraden der Datenbanken und Project Web App-Websitesammlungen (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server-Aktualisierungsprozess Diagramm](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Die große Datenbank-Konsolidierung, Project Server 2010 zu 2013 Migration in 8 einfachen Schritten](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Schritt 2 Migration zu Project Server 2016

Nach der Migration zu Project Server 2013 und überprüfen, ob Ihre Daten erfolgreich migriert wurden, besteht der nächste Schritt darin, Ihre Daten zu Project Server 2016 zu migrieren.
  
Umfassende Informationen dazu, was Sie für ein Upgrade von Project Server 2013 auf Project Server 2016 tun müssen, finden Sie unter [Upgrade auf Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) Content Set.
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2016-Upgradevorgang](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Informieren Sie sich über die erforderlichen Schritte zum Upgrade von Project Server 2013 auf Project Server 2016.  <br/> |
|[Planen des Upgrades auf Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Sehen Sie sich die Planungsüberlegungen an, die Sie beim Upgrade von Project Server 2013 auf Project Server 2016 treffen müssen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wissenswertes über das Upgrade auf diese Version

[Was Sie über das Upgrade von Project Server 2016 wissen müssen](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) , erfahren Sie einige wichtige Änderungen für das Upgrade für diese Version, einschließlich: 
  
- Beachten Sie beim Erstellen der Project Server 2016-Umgebung, in der Sie die Project Server 2013-Daten migrieren werden, dass die Project Server 2016-Installationsdateien in SharePoint Server 2016 enthalten sind. Weitere Informationen finden Sie unter [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Ressourcenpläne sind in Project Server 2016 veraltet. Ihre Project Server 2013-Ressourcenpläne werden zu Ressourcen Engagements in Project Server 2016 und in Project Online migriert. Weitere Informationen finden Sie unter [Übersicht: Ressourcen Engagements](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Schritt 3 migrieren zu Project Server 2019

Nach der Migration zu Project Server 2016 und überprüfen, ob Ihre Daten erfolgreich migriert wurden, besteht der nächste Schritt darin, Ihre Daten zu Project Server 2019 zu migrieren.
  
Umfassende Informationen dazu, was Sie für ein Upgrade von Project Server 2016 auf Project Server 2019 tun müssen, finden Sie unter [Upgrade auf Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) Content Set.
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2019-Upgradeprozess](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Informieren Sie sich über die erforderlichen Schritte zum Upgrade von Project Server 2013 auf Project Server 2016.  <br/> |
|[Planen des Upgrades auf Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Sehen Sie sich die Planungsüberlegungen an, die Sie beim Upgrade von Project Server 2016 auf Project Server 2019 treffen müssen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wissenswertes über das Upgrade auf diese Version

[Was Sie über das Upgrade von Project Server 2019 wissen müssen](https://go.microsoft.com/fwlink/p/?linkid=841827) , erfahren Sie einige wichtige Änderungen für das Upgrade für diese Version, einschließlich: 
  
- Beim Upgradevorgang werden Ihre Daten aus der Project Server 2016-Datenbank in die SharePoint Server 2019-Inhaltsdatenbank migriert.  Project Server 2019 wird keine lange erstellen es besitzt Project Server-Datenbank in der SharePoint Server-Farm.

- Beachten Sie nach dem Upgrade mehrere Änderungen in Project Web App.  Eine Beschreibung dieser Informationen finden Sie unter [What es New in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Migrieren von Portfolio Server 2010

Project Portfolio Server 2010 wurde mit Project Server 2010 für Portfoliostrategie, Priorisierung und Optimierung verwendet. Es wurden keine weiteren Versionen von Project Portfolio Server nach dieser Version erstellt. Portfolio Verwaltungsfeatures sind jedoch in späteren Project Server-Versionen und der Premium-Version von Project online verfügbar. Daten aus Project Portfolio Server 2010 können nicht zu einer der beiden migriert werden. Daten wie Business-Treiber müssen neu erstellt werden.
  
Weitere Ressourcen:
  
- [Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=841280): sehen Sie sich die Portfolio Verwaltungsfeatures an, die in Project Server 2016 und Project Online Premium enthalten sind.
    
- [Microsoft Office Project Portfolio Server 2010-Migrationshandbuch](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Verwandte Themen

[Aktualisieren von SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Ressourcen für das Upgrade von Office 2010-Servern und-Clients](upgrade-from-office-2010-servers-and-products.md)
  

