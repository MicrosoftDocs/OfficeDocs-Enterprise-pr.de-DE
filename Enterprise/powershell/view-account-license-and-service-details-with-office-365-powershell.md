---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert die Verwendung Office 365 PowerShell zum Bestimmen der Office 365 Dienste, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 08e44476ea746b7e8298355e3adc5d0401261acd
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072287"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="7dd98-103">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd98-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="7dd98-104">In Office 365 erteilen Lizenzen aus Lizenzierungs Plänen (auch SKU-oder Office 365-Pläne genannt) Benutzern den Zugriff auf die Office 365 Dienste, die für diese Pläne definiert sind.</span><span class="sxs-lookup"><span data-stu-id="7dd98-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="7dd98-105">Ein Benutzer hat möglicherweise aber keinen Zugriff auf alle Dienste, die in einer Lizenz verfügbar sind, die ihm derzeit zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="7dd98-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="7dd98-106">Sie können Office 365 PowerShell verwenden, um den Status von Diensten in Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7dd98-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="7dd98-107">Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7dd98-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7dd98-108">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="7dd98-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7dd98-109">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="7dd98-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="7dd98-110">Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="7dd98-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="7dd98-111">Verwenden Sie diese Befehle, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="7dd98-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="7dd98-112">Verwenden Sie diese Befehle, um die Lizenzen aufzulisten, die einem Benutzerkonto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="7dd98-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7dd98-113">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd98-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7dd98-114">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7dd98-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7dd98-115">Führen Sie als nächstes den folgenden Befehl aus, um die in Ihrer Organisation verfügbaren Lizenzierungs Pläne aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="7dd98-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="7dd98-116">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="7dd98-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7dd98-117">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="7dd98-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="7dd98-118">Führen Sie als nächstes den folgenden Befehl aus, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen verfügbar sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="7dd98-118">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
<span data-ttu-id="7dd98-119">Verwenden Sie diesen Befehl, um die Lizenzen aufzulisten, die einem Benutzer zugewiesen sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="7dd98-119">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
><span data-ttu-id="7dd98-120">Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7dd98-120">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="7dd98-121">So zeigen Sie Dienste für ein Benutzerkonto an</span><span class="sxs-lookup"><span data-stu-id="7dd98-121">To view services for a user account</span></span>

<span data-ttu-id="7dd98-122">Verwenden Sie die folgende Syntax, um alle Office 365 Dienste anzuzeigen, auf die ein Benutzer Zugriff hat:</span><span class="sxs-lookup"><span data-stu-id="7dd98-122">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="7dd98-123">Dieses Beispiel zeigt die Dienste, auf die der Benutzer BelindaN@litwareinc.com Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="7dd98-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="7dd98-124">Es zeigt die Dienste, die allen Lizenzen zugeordnet sind, die dem Konto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="7dd98-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="7dd98-125">Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="7dd98-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="7dd98-126">Verwenden Sie die folgende Syntax, um alle Dienste für einen Benutzer anzuzeigen, dem *mehrere Lizenzen*zugewiesen wurden:</span><span class="sxs-lookup"><span data-stu-id="7dd98-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="7dd98-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7dd98-127">See also</span></span>

[<span data-ttu-id="7dd98-128">Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd98-128">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="7dd98-129">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd98-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="7dd98-130">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd98-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
