---
title: Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins
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
description: Verwenden Sie die PowerShell-Cmdlets der zentralisierten Bereitstellung, um Sie beim Bereitstellen und Verwalten von Office-Add-Ins für Ihre Office 365-Organisation zu unterstützen.
ms.openlocfilehash: ec851fc85273e9f871c20d5075b16cb97472f975
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957636"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="68fcf-103">Verwenden der PowerShell-Cmdlets für zentrale Bereitstellung zum Verwalten von Add-Ins</span><span class="sxs-lookup"><span data-stu-id="68fcf-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="68fcf-104">Als Office 365-Administrator können Sie Office-Add-Ins über das zentralisierte Bereitstellungsfeature für Benutzer bereitstellen (Weitere Informationen finden Sie unter [Deploy Office Add-Ins in office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="68fcf-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="68fcf-105">Zusätzlich zur Bereitstellung von Office-Add-Ins über das Office 365 Admin Center können Sie auch Microsoft PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="68fcf-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="68fcf-106">Installieren [Sie das zentralisierte O365-Add-in-Bereitstellungsmodul für Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="68fcf-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="68fcf-107">Herstellen einer Verbindung mit Ihren Administratoranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="68fcf-107">Connect using your admin credentials</span></span>

<span data-ttu-id="68fcf-108">Bevor Sie die zentralisierten Bereitstellungs-Cmdlets verwenden können, müssen Sie sich anmelden.</span><span class="sxs-lookup"><span data-stu-id="68fcf-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="68fcf-109">Starten Sie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68fcf-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="68fcf-110">Stellen Sie mithilfe der Anmeldeinformationen Ihres Unternehmens eine Verbindung zu PowerShell her.</span><span class="sxs-lookup"><span data-stu-id="68fcf-110">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="68fcf-111">Führen Sie das folgende Cmdlet aus.</span><span class="sxs-lookup"><span data-stu-id="68fcf-111">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="68fcf-112">Geben Sie auf der Seite **Anmeldeinformationen eingeben** ihre Office 365-Anmeldeinformationen für den globalen Administrator ein.</span><span class="sxs-lookup"><span data-stu-id="68fcf-112">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="68fcf-113">Alternativ können Sie Ihre Anmeldeinformationen direkt in das Cmdlet eingeben.</span><span class="sxs-lookup"><span data-stu-id="68fcf-113">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="68fcf-114">Führen Sie das folgende Cmdlet aus, um die Anmeldeinformationen Ihres Unternehmens als PSCredential-Objekt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="68fcf-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="68fcf-115">Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="68fcf-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="68fcf-116">Hochladen eines Add-in-Manifests</span><span class="sxs-lookup"><span data-stu-id="68fcf-116">Upload an add-in manifest</span></span>

<span data-ttu-id="68fcf-117">Führen Sie das Cmdlet New-Organisationadd-in aus, um ein Add-in-Manifest aus einem Pfad hochzuladen, der entweder ein Dateispeicherort oder eine URL sein kann.</span><span class="sxs-lookup"><span data-stu-id="68fcf-117">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="68fcf-118">Das folgende Beispiel zeigt einen Dateispeicherort für den Wert des _ManifestPath_ -Parameters.</span><span class="sxs-lookup"><span data-stu-id="68fcf-118">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="68fcf-119">Sie können auch das Cmdlet New-Organisationadd-in ausführen, um ein Add-in hochzuladen und es Benutzern oder Gruppen direkt zuzuweisen, indem Sie den Parameter _Members_ verwenden, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="68fcf-119">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="68fcf-120">Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="68fcf-120">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="68fcf-121">Hochladen eines Add-Ins aus dem Office Store</span><span class="sxs-lookup"><span data-stu-id="68fcf-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="68fcf-122">Führen Sie das Cmdlet New-OrganizationAddIn aus, um ein Manifest aus dem Office Store hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="68fcf-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="68fcf-123">Im folgenden Beispiel gibt das Cmdlet New-OrganizationAddIn die Ressourcen-Nr. für ein Add-in für einen US-Standort-und-Inhalts Markt an.</span><span class="sxs-lookup"><span data-stu-id="68fcf-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="68fcf-124">Um den Wert für den Parameter _Asset_ -Nr zu bestimmen, können Sie ihn aus der URL der Office Store-Webseite für das Add-in kopieren.</span><span class="sxs-lookup"><span data-stu-id="68fcf-124">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="68fcf-125">AssetIds beginnen immer mit "WA" gefolgt von einer Zahl.</span><span class="sxs-lookup"><span data-stu-id="68fcf-125">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="68fcf-126">Im vorherigen Beispiel ist die Quelle für den Asset-Wert von WA104099688 die Office Store-Webseiten-URL für das Add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="68fcf-126">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="68fcf-127">Die Werte für den __ Parameter Locale und den Parameter _ContentMarket_ sind identisch und geben das Land/die Region an, in der Sie das Add-in installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="68fcf-127">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="68fcf-128">Das Format lautet en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="68fcf-128">The format is en-US, fr-FR.</span></span> <span data-ttu-id="68fcf-129">usw.</span><span class="sxs-lookup"><span data-stu-id="68fcf-129">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="68fcf-130">Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="68fcf-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="68fcf-131">Abrufen von Details eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="68fcf-131">Get details of an add-in</span></span>

<span data-ttu-id="68fcf-132">Führen Sie das Get-OrganizationAddIn-Cmdlet wie unten gezeigt aus, um Details zu allen Add-Ins abzurufen, die an den Mandanten hochgeladen wurden, und enthalten die Produkt-ID des Add-Ins.</span><span class="sxs-lookup"><span data-stu-id="68fcf-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="68fcf-133">Führen Sie das Cmdlet Get-OrganizationAddIn mit einem Wert für den Parameter _ProductID_ aus, um anzugeben, für welches Add-in Details abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="68fcf-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="68fcf-134">Wenn Sie alle Informationen zu allen Add-Ins sowie den zugewiesenen Benutzern und Gruppen erhalten möchten, übergeben Sie die Ausgabe des Cmdlets Get-OrganizationAddIn an das Cmdlet Format-List, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="68fcf-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="68fcf-135">Aktivieren oder Deaktivieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="68fcf-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="68fcf-136">Zum Deaktivieren eines Add-Ins, damit Benutzer und Gruppen, die ihm zugewiesen sind, keinen Zugriff mehr haben, führen Sie das Cmdlet Set-OrganizationAddIn mit dem Parameter _ProductID_ und dem Parameter _Enabled_ auf `$false`auf, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="68fcf-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="68fcf-137">Wenn Sie ein Add-in wieder aktivieren möchten, führen Sie dasselbe Cmdlet aus __ , wobei der Parameter `$true`Enabled auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="68fcf-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="68fcf-138">Hinzufügen oder Entfernen von Benutzern aus einem Add-in</span><span class="sxs-lookup"><span data-stu-id="68fcf-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="68fcf-139">Zum Hinzufügen von Benutzern und Gruppen zu einem bestimmten Add-in führen Sie das Cmdlet Set-OrganizationAddInAssignments mit den Parametern _ProductID_, _Add_und _Members_ aus.</span><span class="sxs-lookup"><span data-stu-id="68fcf-139">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="68fcf-140">Trennen Sie die e-Mail-Adressen der Mitglieder durch ein Komma.</span><span class="sxs-lookup"><span data-stu-id="68fcf-140">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="68fcf-141">Um Benutzer und Gruppen zu entfernen, führen Sie dasselbe Cmdlet mit dem Parameter _Remove_ aus.</span><span class="sxs-lookup"><span data-stu-id="68fcf-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="68fcf-142">Um allen Benutzern des Mandanten ein Add-in zuzuweisen, führen Sie dasselbe Cmdlet mit dem Parameter _AssignToEveryone_ mit dem Wert auf `$true`.</span><span class="sxs-lookup"><span data-stu-id="68fcf-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="68fcf-143">Sie können dasselbe Cmdlet ausführen und den _AssignToEveryone_ -Parameter deaktivieren, indem Sie seinen Wert auf `$false`festlegen, um keinem Benutzer ein Add-in zuzuweisen und zu den zuvor zugewiesenen Benutzern und Gruppen zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="68fcf-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="68fcf-144">Aktualisieren eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="68fcf-144">Update an add-in</span></span>

<span data-ttu-id="68fcf-145">Um ein Add-in aus einem Manifest zu aktualisieren, führen Sie das Cmdlet Set-OrganizationAddIn mit den Parametern _ProductID_, _ManifestPath_und _locale_ aus, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="68fcf-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="68fcf-146">Vom Office Store hochgeladene Add-Ins werden automatisch innerhalb von wenigen Tagen aktualisiert, nachdem das neueste Update im Office Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="68fcf-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="68fcf-147">Löschen eines Add-ins</span><span class="sxs-lookup"><span data-stu-id="68fcf-147">Delete an add-in</span></span>

<span data-ttu-id="68fcf-148">Um ein Add-in zu löschen, führen Sie das Cmdlet Remove-OrganizationAddIn mit dem Parameter _ProductID_ aus, wie im folgenden Beispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="68fcf-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="68fcf-149">Ausführliche Hilfe zu den einzelnen Cmdlets</span><span class="sxs-lookup"><span data-stu-id="68fcf-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="68fcf-150">Ausführliche Hilfe zu den einzelnen Cmdlets finden Sie unter Verwendung des Cmdlets Get-Help.</span><span class="sxs-lookup"><span data-stu-id="68fcf-150">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="68fcf-151">Das folgende Cmdlet enthält beispielsweise detaillierte Informationen zum Cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="68fcf-151">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


