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
- MET150
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Verwenden Sie die PowerShell-Cmdlets für zentralisierte Bereitstellung, um die Bereitstellung und Verwaltung von Office-Add-Ins für Ihre Office 365 Organisation zu erleichtern.
ms.openlocfilehash: 3e3ca622f4c7a84d1fb267880ebf13cc56ad9373
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004498"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="38c18-103">Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins</span><span class="sxs-lookup"><span data-stu-id="38c18-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="38c18-104">Als Office 365 Administrator können Sie Office-Add-Ins für Benutzer über das zentralisierte Bereitstellungsfeature bereitstellen (siehe [Verwalten der Bereitstellung von Office 365-Add-Ins im Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="38c18-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="38c18-105">Neben der Bereitstellung von Office-Add-Ins über das Admin Center können Sie auch Microsoft PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="38c18-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="38c18-106">[Laden](https://go.microsoft.com/fwlink/p/?linkid=850850) Sie die PowerShell-Cmdlets für zentralisierte Bereitstellung aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="38c18-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="38c18-107">Was möchten Sie machen?</span><span class="sxs-lookup"><span data-stu-id="38c18-107">What do you want to do?</span></span>

[<span data-ttu-id="38c18-108">Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="38c18-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="38c18-109">Hochladen eines Add-in-Manifests</span><span class="sxs-lookup"><span data-stu-id="38c18-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="38c18-110">Hochladen eines Add-Ins aus dem Office Store</span><span class="sxs-lookup"><span data-stu-id="38c18-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="38c18-111">Abrufen von Details eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="38c18-112">Aktivieren oder Deaktivieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="38c18-113">Hinzufügen oder Entfernen von Benutzern aus einem Add-in</span><span class="sxs-lookup"><span data-stu-id="38c18-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="38c18-114">Aktualisieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="38c18-115">Löschen eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="38c18-116">Ausführliche Hilfe zu jedem Cmdlet erhalten</span><span class="sxs-lookup"><span data-stu-id="38c18-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="38c18-117">Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="38c18-117">Connect using your admin credentials</span></span>
<span data-ttu-id="38c18-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="38c18-119">Bevor Sie die Cmdlets für die zentrale Bereitstellung verwenden können, müssen Sie sich anmelden.</span><span class="sxs-lookup"><span data-stu-id="38c18-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="38c18-120">Starten Sie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38c18-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="38c18-121">Stellen Sie eine Verbindung mit PowerShell mithilfe ihrer Unternehmensadministrator Anmeldeinformationen her.</span><span class="sxs-lookup"><span data-stu-id="38c18-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="38c18-122">Führen Sie das folgende Cmdlet aus.</span><span class="sxs-lookup"><span data-stu-id="38c18-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="38c18-123">Geben Sie auf der Seite **Anmeldeinformationen eingeben** Ihre Office 365 globale Administratoranmeldeinformationen ein.</span><span class="sxs-lookup"><span data-stu-id="38c18-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="38c18-124">Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben.</span><span class="sxs-lookup"><span data-stu-id="38c18-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="38c18-125">Führen Sie das folgende Cmdlet aus, das die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt angibt.</span><span class="sxs-lookup"><span data-stu-id="38c18-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="38c18-126">Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="38c18-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="38c18-127">Hochladen eines Add-in-Manifests</span><span class="sxs-lookup"><span data-stu-id="38c18-127">Upload an add-in manifest</span></span>
<span data-ttu-id="38c18-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="38c18-129">Führen Sie das Cmdlet New-organisationadd-in aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, bei dem es sich entweder um einen Dateispeicherort oder eine URL handeln kann.</span><span class="sxs-lookup"><span data-stu-id="38c18-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="38c18-130">Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters.</span><span class="sxs-lookup"><span data-stu-id="38c18-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="38c18-131">Sie können auch das New-organisationadd-in-Cmdlet ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt mithilfe des _Members_ -Parameters zuzuweisen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="38c18-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="38c18-132">Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="38c18-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="38c18-133">Hochladen eines Add-Ins aus dem Office Store</span><span class="sxs-lookup"><span data-stu-id="38c18-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="38c18-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="38c18-135">Führen Sie das Cmdlet New-OrganizationAddIn aus, um ein Manifest aus dem Office Store hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="38c18-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="38c18-136">Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn die Asset-Nr für ein Add-in für einen Standort und einen Inhalts Markt in USA an.</span><span class="sxs-lookup"><span data-stu-id="38c18-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="38c18-137">Um den Wert für den Parameter _Asset_ -Nr zu ermitteln, können Sie ihn aus der URL der Office Store Webseite für das Add-in kopieren.</span><span class="sxs-lookup"><span data-stu-id="38c18-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="38c18-138">AssetIds beginnen immer mit "WA", gefolgt von einer Zahl.</span><span class="sxs-lookup"><span data-stu-id="38c18-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="38c18-139">Im vorherigen Beispiel ist beispielsweise die Quelle für den Wert der WA104099688-Website die URL für das Add-in Office Store Webseite: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="38c18-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="38c18-140">Die Werte für den Parameter _locale_ und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, aus dem das Add-in installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="38c18-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="38c18-141">Das Format lautet en-US, fr-fr.</span><span class="sxs-lookup"><span data-stu-id="38c18-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="38c18-142">und so weiter.</span><span class="sxs-lookup"><span data-stu-id="38c18-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="38c18-143">Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="38c18-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="38c18-144">Abrufen von Details eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-144">Get details of an add-in</span></span>
<span data-ttu-id="38c18-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="38c18-146">Führen Sie das Get-OrganizationAddIn-Cmdlet wie unten beschrieben aus, um Details zu allen Add-Ins abzurufen, die in den Mandanten hochgeladen wurden und die Produkt-ID eines Add-Ins enthalten.</span><span class="sxs-lookup"><span data-stu-id="38c18-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="38c18-147">Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den _ProductID_ -Parameter aus, um anzugeben, für welches Add-in Sie Details abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="38c18-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="38c18-148">Um vollständige Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen zu erhalten, übergeben Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="38c18-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="38c18-149">Aktivieren oder Deaktivieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="38c18-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="38c18-151">Wenn Sie ein Add-in deaktivieren möchten, sodass Benutzern und Gruppen, denen es zugewiesen ist, kein Zugriff mehr gewährt wird, führen Sie das Cmdlet "OrganizationAddIn" mit dem Parameter " _ProductID_ " `$false`und dem Parameter " _Enabled_ " aus, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="38c18-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="38c18-152">Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus _Enabled_ , wobei der Parameter `$true`Enabled auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="38c18-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="38c18-153">Hinzufügen oder Entfernen von Benutzern aus einem Add-in</span><span class="sxs-lookup"><span data-stu-id="38c18-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="38c18-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="38c18-155">Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet "OrganizationAddInAssignments" mit den Parametern " _ProductID_", " _Add_" und " _Members_ " aus.</span><span class="sxs-lookup"><span data-stu-id="38c18-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="38c18-156">Trennen Sie die e-Mail-Adressen von Elementen durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="38c18-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="38c18-157">Wenn Sie Benutzer und Gruppen entfernen möchten, führen Sie das gleiche Cmdlet mit dem _Remove_ -Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="38c18-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="38c18-158">Um ein Add-in allen Benutzern im Mandanten zuzuweisen, führen Sie das gleiche Cmdlet mit dem _AssignToEveryone_ -Parameter aus, wobei `$true`der Wert auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="38c18-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="38c18-159">Um kein Add-in allen Benutzern zuzuweisen und die zuvor zugewiesenen Benutzer und Gruppen wiederherzustellen, können Sie dasselbe Cmdlet ausführen und den Parameter _AssignToEveryone_ deaktivieren, indem Sie seinen Wert auf `$false`festlegen.</span><span class="sxs-lookup"><span data-stu-id="38c18-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="38c18-160">Aktualisieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-160">Update an add-in</span></span>
<span data-ttu-id="38c18-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="38c18-162">Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet "OrganizationAddIn" mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="38c18-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="38c18-163">Aus dem Office Store hochgeladene Add-Ins werden automatisch innerhalb von ein paar Tagen nach der Verfügbarkeit des neuesten Updates im Office Store aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="38c18-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="38c18-164">Löschen eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="38c18-164">Delete an add-in</span></span>
<span data-ttu-id="38c18-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="38c18-166">Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="38c18-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="38c18-167">Ausführliche Hilfe zu jedem Cmdlet erhalten</span><span class="sxs-lookup"><span data-stu-id="38c18-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="38c18-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="38c18-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="38c18-169">Sie können die detaillierte Hilfe zu jedem Cmdlet mithilfe des Cmdlets Get-Help betrachten.</span><span class="sxs-lookup"><span data-stu-id="38c18-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="38c18-170">Beispielsweise enthält das folgende Cmdlet ausführliche Informationen zum Cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="38c18-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


