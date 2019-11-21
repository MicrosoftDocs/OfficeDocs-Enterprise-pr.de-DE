---
title: Während und nach der Datenverschiebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Datenverschiebungen stellen einen Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer dar. Es ist keine Aktion erforderlich, während Microsoft jeden Dienst und die zugehörigen Daten für Ihren Mandanten in ein neues Rechenzentrum Geo verschiebt. Die Datenübertragung und-Validierung erfolgt vorab im Hintergrund mit minimalen Auswirkungen auf die Benutzer.
ms.openlocfilehash: 333c29d4087e18b477f124ca406de4936d1bd5e3
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756574"
---
# <a name="during-and-after-your-data-move"></a>Während und nach der Datenverschiebung

Datenverschiebungen stellen einen Back-End-Vorgang mit minimalen Auswirkungen auf die Endbenutzer dar. Es ist keine Aktion erforderlich, während Microsoft jeden Dienst und die zugehörigen Daten für Ihren Mandanten in ein neues Rechenzentrum Geo verschiebt. Die Datenübertragung und-Validierung erfolgt vorab im Hintergrund mit minimalen Auswirkungen auf die Benutzer.
  
> [!NOTE]
> Verschiebungen treten zu unterschiedlichen Zeiten für jeden Dienst auf. Dadurch werden die beschriebenen reduzierten Funktionen für jeden Dienst zu einem anderen Zeitpunkt angezeigt. 
  
Sehen Sie sich das Office 365 Nachrichten Center zur Bestätigung an, wenn die Verschiebungen für die einzelnen Exchange Online, SharePoint Online und Skype for Business abgeschlossen sind. Wie in der folgenden Tabelle dargestellt, kann es bis zu 24 Monate dauern, nach Ablauf des Registrierungszeitraums alle erforderlichen Datenverschiebungen für alle Kunden in einem bestimmten Geo abzuschließen. Wenn Sie nach dem Wechsel Probleme mit Ihrem Mandanten feststellen, wenden Sie sich an [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) , um Hilfe zu erhalten. 
  

|**Kunden mit Rechnungsadresse in**|**Alle abgeschlossenen Verschiebungen**|
|:-----|:-----|
|Australien, Neuseeland, Fidschi  <br/> |31. Oktober 2017  <br/> |
|Japan  <br/> |31. Oktober 2018  <br/> |
|India  <br/> |31. Oktober 2018  <br/> |
|Kanada  <br/> |30. Juni 2019  <br/> |
|Südkorea  <br/> |31. Oktober 2018  <br/> |
|Vereinigtes Königreich  <br/> |15. September 2019  <br/> |
|Frankreich  <br/> |15. September 2020  <br/> |
|Vereinigte Arabische Emirate  <br/> |1. Februar 2022  <br/> |
|Südafrika  <br/> |1. Februar 2022  <br/> |
   
## <a name="exchange-online"></a>Exchange Online

Da es Zeit braucht, um jeden Benutzer zu einem neuen Geo-Rechenzentrum für einen einzelnen Mandanten zu versetzen, befinden sich einige Benutzer während des Wechsels weiterhin im alten Rechenzentrum, während sich andere in der neuen Geo-Rechenzentrum befinden. Dies bedeutet, dass einige Features, die den Zugriff auf mehrere Postfächer beinhalten, möglicherweise während eines Zeitraums des Verschiebevorgangs nicht vollständig funktionieren, was letzten Wochen dauern kann. Diese Features werden in den folgenden Abschnitten beschrieben.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Öffnen Sie "freigegebener Ordner" in Outlook Web Access

Einige Benutzer öffnen einen freigegebenen e-Mail-Ordner aus einem anderen Postfach (für das der Benutzer über Lese-oder Schreibberechtigungen verfügt) in Outlook Web Access mit dem Feature "freigegebene Ordner". In der folgenden Tabelle wird beschrieben, wie der Zugriff auf freigegebene Ordner während einer Post Fach Verlagerung funktioniert. Beachten Sie, dass Benutzer mit vollständigen Berechtigungen für ein freigegebenes Postfach das Postfach mithilfe von Outlook Web Access während des Wechsels öffnen können. 
  
|**Konfiguration**|**Beschreibung**|
|:-----|:-----|
|Benutzer verfügt über Postfachordner Berechtigung für ein anderes Postfach  <br/> |Möglicherweise limitiert.  <br/> Wenn sich Benutzer a und Postfach b während der Mandanten Verlagerung nicht in demselben Geo befinden, kann Benutzer a den Ordner "Postfach b" nicht in Outlook Web Access öffnen, wenn Benutzer a nur über die Berechtigung für einen bestimmten Ordner in Postfach b verfügt.  <br/> Klicken Sie zum Hinzufügen eines freigegebenen Ordners mit der rechten Maustaste auf den Benutzernamen im linken Navigationsbereich, und wählen Sie **freigegebener Ordner hinzufügen**aus.  <br/> |
|Benutzer mit vollständiger Post Fach Berechtigung für ein anderes Postfach  <br/> |Vollständig unterstützt.  <br/> Wenn Benutzer a über die Berechtigung "Vollzugriff" für Postfach b verfügt, kann Benutzer a auf den freigegebenen Ordner im linken Navigationsbereich in Outlook Web Access klicken, um ein Fenster mit Postfach b zu öffnen.  Ein Benutzer kann ein freigegebenes Postfach mit Outlook Web Access während des Wechsels ohne unerwünschte Auswirkungen öffnen. Die Einschränkung gilt nur für die Freigabe auf Ordnerebene in einem Postfach.           |
   
### <a name="public-folders"></a>Öffentliche Ordner

Wenn sich das Postfach für Öffentliche Ordner vorübergehend in einem anderen Rechenzentrum als der Benutzer befindet, der versucht, darauf zuzugreifen, kann der Benutzer möglicherweise nicht auf das Postfach für Öffentliche Ordner zugreifen. 
  
### <a name="online-archives"></a>Online Archive

Während der Vorgang wird ausgeführt, können Benutzer, die über Outlook für Mac eine Verbindung herstellen, möglicherweise keine Verbindung mit Ihrem Onlinearchivpostfach herstellen. Der Zugriff auf das Archivpostfach für Benutzer, die eine Verbindung mit Outlook und Outlook Web Access herstellen, wird unterstützt.
  
## <a name="sharepoint-online"></a>SharePoint Online

Wenn SharePoint Online verschoben wird, werden auch die Daten für die folgenden Dienste verschoben:
  
- One Drive for Business
    
- Project Online
    
- Project für Office 365
    
- Office 365 Video Dienste
    
- Office im s-Browser
    
- Office 365 ProPlus
    
- Visio Pro für Office 365
    
Nachdem Sie die SharePoint Online Daten verschoben haben, werden möglicherweise einige der folgenden Effekte angezeigt.
  
### <a name="office-365-video-services"></a>Office 365 Video Dienste

- Die Datenverschiebung für Video dauert länger als die Verschiebungen für den Rest ihres Inhalts in SharePoint Online.
    
- Nachdem der SharePoint Online Inhalt verschoben wurde, wird ein Zeitrahmen vorhanden sein, wenn Videos nicht wiedergegeben werden können.
    
- Wir entfernen die transcodierten Kopien aus dem vorherigen Datencenter und Transkodieren Sie erneut im neuen Datencenter.
    
### <a name="search"></a>Suche

Bei der Verschiebung Ihrer SharePoint Online Daten migrieren wir den Such Index und die Sucheinstellungen an einen neuen Speicherort. Bis wir den Umzug Ihrer SharePoint Online Daten **abgeschlossen** haben, werden Ihre Benutzer weiterhin vom Index am ursprünglichen Speicherort bedient. Am neuen Speicherort beginnt die Suche automatisch mit dem Crawlen Ihrer Inhalte, nachdem die SharePoint Online Daten verschoben wurden. Ab diesem Moment werden Ihre Benutzer aus dem migrierten Index bedient. Änderungen an Ihren Inhalten, die nach der Migration aufgetreten sind, werden erst dann in den migrierten Index aufgenommen, wenn Sie Durchforstung abgeholt werden. Die meisten Kunden bemerken nicht, dass die Ergebnisse nach dem Verschieben Ihrer SharePoint Online Daten weniger frisch sind, einige Kunden jedoch in den ersten 24-48 Stunden möglicherweise eine geringere Aktualität erfahren. 
  
Die folgenden Suchfeatures sind betroffen:
  
- Suchergebnisse und Such-Webparts: Ergebnisse enthalten keine Änderungen, die nach der Migration aufgetreten sind, bis das Crawlen Sie abnimmt. 
    
- Vertiefen: vertiefen schließt keine Änderungen ein, die nach der Migration aufgetreten sind, bis durch das Crawlen diese abgeholt wird.
    
- Beliebtheits-und suchberichte für die Website: Counts for Excel Reports im neuen Speicherort umfassen nur migrierte Zählungen und Zählungen aus Verwendungsberichten, die ausgeführt wurden, nachdem das Verschieben der SharePoint Online Daten abgeschlossen wurde. Alle Zählungen aus der Zwischenzeit gehen verloren und können nicht wiederhergestellt werden. Dieser Zeitraum ist normalerweise ein paar Tage. Einige Kunden können kürzere oder längere Verluste erfahren.
    
- Videoportal: anzeigen Anzahl und Statistik für das Videoportal hängen von der Statistik für Excel-Berichte ab, sodass die Anzahl und die Statistiken für das Videoportal für den gleichen Zeitraum wie für Excel-Berichte verloren gehen.
    
- eDiscovery: Elemente, die während der Migration geändert wurden, werden erst angezeigt, wenn die Durchforstung die Änderungen einnimmt.
    
- Data Loss Protection (DLP): Richtlinien werden nicht für Elemente erzwungen, die sich ändern, bis durch das Crawlen die Änderungen einnimmt.
    
## <a name="skype-for-business"></a>Skype for Business

Alle Benutzer werden während des Umschaltens von der Skype for Business-Client Software abgemeldet. Bei der automatischen Anmeldung werden die Benutzer innerhalb von zwei Minuten erneut verbunden.
  
|**Funktionen, die während des gesamten Wechsels funktionieren**|**Features, die während eines Teils des Wechsels möglicherweise eingegrenzt werden**|
|:-----|:-----|
| Instant Messaging und Sprachanrufe  <br/>  Benutzer können Kontakte hinzufügen, Kontaktgruppen hinzufügen, Besprechungen hinzufügen, Ihren Standort festlegen und "What es Happening Today" ändern.  <br/>  ACP-Einstellungen (Audio Conferencing Provider) werden in das Ziel-Datencenter Geo kopiert. Wenn der ACP-Anbieter im Zieldatencenter vorhanden ist, kann er funktionieren. Andernfalls wird dies nicht der Fall sein.  <br/> | Mandantenadministrator-TRPS (Mandanten-Remote-PowerShell) steht Administratoren zum Erstellen von Sitzungen nicht zur Verfügung.  <br/>  Der mandantenadministrator Lac steht Administratoren nicht zur Verfügung, um sich anzumelden und Benutzereinstellungen zu ändern.  <br/> |
   
|**Nach dem Wechsel**|
|:-----|
| Besprechungsdaten (hochgeladene Präsentationen usw.) werden nicht weiterentwickelt und müssen erneut hochgeladen werden.  <br/>  Ältere lync-Clients, wie der Client für lync 2010 Client und lync für Mac 2011, sind bekannt für die Zwischenspeicherung von DNS-Informationen mit dem Dienst, der Anmeldeprobleme verursacht. Das Löschen des DNS-Caches ist möglicherweise erforderlich, wenn sich der Benutzer nicht auf dem neuesten Skype for Business Windows-Client befindet. Weitere Informationen finden Sie unter [Troubleshooting Skype for Business Online DNS Configuration Issues in Office 365](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue). Lync für Mac-Clientbenutzer sollten [diese Anweisungen](https://support.microsoft.com/kb/2629861)befolgen.  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>Skype for Business-Moves, die einen Drittanbieter für Audiokonferenzen einbeziehen
Add-on-Dienste von Drittanbieter-Audiokonferenz-Anbietern für Skype for Business stehen nicht für Benutzer zur Verfügung, die in neuen Geo-spezifischen Rechenzentren verwaltet werden.  Vorhandene Kunden, die einen Drittanbieterdienst für Audiokonferenzen verwenden, sollten keine Umstellung auf ein neues Geo-spezifisches Rechenzentrum anfordern.  Neue Kunden, die in den neuen Geo-spezifischen Rechenzentren bereitgestellt werden, müssen eine Verlagerung an ein regionales Rechenzentrum anfordern, um einen Drittanbieter für Audiokonferenzen verwenden zu können.
  
## <a name="related-topics"></a>Verwandte Themen 
 
[Anfordern der Datenverschiebung](request-your-data-move.md)
    
[Allgemeine häufig gestellte Fragen zur Datenverschiebung](data-move-faq.md)
  
[Neues Datacenter GEOS für Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/regions/)

