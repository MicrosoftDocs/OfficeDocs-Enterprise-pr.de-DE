---
title: Project Server 2010 End-of-Support-roadmap
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
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
description: Klicken Sie auf dem 13 Oktober 2020 für Project Server 2010-Unterstützung endet. Verwenden Sie diesen Artikel zum Planen des Upgrades jetzt.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549783"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 Ende Unterstützung-Wegweiser

Support für Office 2010-Servern und Anwendungen in 2010 beendet wird und Pläne für die Migration berücksichtigt werden müssen. Wenn Sie derzeit Project Server 2010 verwenden, beachten Sie, dass sie und diese weitere zugehörige Produkte in der folgenden Ende des Zeitraums Unterstützung hat:
  
|**Produkt**|**Ablaufdatum für support**|
|:-----|:-----|
|Project Server 2010  <br/> |13 Oktober 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 Oktober 2020  <br/> |
|Project 2010-Standard  <br/> |13 Oktober 2020  <br/> |
|Project 2010 Professional herunter  <br/> |13 Oktober 2020  <br/> |
   
Weitere Informationen zu Office 2010-Server erreichen Stilllegung finden Sie unter [Aktualisieren von Office 2010-Server und Client-Produkte](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Welche funktioniert Ende Mittelwert Support?

Projektserver, wie fast alle Microsoft-Produkte hat eine Supportlebenszyklus während der wir neue Features, Fehlerbehebungen, Sicherheitspatches und So weiter enthalten. Dieser Lebenszyklus dauert in der Regel für zehn Jahren ab dem Zeitpunkt der ersten Version des Produkts, und das Ende dieser Lebenszyklus wird als das Produkt Ablauf des Supports bezeichnet. Da Project Server 2010 dessen Ablauf des Supports auf 10 Oktober 2020 Microsoft wird nicht mehr zur Verfügung erreicht:
  
- Technischen Support für Probleme, die auftreten können.
    
- Fehler korrigiert für Probleme, die ermittelt werden und kann, die die Stabilität und Verwendbarkeit des Servers auswirken.
    
- Sicherheitsupdates für Sicherheitsrisiken, werden erkannt und, die möglicherweise den Server anfällig für Sicherheitslücken.
    
- Zeitzone aktualisiert.
    
Die Installation von Project Server 2010 wird weiterhin nach diesem Datum ausgeführt. Allerdings wird aufgrund der oben aufgeführten Änderungen, dringend empfohlen, dass Sie von Project Server 2010 so bald wie möglich migrieren.
  
## <a name="what-are-my-options"></a>Welche Optionen sind?

Wenn Sie Project Server 2010 verwenden, müssen Sie Ihre Migrationsoptionen, verwenden die sind:
  
- Migrieren zu Project Online
    
- Migrieren Sie zu einer neueren lokalen Version von Project Server (vorzugsweise Project Server 2019).
    
|**Warum möchte ich Ihre Migration zu Project Online**|**Warum würde ich Migration zu Project Server 2019 bevorzugen**|
|:-----|:-----|
| Ich habe die Benutzer mobiler Geräte.  <br/>  Kosten zu migrieren sind ein großes Problem (Hardware, Software, Stunden und Aufwand zum Implementieren usw.).  <br/>  Nach der Migration werden Kosten für meine Umgebung verwalten großer Bedeutung (beispielsweise automatische Updates, garantiert Betriebszeit usw.) verwendet..  <br/> | Geschäftsregeln verhindern, dass mir mein Unternehmen in der Cloud ausgeführt.  <br/>  Ich Steuerung des Updates auf meine Umgebung.  <br/> |
   
> [!NOTE]
> Weitere Informationen zu den Optionen für das Verschieben von Office 2010-Server finden Sie unter [Aktualisieren von Office 2010-Servern und Clients zu erleichtern](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Beachten Sie, dass Project Server eine hybridkonfiguration gegenüber Project Server unterstützt und Project Online kann nicht den gleichen Ressourcenpool freigeben. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Wichtige Aspekte der benötigten stellen Sie bei der Planung der Migration von Project Server 2010

Sie müssen die folgenden berücksichtigen Sie beim Planen der Migration von Project Server 2010:
  
- **Holen Sie sich Hilfe von Microsoft-Partner** - Upgrade von Project Server 2010 kann eine Herausforderung sein und erfordert viel Vorbereitung und Planung. Es kann insbesondere anspruchsvoll sein, wenn Sie nicht demjenigen, der zum Einrichten und Konfigurieren von Project Server 2010 ursprünglich waren. Zum Glück sind Partners Sie wenden können, die dazu verdienen, ob Sie an Project Server 2019 oder Project Online migrieren möchten. Sie können für einen Microsoft-Partner, die bei der Migration im [Microsoft Partner Center](https://go.microsoft.com/fwlink/p/?linkid=841249)unterstützen suchen. Sie können eine Liste aller Microsoft-Partner mit Erfahrung im Projekt über eine Suche auf den Ausdruck *Gold Projekt- und Portfoliomanagement* abrufen. 
    
- **Planen Sie Ihre Anpassungen** - Beachten Sie, dass viele der Anpassungen arbeiten in der Project Server 2010-Umgebung stehen Ihnen möglicherweise nicht verwendet werden bei der Migration zu Project Server 2019 oder mit Project Online. Es gibt große Unterschiede bei der Architektur von Project Server zwischen Versionen, sowie die erforderlichen Betriebssysteme, Datenbankserver und Client Webbrowsern, die unterstützt werden, um die neuere Version entwickelt. Verfügen Sie einen Plan zum Testen oder neu erstellen die Anpassungen nach Bedarf in der neuen Umgebung. Planen des Upgrades wird auch eine gute Möglichkeit zum Überprüfen, ob eine bestimmte Anpassung wirklich erforderlich ist, wie Sie vorwärts verschoben werden. [Erstellen eines Plans für aktuelle Anpassungen während eines Upgrades auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) verfügt über einige große allgemeine Informationen zu bewerten und planen Ihre aktuellen Anpassungen beim Upgrade. 
    
- **Zeit- und Verständnis** - Upgrade Planung, Ausführung, und Testen von dauert viel Zeit und Mühe, insbesondere dann, wenn Sie auf Project Server 2019 aktualisieren. Beispielsweise wenn von Project Server 2010, Project Server 2019 migrieren werden Sie zunächst müssen Migrieren von Project Server 2010 auf Project Server 2013, und überprüfen Sie die Daten, und führen Sie das gleiche bei der Migration zu jeder neuen Version (Project Server 2016 und klicken Sie dann Projektserver 2019). Möglicherweise möchten Sie überprüfen Sie mit einem Microsoft-Partner zum Vergleichen der geschätzten Kosten für ihre Schätzungen des Zeitraums, für sie ihn, und klicken Sie unter welche Kosten dauern wird. 
    
## <a name="migrate-to-project-online"></a>Migrieren zu Project Online

Wenn Sie zum Migrieren von Project Server 2010 zu Project Online auswählen, können Sie Folgendes ein, um manuell Plan Projektdaten migriert ausführen:
  
1. Speichern Sie die Projektpläne aus Project Server 2010, um. MPP-Format.
    
2. Mit Project Professional 2016, Project Professional 2019 oder Project Online Desktop-Client, öffnen Sie jede MPP-Datei, und klicken Sie dann speichern und veröffentlichen zu Project Online.
    
Sie können Ihre PWA-Konfiguration manuell erstellen, in Project Online (beispielsweise erstellen Sie alle erforderlichen benutzerdefinierten Felder oder Enterprise-Kalender erneut). Microsoft Partners können auch dabei helfen.
  
Wichtige Ressourcen:
  
|**Ressource**|**Beschreibung**|
|:-----|:-----|
|[Erste Schritte mit Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Informationen zum Einrichten und verwenden Sie Project Online.  <br/> |
|[Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informationen zu den verschiedenen Project Online-Plänen, die Ihnen zur Verfügung stehen.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrieren Sie zu einer neueren lokalen Version von Project Server

Während wir dringend glauben, dass Sie den Wert und Benutzer am besten erreichen können, von der Migration zu Project Online, wissen wir auch, dass einige Organisationen Project-Daten in einer lokalen Umgebung sein müssen. Wenn Sie Ihre Project Daten lokale beibehalten, können Sie Ihre Project Server 2010-Umgebung auf Project Server 2013, Project Server 2016 oder Project Server 2019 migrieren.
  
Es wird empfohlen, dass die Migration zu Project Server 2019, wenn Sie mit Project Online migrieren können. Projektserver 2019 enthält die meisten der Schlüssel, die Features und Weiterentwicklungen mit vorherigen Versionen von Project Server enthalten, und die Erfahrung mit Project Online verfügbaren es am ehesten entspricht, (obwohl einige Features nur in Project Online verfügbar sind).
  
Nach Abschluss der einzelnen Migration sollten Sie überprüfen, Ihre Daten, um sicherzustellen, dass es erfolgreich migriert wurden.
  
> [!NOTE]
> Wenn Sie erwägen, Migrieren zu Project Server 2013 nur, wenn Sie auf einer lokalen Lösung beschränkt sind, ist es wichtig zu beachten, dass nur ein paar weitere Jahre Support von Links enthalten ist. Project Server 2013 mit Service Pack 2 Ablaufdatum für Support ist 10/13/2023 zurück. Weitere Informationen zum Ende des Zeitraums Unterstützung finden Sie unter [Microsoft Product Lifecycle-Richtlinie](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Wie migriere ich Project Server 2019?

Unterschiede in der Architektur zwischen Project Server 2010 und Project Server 2019 verhindert, dass einen direkte Migrationspfad. Dies bedeutet, dass Sie Ihre Project Server 2010-Daten auf die nächste aufeinander folgende Version von Project Server migrieren, bis Sie ein auf Project Server 2019 Upgrade benötigen.
  
Sie müssen zum upgrade auf Project Server 2019 folgende Schritte ausführen:
  
1. Schritt 1: Migrieren der Daten von Project Server 2010 auf Project Server 2013.
    
2. Schritt 2: Migrieren der Daten auf Project Server 2016 aus Project dienen 2013.
    
3. Schritt 3: Migrieren der Daten von Project Server 2016 zu Project Server 2019.
    
Nach Abschluss der einzelnen Migration sollten Sie überprüfen, Ihre Daten, um sicherzustellen, dass es erfolgreich migriert wurden.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Schritt 1: Migrieren Sie zu Project Server 2013

Der erste Schritt beim Migrieren der Project Server 2010-Daten zu Project Server 2019 wird zuerst die Migration zu Project Server 2013. 
  
Ein umfassendes Verständnis des was Sie tun, um das upgrade von Project Server 2010 auf Project Server 2013 benötigen, finden Sie unter der Inhaltssatz [Durchführen eines Upgrades auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) auf TechNet. 
  
Wichtige Ressourcen:
  
|**Ressource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2013-Upgradevorgang](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Rufen Sie ein allgemeines Verständnis von was Sie tun, um das upgrade von Project Server 2010 auf Project Server 2013 benötigen.  <br/> |
|[Planen eines Upgrades auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Sehen Sie sich planungsüberlegungen, Sie beim Aktualisieren von Project Server 2010 auf Project Server 2013, einschließlich System Requirements müssen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wichtige Informationen zum Upgrade auf diese version

[Was ist neu in Project Server 2013-Upgrade](https://go.microsoft.com/fwlink/p/?linkid=841824) enthält einige wichtigen Änderungen für das Upgrade für diese Version, die wichtigsten wird: 
  
- Es ist kein direktes Upgrade auf Project Server 2013. Das Anfügen der Datenbank-Methode ist die einzige unterstützte Methode für das Upgrade von Project Server 2010 auf Project Server 2013.
    
- Der Upgradevorgang konvertiert nicht nur die Project Server 2010-Daten in Project Server 2013-Format, jedoch wird auch konsolidieren, die vier Project Server 2010-Datenbanken in eine einzelne Project Web App-Datenbank.
    
- SharePoint Server 2013 und Project Server 2013 zur anspruchsbasierten Authentifizierung aus der vorherigen Version geändert. Sie müssen auf Aspekte treffen aktualisieren, wenn Sie die klassischen Authentifizierung verwenden. Weitere Informationen finden Sie unter [Migrieren vom klassischen Modus zur anspruchsbasierten Authentifizierung in SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Weitere Ressourcen:
  
- [Übersicht über den Prozess zum Upgrade auf Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Upgrade der Datenbanken und Project Web App-Websitesammlungen (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server-Upgrade-Prozessdiagramm](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Die große Datenbankkonsolidierung, Migration von Project Server 2010, 2013 in einfachen Schritten 8](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Schritt 2 Migrieren zu Project Server 2016

Nach der Migration zu Project Server 2013, und überprüfen, dass die Daten erfolgreich migriert wurde, wird im nächste Schritt zum Migrieren der Daten auf Project Server 2016.
  
Ein umfassendes Verständnis des was Sie tun, um das upgrade von Project Server 2013 auf Project Server 2016 benötigen, finden Sie unter der [Durchführen eines Upgrades auf Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) Inhaltssatz.
  
Wichtige Ressourcen:
  
|**Ressource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über den Project Server 2016-Upgradevorgang](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Rufen Sie ein allgemeines Verständnis von was Sie tun, um das upgrade von Project Server 2013 auf Project Server 2016 benötigen.  <br/> |
|[Planen des Upgrades auf Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Betrachten Sie Hinweise zur Planung, die Sie beim Aktualisieren von Project Server 2013 auf Project Server 2016 treffen müssen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wichtige Informationen zum Upgrade auf diese version

[Aktualisieren Sie Dinge, die Sie über Project Server 2016 wissen müssen](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) , erfahren Sie einige wichtigen Änderungen für das Upgrade in dieser Version enthalten: 
  
- Wenn Sie Ihre Project Server 2016-Umgebung erstellen, die Sie die Project Server 2013-Daten migriert, beachten Sie, dass die Installationsdateien für Project Server 2016 in SharePoint Server 2016 enthalten sind. Weitere Informationen finden Sie unter [Bereitstellen von Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Ressourcenpläne sind in Project Server 2016 veraltet. Ihre Project Server 2013 Ressourcenpläne werden zu Ressource Projekten in Project Server 2016 und in Project Online migriert werden. Finden Sie unter [Übersicht: Ressource Engagements](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) Weitere Informationen. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Schritt 3 Migrieren zu Project Server 2019

Nach der Migration zu Project Server 2016 und sicherstellen, dass die Daten erfolgreich migriert wurde, wird im nächste Schritt zum Migrieren der Daten auf Project Server 2019.
  
Ein umfassendes Verständnis des was Sie tun, um das upgrade von Project Server 2016 auf Project Server 2019 benötigen, finden Sie unter der [Durchführen eines Upgrades auf Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) Inhaltssatz.
  
Wichtige Ressourcen:
  
|**Ressource**|**Beschreibung**|
|:-----|:-----|
|[Übersicht über die Project Server-2019 Upgradeprozess](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Rufen Sie ein allgemeines Verständnis von was Sie tun, um das upgrade von Project Server 2013 auf Project Server 2016 benötigen.  <br/> |
|[Planen eines Upgrades auf Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Betrachten Sie Hinweise zur Planung, die Sie beim Aktualisieren von Project Server 2016 auf Project Server 2019 treffen müssen.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Wichtige Informationen zum Upgrade auf diese version

[Aktualisieren Sie Dinge, die Sie über Project Server 2019 wissen müssen](https://go.microsoft.com/fwlink/p/?linkid=841827) , erfahren Sie einige wichtigen Änderungen für das Upgrade in dieser Version enthalten: 
  
- Der Upgradevorgang Migrieren der Daten aus der 2016 für Project Server-Datenbank mit der 2019 Inhalte zu SharePoint Server-Datenbank.  Projektserver 2019 nicht lange erstellt Eigentümer von Project Server-Datenbank in der SharePoint-Serverfarm.

- Nach dem Upgrade Achten Sie mehrere Änderungen in Project Web App.  Eine Beschreibung dieser finden Sie unter [Was ist neu in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Migrieren von Portfolio Server 2010

Project Portfolio Server 2010 wurde mit Project Server 2010 für Portfoliostrategie, Priorisierung und Optimierung verwendet. Nach dieser Version wurden keine zusätzlichen Versionen von Project Portfolio Server erstellt. Portfolio Management-Features sind jedoch in späteren Versionen von Project Server und der Premium-Version von Project Online verfügbar. Daten von Project Portfolio Server 2010 können entweder migriert werden. Daten beispielsweise von betriebswirtschaftlichen Faktoren müssen neu erstellt werden.
  
Weitere Ressourcen:
  
- [Project Online-Dienstbeschreibungen](https://go.microsoft.com/fwlink/p/?linkid=841280): finden Sie unter der Portfolio Management-Funktionen, die mit Project Server 2016 und Project Online Premium enthalten sind.
    
- [Migrationshandbuch für Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Verwandte Themen

[Upgrade von SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Ressourcen zum upgrade von Office 2010-Servern und clients](upgrade-from-office-2010-servers-and-products.md)
  

