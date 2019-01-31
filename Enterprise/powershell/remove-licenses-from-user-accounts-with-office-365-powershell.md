---
title: Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651219"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Im nächsten Schritt die Lizenz Pläne für Ihre Mandanten mit diesem Befehl aufgelistet.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Rufen Sie im nächsten Schritt der Anmeldename des Kontos für die Sie eine Lizenz, auch bekannt als den Benutzerprinzipalnamen (UPN) entfernen möchten.

Schließlich geben Sie die Anmeldung und Lizenz Plan Benutzernamen an, entfernen Sie die Zeichen "<" und ">" und führen Sie diese Befehle aus.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

   
Zum Anzeigen der Lizenzinformationen Plan (**AccountSkuID** ) in Ihrer Organisation finden Sie in den folgenden Themen:
    
  - [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    
### <a name="removing-licenses-from-user-accounts"></a>Entfernen von Lizenzen von Benutzerkonten

Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` Lizenz aus dem Benutzerkonto BelindaN@litwareinc.com (Office 365 Enterprise E3).
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Verwenden Sie eine der folgenden Methoden, um Lizenzen von einer Gruppe von vorhandenen lizenzierten Benutzern zu entfernen,:
  
- **Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenzen von allen Konten für Benutzer in der Abteilung "Sales" in den USA.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:
    
1. Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Verwenden Sie folgende Syntax:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz von Benutzerkonten in der Textdatei C:\My Documents\Accounts.txt definiert.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Verwenden Sie die folgende Syntax, um Lizenzen von allen vorhandenen Benutzerkonten zu entfernen:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz aus allen vorhandenen Benutzerkonten lizenziert.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Löschen des Benutzerkontos ist eine weitere Möglichkeit, um eine Lizenz freizugeben. Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

