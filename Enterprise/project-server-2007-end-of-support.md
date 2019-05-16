---
title: Ende der Unterstützung für Project Server 2007 – Roadmap
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: Am 10. Oktober 2017 wurde die Unterstützung für Project Server 2007, Project Portfolio Server und Project 2007 beendet. Verwenden Sie diesen Artikel, um das Upgrade jetzt zu planen.
ms.openlocfilehash: 620b5ae3e23c3b4bdba9c429def81eebedbd32a3
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071051"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Ende der Unterstützung für Project Server 2007 – Roadmap

Die Unterstützung wird für Office 2007-Server und-Anwendungen in 2017 beendet, und Sie müssen Pläne für die Migration berücksichtigen. Wenn Sie Project Server 2007 derzeit verwenden, beachten Sie, dass es und diese anderen verwandten Produkte über die folgenden End-of-Support-Termine verfügen:
  
|**Product**|**Ende des Support Datums**|
|:-----|:-----|
|Project Server 2007  <br/> |10. Oktober 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10. Oktober 2017  <br/> |
|Project 2007 Standard  <br/> |10. Oktober 2017  <br/> |
|Project 2007 Professional  <br/> |10. Oktober 2017  <br/> |
   
Weitere Informationen zu Office 2007-Servern, die den Ruhestand erreichen, finden Sie unter [Upgrade von Office 2007-Servern und Clientprodukten](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Was bedeutet End-of-Support?

Project Server hat, wie fast alle Microsoft-Produkte, einen Supportlebenszyklus, in dem wir neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellen. Dieser Lebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts, und das Ende dieses Lebenszyklus wird als Ende des Supports des Produkts bezeichnet. Da Project Server 2007 das Ende der Unterstützung am 10. Oktober 2017 erreicht hat, bietet Microsoft nicht mehr Folgendes an:
  
- Technischer Support für Probleme, die auftreten können.
    
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können.
    
- Sicherheitsfixes für erkannte Sicherheitsanfälligkeiten, die den Server anfällig für Sicherheitsverletzungen machen können.
    
- Zeitzonenaktualisierungen.
    
Die Installation von Project Server 2007 wird nach diesem Datum fortgesetzt. Aufgrund der oben aufgeführten Änderungen wird jedoch dringend empfohlen, dass Sie so bald wie möglich eine Migration von Project Server 2007 durchführen.
  
## <a name="what-are-my-options"></a>Was sind meine Optionen?

Wenn Sie Project Server 2007 verwenden, müssen Sie sich mit den folgenden Migrationsoptionen vertraut machen:
  
- Migrieren zu Project Online
    
- Migrieren Sie zu einer neueren lokalen Version von Project Server (vorzugsweise Project Server 2016).
    
|**Warum sollte ich lieber zu Project Online migrieren?**|**Warum sollte ich lieber zu Project Server 2016 migrieren?**|
|:-----|:-----|
| Ich habe mobile Benutzer.  <br/>  Kosten für die Migration sind ein großes Problem (Hardware, Software, Arbeitszeiten und Implementierungsaufwand usw.).  <br/>  Nach der Migration sind die Kosten für die Verwaltung meiner Umgebung ein großes Problem (beispielsweise automatische Updates, garantierte Betriebszeit usw.).  <br/> | Geschäftsregeln beschränken mich vom Betrieb meines Unternehmens in der Cloud.  <br/>  Ich benötige Kontrolle über Updates für meine Umgebung.  <br/> |
   
> [!NOTE]
> Weitere Informationen zu Optionen für den Wechsel von Ihren Office 2007-Servern finden Sie unter [Ressourcen zum Upgrade von Office 2007-Servern und-Clients](upgrade-from-office-2007-servers-and-products.md). Beachten Sie, dass Project Server keine Hybrid Konfiguration unterstützt, da Project Server und Project Online nicht denselben Ressourcenpool verwenden können. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Wichtige Überlegungen, die Sie bei der Planung der Migration von Project Server 2007 vornehmen müssen

Bei der Planung der Migration von Project Server 2007 müssen Sie Folgendes berücksichtigen:
  
- **Hilfe von einem Microsoft-Partner** : das Upgrade von Project Server 2007 kann eine Herausforderung sein und erfordert viel Vorbereitung und Planung. Es kann besonders schwierig sein, wenn Sie nicht derjenige waren, der Project Server 2007 ursprünglich installiert und konfiguriert hat. Glücklicherweise gibt es Microsoft-Partner, an die Sie sich wenden können, wenn Sie die Migration zu Project Server 2016 oder Project Online ausführen möchten. Sie können nach einem Microsoft-Partner suchen, der Sie bei ihrer Migration im [Microsoft Partner Center](https://go.microsoft.com/fwlink/p/?linkid=841249)unterstützt. Sie können eine Liste aller Microsoft-Partner mit Fachwissen in Project abrufen, indem Sie den Begriff " *Gold Project" und "Portfolio Management* " Durchsuchen. 
    
- **Planen Ihrer Anpassungen** – beachten Sie, dass viele der Anpassungen, die Sie in der Project Server 2007-Umgebung ausgeführt haben, möglicherweise nicht bei der Migration zu Project Server 2016 oder Project Online funktionieren. Es gibt große Unterschiede zwischen den Versionen der Project Server-Architektur sowie den erforderlichen Betriebssystemen, Datenbankservern und Client Webbrowser, die für die Verwendung mit der neueren Version unterstützt werden. Planen Sie, wie Sie Ihre Anpassungen in ihrer neuen Umgebung testen oder neu erstellen. Die Planung Ihres Upgrades ist auch eine gute Gelegenheit, um zu überprüfen, ob eine bestimmte Anpassung tatsächlich erforderlich ist, wenn Sie fortfahren. [Erstellen eines Plans für aktuelle Anpassungen beim Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) enthält einige allgemeine Informationen zur Bewertung und Planung Ihrer aktuellen Anpassungen beim Upgrade. 
    
- **Zeit und Geduld** – die Planung, Ausführung und das Testen von Upgrades erfordern sehr viel Zeit und Aufwand, insbesondere bei einem Upgrade auf Project Server 2016. Wenn Sie beispielsweise eine Migration von Project Server 2007 zu Project Server 2016 durchführen, müssen Sie zunächst von Project Server 2007 zu Project Server 2010 migrieren und dann Ihre Daten überprüfen und dann dasselbe tun, wenn Sie zu jeder nachfolgenden Version migrieren. Möglicherweise möchten Sie mit einem Microsoft-Partner überprüfen, ob Sie Ihre Kosten mit ihren Schätzungen darüber vergleichen, wie lange es dauert, bis Sie dies tun, und zu welchen Kosten. 
    
## <a name="migrate-to-project-online"></a>Migrieren zu Project Online

Wenn Sie sich für eine Migration von Project Server 2007 zu Project Online entscheiden, können Sie die folgenden Schritte ausführen, um die Projektplandaten manuell zu migrieren:
  
1. Speichern Sie Ihre Projektpläne von Project Server 2003 in. MPP-Format.
    
2. Öffnen Sie jede MPP-Datei mit Project Professional 2013, Project Professional 2016 oder dem Project Online-Desktop Client, und speichern und veröffentlichen Sie Sie dann in Project online.
    
Sie können die PWA-Konfiguration in Project Online manuell erstellen (beispielsweise alle erforderlichen benutzerdefinierten Felder oder Enterprise-Kalender neu erstellen). Microsoft-Partner können Ihnen dabei helfen.
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Erste Schritte mit Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Einrichten und Verwenden von Project online.  <br/> |
|[Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informationen zu den verschiedenen Project Online-Plänen, die Ihnen zur Verfügung stehen.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrieren zu einer neueren lokalen Version von Project Server

Wir sind zwar der festen Überzeugung, dass Sie durch die Migration zu Project Online den bestmöglichen Wert und die beste Benutzererfahrung erzielen können, aber wir wissen, dass einige Organisationen Projektdaten in einer lokalen Umgebung speichern müssen. Wenn Sie Ihre Projektdaten lokal beibehalten möchten, können Sie Ihre Project Server 2007-Umgebung zu Project Server 2010, Project Server 2013 oder Project Server 2016 migrieren.
  
Es wird empfohlen, zu Project Server 2016 zu migrieren, wenn Sie nicht zu Project Online migrieren können. Project Server 2016 enthält alle Features und Fortschritte, die in früheren Versionen von Project Server enthalten sind, und entspricht den verfügbaren Funktionen von Project Online (obwohl einige Features nur in Project online verfügbar sind).
  
Nachdem Sie jede Migration abgeschlossen haben, sollten Sie Ihre Daten überprüfen, um sicherzustellen, dass Sie erfolgreich migriert wurde.
  
> [!NOTE]
> Wenn Sie nur eine Migration zu Project Server 2010 erwägen, wenn Sie auf eine lokale Lösung beschränkt sind, müssen Sie beachten, dass nur noch einige weitere Jahre Unterstützung übrig bleiben. Project Server 2010 mit Service Pack 2-Ende des Supports ist 10/13/2020. Weitere Informationen zum Ende der Support Termine finden Sie unter [Microsoft Product Lifecycle Policy](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Wie kann ich zu Project Server 2016 migrieren?

Die architektonischen Unterschiede zwischen Project Server 2007 und Project Server 2016 verhindern einen direkten Migrationspfad. Dies führt dazu, dass Sie Ihre Project Server 2007-Daten auf die nächste aufeinanderfolgende Version von Project Server migrieren müssen, bis Sie auf Project Server 2016 aktualisieren.
  
Sie müssen Folgendes ausführen, um ein Upgrade auf Project Server 2016 durchzuführen:
  
1. Schritt 1: Migrieren von Project Server 2007 zu Project Server 2010.
    
2. Schritt 2: Migration von Project Serve 2010 zu Project Server 2013.
    
3. Schritt 3: Migrieren von Project Server 2013 zu Project Server 2016.
    
Nachdem Sie jede Migration abgeschlossen haben, sollten Sie Ihre Daten überprüfen, um sicherzustellen, dass Sie erfolgreich migriert wurde.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Schritt 1: Migrieren von Project Server 2007 zu Project Server 2010

Umfassende Informationen dazu, was Sie für ein Upgrade von Project Server 2007 auf Project Server 2010 tun müssen, finden Sie unter [Upgrade auf Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) Content Set auf TechNet. 
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über das Upgrade von Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Informieren Sie sich über die erforderlichen Schritte zum Upgrade von Project Server 2007 auf Project Server 2010.  <br/> |
|[Planen des Upgrades auf Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |Sehen Sie sich die Planungsüberlegungen an, die Sie beim Upgrade von Project Server 2007 auf Project Server 2010 vornehmen müssen, einschließlich System Anforderungen.  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Wie kann ich ein Upgrade ausführen?

Während Details zum Upgrade auf [Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812) -Inhaltssatz gefunden werden können, ist es wichtig zu wissen, dass es zwei verschiedene Methoden gibt, mit denen Sie ein Upgrade durchführen können: 
  
- **Upgrade mit Anfügen von Datenbanken:** Diese Methode aktualisiert nur den Inhalt für Ihre Umgebung und nicht die Konfigurationseinstellungen. Sie ist erforderlich, wenn Sie ein Upgrade von Office Project Server 2007 bereitgestellt auf Hardware ausführen, die nur ein 32-Bit-Server Betriebssystem unterstützt. Es gibt zwei Arten von Upgradeverfahren für Datenbankanfügungen: 
    
  - **Vollständiges Upgrade mit Datenbankanfügung** -migriert die in den Office Project Server 2007-Datenbanken gespeicherten Projektdaten sowie die Microsoft Project Web App (PWA)-Website Daten, die in einer SharePoint-Inhaltsdatenbank gespeichert sind. 
    
  - **Datenbankanfügung – Kernupgrade** – migriert nur die in den Project Server-Datenbanken gespeicherten Projektdaten. 
    
- **Direktes Upgrade**: die Konfigurationsdaten für die Farm und alle Inhalte in der Farm werden in einer festen Reihenfolge auf der vorhandenen Hardware aktualisiert. Wenn Sie das direkte Upgrade starten, wird die gesamte Farm von Setup offline geschaltet, und die Websites und Microsoft Project Web App-Sites sind erst verfügbar, wenn das Upgrade abgeschlossen ist, und dann wird der Server neu gestartet. Nach dem Start eines direkten Upgrades können Sie das Upgrade nicht anhalten oder die Installation auf die vorherige Version zurücksetzen. Es wird dringend empfohlen, ein gespiegeltes Bild Ihrer Produktionsumgebung zu erstellen und das direkte Upgrade auf diese Umgebung und nicht auf Ihre Produktionsumgebung vorzunehmen. 
    
Weitere Ressourcen:
  
- [Superflow für Microsoft Project Server 2010-Upgrade](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Migration von Project Server 2007 zu Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Überlegungen zum Upgrade für Project Web App-Webparts](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Project Software Development Kit (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>Schritt 2: Migrieren zu Project Server 2013

Nach der Migration zu Project Server 2010 und überprüfen, ob Ihre Daten erfolgreich migriert wurden, besteht der nächste Schritt darin, Ihre Daten zu Project Server 2013 zu migrieren.
  
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
    
### <a name="step-3-migrate-to-project-server-2016"></a>Schritt 3: Migrieren zu Project Server 2016

Nach der Migration zu Project Server 2013 und überprüfen, ob Ihre Daten erfolgreich migriert wurden, besteht der nächste Schritt darin, Ihre Daten zu Project Server 2016 zu migrieren.
  
Umfassende Informationen dazu, was Sie für ein Upgrade von Project Server 2013 auf Project Server 2016 tun müssen, finden Sie unter Upgrade auf Project Server 2016 Content Set auf TechNet.
  
Wichtige Ressourcen:
  
|**Resource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2016-Upgradevorgang](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Informieren Sie sich über die erforderlichen Schritte zum Upgrade von Project Server 2013 auf Project Server 2016.  <br/> |
|[Planen des Upgrades auf Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Sehen Sie sich die Planungsüberlegungen an, die Sie beim Upgrade von Project Server 2013 auf Project Server 2016 vornehmen müssen, einschließlich.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wissenswertes über das Upgrade auf diese Version

[Was Sie über das Upgrade von Project Server 2016 wissen müssen](https://go.microsoft.com/fwlink/p/?linkid=841827) , erfahren Sie einige wichtige Änderungen für das Upgrade für diese Version, einschließlich: 
  
- Beachten Sie beim Erstellen der Project Server 2016-Umgebung, in der Sie die Project Server 2013-Daten migrieren werden, dass die Project Server 2016-Installationsdateien in SharePoint Server 2016 enthalten sind. Weitere Informationen finden Sie unter [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Ressourcenpläne sind in Project Server 2016 veraltet. Ihre Project Server 2013-Ressourcenpläne werden zu Ressourcen Engagements in Project Server 2016 und in Project Online migriert. Weitere Informationen finden Sie unter [Übersicht: Ressourcen Engagements](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrieren von Portfolio Server 2007

Project Portfolio Server 2007 wurde mit Project Server 2007 für Portfoliostrategie, Priorisierung und Optimierung verwendet. Es wurden keine weiteren Versionen von Project Portfolio Server nach dieser Version erstellt. Portfolio Verwaltungsfeatures sind jedoch sowohl in Project Server 2016 als auch in der Premium Version von Project online verfügbar. Daten aus Project Portfolio Server 2007 können nicht zu einer der beiden migriert werden. Daten wie Business-Treiber müssen neu erstellt werden.
  
Weitere Ressourcen:
  
- [Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=841280): sehen Sie sich die Portfolio Verwaltungsfeatures an, die in Project Server 2016 und Project Online Premium enthalten sind.
    
- [Microsoft Office Project Portfolio Server 2007-Migrationshandbuch](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Verwandte Themen

[Roadmap für SharePoint Server 2007 Ende der Unterstützung](sharepoint-2007-end-of-support.md)
  
[Ressourcen für das Upgrade von Office 2007-Servern und-Clients](upgrade-from-office-2007-servers-and-products.md)
  

