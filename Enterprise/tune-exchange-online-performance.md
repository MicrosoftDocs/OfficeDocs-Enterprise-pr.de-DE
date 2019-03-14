---
title: Optimieren der Leistung von Exchange Online
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Ihnen mitteilen, wie Sie die Leistung von Exchange Online verbessern.
ms.openlocfilehash: f75869ba6d83a92b1e19743c8b38c4bcbb6762cf
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372852"
---
# <a name="tune-exchange-online-performance"></a>Optimieren der Leistung von Exchange Online

Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Ihnen mitteilen, wie Sie die Leistung von Exchange Online verbessern, insbesondere vor einer Migration. Dieser Artikel ist Teil des Projekts [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Zu berücksichtigende Aspekte für die Verbesserung der Leistung von Exchange Online

Berücksichtigen Sie Folgendes, um die Migrations Geschwindigkeit zu verbessern und die Bandbreiteneinschränkungen Ihrer Organisation für Exchange Online zu verringern:
  
- **Verringern der Postfachgröße.** Geringere Postfachgröße verbessert die Migrations Geschwindigkeit. 
    
- **Verwenden Sie die Post Fach Verschiebungsfunktionen in einer Exchange-hybridbereitstellung.** Bei einer Exchange-hybridbereitstellung werden offline-e-Mails (in der Form von. OST-Dateien) erfordert keinen erneuten Download bei der Migration zu Exchange Online. Dadurch werden die Anforderungen an die Download Bandbreite deutlich reduziert. 
    
- **Planen Sie die Postfachverschiebungen in Zeiten mit niedrigem Internet Datenverkehr und einer niedrigen lokalen Exchange-Verwendung.** Bei der Planung von Verschiebungen werden Migrationsanforderungen an den Replikations Proxy übermittelt und werden möglicherweise nicht sofort ausgeführt. 
    
- **Verwenden Sie Lean Popouts für Outlook im Web.** Lean Popouts bieten kleinere, weniger speicherintensive Versionen bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer, indem Sie einige Komponenten auf dem Server rendern. Weitere Informationen finden Sie unter [Verwenden von Lean-Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Allgemeine Ratschläge

- Stellen Sie sicher, dass die DNS-Suche für outlook.office.com in das MS-Datencenter an einem logischen Eingabespeicherort für Ihren Standort gelangt.

- Recherchieren Sie das Zwischenspeichern von Postfächern, und wählen Sie die entsprechenden Optionen aus. zwischen Speicherungszeitraum, Zwischenspeicherung für freigegebene Postfächer usw.).

- Halten Sie Ihre Outlook-Daten von der Übergabe von VPN-Verbindungen (an eine zentrale) ab, bevor Sie über das Internet übertragen werden.

- Stellen Sie sicher, dass die Postfachdaten den Einschränkungen für Ordner und Element, Beträge entsprechen.
    
Weitere Informationen zur Exchange-Migrationsleistung finden Sie unter [Office 365-Migrationsleistung und bewährte Methoden](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

