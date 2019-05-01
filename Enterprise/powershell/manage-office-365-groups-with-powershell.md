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
# <a name="manage-office-365-groups-with-powershell"></a>Verwalten von Office 365-Gruppen mit PowerShell

 *Letzte Aktualisierung 18 April, 2018* 
  
Dieser Artikel enthält die Schritte zum Ausführen allgemeiner Verwaltungsaufgaben für Gruppen in Microsoft PowerShell. Außerdem werden die PowerShell-Cmdlets für Gruppen aufgelistet. Weitere Informationen zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von SharePoint Online-Websites mithilfe von PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Link zu Ihren Office 365-Gruppen Nutzungsrichtlinien
<a name="BK_LinkToGuideLines"> </a>

Wenn Benutzer [eine Gruppe in Outlook erstellen oder bearbeiten](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), können Sie Ihnen einen Link zu den Nutzungsrichtlinien Ihrer Organisation anzeigen. Wenn Sie beispielsweise ein bestimmtes Präfix oder Suffix für einen Gruppennamen hinzufügen möchten.
  
Verwenden Sie die Azure Active Directory PowerShell, um Ihre Benutzer auf die Nutzungsrichtlinien Ihrer Organisation für Office 365-Gruppen zu verweisen. Sehen Sie sich die [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://go.microsoft.com/fwlink/?LinkID=827484) an, und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** aus, um den Hyperlink Verwendungsrichtlinie zu definieren. Nachdem Sie das AAD-Cmdlet ausgeführt haben, werden dem Benutzer beim Erstellen oder Bearbeiten einer Gruppe in Outlook der Link zu ihren Richtlinien angezeigt. 
  
![Erstellen einer neuen Gruppe mit dem Link "Verwendungsrichtlinien"](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Klicken Sie auf Gruppen Nutzungsrichtlinien, um die Richtlinien für ihre Organisationen in Office 365 zu sehen.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Zulassen, dass Benutzer als Office 365-Gruppe senden
<a name="BK_LinkToGuideLines"> </a>
  
Wenn Sie möchten, dass Ihre Office 365-Gruppen "Senden als" aktivieren, verwenden Sie die Cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) und [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) , um dies zu konfigurieren. Nachdem Sie diese Einstellung aktiviert haben, können Benutzer von Office 365-Gruppen Outlook oder Outlook im Web verwenden, um e-Mails als Office 365-Gruppe zu senden und zu beantworten. Benutzer können zur Gruppe wechseln, eine neue e-Mail erstellen und das Feld "Senden als" in die e-Mail-Adresse der Gruppe ändern. 

([Sie können dies auch im Exchange Admin Center tun](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)
  
Verwenden Sie das folgende Skript, * \<und\> * ersetzen Sie GroupAlias durch den Alias der Gruppe, die Sie aktualisieren möchten, und * \<useraliascontoso\johndoe\> * mit dem Alias des Benutzers, dem Sie permssions erteilen möchten. Stellen Sie [eine Verbindung mit Exchange Online PowerShell her](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) , um dieses Skript auszuführen.

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Nachdem das Cmdlet ausgeführt wurde, können Benutzer zu Outlook oder Outlook im Web wechseln, um diese als Gruppe zu senden, indem Sie die Gruppen-e-Mail-Adresse dem Feld **von** hinzufügen. 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>Erstellen von Klassifikationen für Office-Gruppen in Ihrer Organisation

Sie können Klassifikationen erstellen, die von den Benutzern in Ihrer Organisation beim Erstellen einer Office 365-Gruppe festgelegt werden können. Sie können beispielsweise Benutzern das Festlegen von "Standard", "Secret" und "Top Secret" in von Ihnen erstellten Gruppen gestatten. Gruppen Klassifikationen werden nicht standardmäßig festgelegt, und Sie müssen Sie erstellen, damit Ihre Benutzer Sie festlegen können. Verwenden Sie Azure Active Directory PowerShell, um Ihre Benutzer auf die Verwendungsrichtlinien Ihrer Organisation für Office 365-Gruppen zu verweisen.
  
Sehen Sie sich die [Azure Active Directory-Cmdlets zum Konfigurieren von Gruppeneinstellungen](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) an, und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** aus, um die Klassifizierung für Office 365-Gruppen zu definieren. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Um jeder Klassifizierung eine Beschreibung zuzuordnen, können Sie das Einstellungs Attribut *ClassificationDescriptions* verwenden, um zu definieren.
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

wobei die Klassifizierung mit den Zeichenfolgen in der Classificationlist übereinstimmt.

Beispiel:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Nachdem Sie das obige Azure Active Directory-Cmdlet ausgeführt haben, um die Klassifizierung festzulegen, führen Sie das Cmdlet [Set-Unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) aus, wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Oder erstellen Sie eine neue Gruppe mit einer Klassifizierung.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Weitere Informationen zur Verwendung von Exchange Online PowerShell finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) und [Herstellen einer Verbindung mit Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 
  
Sobald diese Einstellungen aktiviert sind, kann der Gruppenbesitzer eine Klassifizierung aus dem Dropdownmenü in Outlook im Web und Outlook auswählen und auf der Seite Gruppe **Bearbeiten** speichern. 
  
![Wählen Sie Office 365 Group Classification aus.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Ausblenden von Office 365-Gruppen aus GAL
<a name="BKMK_CreateClassification"> </a>

Sie können angeben, ob eine Office 365-Gruppe in der globalen Adressliste (GAL) und anderen Listen in Ihrer Organisation angezeigt werden soll. Wenn Sie beispielsweise über eine Gruppe von Rechtsabteilungen verfügen, die Sie nicht in der Adressliste anzeigen möchten, können Sie verhindern, dass die Gruppe in der GAL angezeigt wird. Führen Sie das Cmdlet Set-Unified Group aus, um die Gruppe aus der Adressliste wie folgt auszublenden:
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Nur internen Benutzern das Senden von Nachrichten an die Office 365-Gruppe geStatten
<a name="BKMK_CreateClassification"> </a>

Wenn Sie nicht möchten, dass Benutzer aus der anderen Organisation e-Mails an eine Office 365-Gruppe senden, können Sie die Einstellungen für diese Gruppe ändern. Nur interne Benutzer können eine e-Mail an Ihre Gruppe senden. Wenn der externe Benutzer versucht, eine Nachricht an diese Gruppe zu senden, wird er abgelehnt.
  
Führen Sie das Cmdlet Set-Unifiedgroup aus, um diese Einstellung wie folgt zu aktualisieren:

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Hinzufügen von e-Mail-Infos zu Office 365-Gruppen
<a name="BKMK_CreateClassification"> </a>

Immer wenn ein Absender versucht, eine e-Mail an eine Office 365-Gruppe zu senden, kann Ihnen ein QuickInfo angezeigt werden.
  
Führen Sie das Cmdlet Set-Unified Group aus, um der Gruppe ein QuickInfo hinzuzufügen:

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Zusammen mit QuickInfo können Sie auch MailTipTranslations festlegen, der zusätzliche Sprachen für die QuickInfo angibt. Angenommen, Sie möchten die spanische Übersetzung haben, und führen Sie dann den folgenden Befehl aus:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Ändern des Anzeigenamens der Office 365-Gruppe

Anzeigename gibt den Namen der Office 365-Gruppe an. Dieser Name wird in Ihrem Exchange Admin Center oder Office 365 Admin Portal angezeigt. Sie können den Anzeigenamen der Gruppe bearbeiten oder einer vorhandenen Office 365-Gruppe einen Anzeigenamen zuweisen, indem Sie den Befehl Set-Unifiedgroup ausführen:

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Ändern der Standardeinstellung von Office 365-Gruppen für Outlook in öffentlich oder privat
<a name="BKMK_CreateClassification"> </a>

Office 365-Gruppen in Outlook werden standardmäßig als privat erstellt. Wenn Ihre Organisation Office 365-Gruppen standardmäßig als öffentlich (oder zurück zu privat) erstellen soll, verwenden Sie die folgende PowerShell-Cmdlet-Syntax:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
So legen Sie den Wert auf private fest
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
So überprüfen Sie die Einstellung: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Weitere Informationen finden Sie unter [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) und [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets für Office 365-Gruppen

Die folgenden Cmdlets können mit Office 365-Gruppen verwendet werden.
  
|**Name des Cmdlets**|**Beschreibung**|
|:-----|:-----|
|[Get-Unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Verwenden Sie dieses Cmdlet zum Nachschlagen vorhandener Office 365-Gruppen und zum Anzeigen der Eigenschaften des Group-Objekts.  <br/> |
|[Set-Unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Aktualisieren der Eigenschaften einer bestimmten Office 365-Gruppe  <br/> |
|[New-Unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Erstellen Sie eine neue Office 365-Gruppe. Dieses Cmdlet bietet einen minimalen Satz von Parametern, um Werte für erweiterte Eigenschaften festZulegen, die Set-Unifiedgroup nach dem Erstellen der neuen Gruppe verwenden.  <br/> |
|[Remove-Unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Löschen einer vorhandenen Office 365-Gruppe  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Abrufen von Mitgliedschafts-und Besitzerinformationen für eine Office 365-Gruppe  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Hinzufügen von hundert oder Tausenden von Benutzern oder neuen Besitzern zu einer vorhandenen Office 365-Gruppe  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Entfernen von Besitzern und Mitgliedern aus einer vorhandenen Office 365-Gruppe  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Wird verwendet, um Informationen zu dem Benutzer Foto anzuzeigen, das einem Konto zugeordnet ist. Benutzer Fotos werden in Active Directory gespeichert  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Wird verwendet, um einem Benutzer Foto ein Konto zuzuordnen. Benutzer Fotos werden in Active Directory gespeichert  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Entfernen des Fotos für eine Office 365-Gruppe  <br/> |

## <a name="related-topics"></a>Verwandte Themen

[Upgrade von Verteilerlisten auf Office 365-Gruppen](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Verwalten der Benutzer, die Office 365-Gruppen erstellen können](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Verwalten des Gastzugriffs auf Office 365-Gruppen](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Ändern der statischen Gruppenmitgliedschaft in "Dynamic" in](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
