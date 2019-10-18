---
title: Konfigurieren von Office 365 Multi-Geo eDiscovery
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: So konfigurieren Sie eDiscovery in Office 365 Multi-Geo.
ms.openlocfilehash: f9d8fe8b65f5772005bf7d6a7ea3735277077d3b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069961"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="1aab8-103">Konfiguration von Office 365 Multi-Geo eDiscovery</span><span class="sxs-lookup"><span data-stu-id="1aab8-103">Office 365 Multi-Geo eDiscovery configuration</span></span>


<span data-ttu-id="1aab8-p101">Standardmäßig kann ein eDiscovery-Manager oder Administrator eines Multi-Geo-Mandaten eDiscovery nur an der zentralen Stelle dieses Mandanten durchführen. Um eDiscovery für Satellitenstandorte durchführen zu können, steht ein neuer Parameter des Compliancesicherheitsfilters namens „Region“ über PowerShell zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1aab8-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="1aab8-106">Der globale Office 365-Administrator muss eDiscovery-Managerberechtigungen zuweisen, damit andere Personen eDiscovery durchführen können, und einen „Region“-Parameter im entsprechenden Compliancesicherheitsfilter zuweisen, um die Region zum Durchführen von eDiscovery als Satellitenstandort festzulegen. Andernfalls wird eDiscovery nicht für den Satellitenstandort durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1aab8-106">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="1aab8-p102">Wenn die eDiscovery-Manager- oder Administratorrolle für einen bestimmten Satellitenstandort festgelegt ist, kann der eDiscovery-Manager oder Administrator nur eDiscovery-Suchaktionen für die SharePoint-Websites und OneDrive-Websites an diesem Satellitenstandort durchführen. Wenn ein eDiscovery-Manager oder Administrator versucht, SharePoint- oder OneDrive-Websites außerhalb des angegebenen Satellitenstandorts zu durchsuchen, werden keine Ergebnisse zurückgegeben. Wenn der eDiscovery-Manager oder Administrator für einen Satellitenstandort einen Export auslöst, werden Daten in der Azure-Instanz dieses Bereichs exportiert. So können Organisationen Compliance gewährleisten, indem nicht zugelassen wird, dass Inhalte über den kontrollierten Rahmen hinaus exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="1aab8-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="1aab8-111">Wenn ein eDiscovery-Manager mehrere SharePoint-Satellitenstandorte durchsuchen möchte, muss ein anderes Benutzerkonto für den eDiscovery-Manager erstellt werden, das den alternativen Satellitenstandort angibt, in dem sich OneDrive- oder SharePoint-Websites befinden.</span><span class="sxs-lookup"><span data-stu-id="1aab8-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="1aab8-112">So legen Sie den Compliancesicherheitsfilter für eine Region fest</span><span class="sxs-lookup"><span data-stu-id="1aab8-112">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="1aab8-113">Öffnen Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1aab8-113">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="1aab8-114">Geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1aab8-114">Enter</span></span>  
    <span data-ttu-id="1aab8-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="1aab8-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="1aab8-116">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="1aab8-116">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="1aab8-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="1aab8-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="1aab8-118">Beispiel: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="1aab8-118">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="1aab8-119">Informationen zu weiteren Parametern und zur Syntax finden Sie im Artikel [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx).</span><span class="sxs-lookup"><span data-stu-id="1aab8-119">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>
