---
title: Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Erfahren Sie, wie Die eine Office 365-Gruppe mit einem bestimmten bevorzugten Datenspeicherort in einer Multi-Geo-Umgebung erstellen.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070001"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD

Wenn ein Benutzer in einer Multi-Geo-Umgebung eine Office 365-Gruppe erstellt, wird als bevorzugter Datenspeicherort der Gruppe automatisch der dieses Benutzers festgelegt. Wenn Sie eine Gruppe mit einem bestimmten PLD erstellen möchten, können Sie dies unter Verwendung von Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet vornehmen. Wenn Sie dies tun, werden das zugewiesene Gruppenpostfach und die SharePoint-Website für die Gruppe der angegebenen Verteilerliste an diesem bestimmten PLD bereitgestellt.

Sie müssen ein globaler Administrator, ein SharePoint Onlineadministrator oder ein Exchange-Onlineadministrator sein, um dies ausführen zu können.

Um eine Office 365-Gruppe mit dem von Ihnen festgelegten PLD zu erstellen, stellen Sie eine Verbindung zu Exchange Online PowerShell her und geben Sie den Parameter *-MailBoxRegion* mit dem Code des Geo-Standorts weiter.

Beispiel: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot des New-UnifiedGroup PowerShell cmdlet mit Syntax](media/multi-geo-new-group-with-pdl-powershell.png)

Beachten Sie, dass die Bereitstellung von SharePoint-Gruppenseiten nach Bedarf erfolgt. Die Seite wird bereitgestellt, wenn ein Gruppenbesitzer oder -mitglied zum ersten Mal auf diese zugreift.

## <a name="geo-location-codes"></a>Codes für geografische Standorte

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).