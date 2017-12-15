---
title: Verwalten einer isolierten SharePoint Online-Teamwebsite
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "Zusammenfassung: Mit diesen Verfahren können Sie Ihre isolierte SharePoint Online-Teamwebsite verwalten."
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="4b07c-103">Verwalten einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="4b07c-103">Manage an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="4b07c-104">**Zusammenfassung:** Mit diesen Verfahren können Sie Ihre isolierte SharePoint Online-Teamwebsite verwalten.</span><span class="sxs-lookup"><span data-stu-id="4b07c-104">**Summary:** Manage your isolated SharePoint Online team site with these procedures.</span></span>
  
<span data-ttu-id="4b07c-105">In diesem Artikel werden allgemeine Verwaltungsaufgaben für eine isolierte SharePoint Online-Teamwebsite erläutert.</span><span class="sxs-lookup"><span data-stu-id="4b07c-105">This article describes common management operations for an isolated SharePoint Online team site.</span></span>
  
## <a name="add-a-new-user"></a><span data-ttu-id="4b07c-106">Hinzufügen eines neuen Benutzers</span><span class="sxs-lookup"><span data-stu-id="4b07c-106">Add a new user</span></span>

<span data-ttu-id="4b07c-107">Wenn ein neuer Benutzer der Website beitritt, müssen Sie entscheiden, in welchem Umfang, d. h. mit welcher Berechtigungsstufe, er an der Website teilnehmen soll:</span><span class="sxs-lookup"><span data-stu-id="4b07c-107">When someone new joins the site, you must decide their level of participation in the site:</span></span>
  
- <span data-ttu-id="4b07c-108">Verwaltung: Fügen Sie das neue Benutzerkonto zur Zugriffsgruppe der Websiteadministratoren hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-108">Administration: Add the new user account to the site admins access group</span></span>
    
- <span data-ttu-id="4b07c-109">Aktive Zusammenarbeit: Fügen Sie das Benutzerkonto zur Zugriffsgruppe der Websitemitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-109">Active collaboration: Add the user account to the site members access group</span></span>
    
- <span data-ttu-id="4b07c-110">Anzeige: Fügen Sie das Benutzerkonto zur Zugriffsgruppe der Websitebetrachter hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-110">Viewing: Add the user account to the site viewers access group</span></span>
    
<span data-ttu-id="4b07c-111">Wenn Sie Benutzerkonten und Gruppen über Windows Server Active Directory (AD) verwalten, fügen Sie die entsprechenden Benutzer mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen zu den entsprechenden Zugriffsgruppen hinzu, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="4b07c-111">If you are managing user accounts and groups through Windows Server Active Directory (AD), add the appropriate users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="4b07c-112">Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder Microsoft PowerShell verwenden:</span><span class="sxs-lookup"><span data-stu-id="4b07c-112">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or Microsoft PowerShell:</span></span>
  
- <span data-ttu-id="4b07c-113">Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Benutzer zu den entsprechenden Zugriffsgruppen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-113">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate users to the appropriate access groups.</span></span>
    
- <span data-ttu-id="4b07c-p101">Für PowerShell, erste [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218). Um eine Zugriffsgruppe mit den Benutzerprinzipalnamen (UPN) ein Benutzerkonto hinzuzufügen, verwenden Sie den folgenden PowerShell-Befehlsblock:</span><span class="sxs-lookup"><span data-stu-id="4b07c-p101">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To add a user account to an access group with its user principal name (UPN), use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="4b07c-116">Um eine Textdatei zu erhalten, die alle PowerShell-Befehle und ein Excel-Konfigurationsarbeitsblatt enthält, die PowerShell-Befehle basierend auf Ihren Gruppen- und Benutzerkontonamen generiert, laden Sie das [Kit für die Bereitstellung einer isolierten SharePoint Online-Teamwebsite](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907) herunter.</span><span class="sxs-lookup"><span data-stu-id="4b07c-116">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 

<span data-ttu-id="4b07c-117">Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto unter Verwendung des Anzeigenamens zu einer Zugriffsgruppe hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4b07c-117">To add a user account to an access group with its display name, use the following PowerShell command block:</span></span>

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a><span data-ttu-id="4b07c-118">Hinzufügen einer neuen Gruppe</span><span class="sxs-lookup"><span data-stu-id="4b07c-118">Add a new group</span></span>

<span data-ttu-id="4b07c-119">Wenn Sie Zugriff für eine ganze Gruppe hinzufügen möchten, müssen Sie entscheiden, in welchem Umfang, d. h. mit welcher Berechtigungsstufe, sämtliche Mitglieder der Gruppe an der Website teilnehmen sollen:</span><span class="sxs-lookup"><span data-stu-id="4b07c-119">To add access to an entire group, you must decide the level of participation of all the members of the group in the site:</span></span>
  
- <span data-ttu-id="4b07c-120">Verwaltung: Fügen Sie die Gruppe zur Zugriffsgruppe der Websiteadministratoren hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-120">Administration: Add the group to the site admins access group</span></span>
    
- <span data-ttu-id="4b07c-121">Aktive Zusammenarbeit: Fügen Sie die Gruppe zur Zugriffsgruppe der Websitemitglieder hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-121">Active collaboration: Add the group to the site members access group</span></span>
    
- <span data-ttu-id="4b07c-122">Anzeige: Fügen Sie die Gruppe zur Zugriffsgruppe der Websitbetrachter hinzu.</span><span class="sxs-lookup"><span data-stu-id="4b07c-122">Viewing: Add the group to the site viewers access group</span></span>
    
<span data-ttu-id="4b07c-123">Wenn Sie Benutzerkonten und Gruppen über Windows Server AD verwalten, fügen Sie die entsprechenden Gruppen mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen zu den entsprechenden Gruppen hinzu, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="4b07c-123">If you are managing user accounts and groups through Windows Server AD, add the appropriate groups to the appropriate groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="4b07c-124">Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:</span><span class="sxs-lookup"><span data-stu-id="4b07c-124">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="4b07c-125">Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Gruppen zu den entsprechenden Zugriffsgruppen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-125">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate groups to the appropriate access groups.</span></span>
    
- <span data-ttu-id="4b07c-p102">Für PowerShell, erste [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218). Verwenden Sie dann die folgenden PowerShell-Befehle:</span><span class="sxs-lookup"><span data-stu-id="4b07c-p102">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). Then, use the following PowerShell commands:</span></span>
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a><span data-ttu-id="4b07c-128">Entfernen eines Benutzers</span><span class="sxs-lookup"><span data-stu-id="4b07c-128">Remove a user</span></span>

<span data-ttu-id="4b07c-129">Wenn der Zugriff auf eine Website für einen Benutzer entfernt werden muss, entfernen Sie den betreffenden Benutzer aus der Zugriffsgruppe, in der er derzeit basierend auf dem Umfang seiner Teilnahme an der Website Mitglied ist:</span><span class="sxs-lookup"><span data-stu-id="4b07c-129">When someone's access must be removed from the site, you remove them from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="4b07c-130">Verwaltung: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websiteadministratoren.</span><span class="sxs-lookup"><span data-stu-id="4b07c-130">Administration: Remove the user account from the site admins access group</span></span>
    
- <span data-ttu-id="4b07c-131">Aktive Zusammenarbeit: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websitemitglieder.</span><span class="sxs-lookup"><span data-stu-id="4b07c-131">Active collaboration: Remove the user account from the site members access group</span></span>
    
- <span data-ttu-id="4b07c-132">Anzeige: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websitebetrachter.</span><span class="sxs-lookup"><span data-stu-id="4b07c-132">Viewing: Remove the user account from the site viewers access group</span></span>
    
<span data-ttu-id="4b07c-133">Wenn Sie Benutzerkonten und Gruppen über Windows Server AD verwalten, entfernen Sie die entsprechenden Benutzer mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen aus den entsprechenden Gruppen, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="4b07c-133">If you are managing user accounts and groups through Windows Server AD, remove the appropriate users from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="4b07c-134">Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:</span><span class="sxs-lookup"><span data-stu-id="4b07c-134">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="4b07c-135">Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Benutzer aus den entsprechenden Zugriffsgruppen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-135">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate users from the appropriate access groups.</span></span>
    
- <span data-ttu-id="4b07c-p103">Für PowerShell, erste [Verbinden mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218). Um ein Benutzerkonto aus einer Access-Gruppe mit der UPN entfernen möchten, verwenden Sie den folgenden PowerShell-Befehlsblock:</span><span class="sxs-lookup"><span data-stu-id="4b07c-p103">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To remove a user account from an access group with its UPN, use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

<span data-ttu-id="4b07c-138">Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto unter Verwendung des Anzeigenamens aus einer Zugriffsgruppe zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="4b07c-138">To remove a user account from an access group with its display name, use the following PowerShell command block:</span></span>
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a><span data-ttu-id="4b07c-139">Entfernen einer Gruppe</span><span class="sxs-lookup"><span data-stu-id="4b07c-139">Remove a group</span></span>

<span data-ttu-id="4b07c-140">Wenn der Zugriff für eine ganze Gruppe entfernt werden soll, entfernen Sie die betreffende Gruppe aus der Zugriffsgruppe, in der sie derzeit basierend auf dem Umfang ihrer Teilnahme an der Website Mitglied ist:</span><span class="sxs-lookup"><span data-stu-id="4b07c-140">To remove access for an entire group, you remove the group from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="4b07c-141">Verwaltung: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websiteadministratoren.</span><span class="sxs-lookup"><span data-stu-id="4b07c-141">Administration: Remove the group from the site admins access group</span></span>
    
- <span data-ttu-id="4b07c-142">Aktive Zusammenarbeit: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websitemitglieder.</span><span class="sxs-lookup"><span data-stu-id="4b07c-142">Active collaboration: Remove the group from the site members access group</span></span>
    
- <span data-ttu-id="4b07c-143">Anzeige: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websitebetrachter.</span><span class="sxs-lookup"><span data-stu-id="4b07c-143">Viewing: Remove the group from the site viewers access group</span></span>
    
<span data-ttu-id="4b07c-144">Wenn Sie Benutzerkonten und Gruppen über Windows Server Active Directory verwalten, entfernen Sie die entsprechenden Gruppen mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen aus den entsprechenden Zugriffsgruppen, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="4b07c-144">If you are managing user accounts and groups through Windows Server Active Directory, remove the appropriate groups from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="4b07c-145">Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:</span><span class="sxs-lookup"><span data-stu-id="4b07c-145">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="4b07c-146">Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Gruppen aus den entsprechenden Zugriffsgruppen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-146">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate groups from the appropriate access groups.</span></span>
    
- <span data-ttu-id="4b07c-147">Bei Verwendung von PowerShell müssen Sie zunächst [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul herstellen](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="4b07c-147">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>    
<span data-ttu-id="4b07c-148">Verwenden Sie den folgenden PowerShell-Befehlsblock, um eine Gruppe unter Verwendung des Anzeigenamens aus einer Zugriffsgruppe zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="4b07c-148">To remove a group from an access group using their display names, use the following PowerShell command block:</span></span>
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a><span data-ttu-id="4b07c-149">Erstellen eines Dokumentunterordners mit benutzerdefinierten Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="4b07c-149">Create a documents subfolder with custom permissions</span></span>

<span data-ttu-id="4b07c-p104">In manchen Fällen benötigt eine Teilmenge der Personen, die innerhalb der isolierten Website arbeiten, einen privateren Ort für die Zusammenarbeit. Für SharePoint Online-Websites können Sie einen Unterordner im Dokumentordner der Website erstellen und benutzerdefinierte Berechtigungen zuweisen. Benutzer ohne Berechtigungen können den Unterordner nicht sehen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-p104">In some cases, a subset of the people working within the isolated site need a more private place to collaborate. For SharePoint Online sites, you can create a subfolder in the Documents folder of the site and assign custom permissions. Those without permissions will not see the subfolder.</span></span>
  
<span data-ttu-id="4b07c-153">Gehen Sie zum Erstellen eines Dokumentunterordners mit benutzerdefinierten Berechtigungen folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="4b07c-153">To create a documents subfolder with custom permissions, do the following:</span></span>
  
1. <span data-ttu-id="4b07c-p105">Melden Sie sich bei Office 365 mit einem Konto an, das ein Mitglied der Zugriffsgruppe der Websiteadministratoren ist. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4b07c-p105">Sign in to Office 365 with an account that is a member of the admins access group for the site. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4b07c-156">Wechseln Sie zu der isolierten Teamwebsite, und klicken Sie auf **Dokumente**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-156">Go to the isolated team site and click **Documents**.</span></span>
    
3. <span data-ttu-id="4b07c-157">Navigieren Sie zu dem Ordner im Dokumentordner, der den Unterordner mit benutzerdefinierten Berechtigungen enthalten soll, erstellen Sie den Ordner, und öffnen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="4b07c-157">Browse to the folder in the documents folder that will contain the subfolder with custom permissions, create the folder, and then open it.</span></span>
    
4. <span data-ttu-id="4b07c-158">Klicken Sie auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-158">Click **Share**.</span></span>
    
5. <span data-ttu-id="4b07c-159">Klicken Sie auf **Freigegeben für > Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-159">Click **Shared with > Advanced**.</span></span>
    
6. <span data-ttu-id="4b07c-160">Klicken Sie auf **Berechtigungsvererbung beenden**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-160">Click **Stop inheriting permissions**, and then click **OK**.</span></span>
    
7. <span data-ttu-id="4b07c-161">Klicken Sie auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-161">Click **Share**.</span></span>
    
8. <span data-ttu-id="4b07c-162">Klicken Sie auf **Freigegeben für > Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-162">Click **Shared with > Advanced**.</span></span>
    
9. <span data-ttu-id="4b07c-163">Klicken Sie auf **Berechtigungen erteilen > Freigegeben für > Erweitert**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-163">Click **Grant Permissions > Shared with > Advanced**.</span></span>
    
10. <span data-ttu-id="4b07c-164">Klicken Sie auf der Berechtigungsseite auf ** \<Websitename > Mitglieder in der Liste**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-164">On the permissions page, click **\<site name> Members in the list**.</span></span>
    
11. <span data-ttu-id="4b07c-165">Klicken Sie auf die ** \<Websitename > Mitglieder** Seite, wählen Sie das Kontrollkästchen neben der Gruppe der Websitemitglieder Access an, klicken Sie auf **Aktionen**, klicken Sie auf **Benutzer aus Gruppe entfernen**, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-165">On the **\<site name> Members** page, select the checkmark next to the site members access group, click **Actions**, click **Remove users from group**, and then click **OK**.</span></span>
    
12. <span data-ttu-id="4b07c-166">Um diesem Unterordner bestimmte Mitglieder hinzuzufügen, klicken Sie auf **Neu > Benutzer hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-166">To add specific members to this subfolder, click **New > Add users**.</span></span>
    
13. <span data-ttu-id="4b07c-167">Geben Sie im Dialogfeld **Freigeben** die Namen der Benutzerkonten ein, die an Dateien im Unterordner zusammenarbeiten können, und klicken Sie dann auf **Freigeben**.</span><span class="sxs-lookup"><span data-stu-id="4b07c-167">In the **Share** dialog box, type the names of the user accounts that can collaborate on files in the subfolder, and then click **Share**.</span></span>
    
14. <span data-ttu-id="4b07c-168">Aktualisieren Sie die Webseite, um die neuen Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4b07c-168">Refresh the web page to see the new results.</span></span>
    
15. <span data-ttu-id="4b07c-169">Klicken Sie unter **Gruppen** im linken Navigationsbereich auf die ** \<Websitename > Besucher** gruppieren und verwenden Sie die Schritte 11 bis 14 Festlegen von Benutzerkonten, die die Dateien im Unterordner anzeigen können (bei Bedarf).</span><span class="sxs-lookup"><span data-stu-id="4b07c-169">Under **Groups** in the left navigation, click the **\<site name> Visitors** group and use steps 11-14 to specify the set of user accounts that can view the files in the subfolder (as needed).</span></span>
    
16. <span data-ttu-id="4b07c-170">Klicken Sie unter **Gruppen** im linken Navigationsbereich auf die ** \<Websitename > Besitzer** gruppieren und verwenden Sie die Schritte 11 bis 14 an die Gruppe von Benutzerkonten, die die Berechtigungen im Unterordner (nach Bedarf) verwalten können.</span><span class="sxs-lookup"><span data-stu-id="4b07c-170">Under **Groups** in the left navigation, click the **\<site name> Owners** group and use steps 11-14 to specify the set of user accounts that can administer the permissions in the subfolder (as needed).</span></span>
    
17. <span data-ttu-id="4b07c-171">Schließen Sie die Registerkarte **Benutzer und Gruppen** im Browser.</span><span class="sxs-lookup"><span data-stu-id="4b07c-171">Close the **People and Groups** tab in your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="4b07c-172">See Also</span><span class="sxs-lookup"><span data-stu-id="4b07c-172">See Also</span></span>

[<span data-ttu-id="4b07c-173">Isolierte SharePoint Online-Teamwebsites</span><span class="sxs-lookup"><span data-stu-id="4b07c-173">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="4b07c-174">Entwerfen einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="4b07c-174">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="4b07c-175">Sicherheitslösungen</span><span class="sxs-lookup"><span data-stu-id="4b07c-175">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="4b07c-176">Bereitstellen einer isolierten SharePoint Online-Teamwebsite</span><span class="sxs-lookup"><span data-stu-id="4b07c-176">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



