---
title: Zusammenarbeit mit Gästen in einer Website
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Hier erfahren Sie, wie Sie mit Gästen in einer SharePoint-Website zusammenarbeiten.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017313"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="1f400-103">Zusammenarbeit mit Gästen in einer Website</span><span class="sxs-lookup"><span data-stu-id="1f400-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="1f400-104">Wenn Sie mit Gästen in Dokumenten, Daten und Listen zusammenarbeiten müssen, können Sie eine SharePoint-Website verwenden.</span><span class="sxs-lookup"><span data-stu-id="1f400-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="1f400-105">Moderne SharePoint-Websites sind mit Office 365 Gruppen verbunden, die die Website Mitgliedschaft verwalten und zusätzliche Tools für die Zusammenarbeit wie ein freigegebenes Postfach und einen Kalender bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="1f400-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="1f400-106">In diesem Artikel werden die Microsoft 365-Konfigurationsschritte durchlaufen, die erforderlich sind, um eine SharePoint-Website für die Zusammenarbeit mit Gästen einzurichten.</span><span class="sxs-lookup"><span data-stu-id="1f400-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="1f400-107">Azure Organizational Relationships-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="1f400-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="1f400-108">Die Freigabe in Microsoft 365 wird auf der höchsten Ebene durch die Einstellungen für organisatorische Beziehungen in Azure Active Directory gesteuert.</span><span class="sxs-lookup"><span data-stu-id="1f400-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="1f400-109">Wenn die Gast Freigabe in Azure AD deaktiviert oder eingeschränkt ist, werden alle Freigabeeinstellungen, die Sie in Microsoft 365 konfigurieren, außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="1f400-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="1f400-110">Überprüfen Sie die Einstellungen für Organisationsbeziehungen, um sicherzustellen, dass die Freigabe für Gäste nicht blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="1f400-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Screenshot der Azure Active Directory-Seite "Organisationsbeziehungen – Einstellungen"](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="1f400-112">So legen Sie Einstellungen für die Organisationsbeziehung fest</span><span class="sxs-lookup"><span data-stu-id="1f400-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="1f400-113">Melden Sie sich bei Microsoft Azure [https://portal.azure.com](https://portal.azure.com)an an.</span><span class="sxs-lookup"><span data-stu-id="1f400-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="1f400-114">Klicken Sie im linken Navigationsbereich auf **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="1f400-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="1f400-115">Klicken Sie im Bereich **Übersicht** auf **Organisationsbeziehungen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="1f400-116">Klicken Sie im Bereich **Organisationsbeziehungen** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="1f400-117">Stellen Sie sicher, dass **Administratoren und Benutzer in der Rolle "Gast einladender" eingeladen** werden und **Mitglieder einladen können** , beide auf " **Ja**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="1f400-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="1f400-118">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1f400-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="1f400-119">Beachten Sie die Einstellungen im Abschnitt Einschränkungen für die **Zusammenarbeit** .</span><span class="sxs-lookup"><span data-stu-id="1f400-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="1f400-120">Stellen Sie sicher, dass die Domänen der Gäste, mit denen Sie zusammenarbeiten möchten, nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="1f400-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="1f400-121">Gast Einstellungen für Office 365 Gruppen</span><span class="sxs-lookup"><span data-stu-id="1f400-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="1f400-122">Moderne SharePoint-Websites verwenden Office 365 Gruppen, um den Website Zugriff zu steuern.</span><span class="sxs-lookup"><span data-stu-id="1f400-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="1f400-123">Die Gast Einstellungen für Office 365 Gruppen müssen aktiviert sein, damit der Gastzugriff auf SharePoint-Websites funktioniert.</span><span class="sxs-lookup"><span data-stu-id="1f400-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Screenshot von Office 365-Gruppen-Gast Einstellungen im Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

<span data-ttu-id="1f400-125">So legen Sie die Gast Einstellungen für Office 365 Gruppen fest</span><span class="sxs-lookup"><span data-stu-id="1f400-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="1f400-126">Erweitern Sie im Microsoft 365 Admin Center in der linken Navigationsleiste **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="1f400-127">Klicken Sie auf **Dienste #a0-Add-ins**.</span><span class="sxs-lookup"><span data-stu-id="1f400-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="1f400-128">Klicken Sie in der Liste auf **Office 365 Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="1f400-129">Stellen Sie sicher, dass die Gruppen **Mitglieder außerhalb Ihrer Organisation Zugriff auf Gruppeninhalte** haben und Gruppen **Besitzer Personen außerhalb Ihrer Organisation hinzufügen zulassen** Kontrollkästchen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="1f400-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="1f400-130">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Änderungen speichern**.</span><span class="sxs-lookup"><span data-stu-id="1f400-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="1f400-131">SharePoint-Freigabeeinstellungen auf Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="1f400-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="1f400-132">Damit Gästezugriff auf SharePoint-Websites haben, müssen die SharePoint-Freigabeeinstellungen auf Organisationsebene für die Freigabe für Gäste zulässig sein.</span><span class="sxs-lookup"><span data-stu-id="1f400-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="1f400-133">Die Einstellungen auf Organisationsebene bestimmen, welche Einstellungen für einzelne Websites verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="1f400-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="1f400-134">Websiteeinstellungen dürfen nicht so restriktiv wie die Einstellungen auf Organisationsebene sein.</span><span class="sxs-lookup"><span data-stu-id="1f400-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="1f400-135">Wenn Sie die Datei-und Ordnerfreigabe für anonyme Benutzer zulassen möchten, wählen Sie **jeden**aus.</span><span class="sxs-lookup"><span data-stu-id="1f400-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="1f400-136">Wenn Sie sicherstellen möchten, dass sich alle Gäste authentifizieren müssen, wählen Sie **neue und vorhandene Gäste**aus.</span><span class="sxs-lookup"><span data-stu-id="1f400-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="1f400-137">Wählen Sie die frei zügigste Einstellung aus, die von einer beliebigen Website in Ihrer Organisation benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="1f400-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Screenshot der SharePoint-Freigabeeinstellungen auf Organisationsebene](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="1f400-139">So legen Sie Freigabeeinstellungen für SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="1f400-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="1f400-140">Klicken Sie im Microsoft 365 Admin Center in der linken Navigationsleiste unter **Admin Centers**auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="1f400-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="1f400-141">Klicken Sie im SharePoint Admin Center im linken Navigationsbereich auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="1f400-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="1f400-142">Stellen Sie sicher, dass die externe Freigabe für SharePoint auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1f400-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="1f400-143">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1f400-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="1f400-144">Erstellen einer Website</span><span class="sxs-lookup"><span data-stu-id="1f400-144">Create a site</span></span>

<span data-ttu-id="1f400-145">Im nächsten Schritt erstellen Sie die Website, die Sie für die Zusammenarbeit mit Gästen verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1f400-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="1f400-146">So erstellen Sie eine Website</span><span class="sxs-lookup"><span data-stu-id="1f400-146">To create a site</span></span>
1. <span data-ttu-id="1f400-147">Klicken Sie im SharePoint Admin Center unter **Websites**auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="1f400-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="1f400-148">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-148">Click **Create**.</span></span>
3. <span data-ttu-id="1f400-149">Klicken Sie auf **Team Website**.</span><span class="sxs-lookup"><span data-stu-id="1f400-149">Click **Team site**.</span></span>
4. <span data-ttu-id="1f400-150">Geben Sie einen Websitenamen ein, und geben Sie einen Namen für den Gruppenbesitzer (Websitebesitzer) ein.</span><span class="sxs-lookup"><span data-stu-id="1f400-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="1f400-151">Wählen Sie unter **Erweiterte Einstellungen**aus, ob es sich um eine öffentliche oder private Website handeln soll.</span><span class="sxs-lookup"><span data-stu-id="1f400-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="1f400-152">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="1f400-152">Click **Next**.</span></span>
7. <span data-ttu-id="1f400-153">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-153">Click **Finish**.</span></span>

<span data-ttu-id="1f400-154">Wir laden Benutzer später ein.</span><span class="sxs-lookup"><span data-stu-id="1f400-154">We'll invite users later.</span></span> <span data-ttu-id="1f400-155">Als nächstes ist es wichtig, die Freigabeeinstellungen auf Standortebene für diese Website zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1f400-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="1f400-156">Freigabeeinstellungen für SharePoint-Websiteebene</span><span class="sxs-lookup"><span data-stu-id="1f400-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="1f400-157">Überprüfen Sie die Freigabeeinstellungen auf Standortebene, um sicherzustellen, dass die gewünschten Zugriffstypen für diese Website zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="1f400-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="1f400-158">Wenn Sie beispielsweise die Einstellungen auf Organisationsebene auf " **jeder**" festlegen, aber alle Gäste für diese Website authentifizieren möchten, stellen Sie sicher, dass die Freigabeeinstellungen auf Standortebene auf " **neu" und "vorhandene Gäste**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="1f400-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="1f400-159">Beachten Sie, dass die Website nicht für anonyme Benutzer (**jede** Einstellung) freigegeben werden kann, aber einzelne Dateien und Ordner können.</span><span class="sxs-lookup"><span data-stu-id="1f400-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Screenshot der externen Freigabeeinstellungen für SharePoint-Websites](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="1f400-161">So legen Sie Freigabeeinstellungen auf Websiteebene fest</span><span class="sxs-lookup"><span data-stu-id="1f400-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="1f400-162">Erweitern Sie im SharePoint Admin Center in der linken Navigationsleiste den Knoten **Websites** , und klicken Sie dann auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="1f400-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="1f400-163">Wählen Sie die Website aus, die Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="1f400-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="1f400-164">Klicken Sie im Menüband auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="1f400-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="1f400-165">Stellen Sie sicher, dass die Freigabe auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1f400-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="1f400-166">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1f400-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="1f400-167">Benutzer einladen</span><span class="sxs-lookup"><span data-stu-id="1f400-167">Invite users</span></span>

<span data-ttu-id="1f400-168">Die Einstellungen für die Gast Freigabe sind nun konfiguriert, sodass Sie mit dem Hinzufügen interner Benutzer und Gäste zu Ihrer Website beginnen können.</span><span class="sxs-lookup"><span data-stu-id="1f400-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="1f400-169">Der Website Zugriff wird über die zugehörige Office 365 Gruppe gesteuert, sodass Benutzer dort hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1f400-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="1f400-170">So laden Sie interne Benutzer zu einer Gruppe ein</span><span class="sxs-lookup"><span data-stu-id="1f400-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="1f400-171">Navigieren Sie zu der Website, auf der Sie Benutzer hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="1f400-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="1f400-172">Klicken Sie oben rechts auf **Mitglieder** .</span><span class="sxs-lookup"><span data-stu-id="1f400-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="1f400-173">Klicken Sie auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-173">Click **Add members**.</span></span>
4. <span data-ttu-id="1f400-174">Geben Sie die Namen oder e-Mail-Adressen der Benutzer ein, die Sie zur Website einladen möchten, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="1f400-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="1f400-175">Gastbenutzer können nicht von der Website hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1f400-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="1f400-176">Sie müssen Sie mit Outlook im Internet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1f400-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="1f400-177">So laden Sie Gäste zu einer Website ein</span><span class="sxs-lookup"><span data-stu-id="1f400-177">To invite guests to a site</span></span>
1. <span data-ttu-id="1f400-178">Klicken Sie in Outlook im Internet unter **Gruppen**auf die Gruppe, der Sie Mitglieder hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="1f400-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="1f400-179">Öffnen Sie die Gruppen Visitenkarte, und klicken Sie dann unter **Weitere Optionen** (...) auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="1f400-180">Geben Sie die e-Mail-Adressen der Gäste ein, die Sie einladen möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="1f400-181">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="1f400-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f400-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1f400-182">See Also</span></span>
