---
title: Verwalten von Office 365-Gruppen mit PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
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
description: In diesem Artikel werden die Schritte für allgemeine Verwaltungsaufgaben für Gruppen in Microsoft PowerShell ausführen.
ms.openlocfilehash: 83b7340cea1fd8d38bba073353b61f0b17fad8a0
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741228"
---
# <a name="manage-office-365-groups-with-powershell"></a>Verwalten von Office 365-Gruppen mit PowerShell

 *Letzte aktualisierte 18-April, 2018* 
  
In diesem Artikel werden die Schritte für allgemeine Verwaltungsaufgaben für Gruppen in Microsoft PowerShell ausführen. Außerdem werden die PowerShell-Cmdlets für Gruppen aufgelistet. Info zum Verwalten von SharePoint-Websites finden Sie unter [Verwalten von SharePoint Online-Websites mithilfe von PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Allgemeine Aufgaben zum Verwalten von Office 365-Gruppen

- [Upgrade Verteilerlisten zu Office 365-Gruppen](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [Verwalten von Personen, die Office 365-Gruppen erstellen können](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [Verwalten des Gastzugriffs auf Office 365-Gruppen](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [Verwalten von Gruppen dynamisch in Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Fügen Sie Hunderte oder Tausende von Benutzern zu Office 365-Gruppen hinzu, verwenden Sie das [Cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Link zu Ihrer Richtlinien für die Verwendung von Office 365-Gruppen
<a name="BK_LinkToGuideLines"> </a>

Wenn können Benutzer [Erstellen oder bearbeiten eine Gruppe in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), Sie sie einen Link zu Richtlinien für die Verwendung Ihrer Organisation anzeigen. Angenommen, Sie benötigen ein spezielles Präfix oder suffix, das auf den Namen einer Gruppe hinzugefügt werden soll.
  
Verwenden Sie die Benutzer Ihrer Organisation Verwendungsrichtlinien für für Office 365-Gruppen auf Azure Active Directory PowerShell. Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://go.microsoft.com/fwlink/?LinkID=827484) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** auf den Verwendung Leitlinie Hyperlink definieren möchten. Einmal führen Sie das Cmdlet AAD des Benutzers sehen Sie, den Link, um Ihre Richtlinien beim Erstellen und bearbeiten Sie eine Gruppe in Outlook. 
  
![Erstellen einer neuen Gruppe durch Verwendung Richtlinien link](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Klicken Sie auf Gruppe Verwendungsrichtlinien für um finden in Ihrem Unternehmen Richtlinien für Office 365-Gruppen](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Zulassen, dass Benutzer senden als der Office 365-Gruppe
<a name="BK_LinkToGuideLines"> </a>

Sie können diese Schritte auch in der Exchange-Verwaltungskonsole durchführen. Finden Sie unter [zulassen, dass Mitglieder "Senden als" oder "Senden im Auftrag von" eine Office 365-Gruppe](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).
  
Wenn Sie Ihre Office 365-Gruppen "Senden als" aktivieren möchten, verwenden Sie die [Add-recipientpermission können](https://go.microsoft.com/fwlink/p/?LinkId=723960) und die Cmdlets [Get-recipientpermission können](https://go.microsoft.com/fwlink/p/?LinkId=733239) , um dies zu konfigurieren. Nachdem Sie diese Einstellung aktivieren, können Office 365-Benutzer Outlook oder Outlook im Web zum Senden und Antworten auf e-Mail, wie die Office 365-Gruppe. Benutzer können wechseln, erstellen eine neue e-Mail-Adresse der Gruppe, und ändern Sie das Feld "Senden als" in e-Mail-Adresse der Gruppe. 
  
> [!NOTE]
> Sie müssen die Gruppe e-Mail-Adresse in das Feld **"Cc"** hinzufügen, beim Verfassen der e-Mails, die "Senden als", damit die Nachricht an die Gruppe gesendet wird und in der Gruppe Unterhaltungen wird angezeigt. 
  
Zu diesem Zeitpunkt ist die einzige Möglichkeit zum Aktualisieren der Postfachrichtlinie [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Verwenden Sie diesen Befehl, um den Gruppenalias festzulegen.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Verwenden Sie diesen Befehl, um den Alias des Benutzers festzulegen.
    
  ```
  $userAlias = "User"
  ```

- Verwenden Sie diesen Befehl, um der Groupalias an das Cmdlet Get-Recipient abzurufenden die Empfänger-Details zu übergeben.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- Klicken Sie dann muss der Empfänger Zielname (Gruppenname) an das Cmdlet Add-recipientpermission können übergeben werden. Die useraliascontoso\johndoe für die die Berechtigung "Sendas" erhält, wird der - Vertrauensnehmerdomäne-Parameter zugewiesen werden.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Sobald das Cmdlet ausgeführt wird, können Benutzer, wie die Gruppe zu senden, indem Sie die Gruppe e-Mail-Adresse in das Feld **aus** Outlook oder Outlook im Web wechseln. 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Erstellen von Klassifikationen für Office-Gruppen in Ihrer Organisation

Sie können Klassifikationen erstellen, die die Benutzer in Ihrer Organisation beim Erstellen einer Gruppe von Office 365 festlegen können. Beispielsweise können Sie Benutzern "Standard", "Geheim" und "Top Secret" Festlegen von für Gruppen, die sie erstellen. Klassifikationen in der Gruppe werden nicht standardmäßig festgelegt, und Sie müssen beim Erstellen, damit Ihre Benutzer festgelegt. Verwenden Sie Azure Active Directory PowerShell, um Ihre Benutzer zu Ihrer Organisation Verwendungsrichtlinien für für Office 365 Gruppen verweisen.
  
Auschecken von [Azure Active Directory-Cmdlets zum Konfigurieren von Einstellungen für die Gruppe](https://go.microsoft.com/fwlink/?LinkID=827484) , und führen Sie die Schritte in den **Einstellungen auf Verzeichnisebene erstellen** die Klassifikation für Office 365 Gruppen definieren. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Eine Beschreibung, die jeder Klassifizierung zuordnen, den Sie verwenden können, um das Attribut der Einstellungen *ClassificationDescriptions* definieren. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Beispiel:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Führen Sie das Cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) nach der Ausführung des oben genannten Azure Active Directory-Cmdlets, um die Klassifikation festzulegen Wenn Sie die Klassifizierung für eine bestimmte Gruppe festlegen möchten. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Oder erstellen Sie eine neue Gruppe mit einer Klassifikation.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Weitere Informationen zur Verwendung von Exchange Online PowerShell finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) und [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415). 
  
Nachdem diese Einstellungen aktiviert sind, werden den Besitzer der Gruppe wählen eine Klassifizierung aus dem Dropdown-Menü in Outlook im Web und Outlook, und speichern Sie es von der Gruppenseite **Bearbeiten** können. 
  
![Wählen Sie Office 365 Gruppe Klassifikation](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Office 365-Gruppen aus der globalen Adressliste ausblenden
<a name="BKMK_CreateClassification"> </a>

Sie können angeben, ob eine Office 365-Gruppe in der globalen Adressliste (GAL) und andere Listen in Ihrer Organisation angezeigt. Wenn Sie eine Gruppe rechtsabteilung, die nicht in der Adressliste angezeigt haben werden sollen, können Sie diese Gruppe aus der Anzeige im GAL beenden. Führen Sie die Gruppe Set-Unified-Cmdlet zum Ausblenden des Gruppe aus der Adressliste wie folgt aus:
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Zulassen, dass nur interne Benutzer Nachricht an Office 365-Gruppe senden
<a name="BKMK_CreateClassification"> </a>

Wenn Sie nicht, dass Benutzer aus einer anderen Organisation zum Senden von e-Mail an eine Gruppe von Office 365 möchten, können Sie die Einstellungen für diese Gruppe ändern. Es können nur interne Benutzer eine e-Mail an Ihre Gruppe senden. Wenn externer Benutzer zum Senden von Nachrichten an diese Gruppe versuchen werden sie abgelehnt.
  
Führen Sie das Set-UnifiedGroup-Cmdlet zum Aktualisieren dieser Einstellung an, wie folgt aus:
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Hinzufügen von e-Mail-Infos zu den Office 365-Gruppen
<a name="BKMK_CreateClassification"> </a>

Wenn der Absender versucht, eine e-Mail an eine Gruppe von Office 365 senden, kann ihm eine e-Mail-Info angezeigt werden.
  
Führen Sie die Gruppe Set-Unified-Cmdlet, um eine e-Mail-Info zur Gruppe hinzufügen möchten:
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Zusammen mit e-Mail-Info können Sie auch festlegen MailTipTranslations, die für zusätzliche Sprachen gibt an, die e-Mail-Info. Angenommen Sie, Sie haben die spanische Übersetzung, und klicken Sie dann den folgenden Befehl ausführen möchten:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Ändern des Anzeigenamens der Gruppe der Office 365

Angezeigter Name Gibt den Namen der Gruppe der Office 365. Dieser Name kann in Ihrer Exchange Admin Center oder o365 Admin-Portal angezeigt werden. Sie können den Anzeigenamen der Gruppe bearbeiten oder einer vorhandenen Office 365-Gruppe einen Anzeigenamen zuweisen, indem Sie Set-UnifiedGroup-Befehl ausführen:
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Verwalten von benutzerfotos in Office 365-Gruppen

|**Name des Cmdlets**|**Beschreibung**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Dient zum Anzeigen von Informationen zum benutzerfoto ein Konto zugeordnet. Benutzerfotos werden in Active Directory gespeichert.  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Verwendet, um ein benutzerfoto mit einem Konto zuzuordnen. Benutzerfotos werden in Active Directory gespeichert.  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Entfernen Sie das Foto für eine Gruppe von Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Ändern Sie die Standardeinstellung der Office 365-Gruppen für Outlook in öffentlich oder privat
<a name="BKMK_CreateClassification"> </a>

Office 365 werden Gruppen in Outlook als privat standardmäßig erstellt werden. Wenn Ihre Organisation Office 365-Gruppen für Outlook können Sie als öffentlich erstellt werden, in der Standardeinstellung (oder auf Private) möchte, verwenden Sie diese Syntax der PowerShell-Cmdlet:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
So legen Sie auf Private fest:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
So überprüfen die Einstellung: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Weitere Informationen finden Sie unter [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) und [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlets für Office 365-Gruppen

Die folgenden Cmdlets wurden kürzlich Office 365 Gruppen zur Verfügung gestellt. Wenn Sie diese verwenden können nicht, hat Ihr Office 365-Abonnement mit dieser Funktionalität noch nicht aktualisiert wurden. Überprüfen Sie Ihre Nachrichtencenter und die [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap).
  
|**Name des Cmdlets**|**Beschreibung**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Verwenden Sie dieses Cmdlet zum Nachschlagen von vorhandenen Office 365-Gruppen, und klicken Sie zum Anzeigen der Eigenschaften des Group-Objekts  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Aktualisieren Sie die Eigenschaften einer bestimmten Gruppe von Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Erstellen einer neuen Office 365-Gruppe an. Dieses Cmdlet bietet einen minimalen Satz von Parametern, für die Einstellung Werte für erweiterte Eigenschaften Set-UnifiedGroup nach dem Erstellen der neuen Gruppe verwenden  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Löschen einer vorhandenen Office 365-Gruppe  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Abrufen von Informationen für Mitgliedschafts- und Besitzer für die Gruppe ein Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Hinzufügen von hundert oder Tausende von Benutzern oder neue Besitzer einer vorhandenen Office 365-Gruppe  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Entfernen Sie Besitzer und Mitglieder aus einer vorhandenen Office 365-Gruppe  <br/> |
   
## <a name="for-more-information"></a>Weitere Informationen

[Verwalten von Office 365 mit Office 365 PowerShell](powershell/manage-office-365-with-office-365-powershell.md)
