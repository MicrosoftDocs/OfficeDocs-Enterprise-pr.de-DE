---
title: "Bereitstellen von SharePoint Online-Websites für drei Ebenen des Schutzes"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Zusammenfassung: Erstellen und Konfigurieren von SharePoint Online Teamwebsites für verschiedene Ebenen der Schutz von Informationen."
ms.openlocfilehash: 4e6e70377f27bcd3cf367aefa1a640188abefc50
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="6c2e1-103">Bereitstellen von SharePoint Online-Websites für drei Ebenen des Schutzes</span><span class="sxs-lookup"><span data-stu-id="6c2e1-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="6c2e1-104">**Zusammenfassung:** Erstellen und Konfigurieren von SharePoint Online Teamwebsites für verschiedene Ebenen der Schutz von Informationen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="6c2e1-p101">Verwenden Sie die Schritte in diesem Artikel zum Entwerfen und Bereitstellen von Basisplan empfindlich und streng vertraulich SharePoint Online Teamwebsites. Weitere Informationen zu diesen drei Ebenen des Schutzes finden Sie unter [Secure SharePoint Online-Websites und Dateien](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="6c2e1-107">SharePoint Online-Teamwebsites mit Basisschutz</span><span class="sxs-lookup"><span data-stu-id="6c2e1-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="6c2e1-p102">Zum Basisschutz gehören sowohl öffentliche als auch private Teamwebsites. Öffentliche Teamwebsites können von allen Benutzern in einer Organisation ermittelt werden, und alle haben Zugriff darauf. Private Websites können nur von Mitgliedern der Office 365-Gruppe ermittelt werden, die der Teamwebsite zugeordnet ist, und nur sie haben Zugriff darauf. Bei diesen beiden Typen von Teamwebsites können Mitglieder die Website mit anderen Benutzern teilen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="6c2e1-112">Öffentlich</span><span class="sxs-lookup"><span data-stu-id="6c2e1-112">Public</span></span>

<span data-ttu-id="6c2e1-113">Um eine SharePoint Online-Teamwebsite mit Basisschutz für den öffentlichen Zugriff und Berechtigungen zu erstellen, gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="6c2e1-p103">Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6c2e1-116">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6c2e1-117">Klicken Sie in der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6c2e1-118">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6c2e1-119">Geben Sie in das Feld **Websitename**einen Namen für die öffentliche Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="6c2e1-120">Geben Sie im Feld **Team Site Beschreibung**eine Beschreibung des Zwecks der Website.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="6c2e1-121">Wählen Sie unter **Datenschutzeinstellungen** die Option **Öffentlich - Alle Benutzer in der Organisation können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6c2e1-122">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6c2e1-123">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-123">Here is your resulting configuration.</span></span>
  
![Grundschutz für eine öffentliche SharePoint Online-Teamwebsite.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="6c2e1-125">Privat</span><span class="sxs-lookup"><span data-stu-id="6c2e1-125">Private</span></span>

<span data-ttu-id="6c2e1-126">Um eine SharePoint Online-Teamwebsite mit Basisschutz für den privaten Zugriff und Berechtigungen zu erstellen, gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="6c2e1-p104">Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6c2e1-129">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6c2e1-130">Klicken Sie in der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6c2e1-131">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6c2e1-132">Geben Sie in das Feld **Websitename**einen Namen für die private Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="6c2e1-133">Geben Sie Team Site in **Beschreibung eine Beschreibung des Zwecks der Website.**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="6c2e1-134">Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6c2e1-135">Klicken Sie auf die **, die möchten Sie hinzufügen?** Bereich, geben Sie im Feld **Mitglieder hinzufügen**, die Namen der Benutzerkonten, die Zugriff auf diese privaten Teamwebsite haben.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="6c2e1-136">Wenn Sie fertig sind hinzufügen den ersten Satz von Elementen zu der Website, klicken Sie auf **Fertig stellen**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="6c2e1-137">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-137">Here is your resulting configuration.</span></span>
  
![Grundschutz für eine private SharePoint Online-Teamwebsite.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="6c2e1-139">Vertauliche SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="6c2e1-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="6c2e1-140">Eine vertrauliche SharePoint Online-Teamwebsite ist eine isolierte Teamwebsite. Das heißt, dass die Berechtigungen über die Mitgliedschaft in SharePoint-Gruppen statt der Mitgliedschaft in der Office 365-Gruppe, die der Teamwebsite zugeordnet ist, gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="6c2e1-141">Beim Erstellen einer isolierten Teamwebsite gibt es zwei Hauptschritte.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="6c2e1-142">Schritt 1: Entwerfen der isolierten Website</span><span class="sxs-lookup"><span data-stu-id="6c2e1-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="6c2e1-143">Um eine isolierte Teamwebsite entwerfen zu können, müssen Sie Folgendes ermitteln:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="6c2e1-144">Die SharePoint-Gruppen und Berechtigungsstufen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="6c2e1-145">Den Satz von Zugriffsgruppen, die Mitglieder der SharePoint-Gruppen sein sollen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="6c2e1-146">Der empfohlene Satz von Access Gruppen ist eine für Websitemitglieder, Website und Websiteadministratoren.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="6c2e1-147">Ob Sie verschachtelte Gruppen innerhalb der Zugriffsgruppe verwenden.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="6c2e1-148">Die empfohlene Gruppenstruktur und die Berechtigungsstufen sehen z. B. wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="6c2e1-149">**SharePoint-Gruppe**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-149">**SharePoint group**</span></span>|<span data-ttu-id="6c2e1-150">**Berechtigungsstufe**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-150">**Permission level**</span></span>|<span data-ttu-id="6c2e1-151">**Zugriffsgruppe (Beispiele)**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6c2e1-152">[Websitename] Elemente des Objekts</span><span class="sxs-lookup"><span data-stu-id="6c2e1-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="6c2e1-153">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="6c2e1-153">Edit</span></span>  <br/> |<span data-ttu-id="6c2e1-154">[Websitename] Elemente des Objekts</span><span class="sxs-lookup"><span data-stu-id="6c2e1-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="6c2e1-155">[Websitename] Besucher</span><span class="sxs-lookup"><span data-stu-id="6c2e1-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="6c2e1-156">Lesen</span><span class="sxs-lookup"><span data-stu-id="6c2e1-156">Read</span></span>  <br/> |<span data-ttu-id="6c2e1-157">[Websitename] Leser von Berichten</span><span class="sxs-lookup"><span data-stu-id="6c2e1-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="6c2e1-158">[Websitename] Besitzer</span><span class="sxs-lookup"><span data-stu-id="6c2e1-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="6c2e1-159">Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="6c2e1-159">Full control</span></span>  <br/> |<span data-ttu-id="6c2e1-160">[Websitename] Administratoren</span><span class="sxs-lookup"><span data-stu-id="6c2e1-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="6c2e1-p105">Die SharePoint-Gruppen und -Berechtigungsstufen werden standardmäßig für eine Teamwebsite erstellt. Sie müssen die Namen der Zugriffsgruppen ermitteln.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="6c2e1-163">Die Details zu den Entwurfsprozess finden Sie unter [Design einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="6c2e1-164">Schritt 2: Bereitstellen der isolierten Website</span><span class="sxs-lookup"><span data-stu-id="6c2e1-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="6c2e1-165">Um Ihre isolierte Website bereitzustellen, müssen Sie zuerst Folgendes durchführen:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="6c2e1-166">Ermitteln Sie die Benutzerkonten und Gruppen, die den einzelnen Zugriffsgruppen hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="6c2e1-167">Erstellen Sie die Zugriffsgruppen, und fügen Sie die Benutzer und Gruppenmitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="6c2e1-168">Die ausführliche Schritte finden Sie unter **Phase 1** des [Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="6c2e1-169">Erstellen Sie als Nächstes mit den folgenden Schritten die SharePoint Online-Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="6c2e1-p106">Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6c2e1-172">Klicken Sie in der Liste von Kacheln auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6c2e1-173">Klicken Sie auf der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6c2e1-174">Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6c2e1-175">Geben Sie in das Feld **Websitename**einen Namen für die private Teamwebsite.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="6c2e1-176">Geben Sie im Feld **Team Site Beschreibung**eine optionale Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="6c2e1-177">Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6c2e1-178">Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6c2e1-179">Konfigurieren Sie als Nächstes auf der neuen SharePoint Online-Teamwebsite die gewünschten Berechtigungen anhand der folgenden Schritte.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="6c2e1-p107">Ermitteln Sie den UPN (User Principal Name) des IT-Administrators oder der anderen Person, die für das Beantworten und Bearbeiten von Anfragen hinsichtlich des Zugriffs auf die Website zuständig ist (Beispiel für einen UPN: belindan@contoso.com). Notieren Sie den UPN hier: _________________________________________.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="6c2e1-182">Klicken Sie in der Symbolleiste auf das Symbol „Einstellungen" und anschließend auf **Websiteberechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="6c2e1-183">Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="6c2e1-184">Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="6c2e1-185">Klicken Sie im Dialogfeld **Einstellungen für die Anforderungen** :</span><span class="sxs-lookup"><span data-stu-id="6c2e1-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="6c2e1-186">Deaktivieren Sie das Kontrollkästchen **zulassen, dass Mitglieder der Website und einzelne Dateien und Ordner freigeben** und **zulassen, dass Mitglieder der Gruppe der Websitemitglieder an andere Benutzer dazu einladen** .</span><span class="sxs-lookup"><span data-stu-id="6c2e1-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="6c2e1-187">Geben Sie den UPN des IT-Administrator aus Schritt 1 in **Alle Anforderungen für den Zugriff zu senden**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="6c2e1-188">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="6c2e1-189">Klicken Sie auf der Registerkarte **Berechtigungen** des Browsers **[Websitename]-Elemente** in der Liste auf.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="6c2e1-190">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="6c2e1-191">Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Gruppe Ihrer Website Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="6c2e1-192">Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="6c2e1-193">Klicken Sie in der Liste **[Websitename] Besitzer** auf.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="6c2e1-194">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="6c2e1-195">Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Gruppe der Administratoren-Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="6c2e1-196">Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="6c2e1-197">Klicken Sie in der Liste auf **Besucher [Websitename]** .</span><span class="sxs-lookup"><span data-stu-id="6c2e1-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="6c2e1-198">Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="6c2e1-199">Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Websitegruppe Leser von Berichten Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="6c2e1-200">Schließen Sie die Registerkarte **Berechtigungen** Ihres Browsers.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="6c2e1-201">Die Ergebnisse dieser Berechtigungseinstellungen sehen folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="6c2e1-202">Die SharePoint-Gruppe **Besitzer [Websitename]** enthält die Gruppe der Administratoren Zugriff, in denen alle Mitglieder die Berechtigungsstufe **Vollzugriff** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-203">Die SharePoint-Gruppe **Mitglieder [Websitename]** enthält die Mitglieder Access Websitegruppe, in denen alle Mitglieder die Berechtigungsstufe **Bearbeiten** haben.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-204">Die SharePoint-Gruppe **Besucher [Websitename]** enthält die Websitegruppe Leser von Berichten Zugriff, in denen alle Mitglieder die Berechtigungsstufe **Lesen** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-205">Die Möglichkeit für den Mitgliedern der einzuladenden Mitglieder ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="6c2e1-206">Die Möglichkeit für Mitglieder auf Zugriff beantragen ist aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="6c2e1-207">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-207">Here is your resulting configuration.</span></span>
  
![Schutzebene „Vertraulich“ für eine isolierte SharePoint Online-Teamwebsite.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="6c2e1-209">Jetzt können die Mitglieder der Website über die Gruppenmitgliedschaft in einer der Zugriffsgruppen sicher zusammenarbeiten und die Ressourcen der Website nutzen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="6c2e1-210">Streng vertrauliche SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="6c2e1-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="6c2e1-211">Eine streng vertrauliche SharePoint Online-Teamwebsite ist eine isolierte Teamwebsite. Das heißt, dass die Berechtigungen über die Mitgliedschaft in SharePoint-Gruppen statt der Mitgliedschaft in der Office 365-Gruppe, die der Teamwebsite zugeordnet ist, gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="6c2e1-212">Das Erstellen einer isolierten Teamwebsite für streng vertrauliche Informationen und die Zusammenarbeit umfasst zwei Haupstschritte.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="6c2e1-213">Schritt 1: Entwerfen der isolierten Website</span><span class="sxs-lookup"><span data-stu-id="6c2e1-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="6c2e1-214">Um eine isolierte Teamwebsite entwerfen zu können, müssen Sie Folgendes ermitteln:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="6c2e1-215">Die SharePoint-Gruppen und Berechtigungsstufen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="6c2e1-216">Den Satz von Zugriffsgruppen, die Mitglieder der SharePoint-Gruppen sein sollen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="6c2e1-217">Der empfohlene Satz von Access Gruppen ist eine für Websitemitglieder, Website und Websiteadministratoren.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="6c2e1-218">Ob Sie verschachtelte Gruppen innerhalb der Zugriffsgruppe verwenden.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="6c2e1-219">Die empfohlene Gruppenstruktur und die Berechtigungsstufen sehen z. B. wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="6c2e1-220">**SharePoint-Gruppe**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-220">**SharePoint group**</span></span>|<span data-ttu-id="6c2e1-221">**Berechtigungsstufe**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-221">**Permission level**</span></span>|<span data-ttu-id="6c2e1-222">**Zugriffsgruppe (Beispiele)**</span><span class="sxs-lookup"><span data-stu-id="6c2e1-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6c2e1-223">[Websitename] Elemente des Objekts</span><span class="sxs-lookup"><span data-stu-id="6c2e1-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="6c2e1-224">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="6c2e1-224">Edit</span></span>  <br/> |<span data-ttu-id="6c2e1-225">[Websitename] Elemente des Objekts</span><span class="sxs-lookup"><span data-stu-id="6c2e1-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="6c2e1-226">[Websitename] Besucher</span><span class="sxs-lookup"><span data-stu-id="6c2e1-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="6c2e1-227">Lesen</span><span class="sxs-lookup"><span data-stu-id="6c2e1-227">Read</span></span>  <br/> |<span data-ttu-id="6c2e1-228">[Websitename] Leser von Berichten</span><span class="sxs-lookup"><span data-stu-id="6c2e1-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="6c2e1-229">[Websitename] Besitzer</span><span class="sxs-lookup"><span data-stu-id="6c2e1-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="6c2e1-230">Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="6c2e1-230">Full control</span></span>  <br/> |<span data-ttu-id="6c2e1-231">[Websitename] Administratoren</span><span class="sxs-lookup"><span data-stu-id="6c2e1-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="6c2e1-p108">Die SharePoint-Gruppen und -Berechtigungsstufen werden standardmäßig für eine Teamwebsite erstellt. Sie müssen die Namen der Zugriffsgruppen ermitteln.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="6c2e1-234">Die Details zu den Entwurfsprozess finden Sie unter [Design einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="6c2e1-235">Schritt 2: Bereitstellen der isolierten Website</span><span class="sxs-lookup"><span data-stu-id="6c2e1-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="6c2e1-236">Um Ihre isolierte Website bereitzustellen, müssen Sie zuerst Folgendes durchführen:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="6c2e1-237">Ermitteln Sie die Benutzer und Gruppenmitglieder der einzelnen Zugriffsgruppen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="6c2e1-238">Erstellen Sie die Zugriffsgruppen, und fügen Sie die Benutzer und Gruppenmitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="6c2e1-239">Erstellen Sie eine isolierte Teamwebsite, die Ihre Zugriffsgruppen verwendet.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="6c2e1-240">Die ausführliche Schritte finden Sie unter [Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e1-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="6c2e1-241">Nachfolgend sind die Ergebnisse dieser Berechtigungseinstellungen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="6c2e1-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="6c2e1-242">Die SharePoint-Gruppe **Besitzer [Websitename]** enthält die Gruppe der Administratoren Zugriff, in denen alle Mitglieder die Berechtigungsstufe **Vollzugriff** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-243">Die SharePoint-Gruppe **Mitglieder [Websitename]** enthält die Mitglieder Access Websitegruppe, in denen alle Mitglieder die Berechtigungsstufe **Bearbeiten** haben.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-244">Die SharePoint-Gruppe **Besucher [Websitename]** enthält die Websitegruppe Leser von Berichten Zugriff, in denen alle Mitglieder die Berechtigungsstufe **Lesen** verfügen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="6c2e1-245">Die Möglichkeit für den Mitgliedern der einzuladenden Mitglieder ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="6c2e1-246">Die Möglichkeit für Mitglieder auf Zugriff beantragen ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="6c2e1-247">Nachfolgend sehen Sie die daraus resultierende Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-247">Here is your resulting configuration.</span></span>
  
![Schutzebene „Streng vertraulich“ für eine isolierte SharePoint Online-Teamwebsite.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="6c2e1-249">Jetzt können die Mitglieder der Website über die Gruppenmitgliedschaft in einer der Zugriffsgruppen sicher zusammenarbeiten und die Ressourcen der Website nutzen.</span><span class="sxs-lookup"><span data-stu-id="6c2e1-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="6c2e1-250">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="6c2e1-250">Next step</span></span>

[<span data-ttu-id="6c2e1-251">Schützen von SharePoint Online-Dateien mit Office 365 Etiketten und DLP</span><span class="sxs-lookup"><span data-stu-id="6c2e1-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="6c2e1-252">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="6c2e1-252">See Also</span></span>

[<span data-ttu-id="6c2e1-253">Sichern von SharePoint Online-Websites und -Dateien</span><span class="sxs-lookup"><span data-stu-id="6c2e1-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6c2e1-254">Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="6c2e1-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6c2e1-255">Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen</span><span class="sxs-lookup"><span data-stu-id="6c2e1-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6c2e1-256">Cloudakzeptanz und Hybridlösungen</span><span class="sxs-lookup"><span data-stu-id="6c2e1-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




