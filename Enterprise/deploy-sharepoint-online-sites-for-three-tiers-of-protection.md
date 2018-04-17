---
title: Bereitstellen von SharePoint Online-Websites für drei Ebenen des Schutzes
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Zusammenfassung: Erstellen und Konfigurieren von SharePoint Online Teamwebsites für verschiedene Ebenen der Schutz von Informationen.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>Bereitstellen von SharePoint Online-Websites für drei Ebenen des Schutzes

 **Zusammenfassung:** Erstellen und Konfigurieren von SharePoint Online Teamwebsites für verschiedene Ebenen der Schutz von Informationen.
  
Verwenden Sie die Schritte in diesem Artikel, um Richtlinien für grundlegende, vertrauliche und streng vertrauliche SharePoint Online-Teamwebsites zu entwerfen. Weitere Informationen zu diesen drei Schutzebenen finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md).
  
## <a name="baseline-sharepoint-online-team-sites"></a>Grundlegende SharePoint Online-Teamwebsites

Der grundlegende Schutz enthält jeweils öffentliche und private Teamwebsites. Öffentliche Teamwebsites können von allen Benutzern in der Organisation ermittelt werden und alle haben Zugriff auf diese. Nur Mitglieder der Office 365-Gruppe, die mit der Teamwebsite verknüpft sind, können die privaten Websites ermitteln und auf diese zugreifen. Diese beiden Arten von Teamwebsites erlauben Mitgliedern, die Website für andere Personen freizugeben.
  
### <a name="public"></a>Public (Öffentlich)

Um eine grundlegende SharePoint Online-Teamwebsite mit öffentlichem Zugriff und Berechtigungen zu erstellen, tun Sie Folgendes:
  
1. Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie in der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Name der Website** einen Namen für die öffentliche Teamwebsite ein. 
    
6. Geben Sie im Feld **Team site description** (Beschreibung der Teamwebsite) eine Beschreibung der Website ein.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Öffentlich - Alle Benutzer in der Organisation können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Grundschutz für eine öffentliche SharePoint Online-Teamwebsite.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>Privat

Um eine grundlegende SharePoint Online-Teamwebsite mit privatem Zugriff und Berechtigungen zu erstellen, tun Sie Folgendes:
  
1. Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie in der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Name der Website** einen Namen für die private Teamwebsite ein. 
    
6. Geben Sie Team Site in **Beschreibung eine Beschreibung des Zwecks der Website.**
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Geben Sie im Bereich **Who do you want to add?** (Wen möchten Sie hinzufügen?) unter **Mitglieder hinzufügen** die Namen der Benutzerkonten ein, die über Zugriff auf diese private Teamwebsite verfügen.
    
9. Wenn Sie fertig sind hinzufügen den ersten Satz von Elementen zu der Website, klicken Sie auf **Fertig stellen**
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Grundschutz für eine private SharePoint Online-Teamwebsite.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>Vertrauliche grundlegende SharePoint Online-Teamwebsites

Eine vertrauliche SharePoint Online-Teamwebsite ist eine isolierte Teamwebsite. Das heißt, dass die Berechtigungen über die Mitgliedschaft in SharePoint-Gruppen statt der Mitgliedschaft in der Office 365-Gruppe, die der Teamwebsite zugeordnet ist, gesteuert werden.
  
Beim Erstellen einer isolierten Teamwebsite gibt es zwei Hauptschritte.
  
### <a name="step-1-design-your-isolated-site"></a>Schritt 1: Entwerfen der isolierten Website

Um eine isolierte Teamwebsite zu erstellen, müssen Sie Folgendes festlegen:
  
- Die SharePoint-Gruppen und Berechtigungsstufen.
    
- Den Satz von Zugriffsgruppen, die Mitglieder der SharePoint-Gruppen sein sollen.
    
     Der empfohlene Satz von Access Gruppen ist eine für Websitemitglieder, Website und Websiteadministratoren.
    
- Ob Sie verschachtelte Gruppen innerhalb Ihrer Zugriffsgruppen verwenden.
    
Beispielsweise sehen die empfohlene Gruppenstruktur und Berechtigungsstufen wie folgt aus:
  
|**SharePoint-Gruppe**|**Berechtigungsstufe**|**Zugriffsgruppe (Beispiele)**|
|:-----|:-----|:-----|
|[Websitename] Mitglieder  <br/> |Bearbeiten  <br/> |[Websitename] Mitglieder  <br/> |
|[Websitename] Besucher  <br/> |Überwachungsdaten  <br/> |[Websitename] Viewer  <br/> |
|[Websitename] Besitzer  <br/> |Vollzugriff  <br/> |[Websitename] Administratoren  <br/> |
   
Die SharePoint-Gruppen und -Berechtigungsstufen werden standardmäßig für eine Teamwebsite erstellt. Sie müssen die Namen Ihrer Zugriffsgruppen bestimmen.
  
Informationen zum Entwurfsprozess finden Sie unter [Entwerfen einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Schritt 2: Bereitstellen Ihrer isolierten Website

Um Ihre isolierte Website bereitzustellen, müssen Sie zunächst Folgendes tun:
  
- Bestimmen Sie die Benutzerkonten und -gruppen, die jeder Zugriffsgruppe hinzugefügt werden soll.
    
- Erstellen Sie die Zugriffsgruppen, und fügen Sie die Benutzer und Gruppenmitglieder hinzu.
    
Detaillierte Schritte finden Sie in **Phase 1** unter [Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md).
  
Erstellen Sie als Nächstes mit den folgenden Schritten die SharePoint Online-Teamwebsite.
  
1. Melden Sie sich beim Office 365-Portal mit einem Konto an, das auch zum Verwalten der SharePoint Online-Teamwebsite verwendet wird (SharePoint Online-Administrator). Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Klicken Sie in der Liste von Kacheln auf **SharePoint**.
    
3. Klicken Sie auf der neuen Registerkarte **SharePoint** in Ihrem Browser auf **+ Website erstellen**.
    
4. Klicken Sie auf der Seite **Website erstellen** auf **Teamwebsite**.
    
5. Geben Sie unter **Name der Website** einen Namen für die private Teamwebsite ein.
    
6. Geben Sie im Feld **Team Site Beschreibung**eine optionale Beschreibung ein.
    
7. Wählen Sie unter **Datenschutzeinstellungen** die Option **Privat - nur Mitglieder können auf diese Website zugreifen** aus, und klicken Sie dann auf **Weiter**.
    
8. Klicken Sie im Bereich **Wer soll hinzugefügt werden?** auf **Fertig stellen**.
    
Konfigurieren Sie dann auf der neuen SharePoint Online-Teamwebsite die Berechtigungen mithilfe folgender Schritte.
  
1. Ermitteln Sie den UPN (User Principal Name) des IT-Administrators oder der anderen Person, die für das Beantworten und Bearbeiten von Anfragen hinsichtlich des Zugriffs auf die Website zuständig ist (Beispiel für einen UPN: belindan@contoso.com). Notieren Sie den UPN hier: _________________________________________.
    
2. Klicken Sie in der Symbolleiste auf das Symbol „Einstellungen" und anschließend auf **Websiteberechtigungen**.
    
3. Klicken Sie im Bereich **Websiteberechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
4. Klicken Sie auf der neuen Registerkarte **Berechtigungen** in Ihrem Browser auf **Zugriffseinstellungen anfordern**.
    
5. Im Dialogfeld **Einstellungen für Zugriffsanforderungen**:
    
  - Deaktivieren Sie die Kontrollkästchen **Mitgliedern das Freigeben der Website sowie einzelner Dateien und Ordner erlauben** und **Mitgliedern erlauben, andere Benutzer der Gruppe "Websitemitglieder" einzuladen**.
    
  - Geben Sie den UPN Ihres IT-Administrators aus Schritt 1 unter **Alle Zugriffsanforderungen senden**.
    
  - Klicken Sie auf **OK**.
    
6. Klicken Sie auf der Registerkarte **Berechtigungen** Ihres Browsers auf **[Websitename] Mitglieder** in der Liste.
    
7. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
8. Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Gruppe Ihrer Website Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.
    
9. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
10. Klicken Sie in der Liste **[Websitename] Besitzer** auf.
    
11. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
12. Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Gruppe der Administratoren-Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.
    
13. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
14. Klicken Sie in der Liste auf **Besucher [Websitename]** .
    
15. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
16. Klicken Sie im Dialogfeld **Freigeben** Geben Sie den Namen der Websitegruppe Leser von Berichten Zugriff für diese Website, wählen Sie sie aus, und klicken Sie auf **Freigeben**.
    
17. Schließen Sie die Registerkarte **Berechtigungen** Ihres Browsers.
    
Die Ergebnisse dieser Berechtigungseinstellungen sehen folgendermaßen aus:
  
- Die SharePoint-Gruppe **[Websitename] Besitzer** enthält die Zugriffsgruppe des Websiteadministrators, in der alle Mitglieder über die Berechtigungsstufe **Vollzugriff** verfügen.
    
- Die SharePoint-Gruppe **[Websitename] Mitglieder** enthält die Zugriffsgruppe der Websitemitglieder, in der alle Mitglieder über die Berechtigungsstufe **Bearbeiten** verfügen.
    
- Die SharePoint-Gruppe **[Websitename] Besucher** enthält die Zugriffsgruppe der Websitebesucher, in der alle Mitglieder über die Berechtigungsstufe **Lesen** verfügen.
    
- Die Möglichkeit, dass Mitglieder andere Mitglieder einladen, ist deaktiviert.
    
- Die Möglichkeit, dass Nicht-Mitglieder Zugriff anfordern, ist aktiviert.
    
Nachfolgend sehen Sie die daraus resultierende Konfiguration.
  
![Schutzebene „Vertraulich“ für eine isolierte SharePoint Online-Teamwebsite.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
Die Mitglieder der Website können nun über Gruppenmitgliedschaft in einer der Zugriffsgruppen sicher an den Ressourcen der Website zusammenarbeiten.
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>Streng vertrauliche SharePoint Online-Teamwebsites

Eine streng vertrauliche SharePoint Online-Teamwebsite ist eine isolierte Teamwebsite, was bedeutet, dass Berechtigungen über die Mitgliedschaft in SharePoint-Gruppen und nicht über die Mitgliedschaft in der Office 365-Gruppe gesteuert werden, die mit der Teamwebsite verknüpft ist.
  
Für die Erstellung einer isolierten Teamwebsite für streng vertrauliche Informationen und Kollaboration sind zwei Schritte nötig.
  
### <a name="step-1-design-your-isolated-site"></a>Schritt 1: Entwerfen Ihrer isolierten Website

Um eine isolierte Teamwebsite zu erstellen, müssen Sie Folgendes festlegen:
  
- Die SharePoint-Gruppen und Berechtigungsstufen.
    
- Den Satz von Zugriffsgruppen, die Mitglieder der SharePoint-Gruppen sein sollen.
    
     Der empfohlene Satz von Access Gruppen ist eine für Websitemitglieder, Website und Websiteadministratoren.
    
- Ob Sie verschachtelte Gruppen innerhalb Ihrer Zugriffsgruppen verwenden.
    
Beispielsweise sehen die empfohlene Gruppenstruktur und Berechtigungsstufen wie folgt aus:
  
|**SharePoint-Gruppe**|**Berechtigungsstufe**|**Zugriffsgruppe (Beispiele)**|
|:-----|:-----|:-----|
|[Websitename] Mitglieder  <br/> |Bearbeiten  <br/> |[Websitename] Mitglieder  <br/> |
|[Websitename] Besucher  <br/> |Überwachungsdaten  <br/> |[Websitename] Viewer  <br/> |
|[Websitename] Besitzer  <br/> |Vollzugriff  <br/> |[Websitename] Administratoren  <br/> |
   
Die SharePoint-Gruppen und -Berechtigungsstufen werden standardmäßig für eine Teamwebsite erstellt. Sie müssen die Namen Ihrer Zugriffsgruppen bestimmen.
  
Informationen zum Entwurfsprozess finden Sie unter [Entwerfen einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md).
  
### <a name="step-2-deploy-your-isolated-site"></a>Schritt 2: Bereitstellen Ihrer isolierten Website

Um Ihre isolierte Website bereitzustellen, müssen Sie zuerst Folgendes durchführen:
  
- Ermitteln Sie die Benutzer und Gruppenmitglieder der einzelnen Zugriffsgruppen.
    
- Erstellen Sie die Zugriffsgruppen, und fügen Sie die Benutzer und Gruppenmitglieder hinzu.
    
- Erstellen Sie eine isolierte Teamwebsite, die Ihre Zugriffsgruppen verwendet.
    
Detaillierte Schritte finden Sie unter [Bereitstellen einer isolierten SharePoint Online-Teamwebsite](deploy-an-isolated-sharepoint-online-team-site.md).
  
Nachfolgend sind die Ergebnisse dieser Berechtigungseinstellungen aufgeführt:
  
- Die SharePoint-Gruppe **[Websitename] Besitzer** enthält die Zugriffsgruppe des Websiteadministrators, in der alle Mitglieder über die Berechtigungsstufe **Vollzugriff** verfügen.
    
- Die SharePoint-Gruppe **[Websitename] Mitglieder** enthält die Zugriffsgruppe der Websitemitglieder, in der alle Mitglieder über die Berechtigungsstufe **Bearbeiten** verfügen.
    
- Die SharePoint-Gruppe **[Websitename] Besucher** enthält die Zugriffsgruppe der Websitebesucher, in der alle Mitglieder über die Berechtigungsstufe **Lesen** verfügen.
    
- Die Möglichkeit, dass Mitglieder andere Mitglieder einladen, ist deaktiviert.
    
- Die Möglichkeit, dass Nicht-Mitglieder Zugriff anfordern, ist deaktiviert.
    
Im Folgenden sehen Sie die resultierende Konfiguration.
  
![Schutzebene „Streng vertraulich“ für eine isolierte SharePoint Online-Teamwebsite.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
Jetzt können die Mitglieder der Website über die Gruppenmitgliedschaft in einer der Zugriffsgruppen sicher zusammenarbeiten und die Ressourcen der Website nutzen.
  
## <a name="next-step"></a>Nächster Schritt

[Schützen von SharePoint Online-Dateien mit Office 365 Etiketten und DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>Siehe auch

[Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md)
  
[Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




