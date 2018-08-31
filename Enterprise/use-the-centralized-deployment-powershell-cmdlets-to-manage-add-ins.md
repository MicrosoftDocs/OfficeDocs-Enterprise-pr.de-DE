---
title: Verwenden Sie die zentrale Bereitstellung PowerShell-Cmdlets zum Verwalten von-add-ins
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
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
description: Verwenden Sie die zentrale Bereitstellung PowerShell-Cmdlets, mit denen Sie die Bereitstellung und Verwaltung von Office-add-ins für Office 365-Organisation.
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540966"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Verwenden Sie die zentrale Bereitstellung PowerShell-Cmdlets zum Verwalten von-add-ins

Sie können Office-add-ins für Benutzer über die zentrale Bereitstellung bereitstellen, als ein Office 365-Admin-Funktion (siehe [Bereitstellen von Office-Add-ins im Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Zusätzlich zur Bereitstellung von Office-add-ins über das Office 365 Administrationscenter, können Sie auch Microsoft PowerShell verwenden. [Laden Sie](https://go.microsoft.com/fwlink/p/?linkid=850850) die zentrale Bereitstellung PowerShell-Cmdlets aus dem Microsoft Download Center. 
    
## <a name="connect-using-your-admin-credentials"></a>Verbindung mit Ihren Administratoranmeldeinformationen

Bevor Sie die Cmdlets zentralisierte Bereitstellung verwenden können, müssen Sie anmelden.
  
1. Starten Sie PowerShell.
    
2. Eine Verbindung zu PowerShell mit Ihren Administratoranmeldeinformationen Unternehmen. Führen Sie das folgende Cmdlet aus.
    
  ```
  Connect-OrganizationAddInService
  ```

3. Geben Sie Ihre Office 365 globaler Administrator-Anmeldeinformationen auf der Seite **Anmeldeinformationen eingeben** . Alternativ können Sie direkt in das Cmdlet Ihre Anmeldeinformationen eingeben. 
    
    Führen Sie das folgende Cmdlet angeben von Ihrem Unternehmen Administratorinformationen als ein PSCredential-Objekt.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Weitere Informationen zum Verwenden von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Hochladen einer Manifest-Add-in

Führen Sie das Cmdlet New-OrganizationAdd-In, um ein Manifest-Add-in aus einem Pfad hochzuladen, einen Dateispeicherort oder eine URL sein kann. Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des Parameters _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Sie können auch das Cmdlet New-OrganizationAdd-In, um ein Add-in hochzuladen, und weisen Sie es Benutzern oder Gruppen direkt mithilfe des _Member_ -Parameters, wie im folgenden Beispiel dargestellt ausführen. Trennen Sie die e-Mail-Adressen der Elemente durch ein Komma. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Ein Add-in aus dem Office Store hochladen

Führen Sie das Cmdlet New-OrganizationAddIn hochladen eine Manifestdatei aus dem Office Store aus.
  
Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn das Hilfethema für ein Add-In für einen Markt USA, Speicherort und Inhalt.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Um den Wert für den Parameter _Hilfethema_ zu bestimmen, können Sie kopieren es aus der URL der im Office Store-Webseite für das Add-in AssetIds immer beginnen mit "WA" gefolgt von einer Zahl. Die Quelle für den Wert Hilfethema WA104099688 ist beispielsweise im vorherigen Beispiel die URL des Office Store-Webseite für das Add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Die Werte für den Parameter _Locale_ und der _ContentMarket_ -Parameter sind identisch, und geben Sie an, das Land/Region, der Sie das Add-in aus installieren möchten. Das Format ist En-US, fr-FR und So weiter. 
  
> [!NOTE]
> -Add-ins aus dem Office Store hochgeladen wird innerhalb einiger Tage der letzten Aktualisierung nicht verfügbar sein, auf dem Office Store automatisch aktualisiert. 
  
## <a name="get-details-of-an-add-in"></a>Hier erhalten Sie von einem Add-in

Führen Sie das Cmdlet Get-OrganizationAddIn wie unten dargestellt enthalten, um die Details der alle Add-Ins, die dem Mandanten hochgeladen abrufen ein Add-in Produkt-ID
  
```
Get-OrganizationAddIn
```

Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den Parameter _ProductId_ an die add-Ins, dass Details für abgerufen werden soll. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Wenn Sie alle Details der alle Add-Ins plus zugewiesene Benutzer und Gruppen erhalten möchten, leiten Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List wie im folgenden Beispiel dargestellt.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Aktivieren Sie oder deaktivieren Sie eines Add-Ins

Um ein Add-in zu deaktivieren, damit Benutzer und Gruppen, die ihm zugewiesen sind nicht mehr Zugriff haben, führen Sie das Cmdlet Set-OrganizationAddIn mit der _ProductId_ -Parameter und der Parameter _Enabled_ legen Sie auf `$false`, wie im folgenden Beispiel gezeigt.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Um ein Add-in wieder zu aktivieren, führen Sie das gleiche Cmdlet mit der Parameter _Enabled_ legen Sie auf `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Hinzufügen oder Entfernen von Benutzern aus einer-Add-in

Zum Hinzufügen von Benutzern und Gruppen zu einer bestimmten Add-in führen Sie das Set-OrganizationAddInAssignments-Cmdlet mit den Parametern _ProductId_, _Hinzufügen_und _Mitglieder_ . Trennen Sie die e-Mail-Adressen der Elemente durch ein Komma. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Führen Sie zum Entfernen von Benutzern und Gruppen mit dem gleiche-Cmdlet mit dem Parameter _Entfernen_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Führen Sie ein Add-in, um alle Benutzer auf dem Mandanten zuzuweisen, mit dem gleiche-Cmdlet mit dem _AssignToEveryone_ -Parameter mit dem Wert `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Um kein Add-In für alle Benutzer zuweisen und Zurücksetzen der zuvor zugewiesene Benutzer und Gruppen, können Sie mit dem gleiche-Cmdlet ausführen und der Parameter _AssignToEveryone_ deaktivieren, indem Sie seinen Wert auf `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aktualisieren eines Add-Ins

Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet Set-OrganizationAddIn mit _ProductId_, _ManifestPath_und _Gebietsschema_ -Parameter, wie im folgenden Beispiel dargestellt. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> -Add-ins aus dem Office Store hochgeladen wird innerhalb einiger Tage der letzten Aktualisierung nicht verfügbar sein, auf dem Office Store automatisch aktualisiert. 
  
## <a name="delete-an-add-in"></a>Löschen eines Add-Ins

Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID-Wert_ fest, wie im folgenden Beispiel dargestellt. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Für jedes Cmdlet detaillierte Hilfe erhalten

Sie können mit dem Cmdlet Get-Help detaillierte Hilfe für alle Cmdlets anzeigen. Beispielsweise enthält das folgende Cmdlet detaillierte Informationen zum Cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


