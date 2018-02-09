---
title: "Schützen von SharePoint Online-Dateien mit Azure Information Protection"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Zusammenfassung: Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite."
ms.openlocfilehash: 5beba188cadc88c15ec75ed2adb4899d9b41b8ec
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Schützen von SharePoint Online-Dateien mit Azure Information Protection

 **Zusammenfassung:** Verwenden Sie Azure Information Protection zum Schützen von Dateien auf einer streng vertraulichen SharePoint Online-Teamwebsite.
  
Konfigurieren Sie anhand der Schritte in diesem Artikel Azure Information Protection, um Verschlüsselung und Berechtigungen auf Dateien in einer streng vertraulichen SharePoint Online-Teamwebsite zu konfigurieren. Der Verschlüsselungs- und Berechtigungsschutz einer Datei bleibt auch dann bestehen, wenn die Datei von der Website heruntergeladen wird. Weitere Informationen zu streng vertraulichen SharePoint Online-Teamwebsites finden Sie unter [Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Wenn Azure Information Protection-Verschlüsselung auf Dateien in Office 365 angewendet wird, kann der Dienst den Inhalt dieser Dateien nicht verarbeiten. Gemeinsame Dokumenterstellung, eDiscovery, Suche, Delve und andere Features für die Zusammenarbeit funktionieren nicht. DLP-Richtlinien können nur auf die Metadaten (einschließlich Office 365-Bezeichnungen) angewendet werden, aber nicht auf den Inhalt dieser Dateien (z. B. Kreditkartennummern in Dateien). 
  
Befolgen Sie zuerst die Anweisungen unter [Aktivieren von Azure Rights Management über Office 365 Admin Center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) für Ihr Office 365-Abonnement.
  
Konfigurieren Sie anschließend Azure Information Protection mit einer neuen bereichsbezogenen Richtlinie und einer untergeordneten Bezeichnung mit dem Schutz und den Berechtigungen für die streng vertrauliche SharePoint Online-Teamwebsite.
  
1. Melden Sie sich mit einem Konto beim Office 365-Portal an, das über die Rolle „Sicherheitsadministrator" oder Unternehmensadministrator" verfügt. Hilfe finden Sie unter [Wo kann ich mich bei Office 365 Business anmelden?](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Wechseln Sie auf einer separaten Registerkarte im Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com).
    
3. Wenn Sie Azure Information Protection zum ersten Mal konfigurieren, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. Klicken Sie im Listenbereich auf **Weitere Dienste**, geben Sie **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
5. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Bereichsbezogene Richtlinien > + Neue Richtlinie hinzufügen**.
    
6. Geben Sie unter **Richtlinienname** einen Namen für die neue Richtlinie und unter **Beschreibung** eine Beschreibung ein.
    
7. Klicken Sie auf **Auswählen, welche Benutzer oder Gruppen diese Richtlinie erhalten > Benutzer/Gruppen**, und wählen Sie dann die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus. 
    
8. Klicken Sie auf **Auswählen > OK**.
    
9. Klicken Sie für die Bezeichnung **Streng vertraulich** auf die Auslassungspunkte (...), und klicken Sie dann auf **Unterbezeichnung hinzufügen**.
    
10. Geben Sie unter **Name** einen Namen für die Unterbezeichnung und unter **Beschreibung** eine Beschreibung für die Bezeichnung ein.
    
11. Klicken Sie unter **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen** auf **Schützen**.
    
12. Klicken Sie im Abschnitt **Schutz** auf **Azure (Cloudschlüssel)**.
    
13. Klicken Sie im Blatt **Schützen** unter **Schutzeinstellungen** auf **+ Berechtigungen hinzufügen**.
    
14. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** unter **Benutzer und Gruppen angeben** auf **+ Verzeichnis durchsuchen**.
    
15. Wählen Sie im Bereich **AAD-Benutzer und -Gruppen** die Websitemitglieder-Zugriffsgruppe für Ihre streng vertrauliche SharePoint Online-Teamwebsite aus, und klicken Sie dann auf **Auswählen**.
    
16. Deaktivieren Sie unter **Aus voreingestellten Berechtigungen wählen** die Kontrollkästchen **Drucken**, **Inhalte kopieren und extrahieren** und **Weiterleiten**.
    
17. Klicken Sie zweimal auf **OK**.
    
18. Klicken Sie auf dem Blatt **Untergeordnete Bezeichnung** auf **Speichern**.
    
19. Schließen Sie das Blatt für die neue bereichsbezogene Richtlinie.
    
20. Klicken Sie auf dem Blatt **Azure Information Protection - Bereichsbezogene Richtlinien** auf **Veröffentlichen**.
    
Dies ist die resultierende Konfiguration für Ihre streng vertrauliche SharePoint Online-Teamwebsite.
  
![Bezeichnung „Azure Information Protection“ für eine isolierte SharePoint Online-Teamwebsite.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Sie können jetzt damit beginnen, Dokumente zu erstellen und diese mit Azure Information Protection und der neuen Bezeichnung zu schützen.
  
Sie müssen den [Azure Information Protection-Client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) auf Ihrem Gerät oder Ihrem Windows-Computer installieren. Sie können ein Skript erstellen und die Installation automatisieren, oder Benutzer können den Client manuell installieren. Informationen finden Sie in den folgenden Ressourcen:
  
- [Die Clientseite von Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Installieren des Azure Information Protection-Clients](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Downloadseite für die manuelle Installation](https://www.microsoft.com/download/details.aspx?id=53018)
    
Nach der Installation führen die Benutzer eine Office-Anwendung (wie z. B. Microsoft Word) aus und melden sich von dort aus mit Ihrem Office 365-Konto an. Die neue Symbolleiste **Information Protection** ermöglicht es Benutzern, die neue Bezeichnung auszuwählen. Stellen Sie sicher, dass Ihre Benutzer die SharePoint Online-Teamwebsite kennen und wissen, welche Bezeichnung sie verwenden müssen, um ihre streng vertraulichen Dateien zu schützen.
  
> [!NOTE]
> Wenn Sie über mehrere streng vertrauliche SharePoint Online-Teamwebsites verfügen, müssen Sie anhand der oben aufgeführten Einstellungen mehrere bereichsbezogene Azure Information Protection-Richtlinien mit Unterbezeichnungen erstellen, wobei die Berechtigungen für jede Unterbezeichnung auf die Websitemitglieder-Zugriffsgruppe einer bestimmten SharePoint Online-Teamwebsite festgelegt sind. 
  
## <a name="see-also"></a>Weitere Artikel

[Sichern von SharePoint Online-Websites und -Dateien](secure-sharepoint-online-sites-and-files.md)
  
[Sichern von SharePoint Online-Websites in einer Entwicklungs-/Testumgebung](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft-Sicherheitsleitfaden für politische Kampagnen, gemeinnützigen Organisationen und andere agile Organisationen](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Cloudakzeptanz und Hybridlösungen](cloud-adoption-and-hybrid-solutions.md)




