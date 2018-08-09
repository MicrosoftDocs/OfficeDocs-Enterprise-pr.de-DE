---
title: Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Erläutert, wie Office 365 PowerShell verwenden, um Zugriff auf Office 365-Diensten für Benutzer in Ihrer Organisation zu deaktivieren.
ms.openlocfilehash: 44b0ed84bb8fd098412c69258834194b2b1eeb2f
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "22196822"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="595e7-103">Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="595e7-104">**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um Zugriff auf Office 365-Diensten für Benutzer in Ihrer Organisation zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="595e7-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="595e7-p101">Wenn ein Office 365-Konto eine Lizenz von einem Lizenzierungsplan zugeordnet ist, sind Office 365-Dienste für den Benutzer über diese Lizenz verfügbar. Sie können jedoch die Office 365-Dienste steuern, die der Benutzer zugreifen kann. Obwohl die Lizenz Zugriff auf SharePoint Online ermöglicht, können Sie beispielsweise Zugriff darauf deaktivieren. Office 365 PowerShell können Sie tatsächlich den Zugriff auf eine beliebige Anzahl von Diensten für deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="595e7-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="595e7-109">ein einzelnes Konto</span><span class="sxs-lookup"><span data-stu-id="595e7-109">An individual account.</span></span>
    
- <span data-ttu-id="595e7-110">eine Gruppe von Konten</span><span class="sxs-lookup"><span data-stu-id="595e7-110">A group of accounts.</span></span>
    
- <span data-ttu-id="595e7-111">Alle Konten in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="595e7-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="595e7-112">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="595e7-112">Before you begin</span></span>
<span data-ttu-id="595e7-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="595e7-113"></span></span>

- <span data-ttu-id="595e7-p102">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="595e7-p103">Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um anzuzeigen, Ihrer verfügbaren lizenzierungspläne und die Office 365-Dienste, die in dieser Pläne zur Verfügung stehen. Weitere Informationen finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="595e7-118">Anzeigen der vor und nach der Ergebnisse der Verfahren in diesem Thema finden Sie unter [Anzeigen von Kontodetails Lizenz und den Dienst mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="595e7-p104">Ein PowerShell-Skript ist verfügbar, die die in diesem Thema beschriebenen Verfahren automatisiert. Insbesondere ermöglicht das Skript anzeigen und Deaktivieren von Diensten in Office 365-Organisation, einschließlich Schlingern. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Schlingern mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="595e7-122">Wenn Sie das Cmdlet **Get-MsolUser** ohne mit dem _Alle_ Parameter verwenden, werden nur die ersten 500 Benutzerkonten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="595e7-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="595e7-123">Planen von bestimmte Office 365-Diensten für bestimmte Benutzer für die einzelnen Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="595e7-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="595e7-124">Um eine bestimmte Gruppe von Office 365-Diensten für Benutzer aus einer einzelnen Lizenzierungsplan deaktivieren möchten, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="595e7-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="595e7-125">Identifizieren Sie die unerwünschten Dienste in den Lizenzierungsplan mithilfe der folgenden Syntax:</span><span class="sxs-lookup"><span data-stu-id="595e7-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="595e7-126">Das folgende Beispiel erstellt ein **LicenseOptions** -Objekt, das in den Lizenzierungsplan mit dem Namen der Office Online und SharePoint Online-Dienste deaktiviert `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="595e7-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="595e7-127">Verwenden Sie das **LicenseOptions**-Objekt aus Schritt 1 für einen oder mehrere Benutzer.</span><span class="sxs-lookup"><span data-stu-id="595e7-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="595e7-128">Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="595e7-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="595e7-129">Das folgende Beispiel erstellt ein neues Konto für Allie Bellew, die die Lizenz zugewiesen und deaktiviert die Dienste, die in Schritt 1 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="595e7-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="595e7-130">Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="595e7-131">Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="595e7-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="595e7-132">In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="595e7-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="595e7-133">Um die Dienste beschrieben in Schritt 1 für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen Ihres Office 365 Plans aus der Anzeige des Cmdlets **Get-MsolAccountSku** (beispielsweise **litwareinc: enterprisepack**), und führen Sie dann die folgenden Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="595e7-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="595e7-134">Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:</span><span class="sxs-lookup"><span data-stu-id="595e7-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="595e7-135">**Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="595e7-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="595e7-136">Das folgende Beispiel deaktiviert die Dienste für Benutzer in der Abteilung "Sales" in den USA.</span><span class="sxs-lookup"><span data-stu-id="595e7-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="595e7-137">**Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="595e7-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="595e7-138">Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:</span><span class="sxs-lookup"><span data-stu-id="595e7-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="595e7-139">In diesem Beispiel wird die Textdatei C:\\eigene\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="595e7-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="595e7-140">Führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="595e7-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="595e7-141">Um Office 365-Diensten für Benutzer zu deaktivieren, während Sie sie an einer Lizenzierungsplan zuweisen, finden Sie unter [Zugriff auf Dienste beim Zuweisen von Benutzerlizenzen deaktivieren](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="595e7-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="595e7-142">Bestimmten Office 365-Diensten für Benutzer aus allen lizenzierungspläne</span><span class="sxs-lookup"><span data-stu-id="595e7-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="595e7-143">Führen Sie die folgenden Schritte, um Office 365-Diensten für Benutzer in allen verfügbaren lizenzierungspläne zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="595e7-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="595e7-144">Kopieren Sie dieses Skript, und fügen Sie es in Editor ein.</span><span class="sxs-lookup"><span data-stu-id="595e7-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="595e7-145">Passen Sie die folgenden Werte für Ihre Umgebung an:</span><span class="sxs-lookup"><span data-stu-id="595e7-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="595e7-146">_<UndesirableService>_ In diesem Beispiel werden wir Office Online und SharePoint Online verwenden.</span><span class="sxs-lookup"><span data-stu-id="595e7-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="595e7-147">_<Account>_ In diesem Beispiel verwenden wir belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="595e7-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="595e7-148">Das angepasste Skript sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="595e7-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="595e7-p105">Speichern Sie das Skript als `RemoveO365Services.ps1` an einem Speicherort, die Sie leicht zu finden. In diesem Beispiel werden wir speichern Sie die Datei in `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="595e7-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="595e7-151">Führen Sie das Skript in Office 365 PowerShell mithilfe des folgenden Befehls.</span><span class="sxs-lookup"><span data-stu-id="595e7-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="595e7-152">Um die Effekte eines dieser Verfahren rückgängig zu machen (d. h., die deaktivierten Dienste erneut aktivieren), führen Sie das Verfahren erneut aus, aber verwenden Sie den Wert `$null` für den Parameter _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="595e7-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="595e7-153">Nach oben</span><span class="sxs-lookup"><span data-stu-id="595e7-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)



## <a name="new-to-office-365"></a><span data-ttu-id="595e7-154">Neu bei Office 365?</span><span class="sxs-lookup"><span data-stu-id="595e7-154">New to Office 365?</span></span>
<span data-ttu-id="595e7-155"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="595e7-155"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="595e7-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="595e7-156">See also</span></span>
<span data-ttu-id="595e7-157"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="595e7-157"></span></span>

<span data-ttu-id="595e7-158">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="595e7-158">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="595e7-159">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-159">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="595e7-160">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-160">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="595e7-161">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-161">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="595e7-162">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-162">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="595e7-163">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="595e7-163">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="595e7-164">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="595e7-164">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="595e7-165">Get-Content</span><span class="sxs-lookup"><span data-stu-id="595e7-165">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="595e7-166">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="595e7-166">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="595e7-167">Neue MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="595e7-167">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="595e7-168">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="595e7-168">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="595e7-169">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="595e7-169">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="595e7-170">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="595e7-170">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="595e7-171">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="595e7-171">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="595e7-172">Where-Object</span><span class="sxs-lookup"><span data-stu-id="595e7-172">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

