---
title: Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, LIL_Placement, O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden."
ms.openlocfilehash: 115a708d8def679d43d88e9c83b68ca13dd72fdc
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Office 365 PowerShell zum Entfernen von Office 365-Lizenzen, die Benutzern zuvor zugewiesen wurden.
  
## <a name="before-you-begin"></a>Bevor Sie beginnen

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Zum Anzeigen der Lizenzinformationen Plan ( **AccountSkuID** ) in Ihrer Organisation finden Sie in den folgenden Themen:
    
  - [Anzeigen von Lizenzen und Diensten mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Bei Verwendung des **Get-MsolUser**-Cmdlets ohne den _-All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    
## <a name="the-short-version-instructions-without-explanations"></a>Die Kurzfassung (Anweisungen ohne Erläuterungen)
<a name="ShortVersion"> </a>

In diesem Abschnitt werden die Verfahren kurz und bündig erläutert. Wenn Sie Fragen haben oder weitere Informationen benötigen, können Sie den Rest des Themas lesen.
  
Verwenden Sie die folgende Syntax, um Lizenzen von einem vorhandenen Benutzerkonto zu entfernen:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` Lizenz aus dem Benutzerkonto BelindaN@litwareinc.com (Office 365 Enterprise E3).
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Verwenden Sie eine der folgenden Methoden, um Lizenzen von einer Gruppe von vorhandenen lizenzierten Benutzern zu entfernen,:
  
- **Filtern die anhand eines vorhandenen Attributs Konto Konten** Verwenden Sie dazu die folgende Syntax:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenzen von allen Konten für Benutzer in der Abteilung "Sales" in den USA.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Verwenden einer Liste spezieller Konten** Führen Sie dazu die folgenden Schritte aus:
    
1. Erstellen und speichern Sie eine Textdatei wie die folgende, die in jeder Zeile ein Konto enthält:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Verwenden Sie folgende Syntax:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz von Benutzerkonten in der Textdatei C:\My Documents\Accounts.txt definiert.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Verwenden Sie die folgende Syntax, um Lizenzen von allen vorhandenen Benutzerkonten zu entfernen:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Dieses Beispiel entfernt die `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) Lizenz aus allen vorhandenen Benutzerkonten lizenziert.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Die Langfassung (Anweisungen mit detaillierten Erläuterungen)
<a name="LongVersion"> </a>

Nichts dauert ewig sowie enthält Office 365-Lizenzen: früher oder später es kommt der Zeitpunkt, Sie eine Lizenz von einem Benutzerkonto zu entfernen müssen. Der Benutzer ist vielleicht Urlaub wechseln; der Benutzer benötigt möglicherweise nicht mehr die Lizenz; Vielleicht - umfasst offensichtlich eine beliebige Anzahl von Gründe, warum Sie möglicherweise eine Benutzerlizenz entfernen möchten.
  
Bevor wir weiter es ist wichtig wechseln, beachten Sie, dass Sie nun erfordert eine Lizenz entfernen, entfernen Sie die Lizenz: deaktivieren alle Dienste für eine Lizenz ist nicht dasselbe wie eine Lizenz entfernen. Nehmen wir beispielsweise an, dass wir alle unsere Office 365-Lizenzen verwendet haben; Anders ausgedrückt, es gibt keine Lizenzen verfügbar ist. Sie beschließen, führen das Verfahren unter [Deaktivieren des Zugriffs auf Services mit Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) , um alle Dienste, beispielsweise für Belinda Newman Konto zu deaktivieren. Nachdem wir gemacht, wie viele Lizenzen haben wir für uns verfügbaren? Haben richtig gehört: 0 (null). Ja, das Verfahren in diesem Thema wird *Deaktivieren* aller Dienste auf dem Belindas Lizenz, aber nicht deaktiviert (d. h., delete) die Lizenz selbst. Die Lizenz noch gültig sein, und es noch Belinda Newman zugewiesen. Er wird nicht nur diese Lizenz Zugriff auf eine beliebige Office 365-Dienste verwenden kann.
  
Und das ist wichtig: Wenn Sie einem Benutzer eine Lizenz entziehen möchten müssen Sie tatsächlich *Entfernen* der Lizenz. Deaktivieren alle Dienste wird verhindert, dass des Benutzers anmelden bei Office 365, aber er wird nicht seine Lizenz frei. Wenn eine Lizenz wieder zu übernehmen, die aktuell, die einem Benutzer zugewiesen ist, müssen Sie einen Befehl ähnlich, einen Befehl ausführen, die den _RemoveLicenses_ -Parameter verwendet, um die Belinda zuvor zugewiesene Lizenz tatsächlich entfernt, werden soll:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Führen Sie diesen Befehl aus, und Belinda Newman wird nicht mehr zur Verwendung von Office 365 lizenziert.
  
> [!NOTE]
> Wie Sie sehen können, wenn Sie den _RemoveLicenses_ -Parameter verwenden, den Sie den Namen der zu entfernenden Lizenz angeben müssen. Wenn Sie nicht sicher sind, welche Lizenzierungsplan verwendet wurde, um dem Benutzer nur führen Sie einen Befehl wie folgt eine Lizenz zuweisen:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Um sich zu vergewissern, ob die Lizenz tatsächlich entfernt wurde, überprüfen Sie das betreffende Konto mit dem Cmdlet "Get-MsolUser":
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Wenn alles planmäßig verlaufen, Eigenschaft der Belindas **"islicensed"** wird jetzt so eingestellt werden `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Löschen des Benutzerkontos ist eine weitere Möglichkeit, um eine Lizenz freizugeben. Weitere Informationen finden Sie unter [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Siehe auch

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Neu bei Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

