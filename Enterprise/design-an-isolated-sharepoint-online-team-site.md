---
title: Entwerfen einer isolierten SharePoint Online-Teamwebsite
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "Zusammenfassung: Schritt über den Entwurfsprozess für SharePoint Online Teamwebsites isoliert."
ms.openlocfilehash: 7b2e8f0bc06a7901c52187ec6e63a056a11fa5e1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="7414c-103">Entwerfen einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="7414c-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="7414c-104">**Zusammenfassung:** Führen Sie durch den Entwurfsprozess für SharePoint Online Teamwebsites isoliert.</span><span class="sxs-lookup"><span data-stu-id="7414c-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="7414c-105">In diesem Artikel werden die wichtigsten Entwurfsentscheidungen erläutert, die Sie vor der Erstellung einer isolierten SharePoint Online-Teamwebsite treffen müssen.</span><span class="sxs-lookup"><span data-stu-id="7414c-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="7414c-106">Phase 1: Ermitteln der SharePoint-Gruppen und Berechtigungsstufen</span><span class="sxs-lookup"><span data-stu-id="7414c-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="7414c-107">Jede SharePoint Online-Teamwebsite wird standardmäßig mit den folgenden SharePoint-Gruppen erstellt:</span><span class="sxs-lookup"><span data-stu-id="7414c-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="7414c-108">\<Websitename > Mitglieder</span><span class="sxs-lookup"><span data-stu-id="7414c-108">\<site name> Members</span></span>
    
- <span data-ttu-id="7414c-109">\<Websitename > Besucher</span><span class="sxs-lookup"><span data-stu-id="7414c-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="7414c-110">\<Websitename > Besitzer</span><span class="sxs-lookup"><span data-stu-id="7414c-110">\<site name> Owners</span></span>
    
<span data-ttu-id="7414c-111">Diese Gruppen unterscheiden sich von Office 365- und Azure Active Directory (AD)-Gruppen und bilden die Grundlage zum Zuweisen von Berechtigungen für die Ressourcen der Website.</span><span class="sxs-lookup"><span data-stu-id="7414c-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="7414c-p101">Der Satz von spezifischen Berechtigungen, der bestimmt, welche Aktionen ein Mitglied einer SharePoint-Gruppe auf einer Website ausführen kann, ist eine Berechtigungsstufe. Für eine SharePoint Online-Teamwebsite gibt es standardmäßig drei Berechtigungsstufen: Bearbeitungszugriff, Lesezugriff und Vollzugriff. In der folgenden Tabelle ist die standardmäßige Korrelation von SharePoint-Gruppen und zugewiesenen Berechtigungsstufen dargestellt:</span><span class="sxs-lookup"><span data-stu-id="7414c-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="7414c-115">**SharePoint-Gruppe**</span><span class="sxs-lookup"><span data-stu-id="7414c-115">**SharePoint group**</span></span>|<span data-ttu-id="7414c-116">**Berechtigungsstufe**</span><span class="sxs-lookup"><span data-stu-id="7414c-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7414c-117">\<Websitename > Mitglieder</span><span class="sxs-lookup"><span data-stu-id="7414c-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="7414c-118">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="7414c-118">Edit</span></span>  <br/> |
|<span data-ttu-id="7414c-119">\<Websitename > Besucher</span><span class="sxs-lookup"><span data-stu-id="7414c-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="7414c-120">Lesen</span><span class="sxs-lookup"><span data-stu-id="7414c-120">Read</span></span>  <br/> |
|<span data-ttu-id="7414c-121">\<Websitename > Besitzer</span><span class="sxs-lookup"><span data-stu-id="7414c-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="7414c-122">Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="7414c-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="7414c-p102">**Bewährte Methode:** Sie können zusätzliche SharePoint-Gruppen und Berechtigungsstufen erstellen. Wir empfehlen jedoch mit dem SharePoint-Standardgruppen und Berechtigungsstufen für Ihre isolierten SharePoint Online-Website.</span><span class="sxs-lookup"><span data-stu-id="7414c-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="7414c-125">Hier sind die SharePoint-Gruppen und Berechtigungsstufen.</span><span class="sxs-lookup"><span data-stu-id="7414c-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![Die standardmäßigen SharePoint-Gruppen und -Berechtigungsstufen für eine SharePoint Online-Website.](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="7414c-127">Phase 2: Zuweisen von Berechtigungen zu Benutzern mit Zugriffsgruppen</span><span class="sxs-lookup"><span data-stu-id="7414c-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="7414c-p103">Sie können Benutzern Berechtigungen zuweisen, indem Sie ihr Benutzerkonto oder eine Office 365- oder Azure AD-Gruppe, in der das Benutzerkonto Mitglied ist, zu den SharePoint-Gruppen hinzufügen. Nach dem Hinzufügen wird den Office 365-Benutzerkonten entweder direkt oder indirekt über die Mitgliedschaft in einer Office 365- oder Azure AD-Gruppe die Berechtigungsstufe zugewiesen, die der SharePoint-Gruppe zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="7414c-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="7414c-130">Am Beispiel der SharePoint-Standardgruppen bedeutet dies:</span><span class="sxs-lookup"><span data-stu-id="7414c-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="7414c-131">Mitglieder der ** \<Websitename > Mitglieder** SharePoint-Gruppe, die Benutzerkonten und Gruppen enthalten können, sind **die Berechtigungsstufen** zugewiesen</span><span class="sxs-lookup"><span data-stu-id="7414c-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="7414c-132">Mitglieder der ** \<Websitename > Besucher** SharePoint-Gruppe, die Benutzerkonten und Gruppen enthalten können, werden die Berechtigungsstufe **Lesen** zugewiesen</span><span class="sxs-lookup"><span data-stu-id="7414c-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="7414c-133">Mitglieder der ** \<Websitename > Besitzer** SharePoint-Gruppe, die Benutzerkonten und Gruppen enthalten können, werden die Berechtigungsstufe **Vollzugriff** zugewiesen</span><span class="sxs-lookup"><span data-stu-id="7414c-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="7414c-p104">**Bewährte Methode:** Obwohl Sie Berechtigungen über die einzelnen Benutzerkonten verwalten können, es wird empfohlen, dass Sie ein einzelnes verwenden Azure Active Directory-Gruppe, stattdessen als eine Zugriffsgruppe bezeichnet. Dies vereinfacht die Verwaltung von Berechtigungen über die Mitgliedschaft in der Zugriffsgruppe statt Verwalten der Liste der Benutzer von für jede SharePoint-Gruppe Konten.</span><span class="sxs-lookup"><span data-stu-id="7414c-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="7414c-p105">Azure Active Directory-Gruppen für Office 365 unterscheiden sich von Office 365-Gruppen. Azure Active Directory-Gruppen werden in der Office-Verwaltungskonsole mit ihren **Typ** zu **Sicherheit** und keine e-Mail-Adresse. Azure Active Directory-Gruppen verwaltet werden können:</span><span class="sxs-lookup"><span data-stu-id="7414c-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="7414c-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="7414c-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="7414c-p106">Dies sind Gruppen, die in Ihrer lokalen Windows Azure AD-Infrastruktur erstellt und mit Office 365-Abonnement synchronisiert wurden. In der Office-Verwaltungskonsole haben diese Gruppen **Status** **Synched mit active Directory**.</span><span class="sxs-lookup"><span data-stu-id="7414c-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="7414c-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="7414c-142">Office 365</span></span>
    
    <span data-ttu-id="7414c-p107">Dies sind Gruppen, die mit der Office-Verwaltungskonsole, der Azure-Portal oder Microsoft PowerShell erstellt wurden. In der Office-Verwaltungskonsole haben diese Gruppen **Status** **Cloud**.</span><span class="sxs-lookup"><span data-stu-id="7414c-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="7414c-145">**Bewährte Methode:** Wenn Sie mithilfe von Windows Server AD lokal und Synchronisierung mit Office 365-Abonnements, führen Sie die gruppenverwaltung von Benutzern und mit Windows Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7414c-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="7414c-146">Für isolierte SharePoint Online-Teamwebsites sieht die empfohlene Gruppenstruktur wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7414c-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="7414c-147">**SharePoint-Gruppe**</span><span class="sxs-lookup"><span data-stu-id="7414c-147">**SharePoint group**</span></span>|<span data-ttu-id="7414c-148">**Azure AD-basierte Zugriffsgruppe**</span><span class="sxs-lookup"><span data-stu-id="7414c-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="7414c-149">**Berechtigungsstufe**</span><span class="sxs-lookup"><span data-stu-id="7414c-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7414c-150">\<Websitename > Mitglieder</span><span class="sxs-lookup"><span data-stu-id="7414c-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="7414c-151">\<Websitename > Mitglieder</span><span class="sxs-lookup"><span data-stu-id="7414c-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="7414c-152">Bearbeiten</span><span class="sxs-lookup"><span data-stu-id="7414c-152">Edit</span></span>  <br/> |
|<span data-ttu-id="7414c-153">\<Websitename > Besucher</span><span class="sxs-lookup"><span data-stu-id="7414c-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="7414c-154">\<Websitename > Leser von Berichten</span><span class="sxs-lookup"><span data-stu-id="7414c-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="7414c-155">Lesen</span><span class="sxs-lookup"><span data-stu-id="7414c-155">Read</span></span>  <br/> |
|<span data-ttu-id="7414c-156">\<Websitename > Besitzer</span><span class="sxs-lookup"><span data-stu-id="7414c-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="7414c-157">\<Websitename > Admins</span><span class="sxs-lookup"><span data-stu-id="7414c-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="7414c-158">Vollzugriff</span><span class="sxs-lookup"><span data-stu-id="7414c-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="7414c-p108">**Bewährte Methode:** Obwohl Sie Office 365 oder Azure Active Directory-Gruppen als Mitglieder der SharePoint-Gruppen verwenden können, wird empfohlen, Azure AD-Gruppen zu verwenden. Azure AD-Gruppen, verwaltete entweder über Windows Azure AD oder Office 365, bieten Ihnen mehr Flexibilität, geschachtelte Gruppen verwenden, um Berechtigungen zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="7414c-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="7414c-161">Hier sind die standardmäßige SharePoint-Gruppen für die Verwendung von Azure AD-based Access Gruppen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="7414c-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![Verwenden von Access Gruppen als Mitglieder von Standardgruppen SharePoint Online-Website.](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="7414c-163">Beachten Sie beim Entwerfen der drei Zugriffsgruppen die folgenden Punkte:</span><span class="sxs-lookup"><span data-stu-id="7414c-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="7414c-164">Sollte nur einige Elemente in der ** \<Websitename > Admins** Zugriffsgruppe, für eine kleine Anzahl von SharePoint Online-Administratoren, die Teamwebsite verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="7414c-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="7414c-p109">Die meisten der Websitemitglieder einer sind der ** \<Websitename > Mitglieder** oder ** \<Websitename > Viewer** Zugriff auf Gruppen. Da Websitemitglieder in der ** \<Websitename > Mitglieder** Zugriffsgruppe haben die Möglichkeit, löschen oder Ändern von Ressourcen in der Website, überlegen Sie sich die Mitgliedschaft. Wenn in unsicheren, das Websitemitglied hinzufügen die ** \<Websitename > Viewer** Zugriffsgruppe.</span><span class="sxs-lookup"><span data-stu-id="7414c-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="7414c-168">Hier ist ein Beispiel für die SharePoint-Gruppen und Access-Gruppen für eine isolierte Website mit dem Namen ProjektX.</span><span class="sxs-lookup"><span data-stu-id="7414c-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![Ein Beispiel für die Verwendung von Zugriffsgruppen für eine SharePoint Online-Website mit dem Namen „ProjectX“.](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="7414c-170">Phase 3: Verwenden von geschachtelten Azure AD-Gruppen</span><span class="sxs-lookup"><span data-stu-id="7414c-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="7414c-p110">Für ein Projekt, das auf eine kleine Anzahl von Personen beschränkt ist, ist es in den meisten Fällen ausreichend, den SharePoint-Gruppen der Website eine einzelne Ebene von Azure AD-basierten Zugriffsgruppen hinzuzufügen. Wenn jedoch eine große Anzahl von Personen vorhanden ist und diese Personen bereits Mitglied in bestehenden Azure AD-Gruppen sind, können Sie SharePoint-Berechtigungen einfacher mithilfe geschachtelter Gruppen zuweisen, d. h. Gruppen, die andere Gruppen als Mitglieder enthalten.</span><span class="sxs-lookup"><span data-stu-id="7414c-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="7414c-p111">Beispiel: Sie möchten eine isolierte SharePoint Online-Teamwebsite für die Zusammenarbeit zwischen den Leitern der Abteilungen Vertrieb, Marketing, Technik, Recht und Support erstellen, und diese Abteilungen haben bereits eigene Gruppen mit Benutzerkonten der Führungskräfte als Mitgliedern. Anstatt eine neue Gruppe für die neuen Websitemitglieder zu erstellen und alle einzelnen Benutzerkonten der Führungskräfte hinzuzufügen, fügen Sie die vorhandenen Führungskräftegruppen für die einzelnen Abteilung zur neuen Gruppe hinzu.</span><span class="sxs-lookup"><span data-stu-id="7414c-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="7414c-p112"> Wenn ein Office 365-Abonnement von mehreren Organisationen gemeinsam genutzt wird, kann eine einzelne Gruppenmitgliedschaftsebene für eine isolierte Website für eine Organisation aufgrund der schieren Anzahl von Benutzerkonten schwierig zu verwalten sein. In diesem Fall können Sie zum Verwalten der Berechtigungen geschachtelte Azure AD-Gruppen für jede Organisation verwenden, die die Gruppen innerhalb der Organisationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="7414c-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="7414c-177">So verwenden Sie geschachtelte Azure AD-Gruppen:</span><span class="sxs-lookup"><span data-stu-id="7414c-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="7414c-178">Identifizieren oder erstellen Sie die Azure AD-Gruppen, die Benutzerkonten enthalten sollen, und fügen Sie die entsprechenden Benutzerkonten als Mitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="7414c-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="7414c-179">Erstellen Sie die Azure AD-basierte Containerzugriffsgruppe, die die anderen Azure AD-Gruppen enthalten soll, und fügen Sie die Gruppen als Mitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="7414c-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="7414c-180"> Um die entsprechende Zugriffsebene für die Containerzugriffsgruppe festzulegen, identifizieren Sie die SharePoint-Gruppe und die entsprechende Berechtigungsstufe.</span><span class="sxs-lookup"><span data-stu-id="7414c-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7414c-181">Sie können keine geschachtelten Office 365-Gruppen verwenden.</span><span class="sxs-lookup"><span data-stu-id="7414c-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="7414c-182">Es folgt ein Beispiel für geschachtelte Azure AD-Gruppen für die Mitgliedergruppe Access ProjektX.</span><span class="sxs-lookup"><span data-stu-id="7414c-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![Ein Beispiel für geschachtelte Zugriffsgruppen für die Mitglieder der Zugriffsgruppe auf der ProjektX-Website.](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="7414c-184">Da alle Benutzerkonten in der Research, Engineering und Project leads Teams Websitemitglieder werden sollen, ist es einfacher, ihren Azure Active Directory-Gruppen zur Gruppe Zugriff ProjektX Mitglieder hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="7414c-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="7414c-185">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7414c-185">Next step</span></span>

<span data-ttu-id="7414c-186">Wenn Sie zum Erstellen und Konfigurieren einer isolierten-Website in der Produktion bereit sind, finden Sie unter [Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="7414c-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7414c-187">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="7414c-187">See Also</span></span>

[<span data-ttu-id="7414c-188">Isolierte SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="7414c-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="7414c-189">Verwalten einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="7414c-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="7414c-190">Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="7414c-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="7414c-191">Bereitstellen einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="7414c-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



