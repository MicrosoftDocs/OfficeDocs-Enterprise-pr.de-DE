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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>Verwalten einer isolierten SharePoint Online-Teamwebsite

 **Zusammenfassung:** Mit diesen Verfahren können Sie Ihre isolierte SharePoint Online-Teamwebsite verwalten.
  
In diesem Artikel werden allgemeine Verwaltungsaufgaben für eine isolierte SharePoint Online-Teamwebsite erläutert.
  
## <a name="add-a-new-user"></a>Hinzufügen eines neuen Benutzers

Wenn ein neuer Benutzer der Website beitritt, müssen Sie entscheiden, in welchem Umfang, d. h. mit welcher Berechtigungsstufe, er an der Website teilnehmen soll:
  
- Verwaltung: Fügen Sie das neue Benutzerkonto zur Zugriffsgruppe der Websiteadministratoren hinzu.
    
- Aktive Zusammenarbeit: Fügen Sie das Benutzerkonto zur Zugriffsgruppe der Websitemitglieder hinzu.
    
- Anzeige: Fügen Sie das Benutzerkonto zur Zugriffsgruppe der Websitebetrachter hinzu.
    
Wenn Sie Benutzerkonten und Gruppen über Windows Server Active Directory (AD) verwalten, fügen Sie die entsprechenden Benutzer mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen zu den entsprechenden Zugriffsgruppen hinzu, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.
  
Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder Microsoft PowerShell verwenden:
  
- Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Benutzer zu den entsprechenden Zugriffsgruppen hinzuzufügen.
    
- Stellen Sie für PowerShell zuerst [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218) her. Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto unter Verwendung des Benutzerprinzipalnamens (User Principal Name, UPN) zu einer Zugriffsgruppe hinzuzufügen:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> Um eine Textdatei zu erhalten, die alle PowerShell-Befehle und ein Excel-Konfigurationsarbeitsblatt enthält, die PowerShell-Befehle basierend auf Ihren Gruppen- und Benutzerkontonamen generiert, laden Sie das [Kit für die Bereitstellung einer isolierten SharePoint Online-Teamwebsite]((https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)) herunter. 

Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto unter Verwendung des Anzeigenamens zu einer Zugriffsgruppe hinzuzufügen:

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>Hinzufügen einer neuen Gruppe

Wenn Sie Zugriff für eine ganze Gruppe hinzufügen möchten, müssen Sie entscheiden, in welchem Umfang, d. h. mit welcher Berechtigungsstufe, sämtliche Mitglieder der Gruppe an der Website teilnehmen sollen:
  
- Verwaltung: Fügen Sie die Gruppe zur Zugriffsgruppe der Websiteadministratoren hinzu.
    
- Aktive Zusammenarbeit: Fügen Sie die Gruppe zur Zugriffsgruppe der Websitemitglieder hinzu.
    
- Anzeige: Fügen Sie die Gruppe zur Zugriffsgruppe der Websitbetrachter hinzu.
    
Wenn Sie Benutzerkonten und Gruppen über Windows Server AD verwalten, fügen Sie die entsprechenden Gruppen mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen zu den entsprechenden Gruppen hinzu, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.
  
Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:
  
- Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Gruppen zu den entsprechenden Zugriffsgruppen hinzuzufügen.
    
- Bei Verwendung von PowerShell müssen Sie zunächst [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul herstellen](https://go.microsoft.com/fwlink/?linkid=842218). Verwenden Sie dann die folgenden PowerShell-Befehle:
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>Entfernen eines Benutzers

Wenn der Zugriff auf eine Website für einen Benutzer entfernt werden muss, entfernen Sie den betreffenden Benutzer aus der Zugriffsgruppe, in der er derzeit basierend auf dem Umfang seiner Teilnahme an der Website Mitglied ist:
  
- Verwaltung: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websiteadministratoren.
    
- Aktive Zusammenarbeit: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websitemitglieder.
    
- Anzeige: Entfernen Sie das Benutzerkonto aus der Zugriffsgruppe der Websitebetrachter.
    
Wenn Sie Benutzerkonten und Gruppen über Windows Server  AD verwalten, entfernen Sie die entsprechenden Benutzer mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen aus den entsprechenden Gruppen, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.
  
Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:
  
- Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Benutzer aus den entsprechenden Zugriffsgruppen zu entfernen.
    
- Stellen Sie für PowerShell zuerst [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul](https://go.microsoft.com/fwlink/?linkid=842218) her. Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto aus einer Zugriffsgruppe zu entfernen:
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

Verwenden Sie den folgenden PowerShell-Befehlsblock, um ein Benutzerkonto unter Verwendung des Anzeigenamens aus einer Zugriffsgruppe zu entfernen:
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>Entfernen einer Gruppe

Wenn der Zugriff für eine ganze Gruppe entfernt werden soll, entfernen Sie die betreffende Gruppe aus der Zugriffsgruppe, in der sie derzeit basierend auf dem Umfang ihrer Teilnahme an der Website Mitglied ist:
  
- Verwaltung: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websiteadministratoren.
    
- Aktive Zusammenarbeit: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websitemitglieder.
    
- Anzeige: Entfernen Sie die Gruppe aus der Zugriffsgruppe der Websitebetrachter.
    
Wenn Sie Benutzerkonten und Gruppen über Windows Server Active Directory verwalten, entfernen Sie die entsprechenden Gruppen mit Ihren gewohnten Verfahren zur Verwaltung von Windows Server AD-Benutzern und -Gruppen aus den entsprechenden Zugriffsgruppen, und warten Sie, bis die Synchronisierung mit Ihrem Office 365-Abonnement erfolgt ist.
  
Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Office Admin Center oder PowerShell verwenden:
  
- Bei Verwendung des Office Admin Centers melden Sie sich mit einem Benutzerkonto an, dem die Rolle „Benutzerkontoadministrator" oder „Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen, um die entsprechenden Gruppen aus den entsprechenden Zugriffsgruppen zu entfernen.
    
- Bei Verwendung von PowerShell müssen Sie zunächst [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul herstellen](https://go.microsoft.com/fwlink/?linkid=842218).    
Verwenden Sie den folgenden PowerShell-Befehlsblock, um eine Gruppe unter Verwendung des Anzeigenamens aus einer Zugriffsgruppe zu entfernen:
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>Erstellen eines Dokumentunterordners mit benutzerdefinierten Berechtigungen

In manchen Fällen benötigt eine Teilmenge der Personen, die innerhalb der isolierten Website arbeiten, einen privateren Ort für die Zusammenarbeit. Für SharePoint Online-Websites können Sie einen Unterordner im Dokumentordner der Website erstellen und benutzerdefinierte Berechtigungen zuweisen. Benutzer ohne Berechtigungen können den Unterordner nicht sehen.
  
Gehen Sie zum Erstellen eines Dokumentunterordners mit benutzerdefinierten Berechtigungen folgendermaßen vor:
  
1. Melden Sie sich bei Office 365 mit einem Konto an, das ein Mitglied der Zugriffsgruppe der Websiteadministratoren ist. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Wechseln Sie zu der isolierten Teamwebsite, und klicken Sie auf **Dokumente**.
    
3. Navigieren Sie zu dem Ordner im Dokumentordner, der den Unterordner mit benutzerdefinierten Berechtigungen enthalten soll, erstellen Sie den Ordner, und öffnen Sie ihn.
    
4. Klicken Sie auf **Freigeben**.
    
5. Klicken Sie auf **Freigegeben für > Erweitert**.
    
6. Klicken Sie auf **Berechtigungsvererbung beenden**, und klicken Sie dann auf **OK**.
    
7. Klicken Sie auf **Freigeben**.
    
8. Klicken Sie auf **Freigegeben für > Erweitert**.
    
9. Klicken Sie auf **Berechtigungen erteilen > Freigegeben für > Erweitert**.
    
10. Klicken Sie auf der Berechtigungsseite auf **\<Mitglieder von Websitename>** in der Liste.

    
11. Aktivieren Sie auf der Seite **\<Mitglieder von Websitename** das Kontrollkästchen neben der Zugriffsgruppe der Websitemitglieder, klicken Sie auf **Aktionen**, klicken Sie auf **Benutzer aus Gruppe entfernen**, und klicken Sie dann auf **OK**.
    
12. Um diesem Unterordner bestimmte Mitglieder hinzuzufügen, klicken Sie auf **Neu > Benutzer hinzufügen**.
    
13. Geben Sie im Dialogfeld **Freigeben** die Namen der Benutzerkonten ein, die an Dateien im Unterordner zusammenarbeiten können, und klicken Sie dann auf **Freigeben**.
    
14. Aktualisieren Sie die Webseite, um die neuen Ergebnisse anzuzeigen.
    
15. Klicken Sie im linken Navigationsbereich unter **Gruppen** auf die Gruppe Besucher von **\<Websitename**, und führen Sie die Schritte 11 bis 14 aus, um den Satz der Benutzerkonten anzugeben, die die Dateien im Unterordner anzeigen können (nach Bedarf).
    
16. Klicken Sie im linken Navigationsbereich unter **Gruppen** auf die Gruppe **\<Besitzer von Websitename>**, und führen Sie die Schritte 11 bis 14 aus, um den Satz der Benutzerkonten anzugeben, die die Berechtigungen im Unterordner verwalten können (nach Bedarf).
    
17. Schließen Sie die Registerkarte **Benutzer und Gruppen** im Browser.
    
## <a name="see-also"></a>Weitere Artikel

[Isolierte SharePoint Online-Teamwebsites](isolated-sharepoint-online-team-sites.md)
  
[Entwerfen einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md)
  
[Sicherheitslösungen](security-solutions.md)

[Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md)



