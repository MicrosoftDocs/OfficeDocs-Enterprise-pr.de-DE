---
title: Verwalten von Microsoft 365-Mandanten mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Microsoft 365, um Ihre Kundenmandanten zu verwalten.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998231"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="f69d4-103">Verwalten von Microsoft 365-Mandanten mit Windows PowerShell für Partner mit Delegierten Zugriffsberechtigungen (Delegated Access Permission, DAP)</span><span class="sxs-lookup"><span data-stu-id="f69d4-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="f69d4-104">Windows PowerShell ermöglicht es den Anbietern von Syndication-und Cloud Solution Providern (CSP), Kundenmandanten Einstellungen, die im Microsoft 365 Admin Center nicht verfügbar sind, einfach zu verwalten und zu melden.</span><span class="sxs-lookup"><span data-stu-id="f69d4-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="f69d4-105">Beachten Sie, dass für das Partneradministrator Konto die Berechtigung verwalten im Namen von (AOBO) erforderlich ist, um eine Verbindung mit dem Mandanten des Kunden herzustellen.</span><span class="sxs-lookup"><span data-stu-id="f69d4-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="f69d4-106">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="f69d4-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="f69d4-107">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="f69d4-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="f69d4-108">Sie bündeln Microsoft 365-Abonnements für Ihre Kunden in ihren Dienst angeboten.</span><span class="sxs-lookup"><span data-stu-id="f69d4-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="f69d4-109">Wenn Sie ein Microsoft 365-Abonnement verkaufen, werden Ihnen automatisch Administratoren im Namen von (AOBO) Berechtigungen für den Kundenmandanten erteilt, damit Sie den Kundenmandanten verwalten und melden können.</span><span class="sxs-lookup"><span data-stu-id="f69d4-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f69d4-110">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="f69d4-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="f69d4-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="f69d4-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="f69d4-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f69d4-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="f69d4-113">Sie benötigen auch die Administratoranmeldeinformationen Ihres Partnermandanten.</span><span class="sxs-lookup"><span data-stu-id="f69d4-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="f69d4-114">Was möchten Sie machen?</span><span class="sxs-lookup"><span data-stu-id="f69d4-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="f69d4-115">Auflisten aller Mandanten-IDs</span><span class="sxs-lookup"><span data-stu-id="f69d4-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="f69d4-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span><span class="sxs-lookup"><span data-stu-id="f69d4-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span></span> <span data-ttu-id="f69d4-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="f69d4-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="f69d4-118">Führen Sie den folgenden Befehl aus, um alle Kundenmandanten-IDs aufzulisten, auf die Sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="f69d4-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="f69d4-119">Dies zeigt eine Liste aller Kundenmandanten nach **TenantId** geordnet an.</span><span class="sxs-lookup"><span data-stu-id="f69d4-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="f69d4-120">PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen.</span><span class="sxs-lookup"><span data-stu-id="f69d4-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f69d4-121">Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.</span><span class="sxs-lookup"><span data-stu-id="f69d4-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="f69d4-122">Abrufen einer Mandanten-ID mithilfe des Domänennamens</span><span class="sxs-lookup"><span data-stu-id="f69d4-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="f69d4-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span><span class="sxs-lookup"><span data-stu-id="f69d4-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span></span> <span data-ttu-id="f69d4-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span><span class="sxs-lookup"><span data-stu-id="f69d4-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="f69d4-125">Auflisten aller Domänen für einen Mandanten</span><span class="sxs-lookup"><span data-stu-id="f69d4-125">List all domains for a tenant</span></span>

<span data-ttu-id="f69d4-126">To get all domains for any one customer tenant, run this command.</span><span class="sxs-lookup"><span data-stu-id="f69d4-126">To get all domains for any one customer tenant, run this command.</span></span> <span data-ttu-id="f69d4-127">Replace  _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="f69d4-127">Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="f69d4-128">Wenn Sie zusätzliche Domänen registriert haben, werden alle Domänen zurückgegeben, die mit der **TenantId** des Kunden verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="f69d4-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="f69d4-129">Abrufen einer Zuordnung aller Mandanten und registrierten Domänen</span><span class="sxs-lookup"><span data-stu-id="f69d4-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="f69d4-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span><span class="sxs-lookup"><span data-stu-id="f69d4-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="f69d4-131">This command generates a listing of all your customer tenant IDs and their domains.</span><span class="sxs-lookup"><span data-stu-id="f69d4-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="f69d4-132">Abrufen aller Benutzer für einen Mandanten</span><span class="sxs-lookup"><span data-stu-id="f69d4-132">Get all users for a tenant</span></span>

<span data-ttu-id="f69d4-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span><span class="sxs-lookup"><span data-stu-id="f69d4-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span></span> <span data-ttu-id="f69d4-134">Replace _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="f69d4-134">Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="f69d4-135">Abrufen aller Details eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="f69d4-135">Get all details about a user</span></span>

<span data-ttu-id="f69d4-136">If you want to see all the properties of a particular user, run this command.</span><span class="sxs-lookup"><span data-stu-id="f69d4-136">If you want to see all the properties of a particular user, run this command.</span></span> <span data-ttu-id="f69d4-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span><span class="sxs-lookup"><span data-stu-id="f69d4-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="f69d4-138">Hinzufügen von Benutzern, Festlegen von Optionen und Zuweisen von Lizenzen</span><span class="sxs-lookup"><span data-stu-id="f69d4-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="f69d4-139">Die Massenerstellung, Konfiguration und Lizenzierung von Microsoft 365-Benutzern ist besonders effizient, indem Windows PowerShell für Office 365 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f69d4-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="f69d4-140">Bei diesem Verfahren, das nur zwei Schritte umfasst, erstellen Sie zuerst Einträge für alle hinzuzufügenden Benutzer in einer CSV-Datei und importieren diese Datei dann mithilfe von Windows PowerShell für Office 365.</span><span class="sxs-lookup"><span data-stu-id="f69d4-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="f69d4-141">Erstellen einer CSV-Datei</span><span class="sxs-lookup"><span data-stu-id="f69d4-141">Create a CSV file</span></span>

<span data-ttu-id="f69d4-142">Erstellen Sie eine CSV-Datei anhand dieses Formats:</span><span class="sxs-lookup"><span data-stu-id="f69d4-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="f69d4-143">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="f69d4-143">where:</span></span>
  
- <span data-ttu-id="f69d4-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span><span class="sxs-lookup"><span data-stu-id="f69d4-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span></span> <span data-ttu-id="f69d4-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span><span class="sxs-lookup"><span data-stu-id="f69d4-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span></span> <span data-ttu-id="f69d4-146">For example, the code for the United States is US, and the code for Brazil is BR.</span><span class="sxs-lookup"><span data-stu-id="f69d4-146">For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="f69d4-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span><span class="sxs-lookup"><span data-stu-id="f69d4-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span></span> <span data-ttu-id="f69d4-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span><span class="sxs-lookup"><span data-stu-id="f69d4-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span></span> <span data-ttu-id="f69d4-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span><span class="sxs-lookup"><span data-stu-id="f69d4-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="f69d4-150">Importieren der CSV-Datei und Erstellen der Benutzer</span><span class="sxs-lookup"><span data-stu-id="f69d4-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="f69d4-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span><span class="sxs-lookup"><span data-stu-id="f69d4-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span></span> <span data-ttu-id="f69d4-152">Be sure to substitute the correct CSV file name.</span><span class="sxs-lookup"><span data-stu-id="f69d4-152">Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="f69d4-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f69d4-153">See also</span></span>

#### 

[<span data-ttu-id="f69d4-154">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="f69d4-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

