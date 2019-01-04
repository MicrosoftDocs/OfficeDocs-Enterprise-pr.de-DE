---
title: Blockieren von Benutzerkonten mit Office 365 PowerShell
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546476"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Blockieren von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten.
  
Zugriff auf Office 365-Konto blockiert verhindert, dass jeder Benutzer mit dem Konto anzumelden und Zugriff auf die Dienste und Daten in Office 365-Organisation. Office 365 PowerShell können Sie um Zugriff auf einzelne und mehrere Benutzerkonten zu blockieren.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden von Azure Active Directory PowerShell Graph-Modul

Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Blockieren des Zugriffs auf einzelne Benutzerkonten

Verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto blockieren:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Der Parameter - ObjectID im Cmdlet Set-AzureAD akzeptiert entweder den Anmeldenamen Kontonamen, den User Principal Name, oder das Konto Objekt-ID. 
  
Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Führen Sie zum Aufheben der Blockierung dieses Benutzerkontos den folgenden Befehl aus:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Wenn das Benutzerkonto, den, das Anzeigenamen des Benutzers UPN anhand, anzeigen möchten, verwenden Sie die folgenden Befehle ein:
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In diesem Beispiel wird das Benutzerkonto UPN für den Benutzer mit dem Namen Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Um ein Konto basierend auf den Anzeigenamen des Benutzers zu blockieren, verwenden Sie die folgenden Befehle ein:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Blockieren Sie den Zugriff auf mehrere Benutzerkonten

Um Zugriff auf mehrere Benutzerkonten zu blockieren, erstellen Sie eine Textdatei mit einer Anmeldung Kontoname für jede Zeile wie folgt:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

In den folgenden Befehlen wird die Text-Beispieldatei C:\My Documents\Accounts.txt. Ersetzen Sie Sie durch den Pfad und den Namen der Textdatei.
  
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell

Zuerst [eine Verbindung mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Blockieren des Zugriffs auf einzelne Benutzerkonten

Verwenden Sie die folgende Syntax, um den Zugriff auf ein einzelnes Benutzerkonto zu blockieren:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Führen Sie zum Aufheben der Blockierung des Benutzerkontos den folgenden Befehl aus:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Blockieren Sie den Zugriff auf mehrere Benutzerkonten

Erstellen Sie zunächst eine Textdatei mit einem Konto in jeder Zeile wie folgt:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
In den folgenden Befehlen wird die Text-Beispieldatei C:\My Documents\Accounts.txt. Ersetzen Sie Sie durch den Pfad und den Namen der Textdatei.
    
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
