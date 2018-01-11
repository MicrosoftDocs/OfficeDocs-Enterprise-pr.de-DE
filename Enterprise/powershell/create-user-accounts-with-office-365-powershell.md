---
title: Erstellen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.
ms.openlocfilehash: 97830f8158f84e6978cf3f2d168aa83d9fc551e6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="27db2-103">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="27db2-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="27db2-104">**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.</span><span class="sxs-lookup"><span data-stu-id="27db2-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="27db2-p101">Sie können Office 365 PowerShell verwenden, um effizient Benutzerkonten, insbesondere mehrere Benutzerkonten, zu erstellen. Beim Erstellen von Benutzerkonten in Office 365 PowerShell sind bestimmte Kontoeigenschaften immer erforderlich. Andere Eigenschaften sind nicht erforderlich, um das Konto zu erstellen, sind aber dennoch wichtig. Diese Eigenschaften werden in der folgenden Tabelle beschrieben:</span><span class="sxs-lookup"><span data-stu-id="27db2-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="27db2-109">**Eigenschaftenname**</span><span class="sxs-lookup"><span data-stu-id="27db2-109">**Property name**</span></span>|<span data-ttu-id="27db2-110">**Erforderlich?**</span><span class="sxs-lookup"><span data-stu-id="27db2-110">**Required?**</span></span>|<span data-ttu-id="27db2-111">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="27db2-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="27db2-112">**Anzeigename**</span><span class="sxs-lookup"><span data-stu-id="27db2-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="27db2-113">Ja</span><span class="sxs-lookup"><span data-stu-id="27db2-113">Yes</span></span>  <br/> |<span data-ttu-id="27db2-p102">Dies ist der Anzeigename, der in Office 365-Diensten verwendet wird. Zum Beispiel „Caleb Sills".</span><span class="sxs-lookup"><span data-stu-id="27db2-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="27db2-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="27db2-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="27db2-117">Ja</span><span class="sxs-lookup"><span data-stu-id="27db2-117">Yes</span></span>  <br/> |<span data-ttu-id="27db2-p103">Dies ist der Kontoname, der zum Anmelden an Office 365-Diensten verwendet wird. Zum Beispiel „CalebS@contoso.onmicrosoft.com".</span><span class="sxs-lookup"><span data-stu-id="27db2-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="27db2-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="27db2-120">**FirstName**</span></span> <br/> |<span data-ttu-id="27db2-121">Nein</span><span class="sxs-lookup"><span data-stu-id="27db2-121">No</span></span>  <br/> ||
|<span data-ttu-id="27db2-122">**Nachname**</span><span class="sxs-lookup"><span data-stu-id="27db2-122">**LastName**</span></span> <br/> |<span data-ttu-id="27db2-123">Nein</span><span class="sxs-lookup"><span data-stu-id="27db2-123">No</span></span>  <br/> ||
|<span data-ttu-id="27db2-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="27db2-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="27db2-125">Nein</span><span class="sxs-lookup"><span data-stu-id="27db2-125">No</span></span>  <br/> |<span data-ttu-id="27db2-p104">Dies ist der Lizenzierungsplan (auch als Lizenzplan, Office 365-Plan oder SKU bezeichnet), aus dem eine verfügbare Lizenz dem Benutzerkonto zugewiesen wird. Die Lizenz definiert die Office 365-Dienste, die für das Konto verfügbar sind. Sie müssen einem Benutzer keine Lizenz zuweisen, wenn Sie das Konto erstellen, aber das Konto benötigt eine Lizenz für den Zugriff auf Office 365-Dienste. Sie haben 30 Tage Zeit, um das Benutzerkonto zu lizenzieren, nachdem Sie es erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="27db2-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="27db2-p105">Verwenden Sie das **Get-MsolAccountSku**-Cmdlet zum Anzeigen der Lizenzierungspläne (**AccountSkuId**) und der verfügbaren Lizenzen in Ihrer Organisation. Weitere Informationen finden Sie unter[Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span><span class="sxs-lookup"><span data-stu-id="27db2-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  </span></span><br/> |
|<span data-ttu-id="27db2-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="27db2-132">**Password**</span></span> <br/> |<span data-ttu-id="27db2-133">Nein</span><span class="sxs-lookup"><span data-stu-id="27db2-133">No</span></span>  <br/> | <span data-ttu-id="27db2-p106">Wenn Sie kein Kennwort angeben, wird dem Benutzerkonto ein zufälliges Kennwort zugewiesen, und das Kennwort wird in den Ergebnissen des Befehls angezeigt. Wenn Sie ein Kennwort angeben, muss es die folgenden Komplexitätsanforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="27db2-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="27db2-136">8 bis 16 ASCII-Textzeichen.</span><span class="sxs-lookup"><span data-stu-id="27db2-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="27db2-137">Zeichen aus drei der folgenden Typen: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole.</span><span class="sxs-lookup"><span data-stu-id="27db2-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="27db2-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="27db2-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="27db2-139">Nein</span><span class="sxs-lookup"><span data-stu-id="27db2-139">No</span></span>  <br/> |<span data-ttu-id="27db2-p107">Dies ist ein gültiger ISO 3166-1-Alpha-2-Ländercode. „US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich. Es ist wichtig, diesen Wert anzugeben, da einige Office 365-Dienste in bestimmten Ländern nicht verfügbar sind, sodass Sie einem Benutzerkonto nur dann eine Lizenz zuweisen können, wenn dieser Wert für das Konto konfiguriert wurde. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="27db2-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="27db2-144">Bevor Sie beginnen:</span><span class="sxs-lookup"><span data-stu-id="27db2-144">Before you begin</span></span>

<span data-ttu-id="27db2-p108">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="27db2-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="27db2-147">Verwenden von Office 365 PowerShell zum Erstellen einzelner Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="27db2-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="27db2-148">Verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="27db2-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="27db2-149">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills" erstellt und eine Lizenz aus dem  `contoso:ENTERPRISEPACK`-Lizenzierungsplan (Office 365 Enterprise E3) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="27db2-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="27db2-150">Verwenden von Office 365 PowerShell zum Erstellen mehrerer Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="27db2-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="27db2-p109">Erstellen Sie eine durch Kommata getrennte Wertedatei (CSV), die die erforderlichen Informationen zum Benutzerkonto enthält. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="27db2-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="27db2-153">Die Spaltennamen und deren Reihenfolge in der ersten Zeile der CSV-Datei sind zufällig, aber stellen Sie sicher, dass die Daten in der restlichen Datei der Reihenfolge der Spaltennamen entspricht, und verwenden Sie die Spaltennamen für die Parameterwerte im Office 365 PowerShell-Befehl.</span><span class="sxs-lookup"><span data-stu-id="27db2-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="27db2-154">Verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="27db2-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="27db2-155">In diesem Beispiel werden die Benutzerkonten aus der Datei mit dem Namen „C:\My Documents\NewAccounts.csv“ erstellt, und die Ergebnisse werden in der Datei mit dem Namen „C:\My Documents\NewAccountResults.csv“ protokolliert.</span><span class="sxs-lookup"><span data-stu-id="27db2-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="27db2-p110">Die Ergebnisse können Sie in der Ausgabedatei überprüfen. Wir haben keine Kennwörter angeben, damit die generierten zufälligen Kennwörter in der Ausgabedatei angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27db2-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="27db2-158">Erstellen von einzelnen Benutzerkonten mit dem Azure Active Directory V2 PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="27db2-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="27db2-p111">Um das Cmdlet **New-AzureADUser** aus dem Azure Active Directory V2 PowerShell-Modul zu verwenden, müssen Sie zunächst eine Verbindung zu Ihrem Abonnement herstellen. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="27db2-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="27db2-161">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="27db2-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="27db2-162">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills“ erstellt:</span><span class="sxs-lookup"><span data-stu-id="27db2-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="27db2-163">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="27db2-163">See also</span></span>

<span data-ttu-id="27db2-164">In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="27db2-164">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="27db2-165">Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="27db2-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="27db2-166">Blockieren von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="27db2-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="27db2-167">Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="27db2-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="27db2-168">Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="27db2-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="27db2-169">Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="27db2-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="27db2-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="27db2-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- <span data-ttu-id="27db2-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)</span><span class="sxs-lookup"><span data-stu-id="27db2-171">[Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)</span></span>
    
- [<span data-ttu-id="27db2-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="27db2-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="27db2-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="27db2-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="27db2-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="27db2-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

