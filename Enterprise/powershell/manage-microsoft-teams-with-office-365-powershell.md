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
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429198"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="ccfa0-103">Verwalten von Microsoft Teams mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccfa0-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="ccfa0-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="ccfa0-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ccfa0-105">Sie können Microsoft Teams mit PowerShell verwalten.</span><span class="sxs-lookup"><span data-stu-id="ccfa0-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="ccfa0-106">Installieren Sie zunächst das [Microsoft Teams-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="ccfa0-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="ccfa0-107">Melden Sie sich mit einem Benutzernamen und einem Kennwort an.</span><span class="sxs-lookup"><span data-stu-id="ccfa0-107">Sign in with a user name and password</span></span>

<span data-ttu-id="ccfa0-108">Für die Office 365-Welt (+ gcc)-Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="ccfa0-109">Für die Office 365 US Governmental DoD Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="ccfa0-110">Für die Office 365 US-Regierung gcc High Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="ccfa0-111">Anmelden mit mehrstufiger Authentifizierung (MFA)</span><span class="sxs-lookup"><span data-stu-id="ccfa0-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="ccfa0-112">Für die Office 365-Welt (+ gcc)-Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="ccfa0-113">Für die Office 365 US Governmental DoD Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="ccfa0-114">Für die Office 365 US-Regierung gcc High Cloud:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="ccfa0-115">Trennen der Verbindung mit Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ccfa0-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="ccfa0-116">Verwenden Sie dazu diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="ccfa0-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="ccfa0-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ccfa0-117">See also</span></span>

[<span data-ttu-id="ccfa0-118">Übersicht über Microsoft Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccfa0-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="ccfa0-119">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccfa0-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ccfa0-120">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ccfa0-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

