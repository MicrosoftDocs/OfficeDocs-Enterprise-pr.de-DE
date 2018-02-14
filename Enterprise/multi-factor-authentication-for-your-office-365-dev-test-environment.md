---
title: "Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung"
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Zusammenfassung: Konfigurieren von an einem Smartphone in einer Office 365-Umgebung Test-/gesendete Textnachrichten mehrstufige Authentifizierung.'
ms.openlocfilehash: 23c5aa4e205937899cac813b3b39780c989a1073
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren Sie die mehrstufige Authentifizierung mithilfe von an einem Smartphone in einer Office 365-Umgebung Test-/gesendete Textnachrichten.
  
Als zusätzliche Sicherheitsmaßnahme für die Anmeldung bei einem Office 365-Abonnement können Sie Azure Multi-Factor Authentication aktivieren, die mehr als nur einen Benutzernamen und ein Kennwort erfordert, um ein Konto zu überprüfen. Mit Multi-Factor Authentication für Office 365 müssen Benutzer auf ihrem Smartphone einen Telefonanruf bestätigen, einen Verifizierungscode eingeben, der ihnen in einer Textnachricht zugesendet wurde, oder ein App-Kennwort auf ihrem Smartphone angeben, nachdem sie ihr Kennwort korrekt eingegeben haben. Eine Anmeldung ist nur möglich, nachdem diese zweite Authentifizierungsstufe passiert wurde.  
  
In diesem Artikel wird beschrieben, wie die Authentifizierung auf Basis einer Textnachricht für ein bestimmtes Office 365-Konto aktiviert und getestet wird.
  
Es gibt zwei Phasen bei der Einrichtung von Multi-Factor Authentication für Office 365 in einer Entwicklungs-/Testumgebung:
  
1. Erstellen der Office 365-Entwicklungs-/Testumgebung
    
2. Aktivieren und Testen von Multi-Factor Authentication für das Konto „Benutzer 2“
    
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung

Wenn Sie auf einfache Weise mit den Mindestanforderungen mehrstufige Authentifizierung testen möchten, befolgen Sie die Anweisungen in Phasen 2 und 3 von [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).
  
Wenn Sie in einer simulierten Enterprise mehrstufige Authentifizierung testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Für das Testen von Multi-Factor Authentication ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie Multi-Factor Authentication testen und damit in einer Umgebung experimentieren können, die eine typische Organisation darstellt. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2: Aktivieren und Testen von Multi-Factor Authentication für das Konto „Benutzer 2“

Aktivieren Sie Multi-Factor Authentication für das Konto „Benutzer 2“ mit den folgenden Schritten:
  
1. Öffnen Sie eine separate Instanz des Browsers, wechseln Sie zu Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und dann Test Office 365-Abonnement mit Ihrem globaler Administrator-Konto anmelden.
    
2. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
3. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
4. Klicken Sie im Bereich aktive Benutzer klicken Sie auf **mehr > Setup Azure Multi-Factor Auth**.
    
5. Klicken Sie in der Liste auf das Konto für **Benutzer 2** .
    
6. Klicken Sie im Abschnitt **Benutzer 2** unter **QuickSteps**, auf **Aktivieren**.
    
7. Klicken Sie im Dialogfeld **zum Aktivieren der mehrstufigen Authentifizierung** auf **mehrstufige Authentifizierung aktivieren**.
    
8. Klicken Sie im Dialogfeld **Update erfolgreich** auf **Schließen**.
    
9. Klicken Sie auf das Symbol des Benutzer-Konto in der oberen rechten Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.
    
10. Schließen Sie Ihre Browserinstanz.
    
Schließen Sie die Konfiguration des Kontos „Benutzer 2“ für die Verwendung einer Textnachricht zur Prüfung ab, und testen Sie es mit den folgenden Schritten:
  
1. Öffnen Sie eine neue Instanz Ihres Browsers.
    
2. Wechseln Sie zu der Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und melden Sie sich mit dem Konto Benutzer 2 (Benutzer2 @\<Organisationsname >. onmicrosoft.com) und das Kennwort ein.
    
3. Nach der Anmeldung werden Sie aufgefordert, das Konto für die zusätzlichen sicherheitsüberprüfung einrichten. Klicken Sie auf **jetzt einrichten**.
    
4. Auf der Seite **zusätzliche Sicherheit Überprüfung** :
    
  - Wählen Sie Ihr Land oder Ihre Region aus.
    
  - Geben Sie die Telefonnummer des Smartphones ein, das Textnachrichten erhalten soll.
    
  - Wählen Sie **mich senden einen Code über Textnachricht**.
    
5. Klicken Sie auf **Kontakt**.
    
6. Geben Sie den Überprüfungscode aus der Textnachricht auf Ihrem Smartphone empfangen, und klicken Sie dann auf **Verify**.
    
7. Klicken Sie auf die **Schritt 3: vorhandenen dauerhafte** Seite, tragen Sie das angezeigten app-Kennwort für das Konto des Benutzers 2 an einem sicheren Ort, und klicken Sie dann auf **Fertig**.
    
8. Wieder auf der Seite Anmeldung Geben Sie das Kennwort für das Konto des Benutzers 2, und klicken Sie auf **Anmelden**.
    
9. Geben Sie den Überprüfungscode aus der Textnachricht auf Ihrem Smartphone empfangen, und klicken Sie dann auf **Anmelden**.
    
10. Wenn hierbei handelt es sich beim ersten signiert Sie sich mit dem Konto Benutzer 2 Aufforderung zum Ändern des Kennworts. Geben Sie das ursprüngliche Kennwort und das neue Kennwort zweimal ein, und klicken Sie dann auf **Kennwort aktualisieren, und melden Sie sich**. Notieren Sie das neue Kennwort ein, an einem sicheren Ort.
    
    Das Office 365-Portal für Benutzer 2 sollte angezeigt werden.
    
## <a name="see-also"></a>Weitere Artikel

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Plan für die mehrstufige Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

