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
description: 'Zusammenfassung: Konfigurieren Sie und veranschaulichen Sie der Klassifizierung von Daten und Beschriftung mit dem Azure Informationen Schutz (per) in Ihrer Office 365 Dev/Test-Umgebung.'
ms.openlocfilehash: a2db6817bea879caeb52ed9b11b40c6c317ea171
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Datenklassifizierung und -kennzeichnung in Office 365-Entwicklungs-/-Testumgebungen

 **Zusammenfassung:** Konfigurieren Sie und veranschaulichen Sie der Klassifizierung von Daten und Beschriftung mit dem Azure Informationen Schutz (per) in Ihrer Office 365 Dev/Test-Umgebung.
  
Der Client Azure Information Protection können Sie ein Dokument klassifizieren, bevor Sie ihn in einen Ordner SharePoint Online in Office 365 hochladen. Mit den Anweisungen in diesem Artikel installieren Sie den Client Azure Information Protection und veranschaulichen der Datenklassifikation. Weitere Informationen finden Sie unter [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Befolgen Sie die Anweisungen in [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>Phase 2: Hinzufügen des Azure Information Protection-Abonnements

In dieser Phase Ihrer Office 365-Umgebung Test-/Azure Information Protection hinzugefügt und für Ihre Benutzerkonten zu aktivieren. Wenn Sie [Office 365 und zur Abstimmung Test-/Umgebung](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)konfiguriert haben, überspringen Sie diese Phase. Das Testversion Enterprise Mobilität Suite-Abonnement umfasst Azure Information Protection-Lizenzen.
  
Melden Sie sich zunächst für ein Azure Information Protection-Testabonnement an.
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Anmelden für ein Azure Information Protection-Testabonnement

1. In Internet Explorer oder in Ihrem Browser wechseln Sie zu [http://portal.office.com](http://portal.office.com) , und melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein.
    
2. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel " **Admin** ".
    
3. Klicken Sie auf der Registerkarte Office 365 Admin im linken Navigationsbereich auf **Abrechnung > Dienste erwerben**.
    
4. Suchen Sie auf der Seite **Dienste erwerben** des **Azure Informationen Protection Premium P2** -Elements. Bewegen Sie die Maus darauf, und klicken Sie auf **Start kostenlose Testversion**.
    
5. Klicken Sie auf der Seite für die **Bestätigung Ihrer Bestellung** auf **Jetzt versuchen**.
    
6. Klicken Sie auf der Seite **Bestellbestätigung** auf **Weiter**.
    
Im nächsten Schritt können Sie die Azure Information Protection-Lizenz für alle Benutzerkonten aktivieren.
  
1. Klicken Sie auf die Registerkarte Office 365 Admin Center auf **Benutzer**.
    
2.  Wählen Sie in der Liste der Benutzerkonten die globale Administratorkonto ein, und klicken Sie dann auf **Bearbeiten** , für die **Lizenzen**.
    
3. Deaktivieren Sie die-Lizenz für **Azure Informationen Protection Premium P2** bis **auf**, klicken Sie auf **Speichern,** und klicken Sie dann zweimal auf **Schließen** .
    
4. Wiederholen Sie die Schritte 2 und 3 für Ihre anderen Konten (Benutzer 1 bis 5).
    
Ihre Office 365-Entwicklungs-/Testumgebung verfügt nun über:
  
- Office 365 E5 Enterprise and Azure Information Protection-Testabonnements.
    
- Alle Ihre Benutzerkonten sind aktiviert für die Verwendung von Office 365 E5 Enterprise und Azure Information Protection.
    
## <a name="phase-3-demonstrate-data-classification"></a>Phase 3: Veranschaulichen der Datenklassifizierung

In dieser Phase veranschaulichen Sie die Datenklassifizierung mit dem Azure Information Protection-Client und der standardmäßigen Azure Information Protection-Richtlinie.
  
Wenn Sie die Unternehmenssimulation in der Office 365- Entwicklungs-/-Testumgebung verwenden, müssen Sie zuerst Office 2016 auf CLIENT1 installieren.
  
1. Verwenden Sie den Browser, und wechseln Sie zu der [Azure-Portal](http://portal.azure.com).
    
2. Klicken Sie auf **Ressourcengruppen >** [Ihre Gruppe Ressourcenname] **> CLIENT1 > Connect**.
    
3. CLIENT1 starten Sie Internet Explorer, wechseln Sie zu der Office-Portal unter [http://portal.office.com](http://portal.office.com)und melden Sie sich mit den User5 Kontonamen und das Kennwort.
    
4. Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Office 2016 installieren**.
    
5. Führen Sie die heruntergeladene Datei, wenn Sie dazu aufgefordert werden, und klicken Sie auf **Ja,** Wenn die Benutzerkontensteuerung dazu aufgefordert werden. Warten Sie Office installieren. Nach Abschluss des Vorgangs **Schließen** klicken Sie zweimal auf.
    
Als Nächstes installieren Sie den Azure Information Protection-Client.
  
1. Wechseln Sie in Ihrem Browser oder Internet Explorer um die [Microsoft Azure Information Protection-Downloadseite](https://www.microsoft.com/download/details.aspx?id=53018).
    
  - Wenn Sie die einfache Version der Office 365-Entwicklungs-/Testumgebung verwenden, nutzen Sie den Browser auf dem lokalen Computer.
    
  - Wenn Sie die Unternehmenssimulation der Office 365-Entwicklungs-/-Testumgebung verwenden, führen Sie Internet Explorer von CLIENT1 aus.
    
2. Klicken Sie auf der Downloadseite **Microsoft Azure Information Protection** auf **Download**, klicken Sie auf **AzInfoProtection.exe**, und klicken Sie dann auf **Weiter**.
    
3. Wenn Sie dazu aufgefordert werden, führen Sie „AzInfoProtection.exe“ aus.
    
4. Klicken Sie im Feld Client **die Azure Information Protection installieren** auf **ich stimme zu**, und klicken Sie dann auf **Ja,** Wenn die Benutzerkontensteuerung dazu aufgefordert werden.
    
5. Klicken Sie in das Feld **wurde erfolgreich abgeschlossen** auf **Close.**
    
Als Nächstes veranschaulichen Sie die Klassifizierung von Dokumenten.
  
1. Klicken Sie auf das **Word** -Symbol in der Taskleiste.
    
2. Wenn Sie dazu aufgefordert werden, melden Sie sich mit den Kontonamen und dem Kennwort für Benutzer 5 an.
    
3. Wenn Sie gerade Office 2016 auf CLIENT1 im installiert die **sollte zunächst festgestellt ersten** Feld, klicken Sie auf **annehmen**.
    
4. Klicken Sie auf **leeres Dokument**. 
    
    Beachten Sie den Abschnitt " **Protection** " auf dem Menüband auf der Registerkarte **Start** und Dokument Klassifikationen in der Zeile.
    
5. Geben Sie in das leere Dokument etwas Text ein.
    
6. Klicken Sie auf **Datei > Speichern**, geben Sie den Namen **BeforeAIP**, und klicken Sie dann auf **OK**. 
    
7. Klicken Sie in der Zeile des Dokumentenklassen auf den Pfeil nach unten für **geheimen Schlüssel**, und klicken Sie dann auf **Alle Unternehmen**.
    
8. Klicken Sie auf **Datei > Speichern unter**, geben Sie den Namen **AfterAIP**, und klicken Sie dann auf **OK**.
    
9. Klicken Sie in der Taskleiste auf **Datei-Explorer** , und öffnen Sie den Ordner **Dokumente** .
    
    Beachten Sie die verschiedenen Dateigröße der Dokumente **BeforeAIP** und **AfterAIP** . Das Dokument AfterAIP ist größer, da sie die Klassifizierungsinformationen enthält.
    
Im nächsten Schritt erlauben Sie jedem, auf die Websitesammlung „Support“ zuzugreifen.
  
1. Klicken Sie auf der Registerkarte **Start von Microsoft Office** **SharePoint**.
    
2. Klicken Sie auf der Registerkarte **SharePoint** **Support**.
    
3. Klicken Sie in der oberen rechten Ecke klicken Sie auf das Symbol **Einstellungen** , und klicken Sie dann auf **freigegeben für**.
    
4. **Freigeben "Support Site Collection"**klicken Sie auf **Erweitert**.
    
5. Klicken Sie in der Liste der SharePoint-Gruppen **Unterstützung Websitesammlung Mitglieder**auf.
    
6. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
7. Geben Sie im **"Support Site Collection" Freigeben**, **jeder**, klicken Sie auf **alle Benutzer mit Ausnahme von externen Benutzern**und klicken Sie dann auf **freigeben.**
    
8. Schließen Sie die Registerkarte **Personen und Gruppen** .
    
Im nächsten Schritt melden Sie sich mit dem Benutzerkonto von Benutzer 5 an und laden das durch AIP geschützte Dokument in den Dokumentordner der Websitesammlung „Support“ hoch.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** in der oberen rechten Ecke klicken Sie auf das Symbol "Benutzer", und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf die ** Office 365 anmelden ** Seite, klicken Sie auf den Kontonamen User5 und anmelden.
    
4. Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **SharePoint > Websitesammlung unterstützen**.
    
5. Klicken Sie auf **Dokumente**, klicken Sie auf **Hochladen**, klicken Sie auf das Dokument **AfterAIP** , und klicken Sie dann auf **Öffnen**.
    
    Das Dokument „NachAIP.docx“ sollte im Ordner „Dokumente“ in der Websitesammlung „Support“ angezeigt werden.
    
## <a name="see-also"></a>Weitere Artikel

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 und zur Abstimmung Test-/Umgebung](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


