---
title: Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten.
ms.openlocfilehash: eb1ca1d9812b08a6ea932fde546351f664c93066
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327327"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Anzeigen lizenzierter und nicht lizenzierter Benutzer mit Office 365 PowerShell

**Zusammenfassung:** Erläutert das Verwenden von Office 365 PowerShell zum Anzeigen von lizenzierten und nicht lizenzierten Benutzerkonten.
  
Benutzerkonten in Ihrer Office 365-Organisation sind möglicherweise einige, alle oder keine der verfügbaren Lizenzen aus den Lizenzierungsplänen zugewiesen, die in Ihrer Organisation verfügbar sind. Mit Office 365 PowerShell können Sie lizenzierte und nicht lizenzierte Benutzer in Ihrer Organisation schnell finden.


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Um die Liste aller Benutzerkonten in Ihrer Organisation, die nicht keines der Lizenzierung Pläne (nicht lizenzierten Benutzer) zugewiesen wurden, führen Sie den folgenden Befehl aus:
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Um die Liste aller Benutzerkonten in Ihrer Organisation, die wurden zugewiesen keines der Lizenzierung Pläne (lizenzierten Benutzern) den folgenden Befehl ausführen:
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Führen Sie den folgenden Befehl in Office 365 PowerShell aus, um die Liste aller Benutzerkonten mit ihrem Lizenzierungsstatus in Ihrer Organisation anzuzeigen:
  
```
Get-MsolUser -All
```

Führen Sie den folgenden Befehl aus, um die Liste aller nicht lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Führen Sie den folgenden Befehl aus, um die Liste aller lizenzierten Benutzerkonten in Ihrer Organisation anzuzeigen:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
