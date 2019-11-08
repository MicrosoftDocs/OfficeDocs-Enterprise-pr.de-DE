---
title: Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Zusammenfassung: Konfigurieren und veranschaulichen, wie Office 365 Verwaltung von Informationsrechten Ihre vertraulichen Dateien schützt, auch wenn Sie in die falsche SharePoint Online Websitesammlung geschrieben werden.'
ms.openlocfilehash: 3fa771d63ca30fb53ac2c77466546cf3a2098deb
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031570"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Schutz vertraulicher Dateien in Office 365-Entwicklungs-/-Testumgebungen

 **Zusammenfassung:** Konfigurieren und veranschaulichen, wie Office 365 Verwaltung von Informationsrechten Ihre vertraulichen Dateien schützt, auch wenn Sie in die falsche SharePoint Online Websitesammlung geschrieben werden.
  
Information Rights Management (IRM) in Office 365 umfasst eine Reihe von Funktionen zum Schutz von Dokumenten, die aus SharePoint Online-Bibliotheken und -Listen heruntergeladen werden. Heruntergeladene Dateien sind verschlüsselt und verfügen über die Berechtigungen zum Öffnen, Kopieren, Speichern und Drucken, welche der SharePoint Online-Bibliothek entsprechen, in der sie gespeichert sind.
  
Mithilfe der Anleitungen in diesem Artikel können Sie IRM in Office 365 für Dateien aktivieren und testen, die in Ihrem Office 365-Testabonnement möglicherweise vertrauliche Informationen enthalten.
  
> [!TIP]
> Klicken Sie [hier](https://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Office 365 zu erhalten.
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>Phase 1: Erstellen Ihrer Office 365-Entwicklungs-/Testumgebung

Wenn Sie den Schutz vertraulicher Dateien auf einfache Weise mit Minimalanforderungen testen möchten, folgen Sie den Anweisungen für Phase 2 und 3 unter [Office 365 dev/test environment](office-365-dev-test-environment.md).
  
Wenn Sie den Schutz vertraulicher Dateien in einer simulierten Unternehmensumgebung testen möchten, folgen Sie den Anweisungen unter [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Zum Testen des Schutzes vertraulicher Dateien ist keine simulierte Enterprise-Entwicklungs-/Testumgebung erforderlich, die ein simuliertes, mit dem Internet verbundenes Intranet und eine Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) Gesamtstruktur umfasst. Dies wird hier als Option bereitgestellt, damit Sie den Schutz vertraulicher Dateien testen und damit in einer Umgebung, die eine typische Organisation darstellt, experimentieren können. 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>Phase 2: Demonstriert, wie Dokumente von Websites, die durch Berechtigungen geschützt sind, anderweitig (und möglicherweise missbräuchlich) verwendet werden können.

In dieser Phase demonstrieren Sie, wie jemand ein Dokument von einer Website, die durch Berechtigungen geschützt ist, herunterladen und anschließend auf eine Website hochladen kann, die nicht auf diese Weise geschützt und entsprechend allgemein zugänglich ist.
  
Sie fügen zuerst drei neue Benutzerkonten für Führungskräfte hinzu und weisen diesen Office 365 E5-Lizenzen zu.
  
Verwenden Sie die Anweisungen unter [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) , um die PowerShell-Module (falls erforderlich) zu installieren und eine Verbindung zu Ihrem neuen Office 365-Abonnement von herzustellen:
  
- Ihrem Computer aus (für die einfache Office 365-Entwicklungs-/Testunternehmensumgebung).
    
- Dem virtuellen Computer CLIENT1 aus (für die simulierte Office 365-Entwicklungs-/Testumgebung).
    
Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** den Namen des globalen Office 365-Administrators (Beispiel: jdoe@contosotoycompany.onmicrosoft.com) und das Kennwort Ihres Office 365-Testabonnements ein.
  
Geben Sie den Namen der Organisation (zum Beispiel „contosotoycompany“) und den zweistelligen Ländercode für Ihren Standort ein. Führen Sie dann über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das CEO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.
  
Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das CFO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.
  
Führen Sie über die „Windows Azure Active Directory-Modul für Windows PowerShell“-Eingabeaufforderung die folgenden Befehle aus:
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

Notieren Sie aus der **New-MsolUser**-Befehlsanzeige das Kennwort, das für das COO-Konto generiert wurde, und bewahren Sie es an einem sicheren Ort auf.
  
Im nächsten Schritt erstellen Sie eine private Führungskräftegruppe und fügen dieser die neuen Führungskräftekonten hinzu.
  
1. Wechseln Sie in Ihrem Browser zum Office-Portal unter [https://admin.microsoft.com](https://admin.microsoft.com) , und melden Sie sich bei Ihrem Office 365 Testabonnement mit ihrem globalen Administratorkonto an.
    
  - Wenn Sie die einfache Office 365-Entwicklungs-/Testumgebung verwenden, öffnen Sie eine private Sitzung in Internet Explorer bzw. in dem von Ihnen bevorzugten Browser, und melden Sie sich von Ihrem lokalen Computer aus an.
    
  - Wenn Sie die simulierte Office 365-Unternehmensentwicklungs-/-testumgebung verwenden, verwenden Sie das Azure-Portal, um sich mit dem virtuellen Computer CLIENT1 zu verbinden, und melden Sie sich dann von CLIENT1 aus an.
    
2. Klicken Sie auf der Registerkarte **Microsoft Office Home** auf **Admin > Gruppen > Gruppen**, und klicken Sie dann auf **Gruppe hinzufügen**.
    
3. Wählen Sie unter **Gruppe hinzufügen** die Option **Office 365-Gruppe** als Gruppentyp aus, geben Sie **Führungskräfte** unter **Name** und **Gruppen-ID** ein, und wählen Sie unter **Datenschutz** die Option **Privat**. Klicken Sie dann auf **Besitzer auswählen**.
    
4. Klicken Sie in der Liste auf den Namen Ihres globalen Administratorkontos.
    
5. Klicken Sie auf **Hinzufügen** und dann auf **Schließen**.
    
6. Klicken Sie in der Gruppenliste auf **Führungskräfte**.
    
7. Klicken Sie auf die Option zum Bearbeiten der Mitglieder****.
    
8. Klicken Sie auf **Mitglieder hinzufügen**. Wählen Sie in der Mitgliederliste die folgenden Benutzerkonten aus:
    
  - Chief Executive Officer
    
  - Chief Financial Officer
    
  - Chief Operations Officer
    
9. Klicken Sie auf **Speichern** und dann auf **Schließen**.
    
10. Schließen Sie die Registerkarte des Office Admin Centers****.
    
Im nächsten Schritt erstellen Sie eine Websitesammlung für Führungskräfte und erlauben nur den Mitgliedern der Führungskräftegruppe den Zugriff darauf.
  
1. Klicken Sie auf die Registerkarte **Microsoft Office Home** auf **Admin**.
    
2. Klicken Sie auf der Registerkarte **Office Admin Center** auf admin Centers **#a0 SharePoint**.
    
3. Klicken Sie auf der Registerkarte **SharePoint Admin Center** auf **neue #a0 private Websitesammlung**.
    
4. Geben Sie im Bereich neue Websitesammlung **Führungs** Kräfte in **Titel**, Führungskräfte im Feld URL ein, geben Sie den Namen des globalen Administratorkontos unter **Administrator**an, und klicken Sie dann auf **OK**.
    
5. Warten Sie, bis die neue Websitesammlung erstellt wurde. Wenn Sie fertig sind, kopieren Sie die URL der neuen Führungskräfte-Websitesammlung, und fügen Sie Sie in eine neue Registerkarte Ihres Browsers ein.
    
6. Klicken Sie in der oberen rechten Ecke der Websitesammlung **Führungskräfte** auf das Einstellungssymbol, und klicken Sie dann auf **Freigegeben für**.
    
7. Klicken Sie in **Share ' Executives '** auf **erweitert**.
    
8. Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder von „Führungskräfte“**.
    
9. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
10. Geben Sie im Bereich Führungs **Kräfte freigeben**den Namen **Führungs**Kräfte ein, klicken Sie auf die Gruppe **Führungskräfte** , und klicken Sie dann auf **Freigeben**.
    
11. Schließen Sie die Registerkarte **Benutzer und Gruppen** .
    
Im nächsten Schritt erlauben Sie allen Gruppenmitgliedern, auf die Websitesammlung „Vertrieb“ zuzugreifen.
  
1. Kopieren Sie auf der Registerkarte **SharePoint Admin Center** die URL der Sales-Websitesammlung, und fügen Sie Sie in eine neue Registerkarte Ihres Browsers ein..
    
2. Klicken Sie in der oberen rechten Ecke auf das Einstellungssymbol, und klicken Sie dann auf **Freigegeben für**.
    
3. Klicken Sie in **share "Sales Site Collection"** auf **erweitert**.
    
4. Klicken Sie in der Liste der SharePoint-Gruppen auf **Mitglieder der Websitesammlung „Vertrieb“**.
    
5. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
6. Geben Sie in **share "Sales Site Collection"** **jeden**ein, klicken Sie auf **jeder außer auf externe Benutzer**, und klicken Sie dann auf **Freigeben**.
    
7. Schließen Sie die **Websitesammlung „Vertrieb“** und die Registerkarten von **SharePoint**.
    
Als Nächstes melden Sie sich mit einem Führungskräftekonto an und erstellen ein Dokument in der Websitesammlung „Führungskräfte“.
  
1. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Klicken Sie auf der **Office 365-Anmeldeseite** auf **Anderes Konto verwenden**.
    
4. Geben Sie den Kontonamen **CEO** sowie das entsprechende Kennwort ein, und klicken Sie auf **Anmelden**.
    
5. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ( **https://**\<Organization Name>**. SharePoint.com/Sites/Executives**) ein.
    
6. Klicken Sie auf **Dokumente**, dann auf **neu** und dann auf **Word-Dokument**.
    
7. Klicken Sie in die Titelleiste, und geben Sie **VertraulicheDaten-VorIRM** ein.
    
8. Klicken Sie in den Textbereich des Dokuments, und geben Sie **Protokoll der letzten Vorstandssitzung** ein. Klicken Sie dann auf **Führungskräfte**.
    
      Die Datei **VertraulicheDaten-VorIRM.docx** sollte im Ordner **Dokumente** angezeigt werden.
    
Im nächsten Schritt laden Sie eine lokale Kopie des Dokuments „VertraulicheDaten-VorIRM.docx“ herunter und veröffentlichen diese versehentlich in der Websitesammlung „Vertrieb“.
  
1. Erstellen Sie auf dem lokalen Computer einen neuen Ordner (beispielsweise C:\\TLGs\\SensitiveDataTestFiles).
    
2. Wählen Sie auf der Registerkarte **Dokumente** in Ihrem Browser das Dokument **VertraulicheDaten-VorIRM.docx** aus, klicken Sie auf die drei Punkte (Ellipse), und klicken Sie dann auf **Herunterladen**.
    
3. Speichern Sie das Dokument **VertraulicheDaten-VorIRM.docx** in dem Ordner, den Sie in Schritt 1 erstellt haben.
    
4. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Sales" ein ( **https://**\<Organization Name>**. SharePoint.com/Sites/Sales**).
    
5. Klicken Sie auf den Ordner **Dokumente** der **Websitesammlung „Vertrieb“**.
    
6. Klicken Sie auf **Hochladen**, und geben Sie dann das Dokument **VertraulicheDaten-VorIRM.docx** in dem Ordner an, den Sie in Schritt 1 erstellt haben. Klicken Sie dann auf **OK**.
    
7. Stellen Sie sicher, dass sich das Dokument **VertraulicheDaten-VorIRM.docx** im Ordner **Dokumente** befindet.
    
8. Schließen Sie die Registerkarten **Vertrieb** und **SharePoint**.
    
Als Nächstes melden Sie sich als Benutzer5 an und versuchen, das Dokument „VertraulicheDaten-VorIRM.docx“ in der Websitesammlung „Vertrieb“ zu öffnen.
  
1. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Klicken Sie auf der **Office 365-Anmeldeseite** auf **Anderes Konto verwenden**.
    
4. Geben Sie den Benutzernamen und das Kennwort von Benutzer 5 ein, und klicken Sie dann auf **Anmelden**.
    
5. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.
    
6. Klicken Sie im Ordner **Dokumente** der **Websitesammlung „Vertrieb“** auf das Dokument **VertraulicheDaten-VorIRM.docx**. 
    
    Sie sollten den Inhalt sehen können.
    
7. Schließen Sie die Registerkarten **Dokumente** und **Websitesammlung „Vertrieb“**.
    
Indem der CEO das Dokument „VertraulicheDaten-VorIRM.docx“ versehentlich in der Websitesammlung „Vertrieb“ veröffentlicht hat, hat er die Berechtigungssicherheit der Websitesammlung „Führungskräfte“ umgangen.
  
Um Office 365 für die Phasen 3 und 4 vorzubereiten, aktivieren Sie IRM für SharePoint Online.
  
1. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Klicken Sie auf der **Office 365-Anmeldeseite** auf den Namen des globalen Administratorkontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
4. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** auf **Admin > Admin Center > SharePoint**.
    
5. Klicken Sie auf der Registerkarte **SharePoint Admin Center** auf **Einstellungen**.
    
6. Wählen Sie auf der Seite im Abschnitt **Verwaltung von Informationsrechten (IRM)** **die Option in der Konfiguration angegebene IRM-Dienst verwenden**aus, und wählen Sie dann **IRM-Einstellungen aktualisieren**aus.
    
7. Schließen Sie die Registerkarte **SharePoint Admin Center**.
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>Phase 3: Verwenden von SharePoint Information Rights Management mit einer privaten Office 365-Gruppe

In dieser Phase verwenden Sie SharePoint Information Rights Management mit einer privaten Office 365-Gruppe, um den Zugriff auf ein Dokument mit vertraulichen Informationen auch dann zu schützen, wenn es auf einer Website mit offenen Berechtigungen veröffentlicht wird.
  
Als Erstes aktivieren und konfigurieren Sie IRM für die Dokumentbibliothek der Websitesammlung „Führungskräfte“.  
  
1. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ein.
    
2. Klicken Sie auf **Dokumente**.
    
3. Klicken Sie in der oberen rechten Ecke auf das Einstellungssymbol, und klicken Sie dann auf **Bibliothekseinstellungen**.
    
4. Klicken Sie auf der Seite **Einstellungen** unter **Berechtigungen und Verwaltung** auf **Information Rights Management**.
    
5. Gehen Sie auf der Seite **Einstellungen für Information Rights Management** wie folgt vor:
    
  - Wählen Sie **Berechtigungen für Dokumente in dieser Bibliothek beim Herunterladen einschränken** aus.
    
  - Geben Sie unter **Berechtigungsrichtlinientitel erstellen** den Text **Führungskräfte** ein.
    
  - Geben Sie unter **Beschreibung der Berechtigungsrichtlinie hinzufügen** den Text **IRM für Führungskräfte** ein.
    
6. Klicken Sie auf **Optionen anzeigen**.
    
7. Wählen Sie unter **Zusätzliche IRM-Bibliothekseinstellungen festlegen** die Option **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen**.
    
8. Wählen Sie unter **Dokumentzugriffsrechte konfigurieren** die Optionen **Drucken durch anzeigende Benutzer zulassen** und **Anzeigenden Benutzern das Schreiben in einer Kopie des heruntergeladenen Dokuments gestatten**.
    
9. Wählen Sie unter **Gruppen Schutz und Anmeldeinformationen Intervall festlegen**die Option **Gruppen Schutz zulassen aus. Standardgruppe**, und geben Sie dann **Führungskräfte**ein.
    
10. Klicken Sie auf **OK**.
    
Im nächsten Schritt fungieren Sie als CEO und laden ein neues Dokument in den Dokumentordner „Führungskräfte“ hoch. Dann laden Sie das Dokument herunter und laden es versehentlich in den Dokumentordner „Vertrieb“ hoch.
  
1. Öffnen Sie den lokalen Ordner, in dem Sie das Dokument **VertraulicheDaten-VorIRM.docx** gespeichert haben.
    
2. 	Klicken Sie mit der rechten Maustaste auf **VertraulicheDaten-VorIRM.docx**, und klicken Sie dann auf **Kopieren**.
    
3. Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Einfügen**.
    
4. Benennen Sie die neue **vertraulichedaten-BeforeIRM-Copy. docx-** Datei in **Dokument vertraulichedaten-nachirm. docx**um.
    
5. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** in Ihrem Browser auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
6. Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).
    
7. Klicken Sie auf der **Office 365-Anmeldeseite** auf den Namen des CEO-Kontos, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
8. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Führungskräfte" ein.
    
9. Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **VertraulicheDaten-NachIRM.docx** im lokalen Ordner an, und klicken Sie dann auf **Öffnen**.
    
10. Wählen Sie das neue Dokument **VertraulicheDaten-NachIRM.docx** auf der Seite **Dokumente** aus, klicken Sie auf die Ellipse (…) in der Menüleiste, und klicken Sie dann auf **Herunterladen**.
    
11. Wenn Sie dazu aufgefordert werden, speichern Sie das Dokument **VertraulicheDaten-NachIRM.docx** in Ihrem lokalen Ordner, und überschreiben Sie dabei die ursprüngliche Version.
    
12. Schließen Sie die Registerkarte der Seite **Dokumente**.
    
13. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.
    
14. Klicken Sie auf **Dokumente**.
    
15. Klicken Sie auf der Seite **Dokumente** auf **Hochladen**, geben Sie das Dokument **VertraulicheDaten-NachIRM.docx** im lokalen Ordner an, und klicken Sie dann auf **Öffnen**.
    
16. Schließen Sie die **Websitesammlung „Vertrieb“** und die Registerkarten von **SharePoint**.
    
Als Nächstes fungieren Sie als normaler Benutzer und versuchen, auf das Dokument **VertraulicheDaten-NachIRM.docx** im Dokumentordner „Vertrieb“ zuzugreifen.
  
1. Klicken Sie auf der Registerkarte der **Microsoft Office-Startseite** in Ihrem Browser auf das Benutzersymbol in der oberen rechten Ecke, und klicken Sie dann auf **Abmelden**.
    
2. Wechseln Sie zu [https://admin.microsoft.com](https://admin.microsoft.com).
    
3. Klicken Sie auf der **Office 365 Anmelde** Seite auf den Kontonamen des Namen, geben Sie das Kennwort ein, und klicken Sie dann auf **Anmelden**.
    
4. Geben Sie auf einer neuen Registerkarte Ihres Browsers die URL der Websitesammlung "Vertrieb" ein.
    
5. Klicken Sie auf **Dokumente**.
    
6. Öffnen Sie auf der Seite **Dokumente** das Dokument **VertraulicheDaten-NachIRM.docx**. 
    
    Es sollte eine Meldung angezeigt werden, die besagt, "Sorry, Word kann dieses Dokument nicht öffnen, da es durch Information Rights Management (IRM) geschützt ist." 
    
7. Klicken Sie auf **In Word bearbeiten**. Sie werden gefragt, ob Sie die Datei öffnen möchten. Klicken Sie auf **Ja**.
    
8. Sie werden aufgefordert, sich anzumelden. Geben Sie den Namen des Kontos für Benutzer 5 an, und klicken Sie auf **Weiter**.
    
9. Sie werden aufgefordert, das Kennwort einzugeben. Geben Sie das Kennwort für das Konto von Benutzer 5 ein, und klicken Sie dann auf **Anmelden**.  
    
    Es sollte eine Nachricht angezeigt werden, die besagt, dass Sie keine Anmeldedaten haben, die Sie zum Öffnen dieses Dokuments berechtigen.
    
10. Klicken Sie auf **Nein**.
    
Eine andere Möglichkeit zum Anzeigen des IRM-Schutzes besteht darin, die Dateien im lokalen Ordner anzusehen. Die Datei **VertraulicheDaten-NachIRM.docx** sollte sehr viel größer sein als die Datei **VertraulicheDaten-VorIRM.docx**. Die Datei **VertraulicheDaten-NachIRM.docx** ist verschlüsselt, und sie enthält die Informationen zum IRM-Schutz.
  
## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)
  
[Basiskonfiguration der Entwicklungs-/Testumgebung](base-configuration-dev-test-environment.md)
  
[Office 365-Entwicklungs-/Testumgebung](office-365-dev-test-environment.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)


