---
title: Anfordern der Datenverschiebung
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 07/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: Vorhandene Office 365 Kunden müssen vor Ablauf der Frist für Ihr Land eine Anforderung übermitteln, damit die Kundendaten ihrer teilnehmenden Office 365 Dienste in ihren neuen Geo verschoben werden.
ms.openlocfilehash: b1fc5606549597eb91990f3675d4d867d0605f04
ms.sourcegitcommit: 626ffb9907d5225acccf94095f54c8244df8dd49
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "35818025"
---
# <a name="how-to-request-your-data-move"></a>Anfordern der Datenverschiebung

> [!NOTE]
> Die Informationen auf dieser Seite gelten nur für Kunden, die bereits Office 365 Mandanten hatten, bevor die neuen Rechenzentren in Ihrem Geo gestartet wurden. 
  
Vorhandene Office 365 Kunden sind berechtigt, eine frühe Migration für die wichtigsten Kundendaten Ihrer Organisation in Ruhe anzufordern.  
  
## <a name="when-can-i-request-a-move"></a>Wann kann ich eine Bewegung anfordern?

|**Kunden mit Rechnungsadresse in**|**Anforderungs Zeitraum beginnt**|**Anforderungs Frist**|
|:-----|:-----|:-----|
|Japan  <br/> |1. August 2016  <br/> |31. Oktober 2016  <br/> |
|Australien, Neuseeland, Fidschi  <br/> |1. August 2016  <br/> |31. Oktober 2016  <br/> |
|Indien  <br/> |1. August 2016  <br/> |31. Oktober 2016  <br/> |
|Kanada  <br/> |1. August 2016  <br/> |31. Oktober 2016  <br/> |
|Vereinigtes Königreich  <br/> |15. März 2017  <br/> |15. September 2017  <br/> |
|Südkorea  <br/> |1. Mai 2017  <br/> |31. Oktober 2017  <br/> |
|Frankreich  <br/> |14. März 2018  <br/> |15. September 2018  <br/> |
|Vereinigte Arabische Emirate  <br/> |15. Juli 2019  <br/> |31. Januar 2020  <br/> |
|Südafrika  <br/> |Geplante  <br/> |Geplante  <br/> |
   
## <a name="how-to-request-a-move"></a>Vorgehensweise Anfordern einer Verlagerung

Für berechtigte Kunden wird eine Seite in Ihrem [Admin Center](https://aka.ms/365admin)angezeigt, die es Ihnen ermöglicht, Ihre wichtigsten Kundendaten in ihren neuen rechenzentrumsbereich zu verschieben.  
  
Um auf die Seite im Microsoft 365 Admin Center zuzugreifen, erweitern Sie im Navigationsbereich auf der linken Seite **Einstellungen**, und klicken Sie dann auf **Organisationsprofil**.
  
![Menü "Einstellungen" mit hervorgehobenem Organisationsprofil](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
Scrollen Sie auf der Seite **Organisationsprofil** nach unten zum Abschnitt **Data Residency Option** . 
  
![Daten Wohnsitz Karte](media/dataresidencyae.jpg)
  
**Dieser Abschnitt wird möglicherweise nicht angezeigt, wenn einer der folgenden zutrifft**:
- Ihr Mandant ist nicht für das Programm zum Verlegen berechtigt.  Die Berechtigung wird durch das Anmelde Land des Mandanten bestimmt.
- Alle Ihre Daten befinden sich bereits im neuen Geo (siehe Abschnitt "Datenspeicherort" auf der Seite). 
  
Wenn Ihre Organisation über Daten Wohnsitz Anforderungen verfügt und Sie eine frühe Migration anfordern müssen, klicken Sie oben rechts im Abschnitt auf **Bearbeiten** . Auf der rechten Seite des Bildschirms wird ein neuer Abschnitt angezeigt, in dem die Details des Verschiebe Programms erläutert werden. Wählen Sie die Umschaltfläche neben dem Text aus, der ja besagt, dass in **meiner Organisation Daten Wohnsitz Anforderungen erfüllt sind**. Klicken Sie auf **Speichern**.
  
![Datencenter-Anmelde Aktions Bildschirm](media/dataresidencyflyoutae.jpg)
  
Der Text im Abschnitt **Data Residency Option** sollte angezeigt werden, um anzugeben, dass **Ihre Organisation aufgefordert wurde, ihre Hauptkunden Daten zu verlagern.** Sie haben auch eine Bestätigungsmeldung in Ihrem Nachrichtencenter. Dadurch wird bestätigt, dass Sie erfolgreich eine Migration angefordert haben. 


  
## <a name="what-happens-after-requesting-a-move"></a>Was geschieht, nachdem eine Bewegung angefordert wurde?

Nachdem Sie eine Bewegung angefordert haben, werden wir Sie so schnell wie möglich mit unseren betriebsbedingten Einschränkungen umstellen. Aufgrund der unvorhersehbaren Natur vieler Einschränkungen können wir nicht ein bestimmtes Datum oder einen Zeitrahmen für die Verschiebungen freigeben. Nach Abschluss der Migration wird eine Benachrichtigung angezeigt.
  
Es kann bis zu 24 Monate dauern, bis der Anforderungs Termin für Ihr Land abgeschlossen ist.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft Teams unterstützt noch keine Migration von Kundeninhalten im Rest von in-Region-in-Länder-Rechenzentren, in denen Data Residency für Microsoft Teams verfügbar ist.  Daher werden nur neue Kunden alle Daten innerhalb des Landes in den neuen Regionen gespeichert, in denen Microsoft Teams den Daten Wohnsitz unterstützt.  Erfahren Sie mehr über Office 365 Daten Wohnsitz für Ihren Unternehmensstandort unter [wo befinden sich Ihre Daten?](https://products.office.com/where-is-your-data-located)   

## <a name="optional-actions-before-you-request-a-move"></a>Optionale Aktionen vor dem Anfordern einer Migration

Führen Sie die folgenden Schritte je nach Bedarf aus.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Wenn Sie eine IP-basierte Firewall verwenden, fügen Sie Zulassungsregeln für die neuen IP-Adressen hinzu.

Es wird empfohlen, anstelle von IP-Adressen DNS-Filterung für Firewalls zu verwenden. Es sind keine neuen DNS-Einträge erforderlich.
  
Wenn Sie eine IP-basierte Firewall für Internet Konnektivität verwenden, müssen Sie Zulassungsregeln für die neuen IP-Adressen für das Ziel-Datencenter Geo hinzufügen. IP-Adressen für das neue Datencenter GEOS zusätzlich zu neuen Servern werden Office 365- [URLs und IP-Adressbereichen](https://go.microsoft.com/fwlink/p/?LinkId=229631)kontinuierlich hinzugefügt.
  
In der Firewall-Dokumentation finden Sie Informationen zum Hinzufügen von Zulassungsregeln (auch bekannt als Whitelisting).
  
Nach dem Hinzufügen von IP-Adressen möchten Sie möglicherweise die Konnektivität mit dem neuen Geo-Rechenzentrum testen. Dazu wird empfohlen, einen [neuen kostenlosen 30-tägigen Test](https://go.microsoft.com/fwlink/?LinkId=522463) Mandanten zu erstellen, sobald die neue Geo-Rechenzentrum verfügbar ist. 
  
### <a name="test-using-a-new-tenant"></a>Testen mit einem neuen Mandanten

Wenn Sie die Konnektivität vor dem Wechsel testen möchten, können Sie einen [neuen kostenlosen 30-tägigen Testmandanten](https://go.microsoft.com/fwlink/?LinkId=522463) einrichten, nachdem die neue Rechenzentrums-Geo-Version verfügbar ist, und damit Office 365 in der neuen Rechenzentrums-Geo-Umgebung nutzen. 
  
Der Testmandant kann nicht mit dem vorhandenen Mandanten kombiniert werden:
  
- Benutzer müssen für Ihre Tests ein separates Test Konto verwenden.
    
- Es gibt keine Möglichkeit, Daten zwischen Mandanten zu verlagern.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Benachrichtigen der Benutzer zur Aktualisierung veralteter Exchange-Einstellungen auf mobilen Geräten

Wenn Benutzer über ein mobiles Gerät verfügen, dessen Exchange Server auf **m.Outlook.com** oder **podxxxxx.Outlook.com**festgelegt ist, empfehlen wir, zu **Outlook.office365.com**zu wechseln, indem Sie den Anweisungen unter [Einrichten eines mobilen Geräts für die Synchronisierung folgen. mit Ihrem Konto](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Verwandte Themen

[Verschieben der Kern Daten in das neue Office 365-Rechenzentrum GEOS](moving-data-to-new-datacenter-geos.md)

[Allgemeine häufig gestellte Fragen zur Datenverschiebung](data-move-faq.md)

[Neues Datacenter GEOS für Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/en-us/regions/)
  

