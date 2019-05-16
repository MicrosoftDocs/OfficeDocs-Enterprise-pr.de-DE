---
title: Ende der Unterstützung für SharePoint Server 2007 – Roadmap
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: Am 10. Oktober 2017 wurde die Unterstützung für SharePoint Server 2007 beendet. In diesem Artikel erfahren Sie mehr über ihre Upgrade-Optionen, Problembehandlung, bewährte Methoden, Systemanforderungen, Upgrade-Schritte und wie Sie Unterstützung von Microsoft-Partnern erhalten.
ms.openlocfilehash: 5e5f697f64c520ec1be2b055be0fd42e1742a9ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070721"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Ende der Unterstützung für SharePoint Server 2007 – Roadmap

Am **10. Oktober 2017**Microsoft Office SharePoint Server 2007 am Ende des Supports. Wenn Sie die Migration von SharePoint Server 2007 zu Office 365 oder einer neueren Version von SharePoint Server nicht begonnen haben, ist es jetzt an der Zeit, mit der Planung zu beginnen. In diesem Artikel werden Ressourcen erläutert, mit denen Personendaten zu SharePoint Online migrieren oder Ihr SharePoint-Server lokal aktualisieren können. 
  
## <a name="what-does-end-of-support-mean"></a>Was bedeutet End-of-Support?

SharePoint Server hat, wie fast alle Microsoft-Produkte, einen Supportlebenszyklus, in dem Microsoft neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellt. Dieser Lebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts, und das Ende dieses Lebenszyklus wird als Ende des Supports des Produkts bezeichnet. Am Ende der Unterstützung bietet Microsoft nicht mehr folgende Möglichkeiten:
  
- Technischer Support für Probleme, die auftreten können;
    
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können
    
- Sicherheitsfixes für erkannte Schwachstellen, die den Server anfällig für Sicherheitsverstöße machen können; und 
    
- Zeitzonenaktualisierungen.
    
Obwohl Ihre SharePoint Server 2007-Farm nach dem 10. Oktober 2017 weiterhin betriebsbereit ist, werden keine weiteren Updates, Patches oder Fixes für das Produkt ausgeliefert (einschließlich Sicherheitspatches/Fixes), und der Microsoft-Support hat seine Support-Anstrengungen vollständig verschoben, um neuere Versionen des Produkts. Da Ihre Installation nicht mehr unterstützt oder gepatcht wird, sollten Sie beim Beenden des Supports das Produkt aktualisieren oder wichtige Daten migrieren.
  
> [!TIP]
> Wenn Sie noch nicht für ein Upgrade oder eine Migration geplant haben, finden Sie unter: [SharePoint 2007 Migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. Sie können auch nach [Microsoft-Partnern](https://go.microsoft.com/fwlink/?linkid=841249) suchen, die beim Upgrade oder bei der Office 365-Migration helfen können (oder beides). 
  
Weitere Informationen zu Office 2007-Servern, die das Ende des Supports erreichen, finden Sie unter [Ressourcen zum Upgrade von Office 2007-Servern und-Clients](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Was sind meine Optionen?

Der erste Stopp sollte die [Produktlebenszyklus-Website](https://go.microsoft.com/fwlink/?linkid=843148)sein. Wenn Sie über ein lokales Microsoft-Produkt verfügen, das veraltet ist, sollten Sie überprüfen, ob das Datum für das Ende des Supports so hoch ist, dass Sie ein Jahr lang oder so ausfallen, oder so lange ihre Migrationen erfordern, dass Sie Upgrades oder Migrationen planen können. Bei der Auswahl des nächsten Schritts kann es hilfreich sein, zu überlegen, was gut genug, besser und am besten für Produktfunktionen sein würde. Hier ein Beispiel:
  
|**Gut**|**Besser**|**Optimal**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint-Hybridlösung  <br/> |SharePoint Server 2016  <br/> |
|||SharePoint-Hybridlösung  <br/> |
   
Wenn Sie Optionen am unteren Ende der Skala wählen (gut genug), denken Sie daran, dass Sie mit der Planung des Upgrades sehr bald beginnen müssen, nachdem die Migration von SharePoint Server 2007 abgeschlossen ist. (Ende der Unterstützung für SharePoint Server 2007 ist der 10. Oktober 2017. Beachten Sie, dass diese Datenänderungen vorbehalten sind und die [Produktlebenszyklus-Website](https://support.microsoft.com/en-us/lifecycle)überprüfen.)
  
## <a name="where-can-i-go-next"></a>Wo kann ich als nächstes Vorgehen?

SharePoint Server kann lokal auf Ihren eigenen Servern installiert werden, oder Sie können SharePoint Online verwenden, bei dem es sich um einen Onlinedienst handelt, der Teil von Microsoft Office 365 ist. Sie haben folgende Möglichkeiten:
  
- Migrieren zu SharePoint Online
    
- Aktualisieren von SharePoint Server lokal
    
- Führen Sie beides aus.
    
- Implementieren einer [SharePoint-Hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) Lösung 
    
Beachten Sie versteckte Kosten im Zusammenhang mit der Wartung einer Serverfarm, bei der die Wartung oder Migration von Anpassungen erfolgt, sowie beim Aktualisieren der Hardware, von der SharePoint Server abhängig ist. Die Verwendung einer lokalen SharePoint Server-Farm ist lohnend, wenn Sie notwendig ist; Andernfalls können Sie, wenn Sie Ihre Farm auf älteren SharePoint-Servern ohne starke Anpassung ausführen, von einer geplanten Migration zu SharePoint Online profitieren.
  
> [!IMPORTANT]
> Es gibt eine weitere Option, wenn der Inhalt in SharePoint 2007 nicht häufig verwendet wird. Einige SharePoint-Administratoren wählen möglicherweise [ein Office 365-Abonnement](https://go.microsoft.com/fwlink/?linkid=843152), richten eine brandneue SharePoint Online-Website ein und schneiden dann sauber von SharePoint 2007 ab, wobei nur die wichtigsten Dokumente auf den neuen SharePoint Online-Websites untersucht werden. Von dort aus können Daten aus der SharePoint 2007-Website in Archive abgeleitet werden. Überlegen Sie, wie Benutzer mit Daten Ihre SharePoint 2007-Installation arbeiten. Es gibt möglicherweise kreative Möglichkeiten, dieses Problem zu beheben. 
  
|**SharePoint Online (SPO)**|**SharePoint Server lokal**|
|:-----|:-----|
|Hohe Kosten in der Zeit (Plan/Execution/Verification)  <br/> |Hohe Kosten in der Zeit (Plan/Execution/Verification)  <br/> |
|Geringere Kosten in Fonds (keine hardwarekäufe)  <br/> |Höhere Kosten in Fonds (Hardware + Entwickler/Administratoren)  <br/> |
|Einmalige Kosten bei der Migration  <br/> |Einmalige Kosten pro zukünftiger Migration  <br/> |
|Niedrige Gesamtbetriebskosten/Wartung  <br/> |Hohe Gesamtbetriebskosten/Wartung  <br/> |
   
Bei der Migration zu Office 365 haben die einmaligen Schritte höhere Kosten, während Sie Daten organisieren und entscheiden, was in die Cloud übernommen werden soll und was Sie zurücklassen sollten. Allerdings sind Upgrades ab diesem Zeitpunkt automatisch, Sie müssen nicht mehr Hardware-und Softwareupdates verwalten, und die Betriebszeit der Farm wird durch eine Vereinbarung zum Service Level von Microsoft ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) gesichert.
  
### <a name="migrate-to-sharepoint-online"></a>Migrieren zu SharePoint Online

Stellen Sie sicher, dass SharePoint Online über alle erforderlichen Features verfügt, indem Sie die zugehörige Dienstbeschreibung überprüfen. Hier ist der Link zu allen Office 365-Dienstbeschreibungen:
  
[Beschreibung der Office 365-Dienste](https://go.microsoft.com/fwlink/?linkid=272060)
  
Es gibt keine direkte Möglichkeit, von SharePoint 2007 zu SharePoint Online zu migrieren; Ihr Wechsel zu SharePoint Online erfolgt manuell. Wenn Sie ein Upgrade auf SharePoint Server 2013 oder SharePoint Server 2016 durchführen, müssen Sie möglicherweise auch die SharePoint-Migrations-API verwenden (beispielsweise zur Migration von Informationen zu OneDrive for Business).
  
|**Online pro**|**Online-con**|
|:-----|:-----|
|Microsoft liefert SPO-Hardware und die gesamte Hardwareverwaltung.  <br/> |Die verfügbaren Features können zwischen SharePoint Server lokal und SPO unterschiedlich sein.  <br/> |
|Sie sind der globale Administrator Ihres Abonnements und können den SPO-Websites Administratoren zuweisen.  <br/> |Einige Aktionen, die einem Farm Administrator in SharePoint Server lokal zur Verfügung stehen, sind nicht vorhanden (oder sind nicht erforderlich), die in der SharePoint-Administratorrolle in Office 365 enthalten sind.  <br/> |
|Microsoft wendet Patches, Fixes und Updates auf zugrunde liegende Hardware und Software an.  <br/> |Da es keinen Zugriff auf das zugrunde liegende Dateisystem im Dienst gibt, sind einige Anpassungen begrenzt.  <br/> |
|Microsoft veröffentlicht [Vereinbarungen zum Service Level](https://go.microsoft.com/fwlink/?linkid=843153) und verschiebt schnell, um Vorfälle auf Dienstebene zu beheben.  <br/> |Sicherungs-und Wiederherstellungs-und andere Wiederherstellungsoptionen werden vom Dienst in SharePoint Online automatisiert-Sicherungen werden überschrieben, wenn Sie nicht verwendet werden.  <br/> |
|Sicherheitstests und Server Leistungsoptimierung werden laufend im Dienst von Microsoft ausgeführt.  <br/> |Änderungen an der Benutzeroberfläche und anderen SharePoint-Features werden vom Dienst installiert und müssen möglicherweise ein-oder ausgeschaltet werden.  <br/> |
|Office 365 erfüllt viele Branchenstandards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[](https://go.microsoft.com/fwlink/?linkid=518597) Die Hilfe bei der Migration ist begrenzt.  <br/> Ein Großteil des Upgrades wird manuell oder über die in der [SharePoint Online-und OneDrive-Migrationsinhalts-Roadmap](https://go.microsoft.com/fwlink/?linkid=843184)beschriebene SPO-Migrations-API ausgeführt.  <br/> |
|Weder Microsoft-Support Techniker noch Mitarbeiter im Datencenter verfügen über uneingeschränkten Administratorzugriff auf Ihr Abonnement.  <br/> |Es können zusätzliche Kosten entstehen, wenn die Hardware Infrastruktur aktualisiert werden muss, um die neuere Version von SharePoint zu unterstützen, oder wenn eine sekundäre Farm für das Upgrade erforderlich ist.  <br/> |
|Partner können bei der einmaligen Aufgabe der Migration Ihrer Daten zu SharePoint Online behilflich sein.  <br/> ||
|Online Produkte werden automatisch über den gesamten Dienst aktualisiert, was bedeutet, dass Funktionen möglicherweise nicht mehr unterstützt werden.  <br/> ||
   
Wenn Sie sich für die Erstellung einer neuen Office 365-Website entschieden haben und die Daten nach Bedarf manuell migrieren, können Sie sich Ihre Office 365-Optionen genau hier ansehen:
  
[Optionen zum Office 365-Plan](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Aktualisieren von SharePoint Server lokal

Es gibt historisch keine Möglichkeit, Versionen in SharePoint-Upgrades zu überspringen, zumindest nicht ab der Version von SharePoint Server 2016. Das führt dazu, dass Upgrades seriell gehen:
  
|||
|:-----|:-----|
||SharePoint 2007 | SharePoint Server 2010 | SharePoint Server 2013 | SharePoint Server 2016 |
   
Um den gesamten Pfad von SharePoint 2007 in SharePoint Server 2016 zu übernehmen, bedeutet dies eine erhebliche Zeitinvestition, die Kosten im Hinblick auf aktualisierte Hardware beinhalten wird (Beachten Sie, dass SQL-Server ebenfalls aktualisiert werden müssen), Software und Verwaltung. Anpassungen müssen entsprechend der Wichtigkeit des Features aktualisiert oder aufgegeben werden.
  
> [!NOTE]
> Es ist möglich, Ihre End-of-Life-SharePoint 2007-Farm zu verwalten, eine SharePoint Server 2016-Farm auf neuer Hardware zu installieren (sodass die einzelnen Farmen nebeneinander ausgeführt werden), und dann eine manuelle Migration von Inhalten zu planen und auszuführen (zum herunterladen und erneuten Hochladen von Inhalten, für Beispiel). Beachten Sie einige der Gotchas von manuellen Verschiebungen (beispielsweise Verschiebungen von Dokumenten, die das zuletzt geänderte Konto durch den Alias des Kontos ersetzen, das die manuelle Verschiebung durchführt), und die Arbeit, die vor der Zeit erledigt werden muss (wie das Neuerstellen von Websites, Unterwebsites, Berechtigungen und Listen Strukturen). Auch hier ist es an der Zeit zu überlegen, welche Daten Sie in den Speicher oder nicht mehr benötigen, eine Aktion, die die Auswirkungen der Migration reduzieren kann.
  
In beiden Fällen müssen Sie Ihre Umgebung vor dem Upgrade säubern. Stellen Sie sicher, dass Ihre vorhandene Farm funktionsfähig ist, bevor Sie ein Upgrade durchführen, und (sicher) bevor Sie die Dekommissionierung ausführen. 
  
Denken Sie daran, die **unterstützten und nicht unterstützten Upgrade-Pfade**zu lesen: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Wenn Sie **Anpassungen vorgenommen**haben, ist es wichtig, dass Sie ein Upgrade für jeden Schritt im Migrationspfad planen: 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Lokale pro-Version**|**Lokale con**|
|:-----|:-----|
|Vollzugriff auf alle Aspekte Ihrer SharePoint-Farm, von der Server Hardware bis.  <br/> |Alle Breaks und Fixes sind in der Verantwortung Ihres Unternehmens (kann bezahlten Microsoft-Support engagieren, wenn Ihr Produkt nicht am Ende des Supports ist):  <br/> |
|Vollständiger Featuresatz von SharePoint Server lokal mit der Option, Ihre lokale Farm mit einem SharePoint Online-Abonnement über Hybrid zu verbinden.  <br/> |Upgrades, Patches, Sicherheitsfixes und die gesamte Wartung von SharePoint Server, die lokal verwaltet werden.  <br/> |
|Vollzugriff für eine bessere Anpassung.  <br/> |[Von Office 365 unterstützte Compliance-Standards](https://go.microsoft.com/fwlink/?linkid=843165) müssen lokal manuell konfiguriert werden.  <br/> |
|Sicherheitstests und Server Leistungsoptimierungen, die in ihrer Niederlassung durchgeführt werden (unter ihrer Kontrolle).  <br/> |Office 365 kann Features für SharePoint Online zur Verfügung stellen, die nicht mit SharePoint Server lokal kooperieren  <br/> |
|Partner können bei der Migration von Daten zur nächsten Version von SharePoint Server (und darüber hinaus) behilflich sein.  <br/> |Ihre SharePoint Server-Websites verwenden nicht automatisch [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) -Zertifikate, wie in SharePoint Online zu sehen.  <br/> |
|Vollständige Kontrolle über Benennungskonventionen, Sicherung und Wiederherstellung und andere Wiederherstellungsoptionen in SharePoint Server lokal.  <br/> |SharePoint Server lokal reagiert auf Produktlebenszyklen.  <br/> |
   
### <a name="upgrade-resources"></a>Ressourcen aktualisieren

Beginnen Sie mit dem wissen, dass Sie die Hardware-und Softwareanforderungen erfüllen, und folgen Sie den unterstützten Aktualisierungsmethoden.
  
- **Hardware-und Softwareanforderungen für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843204) | SharePoint Server 2010 SharePoint Server[2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Software Beschränkungen und-Grenzen für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843245) | SharePoint Server 2007 SharePoint Server[2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Übersicht über den Upgradeprozess für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843250) | SharePoint Server 2007 SharePoint Server[2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Erstellen einer SharePoint-Hybridlösung zwischen SharePoint Online und lokal

Wenn die Antwort auf Ihre Migrationsanforderungen irgendwo zwischen der Self-Control von lokalen angeboten und den niedrigeren Kosten des Besitzes von SharePoint Online angeboten wird, können Sie SharePoint Server 2013 oder 2016 Farmen mit SharePoint Online über Hybriden verbinden. [Informationen zu SharePoint-Hybridlösungen](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Wenn Sie sich für eine hybride SharePoint Server-Farm entscheiden, sollten Sie sich mit den vorhandenen Hybrid Typen vertraut machen und die Verbindung zwischen Ihrer lokalen SharePoint-Farm und Ihrem Office 365-Abonnement konfigurieren.
  
Eine gute Möglichkeit, um zu sehen, wie das funktioniert, ist das Erstellen einer [Office 365-Entwicklungs-/Testumgebung](https://go.microsoft.com/fwlink/?linkid=843152). Sobald Sie eine Testversion oder ein erworbenes Office 365-Abonnement haben, sind Sie auf dem Weg, die Websitesammlungen, Webs und Dokumentbibliotheken in SharePoint Online zu erstellen, auf die Sie Daten migrieren können (entweder manuell, durch Verwendung der Migrations-API oder – wenn Sie mein Websiteinhalte für OneDrive für Unternehmen – über den Hybrid-Assistenten).
  
> [!NOTE]
> Denken Sie daran, dass Ihre SharePoint 2007-Farm in SharePoint Server 2013 oder SharePoint Server 2016 aktualisiert werden muss, um die Hybrid Option zu verwenden. 
  
## <a name="related-topics"></a>Verwandte Themen

[Problembehandlung und Fortsetzen des Upgrades (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Beheben von Problemen mit dem Upgrade (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Behandeln von Problemen beim Datenbankupgrade in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Suchen nach Microsoft-Partnern für das Upgrade](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressourcen für das Upgrade von Office 2007-Servern und-Clients](upgrade-from-office-2007-servers-and-products.md)
  

