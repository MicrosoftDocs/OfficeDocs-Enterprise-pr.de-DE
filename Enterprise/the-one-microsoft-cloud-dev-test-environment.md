---
title: Die One Microsoft Cloud-Entwicklungs-/Testumgebung
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um eine Entwicklungs-/Testumgebung zu erstellen, die alle Microsoft-Cloudangebote enthält.'
ms.openlocfilehash: 0ccea58e86f2e105704aac01ba4379c21a174e3a
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "30573659"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>Die One Microsoft Cloud-Entwicklungs-/Testumgebung

 **Zusammenfassung**: Verwenden Sie diese Testumgebungsanleitung, um eine Entwicklungs-/Testumgebung zu erstellen, die alle Microsoft-Cloudangebote enthält.
  
Mit den Anweisungen in diesem Artikel erstellen Sie ein simuliertes Intranet in Microsoft Azure-Infrastrukturdiensten und fügen dann Abonnements für Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS) und Microsoft Dynamics 365 hinzu. Das Ergebnis ist eine vereinfachte Organisation, die alle Microsoft-Cloudangebote gleichzeitig in einer einzigen Entwicklungs-/Testumgebung nutzt.  
  
![Phase 3 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365, EMS und Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
Die daraus resultierende Konfiguration bietet Ihnen die folgenden Möglichkeiten:
  
- Erleben Sie die Integration in den Microsoft-Cloudangeboten, z. B. die gemeinsame Identitätsinfrastruktur, die von Azure Active Directory (AD) bereitgestellt wird.
    
- Werten Sie End-to-End-Szenarios aus, die mehrere Microsoft-Cloudangebote umfassen.
    
- Erstellen Sie eine Demo, Machbarkeitsstudie oder Entwicklungs-/Testkonfiguration, die mehrere Microsoft-Cloudangebote nutzt.
    
- Bauen Sie Ihre Qualifikation in Bezug auf die Microsoft Cloud zur beruflichen Weiterentwicklung aus.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>Phase 1: Erstellen eines simulierten Intranets und Hinzufügen von Office 365

Folgen Sie den Anweisungen unter [DirSync für Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md).
  
Abbildung 1 zeigt die resultierende Konfiguration, die Office 365 und ein simuliertes Intranet enthält, das in Azure-Infrastrukturdiensten ausgeführt wird, und für die die Verzeichnissynchronisierung von einer lokalen Windows Server Active Directory (AD)-Gesamtstruktur aus erfolgt.
  
**Abbildung 1: Das simulierte Intranet in Azure mit Office 365**

![Die Office 365-Entwicklungs-/Testumgebung mit DirSync](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> Die Azure-Testversion ist 30 Tage gültig. Das Testabonnement für Office 365 Enterprise E5 hat eine Laufzeit von 30 Tagen, die problemlos um weitere 30 Tage verlängert werden kann. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues kostenpflichtiges Azure-Abonnement und ein neues kostenpflichtiges Office 365 Enterprise E5-Abonnement mit einer kleinen Anzahl von Lizenzen. 
  
## <a name="phase-2-add-ems"></a>Phase 2: Hinzufügen von EMS

In dieser Phase registrieren Sie sich für das EMS-Testabonnement und fügen es derselben Organisation wie Ihr Office 365-Testabonnement hinzu.
  
1. Melden Sie sich über einen Browser auf Ihrem Desktopcomputer oder von CLIENT1 aus beim Office 365-Portal unter [https://www.office.com](https://www.office.com) an. Verwenden Sie die Anmeldeinformationen Ihres globalen Administratorkontos.
    
2. Klicken Sie auf die Kachel **Admin**.
    
3. Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Enterprise Mobility + Security E5**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
> [!NOTE]
> Das Testabonnement für Enterprise Mobility + Security E5 ist 90 Tage gültig. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen. 
  
Als Nächstes aktivieren Sie die Enterprise Mobility + Security E5-Lizenz für alle Benutzerkonten.
  
1. Klicken Sie auf der Registerkarte **Office 365 Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Benutzer > Aktive Benutzer**.
    
2. Klicken Sie auf Ihr globales Administratorkonto und dann auf **Bearbeiten**, um die **Produktlizenzen** anzuzeigen.
    
3. Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Enterprise Mobility + Security E5** auf **On**. Klicken Sie auf **Speichern** und dann auf **Schließen**.
    
4. Führen Sie die Schritte 2 und 3 für alle Ihre anderen Konten aus (Benutzer1, Benutzer 2, Benutzer 3, Benutzer 4 und Benutzer 5).
    
Ihre Entwicklungs-/Testumgebung verfügt nun über Folgendes:
  
- Ein simuliertes Intranet, das in Azure-Infrastrukturdiensten ausgeführt wird.
    
- Office 365 E5 Enterprise- und EMS-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten mit Ihrer Liste von Benutzerkonten.
    
- Alle Ihre Benutzerkonten, aktiviert für die Verwendung von Office 365 E5 Enterprise und EMS.
    
Abbildung 2 zeigt die Konfiguration nach dem Hinzufügen von EMS.
  
**Abbildung 2: Das simulierte Intranet in Azure mit Office 365 und EMS**

![Phase 2 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365 und EMS](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>Phase 3: Hinzufügen von Dynamics 365

In dieser Phase registrieren Sie sich für das Dynamics 365-Testabonnement und fügen es derselben Organisation wie Ihre Office 365- und EMS-Testabonnements hinzu.
  
1. Melden Sie sich über einen Browser auf Ihrem Desktopcomputer oder von CLIENT1 aus beim Office 365-Portal unter [https://www.office.com](https://www.office.com) an. Verwenden Sie die Anmeldeinformationen Ihres globalen Administratorkontos.
    
2. Klicken Sie auf die Kachel **Admin**.
    
3. Klicken Sie auf der Registerkarte **Microsoft 365 Admin Center** im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Dynamics 365 Plan 1 Enterprise Edition**. Platzieren Sie den Mauszeiger auf dem Artikelnamen, und klicken Sie auf **Start free trial**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
> [!NOTE]
> Das Testabonnement für Dynamics 365 Plan 1 Enterprise Edition läuft über 30 Tage. Sie können das Testabonnement einfach um weitere 30 Tage verlängern. Für eine dauerhafte Entwicklungs-/Testumgebung erstellen Sie ein neues bezahltes Abonnement mit einer kleinen Anzahl von Lizenzen. 
  
Führen Sie diese Schritte aus, um den Konten des globalen Administrators sowie den Konten von Benutzer 2 und Benutzer 3 Dynamics 365-Lizenzen zuzuweisen und sie zu Systemadministratoren zu machen.
  
1. Klicken Sie auf der Registerkarte **Microsoft 365 Admin Center** auf **Benutzer > Aktive Benutzer**.
    
2. Klicken Sie in der Liste der aktiven Benutzer auf Ihr globales Administratorkonto, und klicken Sie dann auf **Bearbeiten** für **Produktlizenzen**.
    
3. 	Setzen Sie im Bereich **Product licenses** die Produktlizenz für **Dynamics 365 Plan 1 Enterprise Edition** auf **On**. Klicken Sie auf **Speichern** und anschließend zweimal auf **Schließen**.
    
4. Führen Sie die Schritte 2 und 3 für Benutzer 2- und Benutzer 3-Konten durch.
    
5. Schließen Sie die Registerkarte **Microsoft 365 Admin Center**.
    
Konfigurieren Sie anhand dieser Schritte die Benutzer 2- und Benutzer 3-Konten als Dynamics 365-Systemadministratoren.
  
1. Klicken Sie auf der Registerkarte **Office Admin Center** in Ihrem Browser im linken Navigationsbereich auf **Admin Center** und dann auf **Dynamics 365**.
    
    Möglicherweise müssen Sie warten, bis die Bereitstellung von Dynamics 365 abgeschlossen ist, damit Dynamics 365 im Menü angezeigt wird.
    
2. Klicken Sie auf der Registerkarte „Dynamics 365“ auf **Alle** und dann auf **Einrichtung abschließen**.
    
    Warten Sie, bis die Einrichtung abgeschlossen ist.
    
    Sobald die Einrichtung abgeschlossen ist, wird ein Vertriebsaktivitäts-Dashboard mit Beispieldaten angezeigt, die zum Testabonnement gehören. Nehmen Sie sich kurz Zeit, um sich das **Willkommensvideo** anzusehen. Schließen Sie das Videofenster, sobald das Video zu Ende ist.
    
3. Klicken Sie auf der Symbolleiste oben auf den Nach-unten-Pfeil neben **Vertrieb**. Klicken Sie auf **Einstellungen** und dann auf **Sicherheit**.
    
4. Klicken Sie auf der Seite **Sicherheit** auf **Benutzer**.
    
5. Klicken Sie in der Benutzerliste auf **Benutzer 2**.
    
6. Klicken Sie in der Symbolleiste auf **Rollen verwalten**.
    
7. Klicken Sie unter **Rollen verwalten** auf **Systemadministrator** und dann auf **OK**.
    
8. Klicken Sie auf der Symbolleisten oben auf **Sicherheit**.
    
9. Wiederholen Sie die Schritte 5 bis 8 für das Konto „Benutzer 3“.
    
10. Schließen Sie die Registerkarte **Benutzer: Benutzer 3**.
    
> [!NOTE]
> Ihrem globalen Office 365-Administratorkonto wurde automatisch die Rolle des Dynamics 365-Systemadministrators zugewiesen. 
  
Ihre Entwicklungs-/Testumgebung verfügt nun über Folgendes:
  
- Ein simuliertes Intranet, das in Azure-Infrastrukturdiensten ausgeführt wird.
    
- Office 365 E5 Enterprise-, EMS- und Dynamics 365-Testabonnements mit derselben Organisation und demselben Azure AD-Mandanten wie Ihre Liste von Benutzerkonten.
    
- Alle Ihre Benutzerkonten, aktiviert für die Verwendung von Office 365 E5 Enterprise und EMS.
    
- Die Konten des globalen Unternehmensadministrators und der Benutzer 2 und Benutzer 3 dürfen Dynamics 365 verwenden und sind Dynamics 365-Systemadministratoren.
    
Abbildung 3 zeigt die resultierende Konfiguration.
  
**Abbildung 3: Das simulierte Intranet in Azure mit Office 365, EMS und Dynamics 365**

![Phase 3 der One Microsoft Cloud-Entwicklungs-/Testumgebung mit Azure, Office 365, EMS und Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>Nächste Schritte

Sie können jetzt mit Ihrer One Microsoft Cloud-Entwicklungs-/Testumgebung experimentieren. Hier sind einige Ideen zum Ausprobieren mit Anleitung:
  
- [Konfigurieren von MAM-Richtlinien in EMS für Office 365-Anwendungen](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Demonstrieren von Exchange Online in einer Office 365-Integration mit Dynamics 365-Kontakten](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Erstellen eines simulierten standortübergreifenden Netzwerks in Azure-Infrastrukturdiensten zum Hosten serverbasierter Arbeitsauslastungen](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ressourcen zur Cloud-IT-Architektur von Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Hybridlösungen](hybrid-solutions.md)
  
[Sicherheitslösungen](security-solutions.md)





