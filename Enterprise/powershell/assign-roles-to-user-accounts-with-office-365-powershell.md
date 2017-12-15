---
title: Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell
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
- DecEntMigration
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell und des Add-MsolRoleMember -Cmdlets zum Zuweisen von Rollen zu Benutzerkonten.'
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell und das Cmdlet **Add-MsolRoleMember** Benutzerkonten Rollen zugewiesen.
  
Sie können schnell und einfach Rollen-Benutzerkonten mit Office 365 PowerShell durch das Identifizieren von Anzeigename den Namen des Benutzerkontos und den Namen des Rollen zuweisen.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen:

Für die Verfahren in diesem Thema müssen Sie mithilfe eines globalen Administratorkontos eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Bei einer einzelnen Rollenänderung

Legen Sie Folgendes fest:
  
- Das Benutzerkonto, das Sie konfigurieren möchten.
    
    Um das Benutzerkonto angeben, müssen Sie den Anzeigenamen ermitteln. Wenn Sie eine vollständige Liste Konten erhalten möchten, verwenden Sie diesen Befehl aus:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Mit diesem Befehl wird der Anzeigename der Benutzerkonten nach Anzeigename sortiert angezeigt, jeweils einer auf einem Bildschirm. Sie können die Liste mit dem **Where** -Cmdlets weiter eingrenzen. Hier ein Beispiel:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John" beginnt.
    
- Die Rolle, die Sie zuweisen möchten.
    
    Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Nachdem Sie den Anzeigenamen des Kontos und den Namen der Rolle bestimmt haben, verwenden Sie die folgenden Befehle, um dem Konto die Rolle zuzuweisen:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Kopieren Sie die Befehle aus, und fügen sie in Notepad ein. Ersetzen Sie den Text der Beschreibung für die Variablen **$dispName** und **$roleName** mit ihren Werten, entfernen Sie die \< und > Zeichen, und lassen Sie die Anführungszeichen. Kopieren Sie die geänderten Zeilen, und fügen Sie sie in das Windows Azure Active Directory-Modul für Windows PowerShell-Fenster ausführen. Alternativ können Sie die Windows PowerShell Integrated Skript Environment (ISE).
  
Hier ein Beispiel für einen abgeschlossenen Befehlssatz:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Bei mehreren Rollenänderungen

Legen Sie Folgendes fest:
  
- Die Benutzerkonten, die Sie konfigurieren möchten.
    
    Beim Angeben des Benutzerkontos müssen Sie seinen Anzeigenamen bestimmen. Verwenden Sie den folgenden Befehl, um eine Liste der Konten abzurufen:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Mit diesem Befehl wird der Anzeigename des alle Ihre Benutzerkonten, sortiert nach den Anzeigenamen, ein Fenster zu einem Zeitpunkt aufgeführt. Sie können die Liste auf einer kleineren Gruppe mithilfe des Cmdlets **, in dem** filtern. Es folgt ein Beispiel:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Mit diesem Befehl werden nur die Benutzerkonten angezeigt, deren Anzeigename mit „John" beginnt.
    
- Rollen, die Sie jedem Benutzerkonto zuweisen möchten.
    
    Um die Liste der verfügbaren Rollen anzuzeigen, die Benutzerkonten zugeordnet werden können, verwenden Sie den folgenden Befehl:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Erstellen Sie im nächsten Schritt eine durch Trennzeichen getrennte Textdatei (CSV) mit Anzeigenamen und Rollennamen. Hier ein Beispiel:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

Geben Sie anschließend den Speicherort der CSV-Datei an, und führen Sie die resultierenden Befehle in der PowerShell-Eingabeaufforderung aus.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>See also

#### 

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)
#### 

[Add-MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

