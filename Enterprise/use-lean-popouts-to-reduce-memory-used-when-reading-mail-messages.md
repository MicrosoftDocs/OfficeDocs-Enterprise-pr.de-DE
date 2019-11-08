---
title: Verringern des beim Lesen von e-Mail-Nachrichten verwendeten Arbeitsspeichers mithilfe von Lean Popouts
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Internet.
ms.openlocfilehash: bb9a11a27af0b66f1dd557c459d1904c2e57ae92
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030870"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Verringern des beim Lesen von e-Mail-Nachrichten verwendeten Arbeitsspeichers mithilfe von Lean Popouts

Dieser Artikel enthält Informationen zum Verbessern der Leistung von Nachrichten Downloads in Outlook im Internet. Dieser Artikel ist Teil der [Netzwerkplanung und Leistungsoptimierung für Office 365](https://aka.ms/tune) -Projekt.
   
Als Office 365 globaler Administrator können Sie Outlook im Internet so konfigurieren, dass es *schlanke Popouts* , eine kleinere, weniger arbeitsspeicherintensive Version bestimmter e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer. Wenn Lean Popouts für Outlook im Internet konfiguriert sind, werden serverseitige gerenderte Komponenten geladen, die die Leistung optimieren. 
  
> [!NOTE]
> Seit März 2018 stehen Lean-Popouts derzeit nicht für Nachrichten zur Verfügung, die Nutzungsrechte Einschränkungen angeben, beispielsweise IRM (Information Rights Management, Verwaltung von Informationsrechten). 
  
Diese Features funktionieren weiterhin im Hauptfenster, stehen aber in Lean Popouts nicht zur Verfügung:
  
- Outlook-Add-Ins
    
- Skype for Business Anwesenheit
    
 **So konfigurieren Sie Lean Popouts für alle Benutzer in Ihrer Office 365 Organisation**
  
1. Stellen [Sie mithilfe von Remote-PowerShell eine Verbindung zu Exchange Online her](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Führen Sie das Cmdlet " [OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) " mit dem Parameter "LeanPopoutEnabled" wie folgt aus: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Um beispielsweise Lean Popouts für alle Benutzer in Ihrer Organisation zu aktivieren:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  So deaktivieren Sie Lean Popouts für alle Benutzer in Ihrer Organisation:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


