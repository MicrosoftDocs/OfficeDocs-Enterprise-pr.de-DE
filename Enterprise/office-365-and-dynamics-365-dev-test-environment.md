---
title: Office 365- und Dynamics 365-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Zusammenfassung: Verwenden dieser Test Lab Guide für Ihre Office 365-Umgebung Test-/Dynamics 365 hinzufügen.'
ms.openlocfilehash: 00d5cc0fd347aff7e201056f6af9ca271008d285
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365- und Dynamics 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Verwenden Sie in diesem Test Lab Guide Dynamics 365 Ihre Office 365 Dev/Test-Umgebung hinzufügen.
  
Mit den Anweisungen in diesem Artikel fügen Sie der Organisation Ihrer Office 365-Entwicklungs-/Testumgebung ein Dynamics 365-Testabonnement hinzu und erstellen so eine Office 365- und Dynamics 365-Entwicklungs-/Testumgebung.

![Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](images/o365-dynamics365-dev-test.png)
  
  
Sie können ein Dynamics 365-Testabonnement verwenden, um die Funktionen von Dynamics 365 zu demonstrieren. Die folgenden Lösungen sind in einer Dynamics 365 Plan 1, Enterprise Edition-Testversion enthalten:
  
- [Microsoft Dynamics 365 für Sales](https://www.microsoft.com/dynamics365/sales). Erhöhen Sie Ihre Umsätze mit Automatisierung und digitalen Intelligence unterstützen die Vertriebsmitarbeiter konzentrieren und Intelligenter arbeiten.
    
- [Microsoft Dynamics 365 Customer Service](https://www.microsoft.com/dynamics365/customer-service). Verdienen Sie können Ihre Agenten erteilen Sie die ausführliche Informationen und die digitalen Intelligence nahtlos Serverausfalls benötigten.
    
- [Microsoft Dynamics 365 für Dienst dar](https://www.microsoft.com/dynamics365/field-service). Master-Shape der Dienst aufrufen, indem Sie Optimieren Ihrer Zeitpläne, und rüstete Ihrer Mitarbeiter und vorhersehbare Tools Gewinn steigern verwenden.
    
- [Microsoft Dynamics 365 für Project Service-Automatisierung](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Abgeschlossen Sie Ihre Projekte erfolgreich wurde, und erstellen Sie gewinnbringenden Beziehungen mit produktive Mitarbeitern und intelligente Tools.
    
Sie können eine oder mehrere der oben genannten Versionen im Rahmen des Dynamics 365-Testabonnements testen.
  
![Testumgebungsanleitungen in der Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Phase 1: Erstellen einer einfachen oder simulierten Office 365-Unternehmensentwicklungs-/-testumgebung

Wenn Sie Office 365 und Dynamics 365 auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phasen 2 und 3 von [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).
  
Wenn Sie Office 365 und Dynamics 365 für eine simulierte Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).

![Die Office 365-Entwicklungs-/Testumgebung](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> Für die Konfiguration in diesem Artikel ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie mit Office 365 und Dynamics 365 in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Phase 2: Hinzufügen eines Dynamics 365-Testabonnements

In dieser Phase registrieren Sie sich für das Dynamics 365-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Registrieren für ein Dynamics 365-Testabonnement

1. Mit einem Browser auf einem Ihrer Desktopcomputer (Lightweight) oder von CLIENT1 (simuliert Enterprise), melden Sie sich bei Office 365-Portal unter [https://portal.office.com](https://portal.office.com) mit den Anmeldeinformationen Ihres Kontos globaler Administrator.
    
2. Klicken Sie auf die Kachel **Admin**.
    
3. Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Dynamics 365 Plan 1 Enterprise Edition**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.

![Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](images/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> Das Testabonnement für Dynamics 365 Plan 1 Enterprise Edition läuft über 30 Tage. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Phase 3: Zuweisen von Dynamics 365-Lizenzen und Systemadministratoren

In dieser Phase weisen den Konten des globalen Administrators, von Benutzer 2 und Benutzer 3 Dynamics 365-Lizenzen hinzu und machen diese zu Systemadministratoren.
  
Gehen Sie folgendermaßen vor, um Dynamics-365-Lizenzen zuzuweisen.
  
1. Klicken Sie auf der Registerkarte **Office 365 Admin Center** auf **Benutzer > Aktive Benutzer**.
    
2. Klicken Sie in der Liste der aktiven Benutzer auf Ihr globales Administratorkonto, und klicken Sie dann auf **Bearbeiten** für **Produktlizenzen**.
    
3. 	Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Dynamics 365 Plan 1 Enterprise Edition** auf **On**. Klicken Sie auf **Speichern** und anschließend zweimal auf **Schließen**.
    
4. Führen Sie die Schritte 2 und 3 für Benutzer 2- und Benutzer 3-Konten durch.
    
5. Schließen Sie die Registerkarte **Office Admin Center**.
    
Konfigurieren Sie anhand dieser Schritte die Benutzer 2- und Benutzer 3-Konten als Dynamics 365-Systemadministratoren.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **Admin**.
    
2. Klicken Sie auf der Registerkarte **Office-Verwaltungskonsole** im linken Navigationsbereich auf **Admin centers**, und klicken Sie dann auf **Dynamics 365**.
    
    Möglicherweise müssen Sie warten, bis die Bereitstellung von Dynamics 365 abgeschlossen ist, damit Dynamics 365 im Menü angezeigt wird.
    
3. Klicken Sie auf der Registerkarte „Dynamics 365“ auf **Alle** und dann auf **Einrichtung abschließen**.
    
    Warten Sie, bis die Einrichtung abgeschlossen ist.
    
    Sobald die Einrichtung abgeschlossen ist, wird ein Vertriebsaktivitäts-Dashboard mit Beispieldaten angezeigt, die zum Testabonnement gehören. Nehmen Sie sich kurz Zeit, um sich das **Willkommensvideo** anzusehen. Schließen Sie das Videofenster, sobald das Video zu Ende ist.
    
4. Klicken Sie auf der Symbolleiste oben auf den Nach-unten-Pfeil neben **Vertrieb**. Klicken Sie auf **Einstellungen** und dann auf **Sicherheit**.
    
5. Klicken Sie auf der Seite **Sicherheit** auf **Benutzer**.
    
6. Klicken Sie in der Benutzerliste auf **Benutzer 2**.
    
7. Klicken Sie in der Symbolleiste auf **Rollen verwalten**.
    
8. Klicken Sie unter **Rollen verwalten** auf **Systemadministrator** und dann auf **OK**.
    
9. Klicken Sie auf der Symbolleisten oben auf **Sicherheit**.
    
10. Wiederholen Sie die Schritte 5 bis 8 für das Konto „Benutzer 3“.
    
11. Schließen Sie die Registerkarte **Benutzer: Benutzer 3**.
    
> [!NOTE]
> Ihrem globalen Office 365-Administratorkonto wurde automatisch die Rolle des Dynamics 365-Systemadministrators zugewiesen. 
  
Ihre Office 365- und Dynamics 365-Entwicklungs-/Testumgebung umfasst nun Folgendes:
  
- Office 365 E5 Enterprise- und Dynamics 365-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten mit Ihrer Liste von Benutzerkonten.
    
- Das globale Administratorkonto für Ihr Unternehmen sowie die Konten „Benutzer 2“ und „Benutzer 3“ sind so konfiguriert, dass sie sowohl Office 365 E5 Enterprise als auch Dynamics 365 verwenden dürfen. Sie alle sind zudem Dynamics 365-Systemadministratoren.
    
## <a name="next-step"></a>Nächster Schritt

Konfigurieren Sie, und führen Sie dann vor, wie Office 365 und Dynamics 365 in der Exchange Online-Postfächer mit [Exchange Online-Integration für Ihre Umgebung für Office 365 und Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)Test-/zusammenarbeiten.
  
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)

[Abonnement-Verwaltung für Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Verwalten von Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


