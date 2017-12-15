---
title: "Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Zusammenfassung: Mit diesem Test Lab Guide können Geräte in Ihrer Microsoft 365 Dev/Test-Umgebung zu registrieren und Remote zu verwalten."
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung

 **Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.
  
Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
  
Wenn Sie Sicherheit auf Geräteebene anwenden müssen, müssen Sie Geräte bei Microsoft Intune registrieren. Die Gerätregistrierung hilft nicht nur bei der Verwaltung von Geräten des Unternehmens, sondern auch bei persönlichen (BYOD) und freigegebenen Geräten, je nach den rechtlichen Richtlinien Ihrer Organisation.
  
Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung

Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>Phase 2: Anpassen der Unternehmensportal-App für Microsoft Intune

Verwenden Sie diese Schritte, um die Unternehmensportal-App für Microsoft Intune für Ihr fiktives Unternehmen anzupassen:
  
1. Öffnen Sie auf eine neue Registerkarte die Microsoft Intune-Verwaltungskonsole ([https://manage.microsoft.com](https://manage.microsoft.com)).
    
2. Klicken Sie im Navigationsbereich auf **Administrator** , und klicken Sie dann im Bereich **Verwaltung** auf **Verwaltung mobiler Geräte** .
    
3. Wählen Sie in **der Aufgabenliste** **Mobile Gerät Management Behörde festgelegt**. Stellen Sie sicher, dass **Microsoft Intune**festgelegt ist.
    
4. Klicken Sie im Bereich **Verwaltung** auf **Unternehmensportal**.
    
5. Klicken Sie im Bereich **Unternehmensportal** konfigurieren Sie die folgenden Einstellungen:
    
  - Name des Unternehmens: \<den Namen Ihres fiktiven Unternehmens >
    
  - IT-Abteilung Kontaktnamen: **User5**
    
  - IT-Abteilung Telefonnummer: **555-1234**
    
  - IT-Abteilung e-Mail-Adresse: **User5 @**\<fiktive Organisationsname > **. onmicrosoft.com** (e-Mail-Adresse des Kontos User5)
    
6. Wählen Sie im **Anpassung**, **Grün** in **Designfarbe an**.
    
7. Klicken Sie auf **Speichern**.
    
Als nächstes installieren Sie die Unternehmensportal-App für Microsoft Intune und registrieren ein iOS- oder Android-Gerät. Anschließend testen Sie die grundlegende Verwaltungsfunktionalität über die Microsoft Intune-Verwaltungskonsole:
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>Phase 3 (für nur iOS-Geräte): Registrieren und Verwalten eines iOS-Geräts

Um ein iOS-Gerät für die Verwaltung durch Intune zu registrieren, benötigen Sie Folgendes:
  
- Ein iOS-Gerät, z. B. ein Apple iPad oder iPhone.
    
- Kenntnisse in der iOS-Geräte-Kenncode.
    
- Apple ID (Kontoname und Kennwort). Wenn Sie nicht bereits eine verfügen, rufen Sie die [ID Apple-Website](https://appleid.apple.com/#!&amp;page=signin) , und klicken Sie auf **der Apple-ID erstellen**. Erstellen Sie eine Apple-ID für das globale Administratorkonto ein Ihres Office 365-Abonnements. Tragen Sie Ihre neue Apple ID-Kontonamen und das Kennwort an einem sicheren Ort.
    
Damit Intune iOS- und Mac-Geräte verwalten kann, ist ein Zertifikat eines Apple-Pushbenachrichtigungsdiensts erforderlich. Nachdem das Zertifikat zu Intune hinzugefügt wurde, können Benutzer die Unternehmensportal-App für Microsoft Intune zum Registrieren ihrer Geräte installieren, oder der Administrator kann eine Verwaltung von iOS-Unternehmensgeräten einrichten.
  
Sie benötigen eine Datei für die Zertifikatsignieranforderung, um ein Vertrauensstellungszertifikat vom Apple-Portal für Pushzertifikate anzufordern. So erhalten Sie eine Datei für die Zertifikatsignieranforderung
  
1. Klicken Sie in der Microsoft Intune-Verwaltungskonsole im Navigationsbereich auf **Admin** .
    
    Öffnen **der Verwaltungsseite** **Verwaltung mobiler Geräte > iOS und Mac OS X**, und klicken Sie dann auf **Hochladen eines Zertifikats APNs** in **Aufgaben**. 
    
2. Klicken Sie im Bereich **Hochladen eines Zertifikats APNs** klicken Sie auf **die zertifikatanforderung APNs herunterladen**. Speichern Sie das Zertifikat signieren (.csr) Anforderungsdatei lokal mit dem Namen **Dev-Test**.
    
So aktualisieren Sie Ihr APNS-Zertifikat (Apple Push Notification Service)
  
1. Öffnen Sie eine neue Registerkarte, besuchen Sie das [Apple-Push Zertifikate Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), und melden Sie sich mit Ihrem Apple-ID.
    
2. Klicken Sie auf der Seite **Erste Schritte** auf **Zertifikat erstellen**.
    
3. Klicken Sie auf der Seite **Rechtlichen Hinweise** wählen Sie **ich gelesen haben und diese Geschäftsbedingungen zustimmen**, und klicken Sie auf **annehmen**.
    
4. Klicken Sie auf der Seite **Erstellen eines neuen Zertifikats Push** auf **Durchsuchen** und wählen Sie die **Dev-test.csr** -Datei in der vorherigen Prozedur gespeichert, und klicken Sie dann auf **Hochladen**. Bei entsprechender Aufforderung zum Öffnen einer Datei Json, speichern Sie sie im gleichen Ordner, in dem die Dev-test.csr-Datei gespeichert ist.
    
5. Öffnen des [Apple-Push Zertifikate Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in einer anderen Registerkarte und für **Zertifikate für Drittanbieter-Server**, klicken Sie auf **Download**.
    
6. Bei entsprechender Aufforderung zum Öffnen einer Datei .pem, speichern Sie sie mit dem Namen **Dev test.pem** im gleichen Ordner, in dem die Dev-test.csr-Datei gespeichert ist. Dies ist das Zertifikat APNs.
    
So laden sie das APNs-Zertifikat in Intune hoch
  
1. Klicken Sie auf der Microsoft Intune Konsole Verwaltungsregisterkarte auf der Seite **Hochladen eines Zertifikats APNs** **Hochladen des Zertifikats APNs**.
    
2. Klicken Sie auf **Durchsuchen** , und geben Sie die Datei **Dev test.pem** .
    
3. Klicken Sie auf **Öffnen**, geben Sie Ihren Kontonamen Apple ID ein, und klicken Sie dann auf **Hochladen**. Eine Nachricht **bereit für die Registrierung** sollte auf der Seite **iOS und MaxOS X Mobile Geräteeinrichtung** angezeigt werden.
    
Da APNs-Zertifikat installiert ist, kann Intune nun iOS-Geräte registrieren und verwalten, indem Sie die Richtlinie auf registrierte mobile Geräte „geschoben“ wird.
  
So laden Sie die Unternehmensportal-App für Microsoft Intune herunter und registrieren das iOS-Gerät
  
1. Melden Sie sich auf Ihrem iOS-Gerät mit Ihrer Apple-ID an.
    
2. Öffnen Sie die **Apple Store** -app.
    
3. Geben Sie **Intune** in das Suchfeld ein, und tippen Sie auf **Microsoft Intune Unternehmensportal**, dann **erhalten möchten**, und klicken Sie dann **Installieren**.
    
4. Nach der Installation, tippen Sie auf **Öffnen**.
    
5. Melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein, auf dem Bildschirm **Intune Unternehmensportal** .
    
6. Tippen Sie auf dem Bildschirm **Firma Access Setup** **beginnen**und klicken Sie dann zweimal auf **Weiter** .
    
7. Klicken Sie auf die **Was als Nächstes kommt?** Bildschirm, tippen Sie auf **Registrieren**.
    
8. Klicken Sie auf der **zuständigen Administrator aktivieren?** Bildschirm, tippen Sie auf **Aktivieren**.
    
9. Tippen Sie auf dem Bildschirm **Management-Profil** auf **Installieren**.
    
10. Geben Sie im **Kennung eingeben**Ihre iOS-Geräte-Kenncode.
    
11. Tippen Sie auf dem Bildschirm **was im nächsten Schritt wird** auf **Registrieren**.
    
12. Tippen Sie im **Profil installieren**auf **Installieren**.
    
13. Tippen Sie auf der Seite **Warnung** auf **Installieren**.
    
14. **Remoteverwaltung**Tippen Sie auf **Sicherheitscenter**.
    
15. Tippen Sie auf **Fertig** , um die Registrierung abzuschließen.
    
16. Wenn Sie dazu aufgefordert werden **auf dieser Seite "Comp Portal" Öffnen?**, tippen Sie auf **Öffnen**.
    
17. Tippen Sie im Fenster **Setup von Access Unternehmen** auf **beginnen**, und tippen Sie dann auf **Fertig**.
    
18. Auf dem Hauptbildschirm der Unternehmensportal-App von Microsoft Intune sollten Sie Folgendes sehen:
    
  - Eine grünes Banner.
    
  - Oben links Ihren fiktiven Unternehmensnamen.
    
  - Ihre iOS-Gerätename in **Meiner Geräte**aufgeführt.
    
  - Im Abschnitt **Helpdesk** den **Namen des Kontakts** des **User5** mit der Telefonnummer **555-1234** und eine Schaltfläche **Kontakt per e-Mail** .
    
Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote entfernen.
  
So sperren Sie ein iOS-Gerät remote
  
1. Klicken Sie von Ihrem Verwaltungscomputer auf der Registerkarte Microsoft Intune Verwaltungskonsole des Browsers im linken Navigationsbereich auf **Gruppen** .
    
2. Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.
    
3. Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .
    
4. Klicken Sie in der Liste der Geräte auf Ihr iOS-Gerät.  
    
5. Stellen Sie auf dem iOS-Gerät sicher, dass der Hauptbildschirm angezeigt wird.  
    
6. Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Folgen Sie Ihr Gerät iOS, bei der es auf dem Bildschirm Sperrung umgeschaltet.
    
So entfernen Sie den Zugangscode
  
1. Klicken Sie auf der Registerkarte **Geräte** , auf Ihrem Verwaltungscomputer, klicken Sie im Bereich **Alle direkten verwalteten Geräten** .
    
2. Klicken Sie in der Liste auf dem Gerät iOS. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**. Warten Sie eine Minute.
    
3. Vom Gerät iOS entsperren Sie, und beachten Sie, dass eine Kennung nicht mehr vorhanden ist. Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, und klicken Sie dann die **Kennung**.
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>Phase 3 (nur für Android-Geräte): Registrieren und Verwalten eines Android-Geräts

Um ein Android-Gerät für die Verwaltung durch Intune zu registrieren, benötigen Sie Folgendes:
  
- Ein Android-Gerät.
    
- Kenntnisse in Bezug auf das Gerät Kennung.
    
So laden Sie die Unternehmensportal-App für Intune herunter und registrieren das Android-Gerät
  
1. Aus dem Android-Gerät an den **Google wiedergeben Store**besuchen Sie, und tippen Sie dann auf **Erste Schritte**.
    
2. Geben Sie **Intune** in das Suchfeld ein, und tippen Sie dann auf **Intune Unternehmensportal** in den Suchergebnissen.
    
3. Tippen Sie auf das **Unternehmensportal Intune** -Element, und tippen Sie dann auf **Installieren**.
    
4. Tippen Sie auf dem Bildschirm **für vollständige Konto einrichten** auf **Weiter**und dann auf **Überspringen**.
    
5. Tippen Sie im **Unternehmensportal Intune**auf **annehmen**. Die app installiert.
    
6. Tippen Sie auf **Öffnen**, und tippen Sie dann auf **Anmelden**.
    
7. Melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein, auf dem Bildschirm **Intune Unternehmensportal** .
    
8. Tippen Sie auf dem Bildschirm **Firma Access Setup** zweimal auf **beginnen**und anschließend auf **Weiter** .
    
9. Klicken Sie auf die **Was als Nächstes kommt?** Bildschirm, tippen Sie auf **Registrieren**.
    
10. Klicken Sie auf der **zuständigen Administrator aktivieren?** Bildschirm, tippen Sie auf **Activate.**
    
11. Wählen Sie **ich bestätigen** , und tippen Sie dann auf **bestätigen**, auf dem Bildschirm **Datenschutzrichtlinie** . Für die Durchführung der Registrierungsprozess warten.
    
12. **Unternehmen Access** Setupbildschirm Tippen Sie auf **Weiter**, und tippen Sie dann auf **Fertig**.
    
13. Auf dem Hauptbildschirm der Unternehmensportal-App von Microsoft Intune sollten oben links ein grünes Banner und Ihr fiktiver Unternehmensname angezeigt werden.
    
14. Tippen Sie auf **Meine Geräte**. Ihre Namen Android-Gerät in der Liste sollte angezeigt werden.
    
15. Tippen Sie auf **Kontakt IT**. Sie sollten die Telefonnummer des **555-1234**, eine Schaltfläche **wenden Sie sich per e-Mail** finden Sie unter und IT wenden Sie sich an der **User5**.
    
Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote zurücksetzen.
  
So sperren Sie ein Android-Gerät remote
  
1. Klicken Sie von Ihrem Verwaltungscomputer auf der Registerkarte Microsoft Intune Verwaltungskonsole des Browsers im linken Navigationsbereich auf **Gruppen** .
    
2. Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.
    
3. Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .
    
4. Klicken Sie in der Liste der Geräte auf Ihr Android-Gerät.  
    
5. Stellen Sie auf dem Auf-Gerät sicher, dass der Hauptbildschirm angezeigt wird.  
    
6. Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.
    
7. Beobachten Sie das Android-Gerät, wie es zum Sperrbildschirm wechselt.
    
Wenn Sie die Kennung für Android-Geräte zurücksetzen, Verwaltungsportal Intune generiert und starke Kennung konfiguriert.
  
So setzen Sie den Zugangscode remote zurück
  
1. Klicken Sie auf Ihrem Computer Administration, auf der Registerkarte Microsoft Intune Verwaltungskonsole Ihres Browsers, klicken Sie im Bereich **Alle direkten verwalteten Geräten** auf Android-Gerät.
    
2. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**.
    
3. Klicken Sie auf der **Remote-Task: Kennung zurücksetzen** dazu aufgefordert werden, klicken Sie auf **Ja**. Warten Sie eine Minute.
    
4. Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf **Eigenschaften anzeigen**.
    
5. Notieren Sie unter **Kennung zurücksetzen**und die Kennung für die neue.
    
6. Geben Sie auf Ihrem Android-Gerät die neue Kennung auf dem Sperrbildschirm ein.  
    
7. Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, tippen Sie auf **Gerät**, tippen Sie auf **Sperren des Bildschirms**, geben Sie die neue Kennung erneut, tippen Sie zweimal auf **Bildschirm sperren**und Ihrer Wahl für die Kennung.
    
> [!TIP]
> Klicken Sie [hier](http://aka.ms/catlgstack) für eine visuelle Darstellung aller die Artikel in einer Microsoft Cloud Test Lab Guide-Stapel.
  
## <a name="see-also"></a>See Also

[Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise-Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


