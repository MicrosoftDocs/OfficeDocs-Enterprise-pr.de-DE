---
title: Blockieren von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Blockieren von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie mithilfe von Office 365 PowerShell blockieren und zulassen einzelner Zugriff auf Office 365-Konten.
  
Zugriff auf Office 365-Konto blockiert verhindert, dass jeder Benutzer mit dem Konto anzumelden und Zugriff auf die Dienste und Daten in Office 365-Organisation. Wenn Sie Zugriff auf das Konto blockieren, erhält der Benutzer die folgende Fehlermeldung angezeigt, wenn sie versuchen, melden Sie sich:
  
![Gesperrtes Office 365-Konto.](images/o365_powershell_account_blocked.png)
  
Office 365 PowerShell können Sie um Zugriff auf einzelne und mehrere Benutzerkonten zu blockieren.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Wenn Sie ein Benutzerkonto blockieren, kann es bis zu 24 Stunden auf Geräten und Clients des Benutzers wirksam dauern.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Sie können den Zugriff auf einzelne Benutzerkonten mit Office 365 PowerShell blockieren.

Verwenden Sie die folgende Syntax, um den Zugriff auf ein einzelnes Benutzerkonto zu blockieren:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Führen Sie zum Aufheben der Blockierung des Benutzerkontos den folgenden Befehl aus:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Verwenden von Office 365 PowerShell den Zugriff auf mehrere Benutzerkonten blockieren

Erstellen Sie zunächst eine Textdatei mit einem Konto in jeder Zeile wie folgt:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
In den folgenden Befehlen wird die Text-Beispieldatei C:\My Documents\Accounts.txt. Ersetzen Sie Sie durch den Pfad und den Namen der Textdatei.
    
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Blockieren des Zugriffs auf Benutzerkonten mit dem Azure Active Directory V2 PowerShell-Modul

Um das Cmdlet **New-AzureADUser** aus dem Azure Active Directory V2 PowerShell-Modul zu verwenden, müssen Sie zunächst eine Verbindung zu Ihrem Abonnement herstellen. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
Nachdem Sie eine Verbindung hergestellt haben, verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu blockieren:
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Der Parameter „-ObjectID“ im Cmdlet  „Set-AzureAD“ akzeptiert entweder den Kontonamen, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos. 
  
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
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In diesem Beispiel wird das Benutzerkonto UPN für den Benutzer mit dem Namen Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Um einen Kontonamen basierend auf dem Namen des Benutzers zu blockieren, verwenden Sie die folgenden Befehle:
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Zu einem beliebigen Zeitpunkt können Sie die Sperrung eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Um Zugriff auf mehrere Benutzerkonten zu blockieren, erstellen Sie eine Textdatei mit einer Kontoname für jede Zeile wie folgt:
    
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

## <a name="see-also"></a>Siehe auch
<a name="SeeAlso"> </a>

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

