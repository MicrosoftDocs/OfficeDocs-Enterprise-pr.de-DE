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
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Erstellen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.
  
Sie können Office 365 PowerShell verwenden, um effizient Benutzerkonten, insbesondere mehrere Benutzerkonten, zu erstellen. Beim Erstellen von Benutzerkonten in Office 365 PowerShell sind bestimmte Kontoeigenschaften immer erforderlich. Andere Eigenschaften sind nicht erforderlich, um das Konto zu erstellen, sind aber dennoch wichtig. Diese Eigenschaften werden in der folgenden Tabelle beschrieben:
  
****

|**Eigenschaftenname**|**Erforderlich?**|**Beschreibung**|
|:-----|:-----|:-----|
|**Anzeigename** <br/> |Ja  <br/> |Dies ist der Anzeigename, der in Office 365-Diensten verwendet wird. Zum Beispiel „Caleb Sills".  <br/> |
|**UserPrincipalName** <br/> |Ja  <br/> |Dies ist der Kontoname, der zum Anmelden an Office 365-Diensten verwendet wird. Zum Beispiel „CalebS@contoso.onmicrosoft.com".  <br/> |
|**FirstName** <br/> |Nein  <br/> ||
|**Nachname** <br/> |Nein  <br/> ||
|**LicenseAssignment** <br/> |Nein  <br/> |Dies ist der Lizenzierungsplan (auch als Lizenzplan, Office 365-Plan oder SKU bezeichnet), aus dem eine verfügbare Lizenz dem Benutzerkonto zugewiesen wird. Die Lizenz definiert die Office 365-Dienste, die für das Konto verfügbar sind. Sie müssen einem Benutzer keine Lizenz zuweisen, wenn Sie das Konto erstellen, aber das Konto benötigt eine Lizenz für den Zugriff auf Office 365-Dienste. Sie haben 30 Tage Zeit, um das Benutzerkonto zu lizenzieren, nachdem Sie es erstellt haben.<br/> Verwenden Sie das **Get-MsolAccountSku**-Cmdlet zum Anzeigen der Lizenzierungspläne (**AccountSkuId**) und der verfügbaren Lizenzen in Ihrer Organisation. Weitere Informationen finden Sie unter[Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).  <br/> |
|**Password** <br/> |Nein  <br/> | Wenn Sie kein Kennwort angeben, wird dem Benutzerkonto ein zufälliges Kennwort zugewiesen, und das Kennwort wird in den Ergebnissen des Befehls angezeigt. Wenn Sie ein Kennwort angeben, muss es die folgenden Komplexitätsanforderungen erfüllen: <br/>  8 bis 16 ASCII-Textzeichen. <br/>  Zeichen aus drei der folgenden Typen: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. <br/> |
|**UsageLocation** <br/> |Nein  <br/> |Dies ist ein gültiger ISO 3166-1-Alpha-2-Ländercode. „US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich. Es ist wichtig, diesen Wert anzugeben, da einige Office 365-Dienste in bestimmten Ländern nicht verfügbar sind, sodass Sie einem Benutzerkonto nur dann eine Lizenz zuweisen können, wenn dieser Wert für das Konto konfiguriert wurde. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Bevor Sie beginnen:

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Verwenden von Office 365 PowerShell zum Erstellen einzelner Benutzerkonten

Verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills" erstellt und eine Lizenz aus dem  `contoso:ENTERPRISEPACK`-Lizenzierungsplan (Office 365 Enterprise E3) zugewiesen.
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Verwenden von Office 365 PowerShell zum Erstellen mehrerer Benutzerkonten.

1. Erstellen Sie eine durch Kommata getrennte Wertedatei (CSV), die die erforderlichen Informationen zum Benutzerkonto enthält. Beispiel:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Die Spaltennamen und deren Reihenfolge in der ersten Zeile der CSV-Datei sind zufällig, aber stellen Sie sicher, dass die Daten in der restlichen Datei der Reihenfolge der Spaltennamen entspricht, und verwenden Sie die Spaltennamen für die Parameterwerte im Office 365 PowerShell-Befehl.
    
2. Verwenden Sie die folgende Syntax:
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

In diesem Beispiel werden die Benutzerkonten aus der Datei mit dem Namen „C:\My Documents\NewAccounts.csv“ erstellt, und die Ergebnisse werden in der Datei mit dem Namen „C:\My Documents\NewAccountResults.csv“ protokolliert.
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Die Ergebnisse können Sie in der Ausgabedatei überprüfen. Wir haben keine Kennwörter angeben, damit die generierten zufälligen Kennwörter in der Ausgabedatei angezeigt werden.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Erstellen von einzelnen Benutzerkonten mit dem Azure Active Directory V2 PowerShell-Modul

Um das Cmdlet **New-AzureADUser** aus dem Azure Active Directory V2 PowerShell-Modul zu verwenden, müssen Sie zunächst eine Verbindung zu Ihrem Abonnement herstellen. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills“ erstellt:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>Siehe auch

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

