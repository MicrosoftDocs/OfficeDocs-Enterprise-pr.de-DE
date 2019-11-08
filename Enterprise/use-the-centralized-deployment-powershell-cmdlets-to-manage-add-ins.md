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
description: Verwenden Sie die PowerShell-Cmdlets für zentralisierte Bereitstellung, um die Bereitstellung und Verwaltung von Office-Add-Ins für Ihre Office 365 Organisation zu erleichtern.
ms.openlocfilehash: 72f7ad69f1154c65ee5f6bd608770461ae775257
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030860"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins

Als Microsoft 365 Global oder Exchange-Administrator können Sie Office-Add-Ins für Benutzer über das zentralisierte Bereitstellungsfeature bereitstellen (siehe [Deploy Office-Add-Ins im Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Neben der Bereitstellung von Office-Add-Ins über das Microsoft 365 Admin Center können Sie auch Microsoft PowerShell verwenden. Installieren [Sie das zentrale O365-Add-in-Bereitstellungsmodul für Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Öffnen Sie nach dem Herunterladen des Moduls ein reguläres Windows PowerShell Fenster, und führen Sie das folgende Cmdlet aus:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen

Bevor Sie die Cmdlets für die zentrale Bereitstellung verwenden können, müssen Sie sich anmelden.
  
1. Starten Sie PowerShell.
    
2. Stellen Sie eine Verbindung mit PowerShell mithilfe ihrer Unternehmensadministrator Anmeldeinformationen her. Führen Sie das folgende Cmdlet aus.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Geben Sie auf der Seite **Anmeldeinformationen eingeben** Ihre Office 365 globale Administratoranmeldeinformationen ein. Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben. 
    
    Führen Sie das folgende Cmdlet aus, das die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt angibt.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Hochladen eines Add-in-Manifests

Führen Sie das Cmdlet **New-organisationadd-in** aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, bei dem es sich entweder um einen Dateispeicherort oder eine URL handeln kann. Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Sie können auch das **New-organisationadd-in-** Cmdlet ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt mithilfe des _Members_ -Parameters zuzuweisen, wie im folgenden Beispiel gezeigt. Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Hochladen eines Add-Ins aus dem Office Store

Führen Sie das Cmdlet **New-OrganizationAddIn** aus, um ein Manifest aus dem Office Store hochzuladen.
  
Im folgenden Beispiel gibt das Cmdlet **New-OrganizationAddIn** die Asset-Nr für ein Add-in für einen Standort und einen Inhalts Markt in USA an.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Um den Wert für den Parameter _Asset_ -Nr zu ermitteln, können Sie ihn aus der URL der Office Store Webseite für das Add-in kopieren. AssetIds beginnen immer mit "WA", gefolgt von einer Zahl. Im vorherigen Beispiel ist beispielsweise die Quelle für den Wert der WA104099688-Website die URL für das Add-in Office Store Webseite: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Die Werte für den Parameter _locale_ und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, aus dem das Add-in installiert werden soll. Das Format lautet en-US, fr-fr. und so weiter. 
  
> [!NOTE]
> Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert. 
  
## <a name="get-details-of-an-add-in"></a>Abrufen von Details eines Add-ins

Führen Sie das **Get-OrganizationAddIn-** Cmdlet wie unten beschrieben aus, um Details zu allen Add-Ins abzurufen, die in den Mandanten hochgeladen wurden und die Produkt-ID eines Add-Ins enthalten.
  
```powershell
Get-OrganizationAddIn
```

Führen Sie das Cmdlet **Get-OrganizationAddIn** mit einem Wert für den _ProductID_ -Parameter aus, um anzugeben, für welches Add-in Sie Details abrufen möchten. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Um vollständige Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen zu erhalten, übergeben Sie die Ausgabe des Cmdlets **Get-OrganizationAddIn** an das Cmdlet Format-List, wie im folgenden Beispiel dargestellt.
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Aktivieren oder Deaktivieren eines Add-ins

Wenn Sie ein Add-in deaktivieren möchten, sodass Benutzern und Gruppen, denen es zugewiesen ist, kein Zugriff mehr gewährt wird, führen Sie das Cmdlet " **OrganizationAddIn** " mit dem Parameter " _ProductID_ " `$false`und dem Parameter " _Enabled_ " aus, wie im folgenden Beispiel gezeigt.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus __ , wobei der Parameter `$true`Enabled auf festgelegt ist.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Hinzufügen oder Entfernen von Benutzern aus einem Add-in

Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet " **OrganizationAddInAssignments** " mit den Parametern " _ProductID_", " _Add_" und " _Members_ " aus. Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Wenn Sie Benutzer und Gruppen entfernen möchten, führen Sie das gleiche Cmdlet mit dem _Remove_ -Parameter aus. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Um ein Add-in allen Benutzern im Mandanten zuzuweisen, führen Sie das gleiche Cmdlet mit dem _AssignToEveryone_ -Parameter aus, wobei `$true`der Wert auf festgelegt ist.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Um kein Add-in allen Benutzern zuzuweisen und die zuvor zugewiesenen Benutzer und Gruppen wiederherzustellen, können Sie dasselbe Cmdlet ausführen und den Parameter _AssignToEveryone_ deaktivieren, indem Sie seinen Wert auf `$false`festlegen.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Aktualisieren eines Add-ins

Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet " **OrganizationAddIn** " mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert. 
  
## <a name="delete-an-add-in"></a>Löschen eines Add-ins

Um ein Add-in zu löschen, führen **Sie das Cmdlet Remove-OrganizationAddIn** mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel gezeigt. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>Anpassen von Microsoft Store-Add-Ins für Ihre Organisation

Sie müssen das Add-in anpassen, bevor Sie es in Ihrer Organisation bereitstellen. Add-Ins, die älter als Version 1,1 sind, werden von dieser Funktion nicht unterstützt. 

Es wird empfohlen, dass Sie zuerst ein angepasstes Add-in für sich selbst bereitstellen, um sicherzustellen, dass es wie erwartet funktioniert, bevor Sie es in ihrer gesamten Organisation bereitstellen.

Beachten Sie auch die folgenden Einschränkungen:
- Alle URLs müssen absolut sein (Include http oder HTTPS) und gültig.
- *DisplayName* darf 125 Zeichen nicht überschreiten 
- *DisplayName*, *Ressourcen* und *AppDomains* dürfen die folgenden Zeichen nicht enthalten: 
 
    - \<
    -  \>
    -  ;
    -  =   

Wenn Sie ein bereitgestelltes Add-in anpassen möchten, müssen Sie es im Admin Center deinstallieren und unter [Entfernen eines Add-Ins aus dem lokalen Cache](#remove-an-add-in-from-local-cache) weitere Schritte ausführen, um es von jedem Computer zu entfernen, auf dem es bereitgestellt wurde.

Um ein Add-in anzupassen, führen Sie das Cmdlet " **OrganizationAddInOverrides** " mit der *ProductID* als Parameter aus, gefolgt von dem Tag, das Sie überschreiben möchten, und dem neuen Wert. Informationen zum Abrufen der *ProductID* finden Sie unter [Get Details of an Add-in](#get-details-of-an-add-in) in this article. Zum Beispiel:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
Um mehrere Tags für ein Add-in anzupassen, fügen Sie diese Tags zur Befehlszeile hinzu:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> Sie müssen mehrere benutzerdefinierte Tags auf ein Add-in als einen Befehl anwenden. Wenn Sie die Markierungen nacheinander anpassen, wird nur die letzte Anpassung angewendet. Wenn Sie ein Tag versehentlich anpassen, müssen Sie außerdem alle Anpassungen entfernen und von vorne beginnen.

### <a name="tags-you-can-customize"></a>Tags, die Sie anpassen können

| Tag                  | Beschreibung          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| Die URL des Bilds, das als Symbol für das Add-in verwendet wird (in Admin Center). </br> |
| \<DisplayName>| Der Titel des Add-Ins (im Admin Center).|
| \<Hosts>| Liste der apps, die das Add-in unterstützen sollen.|
| \<SourceLocation> | Die Quell-URL, mit der das Add-in verbunden wird.| 
| \<AppDomains-> | Eine Liste der Domänen, mit denen das Add-in eine Verbindung herstellen kann. | 
| \<SupportUrl>| Die URL, die Benutzer für den Zugriff auf Hilfe und Support verwenden können. | 
| \<Ressourcen>  | Dieses Tag enthält eine Reihe von Elementen, einschließlich Titeln, QuickInfos und Symbolen unterschiedlicher Größe.| 
|
### <a name="customize-resources-tag"></a>Ressourcen-Tag anpassen

Jedes Element im- <Resources> Tag des Manifests kann dynamisch angepasst werden. Zunächst müssen Sie das Manifest überprüfen, um die Element-ID zu finden, der Sie einen neuen Wert zuweisen möchten. Das <Resources> -Tag sieht wie folgt aus:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In diesem Fall lautet die Element-ID für das Bild "img16icon", und der ihm zugeordnete Wert lautet "http:<i></i>//Site. <i> </i>com/img. jpg. "

Nachdem Sie die Elemente identifiziert haben, die Sie anpassen möchten, verwenden Sie den folgenden Befehl in PowerShell, um den Elementen neue Werte zuzuweisen:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

Sie können so viele Elemente wie nötig mit dem Befehl anpassen.

### <a name="remove-customization-from-an-add-in"></a>Entfernen der Anpassung von einem Add-in

Die einzige Option, die derzeit zum Löschen von Anpassungen verfügbar ist, besteht darin, alle gleichzeitig zu löschen:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>Anzeigen von Add-in-Anpassungen

Führen Sie das Cmdlet **Get-OrganizationAddInOverrides** aus, um eine Liste der angewendeten Anpassungen anzuzeigen. Wenn **Get-OrganizationAddInOverrides** ohne *ProductID* ausgeführt wird, wird eine Liste aller Add-Ins mit angewendeten Außerkraftsetzungen zurückgegeben.  

```powershell
Get-OrganizationAddInOverrides 
```
Wenn ProductID angegeben ist, wird eine Liste der auf das Add-in angewendeten Außerkraftsetzungen zurückgegeben. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>Entfernen eines Add-Ins aus dem lokalen Cache

Wenn ein Add-in bereitgestellt wurde, muss es aus dem Cache auf jedem Computer entfernt werden, bevor es angepasst werden kann. So remive Sie ein Add-in aus dem Cache:

1. Navigieren Sie zum Ordner "Users" in "\ \". 
1. Wechseln Sie zu Ihrem Benutzerordner
1. Navigieren Sie zu AppData\Local\Microsoft\Office, und wählen Sie den Ordner aus, der Ihrer Office-Version zugeordnet ist.
1. Löschen Sie im *WEF* -Ordner den Ordner *Manifests* .

## <a name="get-detailed-help-for-each-cmdlet"></a>Ausführliche Hilfe zu jedem Cmdlet erhalten

Sie können die detaillierte Hilfe zu jedem Cmdlet mithilfe des Cmdlets Get-Help betrachten. Beispielsweise enthält das folgende Cmdlet ausführliche Informationen zum Cmdlet Remove-OrganizationAddIn.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


