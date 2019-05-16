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
description: Verwenden Sie die PowerShell-Cmdlets der zentralisierten Bereitstellung, um Sie beim Bereitstellen und Verwalten von Office-Add-Ins für Ihre Office 365-Organisation zu unterstützen.
ms.openlocfilehash: 404085d79827664437f3ad327fac4a99166adcf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071141"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="e9b08-103">Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="e9b08-104">Als Office 365-Administrator können Sie Office-Add-Ins über das zentralisierte Bereitstellungsfeature für Benutzer bereitstellen (siehe [Verwalten der Bereitstellung von Office 365-Add-Ins im Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="e9b08-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="e9b08-105">Zusätzlich zur Bereitstellung von Office-Add-Ins über das Office 365 Admin Center können Sie auch Microsoft PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="e9b08-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="e9b08-106">[Laden](https://go.microsoft.com/fwlink/p/?linkid=850850) Sie die PowerShell-Cmdlets für die zentrale Bereitstellung aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="e9b08-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="e9b08-107">Was möchten Sie machen?</span><span class="sxs-lookup"><span data-stu-id="e9b08-107">What do you want to do?</span></span>

[<span data-ttu-id="e9b08-108">Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="e9b08-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="e9b08-109">Hochladen eines Add-in-Manifests</span><span class="sxs-lookup"><span data-stu-id="e9b08-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="e9b08-110">Hochladen eines Add-Ins aus dem Office Store</span><span class="sxs-lookup"><span data-stu-id="e9b08-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="e9b08-111">Abrufen von Details eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="e9b08-112">Aktivieren oder Deaktivieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="e9b08-113">Hinzufügen oder Entfernen von Benutzern aus einem Add-in</span><span class="sxs-lookup"><span data-stu-id="e9b08-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="e9b08-114">Aktualisieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="e9b08-115">Löschen eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="e9b08-116">Ausführliche Hilfe zu den einzelnen Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e9b08-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="e9b08-117">Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="e9b08-117">Connect using your admin credentials</span></span>
<span data-ttu-id="e9b08-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-118"></span></span>

<span data-ttu-id="e9b08-119">Bevor Sie die zentralisierten Bereitstellungs-Cmdlets verwenden können, müssen Sie sich anmelden.</span><span class="sxs-lookup"><span data-stu-id="e9b08-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="e9b08-120">Starten Sie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9b08-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="e9b08-121">Stellen Sie mithilfe der Anmeldeinformationen Ihres Unternehmens eine Verbindung zu PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="e9b08-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="e9b08-122">Führen Sie das folgende Cmdlet aus.</span><span class="sxs-lookup"><span data-stu-id="e9b08-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="e9b08-123">Geben Sie auf der Seite **Anmeldeinformationen eingeben** Ihre Office 365-Anmeldeinformationen für den globalen Administrator ein.</span><span class="sxs-lookup"><span data-stu-id="e9b08-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="e9b08-124">Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben.</span><span class="sxs-lookup"><span data-stu-id="e9b08-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="e9b08-125">Führen Sie das folgende Cmdlet aus, um die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="e9b08-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="e9b08-126">Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="e9b08-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="e9b08-127">Hochladen eines Add-in-Manifests</span><span class="sxs-lookup"><span data-stu-id="e9b08-127">Upload an add-in manifest</span></span>
<span data-ttu-id="e9b08-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-128"></span></span>

<span data-ttu-id="e9b08-129">Führen Sie das Cmdlet New-organisationadd-in aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, der entweder ein Dateispeicherort oder eine URL sein kann.</span><span class="sxs-lookup"><span data-stu-id="e9b08-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="e9b08-130">Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters.</span><span class="sxs-lookup"><span data-stu-id="e9b08-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="e9b08-131">Sie können auch das Cmdlet New-organisationadd-in ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt zuzuweisen, indem Sie den Parameter _Members_ verwenden, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9b08-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="e9b08-132">Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="e9b08-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="e9b08-133">Hochladen eines Add-Ins aus dem Office Store</span><span class="sxs-lookup"><span data-stu-id="e9b08-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="e9b08-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-134"></span></span>

<span data-ttu-id="e9b08-135">Führen Sie das Cmdlet New-OrganizationAddIn aus, um ein Manifest aus dem Office Store hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="e9b08-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="e9b08-136">Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn die Ressourcen-Nr. für ein Add-in für einen US-Standort-und-Inhalts Markt an.</span><span class="sxs-lookup"><span data-stu-id="e9b08-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="e9b08-137">Um den Wert für den Parameter _Asset_ -Nr zu bestimmen, können Sie ihn aus der URL der Office Store-Webseite für das Add-in kopieren.</span><span class="sxs-lookup"><span data-stu-id="e9b08-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="e9b08-138">AssetIds beginnen immer mit "WA" gefolgt von einer Zahl.</span><span class="sxs-lookup"><span data-stu-id="e9b08-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="e9b08-139">Im vorherigen Beispiel ist die Quelle für den Asset-Wert von WA104099688 die Office Store-Webseiten-URL für das Add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="e9b08-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="e9b08-140">Die Werte für den __ Parameter Locale und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, in der Sie das Add-in installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e9b08-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="e9b08-141">Das Format lautet en-US, fr-fr.</span><span class="sxs-lookup"><span data-stu-id="e9b08-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="e9b08-142">usw.</span><span class="sxs-lookup"><span data-stu-id="e9b08-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e9b08-143">Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e9b08-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="e9b08-144">Abrufen von Details eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-144">Get details of an add-in</span></span>
<span data-ttu-id="e9b08-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-145"></span></span>

<span data-ttu-id="e9b08-146">Führen Sie das Get-OrganizationAddIn-Cmdlet wie unten gezeigt aus, um Details zu allen Add-Ins abzurufen, die an den Mandanten hochgeladen wurden, und enthalten die Produkt-ID des Add-Ins.</span><span class="sxs-lookup"><span data-stu-id="e9b08-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="e9b08-147">Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den Parameter _ProductID_ aus, um anzugeben, für welches Add-in Details abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e9b08-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="e9b08-148">Wenn Sie alle Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen erhalten möchten, übergeben Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9b08-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="e9b08-149">Aktivieren oder Deaktivieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="e9b08-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-150"></span></span>

<span data-ttu-id="e9b08-151">Zum Deaktivieren eines Add-Ins, damit Benutzer und Gruppen, die ihm zugewiesen sind, keinen Zugriff mehr haben, führen Sie das Cmdlet Set-OrganizationAddIn mit dem Parameter _ProductID_ und dem Parameter _Enabled_ auf `$false`auf, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9b08-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="e9b08-152">Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus __ , wobei der Parameter `$true`Enabled auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e9b08-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="e9b08-153">Hinzufügen oder Entfernen von Benutzern aus einem Add-in</span><span class="sxs-lookup"><span data-stu-id="e9b08-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="e9b08-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-154"></span></span>

<span data-ttu-id="e9b08-155">Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet Set-OrganizationAddInAssignments mit den Parametern _ProductID_, _Add_und _Members_ aus.</span><span class="sxs-lookup"><span data-stu-id="e9b08-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="e9b08-156">Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="e9b08-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e9b08-157">Um Benutzer und Gruppen zu entfernen, führen Sie dasselbe Cmdlet mit dem Parameter _Remove_ aus.</span><span class="sxs-lookup"><span data-stu-id="e9b08-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e9b08-158">Um allen Benutzern des Mandanten ein Add-in zuzuweisen, führen Sie dasselbe Cmdlet mit dem Parameter _AssignToEveryone_ mit dem Wert auf `$true`.</span><span class="sxs-lookup"><span data-stu-id="e9b08-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="e9b08-159">Sie können dasselbe Cmdlet ausführen und den _AssignToEveryone_ -Parameter deaktivieren, indem Sie seinen Wert auf `$false`festlegen, um keinem Benutzer ein Add-in zuzuweisen und zu den zuvor zugewiesenen Benutzern und Gruppen zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="e9b08-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="e9b08-160">Aktualisieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-160">Update an add-in</span></span>
<span data-ttu-id="e9b08-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-161"></span></span>

<span data-ttu-id="e9b08-162">Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet Set-OrganizationAddIn mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9b08-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="e9b08-163">Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e9b08-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="e9b08-164">Löschen eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="e9b08-164">Delete an add-in</span></span>
<span data-ttu-id="e9b08-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-165"></span></span>

<span data-ttu-id="e9b08-166">Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e9b08-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="e9b08-167">Ausführliche Hilfe zu den einzelnen Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e9b08-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="e9b08-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="e9b08-168"></span></span>

<span data-ttu-id="e9b08-169">Ausführliche Hilfe zu den einzelnen Cmdlets finden Sie unter Verwendung des Cmdlets Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e9b08-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="e9b08-170">Das folgende Cmdlet enthält beispielsweise detaillierte Informationen zum Cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="e9b08-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


