---
title: Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung
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
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="974d4-103">Registrieren Sie iOS und Android-Geräte in Ihrer Microsoft Enterprise 365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="974d4-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="974d4-104">**Zusammenfassung:** Verwenden Sie diese Test Lab Guide zum Registrieren von Geräten in Ihrer Microsoft 365 Dev/Test-Umgebung und Remote zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="974d4-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="974d4-p101">Der Microsoft Enterprise Mobilität Suite zur Abstimmung verhindert, dass Ihre Mitarbeiter produktiv mithilfe ihrer bevorzugten apps und -Geräte beim Schützen von Daten der Organisation. Weitere Informationen finden Sie unter [Enterprise Mobilität + Sicherheit (zur Abstimmung)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="974d4-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="974d4-p102">Wenn Sie Sicherheit auf Device-Ebene anwenden möchten, müssen Sie in Microsoft Intune Geräte registrieren. Gerät-Registrierung können Sie zum Verwalten von Geräten im Besitz der Organisation nicht nur aber auch persönlich (BYOD) und gemeinsam genutzten Geräten, abhängig von Ihrer Organisation rechtliche der Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="974d4-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="974d4-109">Gemäß die Anweisungen in diesem Artikel benötigen Sie möglicherweise registrieren und grundlegende Mobilgerät Management-Funktionen für iOS und Android-Geräte in Ihrer Microsoft 365 Test-/Umgebung testen.</span><span class="sxs-lookup"><span data-stu-id="974d4-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="974d4-110">Phase 1: Erstellen der Microsoft-365 Dev/Test-Umgebung</span><span class="sxs-lookup"><span data-stu-id="974d4-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="974d4-111">Befolgen Sie die Anweisungen in [The Microsoft 365 Enterprise Test-/Umgebung](the-microsoft-365-enterprise-dev-test-environment.md)aus.</span><span class="sxs-lookup"><span data-stu-id="974d4-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="974d4-112">Phase 2: Registrieren Sie Ihre iOS und Android-Geräte</span><span class="sxs-lookup"><span data-stu-id="974d4-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="974d4-113">Verwenden Sie zunächst die Anweisungen in [Installieren und melden Sie sich die app Unternehmensportal](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) zum Anpassen von Microsoft Intune Unternehmensportal-app für Ihren Test-/-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="974d4-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="974d4-114">Im nächsten Schritt verwenden Sie die Anweisungen in [Richten Sie Ihre Unternehmensressourcen zugreifen,](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) einer iOS-Geräte zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="974d4-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="974d4-115">Im nächsten Schritt verwenden Sie die Anweisungen in [Registrieren Ihrer Android-Gerät im Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) Android-Gerät zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="974d4-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="974d4-116">Phase 2: Verwalten Sie Ihrer iOS und Android-Geräte Remote</span><span class="sxs-lookup"><span data-stu-id="974d4-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="974d4-p103">Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand seinen Zugangscode vergisst, können Sie die diesen remote entfernen.</span><span class="sxs-lookup"><span data-stu-id="974d4-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="974d4-120">So sperren Sie ein iOS-Gerät remote</span><span class="sxs-lookup"><span data-stu-id="974d4-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="974d4-121">Öffnen Sie eine neue Registerkarte, und wechseln Sie zur http://manage.microsoft.com (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="974d4-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="974d4-122">Der Microsoft Intune-Verwaltungskonsole des Browsers klicken Sie im linken Navigationsbereich auf **Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="974d4-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="974d4-123">Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.</span><span class="sxs-lookup"><span data-stu-id="974d4-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="974d4-124">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .</span><span class="sxs-lookup"><span data-stu-id="974d4-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="974d4-125">Klicken Sie in der Liste der Geräte auf Ihr iOS-Gerät. </span><span class="sxs-lookup"><span data-stu-id="974d4-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="974d4-126">Stellen Sie auf dem iOS-Gerät sicher, dass der Hauptbildschirm angezeigt wird. </span><span class="sxs-lookup"><span data-stu-id="974d4-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="974d4-p104">Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Folgen Sie Ihr Gerät iOS, bei der es auf dem Bildschirm Sperrung umgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="974d4-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="974d4-129">So entfernen Sie den Zugangscode</span><span class="sxs-lookup"><span data-stu-id="974d4-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="974d4-130">Klicken Sie auf der Registerkarte **Geräte** , auf Ihrem Verwaltungscomputer, klicken Sie im Bereich **Alle direkten verwalteten Geräten** .</span><span class="sxs-lookup"><span data-stu-id="974d4-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="974d4-p105">Klicken Sie in der Liste auf dem Gerät iOS. Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**. Warten Sie eine Minute.</span><span class="sxs-lookup"><span data-stu-id="974d4-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="974d4-p106">Vom Gerät iOS entsperren Sie, und beachten Sie, dass eine Kennung nicht mehr vorhanden ist. Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, und klicken Sie dann die **Kennung**.</span><span class="sxs-lookup"><span data-stu-id="974d4-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="974d4-136">So sperren Sie ein Android-Gerät remote</span><span class="sxs-lookup"><span data-stu-id="974d4-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="974d4-137">Der Microsoft Intune-Verwaltungskonsole des Browsers klicken Sie im linken Navigationsbereich auf **Gruppen** .</span><span class="sxs-lookup"><span data-stu-id="974d4-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="974d4-138">Öffnen Sie im Bereich **Gruppen** **alle Geräte > alle Mobile Geräte > alle direkten verwalteten Geräten**.</span><span class="sxs-lookup"><span data-stu-id="974d4-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="974d4-139">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf der Registerkarte **Geräte** .</span><span class="sxs-lookup"><span data-stu-id="974d4-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="974d4-140">Klicken Sie in der Liste der Geräte auf Ihr Android-Gerät. </span><span class="sxs-lookup"><span data-stu-id="974d4-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="974d4-141">Stellen Sie auf dem Auf-Gerät sicher, dass der Hauptbildschirm angezeigt wird. </span><span class="sxs-lookup"><span data-stu-id="974d4-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="974d4-p107">Klicken Sie auf Ihrem Verwaltungscomputer, klicken Sie auf der Taskleiste auf **Remoteaufgaben > Remote Sperre**. Wenn Sie aufgefordert werden, klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="974d4-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="974d4-144">Beobachten Sie das Android-Gerät, wie es zum Sperrbildschirm wechselt.</span><span class="sxs-lookup"><span data-stu-id="974d4-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="974d4-145">Wenn Sie die Kennung für Android-Geräte zurücksetzen, Verwaltungsportal Intune generiert und starke Kennung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="974d4-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="974d4-146">So setzen Sie den Zugangscode remote zurück</span><span class="sxs-lookup"><span data-stu-id="974d4-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="974d4-147">Klicken Sie auf Ihrem Computer Administration, auf der Registerkarte Microsoft Intune Verwaltungskonsole Ihres Browsers, klicken Sie im Bereich **Alle direkten verwalteten Geräten** auf Android-Gerät.</span><span class="sxs-lookup"><span data-stu-id="974d4-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="974d4-148">Klicken Sie auf der Taskleiste auf **Remoteaufgaben > Kennung zurücksetzen**.</span><span class="sxs-lookup"><span data-stu-id="974d4-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="974d4-p108">Klicken Sie auf der **Remote-Task: Kennung zurücksetzen** dazu aufgefordert werden, klicken Sie auf **Ja**. Warten Sie eine Minute.</span><span class="sxs-lookup"><span data-stu-id="974d4-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="974d4-151">Klicken Sie im Bereich **Alle direkten verwalteten Geräten,** klicken Sie auf **Eigenschaften anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="974d4-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="974d4-152">Notieren Sie unter **Kennung zurücksetzen**und die Kennung für die neue.</span><span class="sxs-lookup"><span data-stu-id="974d4-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="974d4-153">Geben Sie auf Ihrem Android-Gerät die neue Kennung auf dem Sperrbildschirm ein. </span><span class="sxs-lookup"><span data-stu-id="974d4-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="974d4-154">Um die Kennung wieder zu ändern, wechseln Sie in den **Einstellungen**, tippen Sie auf **Gerät**, tippen Sie auf **Sperren des Bildschirms**, geben Sie die neue Kennung erneut, tippen Sie zweimal auf **Bildschirm sperren**und Ihrer Wahl für die Kennung.</span><span class="sxs-lookup"><span data-stu-id="974d4-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="974d4-155">Klicken Sie [hier](http://aka.ms/catlgstack), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in der Microsoft Cloud zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="974d4-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="974d4-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="974d4-156">See Also</span></span>

[<span data-ttu-id="974d4-157">Die Microsoft 365 Enterprise-Entwicklungs-/Testumgebung</span><span class="sxs-lookup"><span data-stu-id="974d4-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="974d4-158">Richtlinien für die Microsoft 365 Enterprise Test-/Umgebung MAM</span><span class="sxs-lookup"><span data-stu-id="974d4-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="974d4-159">Testumgebungsanleitungen (TLGs) zur Cloudakzeptanz</span><span class="sxs-lookup"><span data-stu-id="974d4-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="974d4-160">Enterprise-Mobilität + Sicherheit (zur Abstimmung)</span><span class="sxs-lookup"><span data-stu-id="974d4-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


