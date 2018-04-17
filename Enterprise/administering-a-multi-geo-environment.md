---
title: Verwalten einer Umgebung mit mehreren geografisch
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zum Verwalten von SharePoint und OneDrive-Dienste in einer Umgebung mit mehreren geografisch.
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="5e45a-103">Verwalten einer Umgebung mit mehreren geografisch</span><span class="sxs-lookup"><span data-stu-id="5e45a-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="5e45a-104">Es folgt eine Aufstellung der Funktionsweise von OneDrive und SharePoint-Dienste in einer Umgebung mit mehreren geografisch.</span><span class="sxs-lookup"><span data-stu-id="5e45a-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="5e45a-105">OneDrive Administratorbenutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="5e45a-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="5e45a-p101">Der [OneDrive-Verwaltungskonsole](https://admin.onedrive.com) hat eine Registerkarte **Geo Speicherorte** im linken Navigationsbereich, welche Features, in dem Sie anzeigen und Verwalten von Speicherorten für Ihre Geo können ein Geo-Standorte zuordnen. Verwenden Sie diese Seite zum Hinzufügen oder Löschen von Geo Speicherorte für Ihre Mandanten.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="5e45a-108">Taxonomie</span><span class="sxs-lookup"><span data-stu-id="5e45a-108">Taxonomy</span></span>

<span data-ttu-id="5e45a-p102">Wir unterstützen eine einheitliche [Taxonomie](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) für verwaltete Metadaten von Unternehmen über Geo-Standorte mit das Master-Shape in der zentralen Speicherort für Ihr Unternehmen gehostet wird. Es wird empfohlen, dass Sie der globalen Taxonomie vom zentralen Speicherort verwalten und nur Satelliten Geo Speicherort Taxonomie standortspezifische Begriffe hinzugefügt. Globale Taxonomie Begriffe werden an den Satelliten Geo Orten synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="5e45a-112">Freigabe</span><span class="sxs-lookup"><span data-stu-id="5e45a-112">Sharing</span></span>

<span data-ttu-id="5e45a-p103">Administratoren können festlegen und Verwalten von Freigaberichtlinien für jede ihrer Standorte. Die Websites OneDrive an jedem Standort Geo berücksichtigt nur die entsprechenden Geo bestimmte sharing Einstellungen. Beispielsweise können Sie [externe Freigabe](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) für den zentralen Standort, jedoch nicht für Ihre Satelliten Speicherort umgekehrt gestatten. OneDrive Multi-Geo müssen Sie Ihre Freigabe Einstellungen an jedem Standort Geo verwalten, wie diese über den Mandanten nicht synchronisiert sind.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="5e45a-p104">Verwalten von sharing Besuch der Seite [freigabeeinstellungen OneDrive-Verwaltungskonsole](https://admin.onedrive.com/?v=SharingSettings) . Externe Freigabe wird mit jeder an jedem Satellitenstandort standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="5e45a-119">Benutzer Benutzerprofildienst-Anwendung</span><span class="sxs-lookup"><span data-stu-id="5e45a-119">User Profile Application</span></span>

<span data-ttu-id="5e45a-p105">An jedem Standort Geo ist ein [Benutzer Benutzerprofildienst-Anwendung](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) . Profilinformationen des Benutzers gehostet wird in ihrem Standort Geo und an den Administrator für diesen Speicherort Geo verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="5e45a-122">Wenn Sie benutzerdefinierte Eigenschaften, und es wird empfohlen, die Sie verwenden das gleiche Profilschema verschiedenen Standorten und füllen Sie Ihre benutzerdefinierte Profileigenschaften entweder an allen Speicherorten von Geo oder bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="5e45a-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="5e45a-123">BCS, Secure Store-Apps</span><span class="sxs-lookup"><span data-stu-id="5e45a-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="5e45a-124">BCS, einmaliges Anmelden und Apps verfügen über separate Geo-Instanzen, daher der SharePoint Online-Administrator verwalten und konfigurieren Sie diese Dienste von jeder Geo-Instanz, in dem sie vorhanden sein sollen, sollten.</span><span class="sxs-lookup"><span data-stu-id="5e45a-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="5e45a-125">Sicherheit und Compliance-Verwaltungskonsole</span><span class="sxs-lookup"><span data-stu-id="5e45a-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="5e45a-126">Es ist eine zentrale Compliance Center für den Mandanten mit mehreren geografisch: [Office 365-Sicherheit und Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="5e45a-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="5e45a-127">Schutz (IP) Data Loss Prevention (DLP) Informationsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5e45a-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="5e45a-p106">Sie können Ihre IP DLP Richtlinien für OneDrive for Business in der Mitte Sicherheit und Richtlinientreue festlegen Bereichsdefinierung Richtlinien Bedarf für den gesamten Mandanten oder für Benutzer. Beispiel: Wenn Sie eine Richtlinie für einen Benutzer OneDrive an einem Speicherort Satelliten auswählen möchten, wenden Sie die Richtlinie zu einem bestimmten OneDrive und geben den Benutzer auswählen der OneDrive-Url. Allgemeine Richtlinien bei der Erstellung von DLP-Richtlinien finden Sie unter [Übersicht über Richtlinien zur Verhinderung von Datenverlust](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .</span><span class="sxs-lookup"><span data-stu-id="5e45a-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="5e45a-131">Die DLP-Richtlinien werden automatisch basierend auf ihren Anwendungsbereich an jedem Standort Geo synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="5e45a-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="5e45a-132">Implementieren von Information Protection and Data Loss Prevention-Richtlinien für alle Benutzer an einem Speicherort Geo ist keine Option in der Benutzeroberfläche verfügbar, stattdessen müssen Sie wählen Sie die entsprechenden OneDrive-Konten für die Richtlinie oder gelten die Richtlinie global für alle OneDrive-Konten.</span><span class="sxs-lookup"><span data-stu-id="5e45a-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="5e45a-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="5e45a-133">eDiscovery</span></span> 

<span data-ttu-id="5e45a-p107">Standardmäßig wird eine eDiscovery-Manager oder Administrator der einen Mandanten Multi-Geo eDiscovery nur in der zentralen Speicherort, Mandanten durchführen können. Um die Möglichkeit zum Durchführen von eDiscovery für Satelliten Speicherorte zu unterstützen, ist ein neuer Sicherheitsfilter Compliance-Parameter "Region" aufgerufen über PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="5e45a-136">Office 365 globale Administrator muss eDiscovery-Manager-Berechtigungen zu anderen Benutzern gestatten, Ausführen von eDiscovery, und weisen Sie einen Parameter "Region" in ihren entsprechenden Compliance Sicherheitsfilter an die Region für die Durchführung von eDiscovery als Satelliten zuweisen Speicherort, andernfalls keine eDiscovery für den Speicherort der Satelliten durchgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5e45a-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="5e45a-p108">Wenn die eDiscovery-Manager oder Administrator-Rolle für einen bestimmten Geo-Speicherort festgelegt ist, wird die eDiscovery-Manager oder Administrator nur eDiscovery-Suche Aktionen für die SharePoint-Websites und OneDrive Standorte in diesen Geo-Speicherort ausführen können. Wenn ein eDiscovery-Manager oder Administrator versucht, SharePoint oder OneDrive Websites außerhalb des angegebenen Bereichs suchen, werden keine Ergebnisse zurückgegeben. Wenn nach Exportieren von eDiscovery-Manager oder Administrator für einen Bereich ausgelöst wird, werden Daten an die Azure Instanz dieser Region exportiert. Dadurch Organisationen in Compliance bleiben, indem nicht zulassen Inhalte über gesteuerte Grenzen hinweg exportiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="5e45a-141">Wenn es für ein eDiscovery-Suche über mehrere SharePoint-Regionen Manager erforderlich ist, müssen eines anderen Benutzerkontos für die eDiscovery-Manager erstellt werden, der die alternative Region angibt, wo sich die OneDrive oder SharePoint-Websites befinden.</span><span class="sxs-lookup"><span data-stu-id="5e45a-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5e45a-142"><strong>Multi-Geo unterstützt Geo Speicherorte</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="5e45a-143"><strong>eDiscovery für SharePoint exportiert Daten werden in diesem Speicherort der Azure Blob-Daten...</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5e45a-144"><strong>NAME</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-145">US-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e45a-146"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-147">Europa Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e45a-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-149">Südost oder East Asien-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e45a-150"><strong>KÖNNEN</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-151">US-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e45a-152"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-153">Südost oder East Asien-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e45a-154"><strong>KOREANISCHE</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-155">Mandanten Standardspeicherort Daten</span><span class="sxs-lookup"><span data-stu-id="5e45a-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e45a-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-157">Europa Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e45a-158"><strong>JAPANISCHE</strong></span><span class="sxs-lookup"><span data-stu-id="5e45a-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="5e45a-159">Südost oder East Asien-Rechenzentren</span><span class="sxs-lookup"><span data-stu-id="5e45a-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="5e45a-160">Die Einhaltung von Bestimmungen Sicherheitsfilter für einen Bereich festlegen:</span><span class="sxs-lookup"><span data-stu-id="5e45a-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="5e45a-161">Öffnen von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e45a-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="5e45a-162">die EINGABETASTE</span><span class="sxs-lookup"><span data-stu-id="5e45a-162">Enter</span></span>  
    <span data-ttu-id="5e45a-163">$s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Anmeldeinformationen $cred-Authentifizierung grundlegende - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="5e45a-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="5e45a-164">$eine = $s Import-PSSession - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="5e45a-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="5e45a-165">**Neue ComplianceSecurityFilter** **-Aktion** ALLE **FilterName -** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Benutzer** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="5e45a-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="5e45a-166">Beispiel: **neue ComplianceSecurityFilter-Aktion** alle **FilterName -** NAMEDISCOVERYMANAGERS **-Region** Name **-Benutzer** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5e45a-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="5e45a-167">Finden Sie im Artikel [Neu ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) für zusätzliche Parameter und syntax</span><span class="sxs-lookup"><span data-stu-id="5e45a-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="5e45a-168">Überwachungsprotokollsuche</span><span class="sxs-lookup"><span data-stu-id="5e45a-168">Audit log search</span></span>

<span data-ttu-id="5e45a-p109">Eine einheitliche [Überwachungsprotokoll](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) für alle Standorte Ihrer Geo ist über die Office 365 Audit Log Suchseite verfügbar. Sehen Sie alle Überwachungsprotokolleinträge aus über Geos, beispielsweise Name & EUR Geo Benutzeraktivitäten in einer einzigen Org-Ansicht angezeigt werden, und klicken Sie dann können Sie vorhandene Filter an, um bestimmte Benutzer Aktivitäten finden Sie unter anwenden.</span><span class="sxs-lookup"><span data-stu-id="5e45a-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
