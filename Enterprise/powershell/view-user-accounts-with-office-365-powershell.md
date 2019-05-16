---
title: Anzeigen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Zusammenfassung: anzeigen, auflisten oder Anzeigen Ihrer Benutzerkonten mit Office 365 PowerShell.'
ms.openlocfilehash: e1a99aef4f2045dcba8d7f3894ef82f9e7c36a15
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071101"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Anzeigen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Zeigen Sie Ihre Benutzerkonten auf verschiedene Weise mit Office 365 PowerShell an.
  
Sie können zwar das Office 365 Admin Center verwenden, um die Konten für Ihren Office 365-Mandanten anzuzeigen, Sie können aber auch Office 365 PowerShell verwenden und einige Dinge tun, die das Office 365 Admin Center nicht kann.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Alle Konten anzeigen

Führen Sie den folgenden Befehl aus, um die vollständige Liste der Benutzerkonten anzuzeigen:
  
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

### <a name="view-a-specific-account"></a>Anzeigen eines bestimmten Kontos

Wenn Sie ein bestimmtes Benutzerkonto anzeigen möchten, geben Sie den Anmeldekontonamen des Benutzerkontos ein, das auch als Benutzerprinzipalname (UPN) bezeichnet wird, entfernen Sie die Zeichen "<" und ">", und führen Sie den folgenden Befehl aus:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Es folgt ein Beispiel:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Anzeigen zusätzlicher Eigenschaftswerte für ein bestimmtes Konto

Standardmäßig werden mit dem Cmdlet **Get-AzureADUser** nur die Eigenschaften ObjectID, DisplayName und userPrincipalName der Konten angezeigt.

Um die Liste der anzuzeigenden Eigenschaften selektiver zu machen, können Sie das Cmdlet **Select-Object** in Kombination mit dem Cmdlet **Get-AzureADUser** verwenden. Zur Kombination der beiden Cmdlets verwenden wir das Zeichen "Pipe" (|), das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden. Hier ist ein Beispielbefehl, in dem die DisplayName-, Department-und UsageLocation für jedes Benutzerkonto angezeigt werden:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Dieser Befehl gibt Office 365 Powershell die folgenden Anweisungen:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Zeigt nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort an ( **Select-Object DisplayName, Department, UsageLocation** ).
  
Um alle Eigenschaften für Benutzerkonten anzuzeigen, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (*), um Sie für ein bestimmtes Benutzerkonto anzuzeigen. Es folgt ein Beispiel:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Als weiteres Beispiel können Sie den aktivierten Status eines bestimmten Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft

Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-AzureADUser**-Cmdlets zusammen verwenden. Zur Kombination der beiden Cmdlets verwenden wir das Zeichen "Pipe" (|), das Azure Active Directory PowerShell für Graph anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl weist Azure Active Directory PowerShell für Graph Folgendes zu:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-AzureADUser**) und an den nächsten Befehl senden (**|**).
    
- Suchen aller Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur die Konten zu finden, in denen die UsageLocation-Benutzerkonto Eigenschaft ( ** $ \_. UsageLocation** ) ist nicht angegeben ( **-EQ $NULL** ).
    
Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist. Um alle Eigenschaften für Benutzerkonten anzuzeigen, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (*), um Sie für ein bestimmtes Benutzerkonto anzuzeigen. Hier ein Beispiel:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für das **Where-Object-** Cmdlet, das in diesen Beispielen gezeigt wird **, ist\_Where-Object {$.** [Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**. > [Vergleichsoperator] is **-EQ** für Equals, **-ne** für ungleich, **-lt** für kleiner als, **-gT** für größer als und andere.  [value] ist in der Regel eine Zeichenfolge (eine Folge von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für unspecified> finden Sie unter [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) Weitere Informationen.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Verbinden Sie sich zuerst [mit Ihrem Office 365-Mandanten](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Alle Konten anzeigen

Führen Sie den folgenden Befehl aus, um die vollständige Liste der Benutzerkonten anzuzeigen:
  
```
Get-MsolUser
```

Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Das **Get-MsolUser**-Cmdlet verfügt darüber hinaus über eine Reihe von Parametern zum Filtern der angezeigten Benutzerkonten. Führen Sie beispielsweise diesen Befehl aus, um die Liste der nicht lizenzierten Benutzer (Benutzer, die Office 365 hinzugefügt wurden, aber noch nicht für die Verwendung einer der Dienste lizenziert wurden) zu verwenden.
  
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

Weitere Informationen zu weiteren Parametern zum Filtern der angezeigten Benutzerkonten finden Sie unter [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Anzeigen eines bestimmten Kontos

Um ein bestimmtes Benutzerkonto anzuzeigen, geben Sie den Anmeldenamen des Benutzerkontos des Benutzerkontos ein, das auch als Benutzerprinzipalname (UPN) bezeichnet wird, entfernen Sie die Zeichen "<" und ">", und führen Sie den folgenden Befehl aus:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Anzeigen einiger Konten basierend auf einer gemeinsamen Eigenschaft

Um die Liste der angezeigten Konten weiter einzugrenzen, können Sie die **Where-Object**- und **Get-MsolUser**-Cmdlets zusammen verwenden. Zur Kombination der beiden Cmdlets verwenden wir das Zeichen "Pipe" (|), das Office 365 PowerShell anweist, die Ergebnisse eines Befehls zu übernehmen und an den nächsten Befehl zu senden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Suchen aller Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur die Konten zu finden, in denen die UsageLocation-Benutzerkonto Eigenschaft ( ** $ \_. UsageLocation** ) ist nicht angegeben ( **-EQ $NULL** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Die **UsageLocation**-Eigenschaft ist nur eine von vielen Eigenschaften, die einem Benutzerkonto zugeordnet ist. Um alle Eigenschaften für Benutzerkonten anzuzeigen, verwenden Sie das Cmdlet **Select-Object** und das Platzhalterzeichen (*), um Sie für ein bestimmtes Benutzerkonto anzuzeigen. Hier ein Beispiel:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

In dieser Liste steht das **City**-Objekt für den Namen einer Benutzerkontoeigenschaft. Dies bedeutet, dass Sie mit dem folgenden Befehl eine Liste aller Benutzerkonten für Benutzer, die in London leben, anzeigen können:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  Die Syntax für das **Where-Object-** Cmdlet, das in diesen Beispielen gezeigt wird **, ist\_Where-Object {$.** [Name der Benutzerkonten Eigenschaft] [Vergleichsoperator] Wert **}**.  [Vergleichsoperator] is **-EQ** für Equals, **-ne** für ungleich, **-lt** für kleiner als, **-gt** für größer als und andere.  [value] ist in der Regel eine Zeichenfolge (eine Folge von Buchstaben, Zahlen und anderen Zeichen), ein numerischer Wert oder **$null** für nicht angegeben. Weitere Informationen finden Sie unter [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Sie können den blockierten Status eines Benutzerkontos mit dem folgenden Befehl überprüfen:
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Anzeigen zusätzlicher Eigenschaftswerte für Konten

Das Cmdlet **Get-MsolUser** zeigt standardmäßig drei Eigenschaften von Benutzerkonten an:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Wenn Sie zusätzliche Eigenschaften benötigen, beispielsweise die Abteilung, für die der Benutzer arbeitet, und das Land/die Region, in der der Benutzer Office 365-Dienste verwendet, können Sie **Get-MsolUser** in Kombination mit dem **Select-Object-** Cmdlet ausführen, um die Liste der Benutzerkonten anzugeben. Eigenschaften. Es folgt ein Beispiel:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Zeigt nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort an ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

Mit dem **Select-Object-** Cmdlet können Sie die Eigenschaften auswählen, die von einem Befehl angezeigt werden sollen. Um alle Eigenschaften für Benutzerkonten anzuzeigen, verwenden Sie das Platzhalterzeichen (*), um Sie für ein bestimmtes Benutzerkonto anzuzeigen. Es folgt ein Beispiel:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Um die Liste der anzuzeigenden Konten noch weiter einzuschränken, können Sie auch das **Where-Object**-Cmdlet verwenden. Nachfolgend ist ein Beispielbefehl aufgeführt, mit dem nur die Benutzerkonten angezeigt werden, die über einen nicht angegebenen Verwendungsstandort verfügen:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Dieser Befehl weist Office 365 PowerShell zu folgenden Aktionen an:
  
- Alle Informationen der Benutzerkonten abrufen (**Get-MsolUser**) und an den nächsten Befehl senden (**|**).
    
- Suchen aller Benutzerkonten mit einem nicht angegebenen Verwendungs Speicherort ( **Where-Object {\_$. UsageLocation-EQ $NULL}** ), und senden Sie die resultierenden Informationen an den **|** nächsten Befehl (). Innerhalb der geschweiften Klammern weist der Befehl Office 365 PowerShell an, nur die Konten zu finden, in denen die UsageLocation-Benutzerkonto Eigenschaft ( ** $ \_. UsageLocation** ) ist nicht angegeben ( **-EQ $NULL** ).
    
- Zeigt nur den Namen des Benutzerkontos, die Abteilung und den Verwendungs Speicherort an ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Es sollten Informationen ähnlich den folgenden angezeigt werden:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Wenn Sie die Verzeichnissynchronisierung zum Erstellen und Verwalten Ihrer Office 365-Benutzer verwenden, können Sie anzeigen, aus welchem lokalen Konto ein Office 365-Benutzer stammt. Es wird davon ausgegangen, dass Azure AD Connect für die Verwendung des standardmäßigen Quell Ankers von objectGUID konfiguriert wurde (Weitere Informationen zum Konfigurieren eines Quell Ankers finden Sie unter [Azure AD Connect: Design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)), und es wird davon ausgegangen, dass das Active Directory-Modul für PowerShell installiert (siehe [Remote-Tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>Siehe auch

[Verwalten von Benutzerkonten und Lizenzen mit Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Verwalten von Office 365 mit Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Erste Schritte mit Office 365 PowerShell](getting-started-with-office-365-powershell.md)

