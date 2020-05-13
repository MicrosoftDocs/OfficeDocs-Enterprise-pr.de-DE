---
title: Verwalten von Microsoft Teams mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Zusammenfassung: Verwenden Sie Office 365 PowerShell, um Ihre Microsoft Teams zu verwalten.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209121"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Verwalten von Microsoft Teams mit Office 365 PowerShell

Sie können Microsoft Teams mit Office 365 PowerShell verwalten.
  
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


## <a name="see-also"></a>Weitere Artikel

[Übersicht über Microsoft Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

