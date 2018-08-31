---
title: Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Zusammenfassung: Konfigurieren Sie Multi-Factor Authentication mithilfe von Textnachrichten, die an ein Smartphone in einer Office 365-Entwicklungs-/Testumgebung gesendet werden.'
ms.openlocfilehash: 12458e2dd41518deb0b540e809a08c4df865a3df
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915660"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Multi-Factor Authentication für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren Sie Multi-Factor Authentication mithilfe von Textnachrichten, die an ein Smartphone in einer Office 365-Entwicklungs-/Testumgebung gesendet werden.
  
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
  
1. Öffnen Sie eine separate Instanz des Browsers, fahren Sie mit Office 365-Portal ([https://portal.office.com](https://portal.office.com)), und klicken Sie dann auf Test Office 365-Abonnement mit Ihrem Konto globaler Administrator anmelden.
    
2. Klicken Sie auf der Hauptportalseite auf **Admin**.
    
3. Klicken Sie im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
4. Klicken Sie im Bereich „Aktive Benutzer“ auf **Mehr > Azure Multi-Factor Authentication einrichten**.
    
5. Wählen Sie in der Liste der **Benutzer 2** -Konto aus.
    
6. Klicken Sie im Abschnitt **Benutzer 2** unter **QuickSteps** auf **Aktivieren**.
    
7. Klicken Sie im Dialogfeld **Informationen zum Aktivieren von mehrstufiger Aktualisierung** auf **Multi-Factor Authentication aktivieren**.
    
8. Klicken Sie im Dialogfeld **Update erfolgreich** auf **Schließen**.
    
9. Klicken Sie auf der Registerkarte **Microsoft Office-Starts** auf das Benutzerkontosymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
10. Schließen Sie Ihre Browserinstanz.
    
Schließen Sie die Konfiguration des Kontos „Benutzer 2“ für die Verwendung einer Textnachricht zur Prüfung ab, und testen Sie es mit den folgenden Schritten:
  
1. Öffnen Sie eine neue Instanz Ihres Browsers.
    
2. Wechseln Sie zu Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und melden Sie sich mit dem Konto Benutzer 2 (Benutzer2 @\<Organisationsname >. onmicrosoft.com) und das Kennwort ein.
    
3. Nach der Anmeldung werden Sie aufgefordert, eine zusätzliche Sicherheitsüberprüfung für das Konto einzurichten. Klicken Sie auf **Jetzt einrichten**.
    
4. Führen Sie auf der Seite **Zusätzliche Sicherheitsüberprüfung** die folgenden Schritte aus: 
    
  - Wählen Sie Ihr Land oder Ihre Region aus.
    
  - Geben Sie die Telefonnummer des Smartphones ein, das Textnachrichten erhalten soll.
    
  - Klicken Sie in- **Methode**auf **mich senden einen Code über Textnachricht**.
    
5. Klicken Sie auf **Weiter**.
    
6. Geben Sie den Verifizierungscode aus der Textnachricht ein, die an Ihr Smartphone gesendet wurde, und klicken Sie dann auf **Überprüfen**.
    
7. Zeichnen Sie das auf der Seite **Schritt 3: Keep your existing applications** angezeigte App-Kennwort für das Konto „Benutzer 2“ an einem sicheren Ort auf, und klicken Sie dann auf **Fertig**.
    
8. Wenn dies das erste Mal ist, dass Sie sich mit dem Konto „Benutzer 2“ angemeldet haben, werden Sie aufgefordert, das Kennwort zu ändern. Geben Sie das ursprüngliche Kennwort und dann zwei Mal ein neues Kennwort ein, und klicken Sie dann auf **Kennwort ändern und anmelden**. Zeichnen Sie das neue Kennwort an einem sicheren Ort auf.
    
    Office 365-Portal sollte für Benutzer 2 auf der Registerkarte **Microsoft Office Home** des Browsers angezeigt werden.
    
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Plan für die mehrstufige Authentifizierung für Office 365-Bereitstellungen](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

