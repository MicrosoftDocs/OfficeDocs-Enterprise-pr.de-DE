---
title: Löschen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Informationen zur Verwendung von Office 365 PowerShell zum Löschen von Office 365-Benutzerkonten
ms.openlocfilehash: b7c30ec422475a4cf11b28249e8a20d64a3c90a4
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746428"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Löschen von Benutzerkonten mit Office 365 PowerShell

Sie können Office 365 PowerShell verwenden, um ein Benutzerkonto zu löschen.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu entfernen:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

In diesem Beispiel wird das Benutzerkonto „fabricec@litwareinc.com“ entfernt.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Der Parameter **-ObjectID** im Cmdlet **Remove-AzureAD** akzeptiert entweder den Kontoanmeldenamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos.
  
Um den Kontonamen basierend auf dem Namen des Benutzers anzuzeigen, verwenden Sie die folgenden Befehle:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

In diesem Beispiel wird der Kontoname für den Benutzer namens Caleb Sills angezeigt.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Um einen Kontonamen basierend auf dem Anzeigenamen des Benutzers zu entfernen, verwenden Sie die folgenden Befehle:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Wenn Sie ein Benutzerkonto mit dem Microsoft Azure AD-Modul für Windows PowerShell löschen, wird das Konto nicht endgültig gelöscht. Sie können das gelöschte Benutzerkonto innerhalb von 30 Tagen wiederherstellen.

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


Wenn Sie ein Benutzerkonto löschen möchten, verwenden Sie die folgende Syntax:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

In diesem Beispiel wird das Benutzerkonto „BelindaN@litwareinc.com“ gelöscht.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Wenn Sie ein gelöschtes Benutzerkonto innerhalb der Nachfrist von 30 Tagen wiederherstellen möchten, verwenden Sie die folgende Syntax:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

In diesem Beispiel wird das gelöschte Benutzerkonto „BelindaN@litwareinc.com“ wiederhergestellt.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Hinweise:**
  
- Um die Liste der gelöschten Benutzer anzuzeigen, die wiederhergestellt werden können, führen Sie den folgenden Befehl aus:
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Wenn der ursprüngliche Benutzerprinzipalnamen des Benutzerkontos durch ein anderes Konto verwendet wird, verwenden Sie den _NewUserPrincipalName_-Parameter anstelle von _UserPrincipalName_, um einen anderen Benutzerprinzipalnamen anzugeben, wenn Sie das Benutzerkonto wiederherstellen.


## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

