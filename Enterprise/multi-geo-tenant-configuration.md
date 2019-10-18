---
title: Office 365 Multi-Geo-Mandantenkonfiguration
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Erfahren Sie, wie Sie Office 365 Multi-Geo konfigurieren.
ms.openlocfilehash: e1e76482e6b775a2bb1b6ea4428112af738d6a5a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070011"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="6e93f-103">Office 365 Multi-Geo-Mandantenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="6e93f-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="6e93f-104">Bevor Sie Ihren Mandanten für Office 365 Multi-Geo konfigurieren, stellen Sie sicher, dass Sie [Plan für Office 365 Multi-Geo](plan-for-multi-geo.md) gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="6e93f-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="6e93f-105">Um die Schritte in diesem Artikel auszuführen, benötigen Sie eine Liste der geografischen Standorte, die Sie als Satellitenstandorte aktivieren möchten, und der Testbenutzer, die Sie für diese Standorte bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="6e93f-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="6e93f-106">Hinzufügen des Plans für Multi-Geo-Funktionen in Office 365 zu Ihrem Mandanten</span><span class="sxs-lookup"><span data-stu-id="6e93f-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="6e93f-107">Wenn Sie Office 365 Multi-Geo verwenden möchten, benötigen Sie den Plan _Multi-Geo Capabilities in Office 365_.</span><span class="sxs-lookup"><span data-stu-id="6e93f-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="6e93f-108">Arbeiten Sie mit Ihrem Kontoteam, um diesen Plan zu Ihrem Mandanten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="6e93f-109">Ihr Kontoteam setzt Sie mit dem entsprechenden Lizenzierungsexperten in Verbindung und konfiguriert Ihren Mandanten für Sie.</span><span class="sxs-lookup"><span data-stu-id="6e93f-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="6e93f-p103">Beachten Sie, dass der Plan für _Multi-Geo-Funktionen in Office 365_ ein Serviceplan auf Benutzerebene ist. Sie benötigen eine Lizenz für jeden Benutzer, der an einem Satellitenstandort gehostet werden soll. Sie können mit der Zeit weitere Lizenzen hinzufügen, wenn Sie Benutzer in Ihrem Satellitenstandort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="6e93f-113">Nachdem der Plan _Multi-Geo Capabilities in Office 365_ Ihrem Mandanten bereitgestellt wurde, steht die Registerkarte **Geografische Standorte** im Admin Center von OneDrive sowie SharePoint zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6e93f-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="6e93f-114">Hinzufügen von Satellitenstandorten zu Ihrem Mandanten</span><span class="sxs-lookup"><span data-stu-id="6e93f-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="6e93f-115">Sie müssen für jeden geografischen Standort, an dem Sie Daten speichern möchten, einen Satellitenstandort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="6e93f-116">In der folgenden Tabelle werden verfügbare geografische Standorte angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6e93f-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Screenshot der Seite mit geografischen Orten im SharePoint-Admin Center](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="6e93f-118">So fügen Sie einen Satellitenstandort hinzu</span><span class="sxs-lookup"><span data-stu-id="6e93f-118">To add a satellite location</span></span>

1. <span data-ttu-id="6e93f-119">Öffnen Sie das SharePoint Admin Center.</span><span class="sxs-lookup"><span data-stu-id="6e93f-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="6e93f-120">Navigieren Sie zu der Registerkarte **Geografische Standorte**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="6e93f-121">Klicken Sie auf **Ort hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-121">Click **Add location**.</span></span>

4. <span data-ttu-id="6e93f-122">Wählen Sie den Standort aus, den Sie hinzufügen möchten, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="6e93f-123">Geben Sie die Domäne ein, die Sie mit dem geografischen Standort verwenden möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="6e93f-124">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-124">Click **Close**.</span></span>

<span data-ttu-id="6e93f-p105">Die Bereitstellung kann je nach Größe des Mandanten bis zu 72 Stunden dauern. Sobald die Bereitstellung für einen Satellitenstandort abgeschlossen ist, erhalten Sie eine E-Mail-Bestätigung. Wenn der neue geografische Standort blau auf der Karte auf der Registerkarte **Geografische Standorte** im OneDrive Admin Center angezeigt wird, können Sie mit dem Festlegen der bevorzugten Datenspeicherorte für die Benutzer für diesen geografischen Standort fortfahren.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6e93f-p106">Ihr neuer Satellitenstandort wird mit Standardeinstellungen eingerichtet. Sie können diesen Satellitenstandort entsprechend den lokalen Complianceanforderungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="6e93f-130">Festlegen des bevorzugten Datenspeicherorts für Benutzer</span><span class="sxs-lookup"><span data-stu-id="6e93f-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="6e93f-p107">Nachdem Sie die erforderlichen Satellitenstandorte aktiviert haben, können Sie Ihre Benutzerkonten für die Verwendung des bevorzugten Datenspeicherorts aktualisieren. Es wird empfohlen, auch dann einen bevorzugten Datenspeicherort für jeden Benutzer festzulegen, wenn dieser Benutzer am zentralen Datenspeicherort verbleibt.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e93f-133">Wenn ein Standort, der noch nicht als Satellitenspeicherort oder zentraler Standort konfiguriert wurde, als bevorzugter Datenspeicherort eines Benutzers festgelegt wird, verwendet das System bei der Bereitstellung von OneDrive- und SharePoint-Websites sowie Gruppenpostfächern standardmäßig den zentralen Standort.</span><span class="sxs-lookup"><span data-stu-id="6e93f-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="6e93f-134">Es wird empfohlen, die Prüfungen mit einem Testbenutzer oder einer kleinen Gruppe von Benutzern durchzuführen, bevor die Multi-Geo-Funktionen für Ihre Organisation bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="6e93f-135">In Azure Active Directory gibt es zwei Arten von Benutzerobjekten: Nur-Cloud-Benutzer und synchronisierte Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6e93f-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="6e93f-136">Bitte befolgen Sie die Anweisungen für die entsprechende Benutzerart.</span><span class="sxs-lookup"><span data-stu-id="6e93f-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="6e93f-137">Synchronisieren des bevorzugten Datenspeicherorts von Benutzen mit Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="6e93f-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="6e93f-p109">Wenn für Benutzer in Ihrem Unternehmen eine Synchronisierung zwischen dem lokalen Active Directory-System und Azure Active Directory durchgeführt wird, muss PreferredDataLocation in AD aufgefüllt werden und mit AAD synchronisiert werden. Befolgen Sie den Prozess unter [Azure Active Directory Connect-Synchronisierung: Konfigurieren des bevorzugten Datenspeicherorts für Office 365-Ressourcen](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation), um die Synchronisierung der bevorzugten Datenspeicherorte zwischen lokalem Active Directory und Azure Active Directory zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="6e93f-140">Wir empfehlen, die Einstellung des bevorzugten Datenspeicherorts des Benutzers im Rahmen des Standardworkflows für das Erstellen von Benutzern hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e93f-141">Im Falle von Benutzern ohne bereitgestellte OneDrive-Umgebung sollten Sie nach der Synchronisierung des bevorzugten Datenspeicherortes mit Azure Active Directory mindestens 24 Stunden warten, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="6e93f-142">(Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung von OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="6e93f-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="6e93f-143">Festlegen des bevorzugten Datenspeicherorts für Nur-Cloud-Benutzer</span><span class="sxs-lookup"><span data-stu-id="6e93f-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="6e93f-144">Wenn die Benutzer Ihres Unternehmens über ein lokales Active Directory-System mit Azure Active Directory synchronisiert werden (d. h. wenn sie in Office 365 oder Azure Active Directory erstellt werden), muss der PDL über Azure Active Directory PowerShell festgelegt verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="6e93f-p111">Für die Vorgehensweisen in diesem Abschnitt ist das [Microsoft Azure Active Directory-Modul für Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0) erforderlich. Wenn Azure Active Directory PowerShell bereits installiert ist, stellen Sie sicher, dass Sie ein Update auf die neueste Version durchführen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="6e93f-147">Öffnen Sie das Microsoft Azure Active Directory-Modul für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e93f-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="6e93f-148">Führen Sie `Connect-MsolService` aus, und geben Sie die Anmeldeinformationen des globalen Administrators für Ihren Mandanten ein.</span><span class="sxs-lookup"><span data-stu-id="6e93f-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="6e93f-p112">Verwenden Sie das [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser)-Cmdlet zum Festlegen des bevorzugten Datenspeicherorts für jeden Benutzer. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e93f-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="6e93f-p113">Sie können mithilfe des Get-MsolUser-Cmdlets prüfen, ob der bevorzugte Datenspeicherort korrekt festgelegt wurde. Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6e93f-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Screenshot des PowerShell-Fensters mit Set-MsolUser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="6e93f-154">Wir empfehlen, die Einstellung des bevorzugten Datenspeicherorts von Benutzern im Rahmen des Standardworkflows für das Erstellen von Benutzern vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e93f-155">Im Falle von neuen Benutzern ohne bereitgestellte OneDrive-Umgebung sollten Sie nach der Einstellung des bevorzugten Datenspeicherortes mindestens 24 Stunden warten, damit die Änderungen in Kraft treten, bevor sich die Benutzer bei OneDrive for Business anmelden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="6e93f-156">(Durch Festlegen des bevorzugten Datenspeicherorts vor der Anmeldung des Benutzers für die Bereitstellung von OneDrive for Business wird sichergestellt, dass die neue OneDrive-Umgebung an dem richtigen Ort bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="6e93f-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="6e93f-157">Bereitstellung von OneDrive und Auswirkungen auf den bevorzugten Datenspeicherort</span><span class="sxs-lookup"><span data-stu-id="6e93f-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="6e93f-158">Wenn für einen Benutzer bereits eine OneDrive-Website im Mandanten erstellt wurde, wird beim Festlegen des bevorzugten Speicherorts die vorhandene OneDrive-Bereitstellung nicht automatisch verschoben.</span><span class="sxs-lookup"><span data-stu-id="6e93f-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="6e93f-159">Informationen zum Migrieren der OneDrive-Umgebung eines Benutzers finden Sie unter [Verschieben von One Drive for Business](move-onedrive-between-geo-locations.md). Befolgen Sie die Anweisungen zum Migrieren von OneDrive zwischen geografischen Standorten.</span><span class="sxs-lookup"><span data-stu-id="6e93f-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="6e93f-160">(Bitte beachten Sie, dass Exchange-Postfächer automatisch migriert werden, wenn Sie den PDL eines Benutzers festlegen.)</span><span class="sxs-lookup"><span data-stu-id="6e93f-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="6e93f-161">Wenn ein Benutzer nicht über eine OneDrive-Website innerhalb des Mandanten verfügt, wird OneDrive in Übereinstimmung mit den jeweiligen PDL-Einstellungen bereitgestellt, sofern der PDL des Benutzers einem der Satellitenstandorte des Unternehmens entspricht.</span><span class="sxs-lookup"><span data-stu-id="6e93f-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="6e93f-162">Konfigurieren der Multi-Geo-Suche</span><span class="sxs-lookup"><span data-stu-id="6e93f-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="6e93f-163">Der Multi-Geo-Mandant verfügt über aggregierte Suchfunktionen, mit denen eine Suchabfrage Ergebnisse von allen Orten innerhalb des Mandanten zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="6e93f-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="6e93f-164">Standardmäßig geben Suchen von diesen Einstiegspunkten aggregierte Ergebnisse zurück, auch wenn sich jeder Suchindex an dem jeweiligen relevanten geografischen Standort befindet:</span><span class="sxs-lookup"><span data-stu-id="6e93f-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="6e93f-165">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="6e93f-165">OneDrive for business</span></span>

- <span data-ttu-id="6e93f-166">Delve</span><span class="sxs-lookup"><span data-stu-id="6e93f-166">Delve</span></span>

- <span data-ttu-id="6e93f-167">SharePoint-Homepage</span><span class="sxs-lookup"><span data-stu-id="6e93f-167">SharePoint Home</span></span>

- <span data-ttu-id="6e93f-168">Suchcenter</span><span class="sxs-lookup"><span data-stu-id="6e93f-168">Search Center</span></span>

<span data-ttu-id="6e93f-169">Darüber hinaus können Multi-Geo-Suchfunktionen für Ihre benutzerdefinierte Suchanwendung konfiguriert werden, die die SharePoint-Suche-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="6e93f-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="6e93f-170">Anweisungen, einschließlich Einschränkungen und Unterschiede, finden Sie unter [Konfigurieren der Suche für Multi-Geo in OneDrive for Business](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="6e93f-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="6e93f-171">Überprüfen der Office 365 Multi-Geo-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6e93f-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="6e93f-172">Im Folgenden finden Sie einige grundlegende Anwendungsfälle, in denen eine Überprüfung vor dem Rollout von Office 365 Multi-Geo im Unternehmen möglicherweise sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="6e93f-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="6e93f-173">Nach Abschluss dieser Tests und zusätzlicher Anwendungsfälle, die für Ihr Unternehmen relevant sind, können Sie der ursprünglichen Pilotgruppe bei Bedarf weitere Benutzer hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="6e93f-174">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="6e93f-174">**OneDrive for Business**</span></span>

<span data-ttu-id="6e93f-175">Wählen Sie OneDrive im Office 365-Startprogramm aus und bestätigen Sie, dass Sie automatisch an den entsprechenden geografischen Standort des Benutzers (gemäß dessen PDL) weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="6e93f-176">OneDrive for Business sollte jetzt an diesem Standort bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6e93f-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="6e93f-177">Versuchen Sie nach der Bereitstellung, einige Dokumente hoch- und herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="6e93f-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="6e93f-178">**Mobile OneDrive-App**</span><span class="sxs-lookup"><span data-stu-id="6e93f-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="6e93f-p118">Melden Sie sich bei Ihrer mobilen OneDrive-App mit den Anmeldeinformationen Ihres Testkontos an. Stellen Sie sicher, dass Ihre OneDrive for Business-Dateien angezeigt werden und mit denjenigen auf Ihrem Mobilgerät interagieren können.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="6e93f-181">**OneDrive-Synchronisierungsclient**</span><span class="sxs-lookup"><span data-stu-id="6e93f-181">**OneDrive sync client**</span></span>

<span data-ttu-id="6e93f-p119">Vergewissern Sie sich, dass der OneDrive-Synchronisierungsclient den geografischen Standort für OneDrive for Business nach Anmeldung automatisch erkennt. Wenn Sie den Synchronisierungsclient herunterladen müssen, klicken Sie in der OneDrive-Bibliothek auf **Synchronisieren**.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="6e93f-184">**Office-Anwendungen**</span><span class="sxs-lookup"><span data-stu-id="6e93f-184">**Office applications**</span></span>

<span data-ttu-id="6e93f-p120">Vergewissern Sie sich, dass Sie auf OneDrive for Business zugreifen können, indem Sie sich von einer Office-Anwendung wie Word aus anmelden. Öffnen Sie die Office-Anwendung, und wählen Sie „OneDrive – <TenantName>„. Office erkennt Ihren OneDrive-Ort und zeigt die Dateien, die Sie öffnen können.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="6e93f-188">**Freigabe**</span><span class="sxs-lookup"><span data-stu-id="6e93f-188">**Sharing**</span></span>

<span data-ttu-id="6e93f-p121">Testen Sie die Freigabe von OneDrive-Dateien. Vergewissern Sie sich, dass die Personenauswahl alle SharePoint-Onlinebenutzer unabhängig vom geografischen Standort anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6e93f-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
