---
title: Upgrade von SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
description: SharePoint 2010 und SharePoint Server 2010 sind Ablauf des Supports fast erreicht. Verwenden Sie diesen Artikel als Leitfaden zum upgrade auf SharePoint Online oder eine neuere Version von SharePoint Server lokal.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169867"
---
# <a name="upgrading-from-sharepoint-2010"></a>Upgrade von SharePoint 2010

Auf dem 13 OAT 2020 erreicht Microsoft Office SharePoint Server 2010 Ablauf des Supports. In diesem Artikel werden Ressourcen, die Benutzer migrieren ihre vorhandenen SharePoint Server 2010-Daten nach SharePoint Online, oder aktualisieren Sie Ihre lokalen SharePoint Server unterstützen.
  
## <a name="what-is-end-of-support"></a>Was ist der Ablauf des Supports?

Wenn Ihre sharepointserver 2010 und SharePoint Foundation 2010-Software das Ende des Supportlebenszyklus (die Zeit erreicht, in dem Microsoft neue Features, Updates, Sicherheitspatches und usw. bietet) ist dies die Software 'Ablauf des Supports ', aufgerufen oder, In manchen Fällen seine 'Stilllegung". Nach Ende der Unterstützung (oder EOS) eines Produkts nothing tatsächlich heruntergefahren oder funktioniert; bietet jedoch am Ende der Unterstützung für Software, Microsoft nicht mehr:
  
- Technischen Support für Probleme, die auftreten können.
    
- Fehlerbehebungen für Probleme, die ermittelt werden und kann, die die Stabilität und Verwendbarkeit des Servers auswirken;
    
- Sicherheitsupdates für Sicherheitsrisiken, werden erkannt und, die möglicherweise den Server anfällig für Sicherheitslücken;
    
- Zeitzone aktualisiert.
    
Das bedeutet, fallen keine weiteren Updates, Patches oder Updates werden für das Produkt (einschließlich Patches/Sicherheitspatches) ausgeliefert und Microsoft Support wird haben vollständig verschoben Einsatz Support zu neueren Versionen. Wie das Ende der Unterstützung von SharePoint Server 2010 nähert, sollten Sie ergreifen Chancen zu erhöhen, Daten, die Sie nicht mehr benötigen, vor dem Aktualisieren des Produkts und/oder Migrieren der Daten wichtigen.
  
> [!NOTE]
> Software-Lebenszyklus dauert in der Regel für zehn Jahren ab dem Zeitpunkt der ersten Version des Produkts. Sie können für [Microsoft-Partner](https://go.microsoft.com/fwlink/?linkid=841249) suchen, die mit dem Upgrade auf die nächste Version der Software oder mit Office 365-Migration (oder beides) helfen können. Stellen Sie sicher, dass Sie über Ende des Zeitraums auf wichtige zugrunde liegenden Technologien auch Unterstützung besonders der Version von SQLServer sind mit SharePoint verwendeten. 
  
## <a name="what-are-my-options"></a>Welche Optionen sind?

Überprüfen Sie zunächst das Datum, bei die Unterstützung endet auf der [Website des Produktlebenszyklus](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010). Im nächsten Schritt müssen Sie Ihre Zeit Upgrade oder die Migration mit Kenntnisse von diesem Datum planen. Denken Sie daran, dass Ihr Produkt *wird nicht mehr funktionieren* zum Zeitpunkt aufgeführt, und Sie können ihre Verwendung weiterhin, aber, seit die Installation nach diesem Zeitpunkt nicht mehr gepatcht werden muss, Sie eine Strategie sollten, die Sie reibungslosen Übergang zur nächsten Version unterstützen des Produkts. 
  
Diese Matrix hilft bei der einen Kurs gezeichnet wird, wenn es zum Migrieren von Produktfeatures und Benutzerdaten stammt:
  
|**Ende des Support-Produkt**|**Gut**|**Optimal**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint-Hybridlösung  <br/> |SharePoint Server 2016 (lokal)  <br/> |
|||SharePoint-Cloud-Hybridsuche  <br/> |
   
Wenn Sie die Optionen am unteren Ende der Skala (gute Optionen) auswählen, müssen Sie zum Starten der Planung für das Upgrade von einer anderen sofort nach Abschluss der Migration von SharePoint Server 2010. (Ablauf des Supports für SharePoint Server 2010 und SharePoint Foundation 2010 für Office-Anpassungstool 13, 2020 geplante, aber, Sie stets sollten, *beachten* überprüfen Sie die [Product Lifecycle-Website](https://support.microsoft.com/en-us/lifecycle) nach Ihrer genauesten Datumsangaben!) 
  
## <a name="where-should-i-go-next"></a>Wo soll ich weiter?

SharePoint Server 2013 und SharePoint Foundation 2013 kann lokal installiert auf Ihren eigenen Servern entsprechen. Andernfalls können Sie SharePoint Online und dem ist ein Onlinedienst, der Teil von Microsoft Office 365 ist. Sie können Folgendes festlegen:
  
- Migration zu SharePoint Online
    
- Aktualisieren von SharePoint Server oder SharePoint Foundation lokalen
    
- Führen Sie beide oben genannten Antworten
    
- Implementieren Sie eine [SharePoint-Hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) -Lösung 
    
Achten Sie auf versteckte Kosten für die Verwaltung von einer Serverfarm vorwärts, Wartung oder Migrieren von Anpassungen und Aktualisieren der Hardware, die von der SharePoint-Server abhängt. Wenn Sie wissen, und für alle diese berücksichtigt haben, wird es einfacher, um die Aktualisierung der lokale sein. Andernfalls, wenn Sie Ihre Farm in SharePoint-Legacyserver ohne extra fette Anpassung ausführen, würden Sie aus einer geplanten Migration zu SharePoint Online profitieren. Es ist außerdem möglich, die in der lokalen SharePoint Server Geschäfte opt möglicherweise, um einige Daten in SharePoint Online zum Reduzieren der Hardware Management bleiben umfasst ihre lokalen Daten zu. Es möglicherweise günstiger, einige Daten in SharePoint Online zu verschieben.
  
> [!NOTE]
> SharePoint-Administratoren können [ein Office 365-Abonnement zu erstellen](https://go.microsoft.com/fwlink/?linkid=843152), richten Sie eine völlig neue SharePoint Online-Website, und klicken Sie dann ordnungsgemäß, Ausschneiden Weg von SharePoint Server 2010 Nutzen der nur die wichtigsten Dokumente, die aktuell SharePoint Online-Websites. Dort können alle verbleibenden Daten von der SharePoint Server 2010-Website in lokale Archive ein Ausgleich vorgenommen werden. 
  
|**SharePoint Online (SPO)**|**SharePoint Server lokal**|
|:-----|:-----|
|Hohe Kosten in Zeit (Plan / Ausführung / Überprüfung)  <br/> |Hohe Kosten in Zeit (Plan / Ausführung / Überprüfung)  <br/> |
|Niedrigere Kosten in Mittel (keine Hardware Einkauf)  <br/> |Höhere Kosten in Mittel (Hardware Einkauf)  <br/> |
|Einmalige Gebühr bei der migration  <br/> |Einmalige Gebühr pro zukünftige Migration wiederholt  <br/> |
|Geringe Gesamtbetriebskosten / Wartung  <br/> |Hohe TCO / Wartung  <br/> |
   
Bei der Migration zu Office 365 Verschieben der einmaligen schwerer Kosten Zeitpunkt Planung im Vorfeld ausgegeben haben soll (während Sie Daten organisieren und entscheiden, was in die Cloud zu übernehmen und was zurückbleiben). Nach der Migration Ihrer Daten werden Upgrades jedoch automatische ab diesem Zeitpunkt sehen, wie Sie nicht mehr zum Verwalten von Hardware und Software Updates benötigen und die Betriebszeit Ihrer Farm eine Microsoft Service Level Agreements ([SLAS](https://go.microsoft.com/fwlink/?linkid=843153)) gesichert werden wird.
  
### <a name="migrate-to-sharepoint-online"></a>Migration zu SharePoint Online

Stellen Sie sicher, dass SharePoint Online alle Features bietet, die Sie benötigen, durch die Überprüfung der zugeordneten Service Description. Nachfolgend finden Sie der Link, um alle Office 365-Dienstbeschreibungen:
  
[Office 365-Dienstbeschreibungen](https://go.microsoft.com/fwlink/?linkid=272060)
  
Ist zurzeit eine Möglichkeit, mit dem Sie direkt von SharePoint Server 2010 (oder SharePoint Foundation 2010) mit SharePoint Online migrieren können, also Teil der Arbeit wird manuell gesteuert. Dies Sie geben die Möglichkeit, Archivierung und Löschen von Daten und Websites, die nicht mehr, vor dem Verschieben benötigt werden. Sie können anderen Daten in den Speicher archivieren. Beachten Sie außerdem, dass weder für SharePoint Server 2010 als auch für SharePoint Foundation 2010 arbeiten am Ende des Support, beendet werden damit Administratoren einen Zeitraum können während, den SharePoint noch ausgeführt wird, wenn ihre Kunden vergessen, um einige Daten zu verschieben.
  
Wenn Sie ein auf SharePoint Server 2013 oder SharePoint Server 2016 Upgrade und Daten in SharePoint Online zu platzieren möchten, möglicherweise auch Ihre Move umfassen mithilfe der [Inhaltsmigrations-API für SharePoint](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) (zum Migrieren von Informationen in OneDrive für Unternehmen). 
  
|**Online Pro**|**Online Kohn**|
|:-----|:-----|
|Microsoft stellt SPO Hardware und die gesamte Hardware-Verwaltung.  <br/> |Verfügbare Features können zwischen SharePoint Server lokal und SPO abweichen.  <br/> |
|Sie sind der globale Administrator Ihres Abonnements und Zuweisen von Administratoren zu SPO Websites können.  <br/> |Einige Aktionen, die ein Farmadministrator in SharePoint Server lokal verfügbar sind nicht vorhanden (oder sind nicht erforderlich) in der SharePoint-Administrator-Rolle in Office 365, aber die SharePoint-Zentraladministration, die Verwaltung von Websitesammlungen und Websitebesitzes werden lokal in Ihrer org  <br/> |
|Microsoft wendet Patches, korrigiert und aktualisiert und der Hardware und Software (einschließlich SQL Server auf denen SharePoint Online ausgeführt).  <br/> |Da kein Zugriff auf das zugrunde liegende Dateisystem im Dienst vorhanden ist, sind einige Anpassungen beschränkt.  <br/> |
|Microsoft [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) veröffentlicht und verschiebt schnell in Service Level Vorfälle zu beheben.  <br/> |Sichern und Wiederherstellen und andere Optionen werden vom Dienst in SharePoint Online automatisiert - Sicherungen werden überschrieben wenn er nicht verwendet wird.  <br/> |
|Testen von Sicherheit und Server Performance tuning werden kontinuierlich im Dienst von Microsoft durchgeführt.  <br/> |In der Benutzeroberfläche und anderen SharePoint-Features werden vom Dienst installiert und aktiviert oder deaktiviert umgeschaltet werden möglicherweise geändert.  <br/> |
|Office 365 erfüllt viele Branchenstandards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |Unterstützung für die Migration [schnelle](https://go.microsoft.com/fwlink/?linkid=518597) ist beschränkt.  <br/> Ein Großteil des Upgrades werden manuelle oder über SPO-Inhaltsmigrations-API beschrieben, in der [Übersicht über OneDrive Migration Inhalte und SharePoint Online](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Microsoft-Supporttechniker weder Mitarbeiter im Rechenzentrum haben uneingeschränkten Administratorzugriff auf Ihr Abonnement.  <br/> |Wenn Hardware-Infrastruktur zur Unterstützung der neuen Version von SharePoint aktualisiert werden muss, oder eine sekundäre Farm für ein Upgrade erforderlich ist möglicherweise zusätzliche Kosten vor.  <br/> |
|Partner können mit der einmaligen Auftrag der Migrieren der Daten zu SharePoint Online unterstützen.  <br/> |Nicht alle Überarbeitungen in SharePoint Online befinden sich innerhalb des Steuerelements. Nach der Migration möglicherweise Design Unterschiede in Menüs, Bibliotheken und anderen Features vorübergehend Verwendbarkeit auswirken.  <br/> |
|Online Produkte werden automatisch aktualisiert, über den Dienst, d. h., obwohl Features verwerfen der können, keine true Ablauf des Supports Lebenszyklus ist.  <br/> |Es ist ein Ablauf des Supports Lebenszyklus für SharePoint Server (oder SharePoint Foundation) sowie zugrunde liegenden SQL Server.  <br/> |
   
Wenn Sie zum Erstellen einer neuen Office 365-Website entschieden haben, und werden manuell migrieren von Daten zu es benötigt wird, können Sie Ihre Office 365-Optionen rechts hier anzeigen:
  
[Optionen zum Office 365-Plan](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Upgrade von sharepointserver lokal

Während der neuesten Version des Produkts lokalen SharePoint (SharePoint Server 2016), SharePoint Server-Upgrades *Seriell* wechseln müssen, bedeutet dies, dass es ist nicht möglich, die von SharePoint Server 2010 auf SharePoint Server 2016, direkt aktualisieren. 
  
|||
|:-----|:-----|
||Serielle Upgrade Pfad ***: SharePoint Server 2010 **\>** SharePoint Server 2013 **\>** 2016 für SharePoint Server |
   
Wenn Sie auswählen, um den vollständigen Pfad von SharePoint 2010 auf SharePoint Server 2016 folgen, wird dies Zeit dauern und planen. Upgrades umfassen Kosten im Hinblick auf aktualisierten (Beachten Sie, dass SQL Server ebenfalls aktualisiert werden müssen) Hardware, Software und Verwaltung. Darüber hinaus müssen Anpassungen aktualisiert oder sogar aufgegeben werden. Stellen Sie sicher, dass Sie Notizen für alle Ihre kritischen Anpassungen sammeln, vor dem upgrade der SharePoint-Serverfarm.
  
> [!NOTE]
> Es ist möglich, Ihre Ende im Hinblick auf SharePoint 2010-Farm verwalten, Installieren einer 2016 für SharePoint Server-Farm auf neuer Hardware (also die separaten Farmen Side-by-Side ausgeführt werden), und klicken Sie dann planen und Ausführen einer manuellen Migrations von Inhalten (zum Herunterladen und Hochladen des Inhalts, erneut für Beispiel). Es gibt potenzielle Fehler an diese manuellen Verschiebungen (beispielsweise Dokumente, die von 2010 mit einer aktuellen zuletzt geänderte Kontos mit dem Alias des Kontos wie folgt die manuelle Verschiebung), und einige Arbeit vorausschauendes vorgenommen werden (Neuerstellen von Websites, Unterwebsites, Berechtigungen und Liste Strukturen). Es ist ein guter Zeitpunkt, zu berücksichtigen sind, benötigen Daten, die Sie in den Speicher oder nicht mehr verschieben können. Dies kann die Auswirkung der Migration verringern. In beiden Fällen Bereinigen der Umgebung vor dem upgrade. Stellen Sie sicher, dass die vorhandene Farm ist funktionsfähig, bevor ein Upgrade und (sicher), bevor Sie außer Betrieb setzen! 
  
Denken Sie daran, um die **unterstützte und nicht unterstützte Aktualisierungspfade**zu prüfen: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Wenn Sie **Anpassungen vorgenommen**haben, ist es wichtig, dass Sie einen Plan für jeden Schritt des Upgrades in der Migrationspfad haben: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Lokale Pro**|**Der lokale Kohn**|
|:-----|:-----|
|Vollzugriff auf alle Aspekte der SharePoint-Farm (und der SQL) aus der Serverhardware einrichten.  <br/> |Alle Seitenumbrüche und Updates sind die Verantwortung für Ihr Unternehmen "(aber Sie können kostenpflichtige Microsoft Support beteiligen, wenn Ihr Produkt nicht am Ende des Supports ist):  <br/> |
|Vollen Funktionsumfang von SharePoint Server lokal mit der Option zum Herstellen einer Verbindung Ihrer lokalen Farm eine SharePoint Online-Abonnement über Hybrid.  <br/> |Upgrade, Patches, Sicherheitspatches, Hardware-Upgrades und alle Wartung von SharePoint Server und der SQL-Farm sind lokale verwaltete.  <br/> |
|Vollzugriff für größere Anpassungsoptionen als mit SharePoint Online.  <br/> |[Compliance-Standards von Office 365 unterstützt](https://go.microsoft.com/fwlink/?linkid=843165) müssen manuell konfigurierten lokalen sein.  <br/> |
|Testen von Sicherheit und Server Performance tuning, ausgeführten Ihrer lokal (unter Ihrer Kontrolle).  <br/> |Office 365 möglicherweise Verfügbarmachen von Features für SharePoint Online, die nicht mit SharePoint Server lokalen zusammenarbeiten  <br/> |
|Partner können unterstützen, mit dem Migrieren von Daten auf die nächste Version von SharePoint Server (und darüber hinaus).  <br/> |SharePoint Server-Websites werden nicht automatisch [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) -Zertifikate verwenden, wie in SharePoint Online angezeigt wird.  <br/> |
|Volle Kontrolle über die Benennungskonventionen, Sicherung und Wiederherstellung und anderen Wiederherstellungsoptionen in SharePoint Server lokal.  <br/> |SharePoint Server lokal wurde Beachtung von Produktlebenszyklen.  <br/> |
   
### <a name="upgrade-resources"></a>Aktualisierung von Ressourcen

Beginnen Sie mit dem Vergleichen von Hardware-und softwareanforderungen. Wenn Sie grundlegende Anforderungen für das Upgrade auf die aktuelle Hardware nicht erfüllen, kann bedeuten müssen Sie zuerst die Hardware in der Farm oder von SQL Server aktualisieren oder möglicherweise einige Prozentsatz Ihrer Websites der 'immergrünen' Hardware des SharePoint Online verschieben möchten. Nachdem Sie Ihre Bewertung vorgenommen haben, führen Sie die Methoden und unterstützte Aktualisierungspfade.
  
- **Anforderungen für Hardware und Software**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [2016 für SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Softwarebeschränkungen und-Grenzen für**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [2016 für SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Übersicht über die Upgradeprozess für**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [2016 für SharePoint Server](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Erstellen einer SharePoint-Hybrid-Lösung zwischen SharePoint Online und SharePoint Server: lokal

Eine weitere Option (eine, die möglicherweise die beste aus lokalen und online Welten für einige Migration muss) ist eine hybride, Verbinden von SharePoint Server 2013 oder 2016 Farmen mit SharePoint Online zum Erstellen einer hybrides SharePoint: [erfahren Sie mehr über SharePoint-hybridlösungen ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Wenn Sie sich, dass eine hybride SharePoint-Serverfarm Migration Ziel ist es entscheiden, planen, welche Standorte und Benutzer, die Sie Online verschieben, sollten Sie unbedingt, und welche lokale bleiben müssen. Eine Überprüfung und Bewertung von der SharePoint-Serverfarm Inhalte (bestimmen, welche Daten hoch, Mittel oder niedrig Auswirkung Ihres Unternehmens ist) können hilfreich sein, die für diese Entscheidung sein. Es kann sein, dass das einzige benötigten für SharePoint Online freigeben (a) Benutzerkonten für die Anmeldung und (b) das SharePoint Server-Suchindex--ist dies möglicherweise nicht offensichtlich, bis Sie sehen, wie Ihre Websites verwendet werden. Wenn Ihr Unternehmen später entscheidet, aller Ihrer Inhalte zu SharePoint Online zu migrieren, können Sie alle verbleibenden Konten und Daten online verschieben und Außerbetriebnahme die lokalen Farm und Verwaltung der SharePoint-Farm erfolgt über Office 365 Konsolen von diesem Zeitpunkt an.
  
Achten Sie darauf, dass Sie sich mit den vorhandenen Typen der Hybrid und zum Konfigurieren der Verbindung zwischen Ihrer lokalen SharePoint-Farm und Ihre Office 365-Abonnements vertraut zu machen.
  
Eine gute Möglichkeit, finden Sie unter Funktionsweise eine Hybriden SharePoint-Farm ist, indem Sie eine [Office 365 Dev/Test-Umgebung](https://go.microsoft.com/fwlink/?linkid=843152)erstellen. Nachdem Sie eine Testversion oder Office 365-Abonnement erworben, Sie vermutlich auf dem Weg zum Erstellen von Websitesammlungen, Websites und Dokumentbibliotheken in SharePoint Online, dem Sie Daten migrieren können (entweder manuell durch die Verwendung der API Migration oder – wenn Sie migrieren möchten Meine Website mithilfe des Hybrid-Assistenten zu OneDrive for Business - Content).
  
> [!NOTE]
> Denken Sie daran, dass Sie Ihre SharePoint Server 2010-Farm zuerst aktualisiert werden, muss lokal, SharePoint Server 2013 oder SharePoint Server 2016 Hybrid-Option verwendet. SharePoint Foundation 2010 und SharePoint Foundation 2013 kann nicht mit SharePoint Online Hybrid Verbindungen erstellen. 
  
## <a name="related-topics"></a>Verwandte Themen

[Ressourcen zum Durchführen eines Upgrades von Office 2007 oder 2010-Servern und clients](upgrade-from-office-2010-servers-and-products.md)
  
[Übersicht über den Upgradevorgang von SharePoint 2010 auf SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Bewährte Methoden beim Upgrade von SharePoint 2010 auf SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Behandeln von Problemen beim Datenbankupgrade in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Suchen Sie nach Microsoft Partners Upgrade zu unterstützen](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Aktualisierte Produktwartungsrichtlinie für SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Aktualisierte Produktwartungsrichtlinie für SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

