---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
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
ms.openlocfilehash: 711f48dd2caad6fc2b438010405b126be203bd54
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257600"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="8b327-103">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="8b327-104">Wenn einem Office 365-Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wird, werden dem Benutzer Office 365 Dienste aus dieser Lizenz zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="8b327-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="8b327-105">Sie können jedoch die Office 365 Dienste steuern, auf die der Benutzer zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="8b327-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="8b327-106">Beispielsweise können Sie den Zugriff darauf deaktivieren, auch wenn die Lizenz den Zugriff auf den SharePoint Online Dienst zulässt.</span><span class="sxs-lookup"><span data-stu-id="8b327-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="8b327-107">Sie können PowerShell verwenden, um den Zugriff auf eine beliebige Anzahl von Diensten für einen bestimmten Lizenzierungs Plan für zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="8b327-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="8b327-108">ein einzelnes Konto</span><span class="sxs-lookup"><span data-stu-id="8b327-108">An individual account.</span></span>
    
- <span data-ttu-id="8b327-109">eine Gruppe von Konten</span><span class="sxs-lookup"><span data-stu-id="8b327-109">A group of accounts.</span></span>
    
- <span data-ttu-id="8b327-110">Alle Konten in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="8b327-110">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8b327-111">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8b327-112">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8b327-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="8b327-113">Verwenden Sie anschließend diesen Befehl, um die verfügbaren Lizenzierungs Pläne anzuzeigen, die auch als AccountSkuIds bezeichnet werden:</span><span class="sxs-lookup"><span data-stu-id="8b327-113">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="8b327-114">PowerShell Core unterstützt das Microsoft Azure Active Directory Modul für Windows PowerShell Modul und Cmdlets mit **MSOL** nicht in Ihrem Namen.</span><span class="sxs-lookup"><span data-stu-id="8b327-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8b327-115">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie diese von Windows PowerShell aus ausführen.</span><span class="sxs-lookup"><span data-stu-id="8b327-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="8b327-116">Weitere Informationen finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8b327-116">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8b327-117">Informationen zu den vor-und nach Ergebnissen der Verfahren in diesem Thema finden Sie unter [View Account License and Servicedetails with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8b327-117">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8b327-p103">Ein PowerShell-Skript steht zur Verfügung, das die in diesem Thema erläuterten Verfahren automatisiert. Insbesondere ermöglicht das Skript Ihnen das Anzeigen und Deaktivieren von Diensten in Ihrer Office 365-Organisation, einschließlich Sway. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8b327-p103">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="8b327-121">Deaktivieren bestimmter Office 365 Dienste für bestimmte Benutzer für einen bestimmten Lizenzierungs Plan</span><span class="sxs-lookup"><span data-stu-id="8b327-121">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="8b327-122">Führen Sie die folgenden Schritte aus, um eine bestimmte Gruppe von Office 365 Diensten für Benutzer für einen bestimmten Lizenzierungs Plan zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="8b327-122">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="8b327-123">Identifizieren Sie die unerwünschten Dienste im Lizenzierungs Plan mit der folgenden Syntax:</span><span class="sxs-lookup"><span data-stu-id="8b327-123">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="8b327-124">Im folgenden Beispiel wird ein **licenseoptions** -Objekt erstellt, das die Office-und SharePoint Online-Dienste im Lizenzierungs Plan `litwareinc:ENTERPRISEPACK` mit dem Namen (Office 365 Enterprise E3) deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8b327-124">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="8b327-125">Verwenden Sie das **LicenseOptions**-Objekt aus Schritt 1 für einen oder mehrere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8b327-125">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="8b327-126">Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="8b327-126">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="8b327-127">Im folgenden Beispiel wird ein neues Konto für Allie Bellew erstellt, das die Lizenz zuweist und die in Schritt 1 beschriebenen Dienste deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8b327-127">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```powershell
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="8b327-128">Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="8b327-128">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="8b327-129">Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="8b327-129">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="8b327-130">In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8b327-130">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="8b327-131">Um die in Schritt 1 beschriebenen Dienste für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen des Office 365 Plans in der Anzeige des Cmdlets **Get-MsolAccountSku** (wie **litwareinc: ENTERPRISEPACK**) ein, und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="8b327-131">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```powershell
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="8b327-132">Wenn Sie das Cmdlet **Get-MsolUser** ohne den Parameter _all_ verwenden, werden nur die ersten 500-Benutzerkonten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b327-132">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="8b327-133">Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:</span><span class="sxs-lookup"><span data-stu-id="8b327-133">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="8b327-134">**Filtern der Konten basierend auf einem vorhandenen Kontoattribut** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="8b327-134">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```powershell
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="8b327-135">Im folgenden Beispiel werden die Dienste für Benutzer in der Vertriebsabteilung in den Vereinigten Staaten deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8b327-135">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```powershell
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="8b327-136">**Verwenden einer Liste bestimmter Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="8b327-136">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="8b327-137">Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="8b327-137">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="8b327-138">In diesem Beispiel lautet die Textdatei C:\\My Documents\\Accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="8b327-138">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="8b327-139">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="8b327-139">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="8b327-140">Wenn Sie den Zugriff auf Dienste für mehrere Lizenzierungs Pläne deaktivieren möchten, wiederholen Sie die obigen Anweisungen für jeden Lizenzierungs Plan, um Folgendes sicherzustellen:</span><span class="sxs-lookup"><span data-stu-id="8b327-140">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="8b327-141">Die Benutzerkonten wurden mit dem Lizenzierungs Plan versehen.</span><span class="sxs-lookup"><span data-stu-id="8b327-141">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="8b327-142">Die zu deaktivierenden Dienste stehen im Lizenzierungs Plan zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8b327-142">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="8b327-143">Informationen zum Deaktivieren von Office 365 Diensten für Benutzer, während Sie Sie einem Lizenzierungs Plan zuweisen, finden Sie unter [Deaktivieren des Zugriffs auf Dienste beim Zuweisen von Benutzerlizenzen](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="8b327-143">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="8b327-144">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="8b327-144">New to Office 365?</span></span>
<span data-ttu-id="8b327-145"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="8b327-145"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="8b327-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8b327-146">See also</span></span>
<span data-ttu-id="8b327-147"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="8b327-147"></span></span>

<span data-ttu-id="8b327-148">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8b327-148">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="8b327-149">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8b327-150">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8b327-151">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-151">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8b327-152">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-152">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="8b327-153">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b327-153">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
