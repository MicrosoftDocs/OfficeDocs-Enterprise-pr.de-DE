---
title: Verwenden von Lean Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten
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
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Web.
ms.openlocfilehash: 55cbdec3dc994f3301afaf1bf0a261de446d522a
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655779"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Verwenden von Lean Popouts zum Verringern des Arbeitsspeichers beim Lesen von e-Mail-Nachrichten

Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Web. Dieser Artikel ist Teil des Projekts [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) .
   
Als globaler Office 365-Administrator können Sie Outlook im Web so konfigurieren, dass *Lean Popouts* , eine kleinere, weniger speicherintensive Version bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer, bereitgestellt wird. Wenn Lean-Popouts für Outlook im Web konfiguriert sind, werden serverseitige gerenderte Komponenten geladen, die die Leistung optimieren. 
  
> [!NOTE]
> Ab März 2018 sind Lean-Popouts derzeit nicht für Nachrichten verfügbar, die Nutzungsrechte Einschränkungen wie Information Rights Management (IRM) angeben. 
  
Diese Features funktionieren weiterhin im Hauptfenster, sind jedoch nicht in Lean Popouts verfügbar:
  
- Outlook-Add-Ins
    
- Skype for Business-Anwesenheit
    
 **So konfigurieren Sie Lean-Popouts für alle Benutzer in Ihrer Office 365-Organisation**
  
1. [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Führen Sie das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) mit dem Parameter LeanPopoutEnabled wie folgt aus: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Um beispielsweise Lean-Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  So deaktivieren Sie Lean-Popouts für alle Benutzer in Ihrer Organisation:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


