---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Erläutert die Verwendung von Office 365 PowerShell Zuweisen einer Office 365-Lizenz zu nicht lizenzierten Benutzern.
ms.openlocfilehash: 5040249f29ac8390db5b2933fc04fb1d01f0af2c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931764"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert die Verwendung von Office 365 PowerShell Zuweisen einer Office 365-Lizenz zu nicht lizenzierten Benutzern.
  
Benutzer können keine Office 365-Dienste verwenden, bis Ihr Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wurde. Sie können Office 365 PowerShell verwenden, um Lizenzen für nicht lizenzierte Konten schnell zuzuweisen. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Führen Sie als nächstes die Lizenz Pläne für Ihren Mandanten mit diesem Befehl aus.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz hinzufügen möchten, auch bekannt als Benutzerprinzipalname (UPN).

Geben Sie schließlich den Benutzernamen und den Lizenzplan Namen an, und führen Sie die folgenden Befehle aus.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Führen Sie den Befehl **Get-MsolAccountSku** aus, um die verfügbaren Lizenzierungs Pläne und die Anzahl der verfügbaren Lizenzen in jedem Plan in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in jedem Plan ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Führen Sie diesen Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
Sie können nur Lizenzen zu Benutzerkonten zuweisen, für die die **UsageLocation** -Eigenschaft auf eine gültige ISO 3166-1-Alpha-2-Landeskennzahl festgelegt ist. „US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Führen Sie diesen Befehl aus, um Konten zu suchen, die keinen **UsageLocation** -Wert besitzen.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Führen Sie den folgenden Befehl aus, um den **UsageLocation** -Wert für ein Konto festzulegen.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Beispiel:

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.

### <a name="assigning-licenses-to-user-accounts"></a>Zuweisen von Lizenzen zu Benutzerkonten
    
Verwenden Sie den folgenden Befehl in Office 365 PowerShell, um einem Benutzer eine Lizenz zuzuweisen.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In diesem Beispiel wird dem nicht lizenzierten Benutzer **belindan@litwareinc.com**eine Lizenz aus dem **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenzplan zugewiesen:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Führen Sie diesen Befehl aus, um vielen nicht lizenzierten Benutzern eine Lizenz zuzuweisen.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen. Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.
>

In diesem Beispiel werden allen nicht lizenzierten Benutzern Lizenzen aus dem **litwareinc: ENTERPRISEPACK** -Lizenzierungs Plan (Office 365 Enterprise E3) zugewiesen:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In diesem Beispiel werden die gleichen Lizenzen nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
