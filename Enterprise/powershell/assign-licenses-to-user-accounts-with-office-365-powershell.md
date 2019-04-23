---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Erläutert die Verwendung von Office 365 PowerShell Zuweisen einer Office 365-Lizenz zu nicht lizenzierten Benutzern.
ms.openlocfilehash: ac2cdb8c303cacc5c9664b877ba86a5b196432b1
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957646"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0b71d-103">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b71d-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="0b71d-104">**Zusammenfassung:**  Erläutert die Verwendung von Office 365 PowerShell Zuweisen einer Office 365-Lizenz zu nicht lizenzierten Benutzern.</span><span class="sxs-lookup"><span data-stu-id="0b71d-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="0b71d-105">Benutzer können keine Office 365-Dienste verwenden, bis Ihr Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="0b71d-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="0b71d-106">Sie können Office 365 PowerShell verwenden, um Lizenzen für nicht lizenzierte Konten schnell zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="0b71d-107">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="0b71d-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="0b71d-108">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="0b71d-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="0b71d-109">Führen Sie als nächstes die Lizenz Pläne für Ihren Mandanten mit diesem Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="0b71d-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="0b71d-110">Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz hinzufügen möchten, auch bekannt als Benutzerprinzipalname (UPN).</span><span class="sxs-lookup"><span data-stu-id="0b71d-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="0b71d-111">Geben Sie schließlich den Benutzernamen und den Lizenzplan Namen an, und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="0b71d-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="0b71d-112">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b71d-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="0b71d-113">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0b71d-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="0b71d-114">Führen Sie den Befehl **Get-MsolAccountSku** aus, um die verfügbaren Lizenzierungs Pläne und die Anzahl der verfügbaren Lizenzen in jedem Plan in Ihrer Organisation anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-114">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="0b71d-115">Die Anzahl der verfügbaren Lizenzen in jedem Plan ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="0b71d-115">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="0b71d-116">Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0b71d-116">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="0b71d-117">Führen Sie diesen Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="0b71d-118">Sie können nur Lizenzen zu Benutzerkonten zuweisen, für die die **UsageLocation** -Eigenschaft auf eine gültige ISO 3166-1-Alpha-2-Landeskennzahl festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="0b71d-118">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="0b71d-119">„US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich.</span><span class="sxs-lookup"><span data-stu-id="0b71d-119">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="0b71d-120">Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0b71d-120">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="0b71d-121">Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="0b71d-121">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="0b71d-122">Führen Sie diesen Befehl aus, um Konten zu suchen, die keinen **UsageLocation** -Wert besitzen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="0b71d-123">Führen Sie den folgenden Befehl aus, um den **UsageLocation** -Wert für ein Konto festzulegen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="0b71d-124">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0b71d-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="0b71d-125">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0b71d-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="0b71d-126">Zuweisen von Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="0b71d-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="0b71d-127">Verwenden Sie den folgenden Befehl in Office 365 PowerShell, um einem Benutzer eine Lizenz zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="0b71d-128">In diesem Beispiel wird dem nicht lizenzierten Benutzer **belindan@litwareinc.com**eine Lizenz aus dem **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenzplan zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0b71d-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="0b71d-129">Führen Sie diesen Befehl aus, um vielen nicht lizenzierten Benutzern eine Lizenz zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="0b71d-130">Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.</span><span class="sxs-lookup"><span data-stu-id="0b71d-130">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="0b71d-131">Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.</span><span class="sxs-lookup"><span data-stu-id="0b71d-131">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="0b71d-132">In diesem Beispiel werden allen nicht lizenzierten Benutzern Lizenzen aus dem **litwareinc: ENTERPRISEPACK** -Lizenzierungs Plan (Office 365 Enterprise E3) zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0b71d-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="0b71d-133">In diesem Beispiel werden die gleichen Lizenzen nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0b71d-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="0b71d-134">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="0b71d-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="0b71d-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0b71d-135">See also</span></span>

[<span data-ttu-id="0b71d-136">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b71d-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0b71d-137">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b71d-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0b71d-138">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b71d-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
