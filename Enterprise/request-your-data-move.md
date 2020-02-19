---
title: Anfordern der Datenverschiebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
f1.keywords:
- NOCSH
description: Bestehende Office 365-Kunden müssen die Verschiebung der Kundendaten der teilnehmenden Office 365-Dienste in den neuen geografischen Raum vor dem Stichtag für Ihr Land anfordern.
ms.openlocfilehash: 506943ce802adbd8d443cfb69212834b9c552f61
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106226"
---
# <a name="how-to-request-your-data-move"></a>Anfordern der Datenverschiebung

> [!NOTE]
> Die Informationen auf dieser Seite gelten nur für Kunden, die bereits über Office 365-Mandanten verfügten, bevor die neuen Datencenter in Ihrem geografischen Raum gestartet wurden. 
  
Bestehende Office 365-Kunden sind berechtigt, frühzeitige Migrationen der die wichtigsten ruhenden Kundendaten Ihrer gesamten Organisation anzufordern.  
  
## <a name="when-can-i-request-a-move"></a>Wann kann ich eine Verschiebung anfordern?

|**Kunden mit Anmeldeland in**|**Der Anforderungszeitraum beginnt**|**und endet**|
|:-----|:-----|:-----|
|Japan  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Australien, Neuseeland, Fidschi  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Indien  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Kanada  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Vereinigtes Königreich  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Südkorea  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Frankreich  <br/> |1. Januar 2020  <br/> |30. Juni 2020  <br/> |
|Vereinigte Arabische Emirate  <br/> |15. Juli 2019  <br/> |30. Juni 2020  <br/> |
|Südafrika  <br/> |25. Juli 2019  <br/> |30. Juni 2020  <br/> |
|Schweiz, Liechtenstein  <br/> |10. Dezember 2019  <br/> |30. Juni 2020  <br/> |
|Deutschland  <br/> |Geplant  <br/> |Geplant  <br/> |
   
## <a name="how-to-request-a-move"></a>So fordern Sie eine Migration an

Berechtigten Kunden wird im [Microsoft 365 Admin Center](https://aka.ms/365admin) eine Seite angezeigt, auf der sie die Verschiebung ihrer wichtigsten Kundendaten in die neue Region des Datencenters anfordern können.  
  
Um auf die Seite im Microsoft 365 Admin Center zuzugreifen, erweitern Sie im Navigationsbereich auf der linken Seite **Einstellungen**, und klicken Sie dann auf **Einstellungen**.
Wählen Sie die Registerkarte **Organisationsprofil**aus, und wählen Sie dann die Option **Data Residency**aus.
  
**Möglicherweise wird dieser Abschnitt nicht angezeigt, wenn eines von Folgendem zutrifft**:
- Ihr Mandant ist für das Office 365-Verschiebungsprogramm nicht berechtigt.  Die Berechtigung wird durch das Anmeldeland des Mandanten bestimmt.
- Alle Ihre wichtigsten ruhenden Kundendaten befinden sich bereits im neuen geografischen Raum (siehe den Abschnitt „Datenspeicherort“ der Seite). 
  
Wenn Ihre Organisation Anforderungen an die Data Residency hat und Sie eine frühe Migration anfordern müssen, klicken Sie in dem Abschnitt oben rechts auf **Anmelden**. Auf der rechten Seite des Bildschirms wird ein neuer Abschnitt angezeigt, in dem die Einzelheiten des Office 365-Verschiebungsprogramms erklärt werden. Klicken Sie auf die Umschaltfläche neben dem Text: **Ich möchte die wichtigsten ruhenden Kundendaten meiner Organisation migrieren**. Klicken Sie dann auf **Speichern**.
  
![Bildschirm für die Datencenter-Anmeldung](media/dataresidencyflyoutae.jpg)
  
Im Abschnitt **Data Residency** sollte ein geänderter Text angezeigt werden, der darauf hinweist, dass **Ihre Organisation die Verschiebung ihrer wichtigsten Kundendaten angefordert hat**. Außerdem erhalten Sie im Nachrichtencenter eine Bestätigungsmeldung. Damit wird bestätigt, dass Sie die Verschiebung erfolgreich angefordert haben. 


  
## <a name="what-happens-after-requesting-a-move"></a>Was geschieht nach der Anforderung einer Verschiebung?

Nachdem Sie eine Verschiebung angefordert haben, beabsichtigen wir, Ihre Daten zu migrieren, so schnell es unsere betrieblichen Beschränkungen erlauben. Aufgrund des unberechenbaren Charakters vieler Beschränkungen können wir kein bestimmtes Datum oder einen bestimmten Zeitrahmen für die Verschiebungen angeben. Nach Abschluss der Verschiebung wird eine Meldung angezeigt.
  
Eine Verschiebung kann bis zu 24 Monate ab dem Stichtag der Anforderung dauern.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Kunden in berechtigten Office 365-Ländern können sich ab Januar 2020 für die Migration von Microsoft Teams-Chatdienstdaten anmelden.  Die Anmeldezeitachsen wurden für alle berechtigten Länder neu geöffnet oder erweitert, damit die Kunden die Möglichkeit haben, hinsichtlich Microsoft Teams das frühe Migrationsprogramm in Betracht zu ziehen.   

## <a name="optional-actions-before-you-request-a-move"></a>Optionale Aktionen vor dem Anfordern einer Verschiebung

Führen Sie gegebenenfalls die folgenden Schritte aus.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Wenn Sie eine IP-basierte Firewall verwenden, fügen Sie Zulassungsregeln für die neuen IP-Adressen hinzu.

Wir empfehlen für Firewalls die Verwendung der DNS-Filterung anstelle von IP-Adressen. Es sind keine neuen DNS-Einträge erforderlich.
  
Wenn Sie eine IP-basierte Firewall für die Internetverbindung verwenden, müssen Sie Zulassungsregeln für die neuen IP-Adressen des geografischen Raumr des Ziel-Datencenters hinzufügen. IP-Adressen für den neuen geografischen Raum des Datencenters werden zusätzlich zu neuen Servern kontinuierlich zu [URLs und IP-Adressbereichen für Office 365](https://go.microsoft.com/fwlink/p/?LinkId=229631) hinzugefügt.
  
In Ihrer Firewall-Dokumentation finden Sie Informationen zum Hinzufügen von Zulassungsregeln (auch als Whitelist bezeichnet).
  
Nach dem Hinzufügen von IP-Adressen möchten Sie möglicherweise die Verbindung zum neuen geografischen Raum des Datencenters testen. Dazu wird empfohlen, einen [neuen, ﻿kostenlosen 30-tägigen Test](https://go.microsoft.com/fwlink/?LinkId=522463)mandanten zu erstellen, sobald der neue geografische Raum des Datencenters verfügbar ist. 
  
### <a name="test-using-a-new-tenant"></a>Testen der Verwendung eines neuen Mandanten

Wenn Sie die Verbindung vor der Verschiebung testen möchten, können Sie einen [neuen, ﻿kostenlosen 30-tägigen Testmandanten einrichten](https://go.microsoft.com/fwlink/?LinkId=522463), nachdem der neue geografische Raum des Datencenters verfügbar ist, und ihn nutzen, um Office 365 im neuen geografischen Raum des Datencenters zu erleben. 
  
Der Testmandant kann nicht mit dem vorhandenen Mandanten kombiniert werden:
  
- Benutzer müssen ein separates Testkonto für Ihre Tests verwenden.
    
- Es gibt keine Möglichkeit, Daten zwischen Mandanten zu übertragen.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Informieren Sie Benutzer, veraltete Exchange-Einstellungen auf Mobilgeräten zu aktualisieren.

Wenn Benutzer ein Mobilgerät besitzen, auf dem der Exchange-Server **m.Outlook.com** oder **podxxxxx.outlook.com** festgelegt ist, empfehlen wir, zu **outlook.office365.com** zu wechseln. Folgen Sie den Anweisungen in [Einrichten der Synchronisierung eines Mobilgeräts mit Ihrem Konto](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Verwandte Themen

[Verschieben von Kundenkerndaten in neue Office 365-Datencenter-Regionen](moving-data-to-new-datacenter-geos.md)

[Allgemeine häufig gestellte Fragen zur Datenverschiebung](data-move-faq.md)

[Neue Rechenzentrumsregionen für Microsoft Dynamics CRM Live](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Azure-Dienste nach Region](https://azure.microsoft.com/regions/)
  

