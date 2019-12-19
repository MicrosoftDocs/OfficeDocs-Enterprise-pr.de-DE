---
title: Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/18/2019
audience: Admin
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
ms.openlocfilehash: 832e073ad5443181f1c72af591cc99e3702d6b84
ms.sourcegitcommit: de4240ae8026e3e9a433c7ae23c938dc5b514ace
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2019
ms.locfileid: "40738267"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="8ec71-103">Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ec71-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="8ec71-p101">Benutzerkonten in Ihrer Office 365-Organisation sind möglicherweise einige, alle oder keine der verfügbaren Lizenzen aus den Lizenzierungsplänen zugewiesen, die in Ihrer Organisation verfügbar sind. Mit Office 365 PowerShell können Sie lizenzierte und nicht lizenzierte Benutzer in Ihrer Organisation schnell finden.</span><span class="sxs-lookup"><span data-stu-id="8ec71-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8ec71-106">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="8ec71-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8ec71-107">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8ec71-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="8ec71-108">Führen Sie den folgenden Befehl aus, um die Liste aller Benutzerkonten in Ihrer Organisation anzuzeigen, denen keine Ihrer Lizenzierungs Pläne zugewiesen wurden (nicht lizenzierte Benutzer):</span><span class="sxs-lookup"><span data-stu-id="8ec71-108">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="8ec71-109">Führen Sie den folgenden Befehl aus, um die Liste aller Benutzerkonten in Ihrer Organisation anzuzeigen, denen Ihre Lizenzierungs Pläne zugewiesen wurden (lizenzierte Benutzer):</span><span class="sxs-lookup"><span data-stu-id="8ec71-109">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="8ec71-110">Wenn Sie alle Benutzer in Ihrem Abonnement auflisten möchten, `Get-AzureAdUser -All $true` verwenden Sie den Befehl.</span><span class="sxs-lookup"><span data-stu-id="8ec71-110">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8ec71-111">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ec71-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8ec71-112">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8ec71-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="8ec71-113">Führen Sie den folgenden Befehl in Office 365 PowerShell aus, um die Liste aller Benutzerkonten mit ihrem Lizenzierungsstatus in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="8ec71-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="8ec71-114">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="8ec71-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8ec71-115">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="8ec71-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="8ec71-116">Führen Sie den folgenden Befehl aus, um die Liste aller nicht lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="8ec71-116">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="8ec71-117">Führen Sie den folgenden Befehl aus, um die Liste aller lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="8ec71-117">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="8ec71-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8ec71-118">See also</span></span>

[<span data-ttu-id="8ec71-119">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ec71-119">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8ec71-120">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ec71-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8ec71-121">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ec71-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
