---
title: "Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell"
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
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Informationen zur Verwendung von Office 365 PowerShell zum Löschen und Wiederherstellen von Office 365-Benutzerkonten"
ms.openlocfilehash: fc72d51532780d2ddaaff20ecc6aebab06a001f4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Informationen zur Verwendung von Office 365 PowerShell zum Löschen und Wiederherstellen von Office 365-Benutzerkonten.
  
Wenn Sie Office 365 PowerShell zum Löschen eines Benutzerkontos verwenden, wird das Konto nicht endgültig gelöscht. Sie können das gelöschte Benutzerkonto innerhalb von 30 Tagen wiederherstellen.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen:

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Sie können den Zugriff auf einzelne Benutzerkonten mit Office 365 PowerShell blockieren.
<a name="ShortVersion"> </a>

Wenn Sie ein Benutzerkonto löschen möchten, verwenden Sie die folgende Syntax:
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

In diesem Beispiel wird das Benutzerkonto „BelindaN@litwareinc.com“ gelöscht.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Wenn Sie ein gelöschtes Benutzerkonto innerhalb der Nachfrist von 30 Tagen wiederherstellen möchten, verwenden Sie die folgende Syntax:
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

In diesem Beispiel wird das gelöschte Benutzerkonto „BelindaN@litwareinc.com“ wiederhergestellt.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Hinweise:**
  
- Um die Liste der gelöschten Benutzer anzuzeigen, die wiederhergestellt werden können, führen Sie den folgenden Befehl aus:
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Wenn der ursprüngliche Benutzerprinzipalnamen des Benutzerkontos durch ein anderes Konto verwendet wird, verwenden Sie den  _NewUserPrincipalName_-Parameter anstelle von  _UserPrincipalName_, um einen anderen Benutzerprinzipalnamen anzugeben, wenn Sie das Benutzerkonto wiederherstellen.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Entfernen eines Benutzerkontos mit dem Azure Active Directory V2 PowerShell-Modul
<a name="ShortVersion"> </a>

Um das Cmdlet **Remove-AzureADUser** aus dem Azure Active Directory V2 PowerShell-Modul zu verwenden, müssen Sie zunächst eine Verbindung zu Ihrem Abonnement herstellen. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu entfernen:
  
```
Remove-AzureADUser -ObjectID <Account>
```

In diesem Beispiel wird das Benutzerkonto „fabricec@litwareinc.com“ entfernt.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Der Parameter **-ObjectID** im Cmdlet **Remove-AzureAD** akzeptiert entweder den Kontonamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos.
  
Um den Kontonamen basierend auf dem Namen des Benutzers anzuzeigen, verwenden Sie die folgenden Befehle:
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

In diesem Beispiel wird der Kontoname für den Benutzer namens Caleb Sills angezeigt.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Um einen Kontonamen basierend auf dem Namen des Benutzers zu entfernen, verwenden Sie die folgenden Befehle:
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>Siehe auch
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

