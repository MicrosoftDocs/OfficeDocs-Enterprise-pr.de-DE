---
title: Blockieren von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Erläutert die Verwendung Office 365 PowerShell zum Blockieren und Aufheben der Blockierung des Zugriffs auf Office 365 Konten.
ms.openlocfilehash: 18c7cea2df2514d7402dfcfd894acc03ed69b1c9
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841692"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Blockieren von Benutzerkonten mit Office 365 PowerShell

Wenn Sie den Zugriff auf ein Office 365 Konto sperren, wird verhindert, dass sich jemand mit dem Konto anmeldet und auf die Dienste und Daten in Ihrer Office 365 Organisation zugreift. Sie können Office 365 PowerShell verwenden, um den Zugriff auf einzelne und mehrere Benutzerkonten zu blockieren.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Blockieren des Zugriffs auf einzelne Benutzerkonten

Verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu blockieren:
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Der Parameter-ObjectID im Cmdlet "AzureAD" akzeptiert entweder den Konto Anmeldenamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos. 
  
Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Führen Sie zum Aufheben der Blockierung dieses Benutzerkontos den folgenden Befehl aus:
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Verwenden Sie die folgenden Befehle, um den UPN des Benutzerkontos basierend auf dem Anzeigenamen des Benutzers anzuzeigen:
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In diesem Beispiel wird das Benutzerkonto UPN für den Benutzernamens Caleb Sills angezeigt.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Verwenden Sie die folgenden Befehle, um ein Konto basierend auf dem Anzeigenamen des Benutzers zu blockieren:
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Sie können den blockierten Status eines Benutzerkontos jederzeit überprüfen, indem Sie den folgenden Befehl ausführen:
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Blockieren des Zugriffs auf mehrere Benutzerkonten

Um den Zugriff auf mehrere Benutzerkonten zu blockieren, erstellen Sie eine Textdatei mit einem Konto-Anmeldenamen in jeder Zeile wie die folgende:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

In den folgenden Befehlen lautet die Beispieltextdatei C:\My documents\accounts.txt Ersetzen Sie dies durch den Pfad und den Dateinamen Ihrer Textdatei.
  
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
### <a name="block-access-to-individual-user-accounts"></a>Blockieren des Zugriffs auf einzelne Benutzerkonten

Verwenden Sie die folgende Syntax, um den Zugriff auf ein einzelnes Benutzerkonto zu blockieren:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen. Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.
>

Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Führen Sie zum Aufheben der Blockierung des Benutzerkontos den folgenden Befehl aus:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Sie können den blockierten Status eines Benutzerkontos jederzeit überprüfen, indem Sie den folgenden Befehl ausführen:
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Blockieren des Zugriffs auf mehrere Benutzerkonten

Erstellen Sie zunächst eine Textdatei mit einem Konto in jeder Zeile wie folgt:
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

In den folgenden Befehlen lautet die Beispieltextdatei C:\My documents\accounts.txt Ersetzen Sie dies durch den Pfad und den Dateinamen Ihrer Textdatei.
    
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten, Lizenzen und Gruppen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
