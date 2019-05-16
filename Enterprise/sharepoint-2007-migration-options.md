---
title: Zu berücksichtigende SharePoint 2007-Migrationsoptionen
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
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
description: SharePoint Server 2007 hat das Ende der Unterstützung erreicht, und es ist an der Zeit, ein Upgrade durchführen. Verwenden Sie diesen Artikel, um Ihren Plan zu erstellen.
ms.openlocfilehash: 98151ecd32f0066f583da1142d6010d46e120a43
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070701"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Zu berücksichtigende SharePoint 2007-Migrationsoptionen

Microsoft SharePoint 2007 und SharePoint Server 2007 haben das Ende des Supports erreicht. Es ist Zeit für ein Upgrade! Dieser Artikel enthält Informationen zu den Migrationsoptionen.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Allgemeine Upgrade-Strategien für SharePoint

Es gibt mehrere Methoden zum Aktualisieren einer SharePoint Server-Umgebung. Wenn Sie über eine Microsoft Office SharePoint Server 2007-Farm verfügen, finden Sie im folgenden einige Beispiele für die Upgrade-Methoden:
  
- Update durch Datenbankanfügungen
    
- Paralleles Upgrade
    
- Direktes Upgrade
    
- Hybrides Upgrade (direkt mit getrennten Datenbanken/separater Datenbankanfügung)
    
- SharePoint-Hybriden (Verbinden von Online mit lokalem SharePoint)
    
- Manuelles Verschieben von Daten zwischen Websitesammlungen oder Bibliotheken
    
- Upgrade auf Office 365 ([SharePoint Online Deployment Advisor](https://aka.ms/spoguidance))
    
- Migrations-API zu SharePoint Online (SPO) in Office 365
    
Was eignet sich am besten für Sie?
  
Ihre Kenntnisse darüber, was Ihre Farm macht und wofür Sie verwendet wird, ist eine taktische Stärke beim Upgrade. Die Art und Weise, wie Benutzer die SharePoint-Farm verwenden, unterstützen Sie bei der Auswahl Ihrer Optionen.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 hat auch eine schrittweise Aktualisierung, die hier nicht behandelt wird. Eine Liste mit Schritt spezifischen Upgrade-Artikeln finden Sie unter [SharePoint Server 2007 End of Support Roadmap](sharepoint-2007-end-of-support.md). 
  
Denken Sie daran, den [Produktlebenszyklus](https://support.microsoft.com/en-us/lifecycle/search) und die System Anforderungen für die SharePoint-Version zu überprüfen, auf die Sie ein Upgrade durchführen. Dies ist so, dass Sie wissen, wann das nächste Upgrade erforderlich ist (wenn Sie beispielsweise bei einem Legacy Produkt wie SharePoint Server 2010 anhalten, um weitere Upgrades zu planen), und um sicherzustellen, dass Sie über Hardware verfügen, die ihren Plan unterstützt. 
  
Wenn Sie planen, einige oder alle Ihrer SharePoint-Websites in der Cloud in Office 365 zu überführen, ist dies eine Zeit, um einen Link zu den [Dienstbeschreibungen für Office 365](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)zu markieren. Sie benötigen die Dienstbeschreibungen, um mehr über SharePoint Online-Features zu erfahren und wie diese von lokalen SharePoint-Servern abweichen können. Aktualisieren Sie funktionale Microsoft Office SharePoint Server 2007-Farmen. Wenn die Installation von Websites unterbrochen wurde, beheben Sie diese vor dem Upgrade.
  
## <a name="a-note-about-managing-risk"></a>Ein Hinweis zum Verwalten von Risiken

Methoden wie "nebeneinander" sind im Schema der Aktualisierungslogik wichtig. Beim Upgrade von Side-by-Side führen Sie Ihre Microsoft Office SharePoint Server 2007-Farm aus, erstellen jedoch eine Farm mit der nächsten Version (SharePoint Server 2010) auf neuer Hardware. Dies hat drei Möglichkeiten:
  
1. Sie können mithilfe von Datenbankanfügung Sicherungen Ihrer Microsoft Office SharePoint Server 2007-Datenbanken ausführen, um Sie einzeln zu aktualisieren.
    
2. Wenn Sie herausfinden, dass nur eine kleine Anzahl von wichtigen Dokumentbibliotheken und anderen Informationen in Ihrer Microsoft Office SharePoint Server 2007-Farm verwendet wird, können Sie die Daten manuell aus Microsoft Office SharePoint Server 2007 in SharePoint Server 2010 verschieben. , oder nehmen Sie nur bestimmte Websites und Webs auf die nächste Version (was Ihre Arbeit erleichtern kann).
    
3. Je geringer die Microsoft Office SharePoint Server 2007-Serverfarm ist, desto sicherer sind die Daten, die in der Farm beim Upgrade enthalten sind.
    
Methoden wie in-Place-Upgrades fungieren direkt in Ihrer Microsoft Office SharePoint Server 2007-Farm, sodass Sie weniger einfache Optionen zum aufgeben eines Pfads und zur Wiederaufnahme der ursprünglichen Umgebung benötigen. Erstellen Sie so viel wie möglich einige Sicherheitsmaßnahmen (wie das übernehmen und Testen von Sicherungen der ursprünglichen Umgebung). Wenn Ihre Microsoft Office SharePoint Server 2007-Farm beispielsweise virtuell ist und zum Zwecke der Sicherung und Wiederherstellung dupliziert wird, sichern und Wiederherstellen Sie die aktuellsten Datenbanken vor dem Dienstfenster für das Upgrade. Wenn Sie wissen, dass Sie die Option zum Wiederherstellen von Datenbanksicherungen haben, erhalten Sie nicht nur ein ausfallsicheres, sondern Sie können sich auch beruhigen.
  
> [!TIP]
> Bewährte Methoden für das Upgrade sind für [Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/en-us/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/en-us/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/en-us/library/cc261992%28v=office.15%29.aspx)und [SharePoint Server 2016](https://technet.microsoft.com/en-us/library/cc261992%28v=office.16%29.aspx)vorhanden. Sie können auch nach [Microsoft-Partnern](https://partnercenter.microsoft.com/en-us/pcv/search) suchen, die über Erfahrung mit Upgrades oder Office 365-Migrationen verfügen. 
  
## <a name="make-your-plan"></a>Planen

Wenn Sie ein Upgrade durchführen müssen, benötigen Sie einen Plan, und eine Größe, die in diesen Fällen nicht alle passt. Ihr Plan ist möglicherweise so einfach wie "ein Office 365-Abonnement mit SharePoint Online erstellen, eine Domäne registrieren und Personen umleiten, um Ihre Dateien dort zu speichern". Möglicherweise nicht. Diese Entscheidung liegt bei Ihnen, und es liegt an dem, was Sie und Ihre Benutzer wirklich benötigen.
  
> [!NOTE]
> Es ist riskant, auf Software auszuführen, deren Lebenszyklus beendet wurde. Produkte, die nicht unterstützt werden, werden nicht mehr gepatcht, wenn Probleme gefunden werden. Dies führt auch dazu, dass bei neuen Sicherheitsbedrohungen keine Sicherheitspatches oder-Fixes vorhanden sind, da die End-of-Lifecycle-Produkte nicht mehr unterstützt werden. Vermeiden Sie diese Situation! 
  
### <a name="first-know-your-farm"></a>Zuerst wissen Sie Ihre Farm

Bei der Aktualisierung sollte ihre Entscheidungsfindung davon abhängen, was Ihre Farm für Ihre Organisation tut. Welche Anforderungen genügt es? Welche Rolle spielt es? Jede Farm in Ihrem Unternehmen hat möglicherweise eine andere Rolle. Einige Ihrer SharePoint-Farmen sind möglicherweise *kritisch* , einige sind möglicherweise Dateiarchive--dort zur Aufbewahrung. Oder wenn Ihre Farm viele Rollen gleichzeitig ausfüllt, müssen Sie möglicherweise wissen, welche Websitesammlungen, Websites oder sogar Dokumentbibliotheken ausgeführt werden, Anpassungen vornehmen und wie wichtig diese sind. Die Analyse Ihrer Daten auf dieser Ebene mag viel Arbeit sein, aber es spart Zeit und Aufwand, Ihre Domäne zu meistern, bevor Sie ein Upgrade durchführen oder migrieren. Sobald Sie alle bewegten Teile und die wichtigsten Bits kennen, wissen Sie auch, was Sie herausgewachsen und hinterlassen können. Dieses Wissen profitiert nur von Ihnen. 
  
Was sagen die Benutzer am wichtigsten über Ihre SharePoint Server-Farm?
  
- Integrierte SharePoint-Features
    
- Der umfangreiche Datenkorpus (beispielsweise ein Archiv von Dateien)
    
- Verfügbarkeit
    
- Wichtige apps, Webparts oder Dokumente in der Farm (missionskritische Farm)
    
- Einhaltung der Compliance-Standards
    
- Anpassungen
    
Wenn Sie in Ihrer SharePoint-Farm etwas Wesentliches für Ihr Unternehmen ausführen, sagen Sie, dass es wie ein umfangreicher Katalog wichtiger Daten zu Clientdienstanforderungen fungiert, können Sie eine Zecke neben "kritische Apps" setzen, aber auch "Verfügbarkeit" – das heißt, Ihr Unternehmen wäre Auswirkungen, wenn SharePoint für eine Weile nicht verwendet werden konnte. Entsprechend können Sie "Anpassungen" auch überprüfen, da die von Ihrer Farm bereitgestellten wichtigen Dienste auf benutzerdefiniertem Code, Websitedefinitionen oder einer Reihe von Anpassungen basieren, die zusammenarbeiten.
  
Wenn SharePoint diese Anforderungen erfüllt hat, ohne dass Sie irgendetwas außerhalb der Verwendung der integrierten Funktionen der Software tun müssen, und Sie es in der Regel aktualisieren und normale Verwaltung und Wartung durchführen, haben Sie möglicherweise "Built-in SharePoint" gewählt--Dies kann auch Ihr Grund für die Sitzung auf einer älteren Version von SharePoint. Mit anderen Worten: es erledigt bereits das, was Sie benötigen, und Sie haben noch kein Upgrade auf Microsoft Office SharePoint Server 2007 End of Support erforderlich.
  
Wenn Sie diese Aufzählungszeichen auflisten, erstellen Sie Kriterien für Ihr Upgrade. In anderen Worten: jedes Upgrade müsste in Betracht gezogen werden. Auf diese Weise können Sie Methoden ausschließen, die derzeit nicht Ihren Anforderungen entsprechen.
  
### <a name="a-simple-sample-plan"></a>Ein einfacher Beispielplan

Möglicherweise müssen Sie einen umfassenderen Konsens mit Führungskräften und anderen Administratoren auf dem Weg Ihres SharePoint-Upgrades erzielen. SharePoint Server-Administratoren kooperieren häufig mit Microsoft SQL Server-Admins, arbeiten mit Netzwerk-und Sicherheitsteams und vielem mehr. Wenn es viele Beteiligte gibt, müssen Sie möglicherweise einen Vertrag für den Upgrade-und Migrationsplan erstellen oder anpassen. Wenn Sie beispielsweise Daten migrieren, sodass ein Teil Ihres Unternehmens SharePoint Online in Office 365 verwendet, müssen Sie wahrscheinlich die Leistungsoptimierung oder Tests in Ihrem Netzwerk vornehmen. Betroffene Teams sollten vorab informiert werden.
  
In meinem einfachen Beispiel wird der Vorschlag eines SharePoint-Administrators angezeigt und dann der Plan aufgeführt, auf den alle Beteiligten abgestimmt haben. Um Klarheit zu schaffen, dokumentieren Sie Ihre Vereinbarungen und Entscheidungen.
  
Der Plan beginnt nach einer eingehenden Analyse einer Farm und versucht, die Rolle der Farm, die Problempunkte und andere wichtige Informationen zu identifizieren, die dazu führen, dass einige Upgrade-Optionen eingeschränkt werden. Anschließend wird ein Upgrade-Vorschlag vom SharePoint-Administrator durchgeführt, und die beteiligten vereinbaren einen Aktionsplan.
  
Meine "wichtigste" Aufzählungszeichen Liste:
  
- Verfügbarkeit, integrierte Funktionen in SharePoint und Compliance-Standards.
    
- Der größte Teil der Daten besteht aus drei Websitesammlungen, wobei ein von einem Entwicklungsteam verwendeter Besprechungsarbeitsbereich besonders wichtig ist und in mehreren Zeitzonen weltweit stark verwendet wird.
    
- Es gibt siebzehn weitere Websites, die häufig verwendet werden.
    
- Zwei Dokumentbibliotheken (Besprechungsarbeitsbereich und Dokumente in der Stammwebsitesammlung) sind am größten (über 8000 docs). Es gibt eine Vielzahl von archivierten Dokumenten und Listen mit Arbeitsblatt Anlagen.
    
- Es gibt vierzehn Listen mit Bibliotheken mit vertraulichen Daten, die in Compliance bleiben müssen.
    
- Wir müssen in der Lage sein, halte-und e-Discovery-Aufgaben zu erledigen.
    
- Einige dieser Daten müssen aufgrund von INFOSEC-Regeln lokal bleiben.
    
 **Meine Upgrade-und Migrationsoptionen:**
  
|||
|:-----|:-----|
|**Ja** <br/> |**Nein** <br/> |
|Aktualisieren von Datenbanken mit Datenbankanfügung  <br/> |Direktes Upgrade  <br/> |
|Paralleles Upgrade mit Farmen  <br/> |Hybrid Upgrade  <br/> |
|Migrations-API zu SPO in Office 365 (für persönliche Website-Daten)  <br/> |SharePoint-Hybrid (noch nicht erforderlich)  <br/> |
|Einige manuelle Datenmigrationen zu SharePoint Online für wichtige Daten  <br/> |Update des Assistenten auf Office 365  <br/> |
   
 **Mein geplanter Plan:**
  
Aktualisieren Sie lokal mit Versionen von SharePoint, die parallel ausgeführt werden, so dass wir die Datenbanken zuerst aktualisieren können. Wechseln Sie von SharePoint 2007 zu SharePoint 2010. Administratoren und Entwickler testen die resultierende Farm. Benutzer testen die resultierende Farm. Beheben Sie während dieser Zeit alle Probleme beim Anzeigen anhalten. Aktualisieren Sie erneut SharePoint 2010-Datenbanken auf SharePoint 2013. Test. Benutzer Test/Pilot. Beheben Sie während dieser Zeit alle Probleme beim Anzeigen anhalten.
  
- Überlegen Sie, ob eine Such Verbund-Hybrid Lösung mit SPO Ihren Anforderungen entspricht.
    
- Erwägen Sie die Hilfe bei der [Unterstützung](https://fasttrack.microsoft.com) , wenn Sie von hier aus ein Upgrade auf SharePoint Online durchführen möchten. 
    
- Bestimmen Sie, ob Websitesammlungen zu einem Office 365-Abonnement abgeladen werden können. (Office 365 erfüllt viele [Compliance-Standards](https://technet.microsoft.com/library/office-365-compliance.aspx). Office 365 verfügt über [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) und kann über das Compliance Center [verwaltet](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) werden.) 
    
Fahren Sie andernfalls mit einem parallelen Upgrade auf SharePoint Server 2016 fort.
  
> [!NOTE]
> Zwischen den Empfehlungen der Administratoren, die das Upgrade und den tatsächlichen Prozess planen, handelt es sich um die Unterhaltungen bei anderen Beteiligten, auf denen das Upgrade basiert. Beispielsweise zwingt Economics Administratoren manchmal, ihre Pläne zu ändern. Was auch immer die endgültige Entscheidung ist, sollten Sie dokumentieren, was der vereinbarte Plan ist, vorwärts gehen. Es könnte ungefähr wie folgt aussehen: 
  
 **Mein Aktionsplan:**
  
Lokal verwenden wir eine virtuelle Umgebung zum Erstellen von SharePoint Server 2010 und 2013. SharePoint Server 2016 basiert auf neuer Hardware, die die Systemanforderungen für 2016 erfüllt. Wir führen Datenbankanfügungen zum Upgrade von Datenbanken von SharePoint 2007 über alle Versionen zwischen IT und SharePoint Server 2016 aus. Kern Anpassungen werden in der SharePoint Server 2016-Umgebung zu diesem Zeitpunkt neu erstellt und getestet, wenn systemeigene Features unsere Anforderungen nicht bereits erfüllen. Wenn wir erfolgreich sind, verfügen wir über eine lokale Farm auf neuer Hardware mit aktualisierten Datenbanken und weniger Anpassungen. Wir fügen die aktualisierten Inhaltsdatenbanken an neue Websitesammlungen in SharePoint Server 2013, Test, User Test/Pilot, und führen dann eine DNS-Überprüfung auf die neue SharePoint Server 2016-Umgebung für die Live-Nutzung aus.
  
- Wir werden den Verbund Hybrid zwischen SharePoint Server 2016 und SharePoint Online derzeit nicht berücksichtigen.
    
- Schätzungsweise 35% unserer Websites können in neue SPO-Websites mit Vanity-Domänen umgewandelt werden oder schließlich zu OneDrive für Unternehmen werden. Suchen Sie nach anderen Möglichkeiten, Websites zu konvertieren oder neue Websites an SPO zu leiten.
    
- Einige dieser Teile der Migration sind manuell, per Drag-and-Drop zu OneDrive for Business-persönlichen Websites und einige von der Migrations-API.
    
Detailliertere Schritte oder eine Reihe von Links zu bestimmten Upgrade-Richtungen sollten einem Plan folgen. Der MOSS 2007-Computer sollte nicht außer Betrieb genommen werden, und virtuelle Umgebungen sollten im Interesse des Vergleichs beibehalten werden. das Upgrade ist jedoch abgeschlossen, wenn Benutzer zu SharePoint Server 2016 umgeleitet werden.
  
Häufig sind Hauptfaktoren bei der Auswahl einer Methode die Gesamtkosten des Upgrades und die Kosten in der Zeit (Weitere Informationen dazu finden Sie im SharePoint Migration Roadmap-Artikel). Allerdings wird die Planung im Voraus Ihnen große Vorteile bei der Festlegung der Erwartungen, wählen Sie mit Bedacht und Framing, was den Erfolg aussehen wird.
  
## <a name="related-links"></a>Verwandte Links

[Ressourcen für das Upgrade von Office 2007-Servern und-Clients](upgrade-from-office-2007-servers-and-products.md)
  
[Microsoft Lifecycle Policy und Lebenszyklus Suche](https://support.microsoft.com/en-us/lifecycle)
  
[Suchen nach Microsoft-Partnern, die beim Upgrade oder bei der Migration helfen können](https://partnercenter.microsoft.com/en-us/pcv/search)
  

