---
title: Verwalten von Microsoft Teams mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Zusammenfassung: Verwenden Sie PowerShell zum Verwalten von Microsoft Teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230611"
---
# <a name="manage-microsoft-teams-with-powershell"></a>Verwalten von Microsoft Teams mit PowerShell

*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*

Sie können Microsoft Teams mit PowerShell verwalten.
  
Installieren Sie zunächst das [Microsoft Teams-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Melden Sie sich mit einem Benutzernamen und einem Kennwort an.

Für die Office 365-Welt (+ gcc)-Cloud:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Für die Office 365 US Governmental DoD Cloud: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Für die Office 365 US-Regierung gcc High Cloud:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Anmelden mit mehrstufiger Authentifizierung (MFA)

Für die Office 365-Welt (+ gcc)-Cloud:

```powershell
Connect-MicrosoftTeams
```

Für die Office 365 US Governmental DoD Cloud: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Für die Office 365 US-Regierung gcc High Cloud:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Trennen der Verbindung mit Microsoft Teams

Verwenden Sie dazu diesen Befehl:

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>Siehe auch

[Übersicht über Microsoft Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Verwalten von Microsoft 365 mit PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit PowerShell für Microsoft 365](getting-started-with-office-365-powershell.md)

