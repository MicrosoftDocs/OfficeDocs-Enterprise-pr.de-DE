---
title: Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Zusammenfassung: Konfigurieren Sie und veranschaulichen Sie, wie Office 365 Information Rights Management sensiblen Dateien schützt, auch wenn sie in der falschen SharePoint Online-Websitesammlung bereitgestellt werden."
ms.openlocfilehash: 22f12143dc7cb50c19a135f51c08cb4b9bf02f38
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen

 **Zusammenfassung:** Konfigurieren Sie und veranschaulichen Sie, wie Office 365 Information Rights Management sensiblen Dateien schützt, auch wenn sie in der falschen SharePoint Online-Websitesammlung bereitgestellt werden.
  
Information Rights Management (IRM) in Office 365 umfasst eine Reihe von Funktionen zum Schutz von Dokumenten, die aus SharePoint Online-Bibliotheken und -Listen heruntergeladen werden. Heruntergeladene Dateien sind verschlüsselt und verfügen über die Berechtigungen zum Öffnen, Kopieren, Speichern und Drucken, welche der SharePoint Online-Bibliothek entsprechen, in der sie gespeichert sind.
  
Mithilfe der Anleitungen in diesem Artikel können Sie IRM in Office 365 für Dateien aktivieren und testen, die in Ihrem Office 365-Testabonnement möglicherweise vertrauliche Informationen enthalten.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Wenn Sie vertrauliche Dateischutz auf einfache Weise mit den Mindestanforderungen testen möchten, befolgen Sie die Anweisungen in Phasen 2 und 3 von [Office 365 Dev/Test Environment](office-365-dev-test-environment.md).
  
Wenn Sie vertrauliche Dateischutz in einer simulierten Enterprise testen möchten, befolgen Sie die Anweisungen in [DirSync für Ihre Office 365 Dev/Test-Umgebung](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Für das Testen des Schutzes vertraulicher Dateien ist keine simulierte Unternehmensentwicklungs-/-testumgebung erforderlich, die ein simuliertes Intranet, das mit dem Internet verbunden ist, und die Verzeichnissynchronisierung für eine Windows Server Active Directory-Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie den Schutz vertraulicher Dateien testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Phase 2: Demonstriert, wie Dokumente von Websites, die durch Berechtigungen geschützt sind, anderweitig (und möglicherweise missbräuchlich) verwendet werden können.

In dieser Phase demonstrieren Sie, wie jemand ein Dokument von einer Website, die durch Berechtigungen geschützt ist, herunterladen und anschließend auf eine Website hochladen kann, die nicht auf diese Weise geschützt und entsprechend allgemein zugänglich ist.
  
Sie fügen zuerst drei neue Benutzerkonten für Führungskräfte hinzu und weisen diesen Office 365 E5-Lizenzen zu.
  
Verwenden Sie die Anweisungen in [Verbindung mit Office 365 PowerShell herstellen](https://technet.microsoft.com/library/dn975125.aspx) , installieren Sie die PowerShell-Module (falls erforderlich) und eine Verbindung herstellen, um das neue Office 365-Abonnement aus:
  
- Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).
    
- Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).
    
Geben Sie im Dialogfeld **Windows PowerShell anmelden** den Namen der Office 365 globaler Administrator (Beispiel: jdoe@contosotoycompany.onmicrosoft.com) und das Kennwort für Ihr trial Office 365-Abonnement.
  
Geben Sie den Namen der Organisation (zum Beispiel „contosotoycompany“) und den zweistelligen Ländercode für Ihren Standort ein. Führen Sie dann über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto CEO, und tragen sie Sie an einem sicheren Ort.
  
Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto Leiter der Finanzabteilung, und tragen sie Sie an einem sicheren Ort.
  
Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Beachten Sie aus der Anzeige des Befehls **New-MsolUser** das generierte Kennwort für das Konto COO, und tragen sie Sie an einem sicheren Ort.
  
Im nächsten Schritt erstellen Sie eine private Führungskräftegruppe und fügen dieser die neuen Führungskräftekonten hinzu.
  
1. In Ihrem Browser wechseln Sie zu der Office-Portal unter [http://portal.office.com](http://portal.office.com) , und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.
    
  - Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung in Internet Explorer bzw. in dem von Ihnen bevorzugten Browser, und melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das Azure-Portal, um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.
    
2. Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Admin > Gruppen > Gruppen**, und klicken Sie dann auf **Gruppe hinzufügen**.
    
3. Wählen Sie in **einer Gruppe hinzufügen** **Office 365-Gruppe** für die Gruppe, geben **Führungskräfte** in **Name** und **Gruppen-Id**, wählen Sie **Private** für **private**, und klicken Sie dann auf **Besitzer auswählen**.
    
4. Klicken Sie in der Liste auf den Namen Ihres globalen Administratorkontos.
    
5. Klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Schließen**.
    
6. Klicken Sie in der Gruppenliste auf **Führungskräfte**.
    
7. Klicken Sie auf **Bearbeiten der Mitglieder**.
    
8. Klicken Sie auf **Mitglieder hinzufügen**. Wählen Sie die folgenden Benutzerkonten in der Liste Member:
    
  - Chief Executive Officer
    
  - Chief Financial Officer
    
  - Chief Operations Officer
    
9. Klicken Sie auf **Speichern**, und klicken Sie dann auf **Schließen**.
    
10. Schließen Sie die Registerkarte **Office-Verwaltungskonsole** .
    
Im nächsten Schritt erstellen Sie eine Websitesammlung für Führungskräfte und erlauben nur den Mitgliedern der Führungskräftegruppe den Zugriff darauf.
  
1. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf die Kachel " **Admin** ".
    
2. Klicken Sie auf die Registerkarte **Office Admin Center** auf **Zentriert Admin > SharePoint**.
    
3. Klicken Sie auf der Registerkarte **SharePoint Administrationscenter** auf **Neu > Private Websitesammlung**.
    
4. Im Bereich Auflistung neue Website geben **Führungskräfte** **Titel**, Führungskräfte in das Feld URL Geben Sie den Namen des globalen Administratorkontos in **Administrator**aus, und klicken Sie dann auf **OK**.
    
5. Warten Sie, bis die neue Websitesammlung erstellt wurde. Nach Abschluss des Vorgangs, kopieren Sie die URL der neuen Websitesammlung Führungskräfte, und fügen Sie ihn in eine neue Registerkarte Ihres Browsers.
    
6. Klicken Sie in der oberen rechten Ecke der Websitesammlung **Führungskräfte** auf das einstellungssymbol, und klicken Sie dann auf **freigegeben für**.
    
7. **Freigeben "Executives"**klicken Sie auf **Erweitert**.
    
8. Klicken Sie in der Liste der SharePoint-Gruppen die **Führungskräfte Elemente**auf.
    
9. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
10. Geben Sie im **freigeben "Executives"** **Führungskräfte**, klicken Sie auf die Gruppe **Führungskräfte** und klicken Sie dann auf **Freigeben**.
    
11. Schließen Sie die Registerkarte **Personen und Gruppen** .
    
Im nächsten Schritt erlauben Sie allen Gruppenmitgliedern, auf die Websitesammlung „Vertrieb“ zuzugreifen.
  
1. Kopieren Sie über die Registerkarte **SharePoint Administrationscenter** die URL der Websitesammlung Sales, und fügen Sie ihn in eine neue Registerkarte Ihres Browsers.
    
2. Klicken Sie in der oberen rechten Ecke klicken Sie auf das einstellungssymbol, und klicken Sie dann auf **freigegeben für**.
    
3. **Freigeben "Websitesammlung des Vertriebs"**klicken Sie auf **Erweitert**.
    
4. Klicken Sie in der Liste der SharePoint-Gruppen auf **Sales Websitesammlung Mitglieder**.
    
5. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
6. Geben Sie im **freigeben 'Websitesammlung des Vertriebs'** **jeder** **Person mit Ausnahme von externen Benutzern**auf, und klicken Sie dann auf **Freigeben**.
    
7. Schließen Sie die Registerkarten **Sales-Websitesammlung** und **SharePoint** .
    
Als Nächstes melden Sie sich mit einem Führungskräftekonto an und erstellen ein Dokument in der Websitesammlung „Führungskräfte“.
  
1. Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf der Seite **Office 365 anmelden** auf **ein anderes Konto verwenden**.
    
4. Geben Sie den Kontonamen **CEO** und das zugehörige Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
5. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung Führungskräfte ( **https://**\<Name der Organisation >**.sharepoint.com/sites/executives**).
    
6. Klicken Sie auf **Dokumente**, klicken Sie auf **neu,** und klicken Sie dann auf **Word-Dokument**.
    
7. Klicken Sie in der Titelleiste auf, und geben Sie **SensitiveData BeforeIRM**.
    
8. Klicken Sie in der Hauptteil des Dokuments und geben Sie **Minuten aus der neuesten Pinnwand Besprechung**, und klicken Sie dann auf **"Executives"**.
    
     **SensitiveData BeforeIRM.docx** im Ordner " **Dokumente** " sollte angezeigt werden.
    
Im nächsten Schritt laden Sie eine lokale Kopie des Dokuments „VertraulicheDaten-VorIRM.docx“ herunter und veröffentlichen diese versehentlich in der Websitesammlung „Vertrieb“.
  
1. Erstellen Sie einen neuen Ordner auf Ihrem lokalen Computer (z. B. C:\\TLGs\\SensitiveDataTestFiles).
    
2. Wählen Sie auf der Registerkarte **Dokumente** des Browsers das Dokument **SensitiveData BeforeIRM.docx** , klicken Sie auf die Auslassungspunkte, und klicken Sie auf **Download**.
    
3. Speichern Sie das Dokument **SensitiveData BeforeIRM.docx** in den in Schritt 1 erstellten Ordner.
    
4. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs ( **https://**\<Name der Organisation >**.sharepoint.com/sites/sales**).
    
5. Klicken Sie auf den Ordner **Dokumente** der **Websitesammlung Sales**.
    
6. Klicken Sie auf **Hochladen**, und geben Sie in dem in Schritt 1 erstellten Ordner **SensitiveData BeforeIRM.docx** Dokument, und klicken Sie dann auf **OK**.
    
7. Stellen Sie sicher, dass das Dokument **SensitiveData BeforeIRM.docx** im Ordner " **Dokumente** " ist.
    
8. Schließen Sie die Registerkarten **Sales** und **SharePoint** .
    
Als Nächstes melden Sie sich als Benutzer5 an und versuchen, das Dokument „VertraulicheDaten-VorIRM.docx“ in der Websitesammlung „Vertrieb“ zu öffnen.
  
1. Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf der Seite **Office 365 anmelden** auf **ein anderes Konto verwenden**.
    
4. Geben Sie den User5-Kontonamen und das zugehörige Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
5. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.
    
6. Klicken Sie auf das Dokument **SensitiveData BeforeIRM.docx** , im Ordner **Dokumente** von der **Websitesammlung Sales**.
    
    Sie sollten den Inhalt sehen können.
    
7. Schließen Sie die Registerkarten **Dokumente** und **Sales Websitesammlung festlegen** .
    
Indem der CEO das Dokument „VertraulicheDaten-VorIRM.docx“ versehentlich in der Websitesammlung „Vertrieb“ veröffentlicht hat, hat er die Berechtigungssicherheit der Websitesammlung „Führungskräfte“ umgangen.
  
Um Office 365 für die Phasen 3 und 4 vorzubereiten, aktivieren Sie IRM für SharePoint Online.
  
1. Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Microsoft Office Home** , und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Namen des globalen Administratorkontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
4. Klicken Sie auf der Registerkarte **Start von Microsoft Office** auf **Admin > zentriert Admin > SharePoint**.
    
5. Klicken Sie auf der Registerkarte **SharePoint Administrationscenter** auf **Einstellungen**.
    
6. Wählen Sie auf der Seite **Einstellungen** im Abschnitt **(Information Rights Management, IRM)** aus, **den in Ihrer Konfiguration angegebenen IRM-Dienst**, und wählen Sie dann die **IRM-Einstellungen aktualisieren**.
    
7. Schließen Sie die Registerkarte **SharePoint Administrationscenter** .
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Phase 3: Verwenden von SharePoint Information Rights Management mit einer privaten Office 365-Gruppe

In dieser Phase verwenden Sie SharePoint Information Rights Management mit einer privaten Office 365-Gruppe, um den Zugriff auf ein Dokument mit vertraulichen Informationen auch dann zu schützen, wenn es auf einer Website mit offenen Berechtigungen veröffentlicht wird.
  
Als Erstes aktivieren und konfigurieren Sie IRM für die Dokumentbibliothek der Websitesammlung „Führungskräfte“.  
  
1. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung "Executives".
    
2. Klicken Sie auf **Dokumente**.
    
3. Klicken Sie in der rechten oberen Ecke klicken Sie auf das einstellungssymbol, und klicken Sie dann auf **bibliothekseinstellungen**.
    
4. Klicken Sie auf der Seite **Einstellungen** unter **Berechtigungen und Verwaltung**auf **Information Rights Management**.
    
5. Auf der Seite **Information Rights Management Settings** :
    
  - Wählen Sie die **Berechtigung für Dokumente in dieser Bibliothek beim Herunterladen einschränken**.
    
  - Geben Sie **einen Titel der Berechtigungsrichtlinie erstellen** **Führungskräfte**.
    
  - **Eine Beschreibung der Berechtigungsrichtlinie hinzufügen**Geben Sie **IRM für Führungskräfte**.
    
6. Klicken Sie auf **Optionen anzeigen**.
    
7. Wählen Sie unter **Legen Sie zusätzliche Einstellungen der IRM-Bibliothek** **Dokumente hochladen, die IRM nicht unterstützen, Benutzer können keine**ein.
    
8. Wählen Sie unter **Configure Dokument Zugriffsrechte** **Zulassen Zuschauer zu drucken** und **Zulassen Viewer auf eine Kopie des heruntergeladenen Dokuments schreiben**.
    
9. Wählen Sie unter **Gruppe Schutz und die Anmeldeinformationen Intervall festgelegt** **die Gruppe Protection zulassen** , und geben Sie für die **Gruppe**, **Führungskräfte**.
    
10. Klicken Sie auf **OK**.
    
Im nächsten Schritt fungieren Sie als CEO und laden ein neues Dokument in den Dokumentordner „Führungskräfte“ hoch. Dann laden Sie das Dokument herunter und laden es versehentlich in den Dokumentordner „Vertrieb“ hoch.
  
1. Öffnen Sie den lokalen Ordner, in dem Sie das Dokument **SensitiveData BeforeIRM.docx** gespeichert.
    
2. Mit der rechten Maustaste **SensitiveData BeforeIRM.docx**, und klicken Sie dann auf **Kopieren**.
    
3. Mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Einfügen**.
    
4. Benennen Sie die neue Datei **SensitiveData-BeforeIRM - Copy.docx** in **SensitiveData AfterIRM.docx**.
    
5. Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Startseite von Microsoft Office** in Ihrem Browser, und klicken Sie dann auf **Abmelden**.
    
6. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
7. Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen CEO, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
8. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung "Executives".
    
9. Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **SensitiveData AfterIRM.docx** in Ihrer lokalen Ordner, und klicken Sie dann auf **Öffnen**.
    
10. Wählen Sie das neue Dokument **SensitiveData AfterIRM.docx** der Seite **Dokumente** aus, klicken Sie auf die Auslassungspunkte (...) in der Menüleiste, und klicken Sie dann auf **herunterladen**.
    
11. Wenn Sie aufgefordert werden, speichern Sie das **SensitiveData AfterIRM.docx** -Dokument in Ihrer lokalen Ordner, und überschreiben Sie die ursprüngliche Version.
    
12. Schließen Sie die Registerkarte für die Seite **Dokumente** .
    
13. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.
    
14. Klicken Sie auf **Dokumente**.
    
15. Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **SensitiveData AfterIRM.docx** in Ihrer lokalen Ordner, und klicken Sie dann auf **Öffnen**.
    
16. Schließen Sie die Registerkarten **Sales-Websitesammlung** und **SharePoint** .
    
Im nächsten Schritt versuchen fungiert als normaler Benutzer, das **SensitiveData AfterIRM.docx** Dokument in den Ordner Sales Dokument zuzugreifen.
  
1. Klicken Sie auf das Symbol für Benutzer in der rechten oberen Ecke auf der Registerkarte **Startseite von Microsoft Office** in Ihrem Browser, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zur [http://portal.office.com](http://portal.office.com).
    
3. Klicken Sie auf der Seite **Office 365 anmelden** klicken Sie auf den Kontonamen User5, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
4. Geben Sie auf einer neuen Registerkarte des Browsers die URL der Websitesammlung des Vertriebs.
    
5. Klicken Sie auf **Dokumente**.
    
6. Öffnen Sie auf der Seite **Dokumente** **SensitiveData AfterIRM.docx** Dokument.
    
    Es sollte eine Meldung angezeigt werden, die besagt, dass Word Online dieses Dokument nicht öffnen kann, weil es durch Information Rights Management (IRM) geschützt ist.  
    
7. Klicken Sie auf **in Word bearbeiten**. Sie werden aufgefordert, wenn Sie die Datei öffnen möchten. Klicken Sie auf **Ja**.
    
8. Sie werden aufgefordert,-Anmeldung Geben Sie den Kontonamen des User5-Kontos ein, und klicken Sie dann auf **Weiter**.
    
9. Sie werden aufgefordert, das Kennwort angeben. Geben Sie das Kennwort für das Konto User5, und klicken Sie dann auf **Anmelden**. 
    
    Es sollte eine Nachricht angezeigt werden, die besagt, dass Sie keine Anmeldedaten haben, die Sie zum Öffnen dieses Dokuments berechtigen.
    
10. Klicken Sie auf **Nein**.
    
Eine andere Möglichkeit, finden in der IRM-Schutz ist betrachten Sie die Dateien im lokalen Ordner. Die **SensitiveData AfterIRM.docx** sollte wesentlich größer als die **SensitiveData-BeforeIRM.docx** -Datei. Die Datei **SensitiveData AfterIRM.docx** wird verschlüsselt, und die IRM-Schutz Informationen hinzugefügt.
  
## <a name="see-also"></a>Weitere Artikel

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)


