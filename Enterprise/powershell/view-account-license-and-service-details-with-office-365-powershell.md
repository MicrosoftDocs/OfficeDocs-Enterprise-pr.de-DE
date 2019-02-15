---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert die Verwendung von Office 365 PowerShell zum Bestimmen der Office 365-Dienste, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 113107df75880a21210991d5b301245d75c5c739
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052969"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert die Verwendung von Office 365 PowerShell zum Bestimmen der Office 365-Dienste, die Benutzern zugewiesen wurden.
  
In Office 365 erteilen Lizenzen aus Lizenzierungs Plänen (auch als SKUs oder Office 365-Pläne bezeichnet) Benutzern den Zugriff auf die Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer verfügt jedoch möglicherweise nicht über Zugriff auf alle Dienste, die in einer Lizenz zur Verfügung stehen, die Ihnen derzeit zugewiesen ist. Sie können Office 365 PowerShell verwenden, um den Status von Diensten in Benutzerkonten anzuzeigen. 

Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Führen Sie als nächstes die Lizenz Pläne für Ihren Mandanten mit diesem Befehl aus.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Verwenden Sie diese Befehle, um die in den einzelnen Lizenzierungs Plänen verfügbaren Dienste aufzulisten.

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

Verwenden Sie diese Befehle, um die Lizenzen aufzulisten, die einem Benutzerkonto zugewiesen sind.

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Führen Sie als nächstes den folgenden Befehl aus, um die in Ihrer Organisation verfügbaren Lizenzierungs Pläne aufzulisten. 

```
Get-MsolAccountSku
```

Führen Sie dann diesen Befehl aus, um die Dienste aufzulisten, die in jedem Lizenzierungs Plan verfügbar sind, und die Reihenfolge, in der Sie aufgeführt werden (die Indexnummer).

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
Verwenden Sie diesen Befehl, um die Lizenzen aufzulisten, die einem Benutzer zugewiesen sind, und die Reihenfolge, in der Sie aufgelistet werden (die Indexnummer).

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
>Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
>
   

### <a name="to-view-services-for-a-user-account"></a>So zeigen Sie Dienste für ein Benutzerkonto an

Verwenden Sie die folgende Syntax, um alle Office 365-Dienste anzuzeigen, auf die ein Benutzer Zugriff hat:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

In diesem Beispiel werden die Dienste angezeigt, auf die der Benutzer BelindaN@litwareinc.com Zugriff hat. Dadurch werden die Dienste angezeigt, die allen Lizenzen zugeordnet sind, die Ihrem Konto zugewiesen sind.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Verwenden Sie die folgende Syntax, um alle Dienste für einen Benutzer anzuzeigen, dem *mehrere Lizenzen*zugewiesen wurden:

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
