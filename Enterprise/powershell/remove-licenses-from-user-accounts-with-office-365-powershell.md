---
title: Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
description: Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651219"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="1c84f-103">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="1c84f-104">**Zusammenfassung:** Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="1c84f-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1c84f-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="1c84f-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1c84f-106">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="1c84f-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="1c84f-107">Im nächsten Schritt die Lizenz Pläne für Ihre Mandanten mit diesem Befehl aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="1c84f-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="1c84f-108">Rufen Sie im nächsten Schritt der Anmeldename des Kontos für die Sie eine Lizenz, auch bekannt als den Benutzerprinzipalnamen (UPN) entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="1c84f-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="1c84f-109">Schließlich geben Sie die Anmeldung und Lizenz Plan Benutzernamen an, entfernen Sie die Zeichen "<" und ">" und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="1c84f-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1c84f-110">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1c84f-111">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1c84f-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="1c84f-112">Zum Anzeigen der Lizenzinformationen Plan (**AccountSkuID** ) in Ihrer Organisation finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="1c84f-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="1c84f-113">Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="1c84f-114">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="1c84f-115">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="1c84f-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="1c84f-116">Entfernen von Lizenzen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="1c84f-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="1c84f-117">Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="1c84f-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="1c84f-118">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` Lizenz aus dem Benutzerkonto BelindaN@litwareinc.com (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="1c84f-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="1c84f-119">Verwenden Sie eine der folgenden Methoden, um Lizenzen von einer Gruppe von vorhandenen lizenzierten Benutzern zu entfernen,:</span><span class="sxs-lookup"><span data-stu-id="1c84f-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="1c84f-120">**Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="1c84f-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="1c84f-121">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenzen von allen Konten für Benutzer in der Abteilung "Sales" in den USA.</span><span class="sxs-lookup"><span data-stu-id="1c84f-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="1c84f-122">**Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="1c84f-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="1c84f-123">Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="1c84f-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="1c84f-124">Verwenden Sie folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="1c84f-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="1c84f-125">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz von Benutzerkonten in der Textdatei C:\My Documents\Accounts.txt definiert.</span><span class="sxs-lookup"><span data-stu-id="1c84f-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="1c84f-126">Verwenden Sie die folgende Syntax, um Lizenzen von allen vorhandenen Benutzerkonten zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="1c84f-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="1c84f-127">Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz aus allen vorhandenen Benutzerkonten lizenziert.</span><span class="sxs-lookup"><span data-stu-id="1c84f-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="1c84f-p101">Löschen des Benutzerkontos ist eine weitere Möglichkeit, um eine Lizenz freizugeben. Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="1c84f-p101">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1c84f-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1c84f-130">See also</span></span>

[<span data-ttu-id="1c84f-131">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1c84f-132">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1c84f-133">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c84f-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="1c84f-134">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="1c84f-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

