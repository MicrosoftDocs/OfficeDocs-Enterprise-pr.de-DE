---
title: Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213952"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Anzeigen von Lizenz- und Dienstdetails für Konten mit Office 365 PowerShell

**Zusammenfassung:** Erläutert, wie Office 365 PowerShell verwenden, um die Office 365-Dienste zu ermitteln, die Benutzern zugewiesen wurden.
  
In Office 365 lizenziert Pläne Lizenzieren von (auch gewählte SKUs oder Office 365-Pläne) gewähren des Benutzerzugriffs auf Office 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer möglicherweise jedoch nicht Zugriff auf alle Dienste, die in eine Lizenz verfügbar sind, die ihnen derzeit zugewiesen ist. Office 365 PowerShell können Sie den Status von Diensten auf Benutzerkonten anzuzeigen. 

## <a name="before-you-begin"></a>Bevor Sie beginnen

- Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Office 365 PowerShell herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).
    
- Verwenden Sie die Befehle `Get-MsolAccountSku` und `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` , die folgende Informationen zu erhalten:
    
  - Die Lizenzierungspläne, die in Ihrer Organisation verfügbar sind.
    
  - Die Dienste, die in den einzelnen Lizenzierungsplänen verfügbar sind, und die Reihenfolge, in der sie aufgelistet sind (die Indexnummer).
    
     Weitere Informationen zur Lizenzierung Pläne, Lizenzen und Dienste finden Sie unter [Lizenzen anzeigen und-Dienste mit Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Verwenden Sie den Befehl `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` , um die Lizenzen zu erhalten, die ein Benutzer und die Reihenfolge, in zugewiesen sind, sie darstellen (die Indexnummer) aufgeführt.
    
- Bei Verwendung des **Get-MsolUser** -Cmdlets ohne den _All_-Parameter werden nur die ersten 500 Konten zurückgegeben.
    

## <a name="to-view-services-for-a-user-account"></a>So zeigen Sie Dienste für ein Benutzerkonto an

Um die Office 365-Dienste anzuzeigen, denen ein Benutzer zugreifen kann, verwenden Sie die folgende Syntax:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Dieses Beispiel zeigt die Dienste auf denen der Benutzer BelindaN@litwareinc.com zugreifen kann. Zeigt die Dienste, die alle Lizenzen zugeordnet sind, die ihr Konto zugewiesen sind.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Um alle Dienste für einen Benutzer anzuzeigen, die *mehrere Lizenzen*zugewiesen wurde, verwenden Sie die folgende Syntax:

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>Siehe auch

In den folgenden zusätzlichen Themen finden Sie weitere Informationen zum Verwalten von Benutzern mit Office 365 PowerShell:
  
- [Erstellen von Benutzerkonten mit Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Löschen und Wiederherstellen von Benutzerkonten mit Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Blockieren von Benutzerkonten mit Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Zuweisen von Lizenzen zu Benutzerkonten mit Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Entfernen von Lizenzen von Benutzerkonten mit Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Weitere Informationen zu den in diesen Verfahren Thema verwendeten Cmdlets finden Sie unter den folgenden Themen:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Neu bei Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]