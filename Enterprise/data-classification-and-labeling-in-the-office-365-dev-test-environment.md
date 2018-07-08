---
title: Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Zusammenfassung: Informationen zum Konfigurieren und Demonstrieren der Datenklassifizierung und -kennzeichnung mit dem Azure Information Protection-Client (AIP) in Office 365-Entwicklungs-/-Testumgebungen.'
ms.openlocfilehash: f9674f5e2bac804f5bd23b5f67e733580c50450f
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188093"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen

 **Zusammenfassung:** Informationen zum Konfigurieren und Demonstrieren der Datenklassifizierung und -kennzeichnung mit dem Azure Information Protection-Client (AIP) in Office 365-Entwicklungs-/-Testumgebungen.
  
Der Client Azure Information Protection können Sie ein Dokument klassifizieren, bevor Sie ihn in einen Ordner SharePoint Online in Office 365 hochladen. Mit den Anweisungen in diesem Artikel installieren Sie den Client Azure Information Protection und veranschaulichen der Datenklassifikation. Weitere Informationen finden Sie unter [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Folgen Sie den Anweisungen unter [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Phase 2: Hinzufügen des Azure Information Protection-Abonnements

In dieser Phase fügen Sie Azure Information Protection zu Ihrer Office 365-Entwicklungs-/Testumgebung und aktivieren Sie ihn für Ihre Benutzerkonten. Wenn Sie die [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx) konfiguriert haben, überspringen Sie diese Phase. Das Enterprise Mobility Suit-Testabonnement umfasst Azure Information Protection-Lizenzen.
  
Melden Sie sich zunächst für ein Azure Information Protection-Testabonnement an.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Anmelden für ein Azure Information Protection-Testabonnement

1. Wechseln Sie in Internet Explorer oder Ihren Browser zu [http://portal.office.com](http://portal.office.com) und melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein.
    
2. Klicken Sie auf die Registerkarte **Microsoft Office Home** auf **Admin**.
    
3. Klicken Sie in der Registerkarte „Office 365-Administrator“ im linken Navigationsbereich auf **Abrechnung > Dienste kaufen**.
    
4. Suchen Sie auf der Seite **Dienste kaufen** den Artikel **Azure Information Protection Premium P2**. Bewegen Sie den Mauszeiger über den Artikelnamen, und klicken Sie auf **Kostenlosen Test starten**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
Im nächsten Schritt können Sie die Azure Information Protection-Lizenz für alle Benutzerkonten aktivieren.
  
1. 	Klicken Sie auf der Registerkarte Office 365 Admin Center auf **Benutzer**.
    
2.   Wählen Sie in der Liste der Benutzerkonten Ihr globales Administratorkonto, und klicken Sie dann auf **earbeiten** für **Produktlizenzen**.
    
3. 	Aktivieren die Produktlizenz für **Azure Information Protection Premium P2** zu **in**, klicken Sie auf **peichern,**, und klicken Sie dann zweimal auf **chließen**.
    
4. Wiederholen Sie die Schritte 2 und 3 für Ihre anderen Konten (Benutzer 1 bis 5).
    
Ihre Office 365-Entwicklungs-/Testumgebung verfügt nun über:
  
- Office 365 E5 Enterprise and Azure Information Protection-Testabonnements.
    
- Alle Ihre Benutzerkonten sind aktiviert für die Verwendung von Office 365 E5 Enterprise und Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Phase 3: Veranschaulichen der Datenklassifizierung

In dieser Phase veranschaulichen Sie die Datenklassifizierung mit dem Azure Information Protection-Client und der standardmäßigen Azure Information Protection-Richtlinie.
  
Wenn Sie die Unternehmenssimulation in der Office 365- Entwicklungs-/-Testumgebung verwenden, müssen Sie zuerst Office 2016 auf CLIENT1 installieren.
  
1. Verwenden Sie den Browser, und wechseln Sie zu der [Azure-Portal](http://portal.azure.com).
    
2. 	Klicken Sie auf **Ressourcengruppen >** [Ihr Ressourcengruppenname] **> CLIENT1 > Verbinden**.
    
3. Führen Sie auf CLIENT1 Internet Explorer, fahren Sie mit der Office-Portal unter [http://portal.office.com](http://portal.office.com), und melden Sie sich mit den User5 Kontonamen und das Kennwort.
    
4. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Office 2016 installieren**.
    
5. 	Führen Sie den Download aus, wenn Sie dazu aufgefordert werden, und klicken Sie auf **Ja**, wenn Sie von der Benutzerkontensteuerung dazu aufgefordert werden. Warten Sie, bis Office installiert ist. Klicken Sie nach Abschluss des Vorgangs zweimal auf **Schließen**.
    
Als Nächstes installieren Sie den Azure Information Protection-Client.
  
1. Wechseln Sie in Ihrem Browser oder Internet Explorer um die [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Wenn Sie die einfache Version der Office 365-Entwicklungs-/Testumgebung verwenden, nutzen Sie den Browser auf dem lokalen Computer.
    
  - Wenn Sie die Unternehmenssimulation der Office 365-Entwicklungs-/-Testumgebung verwenden, führen Sie Internet Explorer von CLIENT1 aus.
    
2. Klicken Sie auf der Downloadseite von **Microsoft Azure Information Protection** auf **Herunterladen**, klicken Sie auf **AzInfoProtection.exe**, und klicken Sie dann auf **Weiter**.
    
3. Wenn Sie dazu aufgefordert werden, führen Sie „AzInfoProtection.exe“ aus.
    
4. Klicken Sie im Client-Dialogfeld **Azure Information Protection installieren** auf **Ich stimme zu**, und klicken Sie auf **Ja**, wenn Sie von der Benutzerkontensteuerung dazu aufgefordert werden.
    
5. Klicken Sie im Feld **Erfolgreich abgeschlossen** auf **Schließen**.
    
Als Nächstes veranschaulichen Sie die Klassifizierung von Dokumenten.
  
1. Klicken Sie in der Taskleiste auf das **Word**-Symbol.
    
2. Wenn Sie dazu aufgefordert werden, melden Sie sich mit den Kontonamen und dem Kennwort für Benutzer 5 an.
    
3. Wenn Sie Office 2016 gerade auf CLIENT1 installiert haben, klicken Sie im Feld **Das Wichtigste zuerst** auf **Akzeptieren**.
    
4. Klicken Sie auf **Leeres Dokument**.  
    
    Beachten Sie den Abschnitt **Schutz** auf dem Menüband auf der Registerkarte **Start** sowie die Zeile der Dokumentklassifizierungen.
    
5. Geben Sie in das leere Dokument etwas Text ein.
    
6. Klicken Sie auf **Datei > Speichern**, geben Sie den Namen **VorAIP** ein, und klicken Sie auf **OK**.  
    
7. Klicken Sie in der Zeile der Dokumentklassen auf den Abwärtspfeil für **Geheim**, und klicken Sie auf **Gesamtes Unternehmen**.
    
8. Klicken Sie auf **Datei > Speichern unter**, geben Sie den Namen **NachAIP** ein, und klicken Sie dann auf **OK**.
    
9. Klicken Sie in der Taskleiste auf **Datei-Explorer**, und öffnen Sie dann den **Dokumente**-Ordner.
    
    Beachten Sie die verschiedenen Dateigrößen der Dokumente **VorAIP** und **NachAIP**. Das Dokument „NachAIP“ ist größer, da es die Klassifizierungsinformationen enthält.
    
Im nächsten Schritt erlauben Sie jedem, auf die Websitesammlung „Support“ zuzugreifen.
  
1. 	Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **SharePoint**.
    
2. Klicken Sie auf der Registerkarte **SharePoint** auf die **Websitesammlung „Support“**.
    
3. Klicken Sie in der oberen rechten Ecke auf das **Einstellungen**-Symbol, und klicken Sie dann auf **Freigegeben für**.
    
4. **Freigeben "Support Site Collection"** klicken Sie auf **Erweitert**.
    
5. Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder der Websitesammlung „Support“**.
    
6. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
7. Geben Sie im **"Support Site Collection" Freigeben**, **jeder**, klicken Sie auf **alle Benutzer mit Ausnahme von externen Benutzern**und klicken Sie dann auf **freigeben.**
    
8. Schließen Sie die Registerkarte **Benutzer und Gruppen**.
    
Im nächsten Schritt melden Sie sich mit dem Benutzerkonto von Benutzer 5 an und laden das durch AIP geschützte Dokument in den Dokumentordner der Websitesammlung „Support“ hoch.
  
1. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen User5, und melden Sie sich bei.
    
4. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **SharePoint > Websitesammlung „Support“**.
    
5. Klicken Sie auf **Dokumente**, klicken Sie auf **Hochladen**, klicken Sie auf das Dokument **NachAIP**. Klicken Sie anschließend auf **Öffnen**.
    
    Das Dokument „NachAIP.docx“ sollte im Ordner „Dokumente“ in der Websitesammlung „Support“ angezeigt werden.
    
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365- und EMS-Entwicklungs-/Testumgebung](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


