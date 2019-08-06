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
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Verwenden Sie die PowerShell-Cmdlets für zentralisierte Bereitstellung, um die Bereitstellung und Verwaltung von Office-Add-Ins für Ihre Office 365 Organisation zu erleichtern.
ms.openlocfilehash: 3d6495646c6ce0a1d15f2d911f1fa8af92e3c2c6
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782585"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins

Als Office 365 Administrator können Sie Office-Add-Ins für Benutzer über das zentralisierte Bereitstellungsfeature bereitstellen (siehe [Verwalten der Bereitstellung von Office 365-Add-Ins im Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Neben der Bereitstellung von Office-Add-Ins über das Admin Center können Sie auch Microsoft PowerShell verwenden. [Laden](https://go.microsoft.com/fwlink/p/?linkid=850850) Sie die PowerShell-Cmdlets für zentralisierte Bereitstellung aus dem Microsoft Download Center herunter. 
  
## <a name="what-do-you-want-to-do"></a>Was möchten Sie machen?

[Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Hochladen eines Add-in-Manifests](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Hochladen eines Add-Ins aus dem Office Store](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Abrufen von Details eines Add-ins](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Aktivieren oder Deaktivieren eines Add-ins](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Hinzufügen oder Entfernen von Benutzern aus einem Add-in](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Aktualisieren eines Add-ins](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Löschen eines Add-ins](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Ausführliche Hilfe zu jedem Cmdlet erhalten](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen
<a name="BKMK_Connect"> </a>

Bevor Sie die Cmdlets für die zentrale Bereitstellung verwenden können, müssen Sie sich anmelden.
  
1. Starten Sie PowerShell.
    
2. Stellen Sie eine Verbindung mit PowerShell mithilfe ihrer Unternehmensadministrator Anmeldeinformationen her. Führen Sie das folgende Cmdlet aus.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Geben Sie auf der Seite **Anmeldeinformationen eingeben** Ihre Office 365 globale Administratoranmeldeinformationen ein. Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben. 
    
    Führen Sie das folgende Cmdlet aus, das die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt angibt.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Hochladen eines Add-in-Manifests
<a name="BKMK_UploadManifest"> </a>

Führen Sie das Cmdlet New-organisationadd-in aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, bei dem es sich entweder um einen Dateispeicherort oder eine URL handeln kann. Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Sie können auch das New-organisationadd-in-Cmdlet ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt mithilfe des _Members_ -Parameters zuzuweisen, wie im folgenden Beispiel gezeigt. Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Hochladen eines Add-Ins aus dem Office Store
<a name="BKMK_UploadAddin"> </a>

Führen Sie das Cmdlet New-OrganizationAddIn aus, um ein Manifest aus dem Office Store hochzuladen.
  
Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn die Asset-Nr für ein Add-in für einen Standort und einen Inhalts Markt in USA an.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Um den Wert für den Parameter _Asset_ -Nr zu ermitteln, können Sie ihn aus der URL der Office Store Webseite für das Add-in kopieren. AssetIds beginnen immer mit "WA", gefolgt von einer Zahl. Im vorherigen Beispiel ist beispielsweise die Quelle für den Wert der WA104099688-Website die URL für das Add-in Office Store Webseite: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Die Werte für den __ Parameter Locale und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, aus dem das Add-in installiert werden soll. Das Format lautet en-US, fr-fr. und so weiter. 
  
> [!NOTE]
> Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert. 
  
## <a name="get-details-of-an-add-in"></a>Abrufen von Details eines Add-ins
<a name="BKMK_GetDetails"> </a>

Führen Sie das Get-OrganizationAddIn-Cmdlet wie unten beschrieben aus, um Details zu allen Add-Ins abzurufen, die in den Mandanten hochgeladen wurden und die Produkt-ID eines Add-Ins enthalten.
  
```
Get-OrganizationAddIn
```

Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den _ProductID_ -Parameter aus, um anzugeben, für welches Add-in Sie Details abrufen möchten. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Um vollständige Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen zu erhalten, übergeben Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List, wie im folgenden Beispiel dargestellt.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Aktivieren oder Deaktivieren eines Add-ins
<a name="BKMK_TurnOnOff"> </a>

Wenn Sie ein Add-in deaktivieren möchten, sodass Benutzern und Gruppen, denen es zugewiesen ist, kein Zugriff mehr gewährt wird, führen Sie das Cmdlet "OrganizationAddIn" mit dem Parameter " _ProductID_ " `$false`und dem Parameter " _Enabled_ " aus, wie im folgenden Beispiel gezeigt.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus __ , wobei der Parameter `$true`Enabled auf festgelegt ist.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Hinzufügen oder Entfernen von Benutzern aus einem Add-in
<a name="BKMK_AddRemove"> </a>

Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet "OrganizationAddInAssignments" mit den Parametern " _ProductID_", " _Add_" und " _Members_ " aus. Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Wenn Sie Benutzer und Gruppen entfernen möchten, führen Sie das gleiche Cmdlet mit dem _Remove_ -Parameter aus. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Um ein Add-in allen Benutzern im Mandanten zuzuweisen, führen Sie das gleiche Cmdlet mit dem _AssignToEveryone_ -Parameter aus, wobei `$true`der Wert auf festgelegt ist.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Um kein Add-in allen Benutzern zuzuweisen und die zuvor zugewiesenen Benutzer und Gruppen wiederherzustellen, können Sie dasselbe Cmdlet ausführen und den Parameter _AssignToEveryone_ deaktivieren, indem Sie seinen Wert auf `$false`festlegen.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aktualisieren eines Add-ins
<a name="BKMK_UpdateAddin"> </a>

Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet "OrganizationAddIn" mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert. 
  
## <a name="delete-an-add-in"></a>Löschen eines Add-ins
<a name="BKMK_Delete"> </a>

Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel gezeigt. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Ausführliche Hilfe zu jedem Cmdlet erhalten
<a name="BKMK_GetHelp"> </a>

Sie können die detaillierte Hilfe zu jedem Cmdlet mithilfe des Cmdlets Get-Help betrachten. Beispielsweise enthält das folgende Cmdlet ausführliche Informationen zum Cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


