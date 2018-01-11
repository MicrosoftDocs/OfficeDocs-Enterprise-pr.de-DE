---
title: "Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "Zusammenfassung: Verwenden dieser Test Lab Guide Ihrer Microsoft 365 Test-/Umgebung zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) hinzufügen."
ms.openlocfilehash: cd5a9801ec7cc5c8fe287fa65015fcb02dd542bf
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM

 **Zusammenfassung:** Verwenden Sie diese Test Lab Guide, zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) mit der Microsoft 365 Test-/Umgebung hinzuzufügen.
  
Der Microsoft Enterprise Mobilität + Sicherheit (zur Abstimmung) verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Mit den Anweisungen in diesem Artikel fügen Sie die mobile Anwendung Informationsverwaltungsrichtlinien (MAM) in Ihrer Microsoft 365 Dev/testumgebung.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Phase 1: Erstellen Sie Ihre Microsoft 365 Dev/Test-Umgebung

Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Phase 2: Erstellen und Bereitstellen von MAM-Richtlinien für iOS- und Android-Geräte

In dieser Phase werden zwei verschiedene MAM-Richtlinien erstellt und bereitgestellt: eine für iOS-Geräte und eine für Android-Geräte.
  
1. Wechseln Sie zum Office 365-Portal ([https://portal.office.com](https://portal.office.com)), und melden Sie sich bei Ihrem Office 365-Testabonnement mit Ihrem globalen Administratorkonto an.
    
2. Öffnen Sie auf einer neuen Registerkarte Ihres Browsers das Azure Portal ([https://azure.portal.com](https://azure.portal.com)), und melden Sie sich mit Ihrem Office 365 globaler Administrator-Konto.
    
3. Klicken Sie auf der Azure Portal Registerkarte in Internet Explorer im Navigationsbereich klicken Sie auf **Weitere Dienste** (oder auf den Pfeil nach rechts), geben Sie **Intune**, und klicken Sie dann auf **Intune**.
    
4. Klicken Sie im linken Navigationsbereich auf **Gruppen**.
    
5. Klicken Sie auf der Blade **-Benutzer und Gruppen alle Gruppen** auf **Hinzufügen**.
    
6. In der **Gruppe** Blade, geben Sie im Feld **Name** **iOS Gerätebenutzer verwaltete** **zugewiesen** **Mitgliedschaft geben**Sie in wählen, wählen Sie **Ja** für **Aktivieren von Office-Features?**, und klicken Sie dann auf **Erstellen**. 
    
7. Schließen Sie das **Gruppe** Blade.
    
8. Klicken Sie auf der Blade **-Benutzer und Gruppen alle Gruppen** auf **Hinzufügen**.
    
9. In der **Gruppe** Blade, geben Sie im Feld **Name** **Android verwaltete Gerätebenutzer** **zugewiesen** **Mitgliedschaft geben**Sie in wählen, wählen Sie **Ja** für **Aktivieren von Office-Features?**, und klicken Sie dann auf **Erstellen**.
    
10. Schließen Sie das Blade **-Benutzer und Gruppen alle Gruppen** .
    
11. Klicken Sie auf der Blade **Intune** in der Liste **schnell Aufgaben** **Erstellen einer Compliance-Richtlinie**.
    
12. Klicken Sie auf das **Compliance-Richtlinienprofilen** Blade **-Richtlinie erstellen**.
    
13. Geben Sie auf der Blade **-Richtlinie erstellen** im Feld **Name** **iOS**. **Plattform**wählen Sie **iOS aus**, klicken Sie auf **OK** , auf das Blade **iOS Compliance-Richtlinie** und klicken Sie dann auf **Erstellen**.
    
14. Klicken Sie auf das **Compliance-Richtlinienprofilen** Blade **-Richtlinie erstellen**.
    
15. Das Blade **-Richtlinie erstellen** im Feld **Name**Geben Sie auf **Android**. **Plattform**wählen Sie **Android**, klicken Sie auf **OK** , auf das Blade **Android Compliance-Richtlinien** und klicken Sie dann auf **Erstellen**.
    
16. Klicken Sie auf das Blade **Richtlinienprofilen Compliance** auf den Namen der Richtlinie **Android** .
    
17. Im linken Navigationsbereich dem Blade **Android - Eigenschaften** klicken Sie auf **Aufgaben**, und klicken Sie dann auf **Gruppen auswählen**.
    
18. Klicken Sie in der Blade **Gruppen auswählen** auf der **verwalteten Android-Gerät** Benutzergruppe, und klicken Sie dann auf **auswählen**.
    
19. Klicken Sie auf **Speichern**, und schließen Sie das Blade **Android - Zuordnungen** .
    
20. Klicken Sie auf das Blade **Compliance Richtlinienprofilen** auf den Namen der Richtlinie **iOS** .
    
21. Im linken Navigationsbereich dem Blade **iOS - Eigenschaften** klicken Sie auf **Aufgaben**, und klicken Sie dann auf **Gruppen auswählen**.
    
22. Klicken Sie in der Blade **Gruppen auswählen** auf die Gruppe **verwaltete iOS Gerätebenutzer** , und klicken Sie dann auf **auswählen**.
    
23. Klicken Sie auf **Speichern**, und schließen Sie das Blade **iOS - Zuordnungen** .
    
24. Schließen Sie das **Compliance-Richtlinienprofilen** Blade.
    
25. Klicken Sie auf das Blade **Intune** im linken Navigationsbereich auf **apps verwalten** .
    
26. Klicken Sie auf das Blade **Mobile Apps** auf **Apps**.
    
27. Klicken Sie in der Liste der apps **PowerPoint**, 
    
28. Klicken Sie auf die **PowerPoint-Übersicht** Blade auf **Zuordnungen > Gruppen auswählen > verwaltete iOS-Geräte > Wählen Sie**. Wählen Sie **Geben**Sie in **verfügbar**, und klicken Sie dann auf **Speichern**.
    
29. Wiederholen Sie Schritt 28 für die folgenden Apps:
    
  - Outlook für Android
    
  - Word für iOS
    
  - Excel für iOS
    
  - Outlook für iOS
    
  - Microsoft Dynamics CRM auf iPad für iOS
    
  - Microsoft Dynamics CRM auf iPhone für iOS
    
  - Dynamics CRM für Smartphones für Android
    
  - Dynamics CRM für Tablets für Android
    
  - Excel für Android
    
  - Word für Android
    
  - OneNote für iOS
    
30. Schließen Sie das **Mobile Apps – Apps** Blade.
    
31. Klicken Sie auf das Blade **Mobile Apps** auf **App-Richtlinien**.
    
32. Klicken Sie auf das **App-Richtlinien** Blade auf **eine Richtlinie hinzufügen**.
    
33. Geben Sie auf das **Hinzufügen einer Richtlinie** Blade **iOS**, und klicken Sie dann auf **Wählen Sie apps erforderlich**.
    
34. Klicken Sie in der Blade **Apps** auf **PowerPoint**, **Microsoft Dynamics CRM auf iPhone**, **Excel**, **Microsoft Dynamics CRM auf iPhone**, **Word**, **OneNote**und **Outlook**, und klicken Sie dann auf **auswählen**.
    
35. Klicken Sie auf das Blade **Hinzufügen einer Richtlinie** auf **Erstellen**.
    
36. Klicken Sie auf das **App-Richtlinien** Blade auf **eine Richtlinie hinzufügen**.
    
37. Geben Sie auf das **Hinzufügen einer Richtlinie** Blade **Android**, wählen Sie **Android** **-Plattform**und klicken Sie dann auf **Wählen Sie apps erforderlich**.
    
38. Klicken Sie in der Blade **Apps** auf **PowerPoint**, **Dynamics CRM für Tablets**, **Excel**, **Word**, **Outlook**und **Dynamics CRM für Telefone**, und klicken Sie dann auf **auswählen**.
    
39. Klicken Sie auf das Blade **Hinzufügen einer Richtlinie** auf **Erstellen**.
    
Sie nun verfügen über zwei MAM-Richtlinien, eine für iOS-Geräte und eine für Android-Geräte, und können nun mit verschiedenen Einstellungen für die ausgewählten Apps experimentieren.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="see-also"></a>Weitere Artikel

[Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise-Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


