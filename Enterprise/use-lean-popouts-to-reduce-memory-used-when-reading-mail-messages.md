---
title: Verwenden Sie schlanke Popouts zur Reduzierung der Arbeitsspeicher, die beim Lesen von e-Mail-Nachrichten verwendet
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachricht Download in Outlook im Web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540797"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Verwenden Sie schlanke Popouts zur Reduzierung der Arbeitsspeicher, die beim Lesen von e-Mail-Nachrichten verwendet

Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachricht Download in Outlook im Web. Dieser Artikel ist Teil des Projekts [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune) .
   
Als globaler Office 365-Administrator können Sie Outlook im Web zur Bereitstellung von *schlanke Popouts* , eine kleinere, weniger Arbeitsspeicher-Intensive Version von bestimmten e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer konfigurieren. Wenn schlanke Popouts für Outlook im Web konfiguriert werden, werden serverseitige Komponenten gerendert geladen, die Leistung zu optimieren. 
  
> [!NOTE]
> Ab März 2018 sind schlanke Popouts derzeit nicht verfügbar für Nachrichten, die Verwendung Rechte Einschränkungen, wie etwa Information Rights Management (IRM) angeben. 
  
Diese Features sind weiterhin im Hauptfenster von funktionsfähig sind jedoch nicht verfügbar in schlanke Popouts:
  
- Outlook-Add-Ins
    
- Skype für Business Anwesenheit
    
 **So konfigurieren Sie schlanke Popouts für alle Benutzer in Office 365-Organisation**
  
1. [Verbindung mit Exchange Online mit Remote-PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Führen Sie das Cmdlet " [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) " mit dem Parameter LeanPopoutEnabled wie folgt aus: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Wenn Sie beispielsweise schlanke Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Schlanke Popouts für alle Benutzer in Ihrer Organisation zu deaktivieren:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


