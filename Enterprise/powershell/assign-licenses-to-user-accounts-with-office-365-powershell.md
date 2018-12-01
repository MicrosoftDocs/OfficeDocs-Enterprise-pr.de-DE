---
title: Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123292"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zuweisen eine Office 365-Lizenz nicht lizenzierten Benutzern.
  
Lizenzieren von Benutzerkonten in Office 365 ist wichtig, da Benutzer keine Office 365-Dienste verwendet werden, bis ihr Konto lizenziert wurden. Office 365 PowerShell können Sie nicht lizenzierten Konten, insbesondere mehrere Konten effizient Lizenzen zuweisen. 

## <a name="before-you-begin"></a>Bevor Sie beginnen
<a name="RTT"> </a>

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie das Cmdlet " **Get-MsolAccountSku** ", um die verfügbaren lizenzierungspläne und die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen in Ihrer Organisation anzuzeigen. Die Anzahl der verfügbaren Lizenzen in den verschiedenen Plänen ist **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Diensten finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Führen Sie den Befehl aus, um die nicht lizenzierten Konten in Ihrer Organisation zu suchen,`Get-MsolUser -All -UnlicensedUsersOnly`
    
- Sie können nur für Benutzerkonten Lizenzen zuweisen, die die **usagelocation-Wert angegeben** -Eigenschaft auf einen gültigen ISO 3166-1 Alpha-2-Ländercode festgelegt haben. Beispielsweise uns für die USA und FR für Frankreich. Einige Office 365-Dienste sind in bestimmten Ländern nicht verfügbar. Weitere Informationen finden Sie unter [About Lizenz Einschränkungen](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Führen Sie den Befehl aus, um Konten suchen, die nicht über ein **usagelocation-Wert angegeben** Wert verfügen, `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Um den **usagelocation-Wert angegeben** Wert für ein Konto festzulegen, verwenden Sie die Syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Beispielsweise `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Wenn Sie das Cmdlet **Get-MsolUser** ohne Verwenden der `-All` -Parameter, die nur die ersten 500 Benutzerkonten zurückgegeben werden.

## <a name="assigning-licenses-to-user-accounts"></a>Zuweisen von Lizenzen zu Benutzerkonten
    
Wenn Sie einem Benutzer eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax in Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

In diesem Beispiel wird eine Lizenz aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für den nicht lizenzierten Benutzer `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Wenn Sie mehreren nicht lizenzierten Benutzern eine Lizenz zuweisen möchten, verwenden Sie die folgende Syntax:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Hinweise**
  
- Sie können einem Benutzer nicht mehrere Lizenzen aus dem gleichen Lizenzierungsplan zuweisen.
    
- Wenn Sie nicht über genügend verfügbare Lizenzen verfügen, werden die Lizenzen den Benutzern in der Reihenfolge zugewiesen, in der sie von dem **Get-MsolUser**-Cmdlet zurückgegeben werden, bis alle Lizenzen vergeben sind.
    
In diesem Beispiel wird die Lizenzen aus der `litwareinc:ENTERPRISEPACK` Lizenzierungsplan (Office 365 Enterprise E3) für alle nicht lizenzierten Benutzer.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

In diesem Beispiel werden dieselben Lizenzen den nicht lizenzierten Benutzern in der Vertriebsabteilung in den USA zugewiesen.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Siehe auch
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten](block-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

