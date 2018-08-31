---
title: Verwalten von Office 365-Gruppen mit PowerShell
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Letzte aktualisierte 18-April, 2018
ms.openlocfilehash: 8def3b304a19ad57887c992aa6342ea2cf14ba28
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541072"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="2154b-103">Verwalten von Office 365-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="2154b-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="2154b-104">*Letzte aktualisierte 18-April, 2018*</span><span class="sxs-lookup"><span data-stu-id="2154b-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="2154b-p101">In diesem Artikel werden die Schritte für allgemeine Verwaltungsaufgaben für Gruppen in Microsoft PowerShell ausführen. Außerdem werden die PowerShell-Cmdlets für Gruppen aufgelistet. Info zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von Teamwebsites und kommunikationswebsites mithilfe von PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span><span class="sxs-lookup"><span data-stu-id="2154b-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage team sites and communication sites by using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="2154b-108">Allgemeine Aufgaben zum Verwalten von Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="2154b-109">Upgrade von Verteilerlisten zu Office 365-Gruppen in Outlook</span><span class="sxs-lookup"><span data-stu-id="2154b-109">Upgrade distribution lists to Office 365 Groups in Outlook</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [<span data-ttu-id="2154b-110">Verwalten von Benutzer, die Office 365 Gruppen erstellen können</span><span class="sxs-lookup"><span data-stu-id="2154b-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [<span data-ttu-id="2154b-111">Verwalten von Gastzugriff auf Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [<span data-ttu-id="2154b-112">Verwalten von Gruppen dynamisch in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2154b-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="2154b-113">Fügen Sie Hunderte oder Tausende von Benutzern zu Office 365-Gruppen hinzu, verwenden Sie das [Cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="2154b-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="2154b-114">Link zu Ihrer Richtlinien für die Verwendung von Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="2154b-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-115"></span></span>

<span data-ttu-id="2154b-p102">Wenn können Benutzer [einer Gruppe in Outlook erstellen](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), Sie sie einen Link zu Ihrer Organisation Verwendungsrichtlinien für anzeigen. Angenommen, Sie benötigen ein spezielles Präfix oder suffix, das auf den Namen einer Gruppe hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="2154b-p102">When users [Create a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="2154b-p103">Verwenden Sie die Benutzer Ihrer Organisation Verwendungsrichtlinien für für Office 365-Gruppen auf Azure Active Directory PowerShell. Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://go.microsoft.com/fwlink/?LinkID=827484) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** auf den Verwendung Leitlinie Hyperlink definieren möchten. Einmal führen Sie das Cmdlet AAD des Benutzers sehen Sie, den Link, um Ihre Richtlinien beim Erstellen und bearbeiten Sie eine Gruppe in Outlook.</span><span class="sxs-lookup"><span data-stu-id="2154b-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Erstellen einer neuen Gruppe durch Verwendung Richtlinien link](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Klicken Sie auf Gruppe Verwendungsrichtlinien für um finden in Ihrem Unternehmen Richtlinien für Office 365-Gruppen](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="2154b-123">Zulassen, dass Benutzer senden als der Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="2154b-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="2154b-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-124"></span></span>

<span data-ttu-id="2154b-p104">Sie können diese Schritte auch in der Exchange-Verwaltungskonsole durchführen. Finden Sie unter [zulassen, dass Mitglieder als senden oder im Namen einer Gruppe senden](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span><span class="sxs-lookup"><span data-stu-id="2154b-p104">You can also do this in the Exchange Admin Center. See [Allow members to send as or send on behalf of a Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span></span>
  
<span data-ttu-id="2154b-p105">Wenn Sie Ihre Office 365-Gruppen "Senden als" aktivieren möchten, verwenden Sie die [Add-recipientpermission können](https://go.microsoft.com/fwlink/p/?LinkId=723960) und die Cmdlets [Get-recipientpermission können](https://go.microsoft.com/fwlink/p/?LinkId=733239) , um dies zu konfigurieren. Nachdem Sie diese Einstellung aktivieren, können Office 365-Benutzer Outlook oder Outlook im Web zum Senden und Antworten auf e-Mail, wie die Office 365-Gruppe. Benutzer können wechseln, erstellen eine neue e-Mail-Adresse der Gruppe, und ändern Sie das Feld "Senden als" in e-Mail-Adresse der Gruppe.</span><span class="sxs-lookup"><span data-stu-id="2154b-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2154b-130">Sie müssen die Gruppe e-Mail-Adresse in das Feld **"Cc"** hinzufügen, beim Verfassen der e-Mails, die "Senden als", damit die Nachricht an die Gruppe gesendet wird und in der Gruppe Unterhaltungen wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2154b-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="2154b-131">Zu diesem Zeitpunkt ist die einzige Möglichkeit zum Aktualisieren der Postfachrichtlinie [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="2154b-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="2154b-132">Verwenden Sie diesen Befehl, um den Gruppenalias festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2154b-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="2154b-133">Verwenden Sie diesen Befehl, um den Alias des Benutzers festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2154b-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="2154b-134">Verwenden Sie diesen Befehl, um der Groupalias an das Cmdlet Get-Recipient abzurufenden die Empfänger-Details zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="2154b-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="2154b-p106">Klicken Sie dann muss der Empfänger Zielname (Gruppenname) an das Cmdlet Add-recipientpermission können übergeben werden. Die useraliascontoso\johndoe für die die Berechtigung "Sendas" erhält, wird der - Vertrauensnehmerdomäne-Parameter zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="2154b-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="2154b-137">Sobald das Cmdlet ausgeführt wird, können Benutzer, wie die Gruppe zu senden, indem Sie die Gruppe e-Mail-Adresse in das Feld **aus** Outlook oder Outlook im Web wechseln.</span><span class="sxs-lookup"><span data-stu-id="2154b-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="2154b-138">Erstellen von Klassifikationen für Office-Gruppen in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="2154b-138">Create classifications for Office groups in your organization</span></span>
<span data-ttu-id="2154b-139"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-139"></span></span>

<span data-ttu-id="2154b-p107">Sie können Klassifikationen erstellen, die die Benutzer in Ihrer Organisation beim Erstellen einer Gruppe von Office 365 festlegen können. Beispielsweise können Sie Benutzern "Standard", "Geheim" und "Top Secret" Festlegen von für Gruppen, die sie erstellen. Klassifikationen in der Gruppe werden nicht standardmäßig festgelegt, und Sie müssen beim Erstellen, damit Ihre Benutzer festgelegt. Verwenden Sie Azure Active Directory PowerShell, um Ihre Benutzer zu Ihrer Organisation Verwendungsrichtlinien für für Office 365 Gruppen verweisen.</span><span class="sxs-lookup"><span data-stu-id="2154b-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="2154b-144">Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://go.microsoft.com/fwlink/?LinkID=827484) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** die Klassifikation für Office 365 Gruppen definieren.</span><span class="sxs-lookup"><span data-stu-id="2154b-144">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="2154b-145">Eine Beschreibung, die jeder Klassifizierung zuordnen, den Sie verwenden können, um das Attribut der Einstellungen *ClassificationDescriptions* definieren.</span><span class="sxs-lookup"><span data-stu-id="2154b-145">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="2154b-146">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2154b-146">For example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="2154b-147">Führen Sie das Cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) nach der Ausführung des oben genannten Azure Active Directory-Cmdlets, um die Klassifikation festzulegen Wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="2154b-147">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="2154b-148">Oder erstellen Sie eine neue Gruppe mit einer Klassifikation.</span><span class="sxs-lookup"><span data-stu-id="2154b-148">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="2154b-149">[Verwenden von PowerShell mit Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) und [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) ausführliche Informationen zur Verwendung von Exchange Online PowerShell Auschecken.</span><span class="sxs-lookup"><span data-stu-id="2154b-149">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="2154b-150">Nachdem diese Einstellungen aktiviert sind, werden den Besitzer der Gruppe wählen eine Klassifizierung aus dem Dropdown-Menü in Outlook im Web und Outlook, und speichern Sie es von der Gruppenseite **Bearbeiten** können.</span><span class="sxs-lookup"><span data-stu-id="2154b-150">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Wählen Sie Office 365 Gruppe Klassifikation](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="2154b-152">Office 365-Gruppen aus der globalen Adressliste ausblenden</span><span class="sxs-lookup"><span data-stu-id="2154b-152">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="2154b-153"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-153"></span></span>

<span data-ttu-id="2154b-p108">Sie können angeben, ob eine Office 365-Gruppe in der globalen Adressliste (GAL) und andere Listen in Ihrer Organisation angezeigt. Wenn Sie eine Gruppe rechtsabteilung, die nicht in der Adressliste angezeigt haben werden sollen, können Sie diese Gruppe aus der Anzeige im GAL beenden. Führen Sie die Gruppe Set-Unified-Cmdlet zum Ausblenden des Gruppe aus der Adressliste wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="2154b-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="2154b-157">Zulassen, dass nur interne Benutzer Nachricht an Office 365-Gruppe senden</span><span class="sxs-lookup"><span data-stu-id="2154b-157">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="2154b-158"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-158"></span></span>

<span data-ttu-id="2154b-p109">Wenn Sie nicht, dass Benutzer aus einer anderen Organisation zum Senden von e-Mail an eine Gruppe von Office 365 möchten, können Sie die Einstellungen für diese Gruppe ändern. Es können nur interne Benutzer eine e-Mail an Ihre Gruppe senden. Wenn externer Benutzer zum Senden von Nachrichten an diese Gruppe versuchen werden sie abgelehnt.</span><span class="sxs-lookup"><span data-stu-id="2154b-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="2154b-162">Führen Sie das Set-UnifiedGroup-Cmdlet zum Aktualisieren dieser Einstellung an, wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="2154b-162">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="2154b-163">Hinzufügen von e-Mail-Infos zu den Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-163">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="2154b-164"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-164"></span></span>

<span data-ttu-id="2154b-165">Wenn der Absender versucht, eine e-Mail an eine Gruppe von Office 365 senden, kann ihm eine e-Mail-Info angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2154b-165">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="2154b-166">Führen Sie die Gruppe Set-Unified-Cmdlet, um eine e-Mail-Info zur Gruppe hinzufügen möchten:</span><span class="sxs-lookup"><span data-stu-id="2154b-166">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="2154b-p110">Zusammen mit e-Mail-Info können Sie auch festlegen MailTipTranslations, die für zusätzliche Sprachen gibt an, die e-Mail-Info. Angenommen Sie, Sie haben die spanische Übersetzung, und klicken Sie dann den folgenden Befehl ausführen möchten:</span><span class="sxs-lookup"><span data-stu-id="2154b-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="2154b-169">Ändern des Anzeigenamens der Gruppe der Office 365</span><span class="sxs-lookup"><span data-stu-id="2154b-169">Change Display name of the Office 365 group</span></span>
<span data-ttu-id="2154b-170"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-170"></span></span>

<span data-ttu-id="2154b-p111">Angezeigter Name Gibt den Namen der Gruppe der Office 365. Dieser Name kann in Ihrer Exchange Admin Center oder o365 Admin-Portal angezeigt werden. Sie können den Anzeigenamen der Gruppe bearbeiten oder einer vorhandenen Office 365-Gruppe einen Anzeigenamen zuweisen, indem Sie Set-UnifiedGroup-Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="2154b-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="2154b-174">Verwalten von benutzerfotos in Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-174">Manage user photos in Office 365 Groups</span></span>
<span data-ttu-id="2154b-175"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-175"></span></span>

<span data-ttu-id="2154b-176">| |</span><span class="sxs-lookup"><span data-stu-id="2154b-176"></span></span>
|<span data-ttu-id="2154b-177">**Name des Cmdlets**</span><span class="sxs-lookup"><span data-stu-id="2154b-177">**Cmdlet name**</span></span>|<span data-ttu-id="2154b-178">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="2154b-178">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="2154b-179">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2154b-179">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="2154b-p112">Dient zum Anzeigen von Informationen zum benutzerfoto ein Konto zugeordnet. Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2154b-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="2154b-182">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2154b-182">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="2154b-p113">Verwendet, um ein benutzerfoto mit einem Konto zuzuordnen. Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2154b-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="2154b-185">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="2154b-185">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="2154b-186">Entfernen Sie das Foto für eine Gruppe von Office 365</span><span class="sxs-lookup"><span data-stu-id="2154b-186">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="2154b-187">Ändern Sie die Standardeinstellung der Office 365-Gruppen für Outlook in öffentlich oder privat</span><span class="sxs-lookup"><span data-stu-id="2154b-187">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="2154b-188"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="2154b-188"></span></span>

<span data-ttu-id="2154b-p114">Office 365 werden Gruppen in Outlook als privat standardmäßig erstellt werden. Wenn Ihre Organisation Office 365-Gruppen für Outlook können Sie als öffentlich erstellt werden, in der Standardeinstellung (oder auf Private) möchte, verwenden Sie diese Syntax der PowerShell-Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2154b-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="2154b-191">So legen Sie auf Private fest:</span><span class="sxs-lookup"><span data-stu-id="2154b-191">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="2154b-192">So überprüfen die Einstellung:</span><span class="sxs-lookup"><span data-stu-id="2154b-192">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="2154b-193">Weitere Informationen finden Sie unter [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) und [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="2154b-193">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="2154b-194">Cmdlets für Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="2154b-194">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="2154b-p115">Die folgenden Cmdlets wurden kürzlich Office 365 Gruppen zur Verfügung gestellt. Wenn Sie diese verwenden können nicht, hat Ihr Office 365-Abonnement mit dieser Funktionalität noch nicht aktualisiert wurden. Überprüfen Sie Ihre Nachrichtencenter und die [Wegweiser für Office 365](http://roadmap.office.com/en-us).</span><span class="sxs-lookup"><span data-stu-id="2154b-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
<span data-ttu-id="2154b-198">| |</span><span class="sxs-lookup"><span data-stu-id="2154b-198"></span></span>
|<span data-ttu-id="2154b-199">**Name des Cmdlets**</span><span class="sxs-lookup"><span data-stu-id="2154b-199">**Cmdlet name**</span></span>|<span data-ttu-id="2154b-200">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="2154b-200">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="2154b-201">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="2154b-201">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="2154b-202">Verwenden Sie dieses Cmdlet zum Nachschlagen von vorhandenen Office 365-Gruppen, und klicken Sie zum Anzeigen der Eigenschaften des Group-Objekts</span><span class="sxs-lookup"><span data-stu-id="2154b-202">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="2154b-203">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="2154b-203">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="2154b-204">Aktualisieren Sie die Eigenschaften einer bestimmten Gruppe von Office 365</span><span class="sxs-lookup"><span data-stu-id="2154b-204">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2154b-205">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="2154b-205">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="2154b-p116">Erstellen einer neuen Office 365-Gruppe an. Dieses Cmdlet bietet einen minimalen Satz von Parametern, für die Einstellung Werte für erweiterte Eigenschaften Set-UnifiedGroup nach dem Erstellen der neuen Gruppe verwenden</span><span class="sxs-lookup"><span data-stu-id="2154b-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="2154b-208">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="2154b-208">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="2154b-209">Löschen einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="2154b-209">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2154b-210">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2154b-210">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="2154b-211">Abrufen von Informationen für Mitgliedschafts- und Besitzer für die Gruppe ein Office 365</span><span class="sxs-lookup"><span data-stu-id="2154b-211">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2154b-212">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2154b-212">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="2154b-213">Hinzufügen von hundert oder Tausende von Benutzern oder neue Besitzer einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="2154b-213">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="2154b-214">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="2154b-214">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="2154b-215">Entfernen Sie Besitzer und Mitglieder aus einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="2154b-215">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="2154b-216">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2154b-216">For more information</span></span>

- [<span data-ttu-id="2154b-217">Verwenden von PowerShell</span><span class="sxs-lookup"><span data-stu-id="2154b-217">Using PowerShell</span></span>](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [<span data-ttu-id="2154b-218">Anwenden oder Entfernen einer Outlook Web App-Postfachrichtlinie auf ein Postfach bzw. von einem Postfach</span><span class="sxs-lookup"><span data-stu-id="2154b-218">Apply or remove an Outlook Web App mailbox policy on a mailbox</span></span>](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="2154b-219">Office 365 gruppiert Benennungsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="2154b-219">Office 365 Groups naming policy</span></span>](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

