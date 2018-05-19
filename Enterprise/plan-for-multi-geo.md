---
title: Planen von Multi-Geo in OneDrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Informationen zu Multi-Geo in OneDrive for Business, zur Funktionsweise von Multi-Geo und zu für Datenspeicher verfügbaren geografischen Standorten.
ms.openlocfilehash: 54efc6092338e505ef44344f9c3d3a7efe9ae498
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="5a90a-103">Planen von Multi-Geo in OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="5a90a-103">Plan for OneDrive for Business</span></span>

<span data-ttu-id="5a90a-104">Dieser Leitfaden wurde für Administratoren von multinationalen Unternehmen (MNCs) entwickelt, die den SharePoint Online-Mandanten für die Erweiterung auf weitere geografische Standorte entsprechend den Unternehmensanforderungen in Bezug auf die Datenaufbewahrung vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="5a90a-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="5a90a-p101">In einer Multi-Geo-Konfiguration von OneDrive besteht der Office 365-Mandant aus einem zentralen Standort (auch Standardstandort genannt) und einem oder mehreren Satellitenstandorten. Dies ist ein einzelner Mandanten, der mehrere geografische Standorte umfasst. In Multi-Geo in OneDrive werden Ihre Mandanteninformationen, darunter die geografischen Standorte, in Azure Active Directory (AAD) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="5a90a-108">Im Folgenden werden einige wichtige Begriffe in Bezug auf Multi-Geo erläutert, die beim Verständnis der grundlegenden Konzepte der Konfiguration hilfreich sind:</span><span class="sxs-lookup"><span data-stu-id="5a90a-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="5a90a-109">**Mandant** – Darstellung einer Organisation in der Office 365-Cloud, mit der in der Regel eine oder mehrere Domänen verknüpft sind (zum Beispiel http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="5a90a-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="5a90a-p102">**Geografische Standorte** – Die geografischen Standorte, an denen die Daten Ihres Mandanten gehostet werden. Multi-Geo-Mandanten umfassen mehr als einen geografischen Standort, zum Beispiel Nordamerika und Europa.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="5a90a-112">**Zugelassene Datenspeicherorte (Allowed Data Locations, ADL)** – Die geografischen Standorte, für die Ihr Mandant zum Hosten von OneDrive- und SharePoint-Daten konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="5a90a-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="5a90a-p103">**Bevorzugter Datenspeicherort (Preferred Data Location, PDL)** – Der geografische Standort, an dem OneDrive-Daten eines einzelnen Benutzers gespeichert sind. Dieser kann vom Administrator auf jeden zugelassenen Datenspeicherort festgelegt werden, der für den Mandanten konfiguriert wurde. Wenn Sie den bevorzugten Datenspeicherort für einen Benutzer ändern, der bereits über eine OneDrive-Website verfügt, werden seine OneDrive-Daten nicht automatisch an den neuen geografischen Standort verschoben. Weitere Informationen finden Sie unter [Verschieben einer OneDrive-Bibliothek an einen anderen geografischen Standort](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="5a90a-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="5a90a-117">Für die Aktivierung von Multi-Geo müssen Sie die folgenden Schritte durchführen:</span><span class="sxs-lookup"><span data-stu-id="5a90a-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="5a90a-118">Arbeiten Sie mit Ihrem Kontoteam, um den Serviceplan für _Multi-Geo-Funktionen in Office 365_ hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5a90a-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="5a90a-119">Wählen Sie die gewünschten Satellitenstandorte, und fügen Sie sie Ihrem Mandanten hinzu.</span><span class="sxs-lookup"><span data-stu-id="5a90a-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="5a90a-p104">Legen Sie den bevorzugten Datenspeicherort und den gewünschten Satellitenstandort für Ihre Benutzer fest. Wenn eine neue OneDrive-Website für einen Benutzer bereitgestellt wird, wird sie an dem bevorzugten Datenspeicherort bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="5a90a-122">Migrieren Sie bei Bedarf vorhandene OneDrive-Websites der Benutzer von dem Standardort zu dem bevorzugten Datenspeicherort.</span><span class="sxs-lookup"><span data-stu-id="5a90a-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="5a90a-123">Weitere Informationen zu den einzelnen Schritten finden Sie unter [Konfigurieren von Multi-Geo in OneDrive for Business](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5a90a-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a90a-p105">Beachten Sie, dass Multi-Geo-Funktionen von Office 365 nicht auf Leistungsoptimierung ausgelegt sind, sie dienen lediglich dazu, die jeweiligen Datenaufbewahrungsanforderungen zu erfüllen. Informationen zur Leistungsoptimierung für Office 365 finden Sie unter [Netzwerkplanung und Leistungsoptimierung für Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848), oder wenden Sie sich hierzu an Ihre Supportgruppe.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="5a90a-p106">Sie können einen der folgenden Standorte als Satellitenstandorte festlegen, an denen OneDrive-Dateien gehostet werden können. Erstellen Sie bei der Planung von Multi-Geo eine Liste der Orte, die Sie Ihrem Office 365-Mandanten hinzufügen möchten. Es wird empfohlen, mit einem oder zwei Satellitenstandorten zu beginnen und dann bei Bedarf schrittweise weitere geografische Standorte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5a90a-129"><strong>Standort</strong></span><span class="sxs-lookup"><span data-stu-id="5a90a-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="5a90a-130"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="5a90a-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5a90a-131">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="5a90a-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="5a90a-132">APC</span><span class="sxs-lookup"><span data-stu-id="5a90a-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5a90a-133">Europa/Naher Osten/Afrika</span><span class="sxs-lookup"><span data-stu-id="5a90a-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="5a90a-134">EUR</span><span class="sxs-lookup"><span data-stu-id="5a90a-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5a90a-135">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="5a90a-135">North America</span></span></td>
<td align="left"><span data-ttu-id="5a90a-136">NAM</span><span class="sxs-lookup"><span data-stu-id="5a90a-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5a90a-137">Australien</span><span class="sxs-lookup"><span data-stu-id="5a90a-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="5a90a-138">AUS</span><span class="sxs-lookup"><span data-stu-id="5a90a-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5a90a-139">Kanada</span><span class="sxs-lookup"><span data-stu-id="5a90a-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="5a90a-140">CAN</span><span class="sxs-lookup"><span data-stu-id="5a90a-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5a90a-141">Japan</span><span class="sxs-lookup"><span data-stu-id="5a90a-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="5a90a-142">JPN</span><span class="sxs-lookup"><span data-stu-id="5a90a-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5a90a-143">Korea</span><span class="sxs-lookup"><span data-stu-id="5a90a-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="5a90a-144">KOR</span><span class="sxs-lookup"><span data-stu-id="5a90a-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5a90a-145">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="5a90a-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="5a90a-146">GBR</span><span class="sxs-lookup"><span data-stu-id="5a90a-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="5a90a-147">Zukünftige geografische Speicherorte:</span><span class="sxs-lookup"><span data-stu-id="5a90a-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="5a90a-148">Frankreich</span><span class="sxs-lookup"><span data-stu-id="5a90a-148">France</span></span>
- <span data-ttu-id="5a90a-149">Indien</span><span class="sxs-lookup"><span data-stu-id="5a90a-149">India</span></span>

<span data-ttu-id="5a90a-p107">Beim Konfigurieren von Multi-Geo sollten Sie auch eine Konsolidierung der lokalen Infrastruktur während der Migration zu Office 365 berücksichtigen. Wenn Sie zum Beispiel über lokale Farmen in Singapur und Malaysia verfügen, können Sie sie an dem Satellitenstandort APC zusammenführen, wenn dies entsprechend den Datenaufbewahrungsanforderungen möglich ist.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="5a90a-152">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="5a90a-152">Best practices</span></span>

<span data-ttu-id="5a90a-p108">Es wird empfohlen, einen Testbenutzer in Office 365 zu anfänglichen Testzwecken zu erstellen. Es werden einige Test- und Überprüfungsschritte für diesen Benutzer durchgeführt, bevor mit der Multi-Geo-Funktion in OneDrive für Produktionsbenutzer fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="5a90a-p109">Nach Abschluss der Tests mit dem Testbenutzer, wählen Sie eine Pilotgruppe, vielleicht von Ihrer IT-Abteilung, die zunächst OneDrive an dem neuen geografischen Standort verwenden soll. Wählen Sie für diese erste Gruppe Benutzer, die noch nicht über OneDrive verfügen. Es wird empfohlen, nicht mehr als fünf Personen zu dieser ersten Gruppe hinzuzufügen und sie schrittweise zu erweitern und schließlich einen Rollout im Batch durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="5a90a-p110">Für jeden Benutzer muss ein *bevorzugter Datenspeicherort* festgelegt werden, damit Office 365 den geografischen Standort für die Bereitstellung von OneDrive ermitteln kann. Der bevorzugte Datenspeicherort des Benutzers muss mit einem der ausgewählten Satellitenstandorte oder dem zentralen Standort übereinstimmen. Obwohl das Feld für den bevorzugten Datenspeicherort kein Pflichtfeld ist, wird empfohlen, einen bevorzugten Datenspeicherort für alle Benutzer festzulegen. Workloads eines Benutzers ohne bevorzugten Datenspeicherort werden basierend auf der Multi-Geo-Logik an dem zentralen Standort bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="5a90a-p111">Erstellen Sie eine Liste Ihrer Benutzer mit den entsprechenden Benutzerprinzipalnamen und den Codes für die entsprechenden bevorzugten Datenspeicherorte. Fügen Sie Ihren Testbenutzer und die erste Pilotgruppe hinzu. Sie benötigen diese Liste für die Konfigurationsverfahren.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="5a90a-p112">Wenn für Ihre Benutzer eine Synchronisierung zwischen dem lokalen Active Directory (AD)-System und Azure Active Directory (AAD) erfolgt, müssen Sie den bevorzugten Datenspeicherort für die synchronisierten Benutzer mithilfe von Azure Active Directory Connect festlegen. Sie können den bevorzugten Datenspeicherort für synchronisierte Benutzer nicht direkt mithilfe von Azure AD PowerShell konfigurieren. Die Schritte zum Einrichten der bevorzugten Datenspeicherorte in AD und zum Synchronisieren dieser Liste finden Sie unter [Azure Active Directory Connect-Synchronisierung: Konfigurieren des bevorzugten Datenspeicherorts für Office 365-Ressourcen](https://docs.microsoft.com/de-DE/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="5a90a-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/de-DE/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="5a90a-p113">Die Verwaltung eines Multi-Geo-Mandanten kann von der eines Nicht-Multi-Geo-Mandanten abweichen, da viele SharePoint- und OneDrive-Einstellungen und -Dienste über Multi-Geo-Funktionen verfügen. Es wird empfohlen, den Artikel [Verwalten einer Multi-Geo-Umgebung](administering-a-multi-geo-environment.md) zu lesen, bevor Sie mit der Konfiguration fortfahren.</span><span class="sxs-lookup"><span data-stu-id="5a90a-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="5a90a-170">Informationen zur Endbenutzererfahrung in einer Multi-Geo-Umgebung finden Sie unter [Benutzererfahrung in einer Multi-Geo-Umgebung](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="5a90a-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="5a90a-171">Informationen zu den ersten Schritten beim Konfigurieren von Multi-Geo in OneDrive for Business finden Sie unter [Konfigurieren von Multi-Geo in OneDrive for Business](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5a90a-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="5a90a-172">Denken Sie nach Abschluss der Konfiguration daran, [die OneDrive-Bibliotheken Ihrer Benutzer](move-onedrive-between-geo-locations.md) bei Bedarf zu migrieren, damit Benutzer an ihren bevorzugten Datenspeicherorten arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="5a90a-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
