---
title: Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Zusammenfassung: Konfigurieren und Demonstrieren von Office 365 Advanced Threat Protection in der Office 365-Entwicklungs-/Testumgebung'
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914960"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a>Advanced Threat Protection für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren und Demonstrieren von Office 365 Advanced Threat Protection in der Office 365-Entwicklungs-/Testumgebung
  
Office 365 Advanced Threat Protection (ATP) ist ein Feature von Exchange Online Protection (EOP), das Ihnen hilft, Schadsoftware von Ihrer E-Mail fernzuhalten. Mit ATP erstellen Sie Richtlinien im Exchange Admin Center (EAC) oder im Security &amp; Compliance Center, die helfen sicherzustellen, dass Ihre Benutzer nur auf Links oder Anlagen in E-Mails zugreifen, die als nicht schädlich identifiziert werden. Weitere Informationen finden Sie unter [Advanced Threat Protection für Safe Attachments und Safe Links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).
  
Mit den Anweisungen in diesem Artikel konfigurieren und testen Sie ATP in Ihrem Office 365-Testabonnement.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung

Wenn Sie ATP nur auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in den Phasen 2 und 3 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md).
  
Wenn Sie ATP in einem simulierten Unternehmen testen möchten, führen Sie die Schritte in [DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md) aus.
  
> [!NOTE]
> Für das Testen von ATP ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie ATP testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a>Phase 2: Demonstrieren des standardmäßigen E-Mail-Zustellungsverhaltens von Office 365

In dieser Phase führen Sie vor, dass vor dem Konfigurieren von ATP-Richtlinien potenziell schädliche E-Mails ohne Prüfung oder Maßnahmen zur Risikominderung in Office 365-Postfächer übermittelt werden.
  
1. Öffnen Sie Internet Explorer, und melden Sie sich an dem Outlook-Konto an, das Sie in Phase 2 von [Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md) erstellt haben.
    
  - Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das [Azure-Portal](https://portal.azure.com), um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.
    
2. Öffnen Sie Editor, und geben Sie einen Text ein.
    
3. Speichern Sie die Datei im Ordner „Dokumente" als **getKeys.js**.
    
4. Klicken Sie auf der Registerkarte „Outlook-Mail" von Internet Explorer auf **Neu**.
    
5. Geben Sie in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein.
    
6. Geben Sie für den Betreff **Ihre neuen Schlüssel** ein.
    
7. Geben Sie in den Textbereich **Hier ist die Datei** ein.
    
8. Klicken Sie auf **Anfügen**, doppelklicken Sie im Ordner „Dokumente" auf **getKeys.js**, klicken Sie auf **Als Kopie anfügen**, und klicken Sie dann auf **Senden**.
    
9. Klicken Sie auf **Neu**.
    
10. Geben Sie in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein.
    
11. Geben Sie als Betreff **Neue Reisewebsite** ein.
    
12. Geben Sie in den Textbereich **Jemand hat diese Website an mich weitergeleitet** ein.
    
13. Markieren Sie im Textbereich den Text **diese Website**, und klicken Sie auf der Symbolleiste auf das Linksymbol.
    
14. Geben Sie unter **URL** **http://www.spamlink.contoso.com/**, klicken Sie auf **OK**, und klicken Sie dann auf **Senden**.
    
15. Öffnen eine separate Instanz von Internet Explorer im Modus für private durchsuchen, wechseln Sie Office 365-Portal ([https://portal.office.com](https://portal.office.com)), und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.
    
16. Klicken Sie auf der Hauptportalseite auf die Kachel „apps" und dann auf **E-Mail**.
    
17. Klicken Sie im Posteingang auf die Nachricht mit dem Betreff **Ihre neuen Schlüssel**.
    
18. Klicken Sie im Ordner „Junk-E-Mail" auf die Nachricht mit dem Betreff **Neue Reisewebsite**. Klicken Sie in der Nachricht auf den Link **diese Website**. Sie sollten in etwa folgende Seite sehen: „Fehler! spamlink.contoso.com konnte nicht gefunden werden". Dies ist das richtige Ergebnis, da es keine Webseite an dieser Position gibt.
    
Beachten Sie, dass beide dieser potenziell schädlichen E-Mails erfolgreich übermittelt wurden. Die E-Mail **Ihre neuen Schlüssel** könnte nicht erkannte Schadsoftware enthalten, und es wird nicht verhindert, dass der Benutzer auf den potenziell bösartigen Link in der E-Mail **Neue Reisewebsite** klickt.
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a>Phase 3: Konfigurieren von Richtlinien für sichere Anlagen und sichere Links für ATP

In dieser Phase erstellen und konfigurieren Sie eine Richtlinie für sichere Anlagen, um die Übermittlung von E-Mails mit potenziell schädlichen Anlagen zu verhindern, und eine Richtlinie für sichere Links, um zu verhindern, dass Benutzer potenziell unsichere URLs besuchen.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** in Internet Explorer auf die Kachel **Admin**.
    
2. Klicken Sie im linken Navigationsbereich auf **Admin Center** und dann auf **Exchange**.
    
3. Klicken Sie im linken Navigationsbereich der Admin Center-Registerkarte für Exchange auf **Komplexe Bedrohungen**.
    
4. Klicken Sie auf die Registerkarte **Sichere Anlagen** und dann auf das Pluszeichen (+).
    
5. Geben Sie im Fenster **Neue Richtlinie für sichere Anlagen** in **Name** den Wert **Richtlinie für sichere Anlagen - Blockieren** ein.
    
6. Klicken Sie für **Reaktion für sichere Anlagen bei unbekannter Schadsoftware** auf **Blockieren**.
    
7. Klicken Sie für **Anlage bei Erkennung umleiten** auf **Umleitung aktivieren**, und geben Sie die E-Mail-Adresse des Kontos Ihres globalen Office 365-Administrators ein.
    
8. Klicken Sie für **Angewendet auf** auf den Pfeil nach unten, und klicken Sie dann auf **Die Empfängerdomäne ist**. Klicken Sie im Fenster auf den Namen Ihrer Organisation (z. B. contoso.onmicrosoft.com), und klicken Sie dann auf **OK**.
    
9. Klicken Sie auf **Speichern**. Nach dem Update sollte die neue und aktivierte **Richtlinie für sichere Anlagen - Blockieren** angezeigt werden.
    
10. Klicken Sie auf die Registerkarte **Sichere Links** und dann auf das Pluszeichen (+).
    
11. Geben Sie im Fenster **Neue Richtlinie für sichere Links** in **Name** **Richtlinie für sichere Links** ein.
    
12. Klicken Sie für **Wählen Sie die Aktion für unbekannte, potenziell bösartige URLs in Nachrichten aus** auf **Ein**, und wählen Sie dann **Benutzern das Durchklicken zur ursprünglichen URL nicht gestatten** aus.
    
13. Klicken Sie für **Angewendet auf** auf den Pfeil nach unten, und klicken Sie dann auf **Die Empfängerdomäne ist**. Klicken Sie im Fenster auf den Namen Ihrer Organisation (z. B. contoso.onmicrosoft.com), und klicken Sie dann auf **OK**.
    
14. Klicken Sie auf **Speichern**. Nun sollte die neue und aktivierte **Richtlinie für sichere Links** angezeigt werden.
    
## <a name="phase-4-show-atp-in-action"></a>Phase 4: Vorführen von ATP in Aktion

In dieser Phase führen Sie vor, wie ATP potenziell schädliche E-Mails behandelt.
  
1. Klicken Sie in der Instanz von Internet Explorer, die Sie in Phase 2 zum Senden von E-Mail verwendet haben, im linken Navigationsbereich auf **Gesendete Elemente**.
    
2. Klicken Sie auf die E-Mail mit dem Titel **Ihre neuen Schlüssel**, klicken Sie auf den Dropdownpfeil, und klicken Sie dann auf **Weiterleiten**.
    
3. Geben Sie für die neue Nachricht in **An** die E-Mail-Adresse für den Namen des globalen Office 365-Administrators Ihres Testabonnements ein. Klicken Sie anschließend auf **Senden**
    
4. Klicken Sie auf die E-Mail mit dem Titel **Neue Reisewebsite**, klicken Sie auf auf den Dropdownpfeil, klicken Sie auf **Allen antworten**, und klicken Sie dann auf **Senden**.
    
5. Klicken Sie in der Instanz von Internet Explorer, die Sie in Phase 3 zum Konfigurieren von ATP-Richtlinien verwendet haben, auf die Admin Center-Registerkarte für Exchange, dann auf die Kachel „apps" und dann auf **E-Mail**. Im Posteingang sollten zwei neue E-Mail-Nachrichten angezeigt werden:
    
  - Eine mit dem Titel **WG: Ihre neuen Schlüssel**
    
  - Eine mit dem Titel **WG: Neue Reisewebsite**
    
6. Öffnen Sie die E-Mail-Nachricht mit dem Titel **WG: Neue Reisewebsite**, und klicken Sie auf den Link **diese Website**. Es sollte eine Seite „Diese Website wurde als böswillig klassifiziert" angezeigt werden. Dies zeigt, dass ATP den Zugriff auf die potenziell bösartige Website verhindert.
    
7. Klicken Sie auf der Admin Center-Registerkarte für Exchange von Internet Explorer im linken Navigationsbereich auf **E-Mail-Fluss**.
    
8. Klicken Sie auf die Registerkarte **Nachrichtenablaufverfolgung**, und klicken Sie dann auf **Suche**.
    
9. Doppelklicken Sie im Fenster **Ergebnisse der Nachrichtenablaufverfolgung** auf die Nachricht mit dem Betreff **Ihre neuen Schlüssel**. Diese Nachricht wurde erfolgreich in den Posteingang zugestellt. Schließen Sie dieses Fenster.
    
10. Doppelklicken Sie auf die Nachricht mit dem Betreff **Neue Reisewebsite**. Diese Nachricht wurde erfolgreich in den Posteingang zugestellt. Schließen Sie dieses Fenster.
    
11. Doppelklicken Sie auf die Nachricht mit dem Betreff **WG: Ihre neuen Schlüssel**. Beachten Sie, wie diese Nachricht von ATP verarbeitet und dann in den Posteingang übermittelt wurde. Schließen Sie dieses Fenster.
    
    > [!NOTE]
    > Der Zweck der Richtlinie für sichere Anlagen war es, Anlagen auf bösartigen Code zu scannen. Die Anlage "getKeys.js" wurde zugelassen, da nicht festgestellt wurde, dass sie bösartig ist. Dieser Schritt zeigt, dass ATP eine Überprüfung der Anlage durchgeführt hat. 
  
12. Doppelklicken Sie auf die Nachricht mit dem Betreff **WG: Neue Reisewebsite**. Beachten Sie, dass diese Nachricht erfolgreich in den Posteingang übermittelt wurde.
    
Sie können diese Umgebung jetzt verwenden, um neue Richtlinien zu erstellen und mit ATP zu experimentieren.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md) 

[Advanced Threat Protection für Safe Attachments und Safe Links](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


