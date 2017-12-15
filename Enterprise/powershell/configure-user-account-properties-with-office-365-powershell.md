---
title: Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell
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
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Zusammenfassung: Informationen zum Verwenden von Office 365 PowerShell zum Konfigurieren der Eigenschaften für einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten."
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell

 **Zusammenfassung:** Verwenden Sie Office 365 PowerShell zum Konfigurieren von Eigenschaften des einzelne oder mehrere Benutzerkonten in Ihrem Office 365-Mandanten.
  
Zwar können Sie das Office 365 Admin Center zum Konfigurieren der Eigenschaften für die Benutzerkonten Ihres Office 365-Mandanten verwenden, mit Office 365 PowerShell können Sie jedoch zusätzlich weitere Aktionen durchführen, die mit dem Office 365 Admin Center nicht möglich sind.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Ändern von Eigenschaften für ein bestimmtes Benutzerkonto

Verwenden Sie zum Konfigurieren der Eigenschaften für ein bestimmtes das [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx)-Cmdlet, und geben die Eigenschaften an, die festgelegt oder geändert werden sollen. In diesem Beispiel ändert der Befehl den Verwendungsstandort von Belinda Newman in Frankreich:
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Sie identifizieren das Konto mit dem **-UserPrincipalName** -Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.
  
- -Stadt "\<Ortsname >"
    
- -Land "\<Land Name >"
    
- -Abteilung "\<Abteilungsnamen >"
    
- DisplayName-"\<vollständige Benutzername >"
    
- -Fax "\<Faxnummer >"
    
- -FirstName "\<Vorname Benutzer >"
    
- LastName-"\<letzten Benutzername >"
    
- -MobilePhone "\<Mobiltelefonnummer >"
    
- -Office "\<Bürostandort >"
    
- PhoneNumber-"\<Office Rufnummer >"
    
- PostalCode-"\<Postleitzahl >"
    
- -PreferredLanguage "\<Sprache >"
    
- -Status "\<Zustand Name >"
    
- StreetAddress-"\<Straße >"
    
- -Title "\<Titel Name >"
    
- -Usagelocation-Wert angegeben "\<2-Land oder Region Zeichencode >"
    
    Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).
    
Informationen zu weiteren Parametern finden Sie unter [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx).
  
Führen Sie den folgenden Befehl aus, um die Benutzerprinzipalnamen aller Benutzer anzuzeigen.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Die Liste der User Principal Names alphabetisch sortieren ( **Sort-Objekt UserPrincipalName** ) und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).
    
- Jeweils auf einem Bildschirm anzeigen ( **More** ).
    
Mit diesem Befehl werden alle Konten aufgelistet. Wenn Sie die User Principal Name für ein Konto basierend auf deren Anzeige anzeigen möchten name (vor- und Nachname), füllen Sie die unten aufgeführten **$userName** -Variable (Entfernen der \< und > Zeichen), und führen Sie dann die folgenden Befehle aus:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Ändern von Eigenschaften für alle Benutzerkonten

Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Ändern von Eigenschaften für bestimmte Benutzerkonten

Um die Eigenschaften für einen bestimmten Satz von Benutzerkonten zu ändern, können Sie eine Kombination der Cmdlets **Get-MsolUser**, **Where-Object** und **Set-MsolUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in der Buchhaltungsabteilung in Frankreich geändert:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-MsolUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Hier finden Sie alle Benutzerkonten, die ihre Abteilung-Eigenschaft auf "Accounting" festgelegt ( **Where-Object {$_. Abteilung - Eq "Accounting"}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ).
    
- Benutzerstandort auf „Frankreich" festlegen ( **Set-MsolUser -UsageLocation "FR"** ).
    
- Jeweils auf einem Bildschirm anzeigen ( **More** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Konfigurieren der Benutzerkontoeigenschaften mit dem Azure Active Directory V2 PowerShell-Modul

Um die Eigenschaften für Benutzerkonten mit Azure Active Directory V2 PowerShell-Modul konfigurieren möchten, verwenden Sie das Cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) und geben Sie die Eigenschaften zum Festlegen oder ändern. Aber Sie müssen Sie zuerst zu Ihrem Abonnement verbinden. Die Anweisungen finden Sie unter [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Ändern von Eigenschaften für ein bestimmtes Benutzerkonto

Mit diesem Beispielbefehl wird der Verwendungsstandort von Belinda Newman in Frankreich geändert:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Sie identifizieren das Konto mit dem **-ObjectID** -Parameter und legen bestimmte Eigenschaften mit weiteren Parametern fest bzw. ändern diese. Nachfolgend ist eine Liste der am häufigsten verwendeten Parameter aufgeführt.
  
- -Abteilung "\<Abteilungsnamen >"
    
- DisplayName-"\<vollständige Benutzername >"
    
- -FacsimilieTelephoneNumber "\<Faxnummer >"
    
- -Vorname "\<Vorname Benutzer >"
    
- -Nachname "\<letzten Benutzername >"
    
- -Mobile "\<Mobiltelefonnummer >"
    
- JobTitle-"\<Position >"
    
- -PreferredLanguage "\<Sprache >"
    
- StreetAddress-"\<Straße >"
    
- -Stadt "\<Ortsname >"
    
- -Status "\<Zustand Name >"
    
- PostalCode-"\<Postleitzahl >"
    
- -Land "\<Land Name >"
    
- -TelephoneNumber "\<Office Rufnummer >"
    
- -Usagelocation-Wert angegeben "\<2-Land oder Region Zeichencode >"
    
    Dies ist der zweistellige ISO 3166-1-Ländercode bzw. Regionscode (Alpha-2, A2).
    
Informationen zu weiteren Parametern finden Sie unter [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0).
  
Um die User Principal Name für Ihre Benutzerkonten anzuzeigen, führen Sie den folgenden Befehl aus.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Die Liste der User Principal Names alphabetisch sortieren ( **Sort-Objekt UserPrincipalName** ) und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Nur die UserPrincipalName-Eigenschaft für jedes Konto anzeigen ( **Select-Object UserPrincipalName** ).
- Jeweils auf einem Bildschirm anzeigen ( **More** ).
    
Mit diesem Befehl werden alle Konten aufgelistet. Wenn Sie die User Principal Name für ein Konto basierend auf deren Anzeige anzeigen möchten name (vor- und Nachname), füllen Sie die unten aufgeführten **$userName** -Variable (Entfernen der \< und > Zeichen), und führen Sie dann die folgenden Befehle aus:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

In diesem Beispiel wird der Benutzerprinzipalname für den Benutzer namens Caleb Sills angezeigt.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mit der **$upn** -Variable können Sie Änderungen an den einzelnen Konten basierend auf deren Anzeigenamen vornehmen. Hier ist ein Beispiel für das Festlegen des Verwendungsstandorts von Belinda Newman in Frankreich. Dabei wird Ihr Anzeigenamen anstatt Ihres Benutzerprinzipalnamens verwendet:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Ändern von Eigenschaften für alle Benutzerkonten

Um die Eigenschaften für alle Benutzer zu ändern, können Sie eine Kombination der Cmdlets **Get-AzureADUser** und **et-AzureADUser** verwenden. Im folgende Beispiel wird der Verwendungsstandort für alle Benutzer in Frankreich geändert:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Benutzerstandort auf „Frankreich" festlegen ( **Set-AzureADUser -UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Ändern von Eigenschaften für bestimmte Benutzerkonten

Um Eigenschaften für eine bestimmte Gruppe von Benutzerkonto zu ändern, können Sie die Kombination aus den Cmdlets **Get-AzureADUser**, **wobei**und **Set-AzureADUser** verwenden. Im folgenden Beispiel wird den Verwendungsspeicherort für alle Benutzer in der Buchhaltung in Frankreich geändert:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen für die Benutzerkonten ( **Get-AzureADUser** ) abrufen und senden Sie sie an den nächsten Befehl ( **|** ).
    
- Hier finden Sie alle Benutzerkonten, die die Abteilung-Eigenschaft auf "Buchhaltung" festgelegt werden ( **, in dem {$_. Abteilung - Eq "Accounting"}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ).
    
- Benutzerstandort auf „Frankreich" festlegen ( **Set-AzureADUser -UsageLocation "FR"** ).
    
## <a name="see-also"></a>See also

#### 

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

