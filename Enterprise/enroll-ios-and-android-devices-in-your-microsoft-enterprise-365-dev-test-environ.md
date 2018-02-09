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
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Zusammenfassung: Mit diesem Test Lab Guide können Geräte in Ihrer Microsoft 365 Dev/Test-Umgebung zu registrieren und Remote zu verwalten."
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="6f09b-103">Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="6f09b-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="6f09b-104">**Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="6f09b-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="6f09b-p101">Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="6f09b-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="6f09b-p102">Wenn Sie Sicherheit auf Geräteebene anwenden müssen, müssen Sie Geräte bei Microsoft Intune registrieren. Die Gerätregistrierung hilft nicht nur bei der Verwaltung von Geräten des Unternehmens, sondern auch bei persönlichen (BYOD) und freigegebenen Geräten, je nach den rechtlichen Richtlinien Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="6f09b-109">Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="6f09b-110">Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="6f09b-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="6f09b-111">Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.</span><span class="sxs-lookup"><span data-stu-id="6f09b-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="6f09b-112">Phase 2: Anpassen der Unternehmensportal-App für Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="6f09b-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="6f09b-113">Verwenden Sie diese Schritte, um die Unternehmensportal-App für Microsoft Intune für Ihr fiktives Unternehmen anzupassen:</span><span class="sxs-lookup"><span data-stu-id="6f09b-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="6f09b-114">Öffnen Sie auf eine neue Registerkarte die Microsoft Intune-Verwaltungskonsole ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="6f09b-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="6f09b-115">Klicken Sie im Navigationsbereich auf **Administrator** , und klicken Sie dann im Bereich **Verwaltung** auf **Verwaltung mobiler Geräte** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="6f09b-p103">Wählen Sie in **der Aufgabenliste** **Mobile Gerät Management Behörde festgelegt**. Stellen Sie sicher, dass **Microsoft Intune**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="6f09b-118">Klicken Sie im Bereich **Verwaltung** auf **Unternehmensportal**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="6f09b-119">Klicken Sie im Bereich **Unternehmensportal** konfigurieren Sie die folgenden Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="6f09b-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="6f09b-120">Name des Unternehmens: \<den Namen Ihres fiktiven Unternehmens ></span><span class="sxs-lookup"><span data-stu-id="6f09b-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="6f09b-121">IT-Abteilung Kontaktnamen: **User5**</span><span class="sxs-lookup"><span data-stu-id="6f09b-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="6f09b-122">IT-Abteilung Telefonnummer: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="6f09b-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="6f09b-123">IT-Abteilung e-Mail-Adresse: **User5 @**\<fiktive Organisationsname > **. onmicrosoft.com** (e-Mail-Adresse des Kontos User5)</span><span class="sxs-lookup"><span data-stu-id="6f09b-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="6f09b-124">Wählen Sie im **Anpassung**, **Grün** in **Designfarbe an**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="6f09b-125">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-125">Click **Save**.</span></span>
    
<span data-ttu-id="6f09b-126">Als nächstes installieren Sie die Unternehmensportal-App für Microsoft Intune und registrieren ein iOS- oder Android-Gerät. Anschließend testen Sie die grundlegende Verwaltungsfunktionalität über die Microsoft Intune-Verwaltungskonsole:</span><span class="sxs-lookup"><span data-stu-id="6f09b-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="6f09b-127">Phase 3 (für nur iOS-Geräte): Registrieren und Verwalten eines iOS-Geräts</span><span class="sxs-lookup"><span data-stu-id="6f09b-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="6f09b-128">Um ein iOS-Gerät für die Verwaltung durch Intune zu registrieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="6f09b-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="6f09b-129">Ein iOS-Gerät, z. B. ein Apple iPad oder iPhone.</span><span class="sxs-lookup"><span data-stu-id="6f09b-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="6f09b-130">Kenntnisse in der iOS-Geräte-Kenncode.</span><span class="sxs-lookup"><span data-stu-id="6f09b-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="6f09b-p104">Apple ID (Kontoname und Kennwort). Wenn Sie nicht bereits eine verfügen, rufen Sie die [ID Apple-Website](https://appleid.apple.com/#!&amp;page=signin) , und klicken Sie auf **der Apple-ID erstellen**. Erstellen Sie eine Apple-ID für das globale Administratorkonto ein Ihres Office 365-Abonnements. Tragen Sie Ihre neue Apple ID-Kontonamen und das Kennwort an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="6f09b-p105">Damit Intune iOS- und Mac-Geräte verwalten kann, ist ein Zertifikat eines Apple-Pushbenachrichtigungsdiensts erforderlich. Nachdem das Zertifikat zu Intune hinzugefügt wurde, können Benutzer die Unternehmensportal-App für Microsoft Intune zum Registrieren ihrer Geräte installieren, oder der Administrator kann eine Verwaltung von iOS-Unternehmensgeräten einrichten.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="6f09b-p106">Sie benötigen eine Datei für die Zertifikatsignieranforderung, um ein Vertrauensstellungszertifikat vom Apple-Portal für Pushzertifikate anzufordern. So erhalten Sie eine Datei für die Zertifikatsignieranforderung</span><span class="sxs-lookup"><span data-stu-id="6f09b-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="6f09b-139">Klicken Sie in der Microsoft Intune-Verwaltungskonsole im Navigationsbereich auf **Admin** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="6f09b-140">Öffnen **der Verwaltungsseite** **Verwaltung mobiler Geräte > iOS und Mac OS X**, und klicken Sie dann auf **Hochladen eines Zertifikats APNs** in **Aufgaben**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="6f09b-p107">Klicken Sie im Bereich **Hochladen eines Zertifikats APNs** klicken Sie auf **die zertifikatanforderung APNs herunterladen**. Speichern Sie das Zertifikat signieren (.csr) Anforderungsdatei lokal mit dem Namen **Dev-Test**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="6f09b-143">So aktualisieren Sie Ihr APNS-Zertifikat (Apple Push Notification Service)</span><span class="sxs-lookup"><span data-stu-id="6f09b-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="6f09b-144">Öffnen Sie eine neue Registerkarte, besuchen Sie das [Apple-Push Zertifikate Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), und melden Sie sich mit Ihrem Apple-ID.</span><span class="sxs-lookup"><span data-stu-id="6f09b-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="6f09b-145">Klicken Sie auf der Seite **Erste Schritte** auf **Zertifikat erstellen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="6f09b-146">Klicken Sie auf der Seite **Rechtlichen Hinweise** wählen Sie **ich gelesen haben und diese Geschäftsbedingungen zustimmen**, und klicken Sie auf **annehmen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="6f09b-p108">Klicken Sie auf der Seite **Erstellen eines neuen Zertifikats Push** auf **Durchsuchen** und wählen Sie die **Dev-test.csr** -Datei in der vorherigen Prozedur gespeichert, und klicken Sie dann auf **Hochladen**. Bei entsprechender Aufforderung zum Öffnen einer Datei Json, speichern Sie sie im gleichen Ordner, in dem die Dev-test.csr-Datei gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="6f09b-149">Öffnen des [Apple-Push Zertifikate Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in einer anderen Registerkarte und für **Zertifikate für Drittanbieter-Server**, klicken Sie auf **Download**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="6f09b-p109">Bei entsprechender Aufforderung zum Öffnen einer Datei .pem, speichern Sie sie mit dem Namen **Dev test.pem** im gleichen Ordner, in dem die Dev-test.csr-Datei gespeichert ist. Dies ist das Zertifikat APNs.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="6f09b-152">So laden sie das APNs-Zertifikat in Intune hoch</span><span class="sxs-lookup"><span data-stu-id="6f09b-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="6f09b-153">Klicken Sie auf der Microsoft Intune Konsole Verwaltungsregisterkarte auf der Seite **Hochladen eines Zertifikats APNs** **Hochladen des Zertifikats APNs**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="6f09b-154">Klicken Sie auf **Durchsuchen** , und geben Sie die Datei **Dev test.pem** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="6f09b-p110">Klicken Sie auf **Öffnen**, geben Sie Ihren Kontonamen Apple ID ein, und klicken Sie dann auf **Hochladen**. Eine Nachricht **bereit für die Registrierung** sollte auf der Seite **iOS und MaxOS X Mobile Geräteeinrichtung** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="6f09b-157">Da APNs-Zertifikat installiert ist, kann Intune nun iOS-Geräte registrieren und verwalten, indem Sie die Richtlinie auf registrierte mobile Geräte „geschoben“ wird.</span><span class="sxs-lookup"><span data-stu-id="6f09b-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="6f09b-158">So laden Sie die Unternehmensportal-App für Microsoft Intune herunter und registrieren das iOS-Gerät</span><span class="sxs-lookup"><span data-stu-id="6f09b-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="6f09b-159">Melden Sie sich auf Ihrem iOS-Gerät mit Ihrer Apple-ID an.</span><span class="sxs-lookup"><span data-stu-id="6f09b-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="6f09b-160">Öffnen Sie die **Apple Store** -app.</span><span class="sxs-lookup"><span data-stu-id="6f09b-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="6f09b-161">Geben Sie **Intune** in das Suchfeld ein, und tippen Sie auf **Microsoft Intune Unternehmensportal**, dann **erhalten möchten**, und klicken Sie dann **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="6f09b-162">Nach der Installation, tippen Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="6f09b-163">Melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein, auf dem Bildschirm **Intune Unternehmensportal** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="6f09b-164">Tippen Sie auf dem Bildschirm **Firma Access Setup** **beginnen**und klicken Sie dann zweimal auf **Weiter** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="6f09b-165">Klicken Sie auf die **Was als Nächstes kommt?** Bildschirm, tippen Sie auf **Registrieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="6f09b-166">Klicken Sie auf der **zuständigen Administrator aktivieren?** Bildschirm, tippen Sie auf **Aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="6f09b-167">Tippen Sie auf dem Bildschirm **Management-Profil** auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="6f09b-168">Geben Sie im **Kennung eingeben**Ihre iOS-Geräte-Kenncode.</span><span class="sxs-lookup"><span data-stu-id="6f09b-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="6f09b-169">Tippen Sie auf dem Bildschirm **was im nächsten Schritt wird** auf **Registrieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="6f09b-170">Tippen Sie im **Profil installieren**auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="6f09b-171">Tippen Sie auf der Seite **Warnung** auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="6f09b-172">**Remoteverwaltung**Tippen Sie auf **Sicherheitscenter**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="6f09b-173">Tippen Sie auf **Fertig** , um die Registrierung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="6f09b-174">Wenn Sie dazu aufgefordert werden **auf dieser Seite "Comp Portal" Öffnen?**, tippen Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="6f09b-175">Tippen Sie im Fenster **Setup von Access Unternehmen** auf **beginnen**, und tippen Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="6f09b-176">Auf dem Hauptbildschirm der Unternehmensportal-App von Microsoft Intune sollten Sie Folgendes sehen:</span><span class="sxs-lookup"><span data-stu-id="6f09b-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="6f09b-177">Eine grünes Banner.</span><span class="sxs-lookup"><span data-stu-id="6f09b-177">A green banner.</span></span>
    
  - <span data-ttu-id="6f09b-178">Oben links Ihren fiktiven Unternehmensnamen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="6f09b-179">Ihre iOS-Gerätename in **Meiner Geräte**aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="6f09b-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="6f09b-180">Im Abschnitt **Helpdesk** den **Namen des Kontakts** des **User5** mit der Telefonnummer **555-1234** und eine Schaltfläche **Kontakt per e-Mail** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="6f09b-p111">Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote entfernen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="6f09b-184">So sperren Sie ein iOS-Gerät remote</span><span class="sxs-lookup"><span data-stu-id="6f09b-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="6f09b-185">Klicken Sie von Ihrem Verwaltungscomputer auf der Registerkarte Microsoft Intune Verwaltungskonsole des Browsers im linken Navigationsbereich auf **Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="6f09b-186">Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="6f09b-187">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="6f09b-188">Klicken Sie in der Liste der Geräte auf Ihr iOS-Gerät. </span><span class="sxs-lookup"><span data-stu-id="6f09b-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="6f09b-189">Stellen Sie auf dem iOS-Gerät sicher, dass der Hauptbildschirm angezeigt wird. </span><span class="sxs-lookup"><span data-stu-id="6f09b-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="6f09b-p112">Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Folgen Sie Ihr Gerät iOS, bei der es auf dem Bildschirm Sperrung umgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="6f09b-192">So entfernen Sie den Zugangscode</span><span class="sxs-lookup"><span data-stu-id="6f09b-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="6f09b-193">Klicken Sie auf der Registerkarte **Geräte** , auf Ihrem Verwaltungscomputer, klicken Sie im Bereich **Alle direkten verwalteten Geräten** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="6f09b-p113">Klicken Sie in der Liste auf dem Gerät iOS. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**. Warten Sie eine Minute.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="6f09b-p114">Vom Gerät iOS entsperren Sie, und beachten Sie, dass eine Kennung nicht mehr vorhanden ist. Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, und klicken Sie dann die **Kennung**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="6f09b-199">Phase 3 (nur für Android-Geräte): Registrieren und Verwalten eines Android-Geräts</span><span class="sxs-lookup"><span data-stu-id="6f09b-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="6f09b-200">Um ein Android-Gerät für die Verwaltung durch Intune zu registrieren, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="6f09b-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="6f09b-201">Ein Android-Gerät.</span><span class="sxs-lookup"><span data-stu-id="6f09b-201">An Android device.</span></span>
    
- <span data-ttu-id="6f09b-202">Kenntnisse in Bezug auf das Gerät Kennung.</span><span class="sxs-lookup"><span data-stu-id="6f09b-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="6f09b-203">So laden Sie die Unternehmensportal-App für Intune herunter und registrieren das Android-Gerät</span><span class="sxs-lookup"><span data-stu-id="6f09b-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="6f09b-204">Aus dem Android-Gerät an den **Google wiedergeben Store**besuchen Sie, und tippen Sie dann auf **Erste Schritte**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="6f09b-205">Geben Sie **Intune** in das Suchfeld ein, und tippen Sie dann auf **Intune Unternehmensportal** in den Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="6f09b-206">Tippen Sie auf das **Unternehmensportal Intune** -Element, und tippen Sie dann auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="6f09b-207">Tippen Sie auf dem Bildschirm **für vollständige Konto einrichten** auf **Weiter**und dann auf **Überspringen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="6f09b-p115">Tippen Sie im **Unternehmensportal Intune**auf **annehmen**. Die app installiert.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="6f09b-210">Tippen Sie auf **Öffnen**, und tippen Sie dann auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="6f09b-211">Melden Sie sich mit Ihrem Office 365 globale Administratorkonto ein, auf dem Bildschirm **Intune Unternehmensportal** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="6f09b-212">Tippen Sie auf dem Bildschirm **Firma Access Setup** zweimal auf **beginnen**und anschließend auf **Weiter** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="6f09b-213">Klicken Sie auf die **Was als Nächstes kommt?** Bildschirm, tippen Sie auf **Registrieren**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="6f09b-214">Klicken Sie auf der **zuständigen Administrator aktivieren?** Bildschirm, tippen Sie auf **Activate.**</span><span class="sxs-lookup"><span data-stu-id="6f09b-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="6f09b-p116">Wählen Sie **ich bestätigen** , und tippen Sie dann auf **bestätigen**, auf dem Bildschirm **Datenschutzrichtlinie** . Für die Durchführung der Registrierungsprozess warten.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="6f09b-217">**Unternehmen Access** Setupbildschirm Tippen Sie auf **Weiter**, und tippen Sie dann auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="6f09b-218">Auf dem Hauptbildschirm der Unternehmensportal-App von Microsoft Intune sollten oben links ein grünes Banner und Ihr fiktiver Unternehmensname angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6f09b-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="6f09b-p117">Tippen Sie auf **Meine Geräte**. Ihre Namen Android-Gerät in der Liste sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="6f09b-p118">Tippen Sie auf **Kontakt IT**. Sie sollten die Telefonnummer des **555-1234**, eine Schaltfläche **wenden Sie sich per e-Mail** finden Sie unter und IT wenden Sie sich an der **User5**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="6f09b-p119">Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="6f09b-226">So sperren Sie ein Android-Gerät remote</span><span class="sxs-lookup"><span data-stu-id="6f09b-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="6f09b-227">Klicken Sie von Ihrem Verwaltungscomputer auf der Registerkarte Microsoft Intune Verwaltungskonsole des Browsers im linken Navigationsbereich auf **Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="6f09b-228">Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="6f09b-229">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .</span><span class="sxs-lookup"><span data-stu-id="6f09b-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="6f09b-230">Klicken Sie in der Liste der Geräte auf Ihr Android-Gerät. </span><span class="sxs-lookup"><span data-stu-id="6f09b-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="6f09b-231">Stellen Sie auf dem Auf-Gerät sicher, dass der Hauptbildschirm angezeigt wird. </span><span class="sxs-lookup"><span data-stu-id="6f09b-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="6f09b-p120">Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="6f09b-234">Beobachten Sie das Android-Gerät, wie es zum Sperrbildschirm wechselt.</span><span class="sxs-lookup"><span data-stu-id="6f09b-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="6f09b-235">Wenn Sie die Kennung für Android-Geräte zurücksetzen, Verwaltungsportal Intune generiert und starke Kennung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="6f09b-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="6f09b-236">So setzen Sie den Zugangscode remote zurück</span><span class="sxs-lookup"><span data-stu-id="6f09b-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="6f09b-237">Klicken Sie auf Ihrem Computer Administration, auf der Registerkarte Microsoft Intune Verwaltungskonsole Ihres Browsers, klicken Sie im Bereich **Alle direkten verwalteten Geräten** auf Android-Gerät.</span><span class="sxs-lookup"><span data-stu-id="6f09b-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="6f09b-238">Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="6f09b-p121">Klicken Sie auf der **Remote-Task: Kennung zurücksetzen** dazu aufgefordert werden, klicken Sie auf **Ja**. Warten Sie eine Minute.</span><span class="sxs-lookup"><span data-stu-id="6f09b-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="6f09b-241">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf **Eigenschaften anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="6f09b-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="6f09b-242">Notieren Sie unter **Kennung zurücksetzen**und die Kennung für die neue.</span><span class="sxs-lookup"><span data-stu-id="6f09b-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="6f09b-243">Geben Sie auf Ihrem Android-Gerät die neue Kennung auf dem Sperrbildschirm ein. </span><span class="sxs-lookup"><span data-stu-id="6f09b-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="6f09b-244">Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, tippen Sie auf **Gerät**, tippen Sie auf **Sperren des Bildschirms**, geben Sie die neue Kennung erneut, tippen Sie zweimal auf **Bildschirm sperren**und Ihrer Wahl für die Kennung.</span><span class="sxs-lookup"><span data-stu-id="6f09b-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="6f09b-245">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6f09b-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f09b-246">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="6f09b-246">See Also</span></span>

[<span data-ttu-id="6f09b-247">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="6f09b-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6f09b-248">Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM</span><span class="sxs-lookup"><span data-stu-id="6f09b-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6f09b-249">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="6f09b-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="6f09b-250">Enterprise-Mobilität + Sicherheit (zur Abstimmung)</span><span class="sxs-lookup"><span data-stu-id="6f09b-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


