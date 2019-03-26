---
title: Während und nach der Datenverschiebung
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Datenverschiebungen sind ein Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer. Es ist keine Aktion erforderlich, während Microsoft jeden Dienst und zugehörige Daten für Ihren Mandanten in ein neues Datacenter Geo verschiebt. Die Datenübertragung und-Validierung erfolgt im Hintergrund im Vorfeld mit minimalen Auswirkungen für die Benutzer.
ms.openlocfilehash: 7635de71e207ff01b24b8b8df8664e3f57f395cf
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30647993"
---
# <a name="during-and-after-your-data-move"></a>Während und nach der Datenverschiebung

Datenverschiebungen sind ein Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer. Es ist keine Aktion erforderlich, während Microsoft jeden Dienst und zugehörige Daten für Ihren Mandanten in ein neues Datacenter Geo verschiebt. Die Datenübertragung und-Validierung erfolgt im Hintergrund im Vorfeld mit minimalen Auswirkungen für die Benutzer.
  
> [!NOTE]
> Verschiebungen erfolgen zu unterschiedlichen Zeiten für jeden Dienst. Daher werden die beschriebenen reduzierten Funktionen für jeden Dienst zu einem anderen Zeitpunkt angezeigt. 
  
Sehen Sie sich das Office 365-Nachrichten Center an, um eine Bestätigung zu erhalten, wenn für jeden von Exchange Online, SharePoint Online und Skype for Business Moves ausgeführt werden. Wie in der folgenden Tabelle dargestellt, kann es bis zu 24 Monate dauern, bis nach Ablauf des Registrierungszeitraums alle erforderlichen Datenverschiebungen für alle Kunden in einem bestimmten Geo ausgeführt werden. Wenn Sie nach der Verschiebung Probleme mit Ihrem Mandanten feststellen, wenden Sie sich an den [Office 365-Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um Hilfe zu erhalten. 
  

|**Kunden mit Rechnungsadresse in**|**Alle durchgeführten Verschiebungen**|
|:-----|:-----|
|Australien, Neuseeland, Fidschi  <br/> |31. Oktober 2017  <br/> |
|Japan  <br/> |31. Oktober 2018  <br/> |
|Indien  <br/> |31. Oktober 2018  <br/> |
|Kanada  <br/> |30. Juni 2019  <br/> |
|Südkorea  <br/> |31. Oktober 2018  <br/> |
|United Kingdom  <br/> |15. September 2019  <br/> |
|Frankreich  <br/> |15. September 2020  <br/> |
|Vereinigte Arabische Emirate  <br/> |Angekündigt  <br/> |
|Südafrika  <br/> |Angekündigt  <br/> |
   
## <a name="exchange-online"></a>Exchange Online

Da es Zeit benötigt, um jeden Benutzer für einen einzelnen Mandanten in das neue Datacenter Geo zu verschieben, befinden sich einige Benutzer während der Verschiebung noch im alten Rechenzentrum Geo, während andere sich im neuen Datencenter Geo befinden. Dies bedeutet, dass einige Features, die den Zugriff auf mehrere Postfächer betreffen, möglicherweise während eines Zeitraums des Verschiebungsvorgangs, der sich in den letzten Wochen befindet, nicht vollständig funktionieren. Diese Features werden in den folgenden Abschnitten beschrieben.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Öffnen des "freigegebenen Ordners" in Outlook Web Access

Einige Benutzer öffnen einen freigegebenen e-Mail-Ordner aus einem anderen Postfach (für den der Benutzer Lese-oder Schreibberechtigungen hat) in Outlook Web Access unter Verwendung der Funktion "FreigeGebener Ordner". In der folgenden Tabelle wird beschrieben, wie der Zugriff auf freigegebene Ordner während einer Postfachverschiebung funktioniert. Beachten Sie, dass Benutzer mit vollständigen Berechtigungen für ein freigegebenes Postfach das Postfach während der Verschiebung mithilfe von Outlook Web Access öffnen können. 
  
|**Konfiguration**|**Beschreibung**|
|:-----|:-----|
|Benutzer verfügt über die Berechtigung für den Postfachordner für ein anderes Postfach  <br/> |MöglicherWeise begrenzt.  <br/> Wenn sich Benutzer A und Postfach B während der Mandanten Verschiebung nicht in der gleichen geografischen Umgebung befinden, kann Benutzer a den Ordner von Postfach B in Outlook Web Access nicht öffnen, wenn Benutzer A nur über die Berechtigung für einen bestimmten Ordner in Postfach B verfügt.  <br/> Klicken Sie im linken Navigationsbereich mit der rechten Maustaste auf den Benutzernamen, und wählen Sie **freigegebener Ordner hinzufügen**aus, um einen freigegebenen Ordner hinzuzufügen.  <br/> |
|Benutzer mit vollständiger Post Fach Berechtigung für ein anderes Postfach  <br/> |Vollständig unterstützt.  <br/> Wenn Benutzer A über die Berechtigung "Vollzugriff" für Postfach B verfügt, kann Benutzer A auf den freigegebenen Ordner im linken Navigationsbereich in Outlook Web Access klicken, um ein Fenster mit dem Postfach B zu öffnen.  Ein Benutzer kann während der Verschiebung ein freigegebenes Postfach mit Outlook Web Access ohne nachteilige Auswirkungen öffnen. Die Einschränkung gilt nur für die Freigabe auf Ordnerebene in einem Postfach.           |
   
### <a name="public-folders"></a>Öffentliche Ordner

Wenn sich das Postfach für Öffentliche Ordner vorübergehend in einem anderen Datencenter Geo des Benutzers befindet, der versucht, darauf zuzugreifen, kann der Benutzer möglicherweise nicht auf das Postfach für Öffentliche Ordner zugreifen. 
  
### <a name="online-archives"></a>Online Archive

Während die Verschiebung ausgeführt wird, können Benutzer, die über Outlook für Mac eine Verbindung herstellen, möglicherweise keine Verbindung mit Ihrem Onlinearchivpostfach herstellen. Der Zugriff auf das Archivpostfach für Benutzer, die mit Outlook und Outlook Web Access eine Verbindung herstellen, wird unterstützt.
  
## <a name="sharepoint-online"></a>SharePoint Online

Wenn SharePoint Online verschoben wird, werden auch die Daten für die folgenden Dienste verschoben:
  
- One Drive for Business
    
- Project Online
    
- Project für Office 365
    
- Office 365-Video Dienste
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro für Office 365
    
Nachdem Sie Ihre SharePoint Online-Daten übertragen haben, werden möglicherweise die folgenden Effekte angezeigt.
  
### <a name="office-365-video-services"></a>Office 365-Video Dienste

- Die Datenverschiebung für Video dauert länger als die Verschiebungen für die restlichen Inhalte in SharePoint Online.
    
- Nachdem der SharePoint Online-Inhalt verschoben wurde, gibt es einen Zeitraum, in dem Videos nicht wiedergegeben werden können.
    
- Wir entfernen die transcodierten Kopien aus dem vorherigen Datencenter und codieren Sie erneut im neuen Datencenter.
    
### <a name="search"></a>Suche

Wenn Sie Ihre SharePoint Online-Daten verschieben, migrieren wir den Such Index und die Sucheinstellungen an einen neuen Speicherort. Bis zum Abschluss der Verschiebung Ihrer SharePoint Online-Daten werden Ihre Benutzer weiterhin am ursprünglichen Speicherort aus dem Index bereit **gestellt** . Am neuen Speicherort beginnt die Suche nach der Verschiebung Ihrer SharePoint Online-Daten automatisch mit dem Crawlen Ihrer Inhalte. Ab diesem Zeitpunkt werden Ihre Benutzer aus dem migrierten Index bereitgestellt. Änderungen an Ihren Inhalten, die nach der Migration aufgetreten sind, werden erst nach der Durchforstung in den migrierten Index aufgenommen. Die meisten Kunden bemerken nicht, dass die Ergebnisse nach Abschluss der Verschiebung Ihrer SharePoint Online-Daten weniger frisch sind, aber einige Kunden können in den ersten 24-48 Stunden eine geringere Aktualität erfahren. 
  
Die folgenden Suchfeatures sind betroffen:
  
- Suchergebnisse und Such-Webparts: Ergebnisse schließen keine Änderungen ein, die nach der Migration aufgetreten sind, bis Sie durchforstet werden. 
    
- Untersuchen: verTiefen enthält keine Änderungen, die nach der Migration aufgetreten sind, bis Sie durchforstet werden.
    
- Popularitäts-und Suchberichte für die Website: Zählungen für Excel-Berichte am neuen Speicherort enthalten nur migrierte Anzahlen und Zählungen aus Nutzungsberichten, die nach Abschluss der Verschiebung Ihrer SharePoint Online-Daten ausgeführt wurden. Alle Zahlen aus dem zwischen Zeitraum gehen verloren und können nicht wiederhergestellt werden. Dieser Zeitraum ist in der Regel ein paar Tage. Einige Kunden haben möglicherweise kürzere oder längere Verluste.
    
- Videoportal: die Anzeige Anzahl und die Statistiken für das Videoportal hängen von den Statistiken für Excel-Berichte ab, sodass die Anzeige Anzahl und die Statistiken für das Videoportal für den gleichen Zeitraum wie für die Excel-Berichte verloren gehen.
    
- eDiscovery: Elemente, die während der Migration geändert wurden, werden erst angezeigt, wenn die Änderungen durchforstet werden.
    
- Data Loss Protection (DLP): Richtlinien werden nicht für Elemente erzwungen, die sich ändern, bis das Crawlen die Änderungen aufhebt.
    
## <a name="skype-for-business"></a>Skype for Business

Alle Benutzer werden während der über Schaltung bei der Skype for Business-Client Software abgemeldet. Bei der automatischen Anmeldung werden Benutzer innerhalb von zwei Minuten wieder verbunden.
  
|**Features, die während der gesamten Verschiebung funktionieren**|**Features, die während eines Teils der Verschiebung eingeschränkt werden können**|
|:-----|:-----|
| Sofortnachrichten und VoIP-Anrufe  <br/>  Benutzer können Kontakte hinzufügen, Kontaktgruppen hinzufügen, Besprechungen hinzufügen, Ihren Standort festlegen und "was heute geschieht" ändern.  <br/>  Die Einstellungen für audioKonferenz Anbieter (ACP) werden in den Geo des Ziel-Datencenters kopiert. Wenn der ACP-Anbieter im Zieldatencenter vorhanden ist, funktioniert er. Andernfalls ist dies nicht der Fall.  <br/> | MandantenAdministrator-TRPS (Mandanten-Remote-PowerShell) stehen Administratoren nicht zum Erstellen von Sitzungen zur Verfügung.  <br/>  Der Mandantenadministrator LAC steht Administratoren nicht zur Verfügung, um sich anzumelden und Benutzereinstellungen zu ändern.  <br/> |
   
|**Nach der Verschiebung**|
|:-----|
| Besprechungsdaten (hochgeladene Präsentationen usw.) werden nicht verschoben und müssen erneut hochgeladen werden.  <br/>  Ältere lync-Clients, wie beispielsweise der lync 2010-Client und lync für Mac 2011-Client, wissen, dass DNS-Informationen mit dem Dienst, der Anmeldeprobleme verursacht, zwischengespeichert werden. Das Löschen des DNS-Caches ist möglicherweise erforderlich, wenn der Benutzer nicht auf dem neuesten Windows-Client für Skype for Business ist. Fordern Sie die Benutzer auf, den Problembehandlungs- [Assistenten](https://support.microsoft.com/en-us/kb/2541980) auszuführen, und folgen Sie den Anweisungen zum Löschen des Clientcaches. Lync für Mac-Clientbenutzer sollten [diese Anweisungen](https://support.microsoft.com/en-us/kb/2629861)befolgen.  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>Skype for Business-Moves, die einen Drittanbieter für audioKonferenzen einbeziehen
Add-on-Dienste eines Drittanbieters für audioKonferenzen für Skype for Business stehen nicht für Benutzer zur Verfügung, die in neuen Geo-spezifischen Rechenzentren verwaltet werden.  Bestehende Kunden, die einen Drittanbieterdienst für audioKonferenzen verwenden, sollten keine Verschiebung zu einem neuen geografischen Rechenzentrum anfordern.  Neue Kunden, die in den neuen Geo-spezifischen Rechenzentren bereitgestellt werden, müssen eine Verschiebung zu einem regionalen Rechenzentrum anfordern, um einen Drittanbieter für audioKonferenzen zu verwenden.

## <a name="data-for-other-services-including-teams-yammer-and-power-bi"></a>Daten für andere Dienste, einschließlich Teams, jammern und Power BI

Wir verschieben nur Kundendaten für Exchange Online, SharePoint Online und Skype for Business. Daten für andere Dienste werden nicht verschoben. Es gibt keine Änderung oder Auswirkung für Sie als Kunde oder Benutzer dieser anderen Dienste. Der Verschiebungsprozess wirkt sich nicht auf Sie aus, und der Speicherort der Kundendaten bleibt unverändert.
  
## <a name="related-topics"></a>Verwandte Themen 
 
[Anfordern der Datenverschiebung](request-your-data-move.md)
    
[Allgemeine häufig gestellte Fragen zu Datenverschiebung](data-move-faq.md)
  
[Neues Datencenter GEOS für Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/en-us/regions/)

