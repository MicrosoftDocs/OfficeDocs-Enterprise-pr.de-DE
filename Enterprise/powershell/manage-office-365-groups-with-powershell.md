---
title: Verwalten von Microsoft 365-Gruppen mit PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: In diesem Artikel erfahren Sie, wie Sie allgemeine Verwaltungsaufgaben für Microsoft 365-Gruppen in PowerShell ausführen.
ms.openlocfilehash: 899205fbf53821758f848fd4e1c75f25fd16e223
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605951"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a><span data-ttu-id="014c7-103">Verwalten von Microsoft 365-Gruppen mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="014c7-103">Manage Microsoft 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="014c7-104">*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="014c7-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="014c7-105">In diesem Artikel werden die Schritte zum Ausführen häufiger Verwaltungsaufgaben für Gruppen in Microsoft PowerShell beschrieben.</span><span class="sxs-lookup"><span data-stu-id="014c7-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="014c7-106">Zudem sind die PowerShell-Cmdlets für Gruppen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="014c7-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="014c7-107">Informationen zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von SharePoint Online-Websites mithilfe von PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="014c7-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a><span data-ttu-id="014c7-108">Link zu Ihren Microsoft 365-Gruppen-Nutzungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="014c7-108">Link to your Microsoft 365 Groups usage guidelines</span></span>
<span data-ttu-id="014c7-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-109"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="014c7-110">Wenn Benutzer [eine Gruppe in Outlook erstellen oder bearbeiten](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), können Sie über einen Link auf die Nutzungsrichtlinien Ihrer Organisation verweisen.</span><span class="sxs-lookup"><span data-stu-id="014c7-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="014c7-111">Angenommen, einem Gruppennamen muss ein spezielles Präfix oder Suffix hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="014c7-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="014c7-112">Verwenden Sie die Azure Active Directory (Azure AD) PowerShell, um Ihre Benutzer auf die Verwendungsrichtlinien Ihrer Organisation für Microsoft 365-Gruppen zu richten.</span><span class="sxs-lookup"><span data-stu-id="014c7-112">Use the Azure Active Directory (Azure AD) PowerShell to point your users to your organization's usage guidelines for Microsoft 365 groups.</span></span> <span data-ttu-id="014c7-113">Lesen Sie [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://go.microsoft.com/fwlink/?LinkID=827484), und führen Sie die Schritte unter **Erstellen von Einstellungen auf Verzeichnisebene** aus, um den Link zu den Nutzungsrichtlinien zu definieren.</span><span class="sxs-lookup"><span data-stu-id="014c7-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="014c7-114">Nachdem Sie das AAD-Cmdlet ausgeführt haben, wird den Benutzern beim Erstellen oder Bearbeiten einer Gruppe in Outlook der Link zu Ihren Richtlinien angezeigt.</span><span class="sxs-lookup"><span data-stu-id="014c7-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Eine neue Gruppe mit Link zu Nutzungsrichtlinien erstellen](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Auf "Gruppennutzungsrichtlinien" klicken, um die Office 365-Gruppenrichtlinien Ihrer Organisation anzuzeigen](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-microsoft-365-group"></a><span data-ttu-id="014c7-117">Zulassen, dass Benutzer als Microsoft 365-Gruppe senden</span><span class="sxs-lookup"><span data-stu-id="014c7-117">Allow users to Send as the Microsoft 365 Group</span></span>
<span data-ttu-id="014c7-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-118"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="014c7-119">Wenn Sie möchten, dass Ihre Microsoft 365-Gruppen "Senden als" aktivieren, verwenden Sie die Cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) und [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) , um dies zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="014c7-119">If you want to enable your Microsoft 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="014c7-120">Nachdem Sie diese Einstellung aktiviert haben, können Benutzer von Microsoft 365 Gruppe Outlook oder Outlook im Internet verwenden, um e-Mails als Microsoft 365-Gruppe zu senden und zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="014c7-120">Once you enable this setting, Microsoft 365 group users can use Outlook or Outlook on the web to send and reply to email as the Microsoft 365 group.</span></span> <span data-ttu-id="014c7-121">Benutzer können zur Gruppe wechseln, eine neue E-Mail erstellen und das Feld "Senden als" in die E-Mail-Adresse der Gruppe ändern.</span><span class="sxs-lookup"><span data-stu-id="014c7-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="014c7-122">([Sie können diesen Schritt auch im Exchange Admin Center ausführen](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="014c7-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="014c7-123">Verwenden Sie das folgende Skript, *\<GroupAlias\>* und ersetzen Sie durch den Alias der Gruppe, die Sie aktualisieren möchten, und *\<UserAlias\>* mit dem Alias des Benutzers, dem Sie Berechtigungen erteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="014c7-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="014c7-124">[Stellen Sie eine Verbindung mit Exchange Online PowerShell her](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell), um das Skript auszuführen.</span><span class="sxs-lookup"><span data-stu-id="014c7-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="014c7-125">Sobald das Cmdlet ausgeführt wurde, können Benutzer zu Outlook oder Outlook im Web wechseln und als Gruppe senden, indem sie die E-Mail-Adresse der Gruppe zum Feld **Von** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="014c7-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="014c7-126">Erstellen von Klassifizierungen für Office-Gruppen in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="014c7-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="014c7-127">Sie können Sensitivitäts Bezeichnungen erstellen, die die Benutzer in Ihrer Organisation festlegen können, wenn Sie eine Microsoft 365-Gruppe erstellen.</span><span class="sxs-lookup"><span data-stu-id="014c7-127">You can create sensitivity labels that the users in your organization can set when they create a Microsoft 365 Group.</span></span> <span data-ttu-id="014c7-128">Wenn Sie Gruppen klassifizieren möchten, empfehlen wir die Verwendung von Sensitivitäts Bezeichnungen anstelle des vorherigen Gruppen Klassifizierungs Features.</span><span class="sxs-lookup"><span data-stu-id="014c7-128">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="014c7-129">Informationen zur Verwendung von Sensitivitäts Bezeichnungen finden Sie unter [use Sensitivity Labels to Protect Content in Microsoft Teams, Microsoft 365 Groups und SharePoint Sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span><span class="sxs-lookup"><span data-stu-id="014c7-129">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="014c7-130">Wenn Sie derzeit Klassifizierungs Bezeichnungen verwenden, stehen diese nicht mehr für Benutzer zur Verfügung, die Gruppen erstellen, sobald die Vertraulichkeits Bezeichnungen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="014c7-130">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="014c7-131">Sie können weiterhin das vorherige Gruppen Klassifizierungs Feature verwenden.</span><span class="sxs-lookup"><span data-stu-id="014c7-131">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="014c7-132">Sie können Klassifizierungen erstellen, die von den Benutzern in Ihrer Organisation beim Erstellen einer Office 365-Gruppe festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="014c7-132">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="014c7-133">Beispielsweise können Sie den Benutzern gestatten, die Klassifizierungen "Standard", "Geheim" und "Streng geheim" für erstellte Gruppen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="014c7-133">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="014c7-134">Gruppenklassifizierungen sind nicht standardmäßig festgelegt, und Sie müssen diese erstellen, damit sie von den Benutzern festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="014c7-134">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="014c7-135">Verwenden Sie Azure Active Directory PowerShell, um die Benutzer auf die Nutzungsrichtlinien Ihrer Organisation für Office 365-Gruppen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="014c7-135">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="014c7-136">Lesen Sie [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets), und führen Sie die Schritte unter **Erstellen von Einstellungen auf Verzeichnisebene** aus, um die Klassifizierung für Office 365-Gruppen zu definieren.</span><span class="sxs-lookup"><span data-stu-id="014c7-136">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="014c7-137">Mit dem settings-Attribut *ClassificationDescriptions* können Sie jeder Klassifizierung eine Beschreibung zuordnen.</span><span class="sxs-lookup"><span data-stu-id="014c7-137">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="014c7-138">wobei die Klassifizierung mit den Zeichenfolgen in der ClassificationList übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="014c7-138">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="014c7-139">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="014c7-139">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="014c7-140">Führen Sie nach dem oben genannten Azure Active Directory-Cmdlet zum Festlegen der Klassifizierung das Cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) aus, wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="014c7-140">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="014c7-141">Sie können auch eine neue Gruppe mit einer Klassifizierung erstellen.</span><span class="sxs-lookup"><span data-stu-id="014c7-141">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="014c7-142">Weitere Informationen zur Verwendung von Exchange Online PowerShell finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) und [Herstellen einer Verbindung mit Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="014c7-142">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="014c7-143">Sobald diese Einstellungen aktiviert sind, kann der Gruppenbesitzer eine Klassifizierung aus dem Dropdownmenü in Outlook im Web und Outlook auswählen und sie aus der Gruppenseite **Bearbeiten** speichern.</span><span class="sxs-lookup"><span data-stu-id="014c7-143">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365-Gruppenklassifizierung auswählen](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="014c7-145">Ausblenden von Office 365-Gruppen aus der globalen Adressliste</span><span class="sxs-lookup"><span data-stu-id="014c7-145">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="014c7-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-146"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="014c7-147">Sie können angeben, ob eine Office 365 Gruppe in der globalen Adressliste (GAL) und anderen Listen in Ihrer Organisation angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="014c7-147">You can specify whether an Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="014c7-148">Wenn beispielsweise eine Gruppe der Rechtsabteilung nicht in der Adressliste angezeigt werden soll, können Sie diese Gruppe aus der globalen Adressliste ausblenden.</span><span class="sxs-lookup"><span data-stu-id="014c7-148">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="014c7-149">Führen Sie das Cmdlet "Set-UnifiedGroup" wie folgt aus, um die Gruppe in der Adressliste auszublenden:</span><span class="sxs-lookup"><span data-stu-id="014c7-149">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="014c7-150">Nur internen Benutzern erlauben, Nachrichten an die Office 365-Gruppe zu senden</span><span class="sxs-lookup"><span data-stu-id="014c7-150">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="014c7-151"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-151"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="014c7-152">Wenn Sie nicht möchten, dass Benutzer aus anderen Organisationen e-Mails an eine Office 365 Gruppe senden, können Sie die Einstellungen für diese Gruppe ändern.</span><span class="sxs-lookup"><span data-stu-id="014c7-152">If you don't want users from other organization to send email to an Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="014c7-153">So können nur interne Benutzer E-Mail-Nachrichten an Ihre Gruppe senden.</span><span class="sxs-lookup"><span data-stu-id="014c7-153">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="014c7-154">Wenn externe Benutzer versuchen, eine Nachricht an diese Gruppe zu senden, wird diese zurückgewiesen.</span><span class="sxs-lookup"><span data-stu-id="014c7-154">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="014c7-155">Führen Sie das Cmdlet "Set-UnifiedGroup" wie folgt aus, um diese Einstellung zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="014c7-155">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="014c7-156">Hinzufügen von E-Mail-Infos zu den Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="014c7-156">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="014c7-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-157"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="014c7-158">Immer wenn ein Absender versucht, eine E-Mail an eine Office 365-Gruppe zu senden, kann eine E-Mail-Info angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="014c7-158">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="014c7-159">Führen Sie das Cmdlet "Set-UnifiedGroup" aus, um eine E-Mail-Info zur Gruppe hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="014c7-159">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="014c7-160">Neben einer E-Mail-Info können Sie auch "MailTipTranslations" festlegen, wodurch zusätzliche Sprachen für die E-Mail-Info festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="014c7-160">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="014c7-161">Angenommen Sie, Sie möchten die spanische Übersetzung verwenden, dann führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="014c7-161">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="014c7-162">Ändern des Anzeigenamens der Office 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="014c7-162">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="014c7-163">Der Anzeigename gibt den Namen der Office 365-Gruppe an.</span><span class="sxs-lookup"><span data-stu-id="014c7-163">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="014c7-164">Sie können diesen Namen in Ihrem Exchange Admin Center oder Microsoft 365 Admin Center sehen.</span><span class="sxs-lookup"><span data-stu-id="014c7-164">You can see this name in your exchange admin center or Microsoft 365 admin center.</span></span> <span data-ttu-id="014c7-165">Sie können den Anzeigenamen der Gruppe bearbeiten oder einer vorhandenen Office 365-Gruppe einen Anzeigenamen zuweisen, indem Sie den Befehl "Set-UnifiedGroup" ausführen:</span><span class="sxs-lookup"><span data-stu-id="014c7-165">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="014c7-166">Ändern der Standardeinstellung von Office 365-Gruppen für Outlook auf "Öffentlich" oder "Privat"</span><span class="sxs-lookup"><span data-stu-id="014c7-166">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="014c7-167"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="014c7-167"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="014c7-168">Office 365-Gruppen in Outlook werden standardmäßig als private Gruppen erstellt.</span><span class="sxs-lookup"><span data-stu-id="014c7-168">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="014c7-169">Wenn Office 365-Gruppen in Ihrer Organisation standardmäßig als öffentliche (oder wieder als private) Gruppen erstellt werden sollen, verwenden Sie die folgende Syntax für das PowerShell-Cmdlet:</span><span class="sxs-lookup"><span data-stu-id="014c7-169">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="014c7-170">So legen Sie die Einstellung auf "Privat" fest:</span><span class="sxs-lookup"><span data-stu-id="014c7-170">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="014c7-171">So überprüfen Sie die Einstellung:</span><span class="sxs-lookup"><span data-stu-id="014c7-171">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="014c7-172">Weitere Informationen hierzu finden Sie unter [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) und [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="014c7-172">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="014c7-173">Cmdlets für Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="014c7-173">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="014c7-174">Die folgenden Cmdlets können mit Office 365-Gruppen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="014c7-174">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="014c7-175">**Name des Cmdlets**</span><span class="sxs-lookup"><span data-stu-id="014c7-175">**Cmdlet name**</span></span>|<span data-ttu-id="014c7-176">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="014c7-176">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="014c7-177">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="014c7-177">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="014c7-178">Verwenden Sie dieses Cmdlet, um vorhandene Office 365-Gruppen nachzuschlagen und Eigenschaften des Gruppenobjekts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="014c7-178">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="014c7-179">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="014c7-179">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="014c7-180">Aktualisiert die Eigenschaften einer bestimmten Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="014c7-180">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="014c7-181">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="014c7-181">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="014c7-182">Erstellen einer neuen Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="014c7-182">Create a new Office 365 group.</span></span> <span data-ttu-id="014c7-183">Dieses Cmdlet bietet einen minimalen Satz von Parametern zum Festlegen von Werten für erweiterte Eigenschaften. Verwenden Sie nach dem Erstellen der neuen Gruppe "Set-UnifiedGroup".</span><span class="sxs-lookup"><span data-stu-id="014c7-183">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="014c7-184">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="014c7-184">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="014c7-185">Löscht eine vorhandene Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="014c7-185">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="014c7-186">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="014c7-186">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="014c7-187">Ruft Mitgliedschafts- und Besitzerinformationen für eine Office 365-Gruppe ab.</span><span class="sxs-lookup"><span data-stu-id="014c7-187">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="014c7-188">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="014c7-188">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="014c7-189">Fügt Hunderte oder Tausende von Benutzern oder neuen Besitzern zu einer vorhandenen Office 365-Gruppe hinzu.</span><span class="sxs-lookup"><span data-stu-id="014c7-189">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="014c7-190">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="014c7-190">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="014c7-191">Entfernt Besitzer und Mitglieder aus einer vorhandenen Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="014c7-191">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="014c7-192">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="014c7-192">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="014c7-193">Wird verwendet, um Informationen zu dem Benutzerfoto abzurufen, das mit einem Konto verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="014c7-193">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="014c7-194">Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="014c7-194">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="014c7-195">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="014c7-195">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="014c7-196">Wird verwendet, um ein Benutzerfoto mit einem Konto zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="014c7-196">Used to associate a user photo with an account.</span></span> <span data-ttu-id="014c7-197">Benutzerfotos werden in Active Directory gespeichert.</span><span class="sxs-lookup"><span data-stu-id="014c7-197">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="014c7-198">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="014c7-198">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="014c7-199">Entfernt das Foto für eine Office 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="014c7-199">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="014c7-200">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="014c7-200">Related topics</span></span>

[<span data-ttu-id="014c7-201">Upgraden von Verteilerlisten zu Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="014c7-201">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="014c7-202">Verwalten von Personen, die Office 365-Gruppen erstellen können</span><span class="sxs-lookup"><span data-stu-id="014c7-202">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="014c7-203">Verwalten des Gastzugriffs auf Office 365-Gruppen</span><span class="sxs-lookup"><span data-stu-id="014c7-203">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="014c7-204">Ändern der statischen Gruppenmitgliedschaft in „Dynamisch“</span><span class="sxs-lookup"><span data-stu-id="014c7-204">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
