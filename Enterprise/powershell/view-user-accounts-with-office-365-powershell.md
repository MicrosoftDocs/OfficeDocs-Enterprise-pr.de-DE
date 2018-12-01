---
title: Anzeigen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Zusammenfassung: Anzeigen, Liste oder Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell anzuzeigen.'
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123252"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Anzeigen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Zeigen Sie Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell.
  
Obwohl Sie das Office 365 Admin Center zum Anzeigen von Konten für Ihre Office 365-Mandanten verwenden können, können Sie auch mithilfe von Office 365 PowerShell und führen Sie einige Dinge, die die Office 365-Verwaltungskonsole kann nicht.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a>Office 365 Benutzerkontoinformationen mit Azure Active Directory PowerShell für Diagramm anzeigen 

In den folgenden Abschnitten wird beschrieben, wie Benutzerkontoinformationen angezeigt.

### <a name="all-accounts"></a>Alle Konten

Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl aus:
  
```
Get-AzureADUser
```

Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="a-specific-account"></a>Ein bestimmtes Konto

Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Benutzerprinzipalnamen (UPN) des Benutzerkontos, entfernen Sie die "<" und ">" Zeichen, und führen Sie diesen Befehl:
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a>Zusätzliche Eigenschaftswerte für ein bestimmtes Konto

Standardmäßig zeigt das Cmdlet **Get-AzureADUser** nur die ObjectID, DisplayName und UserPrincipalName Eigenschaften von Konten.

Um weitere werden selektive über die Liste der Eigenschaften für die Anzeige das **Select-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-AzureADUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", weist Azure Active Directory PowerShell für die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl Grafik. Hier ist ein Beispielbefehl, der die DisplayName, Abteilung und usagelocation-Wert angegeben für jedes Benutzerkonto angezeigt wird:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).
  
Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Als weiteres Beispiel können Sie den Aktivierungsstatus eines bestimmten Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a>Einige Benutzerkonten basierend auf einer gemeinsamen Eigenschaft

Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-AzureADUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", weist Azure Active Directory PowerShell für die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl Grafik. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl weist Azure Active Directory PowerShell für Diagramm an:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( ** $ \_. Usagelocation-Wert angegeben** ) ist nicht angegebenen ( **-Eq $Null** ).
    
Die **usagelocation-Wert angegeben** -Eigenschaft ist nur eine viele Eigenschaften mit einem Benutzerkonto verknüpft. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**. > [Vergleichsoperator] **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen ist.  [Wert] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), einen numerischen Wert oder **$Null** für nicht spezifizierte > Weitere Informationen finden Sie in [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) .
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a>Anzeigen von Office 365 Benutzerkontoinformationen mit Microsoft Azure Active Directory-Modul für Windows PowerShell

In den folgenden Abschnitten wird beschrieben, wie Benutzerkontoinformationen angezeigt.

### <a name="all-accounts"></a>Alle Konten

Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl aus:
  
```
Get-MsolUser
```

Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Das Cmdlet **Get-MsolUser** verfügt über eine Reihe von Parametern für das Filtern der Benutzerkonten angezeigt. Führen Sie beispielsweise die Liste der nicht lizenzierten Benutzer (Benutzer, die zu Office 365 hinzugefügt wurden, aber noch nicht noch lizenziert wurden, um die Dienste zu verwenden), diesen Befehl.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Weitere Informationen zu weiteren Parametern zum Filtern der Anzeige der Satz von Benutzerkonten angezeigt wird, finden Sie unter [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="a-specific-account"></a>Ein bestimmtes Konto

Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Benutzerprinzipalnamen (UPN) des Benutzerkontos, entfernen Sie die "<" und ">" Zeichen, und führen Sie diesen Befehl:
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a>Einige Benutzerkonten basierend auf einer gemeinsamen Eigenschaft

Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-MsolUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", Office 365 PowerShell die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl weist. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( ** $ \_. Usagelocation-Wert angegeben** ) ist nicht angegebenen ( **-Eq $Null** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Die **usagelocation-Wert angegeben** -Eigenschaft ist nur eine viele Eigenschaften mit einem Benutzerkonto verknüpft. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (*) an alle für ein bestimmtes Benutzerkonto. Es folgt ein Beispiel:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**.  [Vergleichsoperator] ist **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen.  [Wert] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), einen numerischen Wert oder **$Null** für nicht spezifizierte. Weitere Informationen finden Sie unter [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Sie können den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a>Zusätzliche Eigenschaftswerte für Konten

Das Cmdlet **Get-MsolUser** Standardmäßig zeigt drei Eigenschaften von Benutzerkonten:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Wenn zusätzliche Eigenschaften, wie die Abteilung für der Benutzer funktioniert und Land/Region, in dem der Benutzer Office 365-Dienste verwendet, werden sollen, können Sie **Get-MsolUser** in Kombination mit dem **Select-Object** -Cmdlet zum Angeben der Liste der Benutzerkonto ausführen Eigenschaften. Es folgt ein Beispiel:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

Das **Select-Object** -Cmdlet können Sie die Eigenschaften wählen, die Sie einen Befehl anzeigen möchten. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das Platzhalterzeichen (*) für ein bestimmtes Benutzerkonto alle anzeigen. Es folgt ein Beispiel:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Um die Liste der anzuzeigenden Konten noch weiter einzuschränken, können Sie auch das **Where-Object**-Cmdlet verwenden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ). In die geschweiften Klammern sein, der Befehl fordert Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( ** $ \_. Usagelocation-Wert angegeben** ) ist nicht angegebenen ( **-Eq $Null** ).
    
- Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Wenn Sie zum Erstellen und Verwalten von Office 365-Benutzer verzeichnissynchronisierung verwenden, können Sie das lokales Konto anzeigen von Office 365-Benutzer hochgerechnet wurde hat. Im folgenden wird davon ausgegangen, dass Azure AD-Connect konfiguriert wurde, um die standardmäßige Quelle Verankerung des Objekt-GUID verwenden (Weitere Informationen zum Konfigurieren eines Quelle Anker finden Sie unter [Azure AD-Connect: Entwerfen Konzepte](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) und setzt voraus, dass die Active Directory-Moduls für Powershell hat wurde installiert (siehe [RSAT-Tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

