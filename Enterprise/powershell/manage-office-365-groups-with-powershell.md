---
title: Verwalten von Office 365-Gruppen mit PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Hier erfahren Sie, wie Sie allgemeine Verwaltungsaufgaben für Office 365-Gruppen im Microsoft PowerShell ausführen.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760057"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="5e977-103">Verwalten von Office 365-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e977-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="5e977-104">*Letzte aktualisierte 18-April, 2018*</span><span class="sxs-lookup"><span data-stu-id="5e977-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="5e977-p101">In diesem Artikel werden die Schritte für allgemeine Verwaltungsaufgaben für Gruppen in Microsoft PowerShell ausführen. Außerdem werden die PowerShell-Cmdlets für Gruppen aufgelistet. Info zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von SharePoint Online-Websites mithilfe von PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="5e977-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="5e977-108">Link zu Ihrer Richtlinien für die Verwendung von Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="5e977-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="5e977-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-109"></span></span>

<span data-ttu-id="5e977-p102">Wenn können Benutzer [Erstellen oder bearbeiten eine Gruppe in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), Sie sie einen Link zu Richtlinien für die Verwendung Ihrer Organisation anzeigen. Angenommen, Sie benötigen ein spezielles Präfix oder suffix, das auf den Namen einer Gruppe hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5e977-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="5e977-p103">Verwenden Sie die Benutzer Ihrer Organisation Verwendungsrichtlinien für für Office 365-Gruppen auf Azure Active Directory PowerShell. Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://go.microsoft.com/fwlink/?LinkID=827484) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** auf den Verwendung Leitlinie Hyperlink definieren möchten. Einmal führen Sie das Cmdlet AAD des Benutzers sehen Sie, den Link, um Ihre Richtlinien beim Erstellen und bearbeiten Sie eine Gruppe in Outlook.</span><span class="sxs-lookup"><span data-stu-id="5e977-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Erstellen einer neuen Gruppe durch Verwendung Richtlinien link](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Klicken Sie auf Gruppe Verwendungsrichtlinien für um finden in Ihrem Unternehmen Richtlinien für Office 365-Gruppen](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="5e977-117">Zulassen, dass Benutzer senden als der Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="5e977-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="5e977-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-118"></span></span>
  
<span data-ttu-id="5e977-p104">Wenn Sie Ihre Office 365-Gruppen "Senden als" aktivieren möchten, verwenden Sie die [Add-recipientpermission können](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) und die Cmdlets [Get-recipientpermission können](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) , um dies zu konfigurieren. Nachdem Sie diese Einstellung aktivieren, können Office 365-Benutzer Outlook oder Outlook im Web zum Senden und Antworten auf e-Mail, wie die Office 365-Gruppe. Benutzer können wechseln, erstellen eine neue e-Mail-Adresse der Gruppe, und ändern Sie das Feld "Senden als" in e-Mail-Adresse der Gruppe.</span><span class="sxs-lookup"><span data-stu-id="5e977-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="5e977-122">([Sie können hierzu auch in der Exchange-Verwaltungskonsole](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="5e977-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="5e977-p105">Verwenden Sie das folgende Skript ersetzen \* \<GroupAlias\> \* mit dem Alias der Gruppe, die Sie aktualisieren möchten, und \* \<Useraliascontoso\johndoe\> \* mit dem Alias des Benutzers, der Sie Berechtigungen erteilen möchten. Zum Ausführen dieses Skripts [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) .</span><span class="sxs-lookup"><span data-stu-id="5e977-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="5e977-125">Sobald das Cmdlet ausgeführt wird, können Benutzer, wie die Gruppe zu senden, indem Sie die Gruppe e-Mail-Adresse in das Feld **aus** Outlook oder Outlook im Web wechseln.</span><span class="sxs-lookup"><span data-stu-id="5e977-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="5e977-126">Erstellen von Klassifikationen für Office-Gruppen in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="5e977-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="5e977-p106">Sie können Klassifikationen erstellen, die die Benutzer in Ihrer Organisation beim Erstellen einer Gruppe von Office 365 festlegen können. Beispielsweise können Sie Benutzern "Standard", "Geheim" und "Top Secret" Festlegen von für Gruppen, die sie erstellen. Klassifikationen in der Gruppe werden nicht standardmäßig festgelegt, und Sie müssen beim Erstellen, damit Ihre Benutzer festgelegt. Verwenden Sie Azure Active Directory PowerShell, um Ihre Benutzer zu Ihrer Organisation Verwendungsrichtlinien für für Office 365 Gruppen verweisen.</span><span class="sxs-lookup"><span data-stu-id="5e977-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="5e977-131">Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** die Klassifikation für Office 365 Gruppen definieren.</span><span class="sxs-lookup"><span data-stu-id="5e977-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="5e977-132">Eine Beschreibung, die jeder Klassifizierung zuordnen, den Sie verwenden können, um das Attribut der Einstellungen *ClassificationDescriptions* definieren.</span><span class="sxs-lookup"><span data-stu-id="5e977-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="5e977-133">Klassifikation entspricht, in dem die Zeichenfolgen in der ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="5e977-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="5e977-134">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5e977-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="5e977-135">Führen Sie das Cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) nach der Ausführung des oben genannten Azure Active Directory-Cmdlets, um die Klassifikation festzulegen Wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="5e977-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="5e977-136">Oder erstellen Sie eine neue Gruppe mit einer Klassifikation.</span><span class="sxs-lookup"><span data-stu-id="5e977-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="5e977-137">Weitere Informationen zur Verwendung von Exchange Online PowerShell finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) und [Herstellen einer Verbindung mit Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="5e977-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="5e977-138">Nachdem diese Einstellungen aktiviert sind, werden den Besitzer der Gruppe wählen eine Klassifizierung aus dem Dropdown-Menü in Outlook im Web und Outlook, und speichern Sie es von der Gruppenseite **Bearbeiten** können.</span><span class="sxs-lookup"><span data-stu-id="5e977-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Wählen Sie Office 365 Gruppe Klassifikation](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="5e977-140">Office 365-Gruppen aus der globalen Adressliste ausblenden</span><span class="sxs-lookup"><span data-stu-id="5e977-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="5e977-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-141"></span></span>

<span data-ttu-id="5e977-p107">Sie können angeben, ob eine Office 365-Gruppe in der globalen Adressliste (GAL) und andere Listen in Ihrer Organisation angezeigt. Wenn Sie eine Gruppe rechtsabteilung, die nicht in der Adressliste angezeigt haben werden sollen, können Sie diese Gruppe aus der Anzeige im GAL beenden. Führen Sie das Cmdlet Set-Unified Gruppe blenden Sie die Gruppe aus der Adressliste wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5e977-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="5e977-145">Zulassen, dass nur interne Benutzer Nachricht an Office 365-Gruppe senden</span><span class="sxs-lookup"><span data-stu-id="5e977-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="5e977-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-146"></span></span>

<span data-ttu-id="5e977-p108">Wenn Sie nicht, dass Benutzer aus einer anderen Organisation zum Senden von e-Mail an eine Gruppe von Office 365 möchten, können Sie die Einstellungen für diese Gruppe ändern. Es können nur interne Benutzer eine e-Mail an Ihre Gruppe senden. Wenn externer Benutzer zum Senden von Nachrichten an diese Gruppe versuchen werden sie abgelehnt.</span><span class="sxs-lookup"><span data-stu-id="5e977-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="5e977-150">Führen Sie das Cmdlet Set-UnifiedGroup aktualisieren Sie diese Einstellung an, wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5e977-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="5e977-151">Hinzufügen von e-Mail-Infos zu den Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="5e977-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="5e977-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-152"></span></span>

<span data-ttu-id="5e977-153">Wenn der Absender versucht, eine e-Mail an eine Gruppe von Office 365 senden, kann eine e-Mail-Info für diese angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5e977-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="5e977-154">Führen Sie das Cmdlet Set-Unified Group, um eine e-Mail-Info zur Gruppe hinzufügen möchten:</span><span class="sxs-lookup"><span data-stu-id="5e977-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="5e977-p109">Zusammen mit e-Mail-Info können Sie auch MailTipTranslations, festlegen, der zusätzliche Sprachen für die e-Mail-Info angibt. Angenommen Sie, Sie haben die spanische Übersetzung, und klicken Sie dann den folgenden Befehl ausführen möchten:</span><span class="sxs-lookup"><span data-stu-id="5e977-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="5e977-157">Ändern des Anzeigenamens der Gruppe der Office 365</span><span class="sxs-lookup"><span data-stu-id="5e977-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="5e977-p110">Angezeigter Name Gibt den Namen der Gruppe der Office 365. Sie können diesen Namen in der Exchange-Verwaltungskonsole oder Office 365-Verwaltungsportal sehen. Sie können den Anzeigenamen der Gruppe bearbeiten oder einen Anzeigenamen zu einer vorhandenen Office 365-Gruppe durch Ausführen des Befehls Set-UnifiedGroup zuweisen:</span><span class="sxs-lookup"><span data-stu-id="5e977-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="5e977-161">Ändern Sie die Standardeinstellung der Office 365-Gruppen für Outlook in öffentlich oder privat</span><span class="sxs-lookup"><span data-stu-id="5e977-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="5e977-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5e977-162"></span></span>

<span data-ttu-id="5e977-p111">Office 365 werden Gruppen in Outlook als privat standardmäßig erstellt werden. Wenn Ihre Organisation Office 365 Gruppen als öffentliches erstellt werden möchte, in der Standardeinstellung (oder wieder auf Private), verwenden Sie diese Syntax der PowerShell-Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5e977-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="5e977-165">So legen Sie auf Private fest:</span><span class="sxs-lookup"><span data-stu-id="5e977-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="5e977-166">So überprüfen die Einstellung:</span><span class="sxs-lookup"><span data-stu-id="5e977-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="5e977-167">Weitere Informationen finden Sie unter [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) und [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="5e977-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="5e977-168">Cmdlets für Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="5e977-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="5e977-169">Die folgenden Cmdlets können mit Office 365-Gruppen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5e977-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="5e977-170">**Name des Cmdlets**</span><span class="sxs-lookup"><span data-stu-id="5e977-170">**Cmdlet name**</span></span>|<span data-ttu-id="5e977-171">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="5e977-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="5e977-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5e977-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="5e977-173">Verwenden Sie dieses Cmdlet zum Nachschlagen von vorhandenen Office 365-Gruppen, und klicken Sie zum Anzeigen der Eigenschaften des Group-Objekts</span><span class="sxs-lookup"><span data-stu-id="5e977-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="5e977-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5e977-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="5e977-175">Aktualisieren Sie die Eigenschaften einer bestimmten Gruppe von Office 365</span><span class="sxs-lookup"><span data-stu-id="5e977-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5e977-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5e977-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="5e977-p112">Erstellen einer neuen Office 365-Gruppe an. Dieses Cmdlet bietet einen minimalen Satz von Parametern, für die Einstellung Werte für erweiterte Eigenschaften Set-UnifiedGroup nach dem Erstellen der neuen Gruppe verwenden</span><span class="sxs-lookup"><span data-stu-id="5e977-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="5e977-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5e977-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="5e977-180">Löschen einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="5e977-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5e977-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5e977-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="5e977-182">Abrufen von Informationen für Mitgliedschafts- und Besitzer für die Gruppe ein Office 365</span><span class="sxs-lookup"><span data-stu-id="5e977-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5e977-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5e977-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="5e977-184">Hinzufügen von hundert oder Tausende von Benutzern oder neue Besitzer einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="5e977-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5e977-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5e977-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="5e977-186">Entfernen Sie Besitzer und Mitglieder aus einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="5e977-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5e977-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5e977-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="5e977-p113">Dient zum Anzeigen von Informationen zum benutzerfoto ein Konto zugeordnet. Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5e977-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="5e977-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5e977-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="5e977-p114">Verwendet, um ein benutzerfoto mit einem Konto zuzuordnen. Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5e977-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="5e977-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5e977-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="5e977-194">Entfernen Sie das Foto für eine Gruppe von Office 365</span><span class="sxs-lookup"><span data-stu-id="5e977-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="5e977-195">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5e977-195">Related topics</span></span>

[<span data-ttu-id="5e977-196">Upgrade Verteilerlisten zu Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="5e977-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="5e977-197">Verwalten von Personen, die Office 365-Gruppen erstellen können</span><span class="sxs-lookup"><span data-stu-id="5e977-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="5e977-198">Verwalten des Gastzugriffs auf Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="5e977-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="5e977-199">Statische Gruppenmitgliedschaft in dynamischen ändern</span><span class="sxs-lookup"><span data-stu-id="5e977-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
