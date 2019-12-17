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
ms.openlocfilehash: 96870923c00cebc247609b67378fd39011077d45
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072377"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Erstellen Sie eine Office 365-Gruppe mit einem bestimmten PLD

Wenn ein Benutzer in einer Multi-Geo-Umgebung eine Office 365-Gruppe erstellt, wird als bevorzugter Datenspeicherort der Gruppe automatisch der dieses Benutzers festgelegt. Globale, SharePoint- und Exchange-Administratoren können Gruppen in jeder ausgewählten Region erstellen. 

Wenn Sie eine Gruppe mit einem bestimmten PLD erstellen möchten, können Sie dies über das SharePoint Admin Center oder unter Verwendung des Exchange Online New-UnifiedGroup Microsoft PowerShell-Cmdlets vornehmen. Wenn Sie dies tun, werden das zugewiesene Gruppenpostfach und die SharePoint-Website für die Gruppe der angegebenen Verteilerliste an diesem bestimmten PLD bereitgestellt.

Um eine Office 365-Gruppe mit dem von Ihnen angegebenen PDL zu erstellen, wechseln Sie zum SharePoint Admin Center an dem geografischen Standort, an dem Sie die Gruppenwebsite erstellen möchten.

Zum Beispiel:

Wenn Sie eine Gruppenwebsite an Ihrem Standort in Australien erstellen möchten, wechseln Sie zu https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement.

1. Wählen Sie **+ Erstellen** aus.
2. Führen Sie den Vorgang zum Erstellen einer Gruppenwebsite aus.

Ihre Gruppenwebsite wird an dem geografischen Standort bereitgestellt, der dem SharePoint Admin Center entspricht, von dem aus Sie die Anforderung für die Websiteerstellung initiiert haben. 

Verwenden von Exchange PowerShell 

Stellen Sie eine Verbindung zu Exchange Online PowerShell her, und geben Sie den Parameter *-MailBoxRegion* mit dem Code des geografischen Standorts weiter.

Zum Beispiel: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Screenshot des New-UnifiedGroup PowerShell cmdlet mit Syntax](media/multi-geo-new-group-with-pdl-powershell.png)

Beachten Sie, dass die Bereitstellung von SharePoint-Gruppenseiten nach Bedarf erfolgt. Die Seite wird bereitgestellt, wenn ein Gruppenbesitzer oder -mitglied zum ersten Mal auf diese zugreift.

## <a name="geo-location-codes"></a>Codes für geografische Standorte

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Siehe auch

[Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
