---
title: Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Zusammenfassung: Informationen zum Erstellen von öffentlichen, privaten, vertraulichen und streng vertraulichen SharePoint Online-Teamwebsites in einer Entwicklungs-/Testumgebung."
ms.openlocfilehash: 4878eb201fa32fbeb34be755a22e329fe45d5885
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung

 **Zusammenfassung:** Informationen zum Erstellen von öffentlichen, privaten, vertraulichen und streng vertraulichen SharePoint Online-Teamwebsites in einer Entwicklungs-/Testumgebung.
  
In diesem Artikel finden Sie Schritt-für-Schritt-Anleitungen zum Erstellen einer Entwicklungs-/Testumgebung, die vier verschiedene Typen von SharePoint Online-Teamwebsites für die [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md)-Lösung enthält.
  
![Alle vier Teamwebsites in der sicheren Entwicklungs-/Testumgebung von SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
Verwenden Sie diese Entwicklungs-/Testumgebung zum Experimentieren mit den Verhaltensweisen beim Schutz von Informationen und zur Feinabstimmung der Einstellungen für Ihre spezifischen Anforderungen vor der Bereitstellung von SharePoint Online-Teamwebsites in der Produktion.
  
## <a name="phase-1-create-your-devtest-environment"></a>Phase 1: Erstellen Ihrer Entwicklungs-/Testumgebung

In dieser Phase erhalten Sie Testabonnements für Office 365 und Enterprise Mobility + Security für eine fiktive Organisation.
  
Folgen Sie zunächst den Anweisungen in **Phase 2** des Artikels [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).
  
Als Nächstes registrieren Sie sich für das EMS-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.
  
1. Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Testabonnement beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie auf die Kachel **Admin**.
    
3. Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
Als Nächstes aktivieren Sie die Enterprise Mobility + Security E5-Lizenz für Ihr globales Administratorkonto.
  
1. Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
2. Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.
    
3. Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>Phase 2: Erstellen und Konfigurieren der Azure Active Directory(AD)-Gruppen und -Benutzer

In dieser Phase werden die Azure AD-Gruppen und -Benutzer für Ihre fiktionale Organisation erstellt und konfiguriert.
  
Erstellen Sie zuerst eine Reihe von Gruppen für eine typische Organisation mit dem Azure-Portal.
  
1. Erstellen Sie eine neue Registerkarte im Browser, und wechseln Sie dann zum Azure-Portal unter [(https://portal.azure.com)]((https://portal.azure.com)). Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Office 365 E5-Testabonnement an.
    
2. Klicken Sie im Azure-Portal auf **Azure Active Directory > Benutzer und Gruppen > Alle Gruppen**.
    
3. Klicken Sie auf dem Blatt **Alle Gruppen** auf **+ Neue Gruppe**.
    
4. Auf dem Blatt **Gruppe**:
    
  - Geben **C-Suite** unter **Name** ein.
    
  - Wählen Sie **Zugewiesen** unter **Mitgliedschaft** aus.
    
  - Klicken Sie auf **Ja** für **Office-Features aktivieren**.
    
5. Klicken Sie auf **Erstellen**, und schließen Sie dann das Blatt **Gruppe**.
    
6. Wiederholen Sie die Schritte 3 bis 5 für die folgenden Gruppennamen:
    
  - IT-Mitarbeiter
    
  - Forschungsmitarbeiter
    
  - Normale Mitarbeiter
    
  - Marketingmitarbeiter
    
  - Vertriebsmitarbeiter
    
7. Lassen Sie die Registerkarte für das Azure-Portal in Ihrem Browser geöffnet.
    
Im nächsten Schritt wird die automatische Lizenzierung konfiguriert, sodass Mitgliedern von Gruppen automatisch Lizenzen für Ihre Office 365- und EMS-Abonnements zugewiesen werden.
  
1. Klicken Sie im Azure-Portal auf **Azure Active Directory > Lizenzen > Alle Produkte**.
    
2. Wählen Sie in der Liste **Enterprise Mobility + Security E5** und **Office 365 Enterprise E5** aus, und klicken Sie dann auf **Zuweisen**.
    
3. Klicken Sie auf dem Blatt **Lizenz zuweisen** auf **Benutzer und Gruppen**.
    
4. Wählen Sie in der Liste der Gruppen Folgendes aus:
    
  - C-Suite
    
  - IT-Mitarbeiter
    
  - Forschungsmitarbeiter
    
  - Normale Mitarbeiter
    
  - Marketingmitarbeiter
    
  - Vertriebsmitarbeiter
    
5. Klicken Sie auf **Auswählen** und dann auf **Zuweisen**.
    
6. Schließen Sie die Registerkarte für das Azure Portal in Ihrem Browser.
    
Danach müssen Sie [eine Verbindung mit dem Azure Active Directory V2 PowerShell-Modul herstellen](https://go.microsoft.com/fwlink/?linkid=842218).
  
Geben Sie den Namen Ihrer Organisation, Ihren Standort und ein gemeinsames Kennwort ein, und führen Sie dann die folgenden Befehle über die PowerShell-Eingabeaufforderung oder in der ISE-Umgebung (Integrated Script Environment) aus, um Benutzerkonten zu erstellen und sie zu den Gruppen hinzuzufügen:
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Die Verwendung eines gemeinsamen Kennworts an dieser Stelle dient der Automatisierung und einfacher Konfiguration für eine Entwicklungs-/Testumgebung. Für die Verwendung in Produktionsabonnements wird dies nicht empfohlen. 
  
Gehen Sie folgendermaßen vor, um sicherzustellen, dass die gruppenbasierte Lizenzierung ordnungsgemäß funktioniert.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** in Ihrem Browser auf die Kachel **Admin**.
    
2. Klicken Sie auf der Registerkarte **Office Admin Center** im Browser auf **Benutzer**.
    
3. Klicken Sie in der Benutzerliste auf **CEO**.
    
4. Stellen Sie im Bereich mit den Eigenschaften des Benutzerkontos **CEO** sicher, dass es den Lizenzen **Enterprise Mobility + Security E5** und **Office 365 Enterprise E5** zugewiesen wurde (bei **Produktlizenzen**).
    
## <a name="phase-3-create-office-365-labels"></a>Phase 3: Erstellen von Office 365-Bezeichnungen

In dieser Phase erstellen Sie die Bezeichnungen für die verschiedenen Sicherheitsstufen für Dokumentordner für SharePoint Online-Teamwebsites.
  
1. Melden Sie sich bei Bedarf mithilfe einer privaten Instanz Ihres Internetbrowsers mit dem globalen Administratorkonto Ihres Office 365 E5-Testabonnements beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel **Admin**.
    
3. Klicken Sie auf der neuen Registerkarte **Office Admin Center** im Browser auf **Admin Center > Security &amp; Compliance**.
    
4. Klicken Sie auf der neuen Registerkarte **Start - Security &amp; Compliance** im Browser auf **Klassifizierungen > Bezeichnungen**.
    
5. Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnung erstellen**.
    
6. Geben Sie im Bereich **Name für Bezeichnung** **Intern Öffentlich** ein, und klicken Sie dann auf **Weiter**.
    
7. Klicken Sie im Bereich **Bezeichnungseinstellungen** auf **Weiter**.
    
8. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnung erstellen**, und klicken Sie dann auf **Schließen**.
    
9. Wiederholen Sie die Schritte 5 bis 8 für diese zusätzlichen Bezeichnungen:
    
  - Privat
    
  - Vertraulich
    
  - Streng vertraulich
    
10. Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnungen veröffentlichen**.
    
11. Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Zu veröffentlichende Bezeichnungen wählen**
    
12. Klicken Sie im Bereich **Bezeichnungen wählen** auf **Hinzufügen**, und wählen Sie alle vier Bezeichnungen aus.
    
13. Klicken Sie auf **Fertig**.
    
14. Klicken Sie im Bereich **Zu veröffentlichende Bezeichnungen wählen** auf **Weiter**.
    
15. Klicken Sie im Bereich **Speicherorte auswählen** auf **Weiter**.
    
16. Geben Sie im Bereich **Richtlinie benennen** **Beispielorganisation** unter **Name** ein, und klicken Sie dann auf **Weiter**.
    
17. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnungen veröffentlichen**, und klicken Sie dann auf **Schließen**.
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>Phase 4: Erstellen von SharePoint Online-Teamwebsites

In dieser Phase werden die vier Typen von SharePoint Online-Teamwebsites für Ihre Beispielorganisation erstellt und konfiguriert.
  
### <a name="organization-wide-team-site"></a>Organisationsweite Teamwebsite

Führen Sie folgende Schritte aus, um eine öffentliche SharePoint Online-Basis-Teamwebsite zu erstellen:
  
1. Verwenden Sie, falls erforderlich, einen Browser auf Ihrem lokalen Computer, und melden Sie sich mit Ihrem globalen Administratorkonto beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Websitename** den Namen **Organisationsweit** ein. 
    
6. Geben Sie unter **Beschreibung der Teamwebsite** den Text **SharePoint-Website für die gesamte Organisation** ein.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Öffentlich - Alle Benutzer in der Organisation können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der organisationsweiten Teamwebsite für die Bezeichnung „Intern Öffentlich“.
  
1. Klicken Sie auf der Registerkarte **Organisationsweit - Startseite** in Ihrem Browser auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Intern Öffentlich**, und klicken Sie dann auf **Speichern**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Grundschutz für die organisationsweite öffentliche SharePoint Online-Teamwebsite.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>Teamwebsite für Projekt 1

Führen Sie die folgenden Schritte durch, um eine private SharePoint Online-Basis-Teamwebsite für ein Projekt innerhalb der Organisation zu erstellen:
  
1. Verwenden Sie, falls erforderlich, einen Browser auf Ihrem lokalen Computer, und melden Sie sich mit Ihrem globalen Administratorkonto beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Websitename** den Namen **Projekt 1** ein. 
    
6. Geben Sie unter **Beschreibung der Teamwebsite** den Text **SharePoint-Website für das Projekt 1** ein.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Teamwebsite für Projekt 1 für die Bezeichnung „Privat“.
  
1. Klicken Sie auf der Registerkarte **Projekt 1 - Startseite** in Ihrem Browser auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Privat**, und klicken Sie dann auf **Speichern**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Grundschutz für die private SharePoint Online-Teamwebsite von Projekt1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>Marketingkampagnen – Teamwebsite

Führen Sie die folgenden Schritte durch, um eine isolierte, vertrauliche SharePoint Online-Teamwebsite für Marketingkampagnenressourcen zu erstellen:
  
1. Melden Sie sich über einen Browser auf Ihrem lokalen Computer mit Ihrem globalen Administratorkonto beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Name der Teamwebsite** den Namen **Marketingkampagnen** ein.
    
6. Geben Sie unter **Beschreibung der Teamwebsite** den Text **SharePoint-Website für Marketingkampagnenressourcen (vertraulich)** ein.
    
7.  Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
9. Klicken Sie auf der neuen Registerkarte **Marketingkampagnen** in Ihrem Browser auf der Symbolleiste auf das Symbol „Einstellungen", und klicken Sie dann auf **Websiteberechtigungen**.
    
10. Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
11. Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.
    
12. Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Kontrollkästchen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben**, geben Sie **ITAdmin1@**\<Name Ihrer Organisation>**.onmicrosoft.com** unter **Alle Zugriffsanforderungen an die folgende E-Mail-Adresse senden:** ein, und klicken Sie dann auf **OK**.
    
13. Klicken Sie in der Liste auf **Marketingkampagnenmitglieder**.
    
14. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
15. Geben Sie im Dialogfeld **Freigeben** **Marketing-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
16. Wiederholen Sie die Schritte 14 und 15 für das Benutzerkonto **Researcher1**.
    
17. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
18. Klicken Sie in der Liste auf **Marketingkampagnen - Besitzer**.
    
19. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
20. Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
21. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
22. Schließen Sie die Registerkarte **Benutzer und Gruppen** in Ihrem Browser, klicken Sie auf die Registerkarte **Marketingkampagnen - Startseite** in Ihrem Browser, und schließen Sie dann den Bereich **Websiteberechtigungen**.
    
Ergebnisse der Konfiguration von Berechtigungen:
  
- Die SharePoint-Gruppe **Marketingkampagnen - Mitglieder** enthält nur die Gruppe **Marketingkampagnen** (mit dem globalen Administratorkonto), die Gruppe **Marketing-Mitarbeiter** (mit den Benutzerkonten Marketing1 und Marketing2 und das Benutzerkonto **Researcher1**.
    
- Die SharePoint-Gruppe **Marketingkampagnen - Besitzer** enthält nur die Gruppe **IT-Mitarbeiter** (nur mit den ITAdmin1- und ITAdmin2-Benutzerkonten).
    
- Die SharePoint-Gruppe **Marketingkampagnen - Besucher** enthält keine Gruppen oder Benutzerkonten.
    
- Mitglieder können keine Berechtigungen auf Websiteebene ändern (dies kann nur von Mitgliedern der Gruppe **Marketingkampagnen - Besitzer** ausgeführt werden).
    
- Andere Benutzerkonten können nicht auf die Website oder die zugehörigen Ressourcen zugreifen, Sie können jedoch Zugriff auf die Website anfordern. Dabei wird eine E-Mail an das Postfach des ITAdmin1-Benutzerkontos gesendet.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Marketingkampagnen-Teamwebsite für die Bezeichnung „Vertraulich“.
  
1. Klicken Sie auf der Registerkarte **Marketingkampagnen - Startseite** in Ihrem Browser auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Vertraulich**, und klicken Sie dann auf **Speichern**.
    
Konfigurieren Sie als Nächstes eine Richtlinie zur Verhinderung von Datenverlust (Data Loss Prevention, DLP), die Benutzer benachrichtigt, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung „Vertraulich“ freigeben, die die Marketingkampagnenwebsite enthält (außerhalb der Organisation).
  
1. Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.
    
2. Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.
    
3. Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.
    
4. Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.
    
5. Geben Sie im Bereich **Ihre Richtlinie benennen** den Namen **Bezeichnung „Vertraulich" - SharePoint Online-Teamwebsites** bei **Name** ein, und klicken Sie dann auf **Weiter**
    
6. Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.
    
7. Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.
    
9. In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.
    
10. Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.
    
11. Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.
    
12. Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Weiter**.
    
13. Klicken Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** auf **Richtlinientipptext anpassen**.
    
14. Klicken Sie im Fenster **Richtlinientipps und E-Mail-Benachrichtigungen anpassen** auf **Richtlinientipptext anpassen**.
    
15. Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:
    
  - Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei“ > „Dokument schützen“ > „Mit Kennwort verschlüsseln“, und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.
    
16. Klicken Sie auf **OK**.
    
17. Deaktivieren Sie im Fenster **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** das Kontrollkästchen **Freigeben blockieren und Zugriff auf freigegebene Inhalte einschränken**, und klicken Sie dann auf **Weiter**.
    
18. Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.
    
19. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Schutzebene „Vertraulich“ für die isolierte SharePoint Online-Teamwebsite mit Marketingkampagnen.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>Teamwebsite für Unternehmensstrategie

Führen Sie die folgenden Schritte durch, um eine isolierte, streng vertrauliche SharePoint Online-Teamwebsite für strategische Unternehmensressourcen der Geschäftsführer der Organisation zu erstellen:
  
1. Verwenden Sie, falls erforderlich, einen Browser auf Ihrem lokalen Computer, und melden Sie sich mit Ihrem globalen Administratorkonto beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Name der Teamwebsite** den Namen **Unternehmensstrategie** ein.
    
6. Geben Sie unter **Beschreibung der Teamwebsite** den Text **SharePoint-Website für Unternehmensstrategie (streng vertraulich)** ein.
    
7.  Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
9. Klicken Sie auf der neuen Registerkarte **Unternehmensstrategie** in Ihrem Browser auf der Symbolleiste auf das Symbol „Einstellungen", und klicken Sie dann auf **Websiteberechtigungen**.
    
10. Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
11. Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.
    
12. Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Optionen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben** (sodass alle drei Kontrollkästchen deaktiviert sind), und klicken Sie dann auf **OK**.
    
13. Klicken Sie in der Liste auf **Unternehmensstrategiemitglieder**.
    
14. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
15. Geben Sie im Dialogfeld **Freigeben** **C-Suite** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
16. Klicken Sie in der Liste auf **Unternehmensstrategie - Besitzer**.
    
17. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
18. Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
19. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
20. Schließen Sie die Registerkarte **Benutzer und Gruppen** in Ihrem Browser, klicken Sie auf die Registerkarte **Unternehmensstrategie - Startseite** in Ihrem Browser, und schließen Sie dann den Bereich **Websiteberechtigungen**.
    
Ergebnisse der Konfiguration von Berechtigungen:
  
- Die SharePoint-Gruppe **Unternehmensstrategie - Mitglieder** enthält nur die Gruppe **C-Suite** (mit den Benutzerkonten CEO, CFO und CIO) und die Gruppe **Unternehmensstrategie** (mit dem globalen Administratorkonto).
    
- Die SharePoint-Gruppe **Unternehmensstrategie - Besitzer** enthält nur die Gruppe **IT-Mitarbeiter** (nur mit den ITAdmin1- und ITAdmin2-Benutzerkonten).
    
- Die SharePoint-Gruppe **Unternehmensstrategie - Besucher** enthält keine Gruppen oder Benutzerkonten.
    
- Mitglieder können keine Berechtigungen auf Websiteebene ändern (dies kann nur von Mitgliedern der Gruppe **Unternehmensstrategie - Besitzer** ausgeführt werden).
    
- Andere Benutzerkonten können nicht auf die Website oder ihre Ressourcen zugreifen oder Zugriff auf die Website anfordern. Zusätzliche Berechtigungen für die Website müssen vom globalen Administrator oder von einem Mitglied der Gruppe **Unternehmensstrategie - Besitzer** gewährt werden.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Unternehmensstrategie-Teamwebsite für die Bezeichnung „Streng vertraulich“.
  
1. Klicken Sie auf der Registerkarte **Unternehmensstrategie - Startseite** in Ihrem Browser auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Streng vertraulich**, und klicken Sie dann auf **Speichern**.
    
Konfigurieren Sie als Nächstes eine DLP-Richtlinie, die Benutzer blockiert, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung „Streng vertraulich" freigeben, die die Unternehmensstrategiewebsite enthält (außerhalb der Organisation).
  
1. Falls erforderlich, verwenden Sie einen Browser auf Ihrem lokalen Computer und melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Klicken Sie auf der Registerkarte **Microsoft Office-Homepage** im Browser auf die Kachel **Security &amp; Compliance**.
    
3. Klicken Sie auf der Registerkarte **Security &amp; Compliance** in Ihrem Browser auf **Verhinderung von Datenverlust > Richtlinie**.
    
4. Klicken Sie im Bereich **Verhinderung von Datenverlust** auf **+ Richtlinie erstellen**.
    
5. Klicken Sie im Bereich **Mit einer Vorlage beginnen oder eine benutzerdefinierte Richtlinie erstellen** auf **Benutzerdefiniert**, und klicken Sie dann auf **Weiter**.
    
6. Geben Sie im Bereich **Ihre Richtlinie benennen** den Namen **Bezeichnung „Streng vertraulich" - SharePoint Online-Teamwebsites** bei **Name** ein, und klicken Sie dann auf **Weiter**
    
7. Klicken Sie im Bereich **Speicherorte auswählen** auf **Bestimmte Speicherorte auswählen**, und klicken Sie dann auf **Weiter**.
    
8. Deaktivieren Sie in der Liste der Speicherorte **Exchange-E-Mail** und **OneDrive-Konten**, und klicken Sie dann auf **Weiter**.
    
9. Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Bearbeiten**.
    
10. In der **wählen Sie die Typen der Inhalte zum Schutz** Bereich, klicken Sie auf **hinzufügen** im Dropdown-Listenfeld, und klicken Sie dann auf **Etiketten**.
    
11. Klicken Sie im Bereich **Bezeichnungen** auf **+ Hinzufügen**, wählen Sie die Bezeichnung **Streng vertraulich** aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Fertig**.
    
12. Klicken Sie im Bereich **Typen des zu schützenden Inhalts auswählen** auf **Speichern**.
    
13. Klicken Sie im Bereich **Typen von vertraulichen Informationen anpassen, die geschützt werden sollen** auf **Weiter**.
    
14. Klicken Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** auf **Richtlinientipptext anpassen**.
    
15. Klicken Sie im Fenster **Richtlinientipps und E-Mail-Benachrichtigungen anpassen** auf **Richtlinientipptext anpassen**.
    
16. Geben Sie Folgendes in das Textfeld ein, oder fügen Sie es ein:
    
  - Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei“ > „Dokument schützen“ > „Mit Kennwort verschlüsseln“, und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.
    
17. Klicken Sie auf **OK**.
    
18. Wählen Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** die Option **Begründung für Außerkraftsetzung erforderlich**, und klicken Sie dann auf **Weiter**.
    
19. Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.
    
20. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.
    
Befolgen Sie als Nächstes die Anweisungen unter [Aktivieren von Azure Rights Management über Office 365 Admin Center]((https://docs.microsoft.com/information-protection/deploy-use/activate-office365)).
  
Konfigurieren Sie als Nächstes Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung für Schutz und Berechtigungen, indem Sie die folgenden Schritte ausführen:
  
1. Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).
    
2. Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [(https://portal.azure.com)]((https://portal.azure.com)).
    
3. Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Klicken Sie im Listenbereich auf **Weitere Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
5. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.
    
6. Geben Sie unter **Richtlinienname** **CompanyStrategy** und unter **Beschreibung** **Bezeichnung für Dokumente in der Teamwebsite für Kampagnenstrategie** ein.
    
7. Klicken Sie auf **Wählen Sie aus, welche Benutzer oder Gruppen diese Richtlinie erhalten. > Benutzer/Gruppen** und wählen Sie dann **C-Suite**.
    
8. Klicken Sie auf **Auswählen > OK**.
    
9. Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.
    
10. Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.
    
11. Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.
    
12. Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.
    
13. Klicken Sie auf dem Blatt **Schutz** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.
    
14. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.
    
15. Wählen Sie im Bereich **AAD-Benutzer und -Gruppen** die Option **C-Suite**, und klicken Sie dann auf **Auswählen**.
    
16. Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.
    
17. Klicken Sie zweimal auf **OK**.
    
18. Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.
    
19. Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.
    
20. Klicken Sie auf dem Blatt **Azure Information Protection - Bereichsbezogene Richtlinien** auf **Veröffentlichen** und dann auf **Ja**.
    
Um ein Dokument mit Azure Information Protection und mit dieser neuen Bezeichnung zu schützen, müssen Sie [den Azure Information Protection-Client]((https://docs.microsoft.com/information-protection/rms-client/install-client-app)) auf einem Testcomputer installieren, Office vom Office 365-Portal installieren und sich dann aus Microsoft Word mit einem Konto in der Gruppe **C-Suite** Ihres Testabonnements anmelden.
  
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Schutzebene „Streng vertraulich“ für eine isolierte SharePoint Online-Teamwebsite mit der Unternehmensstrategie.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
Sie können jetzt mit dem Erstellen von Dokumenten in diesen vier Websites beginnen und den Zugriff mit verschiedenen Benutzerkonten in Ihrem Testabonnement testen.
  
Nachfolgend sehen Sie die gesamte Konfiguration für alle vier SharePoint Online-Teamwebsites.
  
![Alle vier Teamwebsites in der sicheren Entwicklungs-/Testumgebung von SharePoint Online.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>Nächster Schritt

Wenn Sie für die Produktionsbereitstellung sicherer SharePoint Online-Websites bereit sind, erhalten Sie unter [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md) detaillierte Informationen und Links zu Schritt-für-Schritt-Bereitstellungsartikeln.
  
## <a name="see-also"></a>Weitere Artikel

[Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md)
  
[Sicherheitslösungen](security-solutions.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




