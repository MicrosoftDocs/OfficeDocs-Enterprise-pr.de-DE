---
title: Anzeigen von Benutzerkonten mit Office 365 PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Zusammenfassung: Anzeigen, Liste oder Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell anzuzeigen.'
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Anzeigen von Benutzerkonten mit Office 365 PowerShell

 **Zusammenfassung:** Anzeigen, Liste oder Ihre Benutzerkonten auf verschiedene Arten mit Office 365 PowerShell anzuzeigen.
  
Obwohl Sie das Office 365 Admin Center zum Anzeigen von Konten für Ihre Office 365-Mandanten verwenden können, können Sie auch mithilfe von Office 365 PowerShell und führen Sie einige Dinge, die die Office 365-Verwaltungskonsole kann nicht.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Anzeigen von Office 365-Benutzerkontoinformationen

Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl in Ihrer Office 365 PowerShell-Eingabeaufforderung oder PowerShell Integrated Skript Environment (ISE).
  
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

Weitere Informationen zu weiteren Parametern zum Filtern der Anzeige der Satz von Benutzerkonten angezeigt wird, finden Sie unter [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-MsolUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", Office 365 PowerShell die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl weist. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
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

Beispielsweise ist **Ort** aus dieser Liste der Name der Benutzereigenschaft Konto. Dies bedeutet, dass Sie den folgenden Befehl verwenden können, um eine Liste der Benutzerkonten für Benutzer, die in London leben anzuzeigen:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**. > [Vergleichsoperator] wird **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen > [] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), eine ohne Angabe dieses Parameters numerischen Wert oder **$Null** für > Weitere Informationen finden Sie in [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Sie können den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Auswählen der anzuzeigenden Benutzerkontoeigenschaften

Das Cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) Standardmäßig zeigt drei Eigenschaften von Benutzerkonten:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Wenn zusätzliche Eigenschaften, wie die Abteilung für der Benutzer funktioniert und Land/Region, in dem der Benutzer Office 365-Dienste verwendet, werden sollen, können Sie **Get-MsolUser** in Kombination mit dem **Select-Object** -Cmdlet zum Angeben der Liste der Benutzerkonto ausführen Eigenschaften. Es folgt ein Beispiel:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
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
David Longmuir      Operations                               US
Scott Wallace            Operations
```

Das **Select-Object** -Cmdlet können Sie die Eigenschaften wählen, die Sie einen Befehl anzeigen möchten. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das Platzhalterzeichen (*) für ein bestimmtes Benutzerkonto alle anzeigen. Es folgt ein Beispiel:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Um weitere werden zu der Liste der Konten, die für die Anzeige von selektive auch das Cmdlet **Where-Object** können Sie. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
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

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Anzeigen von Benutzerkonten mit dem Azure Active Directory V2 PowerShell-Modul

Um Eigenschaften für Benutzerkonten mit Azure Active Directory V2 PowerShell-Modul anzuzeigen, verwenden Sie das Cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Aber Sie müssen Sie zuerst zu Ihrem Abonnement verbinden. Die Anweisungen finden Sie unter[Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Anzeigen von Office 365-Benutzerkontoinformationen

Um die vollständige Liste der Benutzerkonten anzuzeigen, führen Sie diesen Befehl in Ihrer Office 365 PowerShell-Eingabeaufforderung oder PowerShell Integrated Skript Environment (ISE).
  
```
Get-AzureADUser
```

Das Cmdlet **Get-AzureADUser** Standardmäßig zeigt drei Eigenschaften von Benutzerkonten:
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Um weitere werden selektive zu der Liste der Konten für die Anzeige das **Where-Object** -Cmdlet in Kombination mit dem Cmdlet **Get-AzureADUser** können Sie. Um die zwei Cmdlets zu kombinieren, verwenden wir das Pipe-Zeichen "|", Office 365 PowerShell die Ergebnisse eines Befehls und senden Sie sie an den nächsten Befehl weist. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( ** $ \_. Usagelocation-Wert angegeben** ) ist nicht angegebenen ( **-Eq $Null** ).
    
Die **usagelocation-Wert angegeben** -Eigenschaft ist nur eine viele Eigenschaften mit einem Benutzerkonto verknüpft. Um alle Eigenschaften für Benutzerkonten angezeigt wird, verwenden Sie das **Select-Object** -Cmdlet und das Platzhalterzeichen (*) an alle für ein bestimmtes Benutzerkonto eine Seite zu einem Zeitpunkt ( **Weitere** ). Es folgt ein Beispiel:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

**Ort** ist beispielsweise der Name der Benutzereigenschaft Konto. Dies bedeutet, dass Sie den folgenden Befehl verwenden können, um eine Liste der Benutzerkonten für Benutzer, die in London leben anzuzeigen:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für die **Where-Object** -Cmdlet in diesen Beispielen dargestellt ist **Where-Object {$\_.** [-Eigenschaft Benutzerkontonamen] [Vergleichsoperator] [Wert] **}**. > [Vergleichsoperator] wird **-Eq** für gleich, **-Ne** für nicht gleich, **-Lt** kleiner als **-Gt** für größer als und anderen > [] wird in der Regel eine Zeichenfolge (eine Sequenz von Buchstaben, Zahlen und andere Zeichen), eine ohne Angabe dieses Parameters numerischen Wert oder **$Null** für > Weitere Informationen finden Sie in[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
### <a name="select-the-user-account-properties-to-display"></a>Auswählen der anzuzeigenden Benutzerkontoeigenschaften

Das Cmdlet **Get-AzureADUser** Standardmäßig werden die ObjectID, DisplayName und UserPrincipalName-Eigenschaften von Benutzerkonten angezeigt. Wenn zusätzliche Eigenschaften, wie die Abteilung für der Benutzer funktioniert und Land/Region, in dem der Benutzer Office 365-Dienste verwendet, werden sollen, können Sie **Get-AzureADUser** in Kombination mit dem **Select-Object** -Cmdlet zum Angeben der Liste der Benutzer ausführen Eigenschaften von Benutzerkonten. Es folgt ein Beispiel:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).
    
Um weitere werden zu der Liste der Konten, die für die Anzeige von selektive auch das Cmdlet **Where-Object** können Sie. Hier ist ein Beispielbefehl, der nur die Benutzerkonten angezeigt werden, die einen Verwendungsspeicherort nicht angegeben ist:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Hier finden Sie alle Benutzerkonten, die einen Verwendungsspeicherort nicht angegeben haben ( **Where-Object {$\_. Usagelocation-Wert angegeben - Eq $Null}** ) und die resultierende Daten mit dem nächsten Befehl senden ( **|** ). In die geschweiften Klammern sein, der Befehl fordert Office 365 PowerShell nur die Gruppe von Konten, die in dem für das usagelocation-Wert angegeben Benutzerkonto Eigenschaft suchen ( ** $ \_. Usagelocation-Wert angegeben** ) ist nicht angegebenen ( **-Eq $Null** ).
    
- Zeigt nur den Benutzer Konto Name, Abteilung und Verwendung Speicherort ( **Select-Object DisplayName, Abteilung, usagelocation-Wert angegeben** ).
    
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Siehe auch

#### 

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

