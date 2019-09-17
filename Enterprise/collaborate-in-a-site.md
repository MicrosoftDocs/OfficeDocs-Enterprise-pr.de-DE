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
ms.openlocfilehash: 23f55e22d4c85dcd168c403f50b35f574be9ac07
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992384"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="3bd67-103">Zusammenarbeit mit Gästen in einer Website</span><span class="sxs-lookup"><span data-stu-id="3bd67-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="3bd67-104">Wenn Sie mit Gästen in Dokumenten, Daten und Listen zusammenarbeiten müssen, können Sie eine SharePoint-Website verwenden.</span><span class="sxs-lookup"><span data-stu-id="3bd67-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="3bd67-105">Moderne SharePoint-Websites sind mit Office 365 Gruppen verbunden, die die Website Mitgliedschaft verwalten und zusätzliche Tools für die Zusammenarbeit wie ein freigegebenes Postfach und einen Kalender bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="3bd67-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="3bd67-106">In diesem Artikel werden die Microsoft 365-Konfigurationsschritte durchlaufen, die erforderlich sind, um eine SharePoint-Website für die Zusammenarbeit mit Gästen einzurichten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="3bd67-107">Azure Organizational Relationships-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="3bd67-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="3bd67-108">Die Freigabe in Microsoft 365 wird auf der höchsten Ebene durch die Einstellungen für organisatorische Beziehungen in Azure Active Directory gesteuert.</span><span class="sxs-lookup"><span data-stu-id="3bd67-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="3bd67-109">Wenn die Gast Freigabe in Azure AD deaktiviert oder eingeschränkt ist, werden alle Freigabeeinstellungen, die Sie in Microsoft 365 konfigurieren, außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="3bd67-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="3bd67-110">Überprüfen Sie die Einstellungen für Organisationsbeziehungen, um sicherzustellen, dass die Freigabe für Gäste nicht blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="3bd67-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Screenshot der Azure Active Directory-Seite "Organisationsbeziehungen – Einstellungen"](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="3bd67-112">So legen Sie Einstellungen für die Organisationsbeziehung fest</span><span class="sxs-lookup"><span data-stu-id="3bd67-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="3bd67-113">Melden Sie sich bei Microsoft Azure [https://portal.azure.com](https://portal.azure.com)an an.</span><span class="sxs-lookup"><span data-stu-id="3bd67-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="3bd67-114">Klicken Sie im linken Navigationsbereich auf **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="3bd67-115">Klicken Sie im Bereich **Übersicht** auf **Organisationsbeziehungen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="3bd67-116">Klicken Sie im Bereich **Organisationsbeziehungen** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="3bd67-117">Stellen Sie sicher, dass **Administratoren und Benutzer in der Rolle "Gast einladender" eingeladen** werden und **Mitglieder einladen können** , beide auf " **Ja**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="3bd67-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="3bd67-118">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="3bd67-119">Beachten Sie die Einstellungen im Abschnitt Einschränkungen für die **Zusammenarbeit** .</span><span class="sxs-lookup"><span data-stu-id="3bd67-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="3bd67-120">Stellen Sie sicher, dass die Domänen der Gäste, mit denen Sie zusammenarbeiten möchten, nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="3bd67-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="3bd67-121">Gast Einstellungen für Office 365 Gruppen</span><span class="sxs-lookup"><span data-stu-id="3bd67-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="3bd67-122">Moderne SharePoint-Websites verwenden Office 365 Gruppen, um den Website Zugriff zu steuern.</span><span class="sxs-lookup"><span data-stu-id="3bd67-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="3bd67-123">Die Gast Einstellungen für Office 365 Gruppen müssen aktiviert sein, damit der Gastzugriff auf SharePoint-Websites funktioniert.</span><span class="sxs-lookup"><span data-stu-id="3bd67-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Screenshot von Office 365-Gruppen-Gast Einstellungen im Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

<span data-ttu-id="3bd67-125">So legen Sie die Gast Einstellungen für Office 365 Gruppen fest</span><span class="sxs-lookup"><span data-stu-id="3bd67-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="3bd67-126">Erweitern Sie im Microsoft 365 Admin Center in der linken Navigationsleiste **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="3bd67-127">Klicken Sie auf **Dienste #a0-Add-ins**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="3bd67-128">Klicken Sie in der Liste auf **Office 365 Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="3bd67-129">Stellen Sie sicher, dass die Gruppen **Mitglieder außerhalb Ihrer Organisation Zugriff auf Gruppeninhalte** haben und Gruppen **Besitzer Personen außerhalb Ihrer Organisation hinzufügen zulassen** Kontrollkästchen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="3bd67-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="3bd67-130">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Änderungen speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="3bd67-131">SharePoint-Freigabeeinstellungen auf Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="3bd67-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="3bd67-132">Damit Gästezugriff auf SharePoint-Websites haben, müssen die SharePoint-Freigabeeinstellungen auf Organisationsebene für die Freigabe für Gäste zulässig sein.</span><span class="sxs-lookup"><span data-stu-id="3bd67-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="3bd67-133">Die Einstellungen auf Organisationsebene bestimmen, welche Einstellungen für einzelne Websites verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="3bd67-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="3bd67-134">Websiteeinstellungen dürfen nicht so restriktiv wie die Einstellungen auf Organisationsebene sein.</span><span class="sxs-lookup"><span data-stu-id="3bd67-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="3bd67-135">Wenn Sie die Datei-und Ordnerfreigabe für anonyme Benutzer zulassen möchten, wählen Sie **jeden**aus.</span><span class="sxs-lookup"><span data-stu-id="3bd67-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="3bd67-136">Wenn Sie sicherstellen möchten, dass sich alle Gäste authentifizieren müssen, wählen Sie **neue und vorhandene Gäste**aus.</span><span class="sxs-lookup"><span data-stu-id="3bd67-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="3bd67-137">Wählen Sie die frei zügigste Einstellung aus, die von einer beliebigen Website in Ihrer Organisation benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="3bd67-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Screenshot der SharePoint-Freigabeeinstellungen auf Organisationsebene](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="3bd67-139">So legen Sie Freigabeeinstellungen für SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="3bd67-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="3bd67-140">Klicken Sie im Microsoft 365 Admin Center in der linken Navigationsleiste unter **Admin Centers**auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="3bd67-141">Klicken Sie im SharePoint Admin Center im linken Navigationsbereich auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="3bd67-142">Stellen Sie sicher, dass die externe Freigabe für SharePoint auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3bd67-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="3bd67-143">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-143">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="3bd67-144">Standard Link Einstellungen für SharePoint-Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="3bd67-144">SharePoint organization level default link settings</span></span>

<span data-ttu-id="3bd67-145">Die Standardeinstellungen für Datei-und Ordnerverknüpfung legen fest, welche Link Option dem Benutzer standardmäßig angezeigt wird, wenn er eine Datei oder einen Ordner freigegeben hat.</span><span class="sxs-lookup"><span data-stu-id="3bd67-145">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="3bd67-146">Benutzer können den Verknüpfungstyp vor der Freigabe bei Bedarf in eine der anderen Optionen ändern.</span><span class="sxs-lookup"><span data-stu-id="3bd67-146">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="3bd67-147">Beachten Sie, dass sich diese Einstellung auf alle Teams und SharePoint-Websites in Ihrer Organisation auswirkt.</span><span class="sxs-lookup"><span data-stu-id="3bd67-147">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="3bd67-148">Wählen Sie den Linktyp aus, der standardmäßig ausgewählt ist, wenn Benutzer Dateien und Ordner freigeben:</span><span class="sxs-lookup"><span data-stu-id="3bd67-148">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="3bd67-149">**Jeder, der über den Link verfügt** – wählen Sie diese Option aus, wenn Sie eine Vielzahl von Dateien und Ordnern für anonyme Benutzer freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-149">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="3bd67-150">Wenn Sie *jeder* Verknüpfung erlauben möchten, aber über die versehentliche anonyme Freigabe besorgt sind, sollten Sie eine der anderen Optionen als Standard verwenden.</span><span class="sxs-lookup"><span data-stu-id="3bd67-150">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="3bd67-151">Dieser Linktyp ist nur verfügbar, wenn Sie die Freigabe von **Benutzern** aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="3bd67-151">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="3bd67-152">**Nur Personen in Ihrer Organisation** – wählen Sie diese Option aus, wenn Sie davon ausgehen, dass die meisten Datei-und Ordner Freigaben für Personen in Ihrer Organisation gelten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-152">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="3bd67-153">**Bestimmte Personen** – diese Option wird empfohlen, wenn Sie eine Vielzahl von Datei-und Ordner Freigaben für Gäste erwarten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-153">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="3bd67-154">Diese Art von Link funktioniert mit Gästen und erfordert die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="3bd67-154">This type of link works with guests and requires them to authenticate.</span></span>
 
![Screenshot der SharePoint-Freigabeeinstellungen für Dateien und Ordner auf Organisationsebene](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="3bd67-156">So legen Sie die Standard Link Einstellungen für die SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="3bd67-156">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="3bd67-157">Navigieren Sie im SharePoint Admin Center zur Seite Freigabe.</span><span class="sxs-lookup"><span data-stu-id="3bd67-157">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="3bd67-158">Wählen Sie unter **Datei-und Ordner Links**den standardmäßigen Freigabe Link aus, den Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-158">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="3bd67-159">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-159">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="3bd67-160">Erstellen einer Website</span><span class="sxs-lookup"><span data-stu-id="3bd67-160">Create a site</span></span>

<span data-ttu-id="3bd67-161">Im nächsten Schritt erstellen Sie die Website, die Sie für die Zusammenarbeit mit Gästen verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-161">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="3bd67-162">So erstellen Sie eine Website</span><span class="sxs-lookup"><span data-stu-id="3bd67-162">To create a site</span></span>
1. <span data-ttu-id="3bd67-163">Klicken Sie im SharePoint Admin Center unter **Websites**auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-163">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="3bd67-164">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-164">Click **Create**.</span></span>
3. <span data-ttu-id="3bd67-165">Klicken Sie auf **Team Website**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-165">Click **Team site**.</span></span>
4. <span data-ttu-id="3bd67-166">Geben Sie einen Websitenamen ein, und geben Sie einen Namen für den Gruppenbesitzer (Websitebesitzer) ein.</span><span class="sxs-lookup"><span data-stu-id="3bd67-166">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="3bd67-167">Wählen Sie unter **Erweiterte Einstellungen**aus, ob es sich um eine öffentliche oder private Website handeln soll.</span><span class="sxs-lookup"><span data-stu-id="3bd67-167">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="3bd67-168">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-168">Click **Next**.</span></span>
7. <span data-ttu-id="3bd67-169">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-169">Click **Finish**.</span></span>

<span data-ttu-id="3bd67-170">Wir laden Benutzer später ein.</span><span class="sxs-lookup"><span data-stu-id="3bd67-170">We'll invite users later.</span></span> <span data-ttu-id="3bd67-171">Als nächstes ist es wichtig, die Freigabeeinstellungen auf Standortebene für diese Website zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="3bd67-171">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="3bd67-172">Freigabeeinstellungen für SharePoint-Websiteebene</span><span class="sxs-lookup"><span data-stu-id="3bd67-172">SharePoint site level sharing settings</span></span>

<span data-ttu-id="3bd67-173">Überprüfen Sie die Freigabeeinstellungen auf Standortebene, um sicherzustellen, dass die gewünschten Zugriffstypen für diese Website zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="3bd67-173">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="3bd67-174">Wenn Sie beispielsweise die Einstellungen auf Organisationsebene auf " **jeder**" festlegen, aber alle Gäste für diese Website authentifizieren möchten, stellen Sie sicher, dass die Freigabeeinstellungen auf Standortebene auf " **neu" und "vorhandene Gäste**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="3bd67-174">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="3bd67-175">Beachten Sie, dass die Website nicht für anonyme Benutzer (**jede** Einstellung) freigegeben werden kann, aber einzelne Dateien und Ordner können.</span><span class="sxs-lookup"><span data-stu-id="3bd67-175">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Screenshot der externen Freigabeeinstellungen für SharePoint-Websites](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="3bd67-177">So legen Sie Freigabeeinstellungen auf Websiteebene fest</span><span class="sxs-lookup"><span data-stu-id="3bd67-177">To set site-level sharing settings</span></span>
1. <span data-ttu-id="3bd67-178">Erweitern Sie im SharePoint Admin Center in der linken Navigationsleiste den Knoten **Websites** , und klicken Sie dann auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-178">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="3bd67-179">Wählen Sie die Website aus, die Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="3bd67-179">Select the site that you just created.</span></span>
3. <span data-ttu-id="3bd67-180">Klicken Sie im Menüband auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-180">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="3bd67-181">Stellen Sie sicher, dass die Freigabe auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3bd67-181">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="3bd67-182">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-182">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="3bd67-183">Benutzer einladen</span><span class="sxs-lookup"><span data-stu-id="3bd67-183">Invite users</span></span>

<span data-ttu-id="3bd67-184">Die Einstellungen für die Gast Freigabe sind nun konfiguriert, sodass Sie mit dem Hinzufügen interner Benutzer und Gäste zu Ihrer Website beginnen können.</span><span class="sxs-lookup"><span data-stu-id="3bd67-184">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="3bd67-185">Der Website Zugriff wird über die zugehörige Office 365 Gruppe gesteuert, sodass Benutzer dort hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3bd67-185">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="3bd67-186">So laden Sie interne Benutzer zu einer Gruppe ein</span><span class="sxs-lookup"><span data-stu-id="3bd67-186">To invite internal users to a group</span></span>
1. <span data-ttu-id="3bd67-187">Navigieren Sie zu der Website, auf der Sie Benutzer hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-187">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="3bd67-188">Klicken Sie oben rechts auf **Mitglieder** .</span><span class="sxs-lookup"><span data-stu-id="3bd67-188">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="3bd67-189">Klicken Sie auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-189">Click **Add members**.</span></span>
4. <span data-ttu-id="3bd67-190">Geben Sie die Namen oder e-Mail-Adressen der Benutzer ein, die Sie zur Website einladen möchten, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-190">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="3bd67-191">Gastbenutzer können nicht von der Website hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3bd67-191">Guest users can't be added from the site.</span></span> <span data-ttu-id="3bd67-192">Sie müssen Sie mit Outlook im Internet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3bd67-192">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="3bd67-193">So laden Sie Gäste zu einer Website ein</span><span class="sxs-lookup"><span data-stu-id="3bd67-193">To invite guests to a site</span></span>
1. <span data-ttu-id="3bd67-194">Klicken Sie in Outlook im Internet unter **Gruppen**auf die Gruppe, der Sie Mitglieder hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="3bd67-194">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="3bd67-195">Öffnen Sie die Gruppen Visitenkarte, und klicken Sie dann unter **Weitere Optionen** (...) auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-195">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="3bd67-196">Geben Sie die e-Mail-Adressen der Gäste ein, die Sie einladen möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-196">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="3bd67-197">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="3bd67-197">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bd67-198">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3bd67-198">See Also</span></span>
