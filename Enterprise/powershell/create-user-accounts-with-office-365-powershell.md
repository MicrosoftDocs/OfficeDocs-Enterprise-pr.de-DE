---
title: Erstellen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
ms.openlocfilehash: 846dafb842b87f119670f44848152a99341939e7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069061"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="80d41-103">Erstellen von Benutzerkonten mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80d41-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="80d41-104">**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.</span><span class="sxs-lookup"><span data-stu-id="80d41-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="80d41-p101">Sie können Office 365 PowerShell verwenden, um effizient Benutzerkonten, insbesondere mehrere Benutzerkonten, zu erstellen. Beim Erstellen von Benutzerkonten in Office 365 PowerShell sind bestimmte Kontoeigenschaften immer erforderlich. Andere Eigenschaften sind nicht erforderlich, um das Konto zu erstellen, sind aber dennoch wichtig. Diese Eigenschaften werden in der folgenden Tabelle beschrieben:</span><span class="sxs-lookup"><span data-stu-id="80d41-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="80d41-109">**Eigenschaftenname**</span><span class="sxs-lookup"><span data-stu-id="80d41-109">**Property name**</span></span>|<span data-ttu-id="80d41-110">**Erforderlich?**</span><span class="sxs-lookup"><span data-stu-id="80d41-110">**Required?**</span></span>|<span data-ttu-id="80d41-111">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="80d41-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="80d41-112">**Anzeigename**</span><span class="sxs-lookup"><span data-stu-id="80d41-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="80d41-113">Ja</span><span class="sxs-lookup"><span data-stu-id="80d41-113">Yes</span></span>  <br/> |<span data-ttu-id="80d41-p102">Dies ist der Anzeigename, der in Office 365-Diensten verwendet wird. Zum Beispiel „Caleb Sills".</span><span class="sxs-lookup"><span data-stu-id="80d41-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="80d41-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="80d41-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="80d41-117">Ja</span><span class="sxs-lookup"><span data-stu-id="80d41-117">Yes</span></span>  <br/> |<span data-ttu-id="80d41-p103">Dies ist der Kontoname, der zum Anmelden an Office 365-Diensten verwendet wird. Zum Beispiel „CalebS@contoso.onmicrosoft.com".</span><span class="sxs-lookup"><span data-stu-id="80d41-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="80d41-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="80d41-120">**FirstName**</span></span> <br/> |<span data-ttu-id="80d41-121">Nein</span><span class="sxs-lookup"><span data-stu-id="80d41-121">No</span></span>  <br/> ||
|<span data-ttu-id="80d41-122">**Nachname**</span><span class="sxs-lookup"><span data-stu-id="80d41-122">**LastName**</span></span> <br/> |<span data-ttu-id="80d41-123">Nein</span><span class="sxs-lookup"><span data-stu-id="80d41-123">No</span></span>  <br/> ||
|<span data-ttu-id="80d41-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="80d41-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="80d41-125">Nein</span><span class="sxs-lookup"><span data-stu-id="80d41-125">No</span></span>  <br/> |<span data-ttu-id="80d41-p104">Dies ist der Lizenzierungsplan (auch als Lizenzplan, Office 365-Plan oder SKU bezeichnet), aus dem eine verfügbare Lizenz dem Benutzerkonto zugewiesen wird. Die Lizenz definiert die Office 365-Dienste, die für das Konto verfügbar sind. Sie müssen einem Benutzer keine Lizenz zuweisen, wenn Sie das Konto erstellen, aber das Konto benötigt eine Lizenz für den Zugriff auf Office 365-Dienste. Sie haben 30 Tage Zeit, um das Benutzerkonto zu lizenzieren, nachdem Sie es erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="80d41-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="80d41-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="80d41-130">**Password**</span></span> <br/> |<span data-ttu-id="80d41-131">Nein</span><span class="sxs-lookup"><span data-stu-id="80d41-131">No</span></span>  <br/> | <span data-ttu-id="80d41-p105">Wenn Sie kein Kennwort angeben, wird dem Benutzerkonto ein zufälliges Kennwort zugewiesen, und das Kennwort wird in den Ergebnissen des Befehls angezeigt. Wenn Sie ein Kennwort angeben, muss es aus 8 bis 16 ASCII-Textzeichen aus drei der folgenden Kategorien bestehen: Kleinbuchstaben, Großbuchstaben, Zahlen oder Symbole.</span><span class="sxs-lookup"><span data-stu-id="80d41-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="80d41-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="80d41-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="80d41-135">Nein</span><span class="sxs-lookup"><span data-stu-id="80d41-135">No</span></span>  <br/> |<span data-ttu-id="80d41-p106">Dies ist ein gültiger ISO 3166-1-Alpha-2-Ländercode. „US“ steht zum Beispiel für die Vereinigten Staaten und „FR“ für Frankreich. Es ist wichtig, diesen Wert anzugeben, da einige Office 365-Dienste in bestimmten Ländern nicht verfügbar sind, sodass Sie einem Benutzerkonto nur dann eine Lizenz zuweisen können, wenn dieser Wert für das Konto konfiguriert wurde. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="80d41-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="80d41-140">Verwenden der Azure Active Directory PowerShell für Graph-Module</span><span class="sxs-lookup"><span data-stu-id="80d41-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="80d41-141">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="80d41-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="80d41-142">Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="80d41-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="80d41-143">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills“ erstellt:</span><span class="sxs-lookup"><span data-stu-id="80d41-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="80d41-144">Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80d41-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="80d41-145">Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="80d41-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="80d41-146">Erstellen eines einzelnen Benutzerkontos</span><span class="sxs-lookup"><span data-stu-id="80d41-146">Create an individual user account</span></span>

<span data-ttu-id="80d41-147">Verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="80d41-147">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

<span data-ttu-id="80d41-148">Mit dem folgenden Befehl erhalten Sie eine Liste der Namen der Lizenzierungspläne:</span><span class="sxs-lookup"><span data-stu-id="80d41-148">To list the available licensing plan names, use this command:</span></span>

````
Get-MsolAccountSku
````

<span data-ttu-id="80d41-149">In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills" erstellt und eine Lizenz aus dem `contoso:ENTERPRISEPACK`-Lizenzierungsplan (Office 365 Enterprise E3) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="80d41-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="80d41-150">Erstellen mehrerer Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="80d41-150">Create multiple user accounts</span></span>

1. <span data-ttu-id="80d41-p107">Erstellen Sie eine durch Kommata getrennte Wertedatei (CSV), die die erforderlichen Informationen zum Benutzerkonto enthält. Beispiel:</span><span class="sxs-lookup"><span data-stu-id="80d41-p107">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="80d41-153">Die Spaltennamen und deren Reihenfolge in der ersten Zeile der CSV-Datei sind zufällig, aber stellen Sie sicher, dass die Daten in der restlichen Datei der Reihenfolge der Spaltennamen entspricht, und verwenden Sie die Spaltennamen für die Parameterwerte im Office 365 PowerShell-Befehl.</span><span class="sxs-lookup"><span data-stu-id="80d41-153">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="80d41-154">Verwenden Sie die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="80d41-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="80d41-155">In diesem Beispiel werden die Benutzerkonten aus der Datei mit dem Namen „C:\My Documents\NewAccounts.csv“ erstellt, und die Ergebnisse werden in der Datei mit dem Namen „C:\My Documents\NewAccountResults.csv“ protokolliert.</span><span class="sxs-lookup"><span data-stu-id="80d41-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="80d41-p108">Die Ergebnisse können Sie in der Ausgabedatei überprüfen. Wir haben keine Kennwörter angeben, damit die generierten zufälligen Kennwörter, die Office 365 generiert hat, in der Ausgabedatei angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="80d41-p108">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="80d41-158">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="80d41-158">See also</span></span>

[<span data-ttu-id="80d41-159">Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80d41-159">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="80d41-160">Verwalten von Office 365 mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80d41-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="80d41-161">Erste Schritte mit Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="80d41-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
