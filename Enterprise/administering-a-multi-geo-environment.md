---
title: Verwalten einer Multi-Geo-Umgebung
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Dieser Artikel enthält Informationen über die Verwaltung von SharePoint- und OneDrive-Diensten in einer Multi-Geo-Umgebung.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="6d8ce-103">Verwalten einer Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="6d8ce-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="6d8ce-104">In diesem Artikel wird die Funktionsweise von OneDrive- und SharePoint-Diensten in einer Multi-Geo-Umgebung erläutert.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="6d8ce-105">OneDrive-Administratorumgebung</span><span class="sxs-lookup"><span data-stu-id="6d8ce-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="6d8ce-p101">Das [OneDrive Admin Center](https://admin.onedrive.com) verfügt im linken Navigationsbereich über die Registerkarte **Geografische Standorte**, die eine Karte mit geografischen Standorten enthält, auf der Sie Ihre geografischen Standorte anzeigen und verwalten können. Verwenden Sie diese Seite zum Hinzufügen oder Löschen von geografischen Standorten für Ihren Mandanten.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="6d8ce-108">Taxonomie</span><span class="sxs-lookup"><span data-stu-id="6d8ce-108">Taxonomy</span></span>

<span data-ttu-id="6d8ce-p102">Wir unterstützen eine einheitliche [Taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) für verwaltete Unternehmensdaten für alle geografischen Standorte. Die Gestaltungsvorlage wird an einem zentralen Ort für das Unternehmen gehostet. Es wird empfohlen, die globale Taxonomie von einem zentralen Ort aus zu verwalten und nur der Taxonomie der Satellitenstandorte standortspezifische Ausdrücke hinzuzufügen. Globale Taxonomieausdrücke werden mit den Satellitenstandorten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="6d8ce-112">Freigabe</span><span class="sxs-lookup"><span data-stu-id="6d8ce-112">Sharing</span></span>

<span data-ttu-id="6d8ce-p103">Administratoren können die Freigabe von Richtlinien für jeden Standort einrichten und verwalten. OneDrive-Websites an den einzelnen geografischen Standorten berücksichtigen nur die entsprechenden Freigabeeinstellungen des geografischen Standorts. (Sie können z. B. [externe Freigabe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) für Ihren zentralen Standort und nicht für den Satellitenstandort zulassen, und umgekehrt.) Beachten Sie, dass die Freigabeeinstellungen keine Konfiguration von Freigabeeinschränkungen zwischen den geografischen Standorten zulassen.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="6d8ce-p104">Für Multi-Geo in OneDrive müssen Sie Ihre Freigabeeinstellungen für jeden geografischen Standort verwalten, da diese nicht innerhalb des Mandanten synchronisiert werden. Die Einstellungen für die Freigabe können auf der Seite für die [Freigabeeinstellungen im OneDrive Admin Center](https://admin.onedrive.com/?v=SharingSettings) verwalten. Externe Freigabe ist standardmäßig für alle Benutzer an den einzelnen Satellitenstandorten aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="6d8ce-119">Benutzerprofilanwendung</span><span class="sxs-lookup"><span data-stu-id="6d8ce-119">User Profile Application</span></span>

<span data-ttu-id="6d8ce-p105">Es gibt eine [Benutzerprofilanwendung](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) an jedem geografischen Standort. Profilinformationen der Benutzer werden an dem jeweiligen geografischen Standort gehostet und stehen dem Administrator für diesen geografischen Standort zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="6d8ce-p106">Wenn Sie über benutzerdefinierte Profileigenschaften verfügen, wird empfohlen, dasselbe Profilschema für alle geografischen Standorte zu verwenden und die benutzerdefinierten Profileigenschaften entweder für alle oder bestimmte geografischen Standorte aufzufüllen. Eine Anleitung dazu, wie Sie Benutzerprofildaten programmgesteuert auffüllen, finden Sie unter [API für die Massenaktualisierung von Benutzerprofilen](https://docs.microsoft.com/de-DE/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/de-DE/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="6d8ce-124">BCS, Secure Store, Apps</span><span class="sxs-lookup"><span data-stu-id="6d8ce-124">BCS: Secure Store Service</span></span>

<span data-ttu-id="6d8ce-125">BCS, Secure Store und Apps verfügen über separate geografische Instanzen. Daher sollte der SharePoint Online-Administrator diese Dienste von dem jeweiligen geografischen Standort aus verwalten und konfigurieren, an dem diese vorhanden sein sollen.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="6d8ce-126">Security & Compliance Center</span><span class="sxs-lookup"><span data-stu-id="6d8ce-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="6d8ce-127">Es gibt ein zentrales Compliance Center für den Multi-Geo-Mandanten: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="6d8ce-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="6d8ce-128">DLP-Richtlinie in Information Protection</span><span class="sxs-lookup"><span data-stu-id="6d8ce-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="6d8ce-p107">Sie können Ihre DLP-Richtlinien in Information Protection für OneDrive for Business im Security & Compliance Center festlegen und den Geltungsbereich je nach Bedarf auf den gesamten Mandanten oder einzelne Benutzer festlegen. Beispiel: Wenn Sie eine Richtlinie für einen OneDrive-Benutzer an einem Satellitenstandort auswählen möchten, wenden Sie die Richtlinie für eine bestimmte OneDrive-Umgebung an, und geben Sie die URL der OneDrive-Benutzerumgebung ein. Eine allgemeine Anleitung für das Erstellen von DLP-Richtlinien finden Sie unter [Übersicht über die Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="6d8ce-132">Die DLP-Richtlinien werden automatisch basierend auf ihrer Anwendbarkeit auf den jeweiligen geografischen Standort synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="6d8ce-133">Die Implementierung von IP- (Information Protection) und DLP-Richtlinien für alle Benutzer an einem geografischen Standort steht nicht als Option auf der Benutzeroberfläche zur Verfügung. Sie müssen stattdessen die entsprechenden OneDrive-Konten für die Richtlinie auswählen oder die Richtlinie global auf alle OneDrive-Konten anwenden.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="6d8ce-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="6d8ce-134">eDiscovery</span></span> 

<span data-ttu-id="6d8ce-p108">Standardmäßig kann ein eDiscovery-Manager oder Administrator eines Multi-Geo-Mandaten eDiscovery nur an der zentralen Stelle dieses Mandanten durchführen. Um eDiscovery für Satellitenstandorte durchführen zu können, steht ein neuer Parameter des Compliancesicherheitsfilters namens „Region“ über PowerShell zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="6d8ce-137">Der globale Office 365-Administrator muss eDiscovery-Managerberechtigungen zuweisen, damit andere Personen eDiscovery durchführen können, und einen „Region“-Parameter im entsprechenden Compliancesicherheitsfilter zuweisen, um die Region zum Durchführen von eDiscovery als Satellitenstandort festzulegen. Andernfalls wird eDiscovery nicht für den Satellitenstandort durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="6d8ce-p109">Wenn die eDiscovery-Manager- oder Administratorrolle für einen bestimmten geografischen Standort festgelegt ist, kann der eDiscovery-Manager oder Administrator nur eDiscovery-Suchaktionen für die SharePoint-Websites und OneDrive-Websites an diesem geografischen Standort durchführen. Wenn ein eDiscovery-Manager oder Administrator versucht, SharePoint- oder OneDrive-Websites außerhalb der angegebenen Region zu durchsuchen, werden keine Ergebnisse zurückgegeben. Wenn der eDiscovery-Manager oder Administrator für eine Region einen Export auslöst, werden Daten in der Azure-Instanz dieses Bereichs exportiert. So können Organisationen Compliance gewährleisten, indem nicht zugelassen wird, dass Inhalte über den kontrollierten Rahmen hinaus exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="6d8ce-142">Wenn ein eDiscovery-Manager mehrere SharePoint-Regionen durchsuchen möchte, muss ein anderes Benutzerkonto für den eDiscovery-Manager erstellt werden, das die alternative Region angibt, in der sich OneDrive- oder SharePoint-Websites befinden.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6d8ce-143"><strong>Von Multi-Geo unterstützte geografischen Standorte</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="6d8ce-144"><strong>eDiscovery für exportierte SharePoint-Daten erfolgt an diesem Azure Blob-Datenspeicherort...</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="6d8ce-145"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-145"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-146">Rechenzentren in den USA</span><span class="sxs-lookup"><span data-stu-id="6d8ce-146">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d8ce-147"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-147"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-148">Rechenzentren in Europa</span><span class="sxs-lookup"><span data-stu-id="6d8ce-148">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6d8ce-149"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-149"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-150">Rechenzentren in Südost- oder Ostasien</span><span class="sxs-lookup"><span data-stu-id="6d8ce-150">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d8ce-151"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-151"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-152">Rechenzentren in den USA</span><span class="sxs-lookup"><span data-stu-id="6d8ce-152">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6d8ce-153"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-153"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-154">Rechenzentren in Südost- oder Ostasien</span><span class="sxs-lookup"><span data-stu-id="6d8ce-154">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d8ce-155"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-155"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-156">Standardspeicherort für Daten des Mandanten</span><span class="sxs-lookup"><span data-stu-id="6d8ce-156">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6d8ce-157"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-157"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-158">Rechenzentren in Europa</span><span class="sxs-lookup"><span data-stu-id="6d8ce-158">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d8ce-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="6d8ce-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="6d8ce-160">Rechenzentren in Südost- oder Ostasien</span><span class="sxs-lookup"><span data-stu-id="6d8ce-160">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="6d8ce-161">So legen Sie den Compliancesicherheitsfilter für eine Region fest</span><span class="sxs-lookup"><span data-stu-id="6d8ce-161">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="6d8ce-162">Öffnen Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-162">Open Windows PowerShell.</span></span>

2.  <span data-ttu-id="6d8ce-163">Geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="6d8ce-163">Enter</span></span>  
    <span data-ttu-id="6d8ce-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="6d8ce-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="6d8ce-165">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="6d8ce-165">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="6d8ce-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="6d8ce-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="6d8ce-167">Beispiel: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="6d8ce-167">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="6d8ce-168">Informationen zu weiteren Parametern und zur Syntax finden Sie im Artikel [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx).</span><span class="sxs-lookup"><span data-stu-id="6d8ce-168">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="6d8ce-169">Überwachungsprotokollsuche</span><span class="sxs-lookup"><span data-stu-id="6d8ce-169">Audit log search</span></span>

<span data-ttu-id="6d8ce-p110">Ein einheitliches [Überwachungsprotokoll](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) für alle Ihre geografischen Standorte ist auf der Seite für die Office 365-Überwachungsprotokollsuche verfügbar. Sie können alle Überwachungsprotokolleinträge für alle geografischen Standorte anzeigen. Beispiel: Sie können Benutzeraktivitäten für die geografischen Standorte NAM und EUR in einer Organisationsansicht anzeigen und dann vorhandene Filter anwenden, um bestimmte Benutzeraktivitäten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6d8ce-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
