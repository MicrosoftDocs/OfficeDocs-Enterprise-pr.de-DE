---
title: Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/07/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Erläutert die Verwendung von Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die zuvor Benutzern zugewiesen wurden.
ms.openlocfilehash: 66ffe7275bcfd936c7df70d3969b96fefafb355d
ms.sourcegitcommit: 0a99abcb67fc8ee7594cb66f5f7fd0e6e94eb3fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "30474176"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="21e25-103">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="21e25-104">**Zusammenfassung:** Erläutert die Verwendung von Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die zuvor Benutzern zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="21e25-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="21e25-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="21e25-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="21e25-106">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="21e25-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="21e25-107">Führen Sie als nächstes die Lizenz Pläne für Ihren Mandanten mit diesem Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="21e25-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="21e25-108">Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz entfernen möchten, auch bekannt als Benutzerprinzipalname (UPN).</span><span class="sxs-lookup"><span data-stu-id="21e25-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="21e25-109">Geben Sie schließlich die Benutzeranmelde-und Lizenzplan Namen an, entfernen Sie die Zeichen "<" und ">", und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="21e25-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="21e25-110">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="21e25-111">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="21e25-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="21e25-112">Informationen zu den Lizenzierungs Plan (**AccountSkuID** ) in Ihrer Organisation finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="21e25-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="21e25-113">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="21e25-114">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="21e25-115">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="21e25-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="21e25-116">Entfernen von Lizenzen aus Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="21e25-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="21e25-117">Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="21e25-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="21e25-118">In diesem Beispiel wird `litwareinc:ENTERPRISEPACK` die (Office 365 Enterprise E3)-Lizenz aus dem benutzerkonto BelindaN@litwareinc.com entfernt.</span><span class="sxs-lookup"><span data-stu-id="21e25-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="21e25-119">Verwenden Sie eine der folgenden Methoden, um Lizenzen von einer Gruppe von vorhandenen lizenzierten Benutzern zu entfernen,:</span><span class="sxs-lookup"><span data-stu-id="21e25-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="21e25-120">**Filtern der Konten basierend auf einem vorhandenen Kontoattribut** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="21e25-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="21e25-121">In diesem Beispiel werden `litwareinc:ENTERPRISEPACK` die (Office 365 Enterprise E3)-Lizenzen aus allen Konten für Benutzer in der Vertriebsabteilung in den USA entfernt.</span><span class="sxs-lookup"><span data-stu-id="21e25-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="21e25-122">**Verwenden einer Liste bestimmter Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="21e25-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="21e25-123">Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="21e25-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="21e25-124">Verwenden Sie folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="21e25-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="21e25-125">In diesem Beispiel wird `litwareinc:ENTERPRISEPACK` die (Office 365 Enterprise E3)-Lizenz aus den in der Textdatei C:\My documents\accounts.txt</span><span class="sxs-lookup"><span data-stu-id="21e25-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="21e25-126">Verwenden Sie die folgende Syntax, um Lizenzen von allen vorhandenen Benutzerkonten zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="21e25-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="21e25-127">In diesem Beispiel wird `litwareinc:ENTERPRISEPACK` die (Office 365 Enterprise E3)-Lizenz aus allen vorhandenen lizenzierten Benutzerkonten entfernt.</span><span class="sxs-lookup"><span data-stu-id="21e25-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="21e25-128">Eine andere Möglichkeit zum Freigeben einer Lizenz besteht im Löschen des Benutzerkontos.</span><span class="sxs-lookup"><span data-stu-id="21e25-128">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="21e25-129">Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="21e25-129">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="21e25-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="21e25-130">See also</span></span>

[<span data-ttu-id="21e25-131">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="21e25-132">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="21e25-133">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e25-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="21e25-134">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="21e25-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

