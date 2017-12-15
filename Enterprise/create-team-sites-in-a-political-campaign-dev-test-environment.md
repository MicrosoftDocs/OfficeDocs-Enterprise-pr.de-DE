---
title: "Erstellen von Teamwebsites in einer Entwicklungs-/Testumgebung für eine politische Kampagne"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Zusammenfassung: Erstellen Sie öffentliche, private, vertrauliche und streng vertraulich SharePoint Online Teamwebsites in Ihrer politischen Kampagne Test-/-Umgebung."
ms.openlocfilehash: 82e671af271508dfdecac6169a7892a8a12b7865
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a>Erstellen von Teamwebsites in einer Entwicklungs-/Testumgebung für eine politische Kampagne

 **Zusammenfassung:** Erstellen Sie in der Umgebung der politischen Kampagne Test-/öffentliche, private, vertrauliche und streng vertraulich SharePoint Online Teamwebsites. 
  
Verwenden Sie die Anweisungen in diesem Artikel eine Test-/Umgebung erstellen, die vier verschiedenen Typen von SharePoint Online Teamwebsites für die [Microsoft Security Guidance for politischen Kampagnen, gemeinnützige Organisationen, und andere Agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) enthält Lösung. Diese Websites werden auf Thema 10, mit dem Titel **SharePoint- und OneDrive für Unternehmen**ausführlich beschrieben.
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a>Phase 1: Erstellen der Entwicklungs-/Testumgebung für eine politische Kampagne

Führen Sie zunächst die Anweisungen in [Configure Gruppen und Benutzer für eine politischen Kampagne Test-/Umgebung](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) zum Erstellen von Ihrer Abonnements, Benutzer und Gruppen.
  
## <a name="phase-2-create-office-365-labels"></a>Phase 2: Erstellen von Office 365-Bezeichnungen

In dieser Phase erstellen Sie die Beschriftungen für unterschiedlichen Sicherheitsebenen für SharePoint Online Team Websiteordner Dokument.
  
1. Falls erforderlich, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos für Ihr Testabonnement beim Office 365-Portal an. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel **Admin**.
    
3. Klicken Sie auf der neuen Registerkarte **Office Admin Center** im Browser auf **Admin Center > Security &amp; Compliance**.
    
4. Klicken Sie auf der neuen Registerkarte **Start - Security &amp; Compliance** im Browser auf **Klassifizierungen > Bezeichnungen**.
    
5. Klicken Sie im Bereich **Start > Bezeichnungen** auf **Bezeichnung erstellen**.
    
6. Klicken Sie im Bereich **Name die Bezeichnung** Geben Sie **Internal**, und klicken Sie dann auf **Weiter**.
    
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
    
16. Klicken Sie im Bereich **Name der Richtlinie** geben **Kampagne** im **Feld Name**ein, und klicken Sie dann auf **Weiter**.
    
17. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Bezeichnungen veröffentlichen**, und klicken Sie dann auf **Schließen**.
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a>Phase 3: Erstellen von SharePoint Online-Teamwebsites

In dieser Phase werden SharePoint Online-Teamwebsites für Ihre politische Kampagne entsprechend den vier Typen von SharePoint Online-Teamwebsites erstellt und konfiguriert.
  
### <a name="campaign-wide-team-site"></a>Kampagnen-Teamwebsite

Führen Sie folgende Schritte aus, um eine öffentliche SharePoint Online-Basis-Teamwebsite zu erstellen:
  
1. Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie in das Feld **Websitename** **Kampagne breit**. 
    
6. Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für die gesamte Kampagne**.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Öffentlich - Alle Benutzer in der Organisation können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnen-Teamwebsite für die Bezeichnung „Intern“.
  
1. Klicken Sie auf der Registerkarte **Kampagne Wide-Home** Ihres Browsers auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie **intern**im Feld **Bezeichnung Einstellungen anwenden**, und klicken Sie dann auf **Speichern**.
    
### <a name="campaign-project-1-team-site"></a>Teamwebsite für Kampagnenprojekt 1

Führen Sie die folgenden Schritte durch, um eine private SharePoint Online-Basis-Teamwebsite für ein Projekt innerhalb der Kampagne zu erstellen:
  
1. Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie in das Feld **Websitename** **Kampagne Projekt 1**. 
    
6. Geben Sie im Feld **Team Site Beschreibung** **SharePoint-Website für Kampagne Projekt 1**.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Teamwebsite für Kampagnenprojekt 1 für die Bezeichnung „Privat“.
  
1. Klicken Sie auf der Registerkarte **Project-1-Startseite Kampagne** Ihres Browsers auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Privat**, und klicken Sie dann auf **Speichern**.
    
### <a name="campaign-marketing-team-site"></a>Kampagnenmarketing-Teamwebsite

Führen Sie die folgenden Schritte durch, um eine isolierte, vertrauliche SharePoint-Teamwebsite für Kampagnenmarketingressourcen zu erstellen:
  
1. Melden Sie sich mit einem Browser auf dem lokalen Computer an, in das globale Administratorkonto mit Office 365-Portal ([https://portal.office.com](https://portal.office.com)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie in das Feld **Teamname Website** **Kampagne Marketing**.
    
6. Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für Kampagne marketing (/ Kleinschreibung beachten)**.
    
7.  Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
9. Klicken Sie auf das einstellungssymbol auf der neuen Registerkarte **Kampagne Marketing** in Ihrem Browser in der Symbolleiste, und klicken Sie dann auf **Websiteberechtigungen**.
    
10. Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
11. Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.
    
12. Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Kontrollkästchen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben**, geben Sie **ITAdmin1@**<your organization name> **.onmicrosoft.com** unter **Alle Zugriffsanforderungen an die folgende E-Mail-Adresse senden:**, und klicken Sie dann auf **OK**.
    
13. Klicken Sie in der Liste **Mitglieder marketing-Kampagnen** auf.
    
14. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
15. Klicken Sie im Dialogfeld **Freigeben** Geben Sie, **Senior und strategische Personal**, wählen Sie sie aus und klicken Sie dann auf **Freigeben**.
    
16. Wiederholen Sie die Schritte 14 und 15 für die Gruppe **Analytics Personal** und das Benutzerkonto **Regular1** .
    
17. Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.
    
18. Klicken Sie in der Liste auf **Besitzer marketing-Kampagnen** .
    
19. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
20. Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
21. Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.
    
22. Schließen Sie die Registerkarte **Personen und Gruppen** in Ihrem Browser, klicken Sie auf der Registerkarte **Kampagne Marketing-Startseite** in Ihrem Browser, und schließen Sie den Bereich für die **Projektwebsite-Berechtigungen** .
    
Ergebnisse der Konfiguration von Berechtigungen:
  
- Die Kampagne Marketing - SharePoint-Gruppe **Mitglieder** enthält nur die **Senior und strategische Mitarbeiter** Gruppe (die Benutzerkonten Candidate, ChiefOfStaff und Strategic1 enthält), die **Kampagne** Marketinggruppe (: Dieser Abschnitt enthält die Globaler Administratorbenutzerkonto), der Gruppe der **Analytics Staff** (der das Benutzerkonto DataScientist1 enthält), und das Benutzerkonto **Regular1** .
    
- SharePoint-Gruppe der **Kampagne Marketing-Besitzer** enthält nur die **IT-Mitarbeiter** -Gruppe (die nur die Benutzerkonten ITAdmin1 und ITAdmin2 enthält).
    
- SharePoint-Gruppe der **Kampagne Marketing-Besucher** enthält keine Gruppen oder Benutzerkonten.
    
- Mitglieder können nicht auf Standortebene Berechtigungen ändern (Dies kann nur durch ein Mitglied der Gruppe der **Kampagne Marketing-Besitzer** erfolgen).
    
- Andere Benutzerkonten können nicht auf die Website oder die zugehörigen Ressourcen zugreifen, Sie können jedoch Zugriff auf die Website anfordern. Dabei wird eine E-Mail an das Postfach des ITAdmin1-Benutzerkontos gesendet.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnenmarketing-Teamwebsite für die Bezeichnung „Vertraulich“.
  
1. Klicken Sie in der Registerkarte **Kampagne Marketing-Start** des Browsers auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Vertraulich**, und klicken Sie dann auf **Speichern**.
    
Konfigurieren Sie anschließend eine Data Loss Prevention (DLP) Richtlinie, die Benutzer mitgeteilt wird, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung vertrauliche außerhalb der Organisation freigeben. In diesem DLP-Richtlinie gilt für Ressourcen in der Kampagne marketing-Website.
  
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
    
  - Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei" > „Dokument schützen" > „Mit Kennwort verschlüsseln", und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.
    
16. Klicken Sie auf **OK**.
    
17. Deaktivieren Sie im Fenster **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** das Kontrollkästchen **Freigeben blockieren und Zugriff auf freigegebene Inhalte einschränken**, und klicken Sie dann auf **Weiter**.
    
18. Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.
    
19. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.
    
### <a name="campaign-strategy-team-site"></a>Teamwebsite für Kampagnenstrategie

Führen Sie die folgenden Schritte durch, um eine isolierte, streng vertrauliche SharePoint Online-Teamwebsite für Kampagnenstrategieressourcen zu erstellen:
  
1. Falls erforderlich, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich mit Ihrem Konto globaler Administrator Office 365-Portal ([https://portal.office.com](https://portal.office.com)).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen **SharePoint**-Registerkarte in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie in das Feld **Teamname für die Website** **Kampagne Strategie**.
    
6. Geben Sie im Feld **websitebeschreibung Team** **SharePoint-Website für Kampagne Strategie (streng vertraulich)**.
    
7.  Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
9. Klicken Sie auf das einstellungssymbol auf der neuen Registerkarte **Kampagne Strategie** in Ihrem Browser in der Symbolleiste, und klicken Sie dann auf **Websiteberechtigungen**.
    
10. Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
11. Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Einstellungen für Zugriffsrechteanforderungen**.
    
12. Deaktivieren Sie im Dialogfeld **Einstellungen für Zugriffsrechteanforderungen** die Optionen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern das Einladen von anderen zur Websitemitglieder-Gruppe erlauben** (sodass alle drei Kontrollkästchen deaktiviert sind), und klicken Sie dann auf **OK**.
    
13. Klicken Sie auf **Kampagne Strategie für die Elemente** in der Liste.
    
14. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
15. Klicken Sie im Dialogfeld **Freigeben** Geben Sie, **Senior und strategische Personal**, wählen Sie sie aus und klicken Sie dann auf **Freigeben**.
    
16. Klicken Sie in der Liste auf **Kampagne Strategie Besitzer** .
    
17. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
18. Geben Sie im Dialogfeld **Freigeben** **IT-Mitarbeiter** ein, wählen Sie die Option aus, und klicken Sie dann auf **Freigeben**.
    
19. Klicken Sie auf die Schaltfläche „Zurück" in Ihrem Browser.
    
20. Schließen Sie die Registerkarte **Personen und Gruppen** in Ihrem Browser, klicken Sie auf der Registerkarte **Kampagne Strategie-Startseite** in Ihrem Browser, und schließen Sie den Bereich für die **Projektwebsite-Berechtigungen** .
    
Ergebnisse der Konfiguration von Berechtigungen:
  
- Die Kampagne Strategie - SharePoint-Gruppe **Mitglieder** enthält nur die **Senior und strategische Mitarbeiter** Gruppe (die nur die Benutzerkonten Candidate, ChiefOfStaff und Strategic1 enthält) und der **Kampagne Strategie** -Gruppe (die enthält nur der globale Administrator-Benutzerkonto).
    
- SharePoint-Gruppe der **Kampagne Strategie-Besitzer** enthält nur die **IT-Mitarbeiter** -Gruppe (die nur die Benutzerkonten ITAdmin1 und ITAdmin2 enthält).
    
- SharePoint-Gruppe der **Kampagne Strategie-Besucher** enthält keine Gruppen oder Benutzerkonten.
    
- Mitglieder können nicht auf Standortebene Berechtigungen ändern (Dies kann nur durch ein Mitglied der Gruppe der **Kampagne Strategie-Besitzer** erfolgen).
    
- Andere Benutzerkonten nicht Zugriff auf die Website oder seiner Ressourcen oder Zugriff auf die Website anfordern. Zusätzliche Berechtigungen für die Website müssen der globale Administrator oder ein Mitglied der Gruppe der **Kampagne Strategie-Besitzer** erfolgen.
    
Konfigurieren Sie anschließend den Ordner „Dokumente“ der Kampagnenstrategie-Teamwebsite für die Bezeichnung „Streng vertraulich“.
  
1. Klicken Sie auf der Registerkarte **Kampagne Strategie für die Startseite** des Browsers auf **Dokumente**.
    
2. Klicken Sie auf das Symbol für Einstellungen und anschließend auf **Bibliothekeinstellungen**.
    
3. Klicken Sie unter **Berechtigungen und Verwaltung** auf **Bezeichnung auf Elemente in dieser Bibliothek anwenden**.
    
4. Wählen Sie unter **Einstellungen -Bezeichnung anwenden** die Option **Streng vertraulich**, und klicken Sie dann auf **Speichern**.
    
Im nächsten Schritt Konfigurieren einer DLP-Richtlinie, Blöcke der Benutzer, wenn sie ein Dokument auf einer SharePoint Online-Teamwebsite mit der Bezeichnung streng vertraulich außerhalb der Organisation freigeben. In diesem DLP-Richtlinie gilt für Ressourcen in der Kampagne Strategie für die Website.
  
1. Bei Bedarf, verwenden Sie einen Browser auf dem lokalen Computer, und melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit einem Konto an, die die Rolle Sicherheitsadministrator oder Unternehmensadministrator hat.
    
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
    
  - Wenn Sie eine Datei für einen Benutzer außerhalb der Organisation freigeben möchten, laden Sie die Datei herunter, und öffnen Sie sie. Klicken Sie auf „Datei" > „Dokument schützen" > „Mit Kennwort verschlüsseln", und geben Sie dann ein sicheres Kennwort ein. Senden Sie das Kennwort in einer separaten E-Mail oder auf andere Weise.
    
17. Klicken Sie auf **OK**.
    
18. Wählen Sie im Bereich **Was möchten Sie tun, wenn vertrauliche Informationen erkannt werden?** die Option **Begründung für Außerkraftsetzung erforderlich**, und klicken Sie dann auf **Weiter**.
    
19. Klicken Sie im Bereich **Möchten Sie die Richtlinie aktivieren oder zunächst testen?** auf **Ja, Richtlinie aktivieren**, und klicken Sie dann auf **Weiter**.
    
20. Klicken Sie im Bereich **Einstellungen überprüfen** auf **Erstellen**, und klicken Sie dann auf **Schließen**.
    
Verwenden Sie die Anweisungen in [Azure-RMS mit Office 365 Administrationscenter aktivieren](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Konfigurieren Sie als Nächstes Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung für Schutz und Berechtigungen, indem Sie die folgenden Schritte ausführen:
  
1. Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com).
    
3. Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Klicken Sie im Listenbereich auf **Weitere Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
5. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.
    
6. Geben Sie **CampaignStrategy** **Richtliniennamen** und die **Beschriftung für Dokumente in der Kampagne Strategie für die SharePoint-Teamwebsite** im Feld **Beschreibung**ein.
    
7. Klicken Sie auf **auswählen, welche Benutzer oder Gruppen diese Richtlinie erhalten > Benutzer/Gruppen**, und wählen Sie dann **Senior und strategische Personal**.
    
8. Klicken Sie auf **Auswählen > OK**.
    
9. Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.
    
10. Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.
    
11. Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.
    
12. Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.
    
13. Klicken Sie auf dem Blatt **Schutz** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.
    
14. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.
    
15. Klicken Sie im Bereich **AAD Benutzer und Gruppen** wählen Sie aus, **Senior und strategische Mitarbeiter**, und klicken Sie dann auf **auswählen**.
    
16. Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.
    
17. Klicken Sie zweimal auf **OK**.
    
18. Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.
    
19. Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.
    
20. Klicken Sie auf dem Blatt **Azure Information Protection - Bereichsbezogene Richtlinien** auf **Veröffentlichen** und dann auf **Ja**.
    
Sie können jetzt mit dem Erstellen von Dokumenten in diesen vier Websites beginnen und den Zugriff mit verschiedenen Benutzerkonten in Ihrem Testabonnement testen. 
  
Um ein Dokument mit Azure Information Protection und dieser neuen Bezeichnung zu schützen, müssen Sie auf einem Testcomputer [Installieren Sie den Client Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) , Installieren von Office über das Office 365-Portal und melden Sie sich von Microsoft Word mit einem Konto in der ** Senior und strategische Mitarbeiter** Gruppe von Test-Abonnement.
  
## <a name="see-also"></a>See Also

[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Konfigurieren von Gruppen und Benutzer für eine politischen Kampagne Test-/-Umgebung](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




