---
title: Während und nach der Daten verschoben
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 3/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Verschiebt Daten werden mit minimaler Beeinträchtigung für Endbenutzer an einen Back-End-Vorgang. Während Microsoft alle Dienste und die zugehörigen Daten für Ihre Mandanten zu einer neuen Datacenter Geo verschiebt ist keine Aktion erforderlich. Die Datenübertragung und Validierung auftreten im Hintergrund im voraus mit minimaler Beeinträchtigung Benutzern.
ms.openlocfilehash: 8813e73dcbce7b6ea24e497929ca6b8e0928e4e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540877"
---
# <a name="during-and-after-your-data-move"></a>Während und nach der Daten verschoben

Verschiebt Daten werden mit minimaler Beeinträchtigung für Endbenutzer an einen Back-End-Vorgang. Während Microsoft alle Dienste und die zugehörigen Daten für Ihre Mandanten zu einer neuen Datacenter Geo verschiebt ist keine Aktion erforderlich. Die Datenübertragung und Validierung auftreten im Hintergrund im voraus mit minimaler Beeinträchtigung Benutzern.
  
> [!NOTE]
> Tritt auf, wechselt zu unterschiedlichen Zeiten für jeden Dienst. Daher sehen Sie den beschriebenen eingeschränkter Funktionalität für jeden Dienst zu einem anderen Zeitpunkt. 
  
Überwachen Sie die Office 365 Message Center zur Bestätigung, wenn Verschiebungen für jede Exchange Online, SharePoint Online und Skype für Unternehmen abgeschlossen sind. Wie in der folgenden Tabelle gezeigt wird, kann es bis zu 24 Monate nach dem Ende des Zeitraums Registrierung dauern, um alle angeforderten Daten abzuschließen verschiebt für alle Kunden in einer bestimmten Geo. Wenn Sie Probleme mit Ihrem Mandanten nach dem Verschieben angezeigt wird, wenden Sie sich an den [Office 365-Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um Hilfe zu erhalten. 
  

|**Kunden mit Adresse im Abrechnung**|**Abgeschlossen, indem Sie alle Verschiebungen**|
|:-----|:-----|
|Australien, Neuseeland, Fidschi  <br/> |31 Oktober 2017  <br/> |
|Japan  <br/> |31 Oktober 2018  <br/> |
|Indien  <br/> |31 Oktober 2018  <br/> |
|Kanada  <br/> |31 Oktober 2018  <br/> |
|Südkorea  <br/> |31 Oktober 2018  <br/> |
|Vereinigtes Königreich  <br/> |15 September 2019  <br/> |
|Frankreich  <br/> |15 September 2020  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>Wechselt, die ein Drittanbieter-Audio Conferencing Provider betreffen

- Drittanbieter-Audio Conferencing Provider Add-On-Dienste für Skype für Unternehmen sind nicht verfügbar für Benutzer in der neuen Geo-spezifischen Rechenzentren verwaltet. 
    
- Bestehende Kunden mit einem Drittanbieter-Audio Conferencing Provider Dienst sollte eine Verschiebung in einem neuen Geo-spezifischen Rechenzentrum nicht anfordern. 
    
- Neue Kunden, die in der neuen Geo-spezifischen Rechenzentren bereitgestellt müssen eine Verschiebung an einem regionalen Rechenzentrum mit einem Drittanbieter-Audio Conferencing Provider anfordern. 
    
## <a name="exchange-online"></a>Exchange Online

Da Zeit zum Wechsel von jedem Benutzer auf die neue Datacenter Geo für einen einzelnen Mandanten benötigt, werden einige Benutzer in der alten Datacenter Geo beim Verschieben, während andere Personen in der neuen Datacenter Geo enthalten sein sollen. Dies bedeutet, dass einige Features, die Zugriff auf mehrere Postfächer betreffen während eines Zeitraums von des Verschiebens nicht vollständig funktionsfähig ist die letzten Wochen können. In den folgenden Abschnitten werden diese Features beschrieben.
  
### <a name="mailbox-move"></a>Verschieben eines Postfachs

Wenn ein einzelnes Postfach Verschiebungen Crosses Datacenter Geos wird der Inhalt von Postfächern so, dass vorhandene Daten in der Ziel-Geo kopiert werden, wirkt sich das Postfach zuerst vorab bereitgestellt. Zum Zeitpunkt der an die Ziel-Geo ü gesperrt ist, das Postfach in der Quelle Geo für ein paar Minuten. Während dieser Zeiten können keine e-Mail-Clients vorübergehend Verbindung herstellen. Weiteren Änderungen in der Ziel-Geo kopiert wurden, und schließt dann das Postfach verschieben nach dem Ziel Geo. Es wird nicht unterbrochen zu e-Mail-Fluss beim Verschieben.
  
Möglicherweise benötigen einige Benutzer Outlook Desktop neu starten, nachdem das Postfach verschoben wird, wie im [Knowledge Base-Artikel 2591913](https://support.microsoft.com/kb/2591913)beschrieben.
  
### <a name="shared-mailbox"></a>Freigegebenes Postfach

Ein Benutzer mit der Berechtigung "Vollzugriff" auf freigegebene Postfächer wirkt sich nicht beim Verschieben aus.
  
### <a name="resource-mailbox"></a>Ressourcenpostfach

Ein Benutzer, der zur Verwaltung von Konfigurationen von Ressource Postfach über die Seite Optionen in Outlook Web Access kann weiterhin dazu beim Verschieben.
  
Wenn die Ressourcenpostfächer direkt über Exchange-Cmdlets verwaltet werden, funktionieren den Cmdlets Set-MailboxRegionalConfiguration und Set-MailboxCalendarConfiguration nicht, wenn der ausführende Benutzer und das Ressourcenpostfach in verschiedenen Geos sind.
  
### <a name="calendar-delegation"></a>Kalenderdelegierung

Frei/Gebucht-Informationen und zum Freigeben von Kalendern sind nicht während des Verschiebens des Mandanten betroffen. Benutzer A mit Schreibberechtigung für den Kalenderordner des Postfachs B kann Kalenderordner Postfach B mithilfe von Outlook Desktop weiterhin verwalten. Jedoch beim Verschieben bearbeiten Wenn Benutzer A und B Postfach in der gleichen Geo nicht Benutzer A nicht Postfach B-Kalender in Outlook Web Access bis sowohl in der Ziel-Geo verschoben werden.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Öffnen Sie "Freigegebener Ordner" in Outlook Web Access

Einige Benutzer öffnen Sie einen freigegebenen e-Mail-Ordner aus einer anderen Postfach (, die der Benutzer hat Lese- oder Schreibberechtigungen für) in Outlook Web Access mit dem Feature "Freigegebene Ordner". In der folgenden Tabelle wird beschrieben, wie Zugriff auf freigegebene Ordner Works während eines Postfachs verschoben. Bitte beachten Sie, dass Benutzer mit Vollzugriff auf ein freigegebenes Postfach mithilfe von Outlook Web Access beim Verschieben des Postfachs öffnen können. 
  
|**Konfiguration**|**Beschreibung**|
|:-----|:-----|
|Benutzer verfügt über die Berechtigung der Postfach-Ordner auf anderes Postfach  <br/> |Potenziell begrenzt.  <br/> Wenn nicht von Benutzer A und B Postfach in der gleichen Geo während des Verschiebens des Mandanten Benutzer A Postfach B-Ordner in Outlook Web Access nicht möglich, wenn Benutzer eine Berechtigung nur in einen bestimmten Ordner im Postfach b verfügt  <br/> Zum Hinzufügen eines freigegebenen Ordners mit der rechten Maustaste in den linken Navigationsbereich der Benutzername, und wählen Sie **freigegebene Ordner hinzufügen**.  <br/> |
|Benutzer mit der Berechtigung an ein anderes Postfach voll Postfach  <br/> |Vollständig unterstützt.  <br/> Wenn Benutzer eine Berechtigung "Vollzugriff" Postfach b hat, kann Benutzer A den freigegebenen Ordner im linken Navigationsbereich in Outlook Web Access zum Öffnen eines Fensters mit Postfach b klicken  <br/> > [!NOTE]> Ein Benutzer kann ein freigegebenes Postfach mit Outlook Web Access während des Verschiebens ohne nachteiligen Auswirkungen öffnen. Die Einschränkung gilt nur für Ordnerebene Freigabe in einem Postfach.           |
   
### <a name="public-folders"></a>Öffentliche Ordner

Wenn das Postfach für Öffentliche Ordner in einer anderen Datacenter Geo aus dem Benutzer darauf zugreifen möchte vorübergehend ist, kann nicht der Benutzer darauf zugreifen. 
  
### <a name="online-archives"></a>Online-Archiven

Während der Verschiebevorgang ausgeführt wird, werden Benutzer verbinden sich über Outlook Web Access nicht mit ihrem Onlinearchiv Postfach herstellen können. Zugriff auf das Archivpostfach für Benutzer mit Outlook verbinden wird unterstützt.
  
### <a name="ediscovery-amp-auditing"></a>eDiscovery &amp; Überwachung

Die eDiscovery- und Überwachungsfunktionen in die Office 365-Sicherheit &amp; Compliance Center Support Cross-Geo Mandanten verschiebt. Im Gegensatz zu den Exchange-Verwaltungskonsole (EAC), das nicht unterstützt wurde Abfragen von Benutzer, die noch einmal der Mandanten verschieben verschoben werden nicht gestartet. Weitere Informationen zur Sicherheit &amp; Compliance Center, finden Sie unter [Sicherheit in Office 365 &amp; Compliance Center](https://go.microsoft.com/fwlink/p/?linkid=841313). 
  
Die folgende Tabelle zeigt, wie eDiscovery und Überwachung über die Exchange-Verwaltungskonsole und die Sicherheit zugreifen &amp; Compliance Center.
  
||**Exchange-Verwaltungskonsole**|**Sicherheit &amp; Compliance Center**|
|:-----|:-----|:-----|
|eDiscovery  <br/> | Wechseln Sie zu https://portal.office.com, und klicken Sie dann auf die Kachel " **Admin** ". </br> Klicken Sie auf **Admin zentriert** \> **Exchange**. </br> Wählen Sie die **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery &amp; halten**. | Wechseln Sie zu https://portal.office.com, und klicken Sie dann auf die Kachel "Admin". </br> Klicken Sie auf **Admin zentriert** \> **Security &amp; Compliance**. </br> Wählen Sie **Search &amp; Untersuchung** \> **eDiscovery**.|
|Überwachung  <br/> | Wechseln Sie zu https://portal.office.com, und klicken Sie dann auf die Kachel " **Admin** ". </br> Klicken Sie auf **Admin zentriert** \> **Exchange**. Wählen Sie die **Verwaltung der Richtlinientreue** \> **Überwachung**. | Wechseln Sie zu https://portal.office.com, und klicken Sie dann auf die Kachel "Admin". </br> Klicken Sie auf **Admin zentriert** \> **Security &amp; Compliance**. </br> Wählen Sie **Search &amp; Untersuchung** \> **Audit Log suchen**. |
   
### <a name="mailbox-migration"></a>Postfachmigration

Ein Mandant zwischen Geos verschoben wird, kann ein migrationsbatch für einige Benutzer im migrationsbatch Fehler gemeldet, die in der Quelle Geo zurückbleiben. In diesem Fall entfernen Sie den vorhandenen migrationsbatch, um die zugrunde liegende Sync-Anforderung zu entfernen. Nachdem der Batch vollständig bereinigt ist, erstellen Sie den Batch erneut, der erstellt werden in der Ziel-Geo-Synchronisierungsanfragen.
  
## <a name="sharepoint-online"></a>SharePoint Online

Wenn SharePoint Online verschoben wird, werden die Daten für die folgenden Dienste auch verschoben:
  
- One Drive for Business
    
- Project Online
    
- Project für Office 365
    
- Office 365-Video-Dienste
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro für Office 365
    
Nachdem wir das Verschieben Ihrer SharePoint Online-Daten abgeschlossen haben, können Sie einige der folgenden Effekte finden Sie unter.
  
### <a name="office-365-video-services"></a>Office 365-Video-Dienste

- Die Daten für video dauert länger als der hingegen für den Rest Ihrer Inhalte in SharePoint Online zu verschieben.
    
- Nach SharePoint Online Inhalt verschoben wurde, ein Zeitrahmen beim soll Videos sind wiedergegeben wird, können nicht.
    
- Wir sind entfernen Trans-codierten kopiert aus dem vorherigen Datacenter und transcodieren sie erneut in das neue Rechenzentrum.
    
### <a name="search"></a>Suche

Im Rahmen Ihrer SharePoint Online-Daten verschieben, werden Ihre Suchindex und für die Suche an einen neuen Speicherort migrieren. Wir weiterhin, bis das Verschieben Ihrer SharePoint Online-Daten **abgeschlossen** ist, aus dem Index am ursprünglichen Speicherort Ihrer Benutzer unterstützen. In den neuen Speicherort startet Suche automatisch das Crawlen von Inhalten, nachdem wir das Verschieben Ihrer SharePoint Online-Daten abgeschlossen haben. Aus diesem zeigen, und wir betreuen aufwärts Ihre Benutzer aus dem migrierten Index. Änderungen an Ihrer Inhalte, die nach der Migration aufgetreten sind nicht in den migrierten Index einbezogen, bis crawlen sie nimmt. Die meisten Kunden beachten nicht Sie, dass die Ergebnisse sind weniger frische rechts aus, nachdem wir die Verschieben ihrer SharePoint Online-Daten abgeschlossen haben, aber einige Kunden können in den ersten 24 bis 48 Stunden reduzierte Aktualität auftreten 
  
Die folgenden Features für die Suche sind betroffen:
  
- Ergebnisse und Such-Webparts zu suchen: Ergebnisse fügen Sie keine Änderungen, die nach der Migration aufgetreten sind, bis das Crawlen sie nimmt. 
    
- Vertiefen: Eingegangen Änderungen, die nach der Migration aufgetreten sind, bis das Crawlen sie nimmt nicht eingeschlossen.
    
- Beliebtheits- und Suchberichte für die Website: Anzahl der Excel-Berichte in den neuen Speicherort enthalten nur migrierten Bestell- und Anzahl von Verwendungsberichten, die ausgeführt wurden, wir nach dem Verschieben Ihrer SharePoint Online-Daten. Eine beliebige Anzahl aus der vorläufigen Zeitraum verloren und können nicht wiederhergestellt werden. In diesem Zeitraum ist in der Regel einige Tage. Einige Kunden können kürzere oder längere Verlusten auftreten.
    
- Video Portal: Ansicht Bestell- und Statistiken für das Portal Video die Statistik für Excel-Berichte, sodass Ansicht zählt und für das Portal Video abhängig sind für den gleichen Zeitraum wie für den Excel-Berichten verloren.
    
- eDiscovery: Elemente, die während der Migration geändert werden nicht angezeigt, bis das Durchforsten die Änderungen übernommen.
    
- Schutz vor Datenverlust (DLP): Richtlinien nicht auf Elemente erzwungen, die bis zum Crawlen aufnimmt die Änderungen zu ändern.
    
## <a name="skype-for-business"></a>Skype for Business

Alle Benutzer werden aus der Skype für Business-Clientsoftware während Abnahme abgemeldet. Benutzer wird die automatische Anmeldung innerhalb von zwei Minuten erneut.
  
|**Features, die während der gesamten Move arbeiten**|**Features, die während eines Teils des Verschiebens beschränkt sein können**|
|:-----|:-----|
| Instant messaging und VoIP-Anrufe  <br/>  Benutzer können Kontakte hinzufügen, Hinzufügen von Kontaktgruppen, Hinzufügen von Besprechungen, legen Sie ihren Standort fest und "Aktuellen Pläne" zu ändern.  <br/>  Einstellungen für Audio Conferencing Provider (ACP) werden in der Ziel-Datacenter-Geo kopiert. Wenn der Anbieter ACP im Rechenzentrum Ziel vorhanden ist, funktionieren. Andernfalls wird der Zugriff verweigert.  <br/> | Mandanten Admin TRPS (Remote-PowerShell Mandanten) werden nicht für Administratoren zum Erstellen von Sitzungen verfügbar.  <br/>  Mandantenadministrator LAC werden nicht für Administratoren bei der Anmeldung und benutzereinstellungen ändern verfügbar.  <br/> |
   
|**Nach der Migration**|
|:-----|
| Besprechungsdaten (hochgeladenen Präsentationen usw.) werden nicht verschoben und müssen erneut hochgeladenen werden.  <br/>  Älterer Lync-Clients, wie die Lync 2010-Client und Lync für Mac 2011-Client sind Cache DNS-Informationen mit dem Dienst verursacht Probleme mit der Anmeldung bekannt. Löschen des DNS-Caches kann erforderlich sein, wenn der Benutzer nicht auf die neueste Skype für Unternehmen Windows-Client befindet. Bitten Sie die Benutzer zum Ausführen von [Assistenten zur Fehlerbehebung](https://support.microsoft.com/en-us/kb/2541980) , und führen die Schritte zum Deaktivieren des Clientcaches. Lync für Mac-Clientbenutzer führen Sie [diese Schritte](https://support.microsoft.com/en-us/kb/2629861)sollten.<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>Daten für andere Dienste, einschließlich Yammer und Power BI

Wir fortfahren nur Kundendaten für Exchange Online, SharePoint Online und Skype für Unternehmen. Wir werden die Daten für andere Dienste nicht verschoben. Es ist keine Änderung oder Einfluss auf die Sie als ein Kunde oder eine andere Dienste. Des Verschiebens nicht beeinflussen, und der Speicherort der ihre Kundendaten bleibt unverändert.
  

