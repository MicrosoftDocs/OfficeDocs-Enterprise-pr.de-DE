---
title: Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM
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
description: 'Zusammenfassung: Verwenden dieser Test Lab Guide Ihrer Microsoft 365 Test-/Umgebung zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) hinzufügen.'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188153"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM

 **Zusammenfassung:** Verwenden Sie diese Test Lab Guide, zur Abstimmung mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) mit der Microsoft 365 Test-/Umgebung hinzuzufügen.
  
Der Microsoft Enterprise Mobilität + Sicherheit (zur Abstimmung) verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Mit den Anweisungen in diesem Artikel fügen Sie die mobile Anwendung Informationsverwaltungsrichtlinien (MAM) in Ihrer Microsoft 365 Dev/testumgebung.
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>Phase 1: Erstellen Sie Ihre Microsoft 365 Dev/Test-Umgebung

Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Phase 2: Erstellen und Bereitstellen von MAM-Richtlinien für iOS- und Android-Geräte

In dieser Phase werden zwei verschiedene MAM-Richtlinien erstellt und bereitgestellt: eine für iOS-Geräte und eine für Android-Geräte.
  
1. Wechseln Sie zu Office 365-Portal ([https://portal.office.com](https://portal.office.com)) und melden Sie sich Test Office 365-Abonnement mit Ihrer globalen Administratorkonto an.
    
2. Öffnen Sie auf einer neuen Registerkarte des Browsers, das Azure-Portal ([https://azure.portal.com](https://azure.portal.com)), und melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein.
    
3. Klicken Sie auf der Azure Portal Registerkarte in Internet Explorer im Navigationsbereich klicken Sie auf **alle Dienste**, geben Sie **Intune**, und klicken Sie dann auf **Intune**.
    
4. Klicken Sie im linken Navigationsbereich auf **Gruppen**.
    
5. Klicken Sie auf das Blade **Gruppen alle Gruppen** auf **+ neue Gruppe**.
    
6. Wählen Sie in der **Gruppe** Blade, **Office 365** für **Gruppentyp?**, geben Sie im Feld **Name** **iOS Gerätebenutzer verwaltet** , wählen Sie in **die Mitgliedschaft Typ** **zugewiesen** und dann auf **Erstellen**. 
    
7. Schließen Sie das Blatt **Gruppe**.
    
8. Klicken Sie auf das Blade **Gruppen alle Gruppen** auf **Hinzufügen**.
    
9. Wählen Sie in der **Gruppe** Blade, **Office 365** für **Gruppentyp?**, geben Sie im Feld **Name** **Android verwaltete Benutzer des Geräts** , wählen Sie in **die Mitgliedschaft Typ** **zugewiesen** und dann auf **Erstellen**.
    
10. Schließen Sie das Blade **Gruppen alle Gruppen** .
    
11. Klicken Sie auf dem Blatt **Intune** in der Liste **Schnelle Aufgaben** auf **Erstellen Sie eine Konformitätsrichtlinie**.
    
12. Klicken Sie auf dem Blatt **Kompatibilitätsrichtlinienprofile** auf **Richtlinie erstellen**.
    
13. Geben Sie auf dem Blatt **Richtlinie erstellen** im Feld **Name**, den Text **iOS** ein. Wählen Sie für **Plattform** die Option **iOS** aus, klicken Sie auf dem Blatt ** 	iOS-Kompatibilitätsrichtlinie** auf **OK**, und klicken Sie dann auf **Erstellen**.
    
14. Klicken Sie auf dem Blatt **Kompatibilitätsrichtlinienprofile** auf **Richtlinie erstellen**.
    
15. Geben Sie auf dem Blatt **Richtlinie erstellen** im Feld **Name**, den Text **Android** ein. Wählen Sie für **Plattform** die Option **Android** aus, klicken Sie auf dem Blatt **Android-Kompatibilitätsrichtlinie** auf **OK**, und klicken Sie dann auf **Erstellen**.
    
16. Klicken Sie auf dem Blatt **Kompatibilitätsrichtlinienprofile** auf den Richtliniennamen **Android**.
    
17. Klicken Sie im linken Navigationsbereich des Blatts **Android - Eigenschaften** auf **Zuweisungen**, und klicken Sie dann auf **Gruppen auswählen**.
    
18. Klicken Sie auf dem Blatt **Gruppen auswählen** auf die Gruppe **Verwaltete Android-Gerätebenutzer**, und klicken Sie dann auf **Auswählen**.
    
19. Klicken Sie auf **Speichern**, und schließen Sie das Blade **Android - Zuordnungen** .
    
20. Klicken Sie auf dem Blatt **Kompatibilitätsrichtlinienprofile** auf den Richtliniennamen **iOS**.
    
21. Klicken Sie im linken Navigationsbereich des Blatts **iOS - Eigenschaften** auf **Zuweisungen**, und klicken Sie dann auf **Gruppen auswählen**.
    
22. Klicken Sie auf dem Blatt **Gruppen auswählen** auf die Gruppe **Verwaltete iOS-Gerätebenutzer**, und klicken Sie dann auf **Auswählen**.
    
23. Klicken Sie auf **Speichern**, und schließen Sie das Blade **iOS - Zuordnungen** .
    
24. Schließen Sie das Blatt **Kompatibilitätsrichtlinienprofile**.
    
25. Klicken Sie auf dem Blatt **Intune** im linken Navigationsbereich auf **Apps verwalten**.
    
26. Klicken Sie auf dem Blatt **Mobile Apps** auf **Apps**.
    
27. Klicken Sie in der Liste der Apps auf **PowerPoint**.  
    
28. Klicken Sie auf dem Blatt **PowerPoint-Übersicht** auf **Zuweisungen > Gruppen auswählen > Verwaltete iOS-Geräte > Auswählen**. Wählen Sie im Feld **Typ** die Option **Verfügbar** aus, und klicken Sie dann auf **Speichern**.
    
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
    
30. Schließen Sie das Blatt **Mobile Apps - Apps**.
    
31. Klicken Sie auf dem Blatt **Mobile Apps** auf **App-Schutzrichtlinien**.
    
32. Klicken Sie auf dem Blatt **App-Schutzrichtlinien** auf **Richtlinie hinzufügen**.
    
33. Geben Sie auf dem Blatt **Richtlinie hinzufügen** den Namen **iOS** ein, und klicken Sie dann auf **Erforderliche Apps auswählen**.
    
34. Klicken Sie auf dem Blatt **Apps** auf **PowerPoint**, **Microsoft Dynamics CRM auf iPhone**, **Excel**, **Microsoft Dynamics CRM auf iPhone**, **Word**, **OneNote** und **Outlook**, und klicken Sie dann auf **Auswählen**.
    
35. Klicken Sie auf dem Blatt **Richtlinie hinzufügen** auf **Erstellen**.
    
36. Klicken Sie auf dem Blatt **App-Schutzrichtlinien** auf **Richtlinie hinzufügen**.
    
37. Geben Sie auf dem Blatt **Richtlinie hinzufügen** den Namen **Android** ein, wählen Sie unter **Plattform** die Option **Android** aus, und klicken Sie dann auf **Erforderliche Apps auswählen**.
    
38. Klicken Sie auf dem Blatt **Apps** auf **PowerPoint**, **Dynamics CRM für Tablets**, **Excel**, **Word**, **Outlook** und **Dynamics CRM für Smartphones**, und klicken Sie dann auf **Auswählen**.
    
39. Klicken Sie auf dem Blatt **Richtlinie hinzufügen** auf **Erstellen**.
    
Sie nun verfügen über zwei MAM-Richtlinien, eine für iOS-Geräte und eine für Android-Geräte, und können nun mit verschiedenen Einstellungen für die ausgewählten Apps experimentieren.
  
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="see-also"></a>Siehe auch

[Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise-Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


