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
description: Erläutert, wie Office 365 PowerShell zum Blockieren und Aufheben des Zugriffs auf Office 365-Konten verwendet wird.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491391"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Blockieren von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:**  Erläutert, wie Office 365 PowerShell zum Blockieren und Aufheben des Zugriffs auf Office 365-Konten verwendet wird.
  
Das Blockieren des Zugriffs auf ein Office 365-Konto verhindert, dass sich ein Benutzer mit dem Konto anmelden und auf die Dienste und Daten in Ihrer Office 365-Organisation zugreifen kann. Sie können Office 365 PowerShell verwenden, um den Zugriff auf einzelne und mehrere Benutzerkonten zu blockieren.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Zugriff auf einzelne Benutzerkonten blockieren

Verwenden Sie die folgende Syntax, um ein einzelnes Benutzerkonto zu blockieren:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Der Parameter-ObjectID im Cmdlet Set-AzureAD akzeptiert entweder den Anmeldenamen des Kontos, der auch als Benutzerprinzipalname bezeichnet wird, oder die Objekt-ID des Kontos. 
  
Dieses Beispiel blockiert den Zugriff auf das Benutzerkonto „fabricec@litwareinc.com“.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Führen Sie zum Aufheben der Blockierung dieses Benutzerkontos den folgenden Befehl aus:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Verwenden Sie die folgenden Befehle, um das Benutzerkonto UPN basierend auf dem Anzeigenamen des Benutzers anzuzeigen:
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

In diesem Beispiel wird das Benutzerkonto UPN für den Benutzernamens Caleb Sills angezeigt.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Verwenden Sie die folgenden Befehle, um ein Konto basierend auf dem Anzeigenamen des Benutzers zu blockieren:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Sie können jederzeit den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Zugriff auf mehrere Benutzerkonten blockieren

Um den Zugriff auf mehrere Benutzerkonten zu blockieren, erstellen Sie eine Textdatei, die einen Konto Anmeldenamen in jeder Zeile wie folgt enthält:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

In den folgenden Befehlen ist die Beispieltextdatei C:\My Documents\accounts.txt Ersetzen Sie dies durch den Pfad und den Dateinamen der Textdatei.
  
Um den Zugriff auf die in der Textdatei aufgelisteten Konten zu blockieren, führen Sie den folgenden Befehl aus:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Um den Zugriff auf die in der Textdatei aufgelisteten Konten wieder freizugeben, führen Sie den folgenden Befehl aus:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Zugriff auf einzelne Benutzerkonten blockieren

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

Sie können jederzeit den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Zugriff auf mehrere Benutzerkonten blockieren

Erstellen Sie zunächst eine Textdatei, die in jeder Zeile wie folgt ein Konto enthält:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
In den folgenden Befehlen ist die Beispieltextdatei C:\My Documents\accounts.txt Ersetzen Sie dies durch den Pfad und den Dateinamen der Textdatei.
    
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
