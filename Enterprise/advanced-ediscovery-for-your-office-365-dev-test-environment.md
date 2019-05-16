---
title: Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 'Zusammenfassung: Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.'
ms.openlocfilehash: df506b6637d28387fae7587e081251fd81e1ce1a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068341"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Advanced eDiscovery für die Office 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Konfigurieren und Demonstrieren der Erweiterten eDiscovery in Office 365 mit Beispieldaten in der Office 365-Entwicklungs-/Testumgebung.
  
Mit Office 365 Advanced eDiscovery können Sie wichtige Informationen über die in Office 365 gespeicherten Daten schnell finden und analysieren, einschließlich e-Mails und Dokumente. Auf diese Weise können, insbesondere bei Rechtsstreitigkeiten, enorme Zeit- und Geldmengen gespart werden. Weitere Informationen finden Sie unter [Erweiterte eDisvocery in Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).
  
Mit den Anweisungen in diesem Artikel erstellen Sie eine kleine Gruppe von Daten für eine fiktive Vertragsstreitigkeit und analysieren diese mit der Erweiterten eDiscovery.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Wenn Sie Advanced eDiscovery auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phase 2 und Phase 3 von [Office 365 dev/Test Environment](office-365-dev-test-environment.md).
  
Wenn Sie die erweiterte eDiscovery in einem simulierten Unternehmen testen möchten, befolgen Sie die Anweisungen unter [Dirsync für Ihre Office 365 dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Das Testen von Advanced eDiscovery erfordert nicht die simulierte Unternehmensumgebung, die ein simuliertes Intranet enthält, das mit dem Internet und der Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) verbunden ist. Sie wird hier als Option bereitgestellt, damit Sie Tests und experimentieren in einer Umgebung ausführen können, die eine typische Organisation darstellt. 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>Phase 2: Erstellen von Beispieldaten für die Erweiterte eDiscovery

In diesem Verfahren erstellen Sie E-Mail-Nachrichten, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.
  
1. Öffnen Sie Internet Explorer, und melden [https://outlook.com](https://outlook.com) Sie sich bei dem Outlook-Konto an, das Sie in Phase 2 von[Office 365 dev/Test Environment](office-365-dev-test-environment.md)erstellt haben.
    
  - Wenn Sie die einfache Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung von Internet Explorer, und melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie die simulierte Enterprise-dev/Test-Umgebung verwenden, verwenden Sie[https://portal.azure.com](https://portal.azure.com)das Azure-Portal (), um eine Verbindung mit dem virtuellen Computer Client1 herzustellen, und melden Sie sich dann bei CLIENT1 an.
    
2. Klicken Sie auf der Registerkarte **Outlook-Mail** auf **Neu**.
    
3. Geben **Sie unter an**die e-Mail-Adresse des User6-Kontos Ihres Testabonnements ein ( **User6 @.**<organization name> **. onmicrosoft.com**).
    
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
    
14. Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.
    
15. Öffnen Sie eine neue Registerkarte, und melden Sie sich beim Office[https://www.office.com](https://www.office.com)365-Portal () mit dem Kontonamen und dem Kennwort des User6-Kontos Ihres Testabonnements an.
    
16. Klicken Sie auf der Registerkarte **Office 365-Portal** auf **E-Mail**.
    
17. Überprüfen Sie auf der Registerkarte **Mail-User6-Outlook** , ob User6 alle drei e-Mails aus dem Outlook-e-Mail-Konto erhalten hat.
    
18. Wechseln Sie zurück zu Registerkarte **Office 365-Portal** für User6.
    
19. Klicken Sie oben rechts auf das Benutzersymbol, und klicken Sie dann auf **Abmelden**.
    
In diesem Verfahren erstellen Sie zwei Word-Dokumente, die Sie später in einem erweiterten eDiscovery-Fall analysieren werden.
  
1. Klicken Sie auf der Seite **Office** auf **Anmelden**, melden Sie sich mit den Anmeldeinformationen des globalen Administratorkontos an.
    
2. Greifen Sie auf einer neuen Registerkarte auf die URL Ihrer Produktions-SharePoint-Website zu: **https://** <fictional organization name> **. SharePoint.com/Sites/Production**
    
3. Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.
    
4. Geben Sie auf der Seite **Word Online****Tailspin-Vertrangsentwurf** ein, warten Sie, bis **Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite **Word Online**.
    
5. Klicken Sie auf der Registerkarte **Produktions-Websitesammlung** unter **Dokumente** auf **Neu > Word-Dokument**.
    
6. 	Geben Sie auf der Seite **Word Online****Tailspin-Vertrangsentwurf** ein, warten Sie, bis **Gespeichert** im Titel angezeigt wird, und schließen Sie dann die Seite **Word Online**.
    
7. Auf der Registerkarte **Produktions-Websitesammlung** sollte nun **Dokument** und **Dokument1** in der Liste der Dokumente angezeigt werden.
    
8. Schließen Sie die Registerkarte **Produktions-Websitesammlung**.
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>Phase 3: Verwenden von Advanced eDiscovery für eine Rechtsstreitigkeit

Leider ist es bei einer vertraglichen Streitigkeit zwischen Ihrer Organisation und Tailspin Toys zu einem Gerichtsverfahren gekommen. In diesem Verfahren erstellen und konfigurieren Sie einen erweiterten eDiscovery-Fall, um e-Mails und Dokumente zu suchen und zu analysieren, die den Text "Tailspin Contract" enthalten.
  
Der Prozess für die Verwendung der erweiterten eDiscovery ist wie folgt:
  
- Erstellen Sie eine Suche im Security &amp; Compliance Center, analysieren Sie die Ergebnisse, und bereiten Sie die Ergebnisse für die erweiterte eDiscovery vor.
    
- Erstellen Sie und konfigurieren Sie einen Fall in der erweiterten eDiscovery, und analysieren Sie die Suchergebnisse.
    
In diesem Verfahren erstellen Sie eine Suche im Security &amp; Compliance Center für "Tailspin Contract", schauen Sie sich die Ergebnisse an, und bereiten Sie dann die Ergebnisse für Advanced eDiscovery vor.
  
1. Klicken Sie auf der Registerkarte **Office 365-Portal** auf **Admin**.
    
2. Klicken Sie im linken Navigationsbereich der Admin Center-Registerkarte auf **Admin Center > Compliance**.
    
3. Klicken Sie auf der Registerkarte ** &amp; Sicherheitskonformität** auf **Berechtigungen**.
    
4. Doppelklicken Sie in der Liste **Berechtigungen** auf **Organisationsverwaltung**.
    
5. Klicken Sie im Fenster **Rollengruppe** unter **Mitglieder** auf das Pluszeichen (+).
    
6. Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.
    
7. Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.
    
8. Doppelklicken Sie in der Liste **Berechtigungen** auf **eDiscovery-Manager**.
    
9. Klicken Sie im Fenster **Rollengruppe** unter **eDiscovery-Administrator** auf das Pluszeichen.
    
10. Doppelklicken Sie im Fenster **Auswählen von Mitgliedern** auf den Namen Ihres Administratorkontos, und klicken Sie dann auf **OK**.
    
11. Klicken Sie im Fenster **Rollengruppe** auf **Speichern**.
    
12. Klicken Sie im linken Navigationsbereich auf Such ** &amp; Untersuchung > Inhaltssuche**.
    
13. Klicken Sie auf das Pluszeichen, um eine Suche hinzuzufügen.
    
14. Geben Sie im Fenster **Neue Suche** den Text **Tailspin Vertragsuche** unter **Name** ein.
    
15. Klicken Sie unter **Wo sollen wir suchen?** auf **Überall suchen**, wählen Sie **Exchange**, **SharePoint** und **Öffentliche Ordner** aus, und klicken Sie dann auf **Weiter**.
    
16. Geben Sie unter **Wonach sollen wir suchen?** den Text **Tailspin Vertrag** ein, und klicken Sie dann auf **Suche**.
    
17. Klicken Sie in der Liste von Suchvorgängen auf den Namen **Tailspin Vertragsuche**.
    
18. Klicken Sie im Bereich **Tailspin Vertragsuche** auf **Vorschau der Suchergebnisse** unter **Ergebnisse**. Es sollte ein Fenster mit den beiden Dokumenten auf der Produktions-SharePoint-Website ( **Dokument** und **document1**) und der **Test-e-Mail 1** und **e-Mail-** Nachrichten mit e-Mails an User6 angezeigt werden. Schließen Sie das Fenster.
    
19. Klicken Sie im Bereich **Inhaltssuche** unter **Analysieren der Ergebnisse mit der erweiterten eDiscovery** auf **Ergebnisse für Analyse in Vorschau anzeigen**.
    
20. Klicken Sie im Fenster **Vorbereiten der Suchergebnisse für Tailspin Vertragsuche** auf **Vorbereiten** und warten Sie, bis der Vorgang abgeschlossen ist.
    
In diesem Verfahren erstellen Sie einen neuen Fall für die erweiterte eDiscovery und analysieren die Ergebnisse der Tailspin-Vertragsuche.
  
1. Klicken Sie im linken Navigationsbereich unter ** &amp; Such Prüfung**auf **eDiscovery** .
    
2. Klicken Sie im Bereich **eDiscovery** auf **Zur erweiterten eDiscovery wechseln**.
    
3. Klicken Sie auf der Registerkarte **Erweiterte eDiscovery** auf das Pluszeichen, um einen neuen Fall hinzuzufügen.
    
4. 	Geben Sie im Bereich **Fall hinzufügen** den Text **Tailspin vertragliche Unstimmigkeit** unter **Name** ein, und klicken Sie dann auf **OK**. Warten Sie, bis der Fall erstellt wurde.
    
5. Doppelklicken Sie auf den Fall **Tailspin vertragliche Unstimmigkeit** in der Liste. 
    
6. Klicken Sie in der Liste **Container** auf den **Suchcontainer Tailspin Contract** , und klicken Sie dann auf **verarbeiten**. Warten Sie, bis die Bearbeitung abgeschlossen ist.
    
7. Wenn am unteren Rand des Fensters **Verarbeitung abgeschlossen** angezeigt wird, klicken Sie in der linken Navigation auf **Prozesszusammenfassung**, um eine Zusammenfassung anzuzeigen.
    
8. Klicken Sie auf der oberen Navigationsleiste auf **Analysieren**.
    
9. Geben Sie auf der Seite **Setup** unter **Designs** die Zahl **3** in **Maximale Anzahl von Designs** ein.
    
10. Klicken Sie auf **Analysieren** und warten Sie, bis die Analyse abgeschlossen ist. Es sollte eine Reihe von Kreisdiagrammen mit der Analyse der Zielgruppe, Dokumenten, E-Mails und Anlagen angezeigt werden. Weitere Informationen finden Sie unter [Anzeigen von Analyseergebnissen](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).
    
Sie können diese Umgebung jetzt verwenden, um neue Inhalte, neue Suchvorgänge und neue Fälle zu erstellen und um weiter mit der erweiterten eDiscovery in Office 365 zu experimentieren.
  
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security für Ihre Office 365-Entwicklungs-/Testumgebung](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


