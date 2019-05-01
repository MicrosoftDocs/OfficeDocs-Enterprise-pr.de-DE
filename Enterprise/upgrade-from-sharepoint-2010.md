---
title: Aktualisieren von SharePoint 2010
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
description: SharePoint 2010 und SharePoint Server 2010 stehen kurz vor dem Ende der Unterstützung. Verwenden Sie diesen Artikel als Leitfaden für das Upgrade auf SharePoint Online oder eine neuere Version von SharePoint Server lokal.
ms.openlocfilehash: c88c6010aa398d8076fce59976bf6f5c0aa1a743
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492042"
---
# <a name="upgrading-from-sharepoint-2010"></a>Aktualisieren von SharePoint 2010

Am 13. Oktober 2020 erreicht Microsoft Office SharePoint Server 2010 das Ende des Supports. In diesem Artikel werden Ressourcen zur Unterstützung der Migration Ihrer vorhandenen SharePoint Server 2010-Daten zu SharePoint Online oder zum Upgraden Ihrer lokalen SharePoint-Server erläutert.
  
## <a name="what-is-end-of-support"></a>Was ist End of Support?

Wenn Ihre SharePoint Server 2010-und SharePoint Foundation 2010-Software das Ende des Supportlebenszyklus erreicht hat (die Zeit, in der Microsoft neue Features, Bugfixes, Sicherheitsfixes usw. bereitstellt), wird dies als "End of Support" der Software bezeichnet, oder Manchmal wird der "Ruhestand". Nach dem Ende der Unterstützung (oder EOS) eines Produkts wird nichts tatsächlich heruntergefahren oder funktioniert nicht mehr; am Ende der Softwareunterstützung bietet Microsoft jedoch nicht mehr Folgendes:
  
- Technischer Support für Probleme, die auftreten können;
    
- Fehlerbehebungen für erkannte Probleme, die die Stabilität und Benutzerfreundlichkeit des Servers beeinträchtigen können
    
- Sicherheitsfixes für erkannte Schwachstellen, die den Server anfällig für Sicherheitsverstöße machen können;
    
- Zeitzonenaktualisierungen.
    
Das führt dazu, dass keine weiteren Updates, Patches oder Fixes für das Produkt ausgeliefert werden (einschließlich Sicherheitspatches/Fixes), und der Microsoft-Support hat seine Support Bemühungen auf neuere Versionen vollständig verschoben. Als Ende der Unterstützung von SharePoint Server 2010-Lösungen sollten Sie Möglichkeiten nutzen, um Daten zu trimmen, die Sie vor dem Upgrade des Produkts nicht mehr benötigen, und/oder Ihre wichtigen Daten zu migrieren.
  
> [!NOTE]
> Ein Softwarelebenszyklus dauert in der Regel 10 Jahre ab dem Datum der ersten Version des Produkts. Sie können nach [Microsoft-Partnern](https://go.microsoft.com/fwlink/?linkid=841249) suchen, die beim Upgrade auf die nächste Version Ihrer Software oder mit Office 365 Migration helfen können (oder beides). Vergewissern Sie sich, dass Sie unter Stützungs Termine für wichtige zugrunde liegende Technologien sowie insbesondere für die Version von SQL Server, die Sie mit SharePoint verwenden, bekannt sind. 
  
## <a name="what-are-my-options"></a>Was sind meine Optionen?

Überprüfen Sie zuerst das Datum, an dem die Unterstützung auf der [Produktlebenszyklus-Website](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202010)endet. Als nächstes müssen Sie Ihre Upgrade-oder Migrationszeit mit Wissen über dieses Datum planen. Denken Sie daran, dass Ihr Produkt am angegebenen Datum *nicht mehr funktioniert* , und Sie weiterhin verwenden können, aber da Ihre Installation nach diesem Datum nicht mehr gepatcht wird, benötigen Sie eine Strategie, die Ihnen einen reibungsloseren Übergang zur nächsten Version erleichtert. des Produkts. 
  
Diese Matrix hilft beim Plotten eines Kurses bei der Migration von Produktfeatures und Benutzerdaten:
  
|**Produkt Ende des Supports**|**Gut**|**Optimal**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint-Hybridlösung  <br/> |SharePoint Server 2016 (lokal)  <br/> |
|||SharePoint-Cloud-Hybrid Suche  <br/> |
   
Wenn Sie Optionen am unteren Ende der Skalierung (gute Optionen) auswählen, müssen Sie nach Abschluss der Migration von SharePoint Server 2010 mit der Planung eines weiteren Upgrades beginnen. (Ende der Unterstützung für SharePoint Server 2010 und SharePoint Foundation 2010 sind für Okt 13, 2020 geplant, aber *Bitte* beachten Sie, dass Sie die [Produktlebenszyklus-Website](https://support.microsoft.com/en-us/lifecycle) immer auf Ihre genauesten Daten prüfen sollten!) 
  
## <a name="where-should-i-go-next"></a>Wo sollte ich als nächstes Vorgehen?

SharePoint Server 2013 und SharePoint Foundation 2013 können lokal auf Ihren eigenen Servern installiert werden. Andernfalls können Sie SharePoint Online verwenden, bei dem es sich um einen Onlinedienst handelt, der Teil von Microsoft Office 365 ist. Sie haben folgende Möglichkeiten:
  
- Migration zu SharePoint Online
    
- Aktualisieren von SharePoint Server oder SharePoint Foundation lokal
    
- Führen Sie beides aus.
    
- Implementieren einer [SharePoint-Hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) Lösung 
    
Beachten Sie versteckte Kosten im Zusammenhang mit der Wartung einer Serverfarm, bei der die Wartung oder Migration von Anpassungen erfolgt, sowie beim Aktualisieren der Hardware, von der SharePoint Server abhängig ist. Wenn Sie dies wissen und alle diese Konten berücksichtigt haben, ist es einfacher, das lokale Upgrade fortzusetzen. Andernfalls können Sie, wenn Sie Ihre Farm auf SharePoint-Legacy Servern ohne starke Anpassung ausführen, von einer geplanten Migration zu SharePoint Online profitieren. Es ist auch möglich, dass lokale SharePoint Server-Shops einige Daten in SharePoint Online platzieren, um die Menge der Hardwareverwaltung zu reduzieren, in der alle Ihre lokalen Daten einbezogen werden. Es kann günstiger sein, einige Ihrer Daten in SharePoint Online zu verschieben.
  
> [!NOTE]
> SharePoint-Administratoren können [ein Office 365-Abonnement erstellen](https://go.microsoft.com/fwlink/?linkid=843152), eine brandneue SharePoint Online-Website einrichten und dann von SharePoint Server 2010 sauber Ausschneiden, indem Sie nur die wichtigsten Dokumente auf die neuen SharePoint Online-Websites übernehmen. Von dort aus können alle verbleibenden Daten aus der SharePoint Server 2010-Website in lokale Archive geleert werden. 
  
|**SharePoint Online (SPO)**|**SharePoint Server lokal**|
|:-----|:-----|
|Hohe Kosten in der Zeit (Plan/Execution/Verification)  <br/> |Hohe Kosten in der Zeit (Plan/Execution/Verification)  <br/> |
|Geringere Kosten in Fonds (keine hardwarekäufe)  <br/> |Höhere Kosten in Fonds (hardwarekäufe)  <br/> |
|Einmalige Kosten bei der Migration  <br/> |Einmalige Kosten pro zukünftiger Migration  <br/> |
|Niedrige Gesamtbetriebskosten/Wartung  <br/> |Hohe Gesamtbetriebskosten/Wartung  <br/> |
   
Bei der Migration zu Office 365 hat die einmalige Bewegung höhere Kosten bei der Planung, im Vorfeld (während Sie Daten organisieren und entscheiden, was in der Cloud zu übernehmen ist und was Sie zurücklassen sollten). Nachdem die Daten migriert wurden, werden die Upgrades ab diesem Zeitpunkt automatisch vorgenommen, da Sie nicht mehr Hardware-und Softwareupdates verwalten müssen, und die Betriebszeit Ihrer Farm wird durch eine Vereinbarung zum Service Level von Microsoft unterstützt.[](https://go.microsoft.com/fwlink/?linkid=843153)
  
### <a name="migrate-to-sharepoint-online"></a>Migration zu SharePoint Online

Stellen Sie sicher, dass SharePoint Online alle erforderlichen Funktionen bietet, indem Sie die zugehörige Dienstbeschreibung überprüfen. Hier ist der Link zu allen Office 365-Dienstbeschreibungen:
  
[Beschreibung der Office 365-Dienste](https://go.microsoft.com/fwlink/?linkid=272060)
  
Derzeit ist es nicht möglich, eine direkte Migration von SharePoint Server 2010 (oder SharePoint Foundation 2010) zu SharePoint Online durchgeführt zu haben, sodass ein großer Teil der Arbeit manuell erfolgt. Dadurch haben Sie die Möglichkeit, Daten und Websites, die nicht mehr benötigt werden, zu archivieren und zu löschen, bevor Sie mit der Migration fortfahren. Sie können andere Daten in den Speicher archivieren. Denken Sie auch daran, dass weder SharePoint Server 2010 noch SharePoint Foundation 2010 am Ende des Supports funktioniert, sodass Administratoren einen Zeitraum haben können, in dem SharePoint noch ausgeführt wird, wenn Ihre Kunden vergessen, einige Ihrer Daten zu verschieben.
  
Wenn Sie ein Upgrade auf SharePoint Server 2013 oder SharePoint Server 2016 durchführen und sich entscheiden, Daten in SharePoint Online einzufügen, kann es auch sein, dass Sie die [SharePoint-Migrations-API](https://support.office.com/en-us/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) verwenden (um Informationen zu OneDrive for Business zu migrieren). 
  
|**Online pro**|**Online-con**|
|:-----|:-----|
|Microsoft liefert SPO-Hardware und die gesamte Hardwareverwaltung.  <br/> |Die verfügbaren Features können zwischen SharePoint Server lokal und SPO unterschiedlich sein.  <br/> |
|Sie sind der globale Administrator Ihres Abonnements und können den SPO-Websites Administratoren zuweisen.  <br/> |Einige Aktionen, die einem Farm Administrator in SharePoint Server lokal zur Verfügung stehen, sind in der SharePoint-Administratorrolle in Office 365 nicht vorhanden (oder sind nicht erforderlich), aber die SharePoint-Verwaltung, die WebsitesammlungsVerwaltung und der Website Besitz sind lokal Ihre org.  <br/> |
|Microsoft wendet Patches, Fixes und Updates auf zugrunde liegende Hardware und Software an (einschließlich SQL-Servern, auf denen SharePoint Online ausgeführt wird).  <br/> |Da es keinen Zugriff auf das zugrunde liegende Dateisystem im Dienst gibt, sind einige Anpassungen begrenzt.  <br/> |
|Microsoft veröffentlicht [Vereinbarungen zum Service Level](https://go.microsoft.com/fwlink/?linkid=843153) und verschiebt schnell, um Vorfälle auf Dienstebene zu beheben.  <br/> |Sicherungs-und Wiederherstellungs-und andere Wiederherstellungsoptionen werden vom Dienst in SharePoint Online automatisiert-Sicherungen werden überschrieben, wenn Sie nicht verwendet werden.  <br/> |
|Sicherheitstests und Server Leistungsoptimierung werden laufend im Dienst von Microsoft ausgeführt.  <br/> |Änderungen an der Benutzeroberfläche und anderen SharePoint-Features werden vom Dienst installiert und müssen möglicherweise ein-oder ausgeschaltet werden.  <br/> |
|Office 365 erfüllt viele Branchenstandards: [office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |[](https://go.microsoft.com/fwlink/?linkid=518597) Die Hilfe bei der Migration ist begrenzt.  <br/> Ein Großteil des Upgrades wird manuell oder über die in der [SharePoint Online-und OneDrive-Migrationsinhalts-Roadmap](https://go.microsoft.com/fwlink/?linkid=843184)beschriebene SPO-Migrations-API ausgeführt.  <br/> |
|Weder Microsoft-Support Techniker noch Mitarbeiter im Datencenter verfügen über uneingeschränkten Administratorzugriff auf Ihr Abonnement.  <br/> |Es können zusätzliche Kosten entstehen, wenn die Hardware Infrastruktur aktualisiert werden muss, um die neuere Version von SharePoint zu unterstützen, oder wenn eine sekundäre Farm für das Upgrade erforderlich ist.  <br/> |
|Partner können bei der einmaligen Aufgabe der Migration Ihrer Daten zu SharePoint Online behilflich sein.  <br/> |Nicht alle Änderungen an SharePoint Online liegen innerhalb Ihres Steuerelements. Nach der Migration können sich Entwurfs Unterschiede zwischen Menüs, Bibliotheken und anderen Features vorübergehend auf die Benutzerfreundlichkeit auswirken.  <br/> |
|Online Produkte werden automatisch im gesamten Dienst aktualisiert, was bedeutet, dass Funktionen möglicherweise veraltet sind, es gibt jedoch keinen tatsächlichen Supportlebenszyklus.  <br/> |Es gibt ein Ende des Supportlebenszyklus für SharePoint Server (oder SharePoint Foundation) und zugrunde liegende SQL-Server.  <br/> |
   
Wenn Sie sich für die Erstellung einer neuen Office 365-Website entschieden haben und die Daten nach Bedarf manuell migrieren, können Sie sich Ihre Office 365-Optionen genau hier ansehen:
  
[Optionen zum Office 365-Plan](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Aktualisieren von SharePoint Server lokal

Ab der aktuellen Version des lokalen SharePoint-Produkts (SharePoint Server 2016) müssen SharePoint Server-Upgrades *seriell* ausgeführt werden, d. h., es gibt keine Möglichkeit, das Upgrade von SharePoint Server 2010 auf SharePoint Server 2016 direkt durchführen. 
  
|||
|:-----|:-----|
||Serielles Upgrade-Pfad * * * *: Share **\>** point Server 2010 **\>** SharePoint Server 2013 SharePoint Server 2016 |
   
Wenn Sie den gesamten Pfad von SharePoint 2010 zu SharePoint Server 2016 befolgen, wird dies Zeit und Planung dauern. Upgrades erfordern Kosten im Hinblick auf aktualisierte Hardware (Beachten Sie, dass auch SQL-Server aktualisiert werden müssen), Software und Verwaltung. Außerdem müssen Anpassungen möglicherweise aktualisiert oder sogar abgebrochen werden. Stellen Sie sicher, dass Sie vor dem Upgrade Ihrer SharePoint Server-Farm Notizen zu allen wichtigen Anpassungen sammeln.
  
> [!NOTE]
> Es ist möglich, Ihre End-of-Support-SharePoint 2010-Farm zu warten, eine SharePoint Server 2016-Farm auf neuer Hardware zu installieren (daher werden die separaten Farmen nebeneinander ausgeführt), und dann eine manuelle Migration von Inhalten (zum herunterladen und erneuten Hochladen von Inhalten für Beispiel). Es gibt potenzielle Fallstricke für diese manuellen Verschiebungen (beispielsweise Dokumente, die von 2010, die ein Aktuelles, zuletzt geändertes Konto mit dem Alias des Kontos ausführen, das manuell verschoben wird), und einige arbeiten müssen im Vorfeld durchgeführt werden (Neuerstellen von Websites, Unterwebsites, Berechtigungen und Strukturen auflisten). Es empfiehlt sich, zu überlegen, welche Daten Sie in den Speicher verschieben oder nicht mehr benötigen. Dies kann die Auswirkungen der Migration verringern. In beiden Fällen müssen Sie Ihre Umgebung vor dem Upgrade säubern. Stellen Sie sicher, dass Ihre vorhandene Farm funktionsfähig ist, bevor Sie ein Upgrade durchFühren, und (sicher) bevor Sie die Dekommissionierung ausführen. 
  
Denken Sie daran, die **unterstützten und nicht unterstützten Upgrade-Pfade**zu lesen: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Wenn Sie **Anpassungen vorgenommen**haben, ist es wichtig, dass Sie ein Upgrade für jeden Schritt im Migrationspfad planen: 
  
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Lokale pro-Version**|**Lokale con**|
|:-----|:-----|
|Vollzugriff auf alle Aspekte Ihrer SharePoint-Farm (und es ist SQL), von der Server Hardware bis.  <br/> |Alle Breaks und Fixes sind in der Verantwortung Ihres Unternehmens (Sie können jedoch einen bezahlten Microsoft-Support einbinden, wenn Ihr Produkt nicht am Ende des Supports ist):  <br/> |
|Vollständiger Featuresatz von SharePoint Server lokal mit der Option, Ihre lokale Farm mit einem SharePoint Online-Abonnement über Hybrid zu verbinden.  <br/> |Upgrades, Patches, Sicherheitsfixes, Hardwareupgrades und die gesamte Wartung von SharePoint Server und die SQL-Farm werden lokal verwaltet.  <br/> |
|Vollzugriff für größere Anpassungsoptionen als bei SharePoint Online.  <br/> |[Von Office 365 unterstützte Compliance-Standards](https://go.microsoft.com/fwlink/?linkid=843165) müssen lokal manuell konfiguriert werden.  <br/> |
|Sicherheitstests und Server Leistungsoptimierungen, die in ihrer Niederlassung ausgeführt werden (unter ihrer Kontrolle).  <br/> |Office 365 kann Features für SharePoint Online zur Verfügung stellen, die nicht mit SharePoint Server lokal kooperieren  <br/> |
|Partner können bei der Migration von Daten zur nächsten Version von SharePoint Server (und darüber hinaus) behilflich sein.  <br/> |Ihre SharePoint Server-Websites verwenden nicht automatisch [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) -Zertifikate, wie in SharePoint Online zu sehen.  <br/> |
|Vollständige Kontrolle über Benennungskonventionen, Sicherung und Wiederherstellung und andere Wiederherstellungsoptionen in SharePoint Server lokal.  <br/> |SharePoint Server lokal reagiert auf Produktlebenszyklen.  <br/> |
   
### <a name="upgrade-resources"></a>Ressourcen aktualisieren

Vergleichen Sie zunächst die Hardware-und Softwareanforderungen. Wenn Sie die grundlegendenAnforderungen für das Upgrade auf aktueller Hardware nicht erfüllen, bedeutet dies, dass Sie zuerst die Hardware in der Farm oder den SQL-Server aktualisieren müssen, oder dass Sie sich entscheiden, einen Teil der Websites auf die "Evergreen"-Hardware von SharePoint Online zu verschieben. Nachdem Sie Ihre Bewertung vorgenommen haben, befolgen Sie die unterstützten Upgrade-Pfade und-Methoden.
  
- **Hardware-und Softwareanforderungen für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843204) | sharepoint server 2010 sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843206) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Software Beschränkungen und-Grenzen für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843247) | sharepoint server 2010 sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843248) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Übersicht über den Upgradeprozess für**: 
    
    [](https://go.microsoft.com/fwlink/?linkid=843251) | sharepoint server 2010 sharepoint server[2013](https://go.microsoft.com/fwlink/?linkid=843252) | [sharepoint server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-sharepoint-server-on-premises"></a>Erstellen einer SharePoint-Hybridlösung zwischen SharePoint Online und SharePoint Server lokal

Eine weitere Option (die möglicherweise die beste der beiden lokalen und Online-Welten für einige Migrationsanforderungen ist) ist eine hybride, Sie können SharePoint Server 2013 oder 2016-Farmen mit SharePoint Online verbinden, um eine SharePoint-hybride zu erstellen: Informationen [zu SharePoint-Hybridlösungen ](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Wenn Sie sich für eine hybride SharePoint Server-Farm entscheiden, achten Sie darauf, die Websites und Benutzer zu planen, die Sie Online verschieben sollten und die lokal bleiben müssen. Eine Überprüfung und Rangfolge der Inhalte Ihrer SharePoint Server-Farm (ermitteln, welche Daten hohe, mittlere oder geringe Auswirkungen auf Ihr Unternehmen haben) können bei dieser Entscheidung hilfreich sein. Möglicherweise ist das einzige, was Sie mit SharePoint Online freigeben müssen, (a) Benutzerkonten für die Anmeldung und (b) der SharePoint Server-Suchindex – Dies ist möglicherweise erst dann klar, wenn Sie sich ansehen, wie Ihre Websites verwendet werden. Wenn sich Ihr Unternehmen später entscheidet, alle Inhalte zu SharePoint Online zu migrieren, können Sie alle verbleibenden Konten und Daten Online verschieben und Ihre lokale Farm außer Betrieb setzen, und die Verwaltung/Verwaltung der SharePoint-Farm erfolgt über Office 365 Konsolen von diesem Punkt an.
  
Stellen Sie sicher, dass Sie sich mit den vorhandenen Hybrid Typen vertraut machen und die Verbindung zwischen Ihrer lokalen SharePoint-Farm und Ihrem Office 365-Abonnement konfigurieren.
  
Eine gute Möglichkeit, um zu sehen, wie eine hybride SharePoint-Farm funktioniert, ist das Erstellen einer [Office 365 dev/Test-Umgebung](https://go.microsoft.com/fwlink/?linkid=843152). Sobald Sie eine Testversion oder ein erworbenes Office 365-Abonnement haben, sind Sie auf dem Weg, die Websitesammlungen, Webs und Dokumentbibliotheken in SharePoint Online zu erstellen, auf die Sie Daten migrieren können (entweder manuell, durch Verwendung der Migrations-API oder – wenn Sie mein Websiteinhalte für OneDrive für Unternehmen – über den Hybrid-Assistenten).
  
> [!NOTE]
> Denken Sie daran, dass Ihre SharePoint Server 2010-Farm zunächst auf SharePoint Server 2013 oder SharePoint Server 2016 aktualisiert werden muss, um die Hybrid Option zu verwenden. SharePoint Foundation 2010 und SharePoint Foundation 2013 können keine Hybrid Verbindungen mit SharePoint Online erstellen. 
  
## <a name="related-topics"></a>Verwandte Themen

[Ressourcen für ein Upgrade von Office 2007-oder 2010-Servern und-Clients](upgrade-from-office-2010-servers-and-products.md)
  
[Overview of the upgrade process from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493301%28v=office.16%29.aspx)
  
[Bewährte Methoden beim Upgrade von SharePoint 2010 auf SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493305%28v=office.16%29.aspx)
  
[Behandeln von Problemen beim Datenbankupgrade in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Suchen nach Microsoft-Partnern für das Upgrade](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Aktualisierte Produktwartungsrichtlinie für SharePoint 2013](https://technet.microsoft.com/en-us/library/mt493253%28v=office.16%29.aspx)
  
[Aktualisierte Produktwartungsrichtlinie für SharePoint Server 2016](https://technet.microsoft.com/en-us/library/mt782882%28v=office.16%29.aspx)
  

