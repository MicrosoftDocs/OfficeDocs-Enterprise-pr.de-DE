---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert die Verwendung von Office 365 PowerShell zum Bestimmen der Office 365-Dienste, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 113107df75880a21210991d5b301245d75c5c739
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052969"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="b332a-103">Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b332a-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="b332a-104">**Zusammenfassung:** Erläutert die Verwendung von Office 365 PowerShell zum Bestimmen der Office 365-Dienste, die Benutzern zugewiesen wurden.</span><span class="sxs-lookup"><span data-stu-id="b332a-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="b332a-p101">In Office 365 erteilen Lizenzen aus Lizenzierungs Plänen (auch als SKUs oder Office 365-Pläne bezeichnet) Benutzern den Zugriff auf die Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer verfügt jedoch möglicherweise nicht über Zugriff auf alle Dienste, die in einer Lizenz zur Verfügung stehen, die Ihnen derzeit zugewiesen ist. Sie können Office 365 PowerShell verwenden, um den Status von Diensten in Benutzerkonten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b332a-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="b332a-108">Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b332a-108">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="b332a-109">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="b332a-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="b332a-110">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="b332a-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="b332a-111">Führen Sie als nächstes die Lizenz Pläne für Ihren Mandanten mit diesem Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="b332a-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="b332a-112">Verwenden Sie diese Befehle, um die in den einzelnen Lizenzierungs Plänen verfügbaren Dienste aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="b332a-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

<span data-ttu-id="b332a-113">Verwenden Sie diese Befehle, um die Lizenzen aufzulisten, die einem Benutzerkonto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="b332a-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="b332a-114">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b332a-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="b332a-115">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b332a-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="b332a-116">Führen Sie als nächstes den folgenden Befehl aus, um die in Ihrer Organisation verfügbaren Lizenzierungs Pläne aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="b332a-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```
Get-MsolAccountSku
```

<span data-ttu-id="b332a-117">Führen Sie dann diesen Befehl aus, um die Dienste aufzulisten, die in jedem Lizenzierungs Plan verfügbar sind, und die Reihenfolge, in der Sie aufgeführt werden (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="b332a-117">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
<span data-ttu-id="b332a-118">Verwenden Sie diesen Befehl, um die Lizenzen aufzulisten, die einem Benutzer zugewiesen sind, und die Reihenfolge, in der Sie aufgelistet werden (die Indexnummer).</span><span class="sxs-lookup"><span data-stu-id="b332a-118">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
><span data-ttu-id="b332a-119">Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b332a-119">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="b332a-120">So zeigen Sie Dienste für ein Benutzerkonto an</span><span class="sxs-lookup"><span data-stu-id="b332a-120">To view services for a user account</span></span>

<span data-ttu-id="b332a-121">Verwenden Sie die folgende Syntax, um alle Office 365-Dienste anzuzeigen, auf die ein Benutzer Zugriff hat:</span><span class="sxs-lookup"><span data-stu-id="b332a-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="b332a-p102">In diesem Beispiel werden die Dienste angezeigt, auf die der Benutzer BelindaN@litwareinc.com Zugriff hat. Dadurch werden die Dienste angezeigt, die allen Lizenzen zugeordnet sind, die Ihrem Konto zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="b332a-p102">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="b332a-124">Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="b332a-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="b332a-125">Verwenden Sie die folgende Syntax, um alle Dienste für einen Benutzer anzuzeigen, dem *mehrere Lizenzen*zugewiesen wurden:</span><span class="sxs-lookup"><span data-stu-id="b332a-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
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

  
## <a name="new-to-office-365"></a><span data-ttu-id="b332a-126">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="b332a-126">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="b332a-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b332a-127">See also</span></span>

[<span data-ttu-id="b332a-128">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b332a-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b332a-129">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b332a-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b332a-130">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b332a-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
