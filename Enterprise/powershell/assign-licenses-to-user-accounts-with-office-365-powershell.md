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
description: Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651180"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.
  
Benutzer können keine Dienste von Office 365 verwenden, bis ihr Konto eine Lizenz aus einer Lizenzierungsplan zugewiesen wurde. Office 365 PowerShell können Sie schnell Lizenzen nicht lizenzierten Konten zuweisen. 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Im nächsten Schritt die Lizenz Pläne für Ihre Mandanten mit diesem Befehl aufgelistet.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Rufen Sie im nächsten Schritt der Anmeldename des Kontos ein, dem Sie eine Lizenz, auch bekannt als den Benutzerprinzipalnamen (UPN) hinzufügen möchten.

Schließlich geben Sie den Benutzernamen-Anmeldung und Plan Lizenznamen an, und führen Sie diese Befehle aus.

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

Führen Sie den Befehl **Get-MsolAccountSku** , um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Führen Sie diesen Befehl, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
Sie können nur Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Führen Sie diesen Befehl, um Konten zu suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen.

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Um den **usagelocation-Wert angegeben** Wert auf ein Konto festlegen möchten, führen Sie diesen Befehl aus.

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Beispiel:

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.

### <a name="assigning-licenses-to-user-accounts"></a>Zuweisen von Lizenzen zu Benutzerkonten
    
Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie den folgenden Befehl in Office 365 PowerShell.
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In diesem Beispiel wird eine Lizenz aus der **litwareinc: enterprisepack** (Office 365 Enterprise E3) licensing Plan für die nicht lizenzierten Benutzer **belindan@litwareinc.com**:
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Wenn eine Lizenz für viele nicht lizenzierten Benutzer zuweisen möchten, führen Sie diesen Befehl aus.
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>Sie können nicht mehrere Lizenzen für einen Benutzer aus den gleichen Lizenzierungsplan zuweisen. Wenn Sie nicht über genügend verfügbaren Lizenzen verfügen, werden die Lizenzen für Benutzer in der Reihenfolge zugewiesen, die sie vom Cmdlet **Get-MsolUser** zurückgegeben werden, bis die verfügbaren Lizenzen Neige zur.
>

In diesem Beispiel wird allen nicht lizenzierten Benutzern Lizenzen aus den Lizenzierungsplan **litwareinc: enterprisepack** (Office 365 Enterprise E3) zugewiesen:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In diesem Beispiel wird nicht lizenzierten Benutzer in der Abteilung "Sales" in den USA Lizenzen, die dieselben zugewiesen:
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
