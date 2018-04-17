---
title: Planen von OneDrive for Business Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Informationen Sie zu OneDrive für Business Multi-Geo, Multi-Geo Funktionsweise und welche Geo-Speicherorte für die Speicherung von Daten zur Verfügung stehen.
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="93bc6-103">Planen von OneDrive for Business Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="93bc6-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="93bc6-104">Diese Anleitung ist für Administratoren von multinationale Unternehmen (MNCs) entwickelt, die Vorbereiten ihrer SharePoint Online-Mandanten auf zusätzliche Regionen gemäß des Unternehmens Anwesenheit Daten vor-Ort-Anforderungen erfüllt erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="93bc6-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="93bc6-p101">In einer Konfiguration OneDrive Multi-Geo besteht aus Ihrem Office 365-Mandanten einen zentralen Speicherort (auch bekannt als dem Standardspeicherort) und einen oder mehrere Satelliten Geo-Speicherorte. Hierbei handelt es sich um einen einzelnen Mandanten, der sich über mehrere Geo-Standorte erstreckt. In OneDrive Multi-Geo ist Ihre Mandanten Informationen, einschließlich Geo-Standorten in Azure Active Directory (AAD) gesteuert.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="93bc6-108">Es folgen einige wichtige Multi-Geo Begriffe, die Ihnen das Verständnis der grundlegenden Konzepte von der Konfiguration unterstützen:</span><span class="sxs-lookup"><span data-stu-id="93bc6-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="93bc6-109">**Mandanten** – eines Unternehmens Darstellung in der Office 365-Cloud, die in der Regel eine oder mehrere Domänen mit ihm verbundenes hat (beispielsweise http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="93bc6-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="93bc6-p102">**Geo-Speicherorte** – die geografische Standorte hinweg, in Ihrem Mandanten Daten gehostet wird. Multi-Geo Mandanten Zeitspanne mehr als einem Geo-Standort, beispielsweise Nordamerika und Europa.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="93bc6-112">**Zulässige Daten Speicherorte (ADL)** – die Geo Speicherorte für den Host von OneDrive und SharePoint-Daten Ihres Mandanten konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="93bc6-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="93bc6-p103">**Bevorzugte Daten Speicherort (Verteilerliste)** – die Geo Speicherort eines einzelnen Benutzers OneDrive Daten. Dies kann vom Administrator in eines der zulässigen Datenspeicherorte festgelegt werden, die für den Mandanten konfiguriert wurden. Beachten Sie, wenn Sie der persönlichen Verteilerliste für einen Benutzer, die bereits über eine OneDrive-Website verfügt ändern, ihre OneDrive Daten nicht am neuen Speicherort Geo automatisch bewegt werden. Weitere Informationen finden Sie unter [einer OneDrive-Bibliothek mit einem anderen Geo-Speicherort zu verschieben](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="93bc6-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="93bc6-117">Multi-Geo aktivieren sind vier wichtige Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="93bc6-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="93bc6-118">Arbeiten Sie mit Ihr Kundenteam, die Dienstplan _Multi-Geo-Funktionen in Office 365_ hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="93bc6-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="93bc6-119">Wählen Sie die gewünschten Satellitenassemblys Geo Speicherorte und Ihres Mandanten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="93bc6-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="93bc6-p104">Bevorzugte Datenspeicherort Ihrer Benutzer auf den gewünschten Satelliten Geo Speicherort festgelegt. Wenn eine neue Website OneDrive für einen Benutzer bereitgestellt wird, ist es zu ihrer Verteilerliste bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="93bc6-122">Migrieren von vorhandenen OneDrive-Websites der Benutzer aus dem Hauptstandort zu ihren bevorzugten Datenspeicherort nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="93bc6-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="93bc6-123">Details für jeden dieser Schritte finden Sie unter [Konfigurieren von OneDrive für Unternehmen Multi-Geo](multi-geo-tenant-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="93bc6-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93bc6-p105">Beachten Sie, dass die Multi-Geo-Features von Office 365 sind nicht für die Optimierung Fälle Leistung ausgelegt, dafür entwickelt, Daten vor-Ort-Anforderungen erfüllen. Informationen zur leistungsoptimierung für Office 365 finden Sie unter [netzwerkplanung und leistungsoptimierung für Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) , oder wenden Sie sich an Ihrem Supportpersonal.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="93bc6-p106">Sie können konfigurieren einen der folgenden Speicherorte Satelliten Geo Speicherorte sein, auf dem Sie Dateien OneDrive hosten können. Wie Sie Multi-Geo planen möchten, stellen Sie eine Liste der Speicherorte, die Sie Ihrem Office 365-Mandanten hinzufügen möchten. Es wird empfohlen beginnend mit einem oder zwei Satellitenstandorten und schrittweise auf Weitere Geo-Speicherorte erweitert bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="93bc6-129"><strong>Speicherort</strong></span><span class="sxs-lookup"><span data-stu-id="93bc6-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="93bc6-130"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="93bc6-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="93bc6-131">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="93bc6-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="93bc6-132">APC</span><span class="sxs-lookup"><span data-stu-id="93bc6-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="93bc6-133">Europa / Mittlerer Osten / Afrika</span><span class="sxs-lookup"><span data-stu-id="93bc6-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="93bc6-134">EUR</span><span class="sxs-lookup"><span data-stu-id="93bc6-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="93bc6-135">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="93bc6-135">North America</span></span></td>
<td align="left"><span data-ttu-id="93bc6-136">NAME</span><span class="sxs-lookup"><span data-stu-id="93bc6-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="93bc6-137">Australien</span><span class="sxs-lookup"><span data-stu-id="93bc6-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="93bc6-138">AUS</span><span class="sxs-lookup"><span data-stu-id="93bc6-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="93bc6-139">Kanada</span><span class="sxs-lookup"><span data-stu-id="93bc6-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="93bc6-140">KÖNNEN</span><span class="sxs-lookup"><span data-stu-id="93bc6-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="93bc6-141">Japan</span><span class="sxs-lookup"><span data-stu-id="93bc6-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="93bc6-142">JAPANISCHE</span><span class="sxs-lookup"><span data-stu-id="93bc6-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="93bc6-143">Korea</span><span class="sxs-lookup"><span data-stu-id="93bc6-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="93bc6-144">KOREANISCHE</span><span class="sxs-lookup"><span data-stu-id="93bc6-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="93bc6-145">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="93bc6-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="93bc6-146">GBR</span><span class="sxs-lookup"><span data-stu-id="93bc6-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="93bc6-147">Zukünftige geografische Speicherorte:</span><span class="sxs-lookup"><span data-stu-id="93bc6-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="93bc6-148">Frankreich</span><span class="sxs-lookup"><span data-stu-id="93bc6-148">France</span></span>
- <span data-ttu-id="93bc6-149">Indien</span><span class="sxs-lookup"><span data-stu-id="93bc6-149">India</span></span>

<span data-ttu-id="93bc6-p107">Wenn Sie mehrere Geo konfigurieren, nehmen Sie die Möglichkeit, Ihre lokale Infrastruktur konsolidieren während der Migration zu Office 365. Beispielsweise wenn Sie lokale-Farmen in Singapur und Malaysia verfügen, können klicken Sie dann Sie diese an die APC Satelliten Position konsolidieren bereitgestellten Daten vor-Ort-Anforderungen Sie dies tun, können.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="93bc6-152">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="93bc6-152">Best practices</span></span>

<span data-ttu-id="93bc6-p108">Es wird empfohlen, dass die Erstellung eines Testbenutzers in Office 365 ersten Tests durchführen. Wir werde durchgehen einige Schritte Tests und Überprüfungen mit diesen Benutzer bevor Sie mit integrierten produktionsbenutzern in das Feature OneDrive Multi-Geo fortfahren.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="93bc6-p109">Wenn Sie mit dem Testbenutzer Tests abgeschlossen haben, wählen Sie eine Pilotgruppe – vielleicht aus Ihre IT-Abteilung – zuerst OneDrive in einen neuen Geo-Speicherort verwendet werden. Wählen Sie für diese Gruppe ersten Benutzer, die noch nicht über eine OneDrive verfügen. Es wird empfohlen nicht mehr als fünf Personen in dieser ersten Gruppe und schrittweise erweitern einen Ansatz im Batchmodus Einführung folgen.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="93bc6-p110">Jeder Benutzer muss eine *bevorzugte Datenspeicherort* (Verteilerliste) so festgelegt, dass Office 365, welche Geo-Speicherort zum Bereitstellen ihrer OneDrive ermitteln können verfügen. Bevorzugte Datenspeicherort des Benutzers muss eine der gewählten Satellitenstandorten oder den zentralen Standort übereinstimmen. Während das Verteilerliste Feld nicht obligatorisch ist, wird empfohlen, eine Verteilerliste für alle Benutzer festgelegt werden. Arbeitslasten eines Benutzers ohne eine Verteilerliste werden am zentralen Standort auf der Grundlage der Logik Multi-Geo bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="93bc6-p111">Erstellen Sie eine Liste der Benutzer, und umfassen Sie ihren Benutzerprinzipalnamen (UPN) und den Speicherort Code für den Speicherort der entsprechenden bevorzugten Daten. Test-Benutzer und der anfänglichen Pilotgruppe zu enthalten. Für die Konfigurationsverfahren benötigen Sie dieser Liste.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="93bc6-p112">Wenn Ihre Benutzer von einem lokalen Active Directory (AD) System Azure Active Directory (AAD) synchronisiert sind, müssen Sie den Speicherort der bevorzugten Daten synchronisierten Benutzer mithilfe von Azure Active Directory verbinden festlegen. Speicherort der bevorzugten Daten von Azure AD-PowerShell synchronisierten Benutzer können nicht direkt konfiguriert werden. Die Schritte zum Einrichten der Verteilerliste in Active Directory und synchronisieren fallen [Azure Active Directory verbinden Sync: Konfigurieren des bevorzugten Datenspeicherort für Office 365-Ressourcen](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="93bc6-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="93bc6-p113">Die Verwaltung von einem Mandanten Multi-Geo kann unterscheiden sich von einem Multi-Geo-Mandanten, so viele der Einstellungen für SharePoint und OneDrive und Dienste sind Multi-Geo berücksichtigen. Es wird empfohlen, dass Sie [Verwalten einer Umgebung mit mehreren geografisch](administering-a-multi-geo-environment.md) , ehe Sie mit der Konfiguration fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="93bc6-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="93bc6-170">Lesen Sie ausführliche Informationen über Ihre Endbenutzer Erfahrung in einer Umgebung mit mehreren geografisch [Benutzerinteraktion in einer Multgeo Umgebung](multi-geo-user-experience.md) .</span><span class="sxs-lookup"><span data-stu-id="93bc6-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="93bc6-171">Um die ersten Schritte beim Konfigurieren von OneDrive für Unternehmen Multi-Geo, finden Sie unter [Konfigurieren von OneDrive für Unternehmen Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="93bc6-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="93bc6-172">Wenn Sie die Konfiguration abgeschlossen haben, denken Sie daran, [Migrieren Ihrer Benutzer OneDrive Bibliotheken](move-onedrive-between-geo-locations.md) Bedarf Ihrer Benutzer arbeiten von zu ihren bevorzugten Datenspeicherorte erhalten.</span><span class="sxs-lookup"><span data-stu-id="93bc6-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
