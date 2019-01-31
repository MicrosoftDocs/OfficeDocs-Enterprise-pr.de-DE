---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651180"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="dded6-103">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dded6-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="dded6-104">**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.</span><span class="sxs-lookup"><span data-stu-id="dded6-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="dded6-p101">Benutzer können keine Dienste von Office 365 verwenden, bis ihr Konto eine Lizenz aus einer Lizenzierungsplan zugewiesen wurde. Office 365 PowerShell können Sie schnell Lizenzen nicht lizenzierten Konten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="dded6-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dded6-107">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="dded6-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dded6-108">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="dded6-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="dded6-109">Im nächsten Schritt die Lizenz Pläne für Ihre Mandanten mit diesem Befehl aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="dded6-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="dded6-110">Rufen Sie im nächsten Schritt der Anmeldename des Kontos ein, dem Sie eine Lizenz, auch bekannt als den Benutzerprinzipalnamen (UPN) hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="dded6-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="dded6-111">Schließlich geben Sie den Benutzernamen-Anmeldung und Plan Lizenznamen an, und führen Sie diese Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="dded6-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="dded6-112">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dded6-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="dded6-113">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dded6-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="dded6-p102">Führen Sie den Befehl **Get-MsolAccountSku** , um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="dded6-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="dded6-117">Führen Sie diesen Befehl, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.</span><span class="sxs-lookup"><span data-stu-id="dded6-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="dded6-p103">Sie können nur Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="dded6-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="dded6-122">Führen Sie diesen Befehl, um Konten zu suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen.</span><span class="sxs-lookup"><span data-stu-id="dded6-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="dded6-123">Um den **usagelocation-Wert angegeben** Wert auf ein Konto festlegen möchten, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="dded6-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="dded6-124">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="dded6-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="dded6-125">Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dded6-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="dded6-126">Zuweisen von Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="dded6-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="dded6-127">Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie den folgenden Befehl in Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dded6-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="dded6-128">In diesem Beispiel wird eine Lizenz aus der **litwareinc: enterprisepack** (Office 365 Enterprise E3) licensing Plan für die nicht lizenzierten Benutzer **belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="dded6-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="dded6-129">Wenn eine Lizenz für viele nicht lizenzierten Benutzer zuweisen möchten, führen Sie diesen Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="dded6-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="dded6-p104">Sie können nicht mehrere Lizenzen für einen Benutzer aus den gleichen Lizenzierungsplan zuweisen. Wenn Sie nicht über genügend verfügbaren Lizenzen verfügen, werden die Lizenzen für Benutzer in der Reihenfolge zugewiesen, die sie vom Cmdlet **Get-MsolUser** zurückgegeben werden, bis die verfügbaren Lizenzen Neige zur.</span><span class="sxs-lookup"><span data-stu-id="dded6-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="dded6-132">In diesem Beispiel wird allen nicht lizenzierten Benutzern Lizenzen aus den Lizenzierungsplan **litwareinc: enterprisepack** (Office 365 Enterprise E3) zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="dded6-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="dded6-133">In diesem Beispiel wird nicht lizenzierten Benutzer in der Abteilung "Sales" in den USA Lizenzen, die dieselben zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="dded6-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="dded6-134">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="dded6-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="dded6-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dded6-135">See also</span></span>

[<span data-ttu-id="dded6-136">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dded6-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dded6-137">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dded6-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dded6-138">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dded6-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
