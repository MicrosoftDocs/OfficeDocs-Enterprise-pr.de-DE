---
title: Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Verwenden Sie die PowerShell-Cmdlets der zentralisierten Bereitstellung, um Sie beim Bereitstellen und Verwalten von Office-Add-Ins für Ihre Office 365-Organisation zu unterstützen.
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070501"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins

Als Office 365-Administrator können Sie Office-Add-Ins über das zentralisierte Bereitstellungsfeature für Benutzer bereitstellen (Weitere Informationen finden Sie unter [Deploy Office Add-Ins in Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Zusätzlich zur Bereitstellung von Office-Add-Ins über das Office 365 Admin Center können Sie auch Microsoft PowerShell verwenden. Installieren [Sie das zentralisierte O365-Add-in-Bereitstellungsmodul für Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 
    
## <a name="connect-using-your-admin-credentials"></a>Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen

Bevor Sie die zentralisierten Bereitstellungs-Cmdlets verwenden können, müssen Sie sich anmelden.
  
1. Starten Sie PowerShell.
    
2. Stellen Sie mithilfe der Anmeldeinformationen Ihres Unternehmens eine Verbindung zu PowerShell her. Führen Sie das folgende Cmdlet aus.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Geben Sie auf der Seite **Anmeldeinformationen eingeben** Ihre Office 365-Anmeldeinformationen für den globalen Administrator ein. Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben. 
    
    Führen Sie das folgende Cmdlet aus, um die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt anzugeben.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Hochladen eines Add-in-Manifests

Führen Sie das Cmdlet New-organisationadd-in aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, der entweder ein Dateispeicherort oder eine URL sein kann. Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Sie können auch das Cmdlet New-organisationadd-in ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt zuzuweisen, indem Sie den Parameter _Members_ verwenden, wie im folgenden Beispiel gezeigt. Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Hochladen eines Add-Ins aus dem Office Store

Führen Sie das Cmdlet New-OrganizationAddIn aus, um ein Manifest aus dem Office Store hochzuladen.
  
Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn die Ressourcen-Nr. für ein Add-in für einen US-Standort-und-Inhalts Markt an.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Um den Wert für den Parameter _Asset_ -Nr zu bestimmen, können Sie ihn aus der URL der Office Store-Webseite für das Add-in kopieren. AssetIds beginnen immer mit "WA" gefolgt von einer Zahl. Im vorherigen Beispiel ist die Quelle für den Asset-Wert von WA104099688 die Office Store-Webseiten-URL für das Add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Die Werte für den __ Parameter Locale und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, in der Sie das Add-in installieren möchten. Das Format lautet en-US, fr-fr. usw. 
  
> [!NOTE]
> Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist. 
  
## <a name="get-details-of-an-add-in"></a>Abrufen von Details eines Add-ins

Führen Sie das Get-OrganizationAddIn-Cmdlet wie unten gezeigt aus, um Details zu allen Add-Ins abzurufen, die an den Mandanten hochgeladen wurden, und enthalten die Produkt-ID des Add-Ins.
  
```
Get-OrganizationAddIn
```

Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den Parameter _ProductID_ aus, um anzugeben, für welches Add-in Details abgerufen werden sollen. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Wenn Sie alle Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen erhalten möchten, übergeben Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List, wie im folgenden Beispiel gezeigt.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Aktivieren oder Deaktivieren eines Add-ins

Zum Deaktivieren eines Add-Ins, damit Benutzer und Gruppen, die ihm zugewiesen sind, keinen Zugriff mehr haben, führen Sie das Cmdlet Set-OrganizationAddIn mit dem Parameter _ProductID_ und dem Parameter _Enabled_ auf `$false`auf, wie im folgenden Beispiel gezeigt.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus __ , wobei der Parameter `$true`Enabled auf festgelegt ist.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Hinzufügen oder Entfernen von Benutzern aus einem Add-in

Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet Set-OrganizationAddInAssignments mit den Parametern _ProductID_, _Add_und _Members_ aus. Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Um Benutzer und Gruppen zu entfernen, führen Sie dasselbe Cmdlet mit dem Parameter _Remove_ aus. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Um allen Benutzern des Mandanten ein Add-in zuzuweisen, führen Sie dasselbe Cmdlet mit dem Parameter _AssignToEveryone_ mit dem Wert auf `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Sie können dasselbe Cmdlet ausführen und den _AssignToEveryone_ -Parameter deaktivieren, indem Sie seinen Wert auf `$false`festlegen, um keinem Benutzer ein Add-in zuzuweisen und zu den zuvor zugewiesenen Benutzern und Gruppen zurückzukehren.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aktualisieren eines Add-ins

Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet Set-OrganizationAddIn mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist. 
  
## <a name="delete-an-add-in"></a>Löschen eines Add-ins

Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel dargestellt. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Ausführliche Hilfe zu den einzelnen Cmdlets

Ausführliche Hilfe zu den einzelnen Cmdlets finden Sie unter Verwendung des Cmdlets Get-Help. Das folgende Cmdlet enthält beispielsweise detaillierte Informationen zum Cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


