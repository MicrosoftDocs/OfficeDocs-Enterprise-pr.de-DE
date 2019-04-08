---
title: Verwalten von Office 365-Mandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Zusammenfassung: Verwenden Sie Windows PowerShell für Office 365 zum Verwalten von Kundenmandanten.'
ms.openlocfilehash: 4fec058bfd7b7dffa2c29add23d99a144f78decf
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001858"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="cdd8a-103">Verwalten von Office 365-Mandanten mit Windows PowerShell für Partner mit delegierten Zugriffsberechtigungen (Delegated Access Permissions, DAP)</span><span class="sxs-lookup"><span data-stu-id="cdd8a-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="cdd8a-104">**Zusammenfassung:** Verwenden Sie Windows PowerShell für Office 365 zum Verwalten von Kundenmandanten.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="cdd8a-p101">Windows PowerShell ermöglicht Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP) die einfache Verwaltung von Kundenmandanteneinstellungen sowie die Berichterstellung dazu. Dies ist in der Office 365 Admin Center nicht verfügbar. Beachten Sie, dass die Berechtigungen „Verwalten im Namen von" (Administer On Behalf Of, AOBO) für das Administratorkonto des Partners notwendig sind, um eine Verbindung mit seinem Kundenmandanten herstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="cdd8a-107">DAP-Partner (Delegated Access Permission, delegierte Zugriffsberechtigung) sind Syndication-Partner und Cloudlösungsanbieter (Cloud Solution Providers, CSP).</span><span class="sxs-lookup"><span data-stu-id="cdd8a-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="cdd8a-108">Häufig handelt es sich um Netzwerk- oder Telekom-Anbieter für andere Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="cdd8a-109">Sie bündeln Office 365-Abonnements in Serviceangeboten für ihre Kunden.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-109">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="cdd8a-110">Wenn sie ein Office 365-Abonnement verkaufen, erhalten sie automatisch AOBO-Berechtigungen (Administer On Behalf Of, Verwalten im Namen von) für die Kundenmandanten, damit sie diese verwalten und Berichte darüber erstellen können.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-110">When they sell an O365_W14_2nd subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="cdd8a-111">Was sollten Sie wissen, bevor Sie beginnen?</span><span class="sxs-lookup"><span data-stu-id="cdd8a-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="cdd8a-p103">Für die Verfahren in diesem Thema müssen Sie eine Verbindung mit Windows PowerShell für Office 365 herstellen. Weitere Anweisungen finden Sie unter [Verbinden mit Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="cdd8a-114">Sie benötigen auch die Administratoranmeldeinformationen Ihres Partnermandanten.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="cdd8a-115">Was möchten Sie machen?</span><span class="sxs-lookup"><span data-stu-id="cdd8a-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="cdd8a-116">Auflisten aller Mandanten-IDs</span><span class="sxs-lookup"><span data-stu-id="cdd8a-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="cdd8a-p104">Wenn Sie über mehr als 500 Mandanten verfügen, fügen Sie in die Cmdlet-Syntax entweder  _-All_ oder _-MaxResultsParameter_ ein. Dies gilt für andere Cmdlets mit einer umfangreichen Ausgabe, wie z. B. **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="cdd8a-119">Führen Sie den folgenden Befehl aus, um alle Kundenmandanten-IDs aufzulisten, auf die Sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="cdd8a-120">Dies zeigt eine Liste aller Kundenmandanten nach **TenantId** geordnet an.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="cdd8a-121">Abrufen einer Mandanten-ID mithilfe des Domänennamens</span><span class="sxs-lookup"><span data-stu-id="cdd8a-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="cdd8a-p105">Zum Abrufen der **TenantId** eines bestimmten Kundenmandanten nach Domänenname führen Sie den folgenden Befehl aus. Ersetzen Sie _<domänenname.onmicrosoft.com>_ durch den eigentlichen Domänennamen des gewünschten Kundenmandanten.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="cdd8a-124">Auflisten aller Domänen für einen Mandanten</span><span class="sxs-lookup"><span data-stu-id="cdd8a-124">List all domains for a tenant</span></span>

<span data-ttu-id="cdd8a-p106">Um alle Domänen für einen einzigen Kundenmandanten aufzurufen, führen Sie den folgenden Befehl aus. Ersetzen Sie  _<customer TenantId value>_ durch den eigentlichen Wert.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="cdd8a-127">Wenn Sie zusätzliche Domänen registriert haben, werden alle Domänen zurückgegeben, die mit der **TenantId** des Kunden verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="cdd8a-128">Abrufen einer Zuordnung aller Mandanten und registrierten Domänen</span><span class="sxs-lookup"><span data-stu-id="cdd8a-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="cdd8a-p107">Die vorherigen Befehle von Windows PowerShell für Office 365 haben Ihnen gezeigt, wie Sie entweder die Mandanten-IDs oder die Domänen, jedoch nicht beides gleichzeitg abrufen können. Außerdem geben sie die Zuordnung von Mandanten-ID und Domäne nicht an. Dieser Befehl generiert eine Liste aller Kundenmandanten-IDs und ihrer Domänen.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="cdd8a-131">Abrufen aller Benutzer für einen Mandanten</span><span class="sxs-lookup"><span data-stu-id="cdd8a-131">Get all users for a tenant</span></span>

<span data-ttu-id="cdd8a-p108">Hierdurch werden der **UserPrincipalName**, der **DisplayName** und der Status **isLicensed** für alle Benutzer eines bestimmten Mandanten angezeigt. Ersetzen Sie _<customer TenantId value>_ durch den eigentlichen Wert.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="cdd8a-134">Abrufen aller Details eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="cdd8a-134">Get all details about a user</span></span>

<span data-ttu-id="cdd8a-p109">Wenn Sie alle Eigenschaften eines bestimmten Benutzers anzeigen möchten, führen Sie den folgenden Befehl aus:  Ersetzen Sie _<customer TenantId value>_ und _<user principal name value>_ durch die eigentlichen Werte.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="cdd8a-137">Hinzufügen von Benutzern, Festlegen von Optionen und Zuweisen von Lizenzen</span><span class="sxs-lookup"><span data-stu-id="cdd8a-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="cdd8a-p110">Die Massenerstellung, -konfiguration und -lizenzierung von Office 365-Benutzern kann mit Windows PowerShell für Office 365 besonders effizient durchgeführt werden. Bei diesem Verfahren, das nur zwei Schritte umfasst, erstellen Sie zuerst Einträge für alle hinzuzufügenden Benutzer in einer CSV-Datei und importieren diese Datei dann mithilfe von Windows PowerShell für Office 365.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="cdd8a-140">Erstellen einer CSV-Datei</span><span class="sxs-lookup"><span data-stu-id="cdd8a-140">Create a CSV file</span></span>

<span data-ttu-id="cdd8a-141">Erstellen Sie eine CSV-Datei anhand dieses Formats:</span><span class="sxs-lookup"><span data-stu-id="cdd8a-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="cdd8a-142">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="cdd8a-142">where:</span></span>
  
- <span data-ttu-id="cdd8a-p111">**UsageLocation**: Der Wert hierfür ist der zweistellige ISO-Länder-/Regionscode des Benutzers. Die Länder-/Regioinscodes finden Sie auf der[ISO-Online-Browserplattform](https://go.microsoft.com/fwlink/p/?LinkId=532703). Der Code für die Vereinigten Staaten lautet z. B. „US", der Code für Brasilien „BR".</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="cdd8a-p112">**LicenseAssignment**: Der Wert hierfür verwendet das folgende Format: `syndication-account:<PROVISIONING_ID>`. Wenn Sie Kundenmandantenbenutzern zum Beispiel O365_Business_Premium-Lizenzen zuweisen, sieht der Wert **LicenseAssignment** wie folgt aus: **syndication-account:O365_Business_Premium**. Sie finden die PROVISIONING_IDs im Syndication-Partnerportal, auf das Sie als Syndication- oder CSP-Partner Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="cdd8a-149">Importieren der CSV-Datei und Erstellen der Benutzer</span><span class="sxs-lookup"><span data-stu-id="cdd8a-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="cdd8a-p113">Nachdem Sie die CSV-Datei erstellt haben, führen Sie den folgenden Befehl zum Erstellen von Benutzerkonten mit nicht ablaufenden Kennwörtern aus. Der Benutzer muss das Kennwort beim ersten Anmelden ändern, und es weist ihm die ausgewählte Lizenz zu. Achten Sie darauf, dass Sie den richtigen Namen der CSV-Datei angeben.</span><span class="sxs-lookup"><span data-stu-id="cdd8a-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="cdd8a-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cdd8a-152">See also</span></span>

#### 

[<span data-ttu-id="cdd8a-153">Hilfe für Partner</span><span class="sxs-lookup"><span data-stu-id="cdd8a-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

