---
title: Konfiguration des Mandanten für Multi-Geo in OneDrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Konfigurieren von Multi-Geo in OneDrive for Business.
ms.openlocfilehash: 5049904b1419935ed1d55eb73b74d2cd12edb3c0
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547167"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="41ec3-103">Konfiguration des Mandanten für Multi-Geo in OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="41ec3-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="41ec3-p101">Bevor Sie Ihren Mandanten für Multi-Geo in OneDrive for Business konfigurieren, stellen Sie sicher, dass Sie den Artikel [Planen von Multi-Geo in OneDrive for Business](plan-for-multi-geo.md) gelesen haben. Um die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der geografischen Standorte, die Sie als Satellitenstandorte aktivieren möchten, und der Testbenutzer, für die Sie diese Standorte bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="41ec3-106">Hinzufügen des Plans für Multi-Geo-Funktionen in Office 365 zu Ihrem Mandanten</span><span class="sxs-lookup"><span data-stu-id="41ec3-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="41ec3-p102">Wenn Sie Multi-Geo in OneDrive for Business verwenden möchten, benötigen Sie den Plan für _Multi-Geo-Funktionen in Office 365_. Arbeiten Sie mit Ihrem Kontoteam, um diesen Plan zu Ihrem Mandanten hinzuzufügen. Ihr Kontoteam stellt den Kontakt mit dem entsprechenden Lizenzierungsexperten her und unterstützt Sie bei der Konfiguration des Mandanten.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="41ec3-p103">Beachten Sie, dass der Plan für _Multi-Geo-Funktionen in Office 365_ ein Serviceplan auf Benutzerebene ist. Sie benötigen eine Lizenz für jeden Benutzer, der an einem Satellitenstandort gehostet werden soll. Sie können mit der Zeit weitere Lizenzen hinzufügen, wenn Sie Benutzer in Ihrem Satellitenstandort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="41ec3-113">Nachdem Ihr Mandant mit dem Plan für _Multi-Geo-Funktionen in Office 365_ bereitgestellt wurde, wird die Registerkarte **Geografische Standorte** im [OneDrive Admin Center](https://admin.onedrive.com) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="41ec3-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="41ec3-114">Hinzufügen von Satellitenstandorten zu Ihrem Mandanten</span><span class="sxs-lookup"><span data-stu-id="41ec3-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="41ec3-p104">Sie müssen einen Satellitenstandort für jeden geografischen Standort festlegen, für den Sie OneDrive for Business verwenden möchten. In der folgenden Tabelle werden die verfügbaren geografischen Standorte aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="41ec3-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="41ec3-117"><strong>Standort</strong></span><span class="sxs-lookup"><span data-stu-id="41ec3-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="41ec3-118"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="41ec3-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="41ec3-119">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="41ec3-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="41ec3-120">APC</span><span class="sxs-lookup"><span data-stu-id="41ec3-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="41ec3-121">Australien</span><span class="sxs-lookup"><span data-stu-id="41ec3-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="41ec3-122">AUS</span><span class="sxs-lookup"><span data-stu-id="41ec3-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="41ec3-123">Kanada</span><span class="sxs-lookup"><span data-stu-id="41ec3-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="41ec3-124">CAN</span><span class="sxs-lookup"><span data-stu-id="41ec3-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="41ec3-125">Europa/Naher Osten/Afrika</span><span class="sxs-lookup"><span data-stu-id="41ec3-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="41ec3-126">EUR</span><span class="sxs-lookup"><span data-stu-id="41ec3-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="41ec3-127">Frankreich</span><span class="sxs-lookup"><span data-stu-id="41ec3-127">France</span></span></td>
<td align="left"><span data-ttu-id="41ec3-128">FRA</span><span class="sxs-lookup"><span data-stu-id="41ec3-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="41ec3-129">Japan</span><span class="sxs-lookup"><span data-stu-id="41ec3-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="41ec3-130">JPN</span><span class="sxs-lookup"><span data-stu-id="41ec3-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="41ec3-131">Korea</span><span class="sxs-lookup"><span data-stu-id="41ec3-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="41ec3-132">KOR</span><span class="sxs-lookup"><span data-stu-id="41ec3-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="41ec3-133">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="41ec3-133">North America</span></span></td>
<td align="left"><span data-ttu-id="41ec3-134">NAM</span><span class="sxs-lookup"><span data-stu-id="41ec3-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="41ec3-135">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="41ec3-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="41ec3-136">GBR</span><span class="sxs-lookup"><span data-stu-id="41ec3-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="41ec3-137">So fügen Sie eine Satellitenstandort hinzu</span><span class="sxs-lookup"><span data-stu-id="41ec3-137">To add a satellite location</span></span>

1. <span data-ttu-id="41ec3-138">Öffnen Sie das [OneDrive Admin Center](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="41ec3-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="41ec3-139">Navigieren Sie zu der Registerkarte **Geografische Standorte**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="41ec3-140">Klicken Sie auf **Ort hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-140">Click **Add location**.</span></span>

4. <span data-ttu-id="41ec3-141">Wählen Sie den Standort aus, den Sie hinzufügen möchten, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="41ec3-142">Geben Sie die Domäne ein, die Sie mit dem geografischen Standort verwenden möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="41ec3-143">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-143">Click **Close**.</span></span>

<span data-ttu-id="41ec3-p105">Die Bereitstellung kann je nach Größe des Mandanten bis zu 72 Stunden dauern. Sobald die Bereitstellung für einen Satellitenstandort abgeschlossen ist, erhalten Sie eine E-Mail-Bestätigung. Wenn der neue geografische Standort blau auf der Karte auf der Registerkarte **Geografische Standorte** im OneDrive Admin Center angezeigt wird, können Sie mit dem Festlegen der bevorzugten Datenspeicherorte für die Benutzer für diesen geografischen Standort fortfahren.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="41ec3-p106">Ihr neuer Satellitenstandort wird mit Standardeinstellungen eingerichtet. Sie können diesen Satellitenstandort entsprechend den lokalen Complianceanforderungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="41ec3-149">Festlegen der bevorzugen Datenspeicherorte für Benutzer</span><span class="sxs-lookup"><span data-stu-id="41ec3-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="41ec3-p107">Nachdem Sie die erforderlichen Satellitenstandorte aktiviert haben, können Sie Ihre Benutzerkonten für die Verwendung des bevorzugten Datenspeicherorts aktualisieren. Es wird empfohlen, auch dann einen bevorzugten Datenspeicherort für jeden Benutzer festzulegen, wenn dieser Benutzer am zentralen Datenspeicherort verbleibt.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!TIP]
> <span data-ttu-id="41ec3-152">Es wird empfohlen, die Prüfungen mit einem Testbenutzer oder einer kleinen Gruppe von Benutzern durchzuführen, bevor die Multi-Geo-Funktionen für Ihre Organisation bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="41ec3-152">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="41ec3-p108">In AAD gibt es zwei Typen von Benutzerobjekten: Nur-Cloud-Benutzer und synchronisierte Benutzer. Befolgen Sie die entsprechenden Anweisungen für jeden Benutzertyp.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="41ec3-155">Synchronisieren der bevorzugten Datenspeicherorte für Benutzer mithilfe von AD Connect</span><span class="sxs-lookup"><span data-stu-id="41ec3-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="41ec3-p109">Wenn für Benutzer in Ihrem Unternehmen eine Synchronisierung zwischen dem lokalen Active Directory-System und Azure Active Directory durchgeführt wird, muss PreferredDataLocation in AD aufgefüllt werden und mit AAD synchronisiert werden. Befolgen Sie den Prozess unter [Azure Active Directory Connect-Synchronisierung: Konfigurieren des bevorzugten Datenspeicherorts für Office 365-Ressourcen](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation), um die Synchronisierung der bevorzugten Datenspeicherorte zwischen lokalem Active Directory und Azure Active Directory zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="41ec3-158">Es wird empfohlen, die Einstellung des bevorzugten Datenspeicherorts des Benutzers im Rahmen des Standardworkflows für das Erstellen von Benutzern hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41ec3-p110">Warten Sie bei neuen Benutzern ohne OneDrive mindestens 24 Stunden nach der Synchronisierung der bevorzugten Datenspeicherorte für Benutzer mit Azure Active Directory, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung für OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="41ec3-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="41ec3-161">Festlegen des bevorzugten Datenspeicherorts für Nur-Cloud-Benutzer</span><span class="sxs-lookup"><span data-stu-id="41ec3-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="41ec3-162">Wenn für Benutzer in Ihrem Unternehmen keine Synchronisierung zwischen dem lokalen Active Directory-System und Azure Active Directory erfolgt, was bedeutet, dass sie in Office 365 oder Azure Active Directory erstellt werden, müssen die bevorzugten Datenspeicherorte mithilfe von Azure Active Directory PowerShell festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="41ec3-162">If your company’s users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="41ec3-p111">Für die Vorgehensweisen in diesem Abschnitt ist das [Microsoft Azure Active Directory-Modul für Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) erforderlich. Wenn Azure Active Directory PowerShell bereits installiert ist, stellen Sie sicher, dass Sie ein Update auf die neueste Version durchführen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="41ec3-165">Öffnen Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41ec3-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="41ec3-166">Führen Sie `Connect-MsolService` aus, und geben Sie die Anmeldeinformationen des globalen Administrators für Ihren Mandanten ein.</span><span class="sxs-lookup"><span data-stu-id="41ec3-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="41ec3-p112">Verwenden Sie das [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser)-Cmdlet zum Festlegen des bevorzugten Datenspeicherorts für jeden Benutzer. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="41ec3-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="41ec3-p113">Sie können mithilfe des Get-MsolUser-Cmdlets prüfen, ob der bevorzugte Datenspeicherort korrekt festgelegt wurde. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="41ec3-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="41ec3-171">Es wird empfohlen, die Einstellung des bevorzugten Datenspeicherorts des Benutzers im Rahmen des Standardworkflows für das Erstellen von Benutzern hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41ec3-p114">Warten Sie bei neuen Benutzern ohne OneDrive mindestens 24 Stunden nach Festlegung der bevorzugten Datenspeicherorte für Benutzer, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive anmelden. (Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung für OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="41ec3-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="41ec3-174">Bereitstellung von OneDrive und Auswirkungen auf den bevorzugten Datenspeicherort</span><span class="sxs-lookup"><span data-stu-id="41ec3-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="41ec3-p115">Wenn der Benutzer bereits eine OneDrive-Website in dem Mandanten erstellt hat, wird beim Festlegen des bevorzugten Datenspeicherorts die vorhandene OneDrive-Bereitstellung nicht automatisch verschoben. Informationen zum Verschieben der OneDrive-Umgebung eines Benutzers finden Sie unter [Verschieben von OneDrive for Business](move-onedrive-between-geo-locations.md). Befolgen Sie die Anweisungen zum Verschieben von OneDrive zwischen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="41ec3-177">Wenn der Benutzer über keine OneDrive-Website innerhalb des Mandanten verfügt, wird OneDrive automatisch entsprechend des festgelegten Werts für den bevorzugten Datenspeicherort bereitgestellt, wobei davon ausgegangen wird, dass der bevorzugte Datenspeicherort für den Benutzer mit einem Satellitenstandort des Unternehmens übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="41ec3-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="41ec3-178">Konfigurieren der Multi-Geo-Suche</span><span class="sxs-lookup"><span data-stu-id="41ec3-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="41ec3-179">Der Multi-Geo-Mandant verfügt über aggregierte Suchfunktionen, mit denen eine Suchabfrage Ergebnisse von allen Orten innerhalb des Mandanten zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="41ec3-179">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="41ec3-180">Standardmäßig geben Suchen von diesen Einstiegspunkten aggregierte Ergebnisse zurück, auch wenn sich jeder Suchindex an dem jeweiligen relevanten geografischen Standort befindet:</span><span class="sxs-lookup"><span data-stu-id="41ec3-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="41ec3-181">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="41ec3-181">OneDrive for business</span></span>

- <span data-ttu-id="41ec3-182">Delve</span><span class="sxs-lookup"><span data-stu-id="41ec3-182">Delve</span></span>

- <span data-ttu-id="41ec3-183">SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="41ec3-183">SharePoint Home</span></span>

- <span data-ttu-id="41ec3-184">Suchcenter</span><span class="sxs-lookup"><span data-stu-id="41ec3-184">Search Center</span></span>

<span data-ttu-id="41ec3-185">Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte Suchanwendung konfiguriert werden, die die SharePoint-Suche-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="41ec3-185">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="41ec3-186">Anweisungen, einschließlich Einschränkungen und Unterschiede, finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="41ec3-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="41ec3-187">Prüfen der Konfiguration von Multi-Geo in OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="41ec3-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="41ec3-p116">Im Folgenden finden Sie einige grundlegende Anwendungsfälle, in denen eine Überprüfung vor dem Rollout von Multi-Geo in OneDrive for Business im Unternehmen möglicherweise sinnvoll ist. Nach Abschluss dieser Tests und zusätzlicher Anwendungsfälle, die für Ihr Unternehmen relevant sind, möchten Sie der ursprünglichen Pilotgruppe möglicherweise weitere Benutzer hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="41ec3-190">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="41ec3-190">**OneDrive for Business**</span></span>

<span data-ttu-id="41ec3-p117">Wählen Sie im Office 365-App-Startfeld OneDrive aus, und stellen Sie sicher, dass Sie automatisch an den entsprechenden geografischen Standort für den Benutzer, basierend auf dem bevorzugten Datenspeicherort, weitergeleitet werden. OneDrive for Business sollte jetzt an diesem Ort bereitgestellt werden. Versuchen Sie nach der Bereitstellung einige Dokumente hoch- und herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="41ec3-194">**Mobile OneDrive-App**</span><span class="sxs-lookup"><span data-stu-id="41ec3-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="41ec3-p118">Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Testkontos an. Stellen Sie sicher, dass Ihre OneDrive for Business-Dateien angezeigt werden und mit denjenigen auf Ihrem Mobilgerät interagieren können.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="41ec3-197">**OneDrive-Synchronisierungsclient**</span><span class="sxs-lookup"><span data-stu-id="41ec3-197">**OneDrive sync client**</span></span>

<span data-ttu-id="41ec3-p119">Vergewissern Sie sich, dass der OneDrive-Synchronisierungsclient den geografischen Standort für OneDrive for Business nach Anmeldung automatisch erkennt. Wenn Sie den Synchronisierungsclient herunterladen müssen, klicken Sie in der OneDrive-Bibliothek auf **Synchronisieren**.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="41ec3-200">**Office-Anwendungen**</span><span class="sxs-lookup"><span data-stu-id="41ec3-200">**Office applications**</span></span>

<span data-ttu-id="41ec3-p120">Vergewissern Sie sich, dass Sie auf OneDrive for Business zugreifen können, indem Sie sich von einer Office-Anwendung wie Word aus anmelden. Öffnen Sie die Office-Anwendung, und wählen Sie „OneDrive – <TenantName>„. Office erkennt Ihren OneDrive-Ort und zeigt die Dateien, die Sie öffnen können.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="41ec3-204">**Freigabe**</span><span class="sxs-lookup"><span data-stu-id="41ec3-204">**Sharing**</span></span>

<span data-ttu-id="41ec3-p121">Testen Sie die Freigabe von OneDrive-Dateien. Vergewissern Sie sich, dass die Personenauswahl alle SharePoint-Onlinebenutzer unabhängig vom geografischen Standort anzeigt.</span><span class="sxs-lookup"><span data-stu-id="41ec3-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
