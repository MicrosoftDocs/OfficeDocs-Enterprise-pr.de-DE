---
title: OneDrive for Business Multi-Geo Mandantenkonfiguration
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Informationen Sie zum Konfigurieren von OneDrive für Unternehmen Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="4cfc3-103">OneDrive for Business Multi-Geo Mandantenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="4cfc3-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="4cfc3-p101">Bevor Sie Ihrem Mandanten für OneDrive for Business Multi-Geo konfigurieren, sollten Sie darauf achten Sie, dass Sie [Planen von OneDrive for Business Multi-Geo](plan-for-multi-geo.md)gelesen haben. Wenn Sie die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der Speicherorte, die Sie aktivieren möchten und den Testbenutzern, die Sie für diese Standorte bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="4cfc3-106">Fügen Sie die Multi-Geo-Funktionen in Office 365-Plan Ihres Mandanten</span><span class="sxs-lookup"><span data-stu-id="4cfc3-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="4cfc3-p102">Um OneDrive for Business Multi-Geo verwenden, benötigen Sie den _Multi-Geo-Funktionen in Office 365_ -Plan. Arbeiten Sie mit Ihrem Team Konto Ihres Mandanten diesem Plan hinzugefügt. Ihr Kundenteam wird verbinden Sie mit der entsprechenden Lizenzierung Spezialist und Abrufen von Ihrem Mandanten konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="4cfc3-p103">Beachten Sie, dass der _Multi-Geo-Funktionen in Office 365_ -Plan eine auf Benutzerebene Dienstplan ist. Sie benötigen eine Lizenz für jeden Benutzer, die Sie an einem Speicherort Setellite hosten möchten. Sie können weitere Lizenzen über einen Zeitraum beim Hinzufügen von Benutzern in Satelliten Speicherorte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a setellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="4cfc3-113">Nach Ihrem Mandanten mit der _Multi-Geo-Funktionen in Office 365_ -Plan bereitgestellt wurde, wird in der [OneDrive-Verwaltungskonsole](https://admin.onedrive.com)auf der Registerkarte **Geo Speicherorte** verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="4cfc3-114">Legen Sie die zulässigen Daten Speicherorte (ADL) auf Ihres Mandanten</span><span class="sxs-lookup"><span data-stu-id="4cfc3-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="4cfc3-p104">Sie müssen Festlegen einer Datenspeicherort zulässig für SharePoint für jeden Geo-Standort, wo OneDrive für Unternehmen verwendet werden soll. Verfügbare Geo-Standorte sind in der folgenden Tabelle aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="4cfc3-117"><strong>Speicherort</strong></span><span class="sxs-lookup"><span data-stu-id="4cfc3-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="4cfc3-118"><strong>Code</strong></span><span class="sxs-lookup"><span data-stu-id="4cfc3-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="4cfc3-119">Nordamerika</span><span class="sxs-lookup"><span data-stu-id="4cfc3-119">North America</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-120">NAME</span><span class="sxs-lookup"><span data-stu-id="4cfc3-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4cfc3-121">Europa / Mittlerer Osten / Afrika</span><span class="sxs-lookup"><span data-stu-id="4cfc3-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-122">EUR</span><span class="sxs-lookup"><span data-stu-id="4cfc3-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4cfc3-123">Asien-Pazifik</span><span class="sxs-lookup"><span data-stu-id="4cfc3-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-124">APC</span><span class="sxs-lookup"><span data-stu-id="4cfc3-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4cfc3-125">Australien</span><span class="sxs-lookup"><span data-stu-id="4cfc3-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-126">AUS</span><span class="sxs-lookup"><span data-stu-id="4cfc3-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4cfc3-127">Japan</span><span class="sxs-lookup"><span data-stu-id="4cfc3-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-128">JAPANISCHE</span><span class="sxs-lookup"><span data-stu-id="4cfc3-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4cfc3-129">Kanada</span><span class="sxs-lookup"><span data-stu-id="4cfc3-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-130">KÖNNEN</span><span class="sxs-lookup"><span data-stu-id="4cfc3-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="4cfc3-131">Vereinigtes Königreich</span><span class="sxs-lookup"><span data-stu-id="4cfc3-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-132">GBR</span><span class="sxs-lookup"><span data-stu-id="4cfc3-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="4cfc3-133">Korea</span><span class="sxs-lookup"><span data-stu-id="4cfc3-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="4cfc3-134">KOREANISCHE</span><span class="sxs-lookup"><span data-stu-id="4cfc3-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="4cfc3-135">So fügen Sie einen Satelliten Geo-Speicherort hinzu</span><span class="sxs-lookup"><span data-stu-id="4cfc3-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="4cfc3-136">Öffnen Sie die [OneDrive-Verwaltungskonsole](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="4cfc3-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="4cfc3-137">Navigieren Sie zur Registerkarte **Geo-Speicherorte** .</span><span class="sxs-lookup"><span data-stu-id="4cfc3-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="4cfc3-138">Klicken Sie auf **Speicherort hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-138">Click **Add location**.</span></span>

4. <span data-ttu-id="4cfc3-139">Wählen Sie den Speicherort an, dem Sie hinzufügen möchten, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="4cfc3-140">Geben Sie die Domäne, die Sie mit dem Speicherort Geo verwenden möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="4cfc3-141">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-141">Click **Close**.</span></span>

<span data-ttu-id="4cfc3-p105">Nach der Bereitstellung von einem Speicherort Satelliten abgeschlossen wurde, erhalten Sie eine e-Mail-Bestätigung. Wenn am neuen Speicherort Geo Blau auf der Karte auf der Registerkarte **Geo Speicherorte** in der OneDrive-Verwaltungskonsole angezeigt wird, können Sie fortfahren, bevorzugte Datenspeicherort Benutzer auf diesen Geo-Speicherort festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p105">Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="4cfc3-p106">Ihre neuen Satelliten Geo Speicherort wird mit den Standardeinstellungen festgelegt. Dadurch können Sie diesen Speicherort Geo entsprechend Ihren lokalen Compliance-Anforderungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="4cfc3-146">Festlegen der bevorzugten Datenspeicherort Users</span><span class="sxs-lookup"><span data-stu-id="4cfc3-146">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="4cfc3-p107">Nachdem Sie die benötigten Datenspeicherorte aktivieren, können Sie Ihre Benutzerkonten den entsprechenden Daten Speicherort aktualisieren. Es wird empfohlen, dass Sie für jeden Benutzer eine bevorzugte Datenspeicherort festlegen, selbst wenn der Benutzer im Standardspeicherort Daten Kontaktpflege ist.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="4cfc3-149">Es wird empfohlen, dass Sie Überprüfungen mit einem Testbenutzers oder eine kleine Gruppe von Benutzern beginnen, vor der Einführung der zahlreichen organisationsinterne Multi-Geo-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-149">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="4cfc3-p108">In AAD es gibt zwei Arten von Benutzerobjekten: cloud nur und synchronisierten Benutzer. Führen Sie die entsprechenden Anweisungen für den Typ des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="4cfc3-152">Synchronisieren des Benutzers bevorzugte Datenspeicherort mit Active Directory verbinden</span><span class="sxs-lookup"><span data-stu-id="4cfc3-152">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="4cfc3-p109">Benutzer Ihres Unternehmens Azure Active Directory (AAD) von einem lokalen Active Directory (AD) System synchronisiert sind, muss ihre PreferredDataLocation in AD gefüllt und mit AAD synchronisiert. Befolgen Sie das Verfahren in [Verbinden von Azure AD-Synchronisierung: Führen Sie eine Änderung der Standardkonfiguration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) so konfigurieren Sie bevorzugte Datenspeicherort die Synchronisierung von lokalen AD zu AAD.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="4cfc3-155">Es wird empfohlen, dass Sie zählen das Festlegen der bevorzugten Daten Standort des Benutzers als Teil des standard-Benutzer Workflows erstellen.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-155">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cfc3-p110">Warten Sie für neue Benutzer mit keine OneDrive bereitgestellt die mindestens 24 Stunden, nachdem ein Benutzer Verteilerliste mit AAD, damit die Änderungen weitergegeben wird, bevor der Benutzer zu OneDrive for Business anmeldet synchronisiert ist. (Festlegen der bevorzugten Daten sichergestellt Speicherort, bevor der Benutzer meldet sich bei ihrer OneDrive für Unternehmen bereitstellen, dass neue OneDrive des Benutzers in den richtigen Speicherort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="4cfc3-158">Bevorzugte Datenspeicherort festlegen für die Cloud nur Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-158">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="4cfc3-159">Wenn Ihr Unternehmen Benutzer nicht von einem lokalen Active Directory (AD) System Azure Active Directory (AAD) synchronisiert sind, muss was bedeutet, dass sie in Office 365 oder AAD, erstellt werden dann Verteilerliste festgelegt werden von AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-159">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="4cfc3-p111">In diesem Abschnitt Verfahren benötigen Sie die [Microsoft Azure Active Directory Modul für Windows PowerShell-Modul](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Wenn Sie bereits AAD PowerShell installiert haben, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="4cfc3-162">Öffnen Sie die Microsoft Azure Active Directory-Moduls für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-162">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="4cfc3-163">Führen Sie `Connect-MsolService` , und geben Sie die globalen Administratoranmeldeinformationen für Ihre Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-163">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="4cfc3-p112">Verwenden Sie das [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) -Cmdlet zum Festlegen der bevorzugten Daten für jeden Ihrer Benutzer. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="4cfc3-p113">Sie können überprüfen, um zu bestätigen, dass der Speicherort des bevorzugten Daten mit dem Cmdlet Get-MsolUser ordnungsgemäß aktualisiert wurde. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="4cfc3-168">Es wird empfohlen, dass Sie zählen das Festlegen der bevorzugten Daten Standort des Benutzers als Teil des standard-Benutzer Workflows erstellen.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-168">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cfc3-p114">Warten Sie für neue Benutzer mit keine OneDrive bereitgestellt mindestens 24 Stunden, nachdem ein Benutzer Verteilerliste, damit die Änderungen festgelegt ist weitergegeben wird, bevor der Benutzer zu SharePoint OneDrive anmeldet. (Festlegen der bevorzugten Daten sichergestellt Speicherort, bevor der Benutzer meldet sich bei ihrer OneDrive für Unternehmen bereitstellen, dass neue OneDrive des Benutzers in den richtigen Speicherort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="4cfc3-171">Bereitstellung von OneDrive und die Auswirkungen der Verteilerliste</span><span class="sxs-lookup"><span data-stu-id="4cfc3-171">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="4cfc3-p115">Wenn der Benutzer bereits eine OneDrive-Website in den Mandanten erstellt hat, wird die Verteilerliste festlegen nicht automatisch ihre vorhandenen OneDrive verschoben. Zum Verschieben eines Benutzers OneDrive finden Sie unter [OneDrive for Business Geo verschieben](move-onedrive-between-geo-locations.md) , führen Sie die Anweisungen in OneDrive Verschieben zwischen Geo-Speicherorte.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="4cfc3-174">Wenn der Benutzer keine OneDrive-Website in den Mandanten, wird OneDrive bereitgestellt werden für diese in Übereinstimmung mit deren Verteilerliste Wert ab, unter der Voraussetzung, dass der persönlichen Verteilerliste für den Benutzer eine der zulässigen Datenspeicherorte (ADLs) des Unternehmens übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-174">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="4cfc3-175">Konfigurieren der Multi-Geo-Suche</span><span class="sxs-lookup"><span data-stu-id="4cfc3-175">Configuring Multi-Geo search</span></span>

<span data-ttu-id="4cfc3-176">Ihres Mandanten Multi-Geo müssen aggregierte Suchfunktionen ermöglichen eine Suchabfrage Ergebnisse zurückgegeben werden, unabhängig vom Standort in den Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-176">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="4cfc3-177">Standardmäßig werden sucht über diese Einstiegspunkte aggregierte Ergebnisse zurückgegeben, obwohl Sie jede Suchindex in den entsprechenden Geo Speicherort befindet:</span><span class="sxs-lookup"><span data-stu-id="4cfc3-177">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="4cfc3-178">OneDrive für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="4cfc3-178">OneDrive for business</span></span>

- <span data-ttu-id="4cfc3-179">Delve</span><span class="sxs-lookup"><span data-stu-id="4cfc3-179">Delve</span></span>

- <span data-ttu-id="4cfc3-180">SharePoint – Startseite</span><span class="sxs-lookup"><span data-stu-id="4cfc3-180">SharePoint Home</span></span>

- <span data-ttu-id="4cfc3-181">Suchcenter</span><span class="sxs-lookup"><span data-stu-id="4cfc3-181">Search Center</span></span>

<span data-ttu-id="4cfc3-182">Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte suchanwendungen konfiguriert werden, die die SharePoint-Suche API verwenden.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-182">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="4cfc3-183">Überprüfen Sie [Konfigurieren der Suche für OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) Anweisungen, einschließlich aller Einschränkungen und Unterschiede.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-183">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="4cfc3-184">Überprüfen die OneDrive for Business Multi-Geo-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="4cfc3-184">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="4cfc3-p116">Im folgenden sind einige grundlegende Verwendungsszenarien, die Sie Überprüfung vor dem Allgemein Rollout OneDrive for Business Multi-Geo Ihres Unternehmens aufnehmen möchten. Nachdem Sie diese Tests und alle zusätzlichen Anwendungsfälle, die für Ihr Unternehmen relevant sind abgeschlossen haben, können Sie auswählen, gehen Sie zum Hinzufügen von Benutzern in der anfänglichen Pilotgruppe.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="4cfc3-187">**OneDrive für Unternehmen**</span><span class="sxs-lookup"><span data-stu-id="4cfc3-187">**OneDrive for Business**</span></span>

<span data-ttu-id="4cfc3-p117">Wählen Sie OneDrive in das Startprogramm für Office 365-app, und bestätigen Sie, dass Sie automatisch an den entsprechenden Geo-Speicherort für den Benutzer, basierend auf der Benutzer Verteilerliste weitergeleitet werden. OneDrive für Unternehmen sollte an dieser Stelle Bereitstellung beginnen. Versuchen Sie nach der Bereitstellung, hoch- und Herunterladen von Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="4cfc3-191">**OneDrive Mobile App**</span><span class="sxs-lookup"><span data-stu-id="4cfc3-191">**OneDrive Mobile App**</span></span>

<span data-ttu-id="4cfc3-p118">Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Test. Vergewissern Sie sich, dass Ihre OneDrive for Business-Dateien angezeigt und können von Ihrem mobilen Gerät mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="4cfc3-194">**OneDrive Sync-client**</span><span class="sxs-lookup"><span data-stu-id="4cfc3-194">**OneDrive sync client**</span></span>

<span data-ttu-id="4cfc3-p119">Vergewissern Sie sich, dass der OneDrive-Synchronisierungsclient Ihrer OneDrive for Business Geo-Speicherort nach der Anmeldung automatisch erkennt. Wenn Sie den Sync-Client herunterladen müssen, können Sie die **Synchronisierung** in der Bibliothek OneDrive klicken.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="4cfc3-197">**Office-Anwendungen**</span><span class="sxs-lookup"><span data-stu-id="4cfc3-197">**Office applications**</span></span>

<span data-ttu-id="4cfc3-p120">Vergewissern Sie sich, dass Sie von einer Office-Anwendung, wie Word anmelden OneDrive für Unternehmen zugreifen können. Öffnen Sie das Office-Anwendung, und wählen "OneDrive – <TenantName>". Office erkennt Ihres Standorts für OneDrive und zeigen Sie die Dateien, die Sie öffnen können.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="4cfc3-201">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="4cfc3-201">**Sharing**</span></span>

<span data-ttu-id="4cfc3-p121">Versuchen Sie es Freigeben von OneDrive-Dateien. Vergewissern Sie sich, dass die Personenauswahl Sie alle SharePoint online Benutzer unabhängig von ihrem Geo-Standort angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4cfc3-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
