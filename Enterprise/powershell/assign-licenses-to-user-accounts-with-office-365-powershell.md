---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123292"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="83868-103">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="83868-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="83868-104">**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.</span><span class="sxs-lookup"><span data-stu-id="83868-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="83868-p101">Lizenzieren von Benutzerkonten in Office 365 ist wichtig, da Benutzer keine Office 365-Dienste verwendet werden, bis ihr Konto lizenziert wurden. Office 365 PowerShell können Sie nicht lizenzierten Konten, insbesondere mehrere Konten effizient Lizenzen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="83868-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="83868-107">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="83868-107">Before you begin</span></span>
<span data-ttu-id="83868-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="83868-108"></span></span>

- <span data-ttu-id="83868-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="83868-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="83868-p103">Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="83868-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="83868-114">Führen Sie den Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen,`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="83868-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="83868-p104">Sie können nur für Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="83868-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="83868-p105">Führen Sie den Befehl aus, um Konten suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen, `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Um den **usagelocation-Wert angegeben** Wert für ein Konto festzulegen, verwenden Sie die Syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Beispielsweise `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="83868-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="83868-122">Wenn Sie das Cmdlet **Get-MsolUser** ohne Verwenden der `-All` -Parameter, die nur die ersten 500 Benutzerkonten zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="83868-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="83868-123">Zuweisen von Lizenzen zu Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="83868-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="83868-124">Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax in Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83868-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="83868-125">In diesem Beispiel wird eine Lizenz aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für den nicht lizenzierten Benutzer `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="83868-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="83868-126">Wenn Sie mehreren nicht lizenzierten Benutzern eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="83868-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="83868-127">**Hinweise**</span><span class="sxs-lookup"><span data-stu-id="83868-127">**Notes**</span></span>
  
- <span data-ttu-id="83868-128">Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.</span><span class="sxs-lookup"><span data-stu-id="83868-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="83868-129">Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.</span><span class="sxs-lookup"><span data-stu-id="83868-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="83868-130">In diesem Beispiel wird die Lizenzen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für alle nicht lizenzierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="83868-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="83868-131">In diesem Beispiel werden dieselben Lizenzen den nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="83868-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="83868-132">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="83868-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="83868-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="83868-133">See also</span></span>
<span data-ttu-id="83868-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="83868-134"></span></span>

<span data-ttu-id="83868-135">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="83868-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="83868-136">Erstellen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="83868-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="83868-137">Löschen und Wiederherstellen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="83868-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="83868-138">Blockieren von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="83868-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="83868-139">Entfernen von Lizenzen von Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="83868-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="83868-140">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="83868-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="83868-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="83868-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="83868-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="83868-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="83868-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="83868-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="83868-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="83868-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="83868-145">Select-Object</span><span class="sxs-lookup"><span data-stu-id="83868-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="83868-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="83868-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

