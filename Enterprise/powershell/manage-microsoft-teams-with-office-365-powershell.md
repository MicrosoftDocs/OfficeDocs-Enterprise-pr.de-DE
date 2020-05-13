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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="7181b-103">Verwalten von Microsoft Teams mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7181b-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="7181b-104">Sie können Microsoft Teams mit Office 365 PowerShell verwalten.</span><span class="sxs-lookup"><span data-stu-id="7181b-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="7181b-105">Installieren Sie zunächst das [Microsoft Teams-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="7181b-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="7181b-106">Melden Sie sich mit einem Benutzernamen und einem Kennwort an.</span><span class="sxs-lookup"><span data-stu-id="7181b-106">Sign in with a user name and password</span></span>

<span data-ttu-id="7181b-107">Für die Office 365-Welt (+ gcc)-Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="7181b-108">Für die Office 365 US Governmental DoD Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="7181b-109">Für die Office 365 US-Regierung gcc High Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="7181b-110">Anmelden mit mehrstufiger Authentifizierung (MFA)</span><span class="sxs-lookup"><span data-stu-id="7181b-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="7181b-111">Für die Office 365-Welt (+ gcc)-Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="7181b-112">Für die Office 365 US Governmental DoD Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="7181b-113">Für die Office 365 US-Regierung gcc High Cloud:</span><span class="sxs-lookup"><span data-stu-id="7181b-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="7181b-114">Trennen der Verbindung mit Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7181b-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="7181b-115">Verwenden Sie dazu diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="7181b-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="7181b-116">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="7181b-116">See also</span></span>

[<span data-ttu-id="7181b-117">Übersicht über Microsoft Teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="7181b-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="7181b-118">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7181b-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7181b-119">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7181b-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

