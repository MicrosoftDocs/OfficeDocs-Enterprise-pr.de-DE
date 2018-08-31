---
title: Optimieren der Leistung von Exchange Online
ms.author: krowley
author: kccross
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
description: Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Sie zum Verbessern der Leistung von Exchange Online informieren.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541087"
---
# <a name="tune-exchange-online-performance"></a>Optimieren der Leistung von Exchange Online

Dieser Artikel enthält allgemeine Tipps und Links zu anderen Ressourcen, die Sie zum Verbessern der Leistung von Exchange Online informieren. Dieser Artikel ist Teil des Projekts [netzwerkplanung und leistungsoptimierung für Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Beachten Sie, um Verbessern der Leistung von Exchange Online

Zur Verbesserung der Geschwindigkeit der Migration und zur Reduzierung der bandbreiteneinschränkungen Ihrer Organisation für Exchange Online, berücksichtigen Sie Folgendes ein:
  
- **Verringern Sie die Größe von Postfächern.** Eine geringere Postfachgröße erhöht die Migrationsgeschwindigkeit. 
    
- **Verwenden Sie die Funktionen zur Postfachverschiebung bei einer Exchange-Hybridbereitstellung.** Bei einer Exchange-Hybridbereitstellung erfordert Offline-E-Mail (in Form von OST-Dateien) kein erneutes Herunterladen, wenn zu Exchange Online migriert wird. Damit werden Ihre Bandbreitenanforderungen für Downloads erheblich reduziert. 
    
- **Planen Sie das Verschieben von Postfächern für Zeiten mit geringem Datenverkehr aus dem Internet und geringer lokaler Exchange-Nutzung ein.** Bei der Planung von Verschiebungen werden Migrationsanforderungen an den Postfachreplikationsproxy gesendet, und die Anforderungen erfolgen möglicherweise nicht sofort. 
    
- **Schlanke Popouts für Outlook im Web verwenden.** Schlanke Popouts bieten beträgt, weniger Arbeitsspeicher-Intensive Versionen von bestimmten e-Mail-Nachrichten in Microsoft Edge oder Internet Explorer durch einige Komponenten auf dem Server rendern. Weitere Informationen finden Sie unter [schlanke Popouts verwenden, um Arbeitsspeicher zu reduzieren beim Lesen von e-Mail-Nachrichten verwendet](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).
    
Weitere Informationen zur Leistung von Exchange-Migration finden Sie unter [Office 365-migrationsleistung und bewährte Methoden](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

