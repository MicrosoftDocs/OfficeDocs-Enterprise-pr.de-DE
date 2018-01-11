---
title: "Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Zusammenfassung: Konfigurieren und Demonstrieren von Office 365 Cloud App Security in der Office 365-Entwicklungs-/Testumgebung'
ms.openlocfilehash: 8d398dcbf1ca5dea5ee790a64829eef55765025a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren und Demonstrieren von Office 365 Cloud App Security in der Office 365-Entwicklungs-/Testumgebung
  
Office 365 Cloud App Security, vormals Office 365 Advanced Security Management, ermöglicht Ihnen das Erstellen von Richtlinien, die verdächtige Aktivitäten in Ihrem Office 365-Abonnement überwachen und Sie ggf. informieren, damit Sie sie untersuchen und mögliche Gegenmaßnahmen ergreifen können. Weitere Informationen finden Sie unter [Übersicht über Cloud App Security in Office 365]((https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)).
  
Mit den Anweisungen in diesem Artikel aktivieren und testen Sie Cloud App Security in Ihrem Office 365-Testabonnement.
  
> [!TIP]
> Klicken Sie [hier]((http://aka.ms/catlgstack)), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung

Wenn Sie Cloud App Security nur auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).
  
Wenn Sie Cloud App Security in einem simulierten Unternehmen testen möchten, führen Sie die Schritte in [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) aus.
  
> [!NOTE]
> Für das Testen von Cloud App Security ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie Cloud App Security testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Phase 2: Vor dem Aktivieren von Cloud App Security und Erstellen einer Richtlinie

In diesem Verfahren demonstrieren Sie, dass das Ändern einer Benutzerrolle vor dem Aktivieren von Cloud App Security keine E-Mail-Benachrichtigung an den globalen Administrator mit sich bringt.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Testen des Standardbenachrichtigungsverhaltens von Office 365

1. Wechseln Sie zum Office 365-Portal ([(https://portal.office.com)]((https://portal.office.com))), und melden Sie sich bei Ihrem Office 365-Testabonnement mit Ihrem globalen Administratorkonto an.
    
  - Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das [Azure-Portal]((https://portal.azure.com)), um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.
    
2. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
3. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
4. Klicken Sie auf das Konto **Benutzer 4**.
    
5. Klicken Sie auf der Seite **Benutzer 4** auf **Bearbeiten** für die Zeile **Rollen**.
    
6. Klicken Sie auf der Seite **Benutzerrollen bearbeiten** auf **Globaler Administrator**, geben Sie **user4@contoso.com** unter **Alternative E-Mail-Adresse** ein, und klicken Sie dann auf **Speichern**. Klicken Sie zweimal auf **Schließen**.
    
7. Wählen Sie oben links das App-Startsymbol und dann **Admin** aus.
    
8. Warten Sie 30 Minuten. Beachten Sie, dass es im Posteingang keine E-Mail-Nachricht gibt, die Sie über die Änderung der Rolle von Benutzers 4 als globaler Administrator informiert.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Phase 3: Aktivieren von Cloud App Security und Erstellen einer Richtlinie

In diesem Verfahren aktivieren Sie Cloud App Security und erstellen eine neue Richtlinie zum Senden von E-Mail-Benachrichtigungen an Ihr globales Administratorkonto, wenn Änderungen an Benutzerkontorollen vorgenommen werden. Dieses Verfahren erfordert Folgendes:
  
- Der Kontoname des globalen Administrators und das Kennwort für Ihr Office 365-Testabonnement.
    
- Der Name und das Kennwort des Kontos von Benutzer 5 Ihres Office 365-Testabonnements.
    
### <a name="enable-and-configure-cloud-app-security"></a>Aktivieren und Konfigurieren von Cloud App Security

1. Wechseln Sie zum Office 365-Portal ([(https://portal.office.com)]((https://portal.office.com))), und melden Sie sich bei Ihrem Office 365-Testabonnement mit Ihrem globalen Administratorkonto an.
    
2. Klicken Sie auf die Kachel **Security &amp; Compliance**.
    
3. Klicken Sie im linken Navigationsbereich auf **Warnungen > Erweiterte Warnungen verwalten**.
    
4. Klicken Sie auf der Seite **Erweiterte Warnungen verwalten** auf **Office 365 Cloud App Security aktivieren**, und klicken Sie dann auf **Zu Office 365 Cloud App Security wechseln**.
    
5. Klicken Sie auf der neuen **Dashboard**-Registerkarte auf **Steuern > Richtlinien**.
    
6. Klicken Sie auf der Seite **Richtlinie** auf **Richtlinie erstellen**, und klicken Sie dann auf **Aktivitätsrichtlinie**.
    
7. Geben Sie im Feld **Richtlinienname** den Namen **Administrative Aktivität** ein.
    
8. Klicken Sie unter **Schweregrad der Richtlinie** auf **Hoch**.
    
9. Klicken Sie unter **Kategorie** auf **Privilegierte Konten**.
    
10. Klicken Sie in **Filter für die Richtlinie erstellen** unter **Aktivitäten entspricht allen folgenden Kriterien** auf **Administrative Aktivität**.
    
11. Klicken Sie unter **Benachrichtigungen** auf **Benachrichtigung als E-Mail senden**. Geben Sie unter **An** die E-Mail-Adresse Ihres globalen Administratorkontos ein.
    
12. Klicken Sie unten auf der Seite auf **Erstellen**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Phase 4: Vorführen von Cloud App Security in Aktion

In diesem Verfahren demonstrieren Sie, wie Cloud App Security Warnungen erstellt und E-Mail-Benachrichtigungen an das globale Administratorkonto sendet, wenn Benutzer 4 Benutzer 5 als Kennwort- und Benutzerverwaltungsadministrator festlegt.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demonstrieren der E-Mail-Benachrichtigung für eine Änderung an Benutzerkontorollen

1. Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [(https://portal.office.com)]((https://portal.office.com)).
    
3. Klicken Sie auf der Office 365-Anmeldeseite auf **Ein anderes Konto verwenden**.
    
4. Geben Sie den Benutzernamen und das Kennwort von Benutzer 4 ein, und klicken Sie dann auf **Anmelden**.
    
5. Falls erforderlich, ändern Sie das Kennwort von Benutzers 4, und klicken Sie dann auf **Kennwort aktualisieren und anmelden**.
    
6. Klicken Sie auf der Office 365-Portalseite auf **Admin**.
    
7. Klicken Sie bei Bedarf auf **Abbrechen**, wenn Sie dazu aufgefordert, Ihre Administratorkontaktinformationen zu aktualisieren.
    
8. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
9. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
10. Klicken Sie auf das Konto **Benutzer 5**.
    
11. Klicken Sie auf der Seite **Benutzer 5** auf **Bearbeiten** für die Zeile **Rollen**.
    
12. Klicken Sie auf der Seite **Benutzerrollen bearbeiten** auf **Angepasster Administrator**, klicken Sie auf **Kennwortadministrator** und **Benutzerverwaltungsadministrator**, geben Sie **user5@contoso.com** unter **Alternative E-Mail-Adresse** ein, und klicken Sie dann auf **Speichern**. Klicken Sie zweimal auf **Schließen**.
    
13. Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**. 
    
14. Wechseln Sie zu [(https://portal.office.com)]((https://portal.office.com)).
    
15. Klicken Sie auf der Seite **Office 365-Anmeldung** auf den Kontonamen Ihres globalen Administrators.
    
16. Geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
17. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
18. Klicken Sie auf die Kachel **Security &amp; Compliance**.
    
19. Klicken Sie im linken Navigationsbereich auf **Warnungen > Erweiterte Warnungen verwalten**.
    
20. Klicken Sie auf der Seite **Erweiterte Warnungen verwalten** auf **Zu Office 365 Cloud App Security wechseln**.
    
21. Auf der neuen **Dashboard**-Registerkarte werden zwei neue Warnungen für **Administrative Aktivität** angezeigt.
    
22. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Mail**. Warten Sie bis zu 30 Minuten. 
    
    Im Posteingang sollten zwei neue E-Mail-Nachrichten mit dem Titel **Microsoft Azure AD-Benachrichtigungsdienst** angezeigt werden. Eine Nachricht besagt, dass das Konto von Benutzer 5 der Rolle **Kennwortadministrator** hinzugefügt wurde. Die andere Nachricht gibt an, dass das Konto von Benutzer 5 der Rolle **Benutzeradministrator** hinzugefügt wurde (entspricht der Rolle „Benutzerverwaltungsadministrator" im Office 365 Admin Center).
    
Sie können diese Umgebung jetzt verwenden, um neue Richtlinien zu erstellen und weiter mit Office 365 Cloud App Security zu experimentieren. Unter [Erste Schritte mit Advanced Security Management]((https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)) finden Sie Links zu zusätzlichen Konfigurationsartikeln.
  
## <a name="see-also"></a>Weitere Artikel

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Übersicht über Cloud App Security in Office 365]((https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475))


