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
ms.openlocfilehash: c012d7451d022ea8cf3e3fa1a8d0a89d804e9c66
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746278"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deaktivieren des Zugriffs auf Dienste mit Office 365 PowerShell

Wenn einem Office 365-Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wird, werden dem Benutzer Office 365 Dienste aus dieser Lizenz zur Verfügung gestellt. Sie können jedoch die Office 365 Dienste steuern, auf die der Benutzer zugreifen kann. Beispielsweise können Sie den Zugriff darauf deaktivieren, auch wenn die Lizenz den Zugriff auf den SharePoint Online Dienst zulässt. Sie können PowerShell verwenden, um den Zugriff auf eine beliebige Anzahl von Diensten für einen bestimmten Lizenzierungs Plan für zu deaktivieren:

- ein einzelnes Konto
    
- eine Gruppe von Konten
    
- Alle Konten in Ihrer Organisation.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Verwenden Sie anschließend diesen Befehl, um die verfügbaren Lizenzierungs Pläne anzuzeigen, die auch als AccountSkuIds bezeichnet werden:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

Weitere Informationen finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Informationen zu den vor-und nach Ergebnissen der Verfahren in diesem Thema finden Sie unter [View Account License and Servicedetails with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Ein PowerShell-Skript steht zur Verfügung, das die in diesem Thema erläuterten Verfahren automatisiert. Insbesondere ermöglicht das Skript Ihnen das Anzeigen und Deaktivieren von Diensten in Ihrer Office 365-Organisation, einschließlich Sway. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf Sway mit Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Deaktivieren bestimmter Office 365 Dienste für bestimmte Benutzer für einen bestimmten Lizenzierungs Plan
  
Führen Sie die folgenden Schritte aus, um eine bestimmte Gruppe von Office 365 Diensten für Benutzer für einen bestimmten Lizenzierungs Plan zu deaktivieren:
  
1. Identifizieren Sie die unerwünschten Dienste im Lizenzierungs Plan mit der folgenden Syntax:
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  Im folgenden Beispiel wird ein **licenseoptions** -Objekt erstellt, das die Office-und SharePoint Online-Dienste im Lizenzierungs Plan `litwareinc:ENTERPRISEPACK` mit dem Namen (Office 365 Enterprise E3) deaktiviert.
    
  ```powershell
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Verwenden Sie das **LicenseOptions**-Objekt aus Schritt 1 für einen oder mehrere Benutzer.
    
  - Wenn Sie ein neues Konto zu erstellen möchten, für das die Dienste deaktiviert sind, verwenden Sie die folgende Syntax:
    
  ```powershell
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  Im folgenden Beispiel wird ein neues Konto für Allie Bellew erstellt, das die Lizenz zuweist und die in Schritt 1 beschriebenen Dienste deaktiviert.
    
  ```powershell
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Weitere Informationen zum Erstellen von Benutzerkonten in Office 365 PowerShell finden Sie unter [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Verwenden Sie die folgende Syntax, um die Dienste für einen vorhandenen lizenzierten Benutzer zu deaktivieren:
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  In diesem Beispiel werden die Dienste für den Benutzer „BelindaN@litwareinc.com“ deaktiviert.
    
  ```powershell
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Um die in Schritt 1 beschriebenen Dienste für alle vorhandenen lizenzierten Benutzer zu deaktivieren, geben Sie den Namen des Office 365 Plans in der Anzeige des Cmdlets **Get-MsolAccountSku** (wie **litwareinc: ENTERPRISEPACK**) ein, und führen Sie dann die folgenden Befehle aus:
    
  ```powershell
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Wenn Sie das Cmdlet **Get-MsolUser** ohne den Parameter _all_ verwenden, werden nur die ersten 500-Benutzerkonten zurückgegeben.


  - Verwenden Sie eine der folgenden Methoden, um die Dienste für eine Gruppe von vorhandenen Benutzern zu deaktivieren und die Benutzer zu identifizieren:
    
  - **Filtern der Konten basierend auf einem vorhandenen Kontoattribut** Verwenden Sie dazu die folgende Syntax:
    
  ```powershell
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Im folgenden Beispiel werden die Dienste für Benutzer in der Vertriebsabteilung in den Vereinigten Staaten deaktiviert.
    
  ```powershell
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Verwenden einer Liste bestimmter Konten** Führen Sie dazu die folgenden Schritte aus:
    
1. Erstellen Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  In diesem Beispiel lautet die Textdatei C:\\My Documents\\Accounts. txt.
    
2. Führen Sie den folgenden Befehl aus:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Wenn Sie den Zugriff auf Dienste für mehrere Lizenzierungs Pläne deaktivieren möchten, wiederholen Sie die obigen Anweisungen für jeden Lizenzierungs Plan, um Folgendes sicherzustellen:

- Die Benutzerkonten wurden mit dem Lizenzierungs Plan versehen.
- Die zu deaktivierenden Dienste stehen im Lizenzierungs Plan zur Verfügung.

Informationen zum Deaktivieren von Office 365 Diensten für Benutzer, während Sie Sie einem Lizenzierungs Plan zuweisen, finden Sie unter [Deaktivieren des Zugriffs auf Dienste beim Zuweisen von Benutzerlizenzen](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>Neu bei Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Siehe auch
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
