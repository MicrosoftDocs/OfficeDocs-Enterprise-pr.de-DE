---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/04/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Verwenden Sie Office 365 PowerShell, um den Zugriff auf Office 365 Dienste für Benutzer zu deaktivieren.
ms.openlocfilehash: 83967e0b44099fb651edaa7f7cba9e811f9fdf81
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072197"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="7cdb0-103">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="7cdb0-104">Wenn einem Office 365-Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wird, werden dem Benutzer Office 365 Dienste aus dieser Lizenz zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="7cdb0-105">Sie können jedoch die Office 365 Dienste steuern, auf die der Benutzer zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="7cdb0-106">Beispielsweise können Sie den Zugriff darauf deaktivieren, auch wenn die Lizenz den Zugriff auf den SharePoint Online Dienst zulässt.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="7cdb0-107">Sie können PowerShell verwenden, um den Zugriff auf eine beliebige Anzahl von Diensten für einen bestimmten Lizenzierungs Plan für zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="7cdb0-108">ein einzelnes Konto</span><span class="sxs-lookup"><span data-stu-id="7cdb0-108">An individual account.</span></span>
- <span data-ttu-id="7cdb0-109">eine Gruppe von Konten</span><span class="sxs-lookup"><span data-stu-id="7cdb0-109">A group of accounts.</span></span>
- <span data-ttu-id="7cdb0-110">Alle Konten in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="7cdb0-111">Es gibt Office 365 Dienstabhängigkeiten, die verhindern können, dass Sie einen bestimmten Dienst deaktivieren, wenn andere Dienste davon abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7cdb0-112">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7cdb0-113">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="7cdb0-114">Verwenden Sie anschließend diesen Befehl, um die verfügbaren Lizenzierungs Pläne anzuzeigen, die auch als AccountSkuIds bezeichnet werden:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="7cdb0-115">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7cdb0-116">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="7cdb0-117">Weitere Informationen finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="7cdb0-118">Informationen zu den vor-und nach Ergebnissen der Verfahren in diesem Thema finden Sie unter [View Account License and Servicedetails with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="7cdb0-p103">Ein PowerShell-Skript steht zur Verfügung, das die in diesem Thema erläuterten Verfahren automatisiert. Insbesondere ermöglicht das Skript Ihnen das Anzeigen und Deaktivieren von Diensten in Ihrer Office 365-Organisation, einschließlich Sway. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-p103">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="7cdb0-122">Deaktivieren bestimmter Office 365 Dienste für bestimmte Benutzer für einen bestimmten Lizenzierungs Plan</span><span class="sxs-lookup"><span data-stu-id="7cdb0-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="7cdb0-123">Führen Sie die folgenden Schritte aus, um eine bestimmte Gruppe von Office 365 Diensten für Benutzer für einen bestimmten Lizenzierungs Plan zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="7cdb0-124">Schritt 1: Identifizieren der unerwünschten Dienste im Lizenzierungs Plan mithilfe der folgenden Syntax:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="7cdb0-125">Im folgenden Beispiel wird ein **licenseoptions** -Objekt erstellt, das die Office-und SharePoint Online-Dienste im Lizenzierungs Plan `litwareinc:ENTERPRISEPACK` mit dem Namen (Office 365 Enterprise E3) deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="7cdb0-126">Schritt 2: Verwenden Sie das **licenseoptions** -Objekt aus Schritt 1 für einen oder mehrere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="7cdb0-127">Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="7cdb0-128">Im folgenden Beispiel wird ein neues Konto für Allie Bellew erstellt, das die Lizenz zuweist und die in Schritt 1 beschriebenen Dienste deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="7cdb0-129">Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="7cdb0-130">Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="7cdb0-131">In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="7cdb0-132">Um die in Schritt 1 beschriebenen Dienste für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen des Office 365 Plans in der Anzeige des Cmdlets **Get-MsolAccountSku** (wie **litwareinc: ENTERPRISEPACK**) ein, und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="7cdb0-133">Wenn Sie das Cmdlet **Get-MsolUser** ohne den Parameter _all_ verwenden, werden nur die ersten 500-Benutzerkonten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="7cdb0-134">Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="7cdb0-135">**Methode 1. Filtern der Konten basierend auf einem vorhandenen Kontoattribut**</span><span class="sxs-lookup"><span data-stu-id="7cdb0-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="7cdb0-136">Verwenden Sie hierzu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="7cdb0-137">Im folgenden Beispiel werden die Dienste für Benutzer in der Vertriebsabteilung in den Vereinigten Staaten deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="7cdb0-138">**Methode 2: Verwenden einer Liste bestimmter Konten**</span><span class="sxs-lookup"><span data-stu-id="7cdb0-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="7cdb0-139">Gehen Sie dazu folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="7cdb0-140">Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="7cdb0-141">In diesem Beispiel lautet die Textdatei C:\\My Documents\\Accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="7cdb0-142">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="7cdb0-143">Wenn Sie den Zugriff auf Dienste für mehrere Lizenzierungs Pläne deaktivieren möchten, wiederholen Sie die obigen Anweisungen für jeden Lizenzierungs Plan, um Folgendes sicherzustellen:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="7cdb0-144">Die Benutzerkonten wurden mit dem Lizenzierungs Plan versehen.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="7cdb0-145">Die zu deaktivierenden Dienste stehen im Lizenzierungs Plan zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="7cdb0-146">Informationen zum Deaktivieren von Office 365 Diensten für Benutzer, während Sie Sie einem Lizenzierungs Plan zuweisen, finden Sie unter [Deaktivieren des Zugriffs auf Dienste beim Zuweisen von Benutzerlizenzen](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="7cdb0-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="7cdb0-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7cdb0-147">See also</span></span>
<span data-ttu-id="7cdb0-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="7cdb0-148"></span></span>

<span data-ttu-id="7cdb0-149">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7cdb0-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="7cdb0-150">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7cdb0-151">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7cdb0-152">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7cdb0-153">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="7cdb0-154">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cdb0-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
