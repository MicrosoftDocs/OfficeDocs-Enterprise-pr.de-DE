---
title: Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten.
ms.openlocfilehash: 0648fae89a45b080bd48561bb079184f0e97dd36
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546506"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="3b450-103">Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b450-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="3b450-104">**Zusammenfassung:** Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="3b450-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="3b450-p101">Benutzerkonten in Ihrer Office 365-Organisation sind möglicherweise einige, alle oder keine der verfügbaren Lizenzen aus den Lizenzierungsplänen zugewiesen, die in Ihrer Organisation verfügbar sind. Mit Office 365 PowerShell können Sie lizenzierte und nicht lizenzierte Benutzer in Ihrer Organisation schnell finden.</span><span class="sxs-lookup"><span data-stu-id="3b450-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3b450-107">Verwenden von Azure Active Directory PowerShell Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="3b450-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3b450-108">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="3b450-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="3b450-109">Um die Liste aller Benutzerkonten in Ihrer Organisation, die nicht keines der Lizenzierung Pläne (nicht lizenzierten Benutzer) zugewiesen wurden, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="3b450-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="3b450-110">Um die Liste aller Benutzerkonten in Ihrer Organisation, die wurden zugewiesen keines der Lizenzierung Pläne (lizenzierten Benutzern) den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="3b450-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3b450-111">Verwenden Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b450-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3b450-112">Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3b450-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="3b450-113">Führen Sie den folgenden Befehl in Office 365 PowerShell aus, um die Liste aller Benutzerkonten mit ihrem Lizenzierungsstatus in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="3b450-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="3b450-114">Führen Sie den folgenden Befehl aus, um die Liste aller nicht lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="3b450-114">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="3b450-115">Führen Sie den folgenden Befehl aus, um die Liste aller lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="3b450-115">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="3b450-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3b450-116">See also</span></span>

[<span data-ttu-id="3b450-117">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b450-117">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3b450-118">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b450-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3b450-119">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b450-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
