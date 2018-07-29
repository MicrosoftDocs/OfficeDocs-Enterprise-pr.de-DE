---
title: SharePoint 2007-Migrationsoptionen zu berücksichtigen sind
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
description: SharePoint Server 2007 Ablauf des Supports erreicht hat, und es ist Zeit zum Aktualisieren. Verwenden Sie diesen Artikel beim Erstellen des Plans.
ms.openlocfilehash: 4395bc330efd97ae8865e0fb75f93f04fd162ecd
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169877"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint 2007-Migrationsoptionen zu berücksichtigen sind

Microsoft SharePoint 2007 und SharePoint Server 2007 haben Ablauf des Supports erreicht. Es ist Zeit zum Aktualisieren! Dieser Artikel enthält Informationen zu den Migrationsoptionen.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Allgemeine Upgrade-Strategien für SharePoint

Es gibt mehrere Methoden für ein upgrade eine SharePoint Server-Umgebung. Wenn Sie eine Microsoft Office SharePoint Server 2007-Farm sein, folgen es einige Beispiele der Upgrade Methoden:
  
- Datenbankanfügung
    
- Side-by-Side-upgrade
    
- Direktes Upgrade
    
- Hybridupgrades (mit getrennten Datenbanken in-Place / separate mit Anfügen der Datenbank)
    
- SharePoint-Hybriden (mit lokalen SharePoint online verbinden)
    
- Manuelles Verschieben von Daten zwischen Websitesammlungen oder Bibliotheken
    
- Schnelle Assistenten durchführen eines Upgrades auf Office 365 ([Advisor für SharePoint Online-Bereitstellung](https://aka.ms/spoguidance))
    
- Migration API zu SharePoint Online (SPO) in Office 365
    
Was funktioniert am besten für Sie?
  
Ihr Wissen über welche Ihrer Farm ist und wird für die ist eine taktischen Stärke, wenn es darum geht, aktualisieren. Die Möglichkeit, die anhand der SharePoint-Farm helfen Ihnen bei Ihrer Optionen zur Verfügung.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 hat auch ein schrittweises Upgrade hier nicht behandelt. Eine Liste der Schritt-spezifischen Upgrade finden unter Artikel das [Ende des SharePoint Server 2007 unterstützen Roadmap](sharepoint-2007-end-of-support.md). 
  
Denken Sie daran, die [Produktlebenszyklus](https://support.microsoft.com/en-us/lifecycle/search) und Systemanforderungen für alle SharePoint-Version zu überprüfen, die beim Aktualisieren auf. Dies ist, damit Sie beachten müssen, wenn die nächste Aktualisierung bereitgestellt werden muss (beispielsweise, wenn Sie auf ein legacy-Produkt wie SharePoint Server 2010 für weitere Upgrades planen, werden Sie sicher, dass Sie wissen, dass das Ende der Unterstützung von Datum anhalten), und stellen Sie sicher, dass Sie die Hardware, die den Projektplan unterstützt haben. 
  
Wenn Sie beabsichtigen, einige oder alle der SharePoint-Websites zu Office 365 in der Cloud Übergang ist dies eine Uhrzeit für einen Link zu den [Beschreibungen der Dienste für Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)mit einem Lesezeichen versehen. Sie benötigen die Dienstbeschreibungen, um mehr über SharePoint Online-Features erfahren und wie sie von abweichen lokale SharePoint Server. Upgrade funktionalen Microsoft Office SharePoint Server 2007-Farmen. Wenn Ihre Installation Websites enthält, die unterbrochen werden, beheben sie vor dem upgrade.
  
## <a name="a-note-about-managing-risk"></a>Ein Hinweis zum Risikomanagement

Methoden wie "Side-by-Side" sind in das Schema des Upgrade Logik wichtig. Bei einer Aktualisierung Side-by-Side Verwaltung Ihrer Microsoft Office SharePoint Server 2007-Farm, aber eine Farm erstellen die nächste Version von daraus (SharePoint Server 2010) auf neuer Hardware aus. Dadurch werden auf drei Arten:
  
1. Sie haben einen Ort auszuführende Sicherungen Ihrer Microsoft Office SharePoint Server 2007-Datenbanken separat zu aktualisieren, mithilfe der Datenbank anfügen.
    
2. Wenn Sie herausfinden, dass nur eine kleine Anzahl von wichtigen Dokumentbibliotheken und andere Informationen auf der Microsoft Office SharePoint Server 2007-Farm verwendet werden, können Sie Daten aus Microsoft Office SharePoint Server 2007 auf SharePoint Server 2010 manuell zu verschieben , oder übernehmen Sie nur bestimmte Websites und Webs auf die nächste Version (die Ihre Arbeit erleichtern kann).
    
3. Weniger gehen Sie auf der Microsoft Office sharepointserver 2007-Serverfarm, direkt, die sicherer die Daten, die Serverfarm, als Sie ein Upgrade enthält vor.
    
Methoden wie In-Place Upgrade fungiert direkt in der Microsoft Office SharePoint Server 2007-Farm, was Ihnen weniger leicht Optionen zum Abbrechen eines Pfads, und beginnen Sie erneut mit der ursprünglichen Umgebung. Erstellen Sie so weit wie möglich, in einigen Sicherheitsmaßnahmen (wie nutzen und Testen der Sicherungen der ursprünglichen Umgebung). Angenommen, wenn Ihre Microsoft Office SharePoint Server 2007-Farm virtuell ist und, die aus Gründen der Sicherung und Wiederherstellung dupliziert wird, Sichern Sie und Wiederherstellen der aktuellsten Datenbanken vor Ihrer Dienstfenster für das Upgrade. Wissen, dass Sie haben die Möglichkeit zum Wiederherstellen der Datenbank, die nicht Sicherungen werden nur Geben Sie ein Failsafe, es kann Ihnen Gewissheit.
  
> [!TIP]
> Dokumente mit bewährten Methoden für das Upgrade für [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)und [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)vorhanden ist. Sie können auch suchen für [Microsoft-Partner](https://partnercenter.microsoft.com/en-us/pcv/search) , die mit Office 365-Migrationen oder Upgrades Erfahrung verfügen. 
  
## <a name="make-your-plan"></a>Stellen Sie Ihren plan

Wenn Sie aktualisieren möchten, benötigen Sie einen Plan, und alle in diesen Fällen eine Größe passt nicht. Ihr Plan möglicherweise so einfach wie 'Erstellen Sie ein Office 365-Abonnement mit SharePoint Online, eine Domäne registrieren und Umleiten von Personen, um ihre Dateien zu speichern'. Und es kann nicht sein. Diese Entscheidung ist Ihre, und es ist nach unten zu, was Sie und Ihre Benutzer wirklich benötigen.
  
> [!NOTE]
> Es ist riskant, führen auf Software, deren Lebenszyklus beendet wurde. Produkte, die nicht mehr unterstützt werden nicht mehr gepatcht werden, wenn Probleme gefunden werden. Dies bedeutet auch, wenn neue Sicherheitsrisiken entstehen, werden keine Sicherheitspatches oder Fixes, da das Ende des Lebenszyklus-Produkte nicht mehr unterstützt werden. Vermeiden Sie diese Situation! 
  
### <a name="first-know-your-farm"></a>Vorbemerkungen Sie Ihrer farm

Bei der Aktualisierung sollte Ihre Entscheidungsprozess basieren auf die Funktionsweise der Farm für Ihre Organisation. Den müssen erfüllt sie? Was ist ihre Funktion? Jede Farm in Ihrem Unternehmen möglicherweise eine andere Position. Einige der SharePoint-Farmen *kritisch* sein kann, ist möglicherweise einige Datei Archive – dort sicheren Ort. Oder, wenn die Farm auf einmal vielen Rollen füllt, dann müssen Sie möglicherweise wissen, welche Websitesammlungen, Webs oder sogar Dokumentbibliotheken Anpassungen ausführen, und wie wichtig sind. Analysieren der Daten auf dieser Ebene mag wie viel Arbeit, aber es Zeit und Mühe an Ihre Domäne master, bevor Sie aktualisieren oder zu migrieren, speichert es. Nachdem Sie alle beweglichen Teile und die wichtigsten Bits kennen, wissen Sie auch was Sie klein geworden haben und bleiben können. Dieses wissen nur profitieren Sie zukünftig. 
  
Daher sind Benutzer Erfahrungen wichtigste zu Ihrer SharePoint Server-Farm ist?
  
- Integrierter SharePoint-features
    
- Die großer Datenmengen Korpus (beispielsweise ein Archiv-Dateien)
    
- Verfügbarkeit
    
- Wichtige apps, Webparts oder Dokumente in der Farm (Mission critical Farm)
    
- Die Compliance-Standards erfüllt
    
- Anpassungen
    
Wenn Sie etwas entscheidend für Ihr Unternehmen aus der SharePoint-Farm ausführen, sagen Sie es einen umfangreichen Katalog von wichtigen Daten zu Anforderungen für den Client fungiert, kann sich ein Häkchen neben 'Kritischen apps' befinden, aber auch Verfügbarkeit – d. h., Ihr Unternehmen wäre erforderlich, wenn Sie für eine Weile SharePoint verwenden konnte nicht betroffen. Sie können ebenso "Anpassungen" überprüfen, da die kritischen Ihrer Farm Dienste, die Angebote basieren auf benutzerdefinierter Code, Websitedefinitionen oder eine Anzahl von Anpassungen, die zusammenarbeiten.
  
Wenn SharePoint diese Anforderungen erfüllt ohne nichts außerhalb mit, was in die Software integriert ist und Sie in der Regel aktualisieren und Suchtool normalen Verwaltung und Wartung, Sie haben "Integrierter SharePoint" – dies möglicherweise auch Ihre Grund für die auf einer älteren Version von SharePoint. Anders ausgedrückt, dies bereits der Fall ist, was Sie es benötigen, und Sie benötigen hatte keine bis jetzt am Ende der Unterstützung von Microsoft Office SharePoint Server 2007 aktualisieren.
  
Wenn Sie-Aufzählung folgende Punkte Sie Kriterien für das Upgrade erstellen. Anders ausgedrückt, müssten alle Upgrade erfüllen diese Leiste gezogen werden. Dies bietet eine Möglichkeit, Methoden auszuschließen, die derzeit nicht Ihren Anforderungen passen.
  
### <a name="a-simple-sample-plan"></a>Ein einfaches Beispielplan

Es muss möglicherweise werden breiter Klärung mit führende und anderen Administratoren auf dem Pfad, den das SharePoint-Upgrade dauern wird. SharePoint Server-Administratoren zusammen mit Microsoft SQL Server-Admins häufig, arbeiten mit Netzwerk und Sicherheit Teams und vieles mehr. Viele der Beteiligten vorhanden sind, müssen Sie zum Erstellen der Vereinbarung für oder zum Anpassen des Plans für Upgrade und Migration. Beispielsweise wenn Sie Daten migrieren, sodass Teil Ihres Unternehmens in Office 365 SharePoint Online verwendet wird, müssen es höchstwahrscheinlich leistungsoptimierung oder innerhalb des Netzwerks Testen sein. Betroffenen Teams sollte im Voraus informiert werden.
  
In diesem einfachen Beispiel ich ein SharePoint-Administrator Vorschlag anzeigen und Listen Sie die Plan, die alle Beteiligten vereinbart. Aus Gründen der Übersichtlichkeit Ihrer Agreements und Entscheidungen des Dokuments.
  
Der Plan beginnt nach einer Farm eine detaillierte Analyse und versucht, die Rolle der Farm, Schwachpunkte und andere wichtige Informationen, die einige Upgradeoptionen Eingrenzung führt zu identifizieren. Danach erfolgt ein Upgrade Angebot von SharePoint-Administrator, und Beteiligten vereinbaren eines Aktionsplans.
  
Meine Liste mit Bildaufzählungszeichen "wichtigsten":
  
- Verfügbarkeit, Features, die auf SharePoint, integrierte und Compliance-Standards.
    
- Die meisten Daten ist auf drei von Websitesammlungen mit einem Besprechungsarbeitsbereich von einem Entwicklungsteam besonders wichtig und in verschiedenen Zeitzonen extra fette verwendet weltweit verwendet.
    
- Es gibt siebzehn anderen Websites, die in großem Maß genutzt werden.
    
- Zwei Dokumentbibliotheken (Besprechungsarbeitsbereich und Dokumenten auf der Stammwebsitesammlung) sind größten (jede über 8000 Dokumente). Wir haben eine große Anzahl von archivierten Dokumente und Listen mit Kalkulationstabelle Anlagen.
    
- Es gibt vierzehn Listen, Bibliotheken, die vertrauliche Daten enthalten, die im Compliance bleiben muss.
    
- Wir benötigen die Möglichkeit, Archive und elektronische Ermittlung tun wir überall.
    
- Einige dieser Daten müssen lokal, aufgrund von InfoSec Regeln bleiben.
    
 **Meine Auswahlmöglichkeiten Upgrade und Migration:**
  
|||
|:-----|:-----|
|**Ja** <br/> |**Nein** <br/> |
|Upgrade von Datenbanken mit Datenbank anfügen  <br/> |Direktes Upgrade  <br/> |
|Upgrade mit Farmen Side-by-side  <br/> |Hybridupgrades  <br/> |
|Migration API an SPO in Office 365 (für persönliche Websitedaten)  <br/> |SharePoint Hybrid (noch nicht erforderlich)  <br/> |
|Einige Datenmigration manuelle mit SharePoint Online für wichtige Daten  <br/> |Schnelle Assistenten Upgrade auf Office 365  <br/> |
   
 **Meine vorgeschlagenen planen:**
  
Upgrade lokal, mit Versionen von SharePoint Side-by-Side, einige virtualisiert werden, sodass wir zunächst die Datenbanken aktualisieren können. Wechseln Sie von SharePoint 2007 auf SharePoint 2010. Testen die resultierende Farm Administratoren und Entwickler. Benutzer testen die resultierende Farm. Beheben Sie Probleme anzeigen Öffnungsvorgangs während dieser Zeit. In diesem Fall Side-by-Side, aktualisieren Sie SharePoint 2010-Datenbanken auf SharePoint 2013. Pilotphase/Test Benutzer testen. Beheben Sie Probleme anzeigen Öffnungsvorgangs während dieser Zeit.
  
- Sollten Sie eine Suche Federated hybride mit SPO Ihren Anforderungen entspricht.
    
- Erwägen Sie die [Unterstützung für schnelle](https://fasttrack.microsoft.com) , wenn Sie hier nach SharePoint Online aktualisieren möchten. 
    
- Ermitteln Sie, ob alle Websitesammlungen an ein Office 365-Abonnement übergeben werden können. (Office 365 erfüllt viele [Compliance-Standards](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 verfügt über [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) und über das Compliance Center [enthält](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) Möglichkeiten.) 
    
Anderenfalls fahren Sie mit einer Side-by-Side-Upgrade auf SharePoint Server 2016.
  
> [!NOTE]
> Zwischen Empfehlungen, die durch die Planung Administratoren sind des Upgrades und die eigentliche mit anderen Beteiligten nutzt die auf denen das Upgrade erfolgen Unterhaltungen. In einigen Fällen erzwingen Wirtschaftlichkeit beispielsweise Administratoren ihre Pläne ändern. Aufbauen, die abschließende Entscheidung ist, sollten Sie dokumentieren, was der vereinbarten Plan ist, vorwärts. Es kann wie folgt aussehen: 
  
 **Meine Aktion planen:**
  
Lokal, wir eine virtuelle Umgebung verwenden, um die standardmäßige SharePoint Server 2010 und 2013 erstellen. SharePoint Server 2016 wird auf neuer Hardware erstellt, die an das System für 2016 erfüllt. Wir fügt zum upgrade von Datenbanken von SharePoint 2007 über alle Versionen zwischen diesem und 2016 für SharePoint Server-Datenbank. Core Anpassungen sind für neu erstellt wird und getestet in sharepointserver 2016-Umgebung zu diesem Zeitpunkt wenn systemeigene Funktionen nicht bereits unsere Bedürfnissen entsprechen. Wenn wir erfolgreich ausgeführt werden, haben wir eine lokale Farm auf neuer Hardware mit aktualisierten Datenbanken und weniger Anpassungen. Wir werden die aktualisierten Inhaltsdatenbanken für neue Websitesammlungen in SharePoint Server 2013, Test, Benutzer Test/Pilotprojekt Anfügen und dann führen Sie einen DNS Abnahme in die neue SharePoint Server 2016 Umgebung für die Verwendung von live.
  
- Wir wird jetzt nicht Federated Hybrid zwischen SharePoint Server 2016 und SharePoint Online berücksichtigen.
    
- Schätzungsweise 35 % der Websites unserer können in neue SPO-Websites mit Vanity Domänen aktiviert, oder, letztendlich werden aus OneDrive for Business-Speicher. Suchen Sie für andere Möglichkeiten zum Konvertieren von Websites oder neue Websites an SPO weiterleiten.
    
- Einige dieser Teil der Migration werden manuell, durch Drag-and-Drop zu OneDrive für Unternehmen persönliche Websites, und einige von Migration API.
    
Weitere ausführliche Schritte oder eine Anzahl von Links zu bestimmten Upgrade Anweisungen befolgen eines Plans. Der MOSS 2007-Computer sollte nicht außer und virtuelle Umgebungen sollten aus Gründen der Vergleich verwaltet werden. jedoch ist das Upgrade abgeschlossen, wenn Benutzer in SharePoint Server 2016 umgeleitet werden.
  
Häufig wichtige Faktoren bei der Auswahl einer Methode sind die Gesamtkosten des Upgrades und die Kosten in der Zeit (mehr dazu im Artikel Wegweiser für SharePoint-Migration angezeigt). Allerdings Planung hingegen profitiert Sie erheblich in Richtwert mit Bedacht, auswählen und welche Erfolg framing sieht wie folgt aus.
  
## <a name="related-links"></a>Verwandte Links

[Ressourcen zum upgrade von Office 2007-Servern und clients](upgrade-from-office-2007-servers-and-products.md)
  
[Die Suche nach Microsoft Lifecycle Policy und Lebenszyklus](https://support.microsoft.com/en-us/lifecycle)
  
[Suchen Sie nach Microsoft Partners Upgrade und migration](https://partnercenter.microsoft.com/en-us/pcv/search)
  

