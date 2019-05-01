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
description: Erfahren Sie, wie Sie allgemeine Verwaltungsaufgaben für Office 365-Gruppen in Microsoft PowerShell ausführen.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491756"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="e3278-103">Verwalten von Office 365-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3278-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="e3278-104">*Letzte Aktualisierung 18 April, 2018*</span><span class="sxs-lookup"><span data-stu-id="e3278-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="e3278-105">Dieser Artikel enthält die Schritte zum Ausführen allgemeiner Verwaltungsaufgaben für Gruppen in Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3278-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="e3278-106">Außerdem werden die PowerShell-Cmdlets für Gruppen aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="e3278-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="e3278-107">Weitere Informationen zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von SharePoint Online-Websites mithilfe von PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="e3278-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="e3278-108">Link zu Ihren Office 365-Gruppen Nutzungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="e3278-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="e3278-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-109"></span></span>

<span data-ttu-id="e3278-110">Wenn Benutzer [eine Gruppe in Outlook erstellen oder bearbeiten](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), können Sie Ihnen einen Link zu den Nutzungsrichtlinien Ihrer Organisation anzeigen.</span><span class="sxs-lookup"><span data-stu-id="e3278-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="e3278-111">Wenn Sie beispielsweise ein bestimmtes Präfix oder Suffix für einen Gruppennamen hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="e3278-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="e3278-112">Verwenden Sie die Azure Active Directory PowerShell, um Ihre Benutzer auf die Nutzungsrichtlinien Ihrer Organisation für Office 365-Gruppen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e3278-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="e3278-113">Sehen Sie sich die [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://go.microsoft.com/fwlink/?LinkID=827484) an, und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** aus, um den Hyperlink Verwendungsrichtlinie zu definieren.</span><span class="sxs-lookup"><span data-stu-id="e3278-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="e3278-114">Nachdem Sie das AAD-Cmdlet ausgeführt haben, werden dem Benutzer beim Erstellen oder Bearbeiten einer Gruppe in Outlook der Link zu ihren Richtlinien angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e3278-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Erstellen einer neuen Gruppe mit dem Link "Verwendungsrichtlinien"](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Klicken Sie auf Gruppen Nutzungsrichtlinien, um die Richtlinien für ihre Organisationen in Office 365 zu sehen.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="e3278-117">Zulassen, dass Benutzer als Office 365-Gruppe senden</span><span class="sxs-lookup"><span data-stu-id="e3278-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="e3278-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-118"></span></span>
  
<span data-ttu-id="e3278-119">Wenn Sie möchten, dass Ihre Office 365-Gruppen "Senden als" aktivieren, verwenden Sie die Cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) und [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) , um dies zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e3278-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="e3278-120">Nachdem Sie diese Einstellung aktiviert haben, können Benutzer von Office 365-Gruppen Outlook oder Outlook im Web verwenden, um e-Mails als Office 365-Gruppe zu senden und zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="e3278-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="e3278-121">Benutzer können zur Gruppe wechseln, eine neue e-Mail erstellen und das Feld "Senden als" in die e-Mail-Adresse der Gruppe ändern.</span><span class="sxs-lookup"><span data-stu-id="e3278-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="e3278-122">([Sie können dies auch im Exchange Admin Center tun](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span><span class="sxs-lookup"><span data-stu-id="e3278-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="e3278-123">Verwenden Sie das folgende Skript, \* \<und\> \* ersetzen Sie GroupAlias durch den Alias der Gruppe, die Sie aktualisieren möchten, und \* \<useraliascontoso\johndoe\> \* mit dem Alias des Benutzers, dem Sie permssions erteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="e3278-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="e3278-124">Stellen Sie [eine Verbindung mit Exchange Online PowerShell her](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) , um dieses Skript auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e3278-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="e3278-125">Nachdem das Cmdlet ausgeführt wurde, können Benutzer zu Outlook oder Outlook im Web wechseln, um diese als Gruppe zu senden, indem Sie die Gruppen-e-Mail-Adresse dem Feld **von** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e3278-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="e3278-126">Erstellen von Klassifikationen für Office-Gruppen in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="e3278-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="e3278-127">Sie können Klassifikationen erstellen, die von den Benutzern in Ihrer Organisation beim Erstellen einer Office 365-Gruppe festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="e3278-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="e3278-128">Sie können beispielsweise Benutzern das Festlegen von "Standard", "Secret" und "Top Secret" in von Ihnen erstellten Gruppen gestatten.</span><span class="sxs-lookup"><span data-stu-id="e3278-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="e3278-129">Gruppen Klassifikationen werden nicht standardmäßig festgelegt, und Sie müssen Sie erstellen, damit Ihre Benutzer Sie festlegen können.</span><span class="sxs-lookup"><span data-stu-id="e3278-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="e3278-130">Verwenden Sie Azure Active Directory PowerShell, um Ihre Benutzer auf die Verwendungsrichtlinien Ihrer Organisation für Office 365-Gruppen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e3278-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="e3278-131">Sehen Sie sich die [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) an, und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** aus, um die Klassifizierung für Office 365-Gruppen zu definieren.</span><span class="sxs-lookup"><span data-stu-id="e3278-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="e3278-132">Um jeder Klassifizierung eine Beschreibung zuzuordnen, können Sie das Einstellungs Attribut *ClassificationDescriptions* verwenden, um zu definieren.</span><span class="sxs-lookup"><span data-stu-id="e3278-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="e3278-133">wobei die Klassifizierung mit den Zeichenfolgen in der Classificationlist übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="e3278-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="e3278-134">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e3278-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="e3278-135">Nachdem Sie das obige Azure Active Directory-Cmdlet ausgeführt haben, um die Klassifizierung festzulegen, führen Sie das Cmdlet [Set-Unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) aus, wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="e3278-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="e3278-136">Oder erstellen Sie eine neue Gruppe mit einer Klassifizierung.</span><span class="sxs-lookup"><span data-stu-id="e3278-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="e3278-137">Weitere Informationen zur Verwendung von Exchange Online PowerShell finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) und [Herstellen einer Verbindung mit Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="e3278-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="e3278-138">Sobald diese Einstellungen aktiviert sind, kann der Gruppenbesitzer eine Klassifizierung aus dem Dropdownmenü in Outlook im Web und Outlook auswählen und auf der Seite Gruppe **Bearbeiten** speichern.</span><span class="sxs-lookup"><span data-stu-id="e3278-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Wählen Sie Office 365 Group Classification aus.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="e3278-140">Ausblenden von Office 365-Gruppen aus GAL</span><span class="sxs-lookup"><span data-stu-id="e3278-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="e3278-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-141"></span></span>

<span data-ttu-id="e3278-142">Sie können angeben, ob eine Office 365-Gruppe in der globalen Adressliste (GAL) und anderen Listen in Ihrer Organisation angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3278-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="e3278-143">Wenn Sie beispielsweise über eine Gruppe von Rechtsabteilungen verfügen, die Sie nicht in der Adressliste anzeigen möchten, können Sie verhindern, dass die Gruppe in der GAL angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3278-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="e3278-144">Führen Sie das Cmdlet Set-Unified Group aus, um die Gruppe aus der Adressliste wie folgt auszublenden:</span><span class="sxs-lookup"><span data-stu-id="e3278-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="e3278-145">Nur internen Benutzern das Senden von Nachrichten an die Office 365-Gruppe geStatten</span><span class="sxs-lookup"><span data-stu-id="e3278-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="e3278-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-146"></span></span>

<span data-ttu-id="e3278-147">Wenn Sie nicht möchten, dass Benutzer aus der anderen Organisation e-Mails an eine Office 365-Gruppe senden, können Sie die Einstellungen für diese Gruppe ändern.</span><span class="sxs-lookup"><span data-stu-id="e3278-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="e3278-148">Nur interne Benutzer können eine e-Mail an Ihre Gruppe senden.</span><span class="sxs-lookup"><span data-stu-id="e3278-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="e3278-149">Wenn der externe Benutzer versucht, eine Nachricht an diese Gruppe zu senden, wird er abgelehnt.</span><span class="sxs-lookup"><span data-stu-id="e3278-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="e3278-150">Führen Sie das Cmdlet Set-Unifiedgroup aus, um diese Einstellung wie folgt zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="e3278-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="e3278-151">Hinzufügen von e-Mail-Infos zu Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="e3278-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="e3278-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-152"></span></span>

<span data-ttu-id="e3278-153">Immer wenn ein Absender versucht, eine e-Mail an eine Office 365-Gruppe zu senden, kann Ihnen ein QuickInfo angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3278-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="e3278-154">Führen Sie das Cmdlet Set-Unified Group aus, um der Gruppe ein QuickInfo hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e3278-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="e3278-155">Zusammen mit QuickInfo können Sie auch MailTipTranslations festlegen, der zusätzliche Sprachen für die QuickInfo angibt.</span><span class="sxs-lookup"><span data-stu-id="e3278-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="e3278-156">Angenommen, Sie möchten die spanische Übersetzung haben, und führen Sie dann den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="e3278-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="e3278-157">Ändern des Anzeigenamens der Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="e3278-158">Anzeigename gibt den Namen der Office 365-Gruppe an.</span><span class="sxs-lookup"><span data-stu-id="e3278-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="e3278-159">Dieser Name wird in Ihrem Exchange Admin Center oder Office 365 Admin Portal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e3278-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="e3278-160">Sie können den Anzeigenamen der Gruppe bearbeiten oder einer vorhandenen Office 365-Gruppe einen Anzeigenamen zuweisen, indem Sie den Befehl Set-Unifiedgroup ausführen:</span><span class="sxs-lookup"><span data-stu-id="e3278-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="e3278-161">Ändern der Standardeinstellung von Office 365-Gruppen für Outlook in öffentlich oder privat</span><span class="sxs-lookup"><span data-stu-id="e3278-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="e3278-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e3278-162"></span></span>

<span data-ttu-id="e3278-163">Office 365-Gruppen in Outlook werden standardmäßig als privat erstellt.</span><span class="sxs-lookup"><span data-stu-id="e3278-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="e3278-164">Wenn Ihre Organisation Office 365-Gruppen standardmäßig als öffentlich (oder zurück zu privat) erstellen soll, verwenden Sie die folgende PowerShell-Cmdlet-Syntax:</span><span class="sxs-lookup"><span data-stu-id="e3278-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="e3278-165">So legen Sie den Wert auf private fest</span><span class="sxs-lookup"><span data-stu-id="e3278-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="e3278-166">So überprüfen Sie die Einstellung:</span><span class="sxs-lookup"><span data-stu-id="e3278-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="e3278-167">Weitere Informationen finden Sie unter [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) und [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="e3278-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="e3278-168">Cmdlets für Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="e3278-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="e3278-169">Die folgenden Cmdlets können mit Office 365-Gruppen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3278-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="e3278-170">**Name des Cmdlets**</span><span class="sxs-lookup"><span data-stu-id="e3278-170">**Cmdlet name**</span></span>|<span data-ttu-id="e3278-171">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="e3278-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="e3278-172">Get-Unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="e3278-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="e3278-173">Verwenden Sie dieses Cmdlet zum Nachschlagen vorhandener Office 365-Gruppen und zum Anzeigen der Eigenschaften des Group-Objekts.</span><span class="sxs-lookup"><span data-stu-id="e3278-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="e3278-174">Set-Unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="e3278-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="e3278-175">Aktualisieren der Eigenschaften einer bestimmten Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e3278-176">New-Unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="e3278-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="e3278-177">Erstellen Sie eine neue Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="e3278-177">Create a new Office 365 group.</span></span> <span data-ttu-id="e3278-178">Dieses Cmdlet bietet einen minimalen Satz von Parametern, um Werte für erweiterte Eigenschaften festZulegen, die Set-Unifiedgroup nach dem Erstellen der neuen Gruppe verwenden.</span><span class="sxs-lookup"><span data-stu-id="e3278-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="e3278-179">Remove-Unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="e3278-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="e3278-180">Löschen einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e3278-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e3278-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="e3278-182">Abrufen von Mitgliedschafts-und Besitzerinformationen für eine Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e3278-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e3278-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="e3278-184">Hinzufügen von hundert oder Tausenden von Benutzern oder neuen Besitzern zu einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e3278-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e3278-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="e3278-186">Entfernen von Besitzern und Mitgliedern aus einer vorhandenen Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e3278-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e3278-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="e3278-188">Wird verwendet, um Informationen zu dem Benutzer Foto anzuzeigen, das einem Konto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e3278-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="e3278-189">Benutzer Fotos werden in Active Directory gespeichert</span><span class="sxs-lookup"><span data-stu-id="e3278-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e3278-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e3278-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="e3278-191">Wird verwendet, um einem Benutzer Foto ein Konto zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="e3278-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="e3278-192">Benutzer Fotos werden in Active Directory gespeichert</span><span class="sxs-lookup"><span data-stu-id="e3278-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e3278-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e3278-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="e3278-194">Entfernen des Fotos für eine Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="e3278-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="e3278-195">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e3278-195">Related topics</span></span>

[<span data-ttu-id="e3278-196">Upgrade von Verteilerlisten auf Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="e3278-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="e3278-197">Verwalten der Benutzer, die Office 365-Gruppen erstellen können</span><span class="sxs-lookup"><span data-stu-id="e3278-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="e3278-198">Verwalten des Gastzugriffs auf Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="e3278-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="e3278-199">Ändern der statischen Gruppenmitgliedschaft in "Dynamic" in</span><span class="sxs-lookup"><span data-stu-id="e3278-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
