---
title: Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Zusammenfassung: Mit diesem Test Lab Guide können Geräte in Ihrer Microsoft 365 Dev/Test-Umgebung zu registrieren und Remote zu verwalten.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188103"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Registrieren von iOS- und Android-Geräten in Ihrer Entwicklungs-/Testumgebung für Microsoft 365 Enterprise

 **Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.
  
Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Wenn Sie Sicherheit auf Device-Ebene anwenden möchten, müssen Sie in Microsoft Intune Geräte registrieren. Gerät-Registrierung können Sie zum Verwalten von Geräten im Besitz der Organisation nicht nur aber auch persönlich (BYOD) und gemeinsam genutzten Geräten, abhängig von Ihrer Organisation rechtliche der Richtlinien.
  
Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung

Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2: Registrieren Sie Ihre iOS und Android-Geräte

Verwenden Sie zunächst die Anweisungen in [Installieren und melden Sie sich die app Unternehmensportal](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) zum Anpassen von Microsoft Intune Unternehmensportal-app für Ihren Test-/-Mandanten.

Im nächsten Schritt verwenden Sie die Anweisungen in [Richten Sie Ihre Unternehmensressourcen zugreifen,](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) einer iOS-Geräte zu registrieren.

Im nächsten Schritt verwenden Sie die Anweisungen in [Registrieren Ihrer Android-Gerät im Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) Android-Gerät zu registrieren.

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>Phase 2: Verwalten Sie Ihrer iOS und Android-Geräte Remote

Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote entfernen.
  
So sperren Sie ein iOS-Gerät remote
  
1.  Öffnen Sie eine neue Registerkarte, und wechseln Sie zur http://manage.microsoft.com (falls erforderlich). 

2.  Der Microsoft Intune-Verwaltungskonsole des Browsers klicken Sie im linken Navigationsbereich auf **Gruppen** .

3. Öffnen Sie im Bereich **Gruppen****Alle Geräte > Alle mobilen Geräte > Alle direkt verwalteten Geräte**.
    
4. Klicken Sie im Bereich **Alle direkt verwalteten Geräte** auf die Registerkarte **Geräte**.
    
5. Klicken Sie in der Liste der Geräte auf Ihr iOS-Gerät.  
    
6. Stellen Sie auf dem iOS-Gerät sicher, dass der Hauptbildschirm angezeigt wird.  
    
7. Klicken Sie auf dem Verwaltungscomputer auf der Taskleiste auf **Remoteaufgaben > Remotesperre**. Beobachten Sie das iOS-Gerät, wie es zum Sperrbildschirm wechselt.
    
So entfernen Sie den Zugangscode
  
1. Klicken Sie auf dem Verwaltungscomputer im Bereich **Alle direkt verwalteten Geräte** auf die Registerkarte **Geräte**.
    
2. Klicken Sie in der Liste auf Ihr iOS-Gerät. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennungsrückstellung**. Warten Sie eine Minute.
    
3. Entsperren Sie das iOS-Gerät, und beachten Sie, dass keine Kennung mehr vorhanden ist. Um die Kennung wieder einzurichten, gehen Sie zu **Einstellungen** und dann zu **Kennung**.
    
So sperren Sie ein Android-Gerät remote
  
1. Der Microsoft Intune-Verwaltungskonsole des Browsers klicken Sie im linken Navigationsbereich auf **Gruppen** .
    
2. Öffnen Sie im Bereich **Gruppen****Alle Geräte > Alle mobilen Geräte > Alle direkt verwalteten Geräte**.
    
3. Klicken Sie im Bereich **Alle direkt verwalteten Geräte** auf die Registerkarte **Geräte**.
    
4. Klicken Sie in der Liste der Geräte auf Ihr Android-Gerät.  
    
5. Stellen Sie auf dem Auf-Gerät sicher, dass der Hauptbildschirm angezeigt wird.  
    
6. Klicken Sie auf dem Verwaltungscomputer auf der Taskleiste auf **Remoteaufgaben > Remotesperre**. Klicken Sie auf **Ja**, wenn Sie dazu aufgefordert werden.
    
7. Beobachten Sie das Android-Gerät, wie es zum Sperrbildschirm wechselt.
    
Wenn Sie die Kennung für Android-Geräte zurücksetzen, Verwaltungsportal Intune generiert und starke Kennung konfiguriert.
  
So setzen Sie den Zugangscode remote zurück
  
1. Klicken Sie auf Ihrem Verwaltungscomputer auf der Registerkarte der Microsoft Intune-Verwaltungskonsole Ihres Browsers im Bereich **Alle direkt verwalteten Geräte** auf Ihr Android-Gerät.
    
2. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennungsrückstellung**.
    
3. Klicken Sie in der Aufforderung **Remoteaufgabe: Kennungsrückstellung** auf **Ja**. Warten Sie eine Minute.
    
4. Klicken Sie im Bereich **Alle direkt verwalteten Geräte** auf die Registerkarte **Eigenschaften anzeigen**.
    
5. Beachten Sie unter **Kennungsrückstellung** die neue Kennung.
    
6. Geben Sie auf Ihrem Android-Gerät die neue Kennung auf dem Sperrbildschirm ein.  
    
7. Um die Kennung wieder zurück zu ändern, gehen Sie zu **Einstellungen**, tippen Sie auf **Gerät**, auf **Sperrbildschirm**, geben Sie die Kennung erneut ein, tippen Sie auf **Bildschirmsperre**, und legen Sie dann eine Auswahl für die Kennung fest.
    

> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.
  
## <a name="see-also"></a>Siehe auch

[Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise-Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


