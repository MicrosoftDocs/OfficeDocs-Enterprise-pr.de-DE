---
title: Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Zusammenfassung: Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.'
ms.openlocfilehash: c93900e07b8b9adbe0f1120eca77019b9dcc1eda
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897508"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.
  
Office 365 erweiterte eDiscovery können Sie schnell zu finden und Analysieren der relevanten Informationen über die Daten, die in Office 365, einschließlich e-Mails und Dokumente gespeichert ist. Dies kann große Datenmengen Zeit und Kosten, insbesondere in Situationen Rechtsstreitigkeiten sparen. Weitere Informationen finden Sie unter [Office 365 erweiterte eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Mit den Anweisungen in diesem Artikel erstellen Sie eine kleine Gruppe von Daten für eine fiktive Vertragsstreitigkeit und analysieren diese mit der Erweiterten eDiscovery.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der One Microsoft Cloud zu erhalten.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Wenn Sie erweiterte eDiscovery auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phase 2 und Phase 3 des [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).
  
Wenn Sie erweiterte eDiscovery in einer simulierten Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testen erweiterter eDiscovery erfordert keinen die simulierten Enterprise-Umgebung, einschließlich einer simulierten Intranet mit dem Internet verbunden und Directory-Synchronisierung für eine Windows Server Active Directory-Gesamtstruktur. Erfolgt hier als eine Option, damit Sie testen und experimentieren in einer Umgebung ausführen können, die eine typische Organisation darstellt. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Phase 2: Erstellen von Beispieldaten für die Erweiterte eDiscovery

In diesem Verfahren erstellen Sie E-Mail-Nachrichten, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.
  
1. Öffnen Sie Internet Explorer, und melden Sie sich unter [https://outlook.com](https://outlook.com) auf das Outlook-Konto, das Sie in Phase 2 des[Office 365 Dev/Test-Umgebung](office-365-dev-test-environment.md)erstellt haben.
    
  - Wenn Sie die einfache Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie den simulierten Test-/unternehmensumgebung verwenden, verwenden Sie das Azure-Portal ([https://portal.azure.com](https://portal.azure.com)) zum Verbinden mit dem virtuellen Computer CLIENT1, und melden Sie sich von CLIENT1 aus.
    
2. Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.
    
3. Geben Sie im Feld **an**die e-Mail-Adresse des Kontos User6 des Test-Abonnement ( **user6 @.** <organization name> **. onmicrosoft.com**).
    
4. Geben Sie für den Betreff **Test-E-Mail 1** ein.
    
5. Geben Sie in den Textbereich **Tailspin Vertragsentwurf** ein, und klicken Sie dann auf **Senden**.
    
6. Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.
    
7. Geben Sie unter **An** die E-Mail-Adresse des user6-Kontos Ihres Testabonnements ein.
    
8. Geben Sie für den Betreff **Test-E-Mail 2** ein.
    
9. Geben Sie in den Textbereich **Tailspin Geschäftsessen** ein, und klicken Sie dann auf **Senden**.
    
10. Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.
    
11. Geben Sie unter **An** die E-Mail-Adresse des user6-Kontos Ihres Testabonnements ein.
    
12. Geben Sie für den Betreff **Test-E-Mail 3** ein.
    
13. Geben Sie in den Textbereich **Tailspin vertragliche Unstimmigkeiten** ein, und klicken Sie dann auf **Senden**.
    
14. Klicken Sie auf das Symbol für Benutzer in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
15. Öffnen Sie eine neue Registerkarte, und melden Sie sich bei Office 365-Portal ([https://portal.office.com](https://portal.office.com)) mit den Kontonamen und das Kennwort des Kontos User6 des Test-Abonnement.
    
16. Klicken Sie auf der Registerkarte **Office 365-Portal** auf **E-Mail**.
    
17. Überprüfen Sie auf der Registerkarte **E-Mail - User6 - Outlook** , User6 alle drei e-Mails von Outlook-e-Mail-Kontos empfangen.
    
18. Wechseln Sie zurück zu Registerkarte **Office 365-Portal** für User6.
    
19. Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.
    
In diesem Verfahren erstellen Sie zwei Word-Dokumente, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.
  
1. Klicken Sie auf der Seite **Office** auf **Anmelden**, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos an.
    
2. Klicken Sie auf eine neue Registerkarte Zugriff auf die URL der Produktion SharePoint-Website: **https://** <fictional organization name> **.sharepoint.com/sites/production**
    
3. Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.
    
4. Geben Sie auf der Seite **Word Online****Tailspin-Vertrangsentwurf** ein, warten Sie, bis **Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite **Word Online**.
    
5. Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.
    
6. 	Geben Sie auf der Seite **Word Online****Tailspin-Vertrangsentwurf** ein, warten Sie, bis **Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite **Word Online**.
    
7. Auf der Registerkarte **Produktions-Websitesammlung** sollte nun **Dokument** und **Dokument1** in der Liste der Dokumente angezeigt werden.
    
8. Schließen Sie die Registerkarte **Produktions-Websitesammlung**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Phase 3: Verwenden Sie erweiterte eDiscovery gemeldet werden, rechtliche

Leider hat Beilegung eines Vertrag zwischen Ihrer Organisation und Tailspin Toys Zeitpunkt des rechtlichen erreicht. In diesem Verfahren erstellen und konfigurieren eine erweiterte eDiscovery-Fall zum Suchen und Analysieren von e-Mails und Dokumente, die den Text "Tailspin Vertrag" enthalten.
  
Der Prozess für die Verwendung der erweiterten eDiscovery ist wie folgt:
  
- Erstellen Sie eine Suche in das Wertpapier &amp; Compliance Center, analysieren Sie die Ergebnisse, und klicken Sie dann die Ergebnisse für erweiterte eDiscovery vorbereiten.
    
- Erstellen Sie und konfigurieren Sie einen Fall in der erweiterten eDiscovery, und analysieren Sie die Suchergebnisse.
    
In diesem Verfahren erstellen Sie eine Suche in das Wertpapier &amp; Compliance center für "Tailspin Vertrag", sehen die Ergebnisse, und bereiten Sie die Ergebnisse für erweiterte eDiscovery.
  
1. Klicken Sie auf der Registerkarte **Office 365-Portal** auf **Admin**.
    
2. Klicken Sie im linken Navigationsbereich der Admin Center-Registerkarte auf **Admin Center > Compliance**.
    
3. Klicken Sie auf die **Sicherheit &amp; Compliance** Registerkarte, klicken Sie auf **Berechtigungen**.
    
4. Doppelklicken Sie in der Liste **Berechtigungen** auf **Organisationsverwaltung**.
    
5. Klicken Sie im Fenster **Rollengruppe** unter **Mitglieder** auf das Pluszeichen (+).
    
6. Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.
    
7. Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.
    
8. Doppelklicken Sie in der Liste **Berechtigungen** auf **eDiscovery-Manager**.
    
9. Klicken Sie im Fenster **Rollengruppe** unter **eDiscovery-Administrator** auf das Pluszeichen.
    
10. Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.
    
11. Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.
    
12. Klicken Sie im linken Navigationsbereich auf **Suche &amp; Untersuchung > Inhaltssuche**.
    
13. Klicken Sie auf das Pluszeichen, um eine Suche hinzuzufügen.
    
14. Geben Sie im Fenster **Neue Suche** den Text **Tailspin Vertragsuche** unter **Name** ein.
    
15. Klicken Sie unter **Wo sollen wir suchen?** auf **Überall suchen**, wählen Sie **Exchange**, **SharePoint** und **Öffentliche Ordner** aus, und klicken Sie dann auf **Weiter**.
    
16. Geben Sie unter **Wonach sollen wir suchen?** den Text **Tailspin Vertrag** ein, und klicken Sie dann auf **Suche**.
    
17. Klicken Sie in der Liste von Suchvorgängen auf den Namen **Tailspin Vertragsuche**.
    
18. Klicken Sie im Bereich **Tailspin Vertrag Suche** unter **Ergebnisse**auf **Vorschau der Suchergebnisse** . Ein Fenster mit den beiden Dokumenten in der Produktion SharePoint-Website ( **Dokument** und **Document1**) und die **e-Mail testen 1** und **Test e-Mail 3** e-Mails an User6 sollte angezeigt werden. Schließen Sie das Fenster.
    
19. Klicken Sie im Bereich **Inhaltssuche** unter **Analysieren der Ergebnisse mit der erweiterten eDiscovery** auf **Ergebnisse für Analyse in Vorschau anzeigen**.
    
20. Klicken Sie im Fenster **Vorbereiten der Suchergebnisse für Tailspin Vertragsuche** auf **Vorbereiten** und warten Sie, bis der Vorgang abgeschlossen ist.
    
In diesem Verfahren erstellen Sie einen neuen Fall für die erweiterte eDiscovery und analysieren die Ergebnisse der Tailspin-Vertragsuche.
  
1. Klicken Sie im linken Navigationsbereich auf **eDiscovery** unter **Suche &amp; Untersuchung**.
    
2. Klicken Sie im Bereich **eDiscovery** auf **Zur erweiterten eDiscovery wechseln**.
    
3. Klicken Sie auf der Registerkarte **Erweiterte eDiscovery** auf das Pluszeichen, um einen neuen Fall hinzuzufügen.
    
4. 	Geben Sie im Bereich **Fall hinzufügen** den Text **Tailspin vertragliche Unstimmigkeit** unter **Name** ein, und klicken Sie dann auf **OK**. Warten Sie, bis der Fall erstellt wurde.
    
5. Doppelklicken Sie auf den Fall **Tailspin vertragliche Unstimmigkeit** in der Liste. 
    
6. Klicken Sie auf den Container **Tailspin Vertrag Suche** in der Liste **Container** , und klicken Sie dann auf **Prozess**. Warten Sie, bis die Verarbeitung für die Durchführung.
    
7. Wenn am unteren Rand des Fensters **Verarbeitung abgeschlossen** angezeigt wird, klicken Sie in der linken Navigation auf **Prozesszusammenfassung**, um eine Zusammenfassung anzuzeigen.
    
8. Klicken Sie auf der oberen Navigationsleiste auf **Analysieren**.
    
9. Geben Sie auf der Seite **Setup** unter **Designs** die Zahl **3** in **Maximale Anzahl von Designs** ein.
    
10. Klicken Sie auf **Analysieren** , und warten Sie für die Analyse abgeschlossen. Eine Reihe von Kreis-Diagrammen mit Analyse der Zielgruppe, Dokumente, e-Mail-Nachrichten und Anlagen sollte angezeigt werden. Weitere Informationen finden Sie unter [Ergebnisse anzeigen analysieren](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Sie können diese Umgebung jetzt verwenden, um neue Inhalte, neue Suchvorgänge und neue Fälle zu erstellen und um weiter mit der erweiterten eDiscovery in Office 365 zu experimentieren.
  
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


