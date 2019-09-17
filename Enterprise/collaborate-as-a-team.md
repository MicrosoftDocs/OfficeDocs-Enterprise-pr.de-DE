---
title: Zusammenarbeit mit Gästen in einem Team
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Hier erfahren Sie, wie Sie mit Gästen in Microsoft Teams zusammenarbeiten.
ms.openlocfilehash: 9a169e33a9cbd8f079966443bd3d830aa79f4971
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992414"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="a0fdd-103">Zusammenarbeit mit Gästen in einem Team</span><span class="sxs-lookup"><span data-stu-id="a0fdd-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="a0fdd-104">Wenn Sie mit Gästen in Dokumenten, Aufgaben und Unterhaltungen zusammenarbeiten müssen, empfehlen wir die Verwendung von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="a0fdd-105">Microsoft Teams bietet alle in Office und SharePoint verfügbaren Features für die Zusammenarbeit mit beständigem Chat sowie eine anpassbare und erweiterbare Gruppe von Tools für die Zusammenarbeit in einer einheitlichen Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="a0fdd-106">In diesem Artikel werden die Microsoft 365-Konfigurationsschritte durchlaufen, die erforderlich sind, um ein Team für die Zusammenarbeit mit Gästen einzurichten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="a0fdd-107">Azure Organizational Relationships-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a0fdd-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="a0fdd-108">Die Freigabe in Microsoft 365 wird auf der höchsten Ebene durch die Einstellungen für organisatorische Beziehungen in Azure Active Directory gesteuert.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="a0fdd-109">Wenn die Gast Freigabe in Azure AD deaktiviert oder eingeschränkt ist, werden alle Freigabeeinstellungen, die Sie in Microsoft 365 konfigurieren, außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="a0fdd-110">Überprüfen Sie die Einstellungen für Organisationsbeziehungen, um sicherzustellen, dass die Freigabe für Gäste nicht blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Screenshot der Azure Active Directory-Seite "Organisationsbeziehungen – Einstellungen"](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="a0fdd-112">So legen Sie Einstellungen für die Organisationsbeziehung fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="a0fdd-113">Melden Sie sich bei Microsoft Azure [https://portal.azure.com](https://portal.azure.com)an an.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="a0fdd-114">Klicken Sie im linken Navigationsbereich auf **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="a0fdd-115">Klicken Sie im Bereich **Übersicht** auf **Organisationsbeziehungen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="a0fdd-116">Klicken Sie im Bereich **Organisationsbeziehungen** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="a0fdd-117">Stellen Sie sicher, dass **Administratoren und Benutzer in der Rolle "Gast einladender" eingeladen** werden und **Mitglieder einladen können** , beide auf " **Ja**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="a0fdd-118">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="a0fdd-119">Beachten Sie die Einstellungen im Abschnitt Einschränkungen für die **Zusammenarbeit** .</span><span class="sxs-lookup"><span data-stu-id="a0fdd-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="a0fdd-120">Stellen Sie sicher, dass die Domänen der Gäste, mit denen Sie zusammenarbeiten möchten, nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="a0fdd-121">Einstellungen für den Gastzugriff in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a0fdd-121">Teams guest access settings</span></span>

<span data-ttu-id="a0fdd-122">Teams verfügt über einen Master ein/aus-Schalter für Gastzugriff und eine Vielzahl von Einstellungen zur Verfügung, um zu steuern, was Gäste in einem Team tun können.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-122">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="a0fdd-123">Der Hauptschalter, der den **Gastzugriff in Microsoft Teams zulässt** , muss für den Gastzugriff für die Arbeit in Microsoft Teams **eingeschaltet** sein.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-123">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="a0fdd-124">Stellen Sie sicher, dass der Gastzugriff in Microsoft Teams aktiviert ist, und nehmen Sie entsprechend Ihren geschäftlichen Anforderungen eine Anpassung an die Gast Einstellungen vor.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-124">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="a0fdd-125">Beachten Sie, dass sich diese Einstellungen auf alle Teams auswirken.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-125">Keep in mind that these settings affect all teams.</span></span>

![Screenshot der Microsoft Teams-Gastzugriffs-Umschaltfläche](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="a0fdd-127">So legen Sie die Einstellungen für den Gastzugriff für Teams fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-127">To set Teams guest access settings</span></span>

1. <span data-ttu-id="a0fdd-128">Melden Sie sich beim Microsoft 365 Admin Center unter [https://admin.microsoft.com](https://admin.microsoft.com)an.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-128">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="a0fdd-129">Klicken Sie im linken Navigationsbereich auf **Alle anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-129">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="a0fdd-130">Klicken Sie unter **Admin Center**auf **Teams**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-130">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="a0fdd-131">Erweitern Sie im Teamadministrator Center im linken Navigationsbereich die Option **organisationsweite Einstellungen** , und klicken Sie dann auf **Gastzugriff**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-131">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="a0fdd-132">Stellen Sie sicher, dass **Gastzugriff in Microsoft Teams zulassen** auf **ein**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-132">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="a0fdd-133">Nehmen Sie die gewünschten Änderungen an den zusätzlichen Gast Einstellungen vor, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-133">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="a0fdd-134">Es kann bis zu vierundzwanzig Stunden dauern, bis die Einstellung für die Teams-Gast Aktivität aktiviert wird, nachdem Sie sie aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-134">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="a0fdd-135">Gast Einstellungen für Office 365 Gruppen</span><span class="sxs-lookup"><span data-stu-id="a0fdd-135">Office 365 Groups guest settings</span></span>

<span data-ttu-id="a0fdd-136">Teams verwendet Office 365 Gruppen für die Teammitgliedschaft.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-136">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="a0fdd-137">Die Gast Einstellungen für die Office 365 Gruppen müssen aktiviert sein, damit der Gastzugriff in Microsoft Teams funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-137">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Screenshot von Office 365-Gruppen-Gast Einstellungen im Microsoft 365 Admin Center](media/office-365-groups-guest-settings.png)

<span data-ttu-id="a0fdd-139">So legen Sie die Gast Einstellungen für Office 365 Gruppen fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-139">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="a0fdd-140">Erweitern Sie im Microsoft 365 Admin Center in der linken Navigationsleiste **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-140">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="a0fdd-141">Klicken Sie auf **Dienste #a0-Add-ins**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-141">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="a0fdd-142">Klicken Sie in der Liste auf **Office 365 Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-142">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="a0fdd-143">Stellen Sie sicher, dass die Gruppen **Mitglieder außerhalb Ihrer Organisation Zugriff auf Gruppeninhalte** haben und Gruppen **Besitzer Personen außerhalb Ihrer Organisation hinzufügen zulassen** Kontrollkästchen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-143">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="a0fdd-144">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Änderungen speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-144">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="a0fdd-145">SharePoint-Freigabeeinstellungen auf Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="a0fdd-145">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="a0fdd-146">Damit die Gästezugriff auf Dateien in Microsoft Teams haben, müssen die SharePoint-Freigabeeinstellungen auf Organisationsebene für die Freigabe für Gäste zulässig sein.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-146">In order for guests to have access to files in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="a0fdd-147">Mit den Einstellungen auf Organisationsebene wird festgelegt, welche Einstellungen für einzelne Websites verfügbar sind, einschließlich der Websites, die Microsoft Teams zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-147">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="a0fdd-148">Websiteeinstellungen dürfen nicht so restriktiv wie die Einstellungen auf Organisationsebene sein.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-148">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="a0fdd-149">Wenn Sie die Datei-und Ordnerfreigabe für anonyme Benutzer zulassen möchten, wählen Sie **jeden**aus.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-149">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="a0fdd-150">Wenn Sie sicherstellen möchten, dass sich alle Gäste authentifizieren müssen, wählen Sie **neue und vorhandene Gäste**aus.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-150">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="a0fdd-151">Wählen Sie die frei zügigste Einstellung aus, die von einer beliebigen Website in Ihrer Organisation benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-151">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Screenshot der SharePoint-Freigabeeinstellungen auf Organisationsebene](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="a0fdd-153">So legen Sie Freigabeeinstellungen für SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-153">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="a0fdd-154">Klicken Sie im Microsoft 365 Admin Center in der linken Navigationsleiste unter **Admin Centers**auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-154">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="a0fdd-155">Klicken Sie im SharePoint Admin Center im linken Navigationsbereich auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-155">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="a0fdd-156">Stellen Sie sicher, dass die externe Freigabe für SharePoint auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-156">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="a0fdd-157">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-157">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="a0fdd-158">Standard Link Einstellungen für SharePoint-Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="a0fdd-158">SharePoint organization level default link settings</span></span>

<span data-ttu-id="a0fdd-159">Die Standardeinstellungen für Datei-und Ordnerverknüpfung legen fest, welche Link Option dem Benutzer standardmäßig angezeigt wird, wenn er eine Datei oder einen Ordner freigegeben hat.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-159">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="a0fdd-160">Benutzer können den Verknüpfungstyp vor der Freigabe bei Bedarf in eine der anderen Optionen ändern.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-160">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="a0fdd-161">Beachten Sie, dass sich diese Einstellung auf alle Teams und SharePoint-Websites in Ihrer Organisation auswirkt.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-161">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="a0fdd-162">Wählen Sie den Linktyp aus, der standardmäßig ausgewählt ist, wenn Benutzer Dateien und Ordner freigeben:</span><span class="sxs-lookup"><span data-stu-id="a0fdd-162">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="a0fdd-163">**Jeder, der über den Link verfügt** – wählen Sie diese Option aus, wenn Sie eine Vielzahl von Dateien und Ordnern für anonyme Benutzer freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-163">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="a0fdd-164">Wenn Sie *jeder* Verknüpfung erlauben möchten, aber über die versehentliche anonyme Freigabe besorgt sind, sollten Sie eine der anderen Optionen als Standard verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-164">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="a0fdd-165">Dieser Linktyp ist nur verfügbar, wenn Sie die Freigabe von **Benutzern** aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-165">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="a0fdd-166">**Nur Personen in Ihrer Organisation** – wählen Sie diese Option aus, wenn Sie davon ausgehen, dass die meisten Datei-und Ordner Freigaben für Personen in Ihrer Organisation gelten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-166">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="a0fdd-167">**Bestimmte Personen** – diese Option wird empfohlen, wenn Sie eine Vielzahl von Datei-und Ordner Freigaben für Gäste erwarten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-167">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="a0fdd-168">Diese Art von Link funktioniert mit Gästen und erfordert die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-168">This type of link works with guests and requires them to authenticate.</span></span>
 
![Screenshot der SharePoint-Freigabeeinstellungen für Dateien und Ordner auf Organisationsebene](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="a0fdd-170">So legen Sie die Standard Link Einstellungen für die SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-170">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="a0fdd-171">Navigieren Sie im SharePoint Admin Center zur Seite Freigabe.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-171">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="a0fdd-172">Wählen Sie unter **Datei-und Ordner Links**den standardmäßigen Freigabe Link aus, den Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-172">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="a0fdd-173">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-173">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="a0fdd-174">Team erstellen</span><span class="sxs-lookup"><span data-stu-id="a0fdd-174">Create a team</span></span>

<span data-ttu-id="a0fdd-175">Der nächste Schritt besteht darin, das Team zu erstellen, das Sie für die Zusammenarbeit mit Gästen verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-175">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="a0fdd-176">So erstellen Sie ein Team</span><span class="sxs-lookup"><span data-stu-id="a0fdd-176">To create a team</span></span>
1. <span data-ttu-id="a0fdd-177">Klicken Sie in Microsoft Teams auf der Registerkarte **Teams** unten im linken Bereich auf **beitreten oder ein Team erstellen** .</span><span class="sxs-lookup"><span data-stu-id="a0fdd-177">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="a0fdd-178">Klicken Sie auf **Team erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-178">Click **Create a team**.</span></span>
3. <span data-ttu-id="a0fdd-179">Klicken Sie auf **ein Team von Grund auf neu erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-179">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="a0fdd-180">Wählen Sie **private** oder **Public**aus.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-180">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="a0fdd-181">Geben Sie einen Namen und eine Beschreibung für das Team ein, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-181">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="a0fdd-182">Klicken Sie auf **überspringen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-182">Click **Skip**.</span></span>

<span data-ttu-id="a0fdd-183">Wir laden Benutzer später ein.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-183">We'll invite users later.</span></span> <span data-ttu-id="a0fdd-184">Als nächstes ist es wichtig, die Freigabeeinstellungen auf Websiteebene für die SharePoint-Website zu überprüfen, die dem Team zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-184">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="a0fdd-185">Freigabeeinstellungen für SharePoint-Websiteebene</span><span class="sxs-lookup"><span data-stu-id="a0fdd-185">SharePoint site level sharing settings</span></span>

<span data-ttu-id="a0fdd-186">Überprüfen Sie die Freigabeeinstellungen auf Standortebene, um sicherzustellen, dass die gewünschten Zugriffstypen für dieses Team zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-186">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="a0fdd-187">Wenn Sie beispielsweise die Einstellungen auf Organisationsebene auf " **jeder**" festlegen, aber alle Gäste sich für dieses Team authentifizieren möchten, stellen Sie sicher, dass die Freigabeeinstellungen auf Standortebene auf " **neu" und "vorhandene Gäste**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-187">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Screenshot der externen Freigabeeinstellungen für SharePoint-Websites](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="a0fdd-189">So legen Sie Freigabeeinstellungen auf Websiteebene fest</span><span class="sxs-lookup"><span data-stu-id="a0fdd-189">To set site-level sharing settings</span></span>
1. <span data-ttu-id="a0fdd-190">Erweitern Sie im SharePoint Admin Center in der linken Navigationsleiste den Knoten **Websites** , und klicken Sie dann auf **aktive Standorte**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-190">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="a0fdd-191">Wählen Sie die Website für das Team aus, das Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-191">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="a0fdd-192">Klicken Sie im Menüband auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-192">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="a0fdd-193">Stellen Sie sicher, dass die Freigabe auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-193">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="a0fdd-194">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-194">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="a0fdd-195">Benutzer einladen</span><span class="sxs-lookup"><span data-stu-id="a0fdd-195">Invite users</span></span>

<span data-ttu-id="a0fdd-196">Die Einstellungen für die Gast Freigabe sind nun konfiguriert, sodass Sie mit dem Hinzufügen interner Benutzer und Gäste zu Ihrem Team beginnen können.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-196">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="a0fdd-197">So laden Sie interne Benutzer zu einem Team ein</span><span class="sxs-lookup"><span data-stu-id="a0fdd-197">To invite internal users to a team</span></span>
1. <span data-ttu-id="a0fdd-198">Klicken Sie im Team auf **Weitere Optionen** (**\*\***), und klicken Sie dann auf **Mitglied hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-198">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="a0fdd-199">Geben Sie den Namen der Person ein, die Sie einladen möchten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-199">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="a0fdd-200">Klicken Sie auf **Hinzufügen** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-200">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="a0fdd-201">So laden Sie Gäste zu einem Team ein</span><span class="sxs-lookup"><span data-stu-id="a0fdd-201">To invite guests to a team</span></span>
1. <span data-ttu-id="a0fdd-202">Klicken Sie im Team auf **Weitere Optionen** (**\*\***), und klicken Sie dann auf **Mitglied hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-202">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="a0fdd-203">Geben Sie die e-Mail-Adresse des Gasts ein, den Sie einladen möchten.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-203">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="a0fdd-204">Klicken Sie auf **Gäste Informationen bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-204">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="a0fdd-205">Geben Sie den vollständigen Namen des Gasts ein, und klicken Sie auf das Häkchen.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-205">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="a0fdd-206">Klicken Sie auf **Hinzufügen** und dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="a0fdd-206">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0fdd-207">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a0fdd-207">See Also</span></span>

