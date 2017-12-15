---
title: "Erstellen von Teamwebsites in einer Entwicklungs-/Testumgebung für eine politische Kampagne"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Zusammenfassung: Erstellen Sie öffentliche, private, vertrauliche und streng vertraulich SharePoint Online Teamwebsites in Ihrer politischen Kampagne Test-/-Umgebung."
ms.openlocfilehash: 82e671af271508dfdecac6169a7892a8a12b7865
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="d294a-103">Erstellen von Teamwebsites in einer Entwicklungs-/Testumgebung für eine politische Kampagne</span><span class="sxs-lookup"><span data-stu-id="d294a-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="d294a-104">**Zusammenfassung:** Erstellen Sie in der Umgebung der politischen Kampagne Test-/öffentliche, private, vertrauliche und streng vertraulich SharePoint Online Teamwebsites.</span><span class="sxs-lookup"><span data-stu-id="d294a-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="d294a-p101">Verwenden Sie die Anweisungen in diesem Artikel eine Test-/Umgebung erstellen, die vier verschiedenen Typen von SharePoint Online Teamwebsites für die [Microsoft Security Guidance for politischen Kampagnen, gemeinnützige Organisationen, und andere Agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) enthält Lösung. Diese Websites werden auf Thema 10, mit dem Titel **SharePoint- und OneDrive für Unternehmen**ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d294a-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="d294a-107">Phase 1: Erstellen der Entwicklungs-/Testumgebung für eine politische Kampagne</span><span class="sxs-lookup"><span data-stu-id="d294a-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="d294a-108">Führen Sie zunächst die Anweisungen in [Configure Gruppen und Benutzer für eine politischen Kampagne Test-/Umgebung](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) zum Erstellen von Ihrer Abonnements, Benutzer und Gruppen.</span><span class="sxs-lookup"><span data-stu-id="d294a-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="d294a-109">Phase 2: Erstellen von Office 365-Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="d294a-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="d294a-110">In dieser Phase erstellen Sie die Beschriftungen für unterschiedlichen Sicherheitsebenen für SharePoint Online Team Websiteordner Dokument.</span><span class="sxs-lookup"><span data-stu-id="d294a-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="d294a-p102">Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Testabonnement beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d294a-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d294a-113">Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel **Admin**.</span><span class="sxs-lookup"><span data-stu-id="d294a-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="d294a-114">Klicken Sie auf der neuen Registerkarte **Office Admin Center** im Browser auf **Admin Center > Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="d294a-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="d294a-115">Klicken Sie auf der neuen Registerkarte **Start - Security &amp; Compliance** im Browser auf **Klassifizierungen > Bezeichnungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="d294a-116">Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnung erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="d294a-117">Klicken Sie im Bereich **Name die Bezeichnung** Geben Sie **Internal**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d294a-118">Klicken Sie im Bereich **Bezeichnungseinstellungen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-119">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnung erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="d294a-120">Wiederholen Sie die Schritte 5 bis 8 für diese zusätzlichen Bezeichnungen:</span><span class="sxs-lookup"><span data-stu-id="d294a-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="d294a-121">Privat</span><span class="sxs-lookup"><span data-stu-id="d294a-121">Private</span></span>
    
  - <span data-ttu-id="d294a-122">Vertraulich</span><span class="sxs-lookup"><span data-stu-id="d294a-122">Sensitive</span></span>
    
  - <span data-ttu-id="d294a-123">Streng vertraulich</span><span class="sxs-lookup"><span data-stu-id="d294a-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="d294a-124">Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnungen veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="d294a-125">Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Zu veröffentlichende Bezeichnungen wählen**</span><span class="sxs-lookup"><span data-stu-id="d294a-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="d294a-126">Klicken Sie im Bereich **Bezeichnungen wählen** auf **Hinzufügen**, und wählen Sie alle vier Bezeichnungen aus.</span><span class="sxs-lookup"><span data-stu-id="d294a-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="d294a-127">Klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="d294a-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="d294a-128">Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="d294a-129">Klicken Sie im Bereich **Speicherorte auswählen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="d294a-130">Klicken Sie im Bereich **Name der Richtlinie** geben **Kampagne** im **Feld Name**ein, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="d294a-131">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnungen veröffentlichen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="d294a-132">Phase 3: Erstellen von SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="d294a-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="d294a-133">In dieser Phase werden SharePoint Online-Teamwebsites für Ihre politische Kampagne entsprechend den vier Typen von SharePoint Online-Teamwebsites erstellt und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="d294a-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="d294a-134">Kampagnen-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="d294a-134">Campaign wide team site</span></span>

<span data-ttu-id="d294a-135">Führen Sie folgende Schritte aus, um eine öffentliche SharePoint Online-Basis-Teamwebsite zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d294a-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="d294a-136">Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).</span><span class="sxs-lookup"><span data-stu-id="d294a-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d294a-137">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d294a-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d294a-138">Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d294a-139">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="d294a-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d294a-140">Geben Sie in das Feld **Websitename** **Kampagne breit**.</span><span class="sxs-lookup"><span data-stu-id="d294a-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="d294a-141">Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für die gesamte Kampagne**.</span><span class="sxs-lookup"><span data-stu-id="d294a-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="d294a-142">Wählen Sie unter **Datenschutzeinstellungen** die Option **Öffentlich - Alle Benutzer in der Organisation können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-143">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d294a-144">Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnen-Teamwebsite für die Bezeichnung „Intern“.</span><span class="sxs-lookup"><span data-stu-id="d294a-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="d294a-145">Klicken Sie auf der Registerkarte **Kampagne Wide-Home** Ihres Browsers auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="d294a-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d294a-146">Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d294a-147">Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.</span><span class="sxs-lookup"><span data-stu-id="d294a-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d294a-148">Wählen Sie **intern**im Feld **Bezeichnung Einstellungen anwenden**, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="d294a-149">Teamwebsite für Kampagnenprojekt 1</span><span class="sxs-lookup"><span data-stu-id="d294a-149">Campaign project 1 team site</span></span>

<span data-ttu-id="d294a-150">Führen Sie die folgenden Schritte durch, um eine private SharePoint Online-Basis-Teamwebsite für ein Projekt innerhalb der Kampagne zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d294a-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="d294a-151">Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).</span><span class="sxs-lookup"><span data-stu-id="d294a-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d294a-152">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d294a-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d294a-153">Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d294a-154">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="d294a-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d294a-155">Geben Sie in das Feld **Websitename** **Kampagne Projekt 1**.</span><span class="sxs-lookup"><span data-stu-id="d294a-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="d294a-156">Geben Sie im Feld **Team Site Beschreibung** **SharePoint-Website für Kampagne Projekt 1**.</span><span class="sxs-lookup"><span data-stu-id="d294a-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="d294a-157">Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-158">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d294a-159">Konfigurieren Sie anschließend den Ordner „Dokumente“ der Teamwebsite für Kampagnenprojekt 1 für die Bezeichnung „Privat“.</span><span class="sxs-lookup"><span data-stu-id="d294a-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="d294a-160">Klicken Sie auf der Registerkarte **Project-1-Startseite Kampagne** Ihres Browsers auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="d294a-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d294a-161">Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d294a-162">Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.</span><span class="sxs-lookup"><span data-stu-id="d294a-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d294a-163">Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Privat**, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="d294a-164">Kampagnenmarketing-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="d294a-164">Campaign marketing team site</span></span>

<span data-ttu-id="d294a-165">Führen Sie die folgenden Schritte durch, um eine isolierte, vertrauliche SharePoint-Teamwebsite für Kampagnenmarketingressourcen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d294a-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="d294a-166">Melden Sie sich mit einem Browser auf dem lokalen Computer an, in das globale Administratorkonto mit Office 365-Portal ([https://portal.office.com](https://portal.office.com)).</span><span class="sxs-lookup"><span data-stu-id="d294a-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d294a-167">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d294a-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d294a-168">Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d294a-169">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="d294a-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d294a-170">Geben Sie in das Feld **Teamname Website** **Kampagne Marketing**.</span><span class="sxs-lookup"><span data-stu-id="d294a-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="d294a-171">Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für Kampagne marketing (/ Kleinschreibung beachten)**.</span><span class="sxs-lookup"><span data-stu-id="d294a-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="d294a-172">Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-173">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d294a-174">Klicken Sie auf das einstellungssymbol auf der neuen Registerkarte **Kampagne Marketing** in Ihrem Browser in der Symbolleiste, und klicken Sie dann auf **Websiteberechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d294a-175">Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d294a-176">Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d294a-177">Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Kontrollkästchen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben**, geben Sie **ITAdmin1@**<your organization name> **.onmicrosoft.com** unter **Alle Zugriffsanforderungen an die folgende E-Mail-Adresse senden:**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="d294a-178">Klicken Sie in der Liste **Mitglieder marketing-Kampagnen** auf.</span><span class="sxs-lookup"><span data-stu-id="d294a-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="d294a-179">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d294a-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d294a-180">Klicken Sie im Dialogfeld **Freigeben** Geben Sie, **Senior und strategische Personal**, wählen Sie sie aus und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="d294a-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d294a-181">Wiederholen Sie die Schritte 14 und 15 für die Gruppe **Analytics Personal** und das Benutzerkonto **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="d294a-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="d294a-182">Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="d294a-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="d294a-183">Klicken Sie in der Liste auf **Besitzer marketing-Kampagnen** .</span><span class="sxs-lookup"><span data-stu-id="d294a-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="d294a-184">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d294a-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="d294a-185">Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="d294a-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="d294a-186">Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="d294a-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="d294a-187">Schließen Sie die Registerkarte **Personen und Gruppen** in Ihrem Browser, klicken Sie auf der Registerkarte **Kampagne Marketing-Startseite** in Ihrem Browser, und schließen Sie den Bereich für die **Projektwebsite-Berechtigungen** .</span><span class="sxs-lookup"><span data-stu-id="d294a-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d294a-188">Ergebnisse der Konfiguration von Berechtigungen:</span><span class="sxs-lookup"><span data-stu-id="d294a-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d294a-189">Die Kampagne Marketing - SharePoint-Gruppe **Mitglieder** enthält nur die **Senior und strategische Mitarbeiter** Gruppe (die Benutzerkonten Candidate, ChiefOfStaff und Strategic1 enthält), die **Kampagne** Marketinggruppe (: Dieser Abschnitt enthält die Globaler Administratorbenutzerkonto), der Gruppe der **Analytics Staff** (der das Benutzerkonto DataScientist1 enthält), und das Benutzerkonto **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="d294a-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="d294a-190">SharePoint-Gruppe der **Kampagne Marketing-Besitzer** enthält nur die **IT-Mitarbeiter** -Gruppe (die nur die Benutzerkonten ITAdmin1 und ITAdmin2 enthält).</span><span class="sxs-lookup"><span data-stu-id="d294a-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d294a-191">SharePoint-Gruppe der **Kampagne Marketing-Besucher** enthält keine Gruppen oder Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="d294a-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d294a-192">Mitglieder können nicht auf Standortebene Berechtigungen ändern (Dies kann nur durch ein Mitglied der Gruppe der **Kampagne Marketing-Besitzer** erfolgen).</span><span class="sxs-lookup"><span data-stu-id="d294a-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="d294a-193">Andere Benutzerkonten können nicht auf die Website oder die zugehörigen Ressourcen zugreifen, Sie können jedoch Zugriff auf die Website anfordern. Dabei wird eine E-Mail an das Postfach des ITAdmin1-Benutzerkontos gesendet.</span><span class="sxs-lookup"><span data-stu-id="d294a-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="d294a-194">Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnenmarketing-Teamwebsite für die Bezeichnung „Vertraulich“.</span><span class="sxs-lookup"><span data-stu-id="d294a-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="d294a-195">Klicken Sie in der Registerkarte **Kampagne Marketing-Start** des Browsers auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="d294a-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d294a-196">Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d294a-197">Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.</span><span class="sxs-lookup"><span data-stu-id="d294a-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d294a-198">Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Vertraulich**, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="d294a-p103">Konfigurieren Sie anschließend eine Data Loss Prevention (DLP) Richtlinie, die Benutzer mitgeteilt wird, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung vertrauliche außerhalb der Organisation freigeben. In diesem DLP-Richtlinie gilt für Ressourcen in der Kampagne marketing-Website.</span><span class="sxs-lookup"><span data-stu-id="d294a-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="d294a-201">Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="d294a-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="d294a-202">Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.</span><span class="sxs-lookup"><span data-stu-id="d294a-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="d294a-203">Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="d294a-204">Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d294a-205">Geben Sie im Bereich **Ihre Richtlinie benennen** den Namen **Bezeichnung „Vertraulich" - SharePoint Online-Teamwebsites** bei **Name** ein, und klicken Sie dann auf **Weiter**</span><span class="sxs-lookup"><span data-stu-id="d294a-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d294a-206">Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d294a-207">Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-208">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="d294a-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="d294a-209">In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.</span><span class="sxs-lookup"><span data-stu-id="d294a-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="d294a-210">Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="d294a-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="d294a-211">Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="d294a-212">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="d294a-213">Klicken Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** auf **Richtlinientipptext anpassen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="d294a-214">Klicken Sie im Fenster **Richtlinientipps und E-Mail-Benachrichtigungen anpassen** auf **Richtlinientipptext anpassen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="d294a-215">Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:</span><span class="sxs-lookup"><span data-stu-id="d294a-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d294a-p104">Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei" > „Dokument schützen" > „Mit Kennwort verschlüsseln", und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.</span><span class="sxs-lookup"><span data-stu-id="d294a-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="d294a-219">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="d294a-220">Deaktivieren Sie im Fenster **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** das Kontrollkästchen **Freigeben blockieren und Zugriff auf freigegebene Inhalte einschränken**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="d294a-221">Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d294a-222">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="d294a-223">Teamwebsite für Kampagnenstrategie</span><span class="sxs-lookup"><span data-stu-id="d294a-223">Campaign strategy team site</span></span>

<span data-ttu-id="d294a-224">Führen Sie die folgenden Schritte durch, um eine isolierte, streng vertrauliche SharePoint Online-Teamwebsite für Kampagnenstrategieressourcen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d294a-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="d294a-225">Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).</span><span class="sxs-lookup"><span data-stu-id="d294a-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d294a-226">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="d294a-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d294a-227">Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d294a-228">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="d294a-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d294a-229">Geben Sie in das Feld **Teamname für die Website** **Kampagne Strategie**.</span><span class="sxs-lookup"><span data-stu-id="d294a-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="d294a-230">Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für Kampagne Strategie (streng vertraulich)**.</span><span class="sxs-lookup"><span data-stu-id="d294a-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="d294a-231">Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-232">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d294a-233">Klicken Sie auf das einstellungssymbol auf der neuen Registerkarte **Kampagne Strategie** in Ihrem Browser in der Symbolleiste, und klicken Sie dann auf **Websiteberechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d294a-234">Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d294a-235">Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d294a-236">Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Optionen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben** (sodass alle drei Kontrollkästchen deaktiviert sind), und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="d294a-237">Klicken Sie auf **Kampagne Strategie für die Elemente** in der Liste.</span><span class="sxs-lookup"><span data-stu-id="d294a-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="d294a-238">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d294a-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d294a-239">Klicken Sie im Dialogfeld **Freigeben** Geben Sie, **Senior und strategische Personal**, wählen Sie sie aus und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="d294a-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d294a-240">Klicken Sie in der Liste auf **Kampagne Strategie Besitzer** .</span><span class="sxs-lookup"><span data-stu-id="d294a-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="d294a-241">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d294a-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="d294a-242">Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="d294a-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="d294a-243">Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="d294a-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="d294a-244">Schließen Sie die Registerkarte **Personen und Gruppen** in Ihrem Browser, klicken Sie auf der Registerkarte **Kampagne Strategie-Startseite** in Ihrem Browser, und schließen Sie den Bereich für die **Projektwebsite-Berechtigungen** .</span><span class="sxs-lookup"><span data-stu-id="d294a-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d294a-245">Ergebnisse der Konfiguration von Berechtigungen:</span><span class="sxs-lookup"><span data-stu-id="d294a-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d294a-246">Die Kampagne Strategie - SharePoint-Gruppe **Mitglieder** enthält nur die **Senior und strategische Mitarbeiter** Gruppe (die nur die Benutzerkonten Candidate, ChiefOfStaff und Strategic1 enthält) und der **Kampagne Strategie** -Gruppe (die enthält nur der globale Administrator-Benutzerkonto).</span><span class="sxs-lookup"><span data-stu-id="d294a-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="d294a-247">SharePoint-Gruppe der **Kampagne Strategie-Besitzer** enthält nur die **IT-Mitarbeiter** -Gruppe (die nur die Benutzerkonten ITAdmin1 und ITAdmin2 enthält).</span><span class="sxs-lookup"><span data-stu-id="d294a-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d294a-248">SharePoint-Gruppe der **Kampagne Strategie-Besucher** enthält keine Gruppen oder Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="d294a-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d294a-249">Mitglieder können nicht auf Standortebene Berechtigungen ändern (Dies kann nur durch ein Mitglied der Gruppe der **Kampagne Strategie-Besitzer** erfolgen).</span><span class="sxs-lookup"><span data-stu-id="d294a-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="d294a-p105">Andere Benutzerkonten nicht Zugriff auf die Website oder seiner Ressourcen oder Zugriff auf die Website anfordern. Zusätzliche Berechtigungen für die Website müssen der globale Administrator oder ein Mitglied der Gruppe der **Kampagne Strategie-Besitzer** erfolgen.</span><span class="sxs-lookup"><span data-stu-id="d294a-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="d294a-252">Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnenstrategie-Teamwebsite für die Bezeichnung „Streng vertraulich“.</span><span class="sxs-lookup"><span data-stu-id="d294a-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="d294a-253">Klicken Sie auf der Registerkarte **Kampagne Strategie für die Startseite** des Browsers auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="d294a-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d294a-254">Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d294a-255">Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.</span><span class="sxs-lookup"><span data-stu-id="d294a-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d294a-256">Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Streng vertraulich**, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="d294a-p106">Im nächsten Schritt Konfigurieren einer DLP-Richtlinie, Blöcke der Benutzer, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung streng vertraulich außerhalb der Organisation freigeben. In diesem DLP-Richtlinie gilt für Ressourcen in der Kampagne Strategie für die Website.</span><span class="sxs-lookup"><span data-stu-id="d294a-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="d294a-259">Bei Bedarf, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit einem Konto an, die die Rolle Sicherheitsadministrator oder Unternehmensadministrator hat.</span><span class="sxs-lookup"><span data-stu-id="d294a-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="d294a-260">Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="d294a-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="d294a-261">Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.</span><span class="sxs-lookup"><span data-stu-id="d294a-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="d294a-262">Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="d294a-263">Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d294a-264">Geben Sie im Bereich **Ihre Richtlinie benennen** den Namen **Bezeichnung „Streng vertraulich" - SharePoint Online-Teamwebsites** bei **Name** ein, und klicken Sie dann auf **Weiter**</span><span class="sxs-lookup"><span data-stu-id="d294a-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d294a-265">Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d294a-266">Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d294a-267">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="d294a-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="d294a-268">In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.</span><span class="sxs-lookup"><span data-stu-id="d294a-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="d294a-269">Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Streng vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="d294a-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="d294a-270">Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="d294a-271">Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="d294a-272">Klicken Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** auf **Richtlinientipptext anpassen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="d294a-273">Klicken Sie im Fenster **Richtlinientipps und E-Mail-Benachrichtigungen anpassen** auf **Richtlinientipptext anpassen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="d294a-274">Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:</span><span class="sxs-lookup"><span data-stu-id="d294a-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d294a-p107">Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei" > „Dokument schützen" > „Mit Kennwort verschlüsseln", und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.</span><span class="sxs-lookup"><span data-stu-id="d294a-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="d294a-278">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="d294a-279">Wählen Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** die Option **Begründung für Außerkraftsetzung erforderlich**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d294a-280">Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="d294a-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="d294a-281">Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d294a-282">Verwenden Sie die Anweisungen in [Azure-RMS mit Office 365 Administrationscenter aktivieren](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="d294a-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="d294a-283">Konfigurieren Sie als Nächstes Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung für Schutz und Berechtigungen, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d294a-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="d294a-p108">Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="d294a-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d294a-286">Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d294a-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="d294a-287">Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="d294a-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="d294a-288">Klicken Sie im Listenbereich auf **Weitere Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="d294a-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="d294a-289">Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="d294a-290">Geben Sie **CampaignStrategy** **Richtliniennamen** und die **Beschriftung für Dokumente in der Kampagne Strategie für die SharePoint-Teamwebsite** im Feld **Beschreibung**ein.</span><span class="sxs-lookup"><span data-stu-id="d294a-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="d294a-291">Klicken Sie auf **auswählen, welche Benutzer oder Gruppen diese Richtlinie erhalten > Benutzer/Gruppen**, und wählen Sie dann **Senior und strategische Personal**.</span><span class="sxs-lookup"><span data-stu-id="d294a-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="d294a-292">Klicken Sie auf **Auswählen > OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="d294a-293">Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="d294a-294">Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.</span><span class="sxs-lookup"><span data-stu-id="d294a-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="d294a-295">Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="d294a-296">Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.</span><span class="sxs-lookup"><span data-stu-id="d294a-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="d294a-297">Klicken Sie auf dem Blatt **Schutz** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="d294a-298">Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="d294a-299">Klicken Sie im Bereich **AAD Benutzer und Gruppen** wählen Sie aus, **Senior und strategische Mitarbeiter**, und klicken Sie dann auf **auswählen**.</span><span class="sxs-lookup"><span data-stu-id="d294a-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="d294a-300">Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.</span><span class="sxs-lookup"><span data-stu-id="d294a-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="d294a-301">Klicken Sie zweimal auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d294a-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="d294a-302">Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="d294a-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="d294a-303">Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="d294a-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="d294a-304">Klicken Sie auf dem Blatt **Azure Information Protection - Bereichsbezogene Richtlinien** auf **Veröffentlichen** und dann auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="d294a-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="d294a-305">Sie können jetzt mit dem Erstellen von Dokumenten in diesen vier Websites beginnen und den Zugriff mit verschiedenen Benutzerkonten in Ihrem Testabonnement testen.</span><span class="sxs-lookup"><span data-stu-id="d294a-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="d294a-306">Um ein Dokument mit Azure Information Protection und dieser neuen Bezeichnung zu schützen, müssen Sie auf einem Testcomputer [Installieren Sie den Client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) , Installieren von Office über das Office 365-Portal und melden Sie sich von Microsoft Word mit einem Konto in der ** Senior und strategische Mitarbeiter** Gruppe von Test-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="d294a-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d294a-307">See Also</span><span class="sxs-lookup"><span data-stu-id="d294a-307">See Also</span></span>

[<span data-ttu-id="d294a-308">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="d294a-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d294a-309">Konfigurieren von Gruppen und Benutzer für eine politischen Kampagne Test-/-Umgebung</span><span class="sxs-lookup"><span data-stu-id="d294a-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="d294a-310">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="d294a-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d294a-311">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="d294a-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




