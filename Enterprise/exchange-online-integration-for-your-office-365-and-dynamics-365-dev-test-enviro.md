---
title: Exchange Online-Integration für Ihre Office 365 und Dynamics 365-Entwicklungs-/Testumgebung
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
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 'Zusammenfassung: Verwenden Sie diese Testumgebungsanleitung, um die Dynamics 365-Integration für Exchange Online für Ihr Office 365-Testabonnement zu aktivieren.'
ms.openlocfilehash: be79f58f448799bba9c4a9ee51350f198d721e0d
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574019"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Exchange Online-Integration für Ihre Office 365 und Dynamics 365-Entwicklungs-/Testumgebung

 **Zusammenfassung:** Verwenden Sie diese Testumgebungsanleitung, um die Dynamics 365-Integration für Exchange Online für Ihr Office 365-Testabonnement zu aktivieren.
  
Ein nützlicher Vorteil von Microsoft Dynamics 365 besteht darin, dass die gesamte Kundenkommunikation an einem zentralen Ort gespeichert wird, damit jeder Benutzer mit den entsprechenden Berechtigungen auf alle relevanten Kundendatensätze zugreifen kann. Sie können beispielsweise alle E-Mail-Nachrichten anzeigen, die mit einem bestimmten Kontakt, einem Konto, einer Verkaufschance oder einem Falls verknüpft sind.
  
Um E-Mail-Nachrichten und andere Messagingdatensätze in Dynamics 365 zu speichern, müssen Sie das E-Mail-System mit Dynamics 365 synchronisieren. Die serverseitige Synchronisierung ist die bevorzugte Methode für die E-Mail-Synchronisierung.
  
Verwenden Sie diese Testumgebungsanleitung, um Exchange Online und den Outlook Online-Client für Dynamics 365 zu konfigurieren und zu demonstrieren, wie sie die in Dynamics 356 gespeicherten Informationen nutzen können. 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>Phase 1: Erstellen der Office 365- und Dynamics 365-Entwicklungs-/Testumgebung

Folgen Sie den Anweisungen in der Testumgebungsanleitung [Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md) zum Erstellen einer einfachen oder simulierten Unternehmensversion einer Office 365- und Dynamics 365-Entwicklungs-/Testumgebung.
  
> [!NOTE]
> Für die Konfiguration in diesem Artikel ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur (AD) umfasst. Dies wird hier als Option bereitgestellt, damit Sie mit Office 365 und Dynamics 365 in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>Phase 2: Konfigurieren und Demonstrieren der Exchange Online-Integration in Dynamics 365

Gehen Sie wie folgt vor, um das Postfach des globalen Administrators für die Integration von Dynamics 365 und Exchange Online zu konfigurieren:
  
1. Navigieren Sie in einer privaten Sitzung Ihres Browsers zu und [http://admin.microsoft.com](http://admin.microsoft.com) melden Sie sich mit ihrem globalen Office 365-Administratorkonto an.
    
2. Klicken Sie auf der **Microsoft Office-Homepage** auf die Kachel **E-Mail**.
    
3. Klicken Sie auf der Registerkarte neue **e-Mail** in Ihrem Browser auf **neu** , und beachten Sie, dass die untere Ecke des Bereichs unterhalb des Felds zum Eingeben einer Nachricht ein Symbol für meine Vorlagen aufweist.
    
     ![Leere neue E-Mail-Nachricht ohne Integration mit Dynamics 365](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. Klicken Sie auf **verwerfen**, und lassen Sie die Registerkarte **E-Mail** geöffnet.
    
5. Klicken Sie auf die Registerkarte **Microsoft Office Home** in Ihrem Browser, und klicken Sie dann auf die Kachel **Admin**.
    
6. Klicken Sie im linken Navigationsbereich der Registerkarte **Office Admin Center** auf **Admin Center > Dynamics 365**.
    
7. Klicken Sie auf der neuen Registerkarte **Dynamics 365** in Ihrem Browser in der Liste mit den Dynamics 365-Instanzen auf **Öffnen**.
    
8. Klicken Sie auf der neuen Registerkarte **Administration** in Ihrem Browser auf der Navigationsleiste auf den Abwärtspfeil neben **Einstellungen**, und klicken Sie dann auf **E-Mail-Konfiguration** unter **System**.
    
9.  Klicken Sie auf der Seite **E-Mail-Konfiguration** auf **E-Mail-Konfigurationseinstellungen**.
    
10. Ändern Sie auf der Registerkarte **E-Mail** im Dialogfeld **Systemeinstellungen** die Option **Termine, Kontakte und Aufgaben** in **Serverseitige Synchronisierung**, und klicken Sie dann auf **OK**.
    
11. Klicken Sie auf der Seite **E-Mail-Konfiguration** auf **Postfächer**.
    
12. Wählen Sie den Namen des globalen Administrator für Office 365 in der linken Spalte aus, klicken Sie in der Symbolleiste auf **Standard-E-Mail-Einstellungen anwenden**, und klicken Sie dann auf **OK**.
    
13. Klicken Sie in der Symbolleiste auf **E-Mail genehmigen**, und klicken Sie dann auf **OK**.
    
14. Wählen Sie den Namen des globalen Administrator für Office 365 in der linken Spalte aus, klicken Sie in der Symbolleiste auf **Postfächer testen&amp; und aktivieren**, und klicken Sie dann auf **OK**.
    
15. Klicken Sie auf die geöffnete Registerkarte **E-Mail**, und überprüfen Sie, ob der globale Administrator eine Testnachricht erhalten hat.
    
16. Wechseln Sie im Browser zurück zur Registerkarte **Postfächer > Meine aktiven Postfächer**, und aktualisieren Sie die Seite. Die Spalten **Status eingehender E-Mails** und **Status ausgehender E-Mails** müssen für den Namen des globalen Administrators auf **Erfolgt** festgelegt sein. Beachten Sie, dass es bis zu 15 Minuten dauern kann, bis beide Tests durchgeführt sind.
    
Gehen Sie wie folgt vor, um die Dynamics 365-App für Outlook zu installieren und die Funktionen von Dynamics 365 im Postfach des globalen Administrators zu demonstrieren:
  
1. Klicken Sie in Ihrem Browser auf der Registerkarte **Postfächer > Meine aktiven Postfächer** auf den Abwärtspfeil neben **Einstellungen**, und klicken Sie dann auf **Dynamics 365-App für Outlook** unter **System**.
    
2. Klicken Sie auf der Seite **Erste Schritte mit der Microsoft Dynamics 365-App für Outlook** auf den Namen des globalen Administrators, und klicken Sie dann auf **App zu Outlook hinzufügen**. Die Spalte **Status** ändert sich in **Ausstehend**.
    
3. Aktualisieren Sie die Seite, bis der Status sich in **Zu Outlook hinzugefügt** geändert hat. Beachten Sie, dass es bis zu 15 Minuten dauern kann, bis diese Konfiguration durchgeführt ist.
    
4. Klicken Sie im Browser auf die Registerkarte **E-Mail**, und schließen Sie den Browser dann.
    
5. Klicken Sie auf die Registerkarte **Microsoft Office Home** in Ihrem Browser, und klicken Sie dann auf die Kachel **E-Mail**.
    
6. Klicken Sie auf der neuen Registerkarte **E-Mail** im Browser auf **Neu**. Beachten Sie, dass die untere Ecke des Bereichs unterhalb des Felds zum Eingeben einer Nachricht jetzt ein Symbol für Dynamics 365 hat.
    
     ![Leere neue E-Mail-Nachricht bei Integration mit Dynamics 365 (neues Symbol sichtbar)](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. Klicken Sie auf das Symbol für Dynamics 365. Es sollte ein **Dynamics 365**-Fenster angezeigt werden, in dem Sie diese E-Mail verfolgen oder auf Vorlagen, Vertriebsdokumentation oder Artikel zugreifen können.
    
8. Geben Sie im Feld **An** der E-Mail-Nachricht **alex.y.wu@outlook.com** ein, und klicken Sie dann auf **Wiederholen** im Fenster **Dynamics 365**. Es sollte der Abschnitt **Empfänger** im Fenster **Dynamics 365** mit Informationen über Alex Wu angezeigt werden, der ein Kontakt in der Vertriebsanwendung ist, die in den Beispieldaten für das Testabonnement enthalten ist.
    
     ![Dynamics 365-Informationsbereich für einen in Dynamics 365 gespeicherten Vertriebskontakt](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. Klicken Sie auf **Verwerfen**.

> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
    
## <a name="see-also"></a>Siehe auch

[Office 365- und Dynamics 365-Entwicklungs-/Testumgebung](office-365-and-dynamics-365-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[DirSync für die Office 365-Entwicklungs-/Testumgebung](dirsync-for-your-office-365-dev-test-environment.md)

[Abonnement-Verwaltung für Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Verwalten von Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


