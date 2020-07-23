---
title: Entfernen von Microsoft 365-Lizenzen aus Benutzerkonten mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Erläutert die Verwendung von PowerShell zum Entfernen von Microsoft 365-Lizenzen, die zuvor Benutzern zugewiesen wurden.
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230391"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a><span data-ttu-id="71616-103">Entfernen von Microsoft 365-Lizenzen aus Benutzerkonten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-103">Remove Microsoft 365 licenses from user accounts with PowerShell</span></span>

<span data-ttu-id="71616-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="71616-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="71616-105">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="71616-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="71616-106">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="71616-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="71616-107">Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="71616-107">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="71616-108">Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz entfernen möchten, auch bekannt als Benutzerprinzipalname (User Principal Name, UPN).</span><span class="sxs-lookup"><span data-stu-id="71616-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="71616-109">Geben Sie schließlich die Benutzeranmelde-und Lizenzplan Namen an, entfernen Sie die Zeichen "<" und ">", und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="71616-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="71616-110">Wenn Sie alle Lizenzen für ein bestimmtes Benutzerkonto entfernen möchten, geben Sie den Anmeldenamen des Benutzers an, entfernen Sie die Zeichen "<" und ">", und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="71616-110">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="71616-111">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="71616-112">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="71616-112">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="71616-113">Informationen zum Lizenzierungsplan (**AccountSkuID**) in Ihrer Organisation finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="71616-113">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="71616-114">Anzeigen von Lizenzen und Diensten mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-114">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="71616-115">Anzeigen von Konto Lizenz-und Dienstdetails mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-115">View account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="71616-116">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="71616-116">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="71616-117">Entfernen von Lizenzen aus Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="71616-117">Removing licenses from user accounts</span></span>

<span data-ttu-id="71616-118">Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="71616-118">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="71616-119">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="71616-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="71616-120">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="71616-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="71616-121">In diesem Beispiel wird die **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenz aus dem Benutzerkonto BelindaN@litwareinc.com entfernt.</span><span class="sxs-lookup"><span data-stu-id="71616-121">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="71616-122">Sie können das Cmdlet nicht verwenden `Set-MsolUserLicense` , um die Zuweisung von Benutzern von *abgebrochenen* Lizenzen aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="71616-122">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="71616-123">Sie müssen dies für jedes Benutzerkonto im Microsoft 365 Admin Center einzeln durchführen.</span><span class="sxs-lookup"><span data-stu-id="71616-123">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="71616-124">Wenn Sie alle Lizenzen aus einer Gruppe vorhandener lizenzierter Benutzer entfernen möchten, verwenden Sie eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="71616-124">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="71616-125">**Filtern der Konten basierend auf einem vorhandenen Kontoattribut** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="71616-125">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="71616-126">In diesem Beispiel werden alle Lizenzen aus allen Benutzerkonten in der Vertriebsabteilung in den Vereinigten Staaten entfernt.</span><span class="sxs-lookup"><span data-stu-id="71616-126">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="71616-127">**Verwenden einer Liste bestimmter Konten für eine bestimmte Lizenz** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="71616-127">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="71616-128">Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="71616-128">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="71616-129">Verwenden Sie folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="71616-129">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="71616-130">In diesem Beispiel wird die **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenz aus den in der Textdatei C:\My Documents\Accounts.txt definierten Benutzerkonten entfernt.</span><span class="sxs-lookup"><span data-stu-id="71616-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="71616-131">Verwenden Sie die folgende Syntax, um alle Lizenzen aus allen vorhandenen Benutzerkonten zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="71616-131">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="71616-132">Eine andere Möglichkeit zum Freigeben einer Lizenz besteht im Löschen des Benutzerkontos.</span><span class="sxs-lookup"><span data-stu-id="71616-132">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="71616-133">Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="71616-133">For more information, see [Delete and restore user accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="71616-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="71616-134">See also</span></span>

[<span data-ttu-id="71616-135">Verwalten von Microsoft 365-Benutzerkonten,-Lizenzen und-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-135">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="71616-136">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="71616-136">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="71616-137">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="71616-137">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

