---
title: Anzeigen von Microsoft 365-Konto Lizenz-und-Dienstdetails mit PowerShell
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert die Verwendung von PowerShell zum Bestimmen der Microsoft 365-Dienste, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 73af2fd40df8b36507250edcef48359e9d555a7f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230241"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a><span data-ttu-id="e67be-103">Anzeigen von Microsoft 365-Konto Lizenz-und-Dienstdetails mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="e67be-103">View Microsoft 365 account license and service details with PowerShell</span></span>

<span data-ttu-id="e67be-104">*Dieser Artikel bezieht sich sowohl auf Microsoft 365 Enterprise als auch auf Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="e67be-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e67be-105">In Microsoft 365 ermöglichen Lizenzen aus Lizenzierungs Plänen (auch SKU-oder Microsoft 365-Pläne genannt) Benutzern den Zugriff auf die Microsoft 365-Dienste, die für diese Pläne definiert sind.</span><span class="sxs-lookup"><span data-stu-id="e67be-105">In Microsoft 365, licenses from licensing plans (also called SKUs or Microsoft 365 plans) give users access to the Microsoft 365 services that are defined for those plans.</span></span> <span data-ttu-id="e67be-106">Ein Benutzer hat möglicherweise aber keinen Zugriff auf alle Dienste, die in einer Lizenz verfügbar sind, die ihm derzeit zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="e67be-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="e67be-107">Sie können PowerShell für Microsoft 365 verwenden, um den Status von Diensten in Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e67be-107">You can use PowerShell for Microsoft 365 to view the status of services on user accounts.</span></span> 

<span data-ttu-id="e67be-108">Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e67be-108">For more information about licensing plans, license, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e67be-109">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="e67be-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e67be-110">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e67be-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="e67be-111">Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="e67be-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="e67be-112">Verwenden Sie diese Befehle, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e67be-112">Use these commands to list the services that are available in each licensing plan.</span></span>

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

<span data-ttu-id="e67be-113">Verwenden Sie diese Befehle, um die Lizenzen aufzulisten, die einem Benutzerkonto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="e67be-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e67be-114">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e67be-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e67be-115">Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e67be-115">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="e67be-116">Führen Sie als nächstes den folgenden Befehl aus, um die in Ihrer Organisation verfügbaren Lizenzierungs Pläne aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="e67be-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="e67be-117">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="e67be-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e67be-118">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="e67be-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e67be-119">Führen Sie als nächstes den folgenden Befehl aus, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen verfügbar sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="e67be-119">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="e67be-120">Verwenden Sie diesen Befehl, um die Lizenzen aufzulisten, die einem Benutzer zugewiesen sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="e67be-120">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="e67be-121">So zeigen Sie Dienste für ein Benutzerkonto an</span><span class="sxs-lookup"><span data-stu-id="e67be-121">To view services for a user account</span></span>

<span data-ttu-id="e67be-122">Verwenden Sie die folgende Syntax, um alle Microsoft 365-Dienste anzuzeigen, auf die ein Benutzer Zugriff hat:</span><span class="sxs-lookup"><span data-stu-id="e67be-122">To view all the Microsoft 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="e67be-123">Dieses Beispiel zeigt die Dienste, auf die der Benutzer BelindaN@litwareinc.com Zugriff hat.</span><span class="sxs-lookup"><span data-stu-id="e67be-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="e67be-124">Es zeigt die Dienste, die allen Lizenzen zugeordnet sind, die dem Konto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="e67be-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="e67be-125">Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="e67be-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="e67be-126">Verwenden Sie die folgende Syntax, um alle Dienste für einen Benutzer anzuzeigen, dem *mehrere Lizenzen*zugewiesen wurden:</span><span class="sxs-lookup"><span data-stu-id="e67be-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="e67be-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e67be-127">See also</span></span>

[<span data-ttu-id="e67be-128">Verwalten von Microsoft 365-Benutzerkonten,-Lizenzen und-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="e67be-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e67be-129">Verwalten von Microsoft 365 mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="e67be-129">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e67be-130">Erste Schritte mit PowerShell für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e67be-130">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
