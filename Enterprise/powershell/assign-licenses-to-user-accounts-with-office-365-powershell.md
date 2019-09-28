---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: Admin
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
description: Vorgehensweise verwenden Office 365 PowerShell, um nicht lizenzierten Benutzern eine Office 365 Lizenz zuzuweisen.
ms.openlocfilehash: e963b9a0f24ae5b573dfe9612d9d09419809defe
ms.sourcegitcommit: 6b4fca7ccdbb7aeadc705d82f1007ac285f27357
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "37282930"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="94d00-103">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94d00-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="94d00-104">**Zusammenfassung:**  Vorgehensweise verwenden Office 365 PowerShell, um nicht lizenzierten Benutzern eine Office 365 Lizenz zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="94d00-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="94d00-105">Benutzer können keine Office 365 Dienste verwenden, bis Ihrem Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="94d00-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="94d00-106">Sie können Office 365 PowerShell verwenden, um schnell Lizenzen für nicht lizenzierte Konten zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="94d00-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="94d00-107">Benutzerkonten muss ein Standort zugewiesen sein.</span><span class="sxs-lookup"><span data-stu-id="94d00-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="94d00-108">Sie können dies über die Eigenschaften eines Benutzerkontos im Microsoft 365 Admin Center oder über PowerShell tun.</span><span class="sxs-lookup"><span data-stu-id="94d00-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="94d00-109">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="94d00-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="94d00-110">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="94d00-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="94d00-111">Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="94d00-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="94d00-112">Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz hinzufügen möchten, die auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="94d00-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="94d00-113">Stellen Sie als nächstes sicher, dass dem Benutzerkonto ein Verwendungs Speicherort zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="94d00-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="94d00-114">Wenn kein Verwendungs Speicherort zugewiesen ist, können Sie einen mit folgenden Befehlen zuweisen:</span><span class="sxs-lookup"><span data-stu-id="94d00-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="94d00-115">Geben Sie schließlich den Benutzeranmeldenamen und den Namen des Lizenz Plans an, und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="94d00-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="94d00-116">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94d00-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="94d00-117">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="94d00-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="94d00-118">Führen Sie den Befehl **Get-MsolAccountSku** aus, um die verfügbaren Lizenzierungs Pläne und die Anzahl der verfügbaren Lizenzen in jedem Plan in Ihrer Organisation anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="94d00-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="94d00-119">Die Anzahl der verfügbaren Lizenzen in jedem Plan lautet **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="94d00-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="94d00-120">Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="94d00-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="94d00-121">Führen Sie diesen Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.</span><span class="sxs-lookup"><span data-stu-id="94d00-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="94d00-122">Sie können nur Benutzerkonten Lizenzen zuweisen, für die die **UsageLocation** -Eigenschaft auf einen gültigen ISO 3166-1-Alpha-2-Ländercode festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="94d00-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="94d00-123">„US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich.</span><span class="sxs-lookup"><span data-stu-id="94d00-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="94d00-124">Einige Office 365 Dienste stehen in bestimmten Ländern nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="94d00-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="94d00-125">Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="94d00-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="94d00-126">Führen Sie diesen Befehl aus, um Konten zu finden, die keinen **UsageLocation** -Wert haben.</span><span class="sxs-lookup"><span data-stu-id="94d00-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="94d00-127">Um den **UsageLocation** -Wert für ein Konto festzulegen, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="94d00-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="94d00-128">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="94d00-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="94d00-129">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="94d00-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="94d00-130">Zuweisen von Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="94d00-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="94d00-131">Verwenden Sie den folgenden Befehl in Office 365 PowerShell, um einem Benutzer eine Lizenz zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="94d00-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="94d00-132">In diesem Beispiel wird dem nicht lizenzierten Benutzer **belindan\@litwareinc.com**eine Lizenz vom **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenzierungs Plan zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="94d00-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="94d00-133">Um vielen nicht lizenzierten Benutzern eine Lizenz zuzuweisen, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="94d00-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="94d00-134">Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.</span><span class="sxs-lookup"><span data-stu-id="94d00-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="94d00-135">Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.</span><span class="sxs-lookup"><span data-stu-id="94d00-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="94d00-136">In diesem Beispiel werden Lizenzen aus dem Lizenzierungs Plan **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) allen nicht lizenzierten Benutzern zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="94d00-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="94d00-137">In diesem Beispiel werden die gleichen Lizenzen nicht lizenzierten Benutzern in der Vertriebsabteilung in den Vereinigten Staaten zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="94d00-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="94d00-138">Migrieren eines Benutzers in ein anderes Abonnement (Lizenzplan) mit dem Azure Active Directory PowerShell für Graph-Modul</span><span class="sxs-lookup"><span data-stu-id="94d00-138">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="94d00-139">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="94d00-139">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="94d00-140">Rufen Sie als nächstes den Anmeldenamen des Benutzerkontos ab, für das Sie Switch-Abonnements verwenden möchten, auch bekannt als Benutzerprinzipalname (User Principal Name, UPN).</span><span class="sxs-lookup"><span data-stu-id="94d00-140">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="94d00-141">Als nächstes Listen Sie die Abonnements (Lizenz Pläne) für Ihren Mandanten mit diesem Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="94d00-141">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="94d00-142">Als nächstes Listen Sie die Abonnements auf, die das Benutzerkonto derzeit mit diesen Befehlen aufweist.</span><span class="sxs-lookup"><span data-stu-id="94d00-142">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="94d00-143">Identifizieren Sie das Abonnement, das der Benutzer aktuell hat (das von-Abonnement) und das Abonnement, auf das der Benutzer umzieht (das Abonnement).</span><span class="sxs-lookup"><span data-stu-id="94d00-143">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="94d00-144">Geben Sie schließlich die an-und von-Abonnement Namen (SKU-Teilenummern) an, und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="94d00-144">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="94d00-145">Sie können die Änderung des Abonnements für das Benutzerkonto mit den folgenden Befehlen überprüfen.</span><span class="sxs-lookup"><span data-stu-id="94d00-145">You can verify the change in subscription for the user account with these commands.</span></span>

```
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a><span data-ttu-id="94d00-146">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="94d00-146">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="94d00-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="94d00-147">See also</span></span>

[<span data-ttu-id="94d00-148">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94d00-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="94d00-149">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94d00-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="94d00-150">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94d00-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
