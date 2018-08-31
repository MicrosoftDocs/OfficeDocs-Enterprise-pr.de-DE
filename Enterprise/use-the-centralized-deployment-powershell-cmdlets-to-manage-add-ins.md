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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="e61d4-103">Verwenden Sie die zentrale Bereitstellung PowerShell-Cmdlets zum Verwalten von-add-ins</span><span class="sxs-lookup"><span data-stu-id="e61d4-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="e61d4-p101">Sie können Office-add-ins für Benutzer über die zentrale Bereitstellung bereitstellen, als ein Office 365-Admin-Funktion (siehe [Bereitstellen von Office-Add-ins im Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Zusätzlich zur Bereitstellung von Office-add-ins über das Office 365 Administrationscenter, können Sie auch Microsoft PowerShell verwenden. [Laden Sie](https://go.microsoft.com/fwlink/p/?linkid=850850) die zentrale Bereitstellung PowerShell-Cmdlets aus dem Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="e61d4-107">Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="e61d4-107">Connect using your admin credentials</span></span>

<span data-ttu-id="e61d4-108">Bevor Sie die Cmdlets zentralisierte Bereitstellung verwenden können, müssen Sie anmelden.</span><span class="sxs-lookup"><span data-stu-id="e61d4-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="e61d4-109">Starten Sie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e61d4-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="e61d4-p102">Eine Verbindung zu PowerShell mit Ihren Administratoranmeldeinformationen Unternehmen. Führen Sie das folgende Cmdlet aus.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="e61d4-p103">Geben Sie Ihre Office 365 globaler Administrator-Anmeldeinformationen auf der Seite **Anmeldeinformationen eingeben** . Alternativ können Sie direkt in das Cmdlet Ihre Anmeldeinformationen eingeben.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="e61d4-114">Führen Sie das folgende Cmdlet angeben von Ihrem Unternehmen Administratorinformationen als ein PSCredential-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="e61d4-115">Weitere Informationen zum Verwenden von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="e61d4-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="e61d4-116">Hochladen einer Manifest-Add-in</span><span class="sxs-lookup"><span data-stu-id="e61d4-116">Upload an add-in manifest</span></span>

<span data-ttu-id="e61d4-p104">Führen Sie das Cmdlet New-OrganizationAdd-In, um ein Manifest-Add-in aus einem Pfad hochzuladen, einen Dateispeicherort oder eine URL sein kann. Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des Parameters _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="e61d4-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="e61d4-p105">Sie können auch das Cmdlet New-OrganizationAdd-In, um ein Add-in hochzuladen, und weisen Sie es Benutzern oder Gruppen direkt mithilfe des _Member_ -Parameters, wie im folgenden Beispiel dargestellt ausführen. Trennen Sie die e-Mail-Adressen der Elemente durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="e61d4-121">Ein Add-in aus dem Office Store hochladen</span><span class="sxs-lookup"><span data-stu-id="e61d4-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="e61d4-122">Führen Sie das Cmdlet New-OrganizationAddIn hochladen eine Manifestdatei aus dem Office Store aus.</span><span class="sxs-lookup"><span data-stu-id="e61d4-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="e61d4-123">Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn das Hilfethema für ein Add-In für einen Markt USA, Speicherort und Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="e61d4-p106">Um den Wert für den Parameter _Hilfethema_ zu bestimmen, können Sie kopieren es aus der URL der im Office Store-Webseite für das Add-in AssetIds immer beginnen mit "WA" gefolgt von einer Zahl. Die Quelle für den Wert Hilfethema WA104099688 ist beispielsweise im vorherigen Beispiel die URL des Office Store-Webseite für das Add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="e61d4-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="e61d4-p107">Die Werte für den Parameter _Locale_ und der _ContentMarket_ -Parameter sind identisch, und geben Sie an, das Land/Region, der Sie das Add-in aus installieren möchten. Das Format ist En-US, fr-FR und So weiter.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e61d4-130">-Add-ins aus dem Office Store hochgeladen wird innerhalb einiger Tage der letzten Aktualisierung nicht verfügbar sein, auf dem Office Store automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e61d4-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="e61d4-131">Hier erhalten Sie von einem Add-in</span><span class="sxs-lookup"><span data-stu-id="e61d4-131">Get details of an add-in</span></span>

<span data-ttu-id="e61d4-132">Führen Sie das Cmdlet Get-OrganizationAddIn wie unten dargestellt enthalten, um die Details der alle Add-Ins, die dem Mandanten hochgeladen abrufen ein Add-in Produkt-ID</span><span class="sxs-lookup"><span data-stu-id="e61d4-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="e61d4-133">Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den Parameter _ProductId_ an die add-Ins, dass Details für abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="e61d4-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="e61d4-134">Wenn Sie alle Details der alle Add-Ins plus zugewiesene Benutzer und Gruppen erhalten möchten, leiten Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="e61d4-135">Aktivieren Sie oder deaktivieren Sie eines Add-Ins</span><span class="sxs-lookup"><span data-stu-id="e61d4-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="e61d4-136">Um ein Add-in zu deaktivieren, damit Benutzer und Gruppen, die ihm zugewiesen sind nicht mehr Zugriff haben, führen Sie das Cmdlet Set-OrganizationAddIn mit der _ProductId_ -Parameter und der Parameter _Enabled_ legen Sie auf `$false`, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="e61d4-137">Um ein Add-in wieder zu aktivieren, führen Sie das gleiche Cmdlet mit der Parameter _Enabled_ legen Sie auf `$true`.</span><span class="sxs-lookup"><span data-stu-id="e61d4-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="e61d4-138">Hinzufügen oder Entfernen von Benutzern aus einer-Add-in</span><span class="sxs-lookup"><span data-stu-id="e61d4-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="e61d4-p108">Zum Hinzufügen von Benutzern und Gruppen zu einer bestimmten Add-in führen Sie das Set-OrganizationAddInAssignments-Cmdlet mit den Parametern _ProductId_, _Hinzufügen_und _Mitglieder_ . Trennen Sie die e-Mail-Adressen der Elemente durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e61d4-141">Führen Sie zum Entfernen von Benutzern und Gruppen mit dem gleiche-Cmdlet mit dem Parameter _Entfernen_ .</span><span class="sxs-lookup"><span data-stu-id="e61d4-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e61d4-142">Führen Sie ein Add-in, um alle Benutzer auf dem Mandanten zuzuweisen, mit dem gleiche-Cmdlet mit dem _AssignToEveryone_ -Parameter mit dem Wert `$true`.</span><span class="sxs-lookup"><span data-stu-id="e61d4-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="e61d4-143">Um kein Add-In für alle Benutzer zuweisen und Zurücksetzen der zuvor zugewiesene Benutzer und Gruppen, können Sie mit dem gleiche-Cmdlet ausführen und der Parameter _AssignToEveryone_ deaktivieren, indem Sie seinen Wert auf `$false`.</span><span class="sxs-lookup"><span data-stu-id="e61d4-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="e61d4-144">Aktualisieren eines Add-Ins</span><span class="sxs-lookup"><span data-stu-id="e61d4-144">Update an add-in</span></span>

<span data-ttu-id="e61d4-145">Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet Set-OrganizationAddIn mit _ProductId_, _ManifestPath_und _Gebietsschema_ -Parameter, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="e61d4-146">-Add-ins aus dem Office Store hochgeladen wird innerhalb einiger Tage der letzten Aktualisierung nicht verfügbar sein, auf dem Office Store automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e61d4-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="e61d4-147">Löschen eines Add-Ins</span><span class="sxs-lookup"><span data-stu-id="e61d4-147">Delete an add-in</span></span>

<span data-ttu-id="e61d4-148">Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID-Wert_ fest, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e61d4-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="e61d4-149">Für jedes Cmdlet detaillierte Hilfe erhalten</span><span class="sxs-lookup"><span data-stu-id="e61d4-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="e61d4-p109">Sie können mit dem Cmdlet Get-Help detaillierte Hilfe für alle Cmdlets anzeigen. Beispielsweise enthält das folgende Cmdlet detaillierte Informationen zum Cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="e61d4-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


