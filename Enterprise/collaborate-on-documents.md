---
title: Zusammenarbeiten mit Gästen in einem Dokument
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Hier erfahren Sie, wie Sie mit Gästen in einem Dokument in SharePoint und OneDrive zusammenarbeiten.
ms.openlocfilehash: ebb887e4fc337b4c0e94e85e0a08e87be0e74490
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108225"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="4b319-103">Zusammenarbeiten mit Gästen in einem Dokument</span><span class="sxs-lookup"><span data-stu-id="4b319-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="4b319-104">Wenn Sie mit Gästen in Dokumenten in SharePoint oder OneDrive zusammenarbeiten müssen, können Sie Ihnen einen Freigabe Link an das Dokument senden.</span><span class="sxs-lookup"><span data-stu-id="4b319-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="4b319-105">In diesem Artikel werden die Microsoft 365-Konfigurationsschritte durchlaufen, die erforderlich sind, um Freigabelinks für SharePoint und OneDrive für die Anforderungen Ihrer Organisation einzurichten.</span><span class="sxs-lookup"><span data-stu-id="4b319-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive for the needs of your organization.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="4b319-106">Azure Organizational Relationships-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="4b319-106">Azure Organizational relationships settings</span></span>

<span data-ttu-id="4b319-107">Die Freigabe in Microsoft 365 wird auf der höchsten Ebene durch die Einstellungen für organisatorische Beziehungen in Azure Active Directory gesteuert.</span><span class="sxs-lookup"><span data-stu-id="4b319-107">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="4b319-108">Wenn die Gast Freigabe in Azure AD deaktiviert oder eingeschränkt ist, werden alle Freigabeeinstellungen, die Sie in Microsoft 365 konfigurieren, außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="4b319-108">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="4b319-109">Überprüfen Sie die Einstellungen für Organisationsbeziehungen, um sicherzustellen, dass die Freigabe für Gäste nicht blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="4b319-109">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Screenshot der Azure Active Directory-Seite "Organisationsbeziehungen – Einstellungen"](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="4b319-111">So legen Sie Einstellungen für die Organisationsbeziehung fest</span><span class="sxs-lookup"><span data-stu-id="4b319-111">To set organizational relationship settings</span></span>

1. <span data-ttu-id="4b319-112">Melden Sie sich bei Microsoft Azure [https://portal.azure.com](https://portal.azure.com)an an.</span><span class="sxs-lookup"><span data-stu-id="4b319-112">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="4b319-113">Klicken Sie im linken Navigationsbereich auf **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="4b319-113">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="4b319-114">Klicken Sie im Bereich **Übersicht** auf **Organisationsbeziehungen**.</span><span class="sxs-lookup"><span data-stu-id="4b319-114">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="4b319-115">Klicken Sie im Bereich **Organisationsbeziehungen** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="4b319-115">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="4b319-116">Stellen Sie sicher, dass **Administratoren und Benutzer in der Rolle "Gast einladender" eingeladen** werden und **Mitglieder einladen können** , beide auf " **Ja**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="4b319-116">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="4b319-117">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4b319-117">If you made changes, click **Save**.</span></span>

<span data-ttu-id="4b319-118">Beachten Sie die Einstellungen im Abschnitt Einschränkungen für die **Zusammenarbeit** .</span><span class="sxs-lookup"><span data-stu-id="4b319-118">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="4b319-119">Stellen Sie sicher, dass die Domänen der Gäste, mit denen Sie zusammenarbeiten möchten, nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="4b319-119">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="4b319-120">SharePoint-Freigabeeinstellungen auf Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="4b319-120">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="4b319-121">Damit Gästezugriff auf ein Dokument in SharePoint oder OneDrive haben, müssen die Freigabeeinstellungen für SharePoint und OneDrive auf Organisationsebene für die Freigabe für Gäste zulässig sein.</span><span class="sxs-lookup"><span data-stu-id="4b319-121">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="4b319-122">Die Einstellungen auf Organisationsebene für SharePoint bestimmen, welche Einstellungen für einzelne SharePoint-Websites verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4b319-122">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="4b319-123">Websiteeinstellungen dürfen nicht so restriktiv wie die Einstellungen auf Organisationsebene sein.</span><span class="sxs-lookup"><span data-stu-id="4b319-123">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="4b319-124">Die Einstellung auf Organisationsebene für OneDrive legt fest, welche Freigabeebene in den OneDrive-Bibliotheken der Benutzer verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="4b319-124">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="4b319-125">Wenn Sie für SharePoint und OneDrive die Datei-und Ordnerfreigabe für anonyme Benutzer zulassen möchten, wählen Sie **jeden**aus.</span><span class="sxs-lookup"><span data-stu-id="4b319-125">For SharePoint and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="4b319-126">Wenn Sie sicherstellen möchten, dass sich alle Gäste authentifizieren müssen, wählen Sie **neue und vorhandene Gäste**aus.</span><span class="sxs-lookup"><span data-stu-id="4b319-126">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="4b319-127">*Jeder* Link ist die einfachste Möglichkeit zu teilen: Gäste können den Link ohne Authentifizierung öffnen und sind frei, um ihn an andere weiterzugeben.</span><span class="sxs-lookup"><span data-stu-id="4b319-127">*Anyone* links are the easiest way to share: guests can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="4b319-128">Wählen Sie für SharePoint die frei zügigste Einstellung aus, die von einer beliebigen Website in Ihrer Organisation benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="4b319-128">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Screenshot der SharePoint-Freigabeeinstellungen auf Organisationsebene](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="4b319-130">So legen Sie Freigabeeinstellungen für SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="4b319-130">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="4b319-131">Klicken Sie im Microsoft 365 Admin Center in der linken Navigationsleiste unter **Admin Centers**auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4b319-131">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="4b319-132">Klicken Sie im SharePoint Admin Center im linken Navigationsbereich auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="4b319-132">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="4b319-133">Stellen Sie sicher, dass die externe Freigabe für SharePoint oder OneDrive auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4b319-133">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="4b319-134">(Beachten Sie, dass die OneDrive-Einstellung nicht restriktiver als die SharePoint-Einstellung sein kann.)</span><span class="sxs-lookup"><span data-stu-id="4b319-134">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="4b319-135">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4b319-135">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="4b319-136">Standard Link Einstellungen für SharePoint-Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="4b319-136">SharePoint organization level default link settings</span></span>

<span data-ttu-id="4b319-137">Die Standardeinstellungen für Datei-und Ordnerverknüpfung legen fest, welche Link Option dem Benutzer standardmäßig angezeigt wird, wenn er eine Datei oder einen Ordner freigegeben hat.</span><span class="sxs-lookup"><span data-stu-id="4b319-137">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="4b319-138">Benutzer können den Verknüpfungstyp vor der Freigabe bei Bedarf in eine der anderen Optionen ändern.</span><span class="sxs-lookup"><span data-stu-id="4b319-138">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="4b319-139">Beachten Sie, dass sich diese Einstellung auf SharePoint-Websites in Ihrer Organisation sowie auf OneDrive auswirkt.</span><span class="sxs-lookup"><span data-stu-id="4b319-139">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="4b319-140">Wählen Sie den Linktyp aus, der standardmäßig ausgewählt ist, wenn Benutzer Dateien und Ordner freigeben:</span><span class="sxs-lookup"><span data-stu-id="4b319-140">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="4b319-141">**Jeder, der über den Link verfügt** – wählen Sie diese Option aus, wenn Sie eine Vielzahl von Dateien und Ordnern für anonyme Benutzer freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="4b319-141">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="4b319-142">Wenn Sie *jeder* Verknüpfung erlauben möchten, aber über die versehentliche anonyme Freigabe besorgt sind, sollten Sie eine der anderen Optionen als Standard verwenden.</span><span class="sxs-lookup"><span data-stu-id="4b319-142">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="4b319-143">Dieser Linktyp ist nur verfügbar, wenn Sie die Freigabe von **Benutzern** aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="4b319-143">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="4b319-144">**Nur Personen in Ihrer Organisation** – wählen Sie diese Option aus, wenn Sie davon ausgehen, dass die meisten Datei-und Ordner Freigaben für Personen in Ihrer Organisation gelten.</span><span class="sxs-lookup"><span data-stu-id="4b319-144">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="4b319-145">**Bestimmte Personen** – diese Option wird empfohlen, wenn Sie eine Vielzahl von Datei-und Ordner Freigaben für Gäste erwarten.</span><span class="sxs-lookup"><span data-stu-id="4b319-145">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="4b319-146">Diese Art von Link funktioniert mit Gästen und erfordert die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="4b319-146">This type of link works with guests and requires them to authenticate.</span></span>
 
![Screenshot der SharePoint-Freigabeeinstellungen für Dateien und Ordner auf Organisationsebene](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="4b319-148">So legen Sie die Standard Link Einstellungen für SharePoint und OneDrive auf Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="4b319-148">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="4b319-149">Navigieren Sie im SharePoint Admin Center zur Seite Freigabe.</span><span class="sxs-lookup"><span data-stu-id="4b319-149">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="4b319-150">Wählen Sie unter **Datei-und Ordner Links**den standardmäßigen Freigabe Link aus, den Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="4b319-150">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="4b319-151">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4b319-151">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="4b319-152">Freigabeeinstellungen für SharePoint-Websiteebene</span><span class="sxs-lookup"><span data-stu-id="4b319-152">SharePoint site level sharing settings</span></span>

<span data-ttu-id="4b319-153">Wenn Sie Dateien und fodlers in einer SharePoint-Website freigeben, müssen Sie auch die Freigabeeinstellungen auf Websiteebene für diese Website überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4b319-153">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![Screenshot der externen Freigabeeinstellungen für SharePoint-Websites](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="4b319-155">So legen Sie Freigabeeinstellungen auf Websiteebene fest</span><span class="sxs-lookup"><span data-stu-id="4b319-155">To set site-level sharing settings</span></span>
1. <span data-ttu-id="4b319-156">Erweitern Sie im SharePoint Admin Center in der linken Navigationsleiste den Knoten **Websites** , und klicken Sie dann auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="4b319-156">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="4b319-157">Wählen Sie die Website aus, die Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="4b319-157">Select the site that you just created.</span></span>
3. <span data-ttu-id="4b319-158">Klicken Sie im Menüband auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="4b319-158">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="4b319-159">Stellen Sie sicher, dass die Freigabe auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4b319-159">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="4b319-160">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="4b319-160">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="4b319-161">Benutzer einladen</span><span class="sxs-lookup"><span data-stu-id="4b319-161">Invite users</span></span>

<span data-ttu-id="4b319-162">Die Einstellungen für die Gast Freigabe sind jetzt konfiguriert, sodass Benutzer nun Dateien und Ordner für Gäste freigeben können.</span><span class="sxs-lookup"><span data-stu-id="4b319-162">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="4b319-163">Weitere Informationen finden Sie unter [Freigeben von OneDrive-Dateien und-Ordnern](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) und Freigeben von [SharePoint-Dateien oder-Ordnern](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) .</span><span class="sxs-lookup"><span data-stu-id="4b319-163">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b319-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4b319-164">See Also</span></span>
