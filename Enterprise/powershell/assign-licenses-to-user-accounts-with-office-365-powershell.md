---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Vorgehensweise verwenden Office 365 PowerShell, um nicht lizenzierten Benutzern eine Office 365 Lizenz zuzuweisen.
ms.openlocfilehash: 9fbf81db3b942dab90ef214169f197a8fea3f7ed
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841682"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell

Benutzer können keine Office 365 Dienste verwenden, bis Ihrem Konto eine Lizenz aus einem Lizenzierungs Plan zugewiesen wurde. Sie können Office 365 PowerShell verwenden, um schnell Lizenzen für nicht lizenzierte Konten zuzuweisen. 

>[!Note]
>Benutzerkonten muss ein Standort zugewiesen sein. Sie können dies über die Eigenschaften eines Benutzerkontos im Microsoft 365 Admin Center oder über PowerShell tun.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Rufen Sie als nächstes den Anmeldenamen des Kontos ab, für das Sie eine Lizenz hinzufügen möchten, die auch als Benutzerprinzipalname (User Principal Name, UPN) bezeichnet wird.

Stellen Sie als nächstes sicher, dass dem Benutzerkonto ein Verwendungs Speicherort zugewiesen wurde.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Wenn kein Verwendungs Speicherort zugewiesen ist, können Sie einen mit folgenden Befehlen zuweisen:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Geben Sie schließlich den Benutzeranmeldenamen und den Namen des Lizenz Plans an, und führen Sie diese Befehle aus.

```powershell
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

Führen Sie `Get-MsolAccountSku` den Befehl aus, um die verfügbaren Lizenzierungs Pläne und die Anzahl der verfügbaren Lizenzen in jedem Plan in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in jedem Plan lautet **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

>[!Note]
>PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen. Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.
>

Führen Sie diesen Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Sie können nur Benutzerkonten Lizenzen zuweisen, für die die **UsageLocation** -Eigenschaft auf einen gültigen ISO 3166-1-Alpha-2-Ländercode festgelegt ist. „US" steht zum Beispiel für die Vereinigten Staaten und „FR" für Frankreich. Einige Office 365 Dienste stehen in bestimmten Ländern nicht zur Verfügung. Weitere Informationen finden Sie unter [Informationen zu Lizenzbeschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Führen Sie diesen Befehl aus, um Konten zu finden, die keinen **UsageLocation** -Wert haben.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Um den **UsageLocation** -Wert für ein Konto festzulegen, führen Sie diesen Befehl aus.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Zum Beispiel:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den **-All**-Parameter werden nur die ersten 500 Konten zurückgegeben.

### <a name="assigning-licenses-to-user-accounts"></a>Zuweisen von Lizenzen zu Benutzerkonten
    
Verwenden Sie den folgenden Befehl in Office 365 PowerShell, um einem Benutzer eine Lizenz zuzuweisen.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In diesem Beispiel wird dem nicht lizenzierten Benutzer **belindan\@litwareinc.com**eine Lizenz vom **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3)-Lizenzierungs Plan zugewiesen:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Um allen nicht lizenzierten Benutzern eine Lizenz zuzuweisen, führen Sie diesen Befehl aus.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen. Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.
>

In diesem Beispiel werden Lizenzen aus dem Lizenzierungs Plan **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) allen nicht lizenzierten Benutzern zugewiesen:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

In diesem Beispiel werden die gleichen Lizenzen nicht lizenzierten Benutzern in der Vertriebsabteilung in den Vereinigten Staaten zugewiesen:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Migrieren eines Benutzers in ein anderes Abonnement (Lizenzplan) mit dem Azure Active Directory PowerShell für Graph-Modul

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Rufen Sie als nächstes den Anmeldenamen des Benutzerkontos ab, für das Sie Switch-Abonnements verwenden möchten, auch bekannt als Benutzerprinzipalname (User Principal Name, UPN).

Als nächstes Listen Sie die Abonnements (Lizenz Pläne) für Ihren Mandanten mit diesem Befehl auf.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Als nächstes Listen Sie die Abonnements auf, die das Benutzerkonto derzeit mit diesen Befehlen aufweist.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifizieren Sie das Abonnement, das der Benutzer aktuell hat (das von-Abonnement) und das Abonnement, auf das der Benutzer umzieht (das Abonnement).

Geben Sie schließlich die an-und von-Abonnement Namen (SKU-Teilenummern) an, und führen Sie diese Befehle aus.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Sie können die Änderung des Abonnements für das Benutzerkonto mit den folgenden Befehlen überprüfen.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Weitere Artikel

[Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
