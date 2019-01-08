---
title: Erstellen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
ms.openlocfilehash: 902f44dd4fc42d8f29ce92748cbbf1ce03c6615b
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730310"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Erstellen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Erstellen von Benutzerkonten in Office 365.
  
Sie können Office 365 PowerShell verwenden, um effizient Benutzerkonten, insbesondere mehrere Benutzerkonten, zu erstellen. Beim Erstellen von Benutzerkonten in Office 365 PowerShell sind bestimmte Kontoeigenschaften immer erforderlich. Andere Eigenschaften sind nicht erforderlich, um das Konto zu erstellen, sind aber dennoch wichtig. Diese Eigenschaften werden in der folgenden Tabelle beschrieben:
  
|**Eigenschaftenname**|**Erforderlich?**|**Beschreibung**|
|:-----|:-----|:-----|
|**Anzeigename** <br/> |Ja  <br/> |Dies ist der Anzeigename, der in Office 365-Diensten verwendet wird. Zum Beispiel „Caleb Sills".  <br/> |
|**UserPrincipalName** <br/> |Ja  <br/> |Dies ist der Kontoname, der zum Anmelden an Office 365-Diensten verwendet wird. Zum Beispiel „CalebS@contoso.onmicrosoft.com".  <br/> |
|**FirstName** <br/> |Nein  <br/> ||
|**Nachname** <br/> |Nein  <br/> ||
|**LicenseAssignment** <br/> |Nein  <br/> |Dies ist der Lizenzierungsplan (auch als Lizenzplan, Office 365-Plan oder SKU bezeichnet), aus dem eine verfügbare Lizenz dem Benutzerkonto zugewiesen wird. Die Lizenz definiert die Office 365-Dienste, die für das Konto verfügbar sind. Sie müssen einem Benutzer keine Lizenz zuweisen, wenn Sie das Konto erstellen, aber das Konto benötigt eine Lizenz für den Zugriff auf Office 365-Dienste. Sie haben 30 Tage Zeit, um das Benutzerkonto zu lizenzieren, nachdem Sie es erstellt haben. |
|**Password** <br/> |Nein  <br/> | Wenn Sie kein Kennwort angeben, wird dem Benutzerkonto ein zufälliges Kennwort zugewiesen, und das Kennwort wird in den Ergebnissen des Befehls angezeigt. Wenn Sie ein Kennwort angeben, muss es aus 8 bis 16 ASCII-Textzeichen aus drei der folgenden Kategorien bestehen: Kleinbuchstaben, Großbuchstaben, Zahlen oder Symbole. <br/> |
|**UsageLocation** <br/> |Nein  <br/> |Dies ist ein gültiger ISO 3166-1-Alpha-2-Ländercode. „US“ steht zum Beispiel für die Vereinigten Staaten und „FR“ für Frankreich. Es ist wichtig, diesen Wert anzugeben, da einige Office 365-Dienste in bestimmten Ländern nicht verfügbar sind, sodass Sie einem Benutzerkonto nur dann eine Lizenz zuweisen können, wenn dieser Wert für das Konto konfiguriert wurde. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills“ erstellt:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Erstellen eines einzelnen Benutzerkontos

Verwenden Sie die folgende Syntax, um ein einzelnes Konto zu erstellen:
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

Mit dem folgenden Befehl erhalten Sie eine Liste der Namen der Lizenzierungspläne:

````
Get-MsolAccountSku
````

In diesem Beispiel wird ein Konto für den US-amerikanischen Benutzer mit dem Namen „Caleb Sills" erstellt und eine Lizenz aus dem `contoso:ENTERPRISEPACK`-Lizenzierungsplan (Office 365 Enterprise E3) zugewiesen.
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Erstellen mehrerer Benutzerkonten

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

3. Die Ergebnisse können Sie in der Ausgabedatei überprüfen. Wir haben keine Kennwörter angeben, damit die generierten zufälligen Kennwörter, die Office 365 generiert hat, in der Ausgabedatei angezeigt werden.
    
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
